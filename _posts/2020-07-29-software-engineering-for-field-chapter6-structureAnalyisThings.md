---
title: "6장 구조적 분석기법, 실무에 바로 적용하는 소프트웨어 공학, 김희영 저"
last_moified_at: 2020-07-29T00:00:00-00:00
categories:
 - 소프트웨어 공학
tags:
 - 구조적 분석
 - 구조적 분석 역사
 - DFD작성기호
 - DFD 작성
 - 자료사전
 - 소단위명세서
 - DFD작성주의사항
 - DFD작성지침
 - 김희영
---

# 6장 구조적 분석기법

## 6.1 구조적분석이란

- 원리

  - 추상화의 원칙

    특정 대상에 대한 실체를 분리하기 위해 "HOW"가 아닌, "WHAT"으로 표현하는 간소한 방법, 사소한 제약 안받고 문제 해결가능

  - 정형화의 원칙

    소프트웨어의 제어와 산출물의 품질관리를 위한 기초가됨. 형식이 생각과 명령을 자동화시킬 수 있는 근거 제공

  - 분할정복

    큰 시스템을 작은 독립적인 서브시스템으로 분할하고, 분할한 시스템들을 개발 및 해결하는 개념

  - 계층적 구조

    분할정복을 위해 나눠진 모듈들을 상호 연관 관계 및 구조에 대한 이해도 향상에 도움을 줌. 의사소통과 제어문제

- 다익스트라, 구조적 프로그래밍에서 계층적 제어구조 구성

  - 순차(concatenation)

    구문순서에 따라 순서대로 수행된다는 것.

  - 선택(selection)

    프로그램의 상태에 따라서 여러 구문들 중에서 하나를 수행하는 것

  - 반복(repetition)

    특정상태 도달할때까지 구문반복, 집합체 각각 원소들에 대해 어떤 구문 반복수행

## 6.2구조적 분석의 발전

구조적 분석 발전 -> 모듈러 프로그래밍(modular programming)

- 모듈러 프로그래밍
  - 코드의 가독성 높임
  - 재사용성 증가시킴
  - 코딩의 효율성, 기능파악 용이
  - 코딩길이, 시간 줄어듬.
  - 데이터의 생성과 소멸 따른 자원소모 발생
  - 연산자 기반으로 데이터기반보다는 불편함.

## 6.3 DFD 작성을 위한 기호

![img](https://t1.daumcdn.net/cfile/tistory/135FE1334CC5719BC8)

​				출처 <https://yimma.tistory.com/137>

1. ### 프로세스(process)

   전환되거나 저장되거나 분배되기 위한 데이터를 관리하는 작업 또는 행동

   전산화 되기 이전 주로 수작업으 활동 의미, 데이터를 처리하는 작업.

   

2. ### 데이터저장소(data store)

   전산화 되기 이전에 종이로 작성된 문서철이나 관리대장 등

   전산화 과정에서 파일이나, 데이터베이스로 시스템화될 수 있는 부분

3. ### 외부 엔터티(external entity)

   ERD(Entity Relatino Diagram)의 엔터티와 다름

   외부 엔터티 혹은 인터페이스(interface)

   데이터를 제공하거나 제공받는 주체(사람, 조직, 외부시스템) -> 유스케이스에 액터(actor)와 연관성있음

4. ### 데이터흐름(data flow)

   이동하고 움직이는 데이터의 흐름

   

## 6.4 DFD 작성

- 배경도(context diagram)

  - 프로세스가 하나

  - 개발하게 될 시스템 명칭 부여

  - 시스템 관련 외부 엔터티를 배경도에 정의, 관련 모든 외부 엔터티 확인가능

    

- 0수준 DFD

  - 시스템 분석가 사용자 인터뷰, 개략적 DFD초안 작성
  - 사용자 확인 및 검증으로 구체화, 개선

  

- 1수준 DFD

  - 0수준 DFD 더욱 분할하여 최종적 프로그램 구현이 가능한 수준까지 상세화
  - 더 구체화 어려운 프로세스는 "소단위 명세서(mini-spec)" 작성
  - 더 분할 못하는 작은 단위 "원초적 프로세스(primitive process)"

## 6.5 자료사전(data dictionary)작성

DFD의 자료저장소와 데이터흐름에 대한 구체적 내용 설명

ex) 과목파일 = 과목번호, 과목명, 담당교수, 강의실 / 학적파일 = 학번, 성명, 수강신청과목, 과목교수



## 6.6 소단위 명세서(mini-spec) 작성

"DFD"만으로 분석결과 프로그램 개발이 부족하므로, 소단위 명세서를 중간에 두어 분석과 구현의 중간과정으로 활용함.

"원초적 프로세스"에 대한 구체적 설명을 글로 서술하는 것.

화면 혹은 보고서 출력에 대한 처리과정과 처리조건을 글로서 표현하거나 "처리로직(process logic)" 혹은 "알고리즘(algorithm)"으로 표현

```
과목목록 = FIND_DB(과목목록, 연도, 학기)
DO WHILE 과목목록의 과목명 중 1개
출석부 =  FIND_DB(출석부, 연도, 학기, 과목명)
         DO WHILE 출석부의 학생 중 1명
                  결석수 = 출석부의 학생 결석수를 더한 수
                  성적부의 성적 = 성적부 성적 - 결석수 * 2
         END DO
END DO
```



## 6.7 DFD 작성시 주의사항

- 상위수준에서 하위수준으로 일관성 유지

  배경도에 없는 새 외부엔터티 추가시, 배경도 수정해야됨.

  0, 1, 2, 3수준 등 구체화됨. 더 안되면 소단위 명세서 기술

- 자료저장소의 구체화

  자료사전으로 표현되어야함. -> 향후 DB로 구축될것 염두



## 6.8 DFD 작성 지침

1. ### 모든 DFD에 적용되는 규칙

- 입력 데이터, 출력 데이터는 달라야한다. 프로세스를 거쳤는데 변화 없다면 일을 안한것.
- 기호로 표현한 DFD상 데이터저장소, 프로세스, 외부엔터티, 데이터흐름 각자 유일한 명칭 가질것.

1. ### 기호별 작성규칙

   - 프로세스 규칙

     입력만, 출력만 있는 프로세스는 없음.

     프로세스 이름 동사형 작명규칙(한다 붙임)

   - 데이터 저장소 규칙

     한개의 데이터 저장소로부터 다른 데이터 저장소로 직접 이동할 수 없음.

     데이터는 외부 엔터티로부터 직접 이동할 수도 없음.

     외부엔터티로부터 데이터로 직접 이동할수 없음.

     무조건 프로세스를 통해야 전달가능.

     명사형으로 작명해야됨.

   - 외부 엔터티 규칙

     기호 사이에 오직 한 방향의 흐름을 가짐.

     한번 지나간 동일한 프로세스로 직접적 역행은 불가능.

   - 데이터 흐름 규칙

     데이터 저장소로의 데이터흐름은 갱신(삭제 또는 수정) 의미.

     데이터 저장소로부터 데이터 흐름은 추출이나 사용(조회) 의미

     데이터 흐름은 명사형 작명

     

2. ### DFD의 기능적 분해(functional decomposition)

   - 완전성(dompleteness)

     DFD는 모델링 하고자 하는 시스템에 필요한 모든 구성요소를 포함.

   - 균형성(balance)

     상위 수준 1레벨, 하위 프로세스 2베렐, 레발 다운 시 상위수준의 입력과 출력 보존.

   - 타이밍(timing)

     시간개념 표시 못함.(시간에 대한 개념 안가짐)

   - 반복적 개선(iterative enhancement)

     시스템 분석가가 여러번 반복해서 DFD 수정보완개선

   - 분해의 중단(stop of decomposition)

     - 상세수준으로 분해되지 않는 시점(원초적)
       - 각각의 프로세스를 하나의 의사결정이나 계산, 또는 단일 데이터베이스를 조작하는 수준(SQL문장 처리수준)까지 줄었을때
       - 각각의 데이터 저장소가 단일 개체에 대한 데이터 나타낼때, 테이블로 표현 가능한 수준까지 충분,상세하게 정의되었을때
       - 소프트웨어 개발자가 더 상세한 세부사항을 보고자 하지 않을 때, 코딩이 가능하다고 판단할 수준이 되었을 때.
       - 모든 데이터가 다양한 방법으로 처리된다는 것을 보여주기 위해 더 이상 분해할 필요가 없응ㄹ때.
       - 단일 데이터 흐름으로 각각의 사업양식이나 거래, 컴퓨터 온라인 디스플레이, 보고서를 충분히 보여줬다고 생각될때.