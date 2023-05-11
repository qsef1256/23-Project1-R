# 602377121 전정환

## 2023-05-11

### 열 쓰기

```r
data$column
```

### 두 변수의 상관관계

* 상관계수: 상관 관계를 수치로 나타낸 -1에서 1의 값
  * `0` 인 경우, X, Y 사이는 상관성을 찾기 어려움
  * `+` 인 경우 X, Y가 반비례, 음의 상관 관계
  * `-` 인 경우 X, Y가 비례, 양의 상관 관계

* 함수: `cor()`
* 상관관계 != 인과관계

```r
plot(pressure$temperature,
    pressure$pressure,
    main = '온도와 기압',
    xlab = '온도(화씨)',
    ylab = '기압')
```

### 여러 변수의 상관관계

```r
st = data.frame(state.x77)

head(st)
plot(st)
cor(st)
```

### 데이터 전처리

- 확보한 데이터를 가공하여 분석에 적합한 형태로 만드는 과정
- 현실에서는 정리된 데이터 셋을 바로 얻는 경우가 많지 않음

### 결측값의 처리

- 결측값: 수집되지 않았거나 잘못 측정된 값 (NA로 표현)
- 처리 방법: 

1. 제거/제외

```r
z = c(1,2,3,NA,5,NA,8)

sum(z)             # 오류
is.na(z)           # NA 여부 확인
sum(is.na(z))      # NA 개수 확인
sum(z, na.rm=TRUE) # NA 삭제 후 sum
```

2. 추정/치환

```r
z1 = c(1,2,3,NA,5,NA,8)
z2 = c(5,8,3,NA,3,NA,7)

z1[is.na(z1)] = 0           # NA를 0으로 치환
z3 = as.vector(na.omit(z2)) # NA를 제거하고 새로운 벡터를 생성
```

```r
for (i in 1:ncol(x)) {
    this.na = is.na(x, [i])
    cat(colnames(x)[i], '\t', sum(this.na), '\n')
}
```

```r
rowSums(is.na(x))
sum(rowSums(is.na(x)) > 0)
sum(is.na(x))
```

## 2023-05-04

### 선 그래프

```r
month = 1:12
late = c(5,8,7,9,4,6,12,13,8,6,6,4)
late2 = c(5,7,4,3,5,2,6,6,3,5,2,3)
plot(month, # x data
    late, # y data
    main='지각생 통계',
    type='l', # 그래프 종류
    lty=1, # 선 종류
    lwd=1, # 선 굵기
    xlab'Month',
    ylab='Late cnt')
lines(month, late2, type='b',col='blue')
```

### 상자 그림

```r
dist = cars[,2]
boxplot(dist, main='자동차 제동거리')
```

### 산점도

```r
wt = mtcars$wt
mpg = mtcars$mpg
plot(wt, mpg, 
    main='중량-연비 그래프',
    xlab='중량',
    ylab='연비',
    col='red',
    pch=19)
```

* 다중 산점도

```r
vars = c('mpg','disp','draw','wt')
target = mtcars[,cars]
head(target)
plot(target, main='Multi plots')
```


```r
iris.2 = iris[,3:4]
levels(iris$Species)
group = as.numeric(iris$Species)
color = c('red','green','blue')
plot(iris.2,
    main = 'iris plot',
    pch=c(group),
    col=color[group])
```

### 데이터 분석의 절차

1. 문제 정의 및 계획
2. 데이터 수집
3. 데이터 정제 및 전처리
4. 데이터 탐색
5. 데이터 분석
6. 결과 보고

### 분석 도구

* 단일 변수: 1개의 변수
  - 도수분포표
  - 막대그래프
  - 원그래프
  - 히스토그램
  - 선그래프
  - 상자 그림

* 다중 변수: 2개 이상의 변수
  - 매트릭스
  - 데이터 프레임
  - 산점도
  - 상관계수
  - 나무지도
  - 방사형차트

## 2023-04-27

### 막대 그래프

```r
favorite = c('winter', 'summer', 'spring', 'fall')
ds <- table(favorite)
barplot(ds, main = 'Favorite Season', col = 'blue', names=c('가을','봄','겨울','여름'), las=3)
```

```r
age.A = c(13709,10974,7879,5000,4250)
age.B = c(13709,10974,7879,5000,4250)
age.C = c(13709,10974,7879,5000,4250)
ds = rbind(age.A, age.B, age.C)
colnames(ds) = c('1970','1990','2010','2030','2050')
ds

barplot(ds, main='인구 추정')
```

### 히스토그램

```r
head(cars)
dist = cars[,2]
hist(dist, name = 'cars')

hist(iris.Sepal.Lengh,main='Sepal.length',col='orange')

pie(table(mtcars$cy1), main'mtcars', col=topo.colors(3), radius=2)
par(mfrow=c(1,1), mar=c(5,4,4,3)+1) # 화면 분할
```

### 그래프

```r
install.packages('plotrix')

pie3D(ds, main="선호 계절", col = c('brown','green','red','yellow'), radius=1)
```

## 2023-04-13

### 파일 입출력

```r
sink('result.txt', append = T) # 파일로 입력 시작
sink()                         # 파일로 입력 중지
```

```r
read.table('data.txt', header = T, sep = ' ')
```

### 조건문

```r
job.type = 'A'
if (job.type == 'B') {
    bonus = 200
} else {
    bonus = 100
}
print(bonus)
```

```r
ifelse(a>b, a, b)
```

```r
which(score==69)
which(score>=85)
which.min(score)
```

### 반복문

```r
sum = 0
for (i in 1:100) {
    sum = sum + i
}
print(sum)
```

```r
while(T) {
    print('infinity')
}
```

### apply

```r
apply(iris[,1:4], 1, mean) # 행 방향으로 함수 적용
apply(iris[,1:4], 2, mean) # 열 방향으로 함수 적용
```

### 함수

```r
source('ss.R')

myfunc = function(x, y) {
    val.sum = x + y
    val.mul = x * y
    return (list(val.sum, val.mul))
}
```

## 2023-04-06

### 매트릭스

#### 생성

```r
score = matrix(c(90,85,60,78,60,55,23,13,55,78,99,40), nrow=4)
matrix(1:20,4,5)
rownames(score) = c("John", "Doe", "Mark", "Jame")
colnames(score) = c("English", "Math", "Science")
colnames(score)[2]
```

#### 기본 정보 보기

```r
dim(score) : 행과 열의 개수 보이기
head(score) : 앞부분 일부 보기
tail(score) : 뒷부분 일부 보기
```

#### 합계 및 평균

```r
colSums(iris[,-5])
colMeans(iris[,-5])
rowSums(iris[,-5])
rowMeans(iris[,-5])
```

#### 값 추출

```r
IR.1 = subset(iris, Species="setosa")
```

#### 구조 확인

```r
class(iris)
is.matrix(iris)
is.data.frame(iris)
```

#### 구조 변환

```r
data.frame(iris)
as.martix(iris[,1:4])
```

#### 출력

```r
print(iris)
cat(x, '\n')
```

### 데이터셋
* iris 셋: 붗꽃 샘플 데이터

### 파일 입출력

#### csv

```r
getwd() : 작업 폴더 알아내기
setwd('C:\RWorks') 작업 폴더 설정하기
air = read.csv('airquality.csv', header = T)
```

#### xlsx

```r
read.xlsx("air.xlsx", header = T, sheetIndex = 1)
```

## 2023-03-30

### 함수

 * `ls()`: 변수 목록 확인하기
 * `rm(foobar)`: 변수 지우기
 * `range()`: 벡터 범위 구하기
 * `length()`: 벡터 길이 구하기
 * `sum()`: 합
 * `factor(벡터)`: 따옴표 trim

### 자료 구조

* 리스트
* 데이터 프레임
* 범주형 자료: 문자열 등, 산술 연산 불가
* 수치형 자료: 산술 연산 가능

벡터끼리 산술 연산이 가능

### 연산자

JS와 비슷하다.

### 리스트

1차원 배열. 벡터는 여러개의 자료형을 저장할 수 없으나 리스트는 가능. 리스트 안에 벡터를 넣을 수 있음

```r
list(name='Tom', age='25', student='TRUE')
```

### 매트릭스, 데이터 프레임

2차원 배열. 매트릭스는 한가지 자료형만 저장할 수 있으나 데이터 프레임은 서로 다른 종류의 데이터 저장이 가능함.

* 매트릭스

```r
value <- matrix(1:20, nrow=4, ncol=5)
```

* cbind, rbind

값 추출은 파이썬 방식과 비슷

## 2023-03-23

### 패키지 설치하기

다른 언어에서의 라이브러리와 동일

* 설치하기
```r
install.packages("package name") 
```
* 사용하기
```r
library(package name)
```
* 패키지 설치 전 패키지 목록 (Packages) 에서 이미 설치되어 있는지 확인할 것

### 도움말

함수 이름 앞에 ? 를 붙여서 실행하면 도움말이 나온다.

예: `?max()`

### 유용한 함수 및 패키지

* `sys.time()`: 현재 시간을 불러옴
* `log(x = 100, base = 10)`: 로그 함수 (기본 밑 e)
* `print("value")`: 출력
* `cat("a", "b")`: 합치기
* `mean(values)`: 산술 평균

### 산술 연산

* 대입: `a <- 10`
* 호출: `a`

### 변수명 작명 규칙

* 첫 글자는 영문이나 마침표로 시작, 영문자 일반적
* 두번째 부터는 영문자, 숫자, 마침표, 밀줄(_) 사용 가능
* 변수명에서 대문자와 소문자는 별개의 문자 취급
* 변수명 중간에 빈 칸을 넣을 수 없음

### 자료형

* 숫자형: 1,2,3,10,-4 (실수 포함)
* 문자형: `"문자"`
* 논리형: `TRUE`, `FALSE`

#### 특수값

* `NULL`: 정의 되어 있지 않음
* `NA`: 결측값 
* `NaN`: 수학적 정의 불가
* `Inf`, `-Inf`: 무한대

### 벡터

타 언어의 배열 같은 역할, 변수에는 하나의 값만이 들어감. 방향과 길이를 가진 그 벡터와 헷갈리지 않도록 주의할 것

* 문법: `c(값들)`, `시작:끝` (range)
* 예시: `score <- c(68, 29, 15, 95, 93, 83, 50:65)`
* 각 자료형 별의 벡터를 만들 수 있다.

#### 함수

* `sep(시작,끝,간격)`: Py range와 비슷
* `rep(반복할 것, times=횟수)`: 반복문
* `rep(반복할 벡터, each=횟수)`: 벡터용 반복문
* `names(벡터)`: 변수 이름 출력
* `paste(a, b, sep='delimeter')`: a + b 해서 새로운 벡터에 저장

#### 인덱스

* 인덱스 시작이 **1** 이다.
* 문법: `이름[인덱스]`
* 예: `v1[2] <- 3`

## 2023-03-16

### R 언어의 특징

#### 주요 특징
* 다양한 패키지 제공
* 데이터 분석에 사용되는 함수들을 종류별로 묶어 패키지 형태로 제공

#### 통계 그래프
* 그래프 기능을 제공함

#### 편리한 환경
* `R Studio` 제공 (IDE)

#### 플랫폼
* Windows, Mac, Linux
* 무료

#### 배우는 이유
* 데이터 처리

### R Studio

* 전체 영역을 4등분함

1. 소스 영역: 소스를 입력할 수 있는 영역
2. 환경 영역: R 명령문이 실행되는 동안 만들어지는 변수나 자료 구조를 보여주는 영역
3. 콘솔 영역: 자바스크립트 콘솔 처럼 직접 명령문을 입력할 수 있는 구역
4. 파일 영역: 윈도우의 파일 탐색기와 동일한 역할을 하는 영역

### R 문법

#### 연산자

* `+` : 더하기
* `-` : 빼기
* `*` : 곱하기
* `/` : 나누기
* `%%` : 나머지
* `^` : 제곱

#### 주석

`#` 뒤에 기록

#### 함수

* `max()`
* `min()`
등 다양한 함수 존재

### R 패키지

다른 언어에서 라이브러리와 동일