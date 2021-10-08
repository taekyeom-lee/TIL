### commit f2b8526fb57a9d4109f96a0ab86deb608ef54626
---

## 해결

NextButton, PrevButton 누르면 그다음 페이지 콘텐츠들을 전달하기

---

우선 RowContainer Component에서

HandlePrev, HadleNext을 width: 60px 적용한다.

그후 background: rgba(20, 20, 20, .5)을 사용하여 살짝 드러나는 Item을 어둡게 만든다.

<br/>

기존의 Slider로 넘길 데이터는 6개씩 나눠서 page에 따라서 보내주었다. 

새로운 방식으로는 Infinity scroll 효과? 를 보여주기위해 모든 데이터를 Slider로 보내준다

하지만 이렇게되면 y축 스크롤이 엄청 길어진다(완성하고 알게됨) <span style="color:	lightcoral">← 해결할것</span>

<br/>

Slider Component를 보기전에 SliderItem Component로 

SliderItem padding: 0 2px; 적용한다.

map에서 주어지고 Slider로 전달받은 index 값으로 

첫번째는 padding-right:2px; 마지막꺼는 padding-left: 2px; 하려고 했지만 실패했다. <span style="color:	lightcoral">← 해결할것</span>

<br/>

그후 1903이라는 width 전체 길이를 사용해 

(100%는 사용하지 못한다. 데이터가 아주 길기 때문이다 6 * 7 = 42개)

Slider여백 60+60, SliderItem 여백 (2+2) * 6

1903-120-24=1759

1759/6=293.166666

약 293, SliderItem TitleCard width: 293px;로 적용한다.

<br/>

Slider Component로 가서 pageNumber를 전달받아

transform: translateX()를 사용하여 각 페이지에 해당하는 Item을 전달 시켜준다.

transition: transform을 사용하여 동작을 스무스하게 보여준다.

<br/>

PreviewModal Component에서

전달 받은 index를 index % 6을 하여 해당하는 case에 따라 transform하여 PreviewModal을 화면에 띄어준다.

page 1을 적용이 잘되지만 page 2부터는 적용이 안된다 <span style="color:	lightcoral">← 해결할것</span>

<br/>

## 해결할 문제

하지만 이렇게되면 y축 스크롤이 엄청 길어진다(완성하고 알게됨) <span style="color:	lightcoral">← 해결할것</span>

첫번째는 padding-right:2px; 마지막꺼는 padding-left: 2px; 하려고 했지만 실패했다. <span style="color:	lightcoral">← 해결할것</span>

page 1을 적용이 잘되지만 page 2부터는 적용이 안된다 <span style="color:	lightcoral">← 해결할것</span>

HandlePrev, HadleNext 쪽에 살짝 드러나는 사진 hover 작용 못하게 만들기 ← 해결할것

PreviewModal이 나타날때 왼쪽 Item과의 z-index 영향을 받지않는다(not working) ← 해결할것

사진이 무거워서 렌더링될때 속도가 오래걸린다 ← 해결할것