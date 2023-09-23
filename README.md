# Docker save và docker load

## Docker save 

- docker save là một lệnh được sử dụng để lưu trữ một image Docker dưới dạng một tệp tar. Tệp tar này có thể được lưu trữ cục bộ hoặc chia sẻ với người khác.

Cú pháp:

```
docker save [OPTIONS] IMAGE
```

> Các tùy chọn:

+ -o, --output FILE: Tên tệp để lưu image.
+ -q, --quiet: Không hiển thị thông tin chi tiết.
+ -v, --verbose: Hiển thị thông tin chi tiết.

Ví dụ:

### Lưu image my-image dưới dạng tệp my-image.tar:

```
docker save -o my-image.tar my-image
```

### Sử dụng Docker load để tạo lại image:

Tệp tar được tạo bởi lệnh docker save có thể được sử dụng để tạo lại image bằng lệnh docker load.

```
docker load [OPTIONS] FILE
```

> Các tùy chọn:

+ -i, --input FILE: Tên tệp để tải image.
+ -q, --quiet: Không hiển thị thông tin chi tiết.
+ -v, --verbose: Hiển thị thông tin chi tiết.

Ví dụ:

Tạo lại image my-image từ tệp my-image.tar:

docker load -i my-image.tar
### Lợi ích của việc sử dụng Docker save:

- Dễ dàng lưu trữ và chia sẻ image: Tệp tar được tạo bởi lệnh docker save có thể được lưu trữ cục bộ hoặc chia sẻ với người khác. Điều này giúp bạn dễ dàng lưu trữ và chia sẻ image với người khác.
- Dễ dàng sao lưu image: Bạn có thể sử dụng lệnh docker save để sao lưu image của mình. Điều này giúp bạn bảo vệ image của mình khỏi bị mất hoặc hỏng.

### Ưu điểm:

- Dễ dàng lưu trữ và chia sẻ image.
- Dễ dàng sao lưu image.
  
### Nhược điểm:
- Tạo ra tệp tar có thể lớn.

## Docker load

- Docker load là một lệnh được sử dụng để tạo lại một image Docker từ một tệp tar. Tệp tar này có thể được tạo bởi lệnh docker save hoặc được tải xuống từ một nguồn khác.

```
docker load [OPTIONS] FILE
```

> Các tùy chọn:

+ -i, --input FILE: Tên tệp để tải image.
+ -q, --quiet: Không hiển thị thông tin chi tiết.
+ -v, --verbose: Hiển thị thông tin chi tiết.
+ 
Ví dụ:

Tạo lại image my-image từ tệp my-image.tar:

```
docker load -i my-image.tar
```

### Lợi ích của việc sử dụng Docker load:

- Dễ dàng tạo lại image: Bạn có thể sử dụng lệnh docker load để tạo lại image mà bạn đã lưu trữ hoặc tải xuống. Điều này giúp bạn dễ dàng tạo lại image mà bạn cần mà không cần phải xây dựng lại từ đầu.
- Dễ dàng chia sẻ image: Bạn có thể sử dụng lệnh docker save để lưu trữ image của mình dưới dạng tệp tar. Tệp tar này có thể được chia sẻ với người khác bằng lệnh docker load.

### Một số lưu ý khi sử dụng Docker load:

- Tệp tar được tạo bởi lệnh docker save phải được tải xuống hoàn toàn trước khi bạn có thể sử dụng lệnh docker load để tạo lại image.
- Nếu tệp tar bị hỏng, lệnh docker load sẽ thất bại.
- Nếu bạn đang sử dụng lệnh docker load để tạo lại image từ một nguồn khác, bạn nên đảm bảo rằng image đó tương thích với phiên bản Docker mà bạn đang sử dụng.

### Ưu điểm:

- Dễ dàng tạo lại image.
- Dễ dàng chia sẻ image.
  
### Nhược điểm:

- Tệp tar phải được tải xuống hoàn toàn trước khi có thể tạo lại image.
- Nếu tệp tar bị hỏng, lệnh sẽ thất bại.

## So sánh docker save và docker load

 <table data-sourcepos="22:1-29:135">
                <tbody>
                    <tr data-sourcepos="22:1-22:41">
                        <th data-sourcepos="22:1-22:11">Tính năng</th>
                        <th data-sourcepos="22:13-22:25">Docker save</th>
                        <th data-sourcepos="22:27-22:39">Docker load</th>
                    </tr>
                    <tr data-sourcepos="24:1-24:45">
                        <td data-sourcepos="24:1-24:11">Chức năng</td>
                        <td data-sourcepos="24:13-24:27">Lưu trữ image</td>
                        <td data-sourcepos="24:29-24:43">Tạo lại image</td>
                    </tr>
                    <tr data-sourcepos="25:1-25:35">
                        <td data-sourcepos="25:1-25:12">Tệp đầu ra</td>
                        <td data-sourcepos="25:14-25:22">Tệp tar</td>
                        <td data-sourcepos="25:24-25:33">Không có</td>
                    </tr>
                    <tr data-sourcepos="26:1-26:83">
                        <td data-sourcepos="26:1-26:9">Yêu cầu</td>
                        <td data-sourcepos="26:11-26:44">Phải có quyền truy cập vào image</td>
                        <td data-sourcepos="26:46-26:81">Không cần quyền truy cập vào image</td>
                    </tr>
                    <tr data-sourcepos="27:1-27:89">
                        <td data-sourcepos="27:1-27:11">Thời gian</td>
                        <td data-sourcepos="27:13-27:48">Tùy thuộc vào kích thước của image</td>
                        <td data-sourcepos="27:50-27:87">Tùy thuộc vào kích thước của tệp tar</td>
                    </tr>
                    <tr data-sourcepos="28:1-28:116">
                        <td data-sourcepos="28:1-28:18">Khả năng mở rộng</td>
                        <td data-sourcepos="28:20-28:65">Có thể lưu trữ nhiều image trong một tệp tar</td>
                        <td data-sourcepos="28:67-28:114">Chỉ có thể tạo lại một image tại một thời điểm</td>
                    </tr>
                    <tr data-sourcepos="29:1-29:135">
                        <td data-sourcepos="29:1-29:18">Tính tương thích</td>
                        <td data-sourcepos="29:20-29:67">Phải tương thích với phiên bản Docker hiện tại</td>
                        <td data-sourcepos="29:69-29:133">Phải tương thích với phiên bản Docker được sử dụng để tạo
                            image</td>
                    </tr>
                </tbody>
            </table>
