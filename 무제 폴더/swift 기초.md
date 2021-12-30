# swift 기초 



## :: 명명법 / 콘솔로그 / 문자열 보간법 ::

### 명명법

* Lower Camel Case : 함수, 메서드, 변수, 상수등

  Ex) someVariableName

* Upper Camel Case : 타입, 클래스, 구조체, 열과형등

​		Ex) Person,Point, Week

### 콘솔로그

* print : 단순 문자열 출력 
* dump : 인스턴스의 자세한 설명(description 프로터티)까지 출력



## 문자열 보간법

* String Interpolaton
* 프로그램 실행 중 문자열 내에 변수 똔느 상수의 실질적인 값을 표현하기 위해 사용
* \ ()



```swift
import Swift

let age: Int = 10

print("안녕하세요! 저는\(age + 5)살입니다") // "안녕하세요! 저는 15살입니다"

class Person{
  var name: String = "yagom"
  var age: Ing = 10
}
let yagom: Person = Person()
print(yagom) // "파일명.Person"

dump(yagom) // ▿ 파일명.Person #0
 						// - name: "yagom"
						// - age: 10
```



## :: 상수와 변수 ::



### 상수와 변수 선언

* let : 상수 선언 키워드 
* var : 변수 선언 키워드



```swift
// 상수와 변수 선언
let 상수이름: 타입 = 값
var 변수이름: 타입 = 값

// 값의 타입이 명확하다면 타입 생략 가능
let 상수이름 = 값
var 변수이름 = 값

// 상수와 변수 활용
let constant: String = "차후에 변경이 불가능한 상수 let"
var variable: String = "차후에 변경이 가능한 변수 var"

variable = "변수는 이렇게 차후에 다른 값을 할당할 수 있지만"

constant = "상수는 차후에 값을 변경할 수 없습니다" // 오류발생


let sum: Int
let inputA: Int = 100
let inputB: Int = 200

// 선언 후 첫 할당
sum = inputA + inputB

sum = 1 // 그 이후에는 다시 값을 바꿀 수 없습니다, 오류발생

// 변수도 물론 차후에 할당하는 것이 가능합니다
var nickName: String

nickName = "yagom"

// 변수는 차후에 다시 다른 값을 할당해도 문제가 없지요
nickName = "야곰"
```



## :: 기본 데이터 타입 ::

### **Swift의 기본 데이터 타입**

* Bool
* Int, UInt
* Float, Double
* Character, String



### Bool

* true와 false만을 값으로 가지는 타입  // 0,1은 넣을 수 없음 

  ```swift
  var someBool: Bool = true
  someBool = false
  someBool = 0 // 컴파일 오류발생
  someBool = 1 // 컴파일 오류발생
  ```



### Int, Uint 

* Int : 정수형 타입
* Uint : 양의 정수형 타입 

```swift
// Int
var someInt: Int = -100
// someInt = 100.1 // 컴파일 오류발생

//UInt
var someUInt: UInt = 100
// someUInt = -100 // 컴파일 오류발생
// someUInt = someInt // 컴파일 오류발생
```



### Float, Double

* Float : 실수형 타입 32비트
* Double :  실수형 타입 64비트

```swift
// Float
var someFloat: Float = 3.14
someFloat = 3

// Double
var someDouble: Double = 3.14
someDouble = 3
// someDouble = someFloat // 컴파일 오류발생
```



### Character , String

* Character : 문자 타입, 큰따움표 사용

* Srting : 문자열 타입, 큰따움표 사용

  ```swift
  // Character
  var someCharacter: Character = "🇰🇷"
  someCharacter = "😄"
  someCharacter = "가"
  someCharacter = "A"
  // someCharacter = "하하하" // 컴파일 오류발생
  print(someCharacter)
  
  // String
  var someString: String = "하하하 😄 "
  someString = someString + "웃으면 복이와요"
  print(someString)
  
  // someString = someCharacter // 컴파일 오류발생
  ```

  

## **:: Any, AnyObject, nil ::**

* Any : Swift의 모든 타입을 지칭한느 키워드
* AnyObject : 모든 크래스 타입을 지칭하는 프로토콜
* nil : 없음을 의미하는 키워드 

### Any

* Swift의 모든 타입을 지칭하는 키워드

```swift
var someAny: Any = 100
someAny = "어떤 타입도 수용 가능합니다"
someAny = 123.12

// Any 타입에 Double 자료를 넣어두었더라도 Any는 Double 타입이 아니기 때문에 할당할 수 없습니다. 
// 명시적으로 타입을 변환해 주어야 합니다. (타입 변환은 차후에 다룹니다.)
let someDouble: Double = someAny  // 컴파일 오류발생
```

### AnyObject

* 모든 클래스 타입을 지칭하는 프로토콜

```swift
class SomeClass {}
var someAnyObject: AnyObject = SomeClass()

// AnyObject는 클래스의 인스턴스만 수용 가능하기 때문에 클래스의 인스턴스가 아니면 할당할 수 없습니다.
someAnyObject = 123.12    // 컴파일 오류발생
```



### nil

* 없음을 의미하는 키워드

  ```swift
  // someAny는 Any 타입이고, someAnyObject는 AnyObject 타입이기 때문에 nil을 할당할 수 없습니다.
  var someAny: Any = 100
  var someAnyObject: AnyObject = SomeClass()
  
  // nil을 다루는 방법은 옵셔널 파트에서 다룹니다.
  someAny = nil         // 컴파일 오류발생
  someAnyObject = nil   // 컴파일 오류발생
  ```

  

## :: 컬렉션 타입 ::

* Array : 순서가 있는 리스트 컬렉션
* Dictionary : 키와 벨류가 쌍으로 이루어진 컬렉션
* Set : 순서가 없고, 멤버가 유일한 컬렉션



### Array

* 멤버가 순서(인덱스)를 가진 리스트 형태의 컬렉션 타입

  ```swift
  // 1. Array 선언 및 생성
  var integers: Array<Int> = Array<Int>()
  
  // 위와 동일한 표현
  // var integers: Array<Int> = [Int]()
  // var integers: Array<Int> = []
  // var integers: [Int] = Array<Int>()
  // var integers: [Int] = [Int]()
  // var integers: [Int] = []
  // var integers = [Int]()
  
  
  // 2. Array 활용
  integers.append(1)
  integers.append(100)
  
  // Int 타입이 아니므로 Array에 추가할 수 없습니다
  //integers.append(101.1)
  
  print(integers)	// [1, 100]
  
  // 멤버 포함 여부 확인
  print(integers.contains(100)) // true
  print(integers.contains(99)) // false
  
  // 멤버 교체
  integers[0] = 99
  
  // 멤버 삭제
  integers.remove(at: 0)
  integers.removeLast()
  integers.removeAll()
  
  // 멤버 수 확인
  print(integers.count)
  
  // 인덱스를 벗어나 접근하려면 익셉션 런타임 오류발생
  //integers[0]
  
  
  // 3. 불변 Array: let을 사용하여 Array 선언
  let immutableArray = [1, 2, 3]
  
  // 수정이 불가능한 Array이므로 멤버를 추가하거나 삭제할 수 없습니다
  //immutableArray.append(4)
  //immutableArray.removeAll()
  ```

  

### Dictionary

* '키'와 '값'의 쌍으로 이루어진 컬렉션 타입

```swift
// 1. Dictionary의 선언과 생성
// Key가 String 타입이고 Value가 Any인 빈 Dictionary 생성
var anyDictionary: Dictionary<String, Any> = [String: Any]()

// 위와 동일한 표현
// var anyDictionary: Dictionary <String, Any> = Dictionary<String, Any>()
// var anyDictionary: Dictionary <String, Any> = [:]
// var anyDictionary: [String: Any] = Dictionary<String, Any>()
// var anyDictionary: [String: Any] = [String: Any]()
// var anyDictionary: [String: Any] = [:]
// var anyDictionary = [String: Any]()


// 2. Dictionary 활용
// 키에 해당하는 값 할당
anyDictionary["someKey"] = "value"
anyDictionary["anotherKey"] = 100

print(anyDictionary) // ["someKey": "value", "anotherKey": 100]

// 키에 해당하는 값 변경
anyDictionary["someKey"] = "dictionary"
print(anyDictionary) ["someKey": "dictionary", "anotherKey": 100]

// 키에 해당하는 값 제거
anyDictionary.removeValue(forKey: "anotherKey")
anyDictionary["someKey"] = nil
print(anyDictionary)


// 3. 불변 Dictionary: let을 사용하여 Dictionary 선언
let emptyDictionary: [String: String] = [:]
let initalizedDictionary: [String: String] = ["name": "yagom", "gender": "male"]

// 불변 Dictionary이므로 값 변경 불가
//emptyDictionary["key"] = "value"

// 키에 해당하는 값을 다른 변수나 상수에 할당하고자 할 때는 옵셔널과 타입 캐스팅 파트에서 다룹니다
// "name"이라는 키에 해당하는 값이 없을 수 있으므로 String 타입의 값이 나올 것이라는 보장이 없습니다.
// 컴파일 오류가 발생합니다
// let someValue: String = initalizedDictionary["name"]
```



### Set

* 중복되지 않는 멤버가 순서없이 존재하는 컬렉션

```swift
// 1. Set 생성 및 선언
var integerSet: Set<Int> = Set<Int>()

// insert : 새로운 멤버 입력
// 동일한 값은 여러번 insert해도 한번만 저장됩니다.
integerSet.insert(1)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(100)

print(intigerSet) // {100, 99, 1}

// contains: 멤버 포함 여부 확인
print(integerSet.contatins(1)) // true
print(integerSet.contains(2)) // false

// remove: 멤버 삭제
integerSet.remove(99) // {100, 1}
integerSet.removeFirst() // {1}

// count: 멤버 개수
integerSet.count // 1


// 2. Set의 활용
// 멤버의 유일성이 보장되기 때문에 집합 연산에 활용하면 유용합니다.
let setA: Set<Int> = [1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7]

// 합집합
let union: Set<Int> = setA.union(setB)
print(union) // [2, 4, 5, 6, 7, 3, 1]

// 합집합 오름차순 정렬
let sortedUnion: [Int] = union.sorted()
print(sortedUnion) // [1, 2, 3, 4, 5, 6, 7]

// 교집합
let intersection: Set<Int> = setA.intersection(setB)
print(intersection) // [5, 3, 4]

// 차집합
let subtracting: Set<Int> = setA.subtracting(setB)
print(subtracting) // [2, 1]
```



## :: 함수 기본 ::

### 1. 함수선언의 기본 형태

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

// 예)
// sum이라는 이름을 가지고 
// a와 b라는 Int 타입의 매개변수를 가지며 
// Int 타입의 값을 반환하는 함수
func sum(a: Int, b: Int) -> Int {
    return a + b
}
```



### 2. 반환 값이 없는 함수

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> Void {
    /* 함수 구현부 */
    return
}

// 예)
func printMyName(name: String) -> Void {
    print(name)
}

// 반환 값이 없는 경우, 반환 타입(Void)을 생략해 줄 수 있습니다
func printYourName(name: String) {
    print(name)
}
```



### 3. 매개변수가 없는 함수 

```swift
func 함수이름() -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

// 예)
func maximumIntegerValue() -> Int {
    return Int.max
}
```



### 4. **매개변수와 반환값이 없는 함수**

```swift
func 함수이름() -> Void {
    /* 함수 구현부 */
    return
}

// 함수 구현이 짧은 경우
// 가독성을 해치지 않는 범위에서
// 줄바꿈을 하지 않고 한 줄에 표현해도 무관합니다
func hello() -> Void { print("hello") }


// 반환 값이 없는 경우, 반환 타입(Void)을 생략해 줄 수 있습니다
func 함수이름() {
    /* 함수 구현부 */
    return
}

func bye() { print("bye") }

```



### 5. 함수 호출

```swift
sum(a: 3, b: 5) // 8

printMyName(name: "yagom") // yagom

printYourName(name: "hana") // hana

maximumIntegerValue() // Int의 최댓값

hello() // hello

bye() // bye
```





## :: 함수 고급 ::



### 1. 매개변수 기본 값 

* 매개변수에 기본적으로 전달될 값을 미리 정할 수 있다
* 기본값을 갖는 매개변수는 매개변수 목록 중 뒤쪽에 위치하는 것이 좋습니다.

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 = 매개변수 기본값 ...) -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

func greeting(friend: String, me: String = "yagom") {
    print("Hello \(friend)! I'm \(me)")
}

// 매개변수 기본값을 가지는 매개변수는 호출시 생략할 수 있습니다
greeting(friend: "hana") // Hello hana! I'm yagom
greeting(friend: "john", me: "eric") // Hello john! I'm eric
```



### 2. **전달인자 레이블(Argument Label)**

* 함수를 호출할 때 함수 사용자의 입장에서 매개변수의 역할을 좀 더 명확하게 표현하고자 할 때 사용합니다.
* 전달인자 레이블은 변경하여 동일한 이름의 함수를 중복으로 생성가능합니다.

```swift
func 함수이름(전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
    /* 함수 구현부 */
    return
}

// 함수 내부에서 전달인자를 사용할 때에는 매개변수 이름을 사용합니다
func greeting(to friend: String, from me: String) {
    print("Hello \(friend)! I'm \(me)")
}

// 함수를 호출할 때에는 전달인자 레이블을 사용해야 합니다
greeting(to: "hana", from: "yagom") // Hello hana! I'm yagom
```



### 3. 가변 매개변수

* 전달 받을 값의 개수를 알기 어려울 때 사용합니다.
* 가변 매개변수는 함수당 하나만 가질 수 있습니다.
* 기본값이 있는 매개변수와 같이 가변 매개변수 역시 매개변수 목록 중 뒤쪽에 위치하는 것이 좋습니다.

```swift
//func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
//    /* 함수 구현부 */
//    return
//}

func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}
print(sayHelloToFriends(me: "yagom", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm yagom!

print(sayHelloToFriends(me: "yagom"))
// Hello []! I'm yagom!
```



### 4.**데이터 타입으로서의 함수**

*  스위프트의 함수는 일급객체입니다. 그래서 함수를 변수, 상수 등에 할당이 가능하고 매개변수를 통해 전달할 수도 있습니다.
* **함수의 타입 표현** : 반환 타입을 생략할 수 없습니다.

```swift
(매개변수1타입, 매개변수2타입 ...) -> 반환타입

//함수타입 사용

var someFunction: (String, String) -> Void = greeting(to:from:)
someFunction("eric", "yagom") // Hello eric! I'm yagom

someFunction = greeting(friend:me:)
someFunction("eric", "yagom") // Hello eric! I'm yagom


// 타입이 다른 함수는 할당할 수 없습니다 - 컴파일 오류 발생
//someFunction = sayHelloToFriends(me: friends:)


func runAnother(function: (String, String) -> Void) {
    function("jenny", "mike")
}

// Hello jenny! I'm mike
runAnother(function: greeting(friend:me:))

// Hello jenny! I'm mike
runAnother(function: someFunction)
```



## :: 조건문 ::

* if~else
* switch



### 1. If~else

- **if-else 구문의 기본 형태** 
- if만 단독으로 사용해도되고, else, else if 와 조합해서 사용 가능합니다.
- if 뒤의 조건 값에는 Bool 타입의 값만 위치해야 합니다. 
- 조건을 감싸는 소괄호는 선택사항입니다.

```swift
if 조건 {
     /* 실행 구문 */
} else if 조건 {
    /* 실행 구문 */
} else {
    /* 실행 구문 */
}
```

* if~else의 활용

```swift
let someInteger = 100

if someInteger < 100 {
    print("100 미만")
} else if someInteger > 100 {
    print("100 초과")
} else {
    print("100")
} // 100

// 스위프트의 조건에는 항상 Bool 타입이 들어와야 합니다.
// someInteger는 Bool 타입이 아닌 Int 타입이기 때문에
// 컴파일 오류가 발생합니다.
//if someInteger { }
```



### 2. Switch

- 명시적 break를 하지 않아도 자동으로 case마다 break 됩니다.
- fallthrough 키워드를 사용하여 break를 무시할 수 있습니다.
- 쉼표(,)를 사용하여 하나의 case에 여러 패턴을 명시할 수 있습니다.

```swift
switch 비교값 {
case 패턴:
    /* 실행 구문 */
default:
    /* 실행 구문 */
}
```

* Switch문의 활용

```swift
// 범위 연산자를 활용하면 더욱 쉽고 유용합니다
switch someInteger {
case 0:
    print("zero")
case 1..<100:
    print("1~99")
case 100:
    print("100")
case 101...Int.max:
    print("over 100")
default:
    print("unknown")
} // 100

// 정수 외의 대부분의 기본 타입을 사용할 수 있습니다
switch "yagom" {
case "jake":
    print("jake")
case "mina":
    print("mina")
case "yagom":
    print("yagom!!")
default:
    print("unknown")
} // yagom!!
```



## :: 반복문 ::

- **for-in**
- **while**
- **repeat-while**



 ### 1.for~in 구문

- 기존 언어의 for-each 구문과 유사합니다.
- Dictionary의 경우 이터레이션 아이템으로 튜플이 들어옵니다. (하단 애플 문서의 튜플 부분 참조) 
- **for-in 구문 기본 형태**

```swift
for item in items {
    /* 실행 구문 */
}
```



* for~in 구문의 사용

```swift
var integers = [1, 2, 3]
let people = ["yagom": 10, "eric": 15, "mike": 12]

for integer in integers {
    print(integer)
}

// Dictionary의 item은 key와 value로 구성된 튜플 타입입니다
for (name, age) in people {
    print("\(name): \(age)")
}
```



### 2. while

* while의 기본 형태

  ```swift
  while integers.count > 1 {
      integers.removeLast()
  }
  ```



### **3. repeat-while 구문**

- 기존 언어의 do-while 구문과 형태/동작이 유사합니다.
- **repeat-while 구문의 기본 형태**

```swift
repeat {
    /* 실행 구문 */
} while 조건
```

- **repeat-while 구문의 사용**

```swift
repeat {
    integers.removeLast()
} while integers.count > 0
```



## :: 옵셔널 ::



### 1. 옵셔널이란? 

- 값이 있을 수도, 없을 수도 있음을 표현
- nil이 할당 될 수 있는지 없는지 표현

```swift
// someOptionalParm에 nil이 할당 될 수 있다.
func someFunction(someOptionalParam: Int?) {
       // ....
}

/// someOptionalParm에 nil이 할당 될 수 없다.
func someFunction(someOptionalParam: Int) {
       // ....
}

someFunction(someOptionalParam: nil)
// someFunction(someParam: nil) 
```



### 2. **옵셔널 문법과 선언**

- 옵셔널 문법 = enum + generics

- 옵셔널 선언

```swift
enum Optional<Wrapped>: ExpressibleByNiliteral {
         case none
         case some(Wrapped)
}

let optionalValue: Optional<Int> = nil
let optionalValue: Int? =nil
```



* 옵셔널 표현

  * 1. 느낌표(!)를 이용한 암시적 추출 옵셔널 

    ```swift
    // Implicitly Unwrapped Optional
    var implicitlyUnwrappedOptionalValue: Int! = 100
    
    switch implicitlyUnwrappedOptionalValue {
    case .none:
        print("This Optional variable is nil")
    case .some(let value):
        print("Value is \(value)")
    }
    
    // 기존 변수처럼 사용 가능
    implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1
    
    // nil 할당 가능
    implicitlyUnwrappedOptionalValue = nil
    
    // 잘못된 접근으로 인한 런타임 오류 발생
    //implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1
    ```

  *  \2. 물음표(?)를 이용한 옵셔널

  ```swift
  // Optional
  var optionalValue: Int? = 100
  
  switch optionalValue {
  case .none:
      print("This Optional variable is nil")
  case .some(let value):
      print("Value is \(value)")
  }
  
  // nil 할당 가능
  optionalValue = nil
  
  // 기존 변수처럼 사용불가 - 옵셔널과 일반 값은 다른 타입이므로 연산불가
  //optionalValue = optionalValue + 1
  ```

  

### 3.옵셔널 사용 이유

- **명시적 표현**
  - nil의 가능성을 코드만으로 표현가능
  - 문서/주석 작성 시간 절약

- **안전한 사용**
  - 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않고 사용가능
  - 예외 상황을 최소화 하는 안전한 코딩
  - 효율적 코딩



## :: 옵셔널 추출 ::

  ### **1. 옵셔널 추출이란?**

- 옵셔널에 들어있는 값을 사용하기 위해 꺼내오는 것



**2. 옵셔널 방식**

- **옵셔널 바인딩**

\1. nil 체크 + 안전한 추출
\2. 옵셔널 안에 값이 들어있는지 확인하고 값이 있으면 값을 꺼내옵니다.
\3. if-let 방식 사용

```swift
func printName(_ name: String) {
    print(name)
}

var myName: String? = nil

//printName(myName)
// 전달되는 값의 타입이 다르기 때문에 컴파일 오류발생

if let name: String = myName {
    printName(name)
} else {
    print("myName == nil")
}


var yourName: String! = nil

if let name: String = yourName {
    printName(name)
} else {
    print("yourName == nil")
}

// name 상수는 if-let 구문 내에서만 사용가능합니다
// 상수 사용범위를 벗어났기 때문에 컴파일 오류 발생
//printName(name)


// ,를 사용해 한 번에 여러 옵셔널을 바인딩 할 수 있습니다
// 모든 옵셔널에 값이 있을 때만 동작합니다
myName = "yagom"
yourName = nil

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)")
}
// yourName이 nil이기 때문에 실행되지 않습니다
yourName = "hana"

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)")
}
// yagom and hana
```



* **강체추출 :** 옵셔널에 값이 들어있는지 아닌지 확인하지 않고 강제로 값을 꺼내는 방식, 만약 값이 없을경우(nil) 런타임 오류가 발생하기 때문에 추천되지 않습니다.

```swift
var myName: String? = yagom
var youName: String! = nil


printName(myName!) // yagom
myName = nil

//print(myName!)
// 강제추출시 값이 없으므로 런타임 오류 발생
yourName = nil

//printName(yourName)
// nil 값이 전달되기 때문에 런타임 오류발생
```

