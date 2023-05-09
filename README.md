# Learning Socket.io

## CÁC VẤN ĐỀ CỦA SOCKET.IO

# Môi trường
Cần có module socket.io
npm install --save socket.io express

Cần require module vào dự án
* Tại server
var app require('express')
var server = require('http).createServer(app)
var io = require('socket.io')(server)

Lắng nghe kết nối của client
io.on('connection', socket => {
    ....
})

* Tại client
<script src="./socket.io/socket.io.js"></script>
Nếu chưa có đường dẫn trên:
1. Vào thư mục node_modules/socket.io/client-dist sao chép file socket.io.js
2. Tạo thư mục socket.io tại public vào dán file socket.io.js vào

var socket = io('localhost:3000');

# Gửi nhận event
* Gửi dữ liệu: emit(<connect name>, <data>)
* Nhận dữ liệu: on(<connect name>, (<data>) => {
    ....
})


# Broadcasting
Phương thức socket.emit sẽ gửi đến tất cả các client đang kết nối
Phương thức socket.broadcast.emit sẽ gửi đến tất các client khác trừ client đang được lắng nghe (sender đang sử dụng)

# Namespace
* Namespace mặc định: io() không được chỉ cho client khi kết nối tới server
* Namespace tùy chỉnh: socket.of(<route>): 

# Rooms
Trong mỗi một namespace, các kênh tùy ý mà các socket có thể tham gia hoặc rơi đi đgl rooms
Rooms chỉ được tham gia ở phía server
* Tham gia
socket.join(<room name>)
Gửi event trong room
socket.in(<room name>).emit();

* Rời khỏi
socket.leave(<room name>)

# Bắt lỗi
* Các API phía client cung cấp các sự kiện
Connect − Khi kết nối thành công
Connecting − Khi clients đang kết nối
Disconnect − Khi clients bị ngắt kết nối tới server
Connect_failed − Kết nối xảy ra lỗi.
Error − Khi quá trình gửi event gửi tới server bị lỗi
Message − Khi server gửi tin qua send function.
Reconnect − Khi đã kết nối lại thành công.
Reconnecting − Khi đang kết nối lại
Reconnect_failed − Khi kết nối lại bị lỗi.



