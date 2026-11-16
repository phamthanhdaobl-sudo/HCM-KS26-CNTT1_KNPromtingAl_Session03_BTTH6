# HCM-KS26-CNTT1_KNPromtingAl_Session03_BTTH6
# BÀI THỰC HÀNH 6: CHUẨN HÓA DỮ LIỆU SINH VIÊN THÀNH JSON

**Họ và tên:** Phạm Thành Đạo  
**Lớp:** HCM-KS26-CNTT1

## 1. Mục tiêu

Sử dụng kỹ thuật Prompt Engineering theo khung CREATE để yêu cầu AI đọc, chuẩn hóa thông tin sinh viên từ nhiều nguồn dữ liệu khác nhau và chuyển đổi thành định dạng JSON thống nhất.

Đảm bảo dữ liệu chính xác, không tự ý bổ sung thông tin, không làm mất bản ghi và kiểm tra tổng số lượng sinh viên trước khi xuất kết quả.

## 2. Xây dựng Prompt theo khung CREATE

### C – Character (Vai trò)

Bạn là chuyên viên quản lý dữ liệu của phòng đào tạo, có nhiệm vụ xử lý, chuẩn hóa và chuyển đổi dữ liệu sinh viên thành định dạng JSON phục vụ hệ thống quản lý.

### R – Request (Yêu cầu)

Hãy đọc danh sách thông tin sinh viên được cung cấp, phân tích từng bản ghi, chuẩn hóa họ tên, email và trạng thái học tập, sau đó chuyển toàn bộ dữ liệu thành cấu trúc JSON theo yêu cầu.

### E – Examples (Ví dụ)

Dữ liệu đầu vào:

Nguyễn Văn An - an.nguyen@gmail.com - đang học

Kết quả đầu ra:

{
  "fullName": "Nguyễn Văn An",
  "email": "an.nguyen@gmail.com",
  "status": "đang học"
}

### A – Adjustments (Điều chỉnh và ràng buộc)

- Trường `fullName`: Lưu họ và tên đầy đủ của sinh viên.
- Trường `email`: Lưu địa chỉ email chính xác theo dữ liệu đầu vào.
- Trường `status`: Chỉ được nhận một trong ba giá trị:
  - `đang học`
  - `bảo lưu`
  - `nghỉ học`
- Không tự ý bổ sung thông tin không có trong dữ liệu gốc.
- Không được bỏ sót hoặc làm mất bất kỳ bản ghi nào.
- Nếu một trường dữ liệu không xác định được, sử dụng giá trị `UNKNOWN`.
- Không tự suy đoán thông tin còn thiếu.
- Không thay đổi nội dung họ tên và địa chỉ email nếu dữ liệu đã hợp lệ.

### T – Type of Output (Định dạng đầu ra)

Chỉ xuất dữ liệu dưới dạng JSON hợp lệ, theo cấu trúc:

{
  "students": [
    {
      "fullName": "Nguyễn Văn An",
      "email": "an.nguyen@gmail.com",
      "status": "đang học"
    }
  ],
  "totalRecords": 4
}

Không sử dụng Markdown Code Fence, không giải thích hoặc thêm nội dung bên ngoài JSON.

### E – Evaluation (Tiêu chí đánh giá)

- JSON phải đúng cú pháp và có thể phân tích bằng chương trình xử lý JSON.
- Có đầy đủ 4 bản ghi sinh viên.
- Mỗi bản ghi phải có đủ 3 trường `fullName`, `email`, `status`.
- Trạng thái phải thuộc một trong ba giá trị được cho phép hoặc là `UNKNOWN` nếu không xác định được.
- Giá trị `totalRecords` phải bằng số lượng bản ghi thực tế trong mảng `students`.
- Không được tự ý thêm, sửa hoặc loại bỏ thông tin.

## 3. Dữ liệu đầu vào

Nguyễn Văn An - an.nguyen@gmail.com - đang học

Trần Thị Bình - binhtt@gmail.com - bảo lưu

Lê Hoàng Nam - nam.le@gmail.com - đang học

Phạm Minh Đức - duc.pham@gmail.com - nghỉ học

## 4. Kết quả JSON sau khi chuẩn hóa

{
  "students": [
    {
      "fullName": "Nguyễn Văn An",
      "email": "an.nguyen@gmail.com",
      "status": "đang học"
    },
    {
      "fullName": "Trần Thị Bình",
      "email": "binhtt@gmail.com",
      "status": "bảo lưu"
    },
    {
      "fullName": "Lê Hoàng Nam",
      "email": "nam.le@gmail.com",
      "status": "đang học"
    },
    {
      "fullName": "Phạm Minh Đức",
      "email": "duc.pham@gmail.com",
      "status": "nghỉ học"
    }
  ],
  "totalRecords": 4
}

## 5. Kiểm tra kết quả

| Tiêu chí | Kết quả |
|---|---|
| Tổng số bản ghi đầu vào | 4 |
| Tổng số bản ghi đầu ra | 4 |
| Số bản ghi bị mất | 0 |
| Số trường dữ liệu mỗi sinh viên | 3 |
| Trạng thái hợp lệ | 4/4 |
| Giá trị totalRecords | 4 |
| Cấu trúc JSON | Hợp lệ |

## 6. Kết luận

Việc sử dụng Prompt theo khung CREATE giúp AI thực hiện quá trình chuẩn hóa dữ liệu sinh viên một cách rõ ràng và có hệ thống. Dữ liệu đầu vào được chuyển thành JSON thống nhất, giúp phòng đào tạo dễ dàng quản lý và tích hợp vào hệ thống.

Đặc biệt, việc bổ sung các ràng buộc và tiêu chí đánh giá giúp hạn chế sai sót, tránh mất bản ghi và đảm bảo số lượng dữ liệu đầu ra luôn khớp với dữ liệu ban đầu.
