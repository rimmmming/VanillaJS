##  Function

모든 함수는 Function타입의 인스턴스이며 다른 참조 타입과 마찬가지로 프로퍼티와 메서드가 있다.

### 함수 선언 vs 함수 표현식

함수 선언식으로 선언 했을 경우
- 코드 실행전에 '함수 선언 호이스팅'이란 과정을 통해 실행 컨텍스트에 추가
- 자바스크립트 엔진은 코드를 평가할 때 제일 먼저 함수 선언을 찾은 다음 맨위로 올림

```
함수 선언
function sum(num1, num2){
    return num1 + num2;
}

함수 표현식
var sum = function(num1, num2){
    return num1 + num2;
}
```

### 값처럼 쓰는 함수

함수를 다른 함수에 매개변수로 넘기거나, 함수가 실행 결과로 다른 함수를 반환하는 일이 가능함.

```
function callfunc(some, arg){
    some(arg)
}

function add10(num){
    return num + 10
}

function callfunc(add10, 10) // 20

```

### 함수의 내부구조

- arguments (배열과 비슷한 객체, 함수에 전달된 매개변수를 모두 포함)
- this (this객체가 실행중인 컨텍스트 객체에 대한 참조)

```
window.color = 'red';
var o = {color : 'blue};

function sayColor(){
    alert(this.color);
}

sayColor(); // "red"  전역스코프에서 호출하여 window를 가리킴

o.sayColor = sayColor; 
o.sayColor(); // "blue" 함수를 객체 o의 메서드로 할당한 다음 호출 하였으므로 객체 o를 가리킴 
```

** 함수 이름은 단순히 포인터를 저장한 변수 일 뿐!!! sayColor()와 o.sayColor()는 같은 함수를 가리키지만 다른 컨텍스트에서 실행함