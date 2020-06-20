---

typora-copy-images-to: images
---

# 200519 | Teachable Machine Test

## Introduction

 각각의 동작의 바른 자세와 나쁜 자세를 모두 학습 시켜, 동작 순서 알고리즘 구현 전 자세를 정확하게 구분하는지 테스트해보았다.

 정확한 동작을 위하여, 전문가 영상 mp4를 Open CV를 이용하여 프레임 별로 나누어 jpg 파일로 저장하여 Teachable Machine에 업로드하여 학습하였다. 올바른 스쿼트자 세인 Stand 와 Squat Class를 학습 시키고, 올바르지 않은 Bad 자세 4가지 Class를 학습시켜, 총 6개의 Class를 학습하였다.



## Method

### Class

#### Class 1: Stand

76 poses Samples, 2 people

![다운로드](./images/다운로드.png) ![stand](./images/다운로드 (1).png)![stand3](./images/다운로드 (2).png)



#### Class 2: Squat

31 Pose Samples, 1 person

![squat2](./images/다운로드 (4).png)![squat](./images/다운로드 (3).png)



#### Class 3: Bad 1

57 Pose Samples, 1 Person

![bad1-3](./images/다운로드 (7).png)![bad1-2](./images/다운로드 (6).png)![bad](./images/다운로드 (5)-1589859261794.png)



#### Class 4: Bad 2

173 Pose Samples, 1 Person

<img src="./images/다운로드 (8).png" alt="bad2-1" style="zoom:80%;" /><img src="./images/다운로드 (11).png" alt="bad2-2" /><img src="./images/다운로드 (8).png" alt="bad2-1" style="zoom:80%;" /><img src="./images/다운로드 (11).png" alt="bad2-2" /><img src="./images/다운로드 (11).png" alt="bad2-2" style="zoom:80%;" />![bad2-4](./images/다운로드 (9).png)<img src="./images/다운로드 (11).png" alt="bad2-2" style="zoom:80%;" />![bad2-4](./images/다운로드 (9).png)



#### Class 5: Bad 3

 94 Pose Samples, 1 Person

![bad3-1](./images/다운로드 (14).png)![bad3-2](./images/다운로드 (13).png)![bad3-3](./images/다운로드 (12).png)



#### Class 6: Bad 4

73 Pose Samples, 1 Person

![bad4-1](./images/다운로드 (17).png)![bad4-2](./images/다운로드 (16).png)![bad4-3](./images/다운로드 (15).png)





## Result

- Class 1 ~ 3 까지는 잘 구분됨

- Class 4 ~6 은 잘 구분되지 않고, Class 1 ~ 3 과 겹쳐서 반응함.

  < 원인 분석 >

  - Class 4(Bad 2) 의 경우 허리가 위쪽으로 굽어지는 잘못된 동작으로, 각 프레임 사진마다 인식되는 Pose estimation 이 끊기는 경우가 발생됨. 끊기지 않는 경우라 하더라도, Side 면에서 인식된 형상이 Class 3(Bad 1) 과 비슷하여 구분되지 않은 것으로 예상됨.
  - Class 5(Bad 3)와 Class 6(Bad 4)의 경우에도, 사람의 인식에서는 잘못된 동작으로 구분이 가능하지만, 기계가 인식한 형상은 각각 Class 2의 올바른 Squat 자세와 Class 1의 올바른 Stand 자세와 비슷하게 인식되기 때문에 구분이 되지 않음.

  

## Conclusion

- 사람의 인식과 기계의 인식이 다름을 인지하고, 각 동작 인식 및 순서 알고리즘을 설계해야함.

- 잘못된 자세의 범위를 어떻게 인식하고 구분할 것인지에 대한 고민이 필요함.