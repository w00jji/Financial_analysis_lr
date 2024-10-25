# Financial_analysis_lr

### 다운샘플링(분기별,주별) 축약해서 보는 방법
- 년도와,월을 추출하여 그룹핑
- how 변수에 보고싶은 집계 값 설정 -> agg 함수 사용해서 추출

- 월별로 보고싶으면
  - df.groupby(pd.Grouper(key = '일자',freq = 'm')).agg(how)
- 주별로 보고싶으면
  - df.groupby(pd.Grouper(key = '일자',freq = 'w')).agg(how)
 

### 간단한 모멘텀 전략 : 자산이 오르는 추세에 있으면 그 추세를 유지하려는 경향이 있다
**과거 6일 전의 종가 대비 당일 종가가 3%이상 높다면 상승장으로 판단**
- 별로 좋은 결과는 안나온다.


### 이동 평규선 투자 전략
- 사용함수
  - rolling(window = 3).mean()
- 시가(Open)가 5일 이동 평균선을 돌파하면 상승 추세라고 판단하고 참여
  - df['MA5'] = df['종가'].rolling(window =5).mean()
  - cond = df['MA5']<df['종가']


### 각 종목당 비교하기 쉽게 만들고 시각화
- 예시
  - samsung_index = samsung['Close'] / samsung['Close'][0]*100
  - 시각화
    -plt.plot(samsung.index,samsung_index)
    - plt.plot(sk.index,sk_index)
    - plt.legend(['samsung','sk'])
    - plt.grid()
    - plt.show()
   

### 캔들 차트
- 필요 라이브러리 : mplfinace
- 사용기법
  - 이동평균선
  - 볼린져 밴드 



 
