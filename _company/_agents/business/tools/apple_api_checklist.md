# 🍏 Apple Developer API 권한 신청 체크리스트

_2026-06-15 기한 — 반드시 완료해야 iOS 앱 분석 데이터 확보 가능_

## ✅ 신청 전 준비사항
- [ ] Apple Developer 프로그램 가입 완료 ($99/년 결제됨)
- [ ] App Store Connect 관리자 권한 확인 (appstoreconnect.apple.com 로그인 가능)

## ✅ 신청 절차 (순서대로 실행)

### Step 1: App Store Connect API 접근 페이지 이동
```
https://appstoreconnect.apple.com/access/api
```

### Step 2: 인증서 및 키 생성
1. **"Generate Keys"** 버튼 클릭
2. 키 유형: **App Store Connect API** 선택
3. 키 이름 입력 (예: `ALTIT_Content_Analysis_Key`)
4. 생성 후 **고유 식별자 3가지 다운로드** (자동 제공됨):
   - `key_id`
   - `issuer_id`  
   - `.p8 파일` (사양 키 — **한 번만 제공됨, 절대 분실 금지**)

### Step 3: 권한 수준 설정
- **Read Only**로 시작 (보안 우선)
- 필요 시 이후 확장:
  - `access_apps.read` — 앱 목록 조회
  - `access_appAnalytics.read` — 분석 데이터 (다운로드 수 등)
  - `access_inAppPurchase.read` — 구매 데이터

### Step 4: 저장 위치 기록
```bash
# .p8 파일은 안전한 곳에 보관 (예:)
/Users/armonio/connectai/_company/secrets/appstore-connect-key.p8
```

## ✅ 신청 후 확인사항
- [ ] `key_id` 복사 완료
- [ ] `issuer_id` 복사 완료  
- [ ] `.p8 파일` 안전한 위치 저장
- [ ] `_company/.gitignore`에 `.p8` 추가 (Git 누출 방지)

## 🚨 주의사항
1. **.p8 파일은 한 번만 다운로드 가능** — 분실 시 새로 생성해야 함
2. **Git에 절대 커밋 금지** — 시크릿 누출 시 키 무효화됨
3. **권한 신청 후 활성화까지 24~48시간 소요** 가능

---
_생성: 2026-06-06 | 현빈 (Business Agent)_