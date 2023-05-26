# 🍭🧋🍹JuiceMaker🧃🥛🍬

<Img src = "https://hackmd.io/_uploads/H12Bxv4Sn.png" width="700"/>


## 📖 목차

1. [소개](#1.)
2. [팀원](#2.)
3. [타임라인](#3.)
4. [다이어그램](#4.)
5. [실행 화면](#5.)
6. [트러블 슈팅](#6.)
7. [참고 링크](#7.)
8. [팀 회고](#8.)

<br>

<a id="1."></a>

## 1. 📢 소개

    사용자가 쥬스를 선택하면 과일 재고를 확인하고 
    쥬스 레시피에 따라 과일 재고를 소진하여 쥬스를 만들 수 있습니다.
    만약 과일의 재고가 부족한 경우, 혹은 과일 재고를 변경하고 싶은 경우
    과일 재고 변경 화면에서 변경이 가능합니다.

<br>

<a id="2."></a>

## 2. 🦊 팀원 🐷

| [Minsup 🦊](https://github.com/agilestarskim) | [Serena 🐷](https://github.com/serena0720) |
| :--------: | :--------: |
| <Img src = "https://avatars.githubusercontent.com/u/79740398?v=4" width="300"/>| <Img src = "https://i.imgur.com/q0XdY1F.jpg" width="300"/>|

<br>

<a id="3."></a>
## 3. ⏱️ 타임라인

|날짜|내용|
|:---:|---|
| **2023.05.09** |▫️ `FruiteStore` 재고 클래스 및 `JuiceMaker` 과일쥬스 클래스 정의 <br> ▫️ `Error` 케이스 정의 및 별도 파일 분리 <br> ▫️ `updateStock`, `checkStock` 함수 정의 <br> ▫️ `useValidStock` 함수 정의, 재고 확인 후 재고 업데이트 가능하게 수정 <br> ▫️ `useValidStock` 함수에 반복문 `foreach` 활용하여 반복 코드 제거 |
| **2023.05.10** | ▫️ `JuiceRecipe alias` 명명  <br> ▫️ `Errors` 폴더 생성 및 이름 변경 <br> ▫️ `enum rawValue`대신 계산 프로퍼티를 이용해 `name`으로 접근 | 
| **2023.05.11** | ▫️ `stock` 관련 `updateStock`, `spendStock` 으로 함수 분리 <br> ▫️ `FruitStock` 주입 및 기본값 설정 | 
| **2023.05.16** | ▫️ `Main`, `Stock ViewController` 생성, `error` 메세지 `alert` 구현 <br> ▫️ 네비게이션 `push`로 변경 <br> ▫️ 주문 버튼, 알럿 버튼 추가, 재고레이블 연결 <br> ▫️ 알럿 아니오 클릭 시 화면이동 <br> ▫️ `NotificationCenter`로 `Stock Label` 업데이트 구현 <br> ▫️ `error description` 구현 <br> ▫️ `onTouchOrderButton` 함수분리 <br> ▫️ `notification` 알람 시 `configurelabel` 재활용 | 
| **2023.05.17** | ▫️ `typecasting`제거, 스토리보드 ID변경 <br> ▫️ `StoryBoardable` 추가, `NavigationController` 한개 삭제 <br> ▫️ `NotificationCenter`에서 `Delegate`패턴으로 신호 전달 방법 변경 <br> ▫️ `onTouchorderButton`내부`switch`문 제거 <br> ▫️ 중복된 에러 처리 리팩토링 | 
| **2023.05.18** | ▫️ `delegate pattern`을 메소드로 수정 <br> ▫️ 타겟워드 삭제 메소드 변경 <br> ▫️ `Namespace` 생성, 터치메소드 이름 변경| 
| **2023.05.19** | ▫️ `Error` 종류 추가 <br> ▫️ `Error` 별 다른 얼럿 메세지 | 
| **2023.05.23** | ▫️ 오토 레이아웃 <br> ▫️ `StockViewController`에 `juiceMaker` 주입 |
| **2023.05.24** | ▫️ `stepper` 구현 <br> ▫️ `StockViewController`에 `custom init`추가 <br> ▫️ `Storyboardable` 삭제| 
| **2023.05.25** | ▫️ `delegate pattern`으로 업데이트된 재고 전달 | 
| **2023.05.26** | ▫️ `@available`을 통해 fatalError 런타임에러 방지| 

<br>

<a id="4."></a>
## 4. 📊 다이어그램

<Img src = "https://hackmd.io/_uploads/SyhDxATBn.png" width=100%/>
<Img src = "https://hackmd.io/_uploads/BkI0gApSn.png" width=100%/>



<br>

<a id="5."></a>
## 5. 📲 실행 화면
|쥬스 주문 화면|
|:---:|
|<Img src = "https://github.com/serena0720/ios-juice-maker/assets/79740398/80611c7c-7a58-4ebb-9062-8a81bcf1b1cd" width=100%>|

|재고 수정 화면|
|:---:|
|<Img src = "https://github.com/serena0720/ios-juice-maker/assets/79740398/49507512-63e9-45e8-8a0e-e455e572da18" width=100%>|



<br>

<a id="6."></a>
## 6. 🛎️ 트러블 슈팅

### 🔥 다중 역할의 함수 역할 분리

#### 문제상황
- `checkStock` 한가지 함수 안에서 재고 확인과 재고 업데이트 역할 2가지를 역할을 수행하였습니다. 한 함수 안에는 한가지의 역할을 수행해야 한다고 배웠기에 이를 분리해야겠다 생각했습니다.

#### 해결방법
- 재고 확인 함수 `checkStock`과 재고 업데이트 함수 `updateStock`으로 각각의 역할을 분배하였습니다.
- 두 함수를 호출하는 `useValidStock` 함수를 만들었습니다.
    
⚠️ 수정 전

```swift
private func updateStock(usedFruit: (fruit: Fruit, amount: Int)) { 
    guard let currentAmount = fruitStock[usedFruit.fruit],
        currentAmount < amount else { return }

    fruitStock[usedFruit.fruit] = currentAmount - usedFruit.amount   
}
```

✅ 수정 후

```swift
private func validateStock(ingredient: Ingredient) throws {
    let currentStock = getStock(fruit: ingredient.fruit)

    guard currentStock >= ingredient.amount else {
        throw FruitStoreError.notEnoughStock(ingredient.fruit)
    }
}

private func spendStock(of fruit: Fruit, by amount: Int) {
    self.fruitStock[fruit] = getStock(fruit: fruit) - amount
}
```
                                   


<br>

### 🔥 중복 코드 삭제 방법
    
#### 문제상황

```swift
switch juice {
...
case .mangoKiwiJuice:
    try fruitStore.checkStock(fruit: .mango, by: 2)
    try fruitStore.checkStock(fruit: .kiwi, by: 1)
    fruitStore.updateStock(fruit: .mango, amount: 2)
    fruitStore.updateStock(fruit: .kiwi, amount: 1)
...
```
    
- `JuiceMaker`에서 쥬스를 만들 때, 재고 확인 및 재고 업데이트 함수(위 코드 참조)를 케이스별로 호출해야했습니다.
- 특히 망고키위쥬스와 같이 과일의 종류가 2가지인 경우 각 과일별로 함수들을 호출해야했기 때문에 중복 함수가 많다고 생각했습니다.
    
#### 해결방법

- `Juice` 타입에서 `recipe` 계산 프로퍼티를 사용해 레시피를 반환해줍니다.
- `FruitStore`에서 유효성검증과 재고소모 함수를 묶어 `useValidStock`을 생성했습니다.
- `makeJuice`에서 `useValidStock`을 호출해 `recipe`를 받아 코드를 획기적으로 줄였습니다.

⚠️ 수정 전
        
```swift
func makeJuice(juice: Juice) {
    do {
        switch juice {
        ...
        case .mangoKiwiJuice:
            try fruitStore.checkStock(fruit: .mango, by: 2)
            try fruitStore.checkStock(fruit: .kiwi, by: 1)
            fruitStore.updateStock(fruit: .mango, amount: 2)
            fruitStore.updateStock(fruit: .kiwi, amount: 1)
        }
        ...    
    } catch {
        
    }
}    
```
    
 ✅ 수정 후
        
```swift
func makeJuice(juice: Juice) {
    do {
        try fruitStore.useValidStock(recipe: juice.recipe)
    } catch {
        ...
    }
}    
```
 
<br>

### 🔥 여러 과일이 필요한 쥬스에서 에러 시 되돌리는 방법

#### 문제상황
- 딸바쥬스의 경우 딸기의 재고와 바나나의 재고를 둘다 확인한 다음, 재고가 있다면 필요한 만큼 재고를 빼는 방식의 로직을 사용하고 있습니다.
- 하지만 딸기는 재고가 충분한데 바나나의 재고가 없다면 딸기는 이미 재고가 업데이트 되었기 때문에 다시 되돌리는 과정이 필요했습니다.

#### 해결방법
- 따라서 `for`문 안에서 두 함수를 동시에 부르는 것이 아닌 첫번째 `for`문에서 검증을 다 마친 뒤, 두 번째 `for`문에서 재고를 업데이트 하는 것으로 해결했습니다.
- 또한 `for`에서 `forEach`로 수정하여 축약 표현($)을 사용했습니다.

⚠️ 수정 전
    
```swift
func useValidStock(juiceRecipe: Recipe) throws {  
    try juiceRecipe.forEach { 
        try validateStock(ingredient: $0) 
        spendStock(of: $0.fruit, by: $0.amount)
    }
}
```

✅ 수정 후
    
```swift
func useValidStock(juiceRecipe: Recipe) throws {
    try juiceRecipe.forEach { try validateStock(ingredient: $0) }
    juiceRecipe.forEach { spendStock(of: $0.fruit, by: $0.amount)}
}
```
        
### 🔥 instantiateViewController 재사용

#### 문제상황
- 스토리보드에서 `viewController`를 가져오기 위해 `instantiateViewController(withIdentifier:)` 메소드를 호출합니다.
- 하지만 다운캐스팅과 옵셔널 언래핑을 해줘야하고 여러 곳에서 호출되기 때문에 재사용성에 대해 고민하였습니다.

#### 해결방법
- 프로토콜과 `extension`을 사용한 기본구현을 통해 "Main" 스토리보드에서 `id`를 통해 `viewController`를 가져오는 `static function`을 구현했습니다.
- 참고자료: 하단 참조

⚠️ 수정 전
    
```swift
@IBAction func tapStockButton(_ sender: UIBarButtonItem) {
    if let StockViewController = self.storyboard?.instantiateViewController(identifier: "StockViewController") {
        self.navigationController?.present(StockViewController, animated: true)
    }
}
```

✅ 수정 후
    
```swift
@IBAction func tapStockButton(_ sender: UIBarButtonItem) {
    let stockViewController = StockViewController.instantiate()
    self.navigationController?.present(stockViewController, animated: true)
}
```

### 🔥 fruitStock 변경 시 MainViewController에서 신호 전달 받는 법

#### 문제상황
- 처음엔 `fruitStock`이 `didSet` 될 때 마다 `Notification.post`하고 `MainViewController`에서 수신하는 방식을 사용해 `view`를 업데이트 하였습니다.
- 좋은 방식이긴 하였으나 `Delegate` 패턴을 적용해보고 싶어 리팩토링을 하였습니다. 당시 `Delegate`를 사용해야하는 명확한 이유는 없었다는게 오점이였습니다.

#### 해결방법
- `JuiceMaker`에 `FruitStore`의 재고를 가져오는 함수가 있고 `MainViewController`에서 언제 레이블을 업데이트 해야하는지도 명확히 알고 있기 때문에 `Delegate`, `Notification` 을 사용하는 것보다 그냥 `JuiceMaker`의 `getStock`을 호출하여 `view`를 업데이트 하였습니다.

### 🔥 매직넘버 리터럴

#### 문제상황
- "맛있게 드세요" 등 문자열을 코드에서 그대로 사용하고 있어 유지보수에 어려움을 느꼈습니다.

#### 해결방법
- Namespace를 사용하여 문자열 추적 관리가 용이해졌습니다.

### 🔥 객체 간 결합도 낮추기

#### 문제상황
- `MainVC`와 `StockVC`가 `JuiceMaker`를 주입하면서 결합도가 높아졌습니다.
- `JuiceMaker`를 수정하면 두 `VC` 모두 수정해야하고 예기치 못한 부작용이 발생할 수 있습니다.

#### 해결방법
- `StockVC`가 정말로 `JuiceMaker` 객체가 필요한지 고민을 해보았습니다.
- 초기 `label.text`는 MainVC에서 `FruitStock`만 전달받아 초기화하면 되고, 마지막 최종 업데이트는 `MainVC`가 해도 되었기때문에 `JuiceMaker`객체가 필요없다고 판단하여 삭제했습니다. 
- 최종 업데이트를 `MainVC`가 하기 위해 `Delegate` 패턴을 이용해 파라미터로 변경된 재고를 보내주었고 이로써 결합도를 낮출 수 있게 되었습니다.

### 🔥 StockVC custom init 만들기

#### 문제상황
- `MainVC`에서 `StockVC`로 인스턴스를 전달하고자 할 때, 주입받는 `StockVC`에서 새롭게 `init`을 통해 초기화를 해야합니다. 이때 `StockVC`가 상속받는 `UIViewController`에 기본적으로 제공되는 `required init`을 덮어 쓰기 때문에 `required init`을 새롭게 다시 정의해야합니다. 하지만 이때 새로 정의한 `init`이 아닌 `required init`을 타게되면 `fatalError`가 나게 됩니다.
- 또한 새로운 `init`을 정의했기 때문에 `.instantiateViewController`를 사용할 수 없게 되었습니다.

#### 해결방법
- `custom init`을 만들게 되면 `.instantiateViewController`의 `creator` 파라미터를 받는 메소드를 사용해야합니다.
```swift
.instantiateViewController(
    identifier: String(describing: StockViewController.self),
    creator: { coder in
        StockViewController(currentFruitStock: self.juiceMaker.getAllStock(), coder: coder)
    }
)
```

- 하지만 init 메소드가 2개이기 때문에 개발자가 실수로 required init으로 접근할 수 있습니다.
- 이때 `@available(*, unavailable)`을 사용하면 해당 기능을 사용할 수 없게 강제할 수 있습니다. 따라서 개발자가 실수로 `required init?`으로 생성하면 내부의 `fatalError`를 실행하지 못하도록 컴파일 에러를 발생시킬 수 있습니다.

```swift
@available(*, unavailable)
required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
}
```

<br>


<a id="7."></a> 
## 7. 🔗 참고 링크
- [🍎Apple Docs: UIViewController](https://developer.apple.com/documentation/uikit/uiviewcontroller)
- [🍎Apple Docs: Initialization](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/initialization/#Required-Initializers)
- [🍎Apple Docs: instantiateViewController(identifier:creator:)](https://developer.apple.com/documentation/uikit/uistoryboard/3213989-instantiateviewcontroller)
- [📘Blog: Delegate, Notification, KVO 비교 및 장단점 정리](https://you9010.tistory.com/275#:~:text=key%20값으로%20Notification의,정보를%20받을%20수%20없음.)
- [📘Blog: Instantiating View Controllers From a Storyboard](https://cocoacasts.com/mastering-navigation-with-coordinators-instantiating-view-controllers-from-a-storyboard)
- [📘Blog: Instantiate and Present a viewController in Swift](https://stackoverflow.com/questions/24035984/instantiate-and-present-a-viewcontroller-in-swift)
- [📘Blog: @available(*, unavailable) 사용하여 비가용성 정의](https://dev-dmsgk.tistory.com/47)
- [📘Blog: UML Class Diagram with Swift](https://zdodev.github.io/uml/swift/UML-Class-Diagram/)
- [📘Blog: Storyboard instantiate](https://cocoacasts.com/mastering-navigation-with-coordinators-instantiating-view-controllers-from-a-storyboard)
- [📘Blog: Attributes](https://xho95.github.io/swift/language/grammar/attribute/2020/08/14/Attributes.html)

<br>

<a id="8."></a>
## 8. 👥 팀 회고
### 👏🏻 우리팀이 잘한 점
- 코드에 대한 열정으로 배열, 딕셔너리, 튜플을 활용하여 효율적이고 가독성 높은 코드를 짰습니다.
- 서로 코드에 대해 질문하고 대답하면서 같이 성장해 나가는 것이 눈에 보였습니다.
- 코드를 짜는 것에만 집중하는 것이 아니라 팀원 간에 성향을 먼저 맞추고 배려를 먼저 생각하였습니다.
        
### 👊🏻 우리팀 개선할 점
- 처음엔 생각을 설명하는 방법이 미숙해 오해를 했지만 점점 의사소통하는 법에 익숙해지고 있습니다.
- 컨디션 관리에 좀 더 신경을 써야겠다고 생각했습니다🥲

### 💜 서로에게 좋았던 점 피드백
- Dear. Minsup 🦊 
    - 시간 약속을 잘 지킵니다.
    - 코드에 대한 이해가 높아 모르는 부분에 설명을 잘 해 줬습니다.
    - 코드 공부에 대한 열정이 높습니다!
    - 시간 조율이 원활했습니다.
    
- Dear. Serena 🐷
    - 시간 약속을 잘 지킵니다.
    - 배움의 의욕이 높고 깨달았을 때 응용력이 좋습니다.
    - 배려와 양보를 잘 해주었습니다.
    - 리액션이 좋고 사람을 편안하게 해줍니다.
    - 디자인의 감각이 뛰어납니다.
