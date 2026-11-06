# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV:2A202603889**
- **Họ và tên: Nguyễn Lương Phúc**
- **SEED** (in ở ô đầu notebook):4609

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | Có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | Có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | Có |

## 2. Kết quả chính

                                precision  recall  F1 (test)  F1 (SUB 40)  \
1. BoW + LogReg (tự code)            0.986   0.828      0.900        0.833   
2. BoW + MLP (deep learning)         0.953   0.943      0.948        0.923   
3a. Encoder (MiniLM) + kNN           0.838   0.954      0.892        0.950   
3b. Encoder (MiniLM) + LogReg        0.966   0.977      0.971        1.000   
3c. Encoder (MiniLM) + MLP head      0.965   0.954      0.960        0.974   
4a. LLM nhỏ zero-shot                0.909   1.000      0.952        0.952   

                                 train (s)  tin/s (cả lô)  p50 ms/tin  \
1. BoW + LogReg (tự code)           10.028      25079.913       0.068   
2. BoW + MLP (deep learning)         6.089      34125.683       0.190   
3a. Encoder (MiniLM) + kNN          97.947         23.657      55.520   
3b. Encoder (MiniLM) + LogReg       98.402         30.797      26.095   
3c. Encoder (MiniLM) + MLP head     99.444         31.764      42.789   
4a. LLM nhỏ zero-shot                0.000          1.480     589.485   

                                 p95 ms/tin  USD / 1k tin  
1. BoW + LogReg (tự code)             0.256         0.000  
2. BoW + MLP (deep learning)          0.377         0.000  
3a. Encoder (MiniLM) + kNN           82.878         0.000  
3b. Encoder (MiniLM) + LogReg        42.599         0.000  
3c. Encoder (MiniLM) + MLP head      65.272         0.000  
4a. LLM nhỏ zero-shot              1074.382         0.027  
• Hàng LLM chỉ đo trên SUB (40 tin) → so sánh chất lượng công bằng bằng cột 'F1 (SUB 40)'.
• SUB chỉ 40 tin: 1 tin sai đổi F1 vài điểm. Chênh < ~0.05 F1 coi như HOÀ — đừng xếp hạng theo số lẻ.
• Inference đo TỪ VĂN BẢN THÔ → NHÃN (gồm cả vectorize / encode). p50/p95 = gọi từng tin một, như một request thật.
• train (s) của 3a/3b/3c = thời gian encoder MiniLM encode tập train (+ train đầu LogReg / MLP); LLM = 0 vì không train. Số đo phụ thuộc CPU/GPU của Colab.

## 3. Dự đoán và thực tế

*Chọn 3 dự đoán `predict(...)` lệch nhiều nhất so với kết quả. Mỗi cái: bạn đoán gì, ra gì, vì sao lệch.*

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
