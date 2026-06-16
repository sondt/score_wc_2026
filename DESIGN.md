---
name: WorldCup 2026 — Bảng tỷ số
version: 1.0.0
colors:
  primary: "#0B6E4F"        # emerald — màu sân cỏ, nhận diện chính
  primaryDark: "#08543C"
  accent: "#F5B700"         # gold — cúp vàng, điểm nhấn
  live: "#E5383B"           # red — trận đang đá / LIVE
  surface: "#FFFFFF"
  surfaceAlt: "#F4F7F5"     # nền card phụ / sọc bảng
  bg: "#0A1F17"             # nền tối header gradient gốc
  text: "#13211B"
  textMuted: "#5E726A"
  border: "#E3EAE6"
  win: "#0B6E4F"
  draw: "#9AA8A1"
  loss: "#C24B4B"
typography:
  display: "'Sora', system-ui, sans-serif"
  body: "system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif"
  scoreSize: "1.75rem"
  bodySize: "0.95rem"
  weightBold: 800
layout:
  maxWidth: "560px"         # mobile-first, đọc trên điện thoại
  gap: "12px"
  pad: "16px"
shapes:
  radius: "16px"
  radiusSm: "10px"
  radiusPill: "999px"
elevation:
  card: "0 1px 3px rgba(11,110,79,.08), 0 8px 24px rgba(11,110,79,.06)"
  live: "0 0 0 3px rgba(229,56,59,.15)"
---

# WorldCup 2026 — Bảng tỷ số

## Overview
App xem **tự động cập nhật** tỷ số & kết quả World Cup 2026 cho người dùng phổ thông
(không cần kiến thức kỹ thuật). Mở trên điện thoại là thấy ngay trận đang đá, kết quả
mới nhất, lịch sắp tới và bảng xếp hạng. Tinh thần: **đơn giản, đẹp, nhanh, tiện** —
không nút bấm phức tạp, tự refresh.

## Colors
- `primary` (emerald) dùng cho header, nhãn nhóm, đội thắng. Gợi màu sân cỏ.
- `accent` (gold) chỉ dùng điểm nhấn nhỏ (icon cúp, viền top trận hôm nay) — tránh lạm dụng.
- `live` (đỏ) DÀNH RIÊNG cho trạng thái đang đá (chấm nhấp nháy, phút thi đấu).
- Nền sáng (`surface`/`surfaceAlt`) cho thân app để dễ đọc ngoài trời; header dùng
  gradient tối `bg → primaryDark` cho cảm giác "premium".
- Contrast: text `#13211B` trên nền trắng ~ 14:1; chữ trắng trên header tối ~ 12:1 (đạt WCAG AA/AAA).

## Typography
- Display **Sora** (Google Fonts) cho tiêu đề & tỷ số — hiện đại, thể thao.
- Body dùng system-ui cho tốc độ tải và quen mắt.
- Tỷ số to, đậm (`weightBold` 800) là phần tử nổi bật nhất mỗi card.

## Layout
- Mobile-first, khung `maxWidth` 560px căn giữa trên màn lớn.
- Tab dính (sticky) phía trên: Hôm nay · Kết quả · Lịch · BXH.
- Mỗi trận là 1 card: [cờ + tên đội] — [tỷ số] — [cờ + tên đội], dưới là giờ VN / sân / phút.

## Elevation & Depth
- Card nổi nhẹ (`card` shadow). Trận LIVE thêm viền đỏ phát sáng (`live` ring).

## Shapes
- Bo góc lớn `radius` 16px cho card, `radiusPill` cho nhãn nhóm/tab.

## Components
- **MatchCard**: hai đội + tỷ số; biến thể `live` (đỏ, phút), `finished` (đậm), `upcoming` (giờ VN).
- **GroupTable**: bảng xếp hạng 1 bảng — Đ, T-H-B, HS, Điểm; tô đậm 2 đội đầu (đi tiếp).
- **Tabs**: chuyển khu vực, không reload.
- **StatusBar**: thời điểm cập nhật gần nhất + chấm trạng thái kết nối.

## Do's and Don'ts
- ✅ Để tỷ số là thứ to & rõ nhất.
- ✅ Luôn hiển thị **giờ Việt Nam (GMT+7)**.
- ✅ Tự cập nhật ngầm; báo lỗi nhẹ nhàng, không chặn người xem.
- ❌ Không bắt người dùng đăng nhập / cấu hình.
- ❌ Không hardcode màu ngoài token; không dùng đỏ cho việc khác ngoài LIVE.
