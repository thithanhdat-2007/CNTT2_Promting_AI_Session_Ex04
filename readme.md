# Giải pháp Chuẩn hóa Câu lệnh theo Khung CREATE – Chuỗi Bán lẻ TechShop

Tài liệu này trình bày quy trình phân tích chẩn đoán lỗi ("phẫu thuật" câu lệnh sơ sài) và nâng cấp thành các **Master Prompt** chuẩn doanh nghiệp theo khung **CREATE** (**C**haracter – **R**equest – **E**xamples – **A**djustment – **T**ype of Output – **E**xtras) cho 3 phòng ban: Chăm sóc khách hàng, Bán hàng và Kỹ thuật bảo hành.

---

## Phần 1: Phân tích chẩn đoán lỗi (Phẫu thuật câu lệnh sơ sài)

### 1. Bộ phận CSKH
* **Câu lệnh gốc:** *"Viết tin nhắn xin lỗi khách vì hàng giao chậm."*
* **Chẩn đoán chi tiết các thành phần CREATE bị khuyết:**
  * **Character (Vai trò):** Không xác định AI đóng vai ai (Chuyên viên CSKH tận tâm của TechShop), dẫn đến giọng văn vô hồn, thiếu sự đồng cảm và tinh thần chịu trách nhiệm của thương hiệu.
  * **Request (Yêu cầu):** Quá chung chung, chỉ yêu cầu "xin lỗi" mà không yêu cầu AI lồng ghép lý do khách quan, thời gian giao hàng dự kiến mới và chính sách đền bù/xoa dịu khách hàng.
  * **Examples (Ví dụ mẫu):** Thiếu mẫu câu xưng hô chuẩn của TechShop hoặc cách xử lý khủng hoảng khéo léo.
  * **Adjustment (Điều chỉnh/Ràng buộc):** Không có quy tắc giới hạn độ dài tin nhắn (phù hợp với Zalo/SMS), không có lệnh cấm dùng các từ ngữ đổ lỗi cho khách hàng hoặc đơn vị vận chuyển một cách thiếu chuyên nghiệp.
  * **Type of Output (Định dạng đầu ra):** Không định hình cấu trúc tin nhắn (Lời chào $\rightarrow$ Lời xin lỗi & Lý do $\rightarrow$ Thời gian cập nhật $\rightarrow$ Quà tặng đền bù $\rightarrow$ Lời cam kết).
  * **Extras (Bối cảnh bổ sung):** Thiếu dữ liệu đầu vào động (tên khách hàng, mã đơn hàng, tên sản phẩm, nguyên nhân trễ, voucher đền bù cụ thể).

### 2. Bộ phận Bán hàng (Sales)
* **Câu lệnh gốc:** *"Tư vấn cho anh khách mua laptop gaming."*
* **Chẩn đoán chi tiết các thành phần CREATE bị khuyết:**
  * **Character (Vai trò):** Thiếu vai trò Chuyên viên Tư vấn Giải pháp Công nghệ của TechShop (người hiểu rõ phần cứng và tâm lý game thủ, không chỉ là người đọc thông số).
  * **Request (Yêu cầu):** Yêu cầu mở ("tư vấn"), không khoanh vùng số lượng máy (khiến AI liệt kê tràn lan 10 mẫu) và không yêu cầu phân tích điểm mạnh/yếu theo nhu cầu thực tế.
  * **Examples (Ví dụ mẫu):** Thiếu cấu trúc trình bày một mẫu máy chuẩn (Tên máy – Điểm ăn tiền nhất – Phù hợp với tựa game nào – Giá ưu đãi tại TechShop).
  * **Adjustment (Điều chỉnh/Ràng buộc):** Không giới hạn số lượng gợi ý (tối đa 3 mẫu trong tầm giá), cấm liệt kê thông số khô khan như bảng cấu hình kỹ thuật.
  * **Type of Output (Định dạng đầu ra):** Không yêu cầu định dạng so sánh trực quan (dạng danh sách có phân nhóm theo nhu cầu hoặc bảng so sánh nhanh) kèm câu hỏi chốt sale ở cuối.
  * **Extras (Bối cảnh bổ sung):** Thiếu hoàn toàn chân dung khách hàng (ngân sách bao nhiêu, chơi game gì: eSports nhẹ hay AAA nặng, có cần mang đi học/đi làm không, danh sách máy đang sẵn kho).

### 3. Bộ phận Kỹ thuật bảo hành
* **Câu lệnh gốc:** *"Báo giá thay màn hình laptop vỡ cho khách."*
* **Chẩn đoán chi tiết các thành phần CREATE bị khuyết:**
  * **Character (Vai trò):** Thiếu vai trò Kỹ thuật viên Trưởng / Điều phối viên Trung tâm Bảo hành TechShop (chuyên nghiệp, minh bạch, am hiểu kỹ thuật và chính sách hãng).
  * **Request (Yêu cầu):** Chỉ hỏi "báo giá" mà không yêu cầu AI phân loại các phân khúc màn hình (Chính hãng vs Linh kiện thay thế loại 1), quy trình kiểm tra máy và thời gian xử lý.
  * **Examples (Ví dụ mẫu):** Không có khung báo giá mẫu để AI bám theo.
  * **Adjustment (Điều chỉnh/Ràng buộc):** Thiếu ràng buộc nghiêm ngặt: **Không tự bịa đặt giá chính xác** khi chưa biết mã máy (Model/Serial), bắt buộc phải đưa ra bảng giá tham khảo theo dải kích thước/tần số quét và yêu cầu khách cung cấp mã máy để tra cứu chính xác.
  * **Type of Output (Định dạng đầu ra):** Thiếu cấu trúc chuẩn gồm: Bảng giá tham khảo (Markdown Table) + Quy định bảo hành linh kiện + Các bước tiếp nhận máy.
  * **Extras (Bối cảnh bổ sung):** Thiếu thông tin chính sách bảo hành thực tế của TechShop (thời gian bảo hành màn hình mới, cam kết không tráo đổi linh kiện, thời gian thay lấy liền).

---

## Phần 2: Nâng cấp chuẩn hóa thành 3 Master Prompt (Khung CREATE)

Các Master Prompt dưới đây được thiết kế có sẵn các biến đầu vào `[TRONG_NGOẶC_VUÔNG]` để nhân viên TechShop chỉ cần điền thông tin thực tế và chạy ngay.

---

### 1. Master Prompt – Bộ phận CSKH (Xử lý giao hàng chậm)

```markdown
# C - CHARACTER (Vai trò)
Bạn là Chuyên viên Chăm sóc Khách hàng Cấp cao tại chuỗi bán lẻ công nghệ TechShop. Bạn có phong thái tận tâm, chân thành, biết lắng nghe và luôn đặt trải nghiệm của khách hàng lên hàng đầu.

# R - REQUEST (Yêu cầu)
Hãy soạn một tin nhắn gửi qua Zalo/SMS để chủ động xin lỗi khách hàng về việc đơn hàng bị giao chậm hơn dự kiến. Tin nhắn cần thể hiện sự cầu thị, thông báo rõ lịch giao hàng mới và gửi tặng mã ưu đãi như một lời tạ lỗi thiết thực từ TechShop.

# E - EXAMPLES (Ví dụ mẫu về văn phong & cấu trúc)
"Chào anh/chị [Tên khách], TechShop rất tiếc phải thông báo đơn hàng [Mã đơn] của mình hiện đang chậm hơn dự kiến 1 ngày do sự cố điều phối từ kho trung chuyển. Dự kiến đơn sẽ đến tay anh/chị trước [Thời gian mới]. Để thay lời xin lỗi vì sự bất tiện này, TechShop xin gửi tặng anh/chị voucher [Mã giảm giá] trị giá [Giá trị] cho lần mua sắm tới..."

# A - ADJUSTMENT (Điều chỉnh & Ràng buộc)
- Giọng văn: Chân thành, lịch sự, xưng hô "TechShop" và gọi khách là "Anh/Chị" (hoặc theo danh xưng cung cấp).
- Tuyệt đối KHÔNG dùng văn phong đổ lỗi cho khách hàng hoặc thoái thác trách nhiệm hoàn toàn cho đơn vị vận chuyển.
- Độ dài: Ngắn gọn, súc tích dưới 150 từ để khách dễ đọc trên màn hình điện thoại.
- Không sử dụng các từ ngữ sáo rỗng, máy móc như "kính mong quý khách thông cảm sâu sắc".

# T - TYPE OF OUTPUT (Định dạng đầu ra)
Trả về 01 đoạn tin nhắn hoàn chỉnh, chia thành 3 đoạn ngắn rõ ràng:
1. Lời chào + Lời xin lỗi trực diện kèm nguyên nhân ngắn gọn.
2. Thời gian giao hàng dự kiến mới + Cam kết theo dõi sát sao.
3. Quà tặng đền bù + Lời cảm ơn và thông tin hỗ trợ trực tiếp.

# E - EXTRAS (Dữ liệu đầu vào thực tế)
- Tên khách hàng: [Nhập tên khách, VD: Anh Minh]
- Mã đơn hàng & Sản phẩm: [Nhập mã đơn & SP, VD: #TS8892 - Chuột Logitech G Pro X]
- Nguyên nhân chậm trễ: [Nhập lý do, VD: Ảnh hưởng thời tiết mưa bão tại trạm trung chuyển]
- Thời gian giao dự kiến mới: [Nhập thời gian, VD: Trước 17h00 ngày mai, 15/11]
- Chính sách đền bù áp dụng: [Nhập ưu đãi, VD: Voucher giảm 100.000đ (Mã: TECHCARE100) + Miễn phí giao hàng đơn sau]
```

---

### 2. Master Prompt – Bộ phận Bán hàng (Tư vấn Laptop Gaming)

```markdown
# C - CHARACTER (Vai trò)
Bạn là Chuyên viên Tư vấn Giải pháp Công nghệ xuất sắc tại TechShop, có kiến thức sâu rộng về phần cứng máy tính và am hiểu trải nghiệm thực tế của cộng đồng game thủ. Bạn tư vấn như một người bạn đồng hành am hiểu kỹ thuật, trung thực và tập trung vào giá trị sử dụng thực tế.

# R - REQUEST (Yêu cầu)
Dựa trên nhu cầu và ngân sách của khách hàng, hãy chọn lọc và tư vấn tối đa 03 mẫu laptop gaming phù hợp nhất đang có sẵn tại TechShop. Phân tích rõ lý do vì sao từng mẫu máy đáng mua trong tầm giá và kết thúc bằng một câu hỏi mở để dẫn dắt khách chốt đơn hoặc đến trải nghiệm trực tiếp.

# E - EXAMPLES (Ví dụ mẫu cho từng gợi ý máy)
"**1. Asus TUF Gaming F15 (2024) – Giá ưu đãi: 22.990.000đ**
- **Điểm ăn tiền nhất:** Sở hữu card rời RTX 4060 8GB mạnh nhất phân khúc dưới 23 triệu, màn hình 144Hz chuẩn màu 100% sRGB.
- **Trải nghiệm thực tế:** Chiến mượt Max Setting các tựa game AAA như Cyberpunk 2077, Black Myth: Wukong và cân tốt các tác vụ render đồ họa.
- **Lưu ý nhỏ:** Trọng lượng 2.2kg, phù hợp nếu anh/chị ít phải di chuyển liên tục mỗi ngày."

# A - ADJUSTMENT (Điều chỉnh & Ràng buộc)
- CHỈ đề xuất đúng 2 đến 3 mẫu máy sát với ngân sách nhất (không liệt kê dàn trải).
- Không sao chép khô khan toàn bộ bảng thông số kỹ thuật; phải chuyển hóa thông số thành lợi ích thực tế (VD: thay vì chỉ ghi "tản nhiệt 2 quạt", hãy giải thích "chơi game liên tục 3 tiếng không bị tụt FPS").
- Luôn nêu rõ 1 điểm hạn chế nhỏ của từng máy để tạo sự tin cậy tuyệt đối.

# T - TYPE OF OUTPUT (Định dạng đầu ra)
Trình bày theo cấu trúc tư vấn bán hàng chuyên nghiệp gồm 4 phần:
1. Lời chào & Xác nhận lại nhu cầu của khách.
2. Chi tiết 03 đề xuất máy (theo đúng cấu trúc ở mục Examples).
3. Bảng so sánh nhanh 3 tiêu chí: Hiệu năng game / Màn hình / Tính di động.
4. Thông tin khuyến mãi đi kèm tại TechShop + Câu hỏi gợi mở chốt đơn.

# E - EXTRAS (Dữ liệu đầu vào thực tế)
- Danh xưng khách hàng: [VD: Anh Hoàng]
- Ngân sách dự kiến: [VD: Khoảng 22 - 25 triệu đồng]
- Nhu cầu chính & Tựa game hay chơi: [VD: Chơi Valorant, FC Online, thỉnh thoảng chơi game AAA và làm lập trình]
- Yêu cầu đặc biệt (nếu có): [VD: Cần máy thiết kế không quá hầm hố, tản nhiệt tốt]
- Danh sách máy sẵn kho & Khuyến mãi hiện hành: [VD: Asus TUF F15, Lenovo LOQ 15IRX9, Acer Nitro V. Tặng balo gaming + chuột không dây + giảm thêm 500k cho sinh viên]
```

---

### 3. Master Prompt – Bộ phận Kỹ thuật bảo hành (Báo giá thay màn hình)

```markdown
# C - CHARACTER (Vai trò)
Bạn là Điều phối viên Kỹ thuật tại Trung tâm Bảo hành & Sửa chữa ủy quyền của TechShop. Phong thái của bạn chuẩn mực, minh bạch, am hiểu chuyên môn kỹ thuật và luôn đặt sự an tâm của khách hàng lên hàng đầu.

# R - REQUEST (Yêu cầu)
Hãy phản hồi yêu cầu hỏi giá thay màn hình laptop bị vỡ của khách hàng. Nội dung cần giải thích rõ rằng giá chính xác phụ thuộc vào mã máy (Model) cụ thể, đồng thời cung cấp bảng giá tham khảo theo các phân khúc phổ biến tại TechShop, quy trình tiếp nhận minh bạch và chính sách bảo hành sau sửa chữa.

# E - EXAMPLES (Ví dụ mẫu về cách giải thích kỹ thuật)
"Vì mỗi dòng laptop sử dụng chuẩn chân cáp (30-pin hoặc 40-pin), độ phân giải và tần số quét khác nhau nên chi phí thay thế sẽ chênh lệch tùy theo mã máy. Để anh/chị dễ dự trù kinh phí, TechShop xin gửi bảng giá tham khảo cho các dòng màn hình phổ thông hiện nay..."

# A - ADJUSTMENT (Điều chỉnh & Ràng buộc)
- Tuyệt đối KHÔNG bịa đặt một con số báo giá cố định duy nhất khi chưa có mã máy chính xác của khách.
- Phải phân biệt rõ hai lựa chọn linh kiện (nếu có): Màn hình chính hãng (Zin theo máy) và Màn hình thay thế chuẩn OEM loại 1.
- Bắt buộc nhấn mạnh cam kết chống tráo đổi linh kiện (khách được ký tên lên linh kiện và xem trực tiếp kỹ thuật viên thao tác).
- Giọng văn: Rõ ràng, khách quan, chuyên nghiệp.

# T - TYPE OF OUTPUT (Định dạng đầu ra)
Trình bày nội dung theo 4 mục rõ ràng:
1. Lời chào & Giải thích ngắn gọn yếu tố quyết định giá màn hình.
2. **Bảng giá tham khảo** (định dạng Markdown Table gồm các cột: Phân loại màn hình | Đặc điểm kỹ thuật | Chi phí tham khảo | Thời gian bảo hành).
3. **Quy trình & Cam kết dịch vụ tại TechShop** (gạch đầu dòng các cam kết: kiểm tra miễn phí, thay lấy liền trong 30-45 phút, ký tên linh kiện).
4. Hướng dẫn khách gửi thông tin (Tem mã máy dưới đáy laptop hoặc ảnh chụp tình trạng vỡ) để nhận báo giá chính xác 100%.

# E - EXTRAS (Dữ liệu đầu vào thực tế)
- Tên khách hàng: [VD: Chị Thảo]
- Thông tin máy khách cung cấp ban đầu: [VD: Khách chỉ nhắn "Laptop Dell bị rơi vỡ màn hình", chưa rõ mã]
- Khung giá & Chính sách thực tế của TechShop:
  + Màn hình HD/Full HD 60Hz tiêu chuẩn: 1.200.000đ – 1.800.000đ (BH 12 tháng).
  + Màn hình Full HD IPS 144Hz (Dòng Gaming): 2.100.000đ – 2.900.000đ (BH 06 - 12 tháng).
  + Màn hình 2K / OLED / Cảm ứng cao cấp: 3.500.000đ – 5.500.000đ (BH 06 tháng).
  + Công thay thế & Vệ sinh máy cơ bản: Miễn phí 100%.
```