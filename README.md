# QKULDA(Q-Kernel Optimized UMAP Linear Discriminant Analysis)

## Introduction
QKULDA(Q-Kernel Optimized UMAP Linear Discriminant Analysis)는 고차원 데이터의 분류 성능을 극대화하기 위해 새롭게 제안된 방법론입니다. 기존 LDA의 한계를 극복하기 위해 Kernel LDA와 UMAP을 결합하고, Q 최적화를 통해 커널 파라미터를 최적화하여 정확도를 향상시킵니다.

### 주요 특징
- **Kernel LDA 도입**: 비선형 데이터도 효과적으로 분류 가능
- **Q 최적화**: 커널 함수 파라미터 최적화를 통해 등분산성 가정 완화 및 클래스 간 분리 극대화
- **UMAP 통합**: 고차원 데이터의 차원 축소로 계산 효율성 증대

### 실행 과정
1. **Google Drive 마운트 및 데이터 로드**
   - Google Drive를 마운트하여 데이터 파일을 불러옵니다.
2. **데이터 표준화 및 UMAP 차원 축소**
   - 데이터를 표준화한 뒤, UMAP을 사용하여 차원 축소를 수행합니다.
3. **Q 최적화로 커널 파라미터(`sigma`) 탐색**
   - Q 최적화 방법을 통해 최적의 커널 파라미터를 탐색합니다.
4. **Kernel LDA 수행 및 교차 검증**
   - Kernel LDA를 적용하고, 교차 검증을 통해 최적의 파라미터(`lambda1`, `lambda2`)를 찾습니다.
5. **모델 학습**
   - 학습된 모델로 예측을 수행합니다.

### 주요 메서드
- **`fit_transform_umap`**: UMAP을 사용하여 데이터의 차원 축소
- **`optimize_sigma`**: 최적의 커널 파라미터(`sigma`) 탐색
- **`cross_validate`**: 교차 검증을 통해 최적의 파라미터(`lambda1`, `lambda2`) 탐색
- **`predict`**: 학습된 모델로 새로운 데이터를 예측


## Experiment and Results

### 데이터셋
- **Arcene 데이터셋**:  
  UCI 머신러닝 저장소에서 제공하는 데이터셋으로, 10,000개의 고차원 특징(feature)을 포함하며, 이진 분류 작업에 사용됩니다.

### 주요 결과
- **QKULDA 정확도**: 92.5%
- **기존 LDA 정확도**: 47%
- **시간 복잡도**:  
  - QKULDA 학습 시간: 최대 5분  
  - 기존 LDA 학습 시간: 30분 이상 소요

### 성능 비교
- QKULDA는 기존 LDA와 비교하여 **정확도**와 **계산 효율성** 측면에서 모두 우수한 성능을 발휘했습니다.
