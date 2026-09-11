# Hướng dẫn nhúng hình vẽ (SVG) vào Flashcard Toán

Để flashcard sinh động hơn, bạn có thể nhúng trực tiếp các hình vẽ hình học hoặc đồ thị hàm số vào thẻ.

## Các bước thực hiện:

### 1. Vẽ hình bằng công cụ chuyên dụng
Sử dụng các công cụ hỗ trợ xuất SVG tốt:
- **GeoGebra:** Vẽ hình -> Export -> Graphics View as SVG.
- **Desmos:** Vẽ đồ thị -> Share Graph -> Export Image -> Chọn SVG.
- **Mathcha.io:** Công cụ chuyên cho toán học, hỗ trợ vẽ và xuất mã SVG cực sạch.

### 2. Chuẩn bị mã SVG
Khi copy mã SVG, hãy đảm bảo:
- Có thuộc tính `viewBox="..."` (để hình tự co giãn).
- Xóa các thuộc tính `width` và `height` cố định (ví dụ `width="500px"`) để tránh bị tràn màn hình. App sẽ tự động đặt `max-width: 100%`.
- Xóa phần khai báo XML `<?xml ... ?>` và các comment dư thừa để file JSON gọn nhẹ hơn.

### 3. Dán vào file FLASHCARD.json
Dán toàn bộ thẻ `<svg>...</svg>` vào trường `front` hoặc `back`. 
**Lưu ý quan trọng:** Vì mã SVG có chứa nhiều dấu ngoặc kép `"`, bạn cần phải escape chúng thành `\"` khi đặt vào file JSON.

**Ví dụ một thẻ hoàn chỉnh:**
```json
{
  "cardId": "toan10_sample_svg",
  "lessonId": "toan10_t1_b1",
  "front": "Đồ thị hàm số bậc hai $y = x^2$ trông như thế nào?",
  "back": "<svg viewBox=\"0 0 100 100\" xmlns=\"http://www.w3.org/2000/svg\"><path d=\"M10 80 Q 50 10 90 80\" stroke=\"black\" fill=\"transparent\"/></svg>\nĐây là hình Parabol hướng bề lõm lên trên."
}
```

## Mẹo nhỏ:
- Sử dụng công cụ **SVG Optimizer (SVGO)** online để làm gọn mã SVG trước khi dán.
- Ưu tiên các hình vẽ đơn sắc (đen/trắng) để phù hợp với giao diện của app.
