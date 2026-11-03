# TQQQ Android 앱 v0.1 (Flutter source)

## Android APK 만들기
GitHub 저장소에 이 폴더 내용 전체를 업로드하고 Actions > Build Android APK > Run workflow를 누릅니다. 실행이 완료되면 Artifacts의 `tqqq-app-apk`를 다운로드합니다.

또는 Flutter SDK가 설치된 환경에서:

```sh
flutter create --platforms android --org com.jcapps --project-name tqqq_app .
flutter pub get
flutter build apk --release
```

## 현재 구현
- 홈/히스토리/누적 성과/관리 4탭, 라이트 테마
- Yahoo Finance QQQ/TQQQ 일봉 조회 기반 신호 표시 (실패 시 오류 표시, 조작된 값 없음)
- 달러 최초 투자금, 추가 입금/출금, 매도 후 계좌 잔고 정산의 기기 내 저장
- USD/KRW 표시 전환, 공개 환율 API 조회 및 마지막 조회 환율 저장
- 현금흐름을 차감한 순손익 (수익률이 아님)
- 알림 토글 저장

## 구현되지 않은 항목 / 주의
- APK를 여기서 직접 빌드하거나 실제 안드로이드 기기에서 테스트하지 않았습니다.
- 앱 종료 상태 푸시, 장중 실시간 경보, 자동 모의 체결 및 전략 누적 수익률, 매수 수량/체결가 장부, 세금 처리는 아직 없습니다.
- 신호 엔진은 일봉 종가로 상태를 추정하며 최초 로딩 시 과거 2년 데이터로 초기화됩니다. 실제 전략의 완전한 과거 상태와 차이가 있을 수 있습니다.
- 원화 환산은 현재 조회 환율을 이용한 참고 값이며 실제 환전 비용을 반영하지 않습니다.
- 현재 기록된 총 달러 잔고는 수동 입력값입니다. 주식을 보유 중인 경우 전체 평가자산과 다를 수 있습니다.
- 백엔드 없는 공개 API 조회는 서비스 제공자의 변경이나 차단에 따라 실패할 수 있습니다.
