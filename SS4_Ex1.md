# BÀI 1: Phân tích & Lựa chọn (Thực hành thiết kế prompt tối ưu hóa mã nguồn)

**Đáp án lựa chọn:** Phương án B

### 1. Phân tích chi tiết tại sao Phương án B là tối ưu nhất

Phương án B là một prompt xuất sắc vì nó bao phủ đầy đủ và rõ ràng **5 thành phần cốt lõi** của một câu lệnh chất lượng cao, giúp định hướng AI tạo ra kết quả chính xác ngay từ lần đầu tiên:

* **Role (Vai trò):** *"đóng vai trò là một Java Senior Developer"*. Thiết lập tiêu chuẩn đầu ra ở mức chuyên nghiệp, AI sẽ áp dụng các tiêu chuẩn Clean Code thay vì chỉ viết code chạy được.
* **Goal (Mục tiêu):** *"tái cấu trúc (refactor) logic rẽ nhánh lồng nhau phức tạp... thành các câu lệnh điều kiện bảo vệ (guard clauses / return sớm)"*. Chỉ định chính xác kỹ thuật cần sử dụng, tránh việc AI tự do sáng tạo sai hướng.
* **Context (Ngữ cảnh):** Ngữ cảnh được ngầm hiểu thông qua đoạn mã đầu vào (class `DiscountService`) và phiên bản môi trường *"sử dụng Java 11"*.
* **Constraint (Ràng buộc):** *"Giữ nguyên logic nghiệp vụ tính chiết khấu ban đầu, không thay đổi kiểu dữ liệu đầu vào/đầu ra"*. Đây là ràng buộc tối quan trọng trong việc tái cấu trúc (refactoring) để đảm bảo mã mới không làm vỡ hệ thống cũ (không phá hỏng Unit Test).
* **Format (Định dạng):** *"Trình bày kết quả dưới dạng khối mã nguồn Java hoàn chỉnh kèm giải thích ngắn bằng tiếng Việt"*. Giúp đầu ra dễ đọc, dễ sao chép và thân thiện với người dùng.

---

### 2. Phân tích lý do loại trừ các phương án còn lại

**Phương án A:**
* **Nhược điểm:** Quá chung chung và sơ sài. Hoàn toàn thiếu các thành phần: Vai trò, Ràng buộc, Định dạng và Kỹ thuật cụ thể.
* **Nguy cơ:** Từ "đẹp hơn" là một khái niệm trừu tượng. AI có thể hiểu sai ý và tái cấu trúc theo kiểu rút gọn thành Toán tử ba ngôi (Ternary Operator) lồng nhau chằng chịt, khiến mã nguồn rác và khó đọc hơn cả ban đầu, hoặc tự ý đổi tên biến, đổi cấu trúc hàm gây lỗi biên dịch.

**Phương án C:**
* **Nhược điểm:** Mặc dù có Mục tiêu (viết ngắn gọn) và Ràng buộc kỹ thuật (Java Stream API), nhưng lại **áp dụng sai kỹ thuật**.
* **Nguy cơ:** Java Stream API được thiết kế để xử lý các luồng dữ liệu tập hợp (Collections, Arrays, Lists...), không phải để xử lý logic rẽ nhánh có điều kiện trên các biến đơn trị (scalar values) như chuỗi `type` hay số thực `amount`. Việc ép AI dùng Stream API cho trường hợp này sẽ dẫn đến tình trạng AI "ảo giác" (hallucination), sinh ra đoạn mã khiên cưỡng, sai cú pháp, hoặc cực kỳ tối nghĩa, làm giảm sút nghiêm trọng hiệu năng và tính bảo trì của dự án.