import anthropic

# uses ANTHROPIC_API_KEY or credentials from `ant auth login`
client = anthropic.Anthropic()

with client.messages.stream(
    model="claude-opus-5-5",
    max_tokens=20000,
    messages=[
        {
            "role": "user",
            "content": "Trong tương lai gần, một sự kiện bí ẩn có tên là First Light (Ánh Sáng Đầu Tiên) xảy ra, ban cho những người ngẫu nhiên siêu năng lực (gọi là radiance - ánh sáng). Những người có radiance bị đối xử tệ nhất là bị nghi ngờ, tệ hơn nữa là bị săn đuổi và ngược đãi. Sau First Light, một chất mới có tên là Radianite được tiết lộ và có một số đặc tính đáng kinh ngạc, khiến nó trở thành một nguồn năng lượng tuyệt vời. (Lưu ý rằng radianite đã được khám phá và thử nghiệm một thời gian trước khi First Light xảy ra. Người ta tin rằng First Light là do thí nghiệm với radianite gây ra. Tiện thể, radianite thậm chí đã được tìm thấy được sử dụng từ thời Edo của Nhật Bản, nhờ vào trò du hành thời gian của Yoru, mà không thực sự liên quan lắm.) Nhanh đến vài năm sau, trái đất đã chuyển đổi hoàn toàn sang radianite và thế giới đã trở nên tiên tiến hơn về mặt công nghệ. Tập đoàn Kingdom (Kingdom Industries ở Trái Đất Omega) kiểm soát hầu hết các nghiên cứu năng lượng radianite và sử dụng thương mại.",
        },
    ],
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
