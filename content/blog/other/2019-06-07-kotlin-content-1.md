---
layout: post
title: [kotlin] 코틀린 도입시 고려할 것들
date: 2019-06-07
tags: [kotlin]
---



# 코틀린 도입시 고려할 것들

## 개발 환경

#### 버전 업데이트 시 변화가 크지 않음
1.0 ~ 1.3의 문법, API 하위 호환

#### 언어 주변 환경

개발을 주도하는 업체가 Jetbrains. Java IDE를 개발하고 있는 수준이기 때문에, 컴파일러와 관련된 기술력이나 프로그래밍 언어에 대한 이해가 상당할 것이라 생각됨.
Google의 안드로이드 개발 환경도 Eclipse + ADT에서 Jetbrains 사의 Android Studio로 바뀐지 오래다. 이 점도 신뢰를 높이는데 일조함

#### 도입이 간단하다

새로운 언어를 도입하고자 할 때는 개발 환경 구축에 문제가 생겨 시간이 오래 걸리고, 제대로 된 개발 환경이 갖춰져 있지 않을 때 오히려 언어 자체의 개발 생산성을 개발 환경이 상쇄할 수 있는 우려가 있다.
Kotlin은 우선 IDE에 연동하기 위한 Intellij 용 플러그인을 Jetbrains에서 제공하고 있다. 같은 회사에서 IDE와 언어를 만들기 때문에 지원이 확실하다.

플러그인 설치도 간단하다. 업데이트 역시 마찬가지

프로젝트 빌드에 도입하는 것 또한 간단합니다.

  `Android Studio > Tools > Kotlin > Configure Kotlin in Project`를 클릭하면 다이얼로그가 나와서, OK 버튼을 누르면  자동으로 설치합니다.

#### 자바와의 연계 기능이 강력하다.

개발 언어를 변경하는 경우 기존 언어와의 동시 사용이 어렵거나, 원활하지 않은 경우 기존 프로젝트에 추가로 도입할 수도 없으며 과거의 코드 리소스가 낭비되고, 만에 하나 문제가 발생하는 경우를 피할 수가 없습니다.

그 점에서 볼 때 Kotlin은 Java와의 연계 능력이 정말로 강력합니다. Scala나 Groovy와 마찬가지로 java 바이트코드로 컴파일되어 JVM 위에서 구동됩니다.

언어 사양에서 우선 Java와의 연계가 중요시되고 있으며, 기존 Java 프로젝트에 Kotlin 소스를 섞어서 사용할 수 있도록 되어잇습니다. 또 Kotlin에서 자연스럽게 Java의 클래스나 메소드를 호출 가능합니다. 공식 사이트에서도  100% Interoperable with Java라고 나와있습니다.

## 언어 특성

#### 정적 타입 지정 언어

자바와 마찬가지로 코틀린은 정적 타입 지정 언어이다. 모든 프로그램의 구성 요소의 타입을 컴파일 시점에 알 수 있고, 프로그램 안에서 객체의 필드나 메소드를 사용할 때마다 컴파일러가 타입을 검증해준다는 뜻이다. 그에 따라 코드가 더 짧아지고, 유연하다.

```kotlin
var x = 1
var s = "string"
```

자바와 비교하여 타입 추론 기능이 있다. 컴파일러가 문맥을 고려해 변수 타입을 결정한다.

- 성능 : 실행 시점에 어떤 메서드를 호출할지 알아내는 과정이 필요 없으므로 메소드 호출이 더 빠르다.
- 신뢰성 : 컴파일러가 프로그램의 정확성을 검증하기 때문에 실행 시 프로그램이 오류로 중단될 가능성이 적다.
- 유지 보수성 : 코드에서 다루는 객체가 어떤 타입에 속하는지 알 수 있기 때문에 처음 보는 코드를 다룰 때 더 쉽다.
- 도구 지원 : 정적 타입을 활용하면 안전한 리팩토링이 가능하고, 도구는 정확한 코드 완성 기능을 제공하며 IDE의 다른 지원 기능도 더 잘 만들 수 있다.

### 자바와 성능을 비교하면?
