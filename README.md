# zgt

Zig GUI Toolkit

**As of now, zgt is NOT ready for any non-toy use as i'm still making breaking changes**

```zig
usingnamespace @import("zgt");
const std = @import("std");

pub fn run() !void {
    var window = try Window.init();
    try window.set(
        try Column(.{}, .{
            try Row(.{}, .{
                Button(.{ .label = "Save", .onclick = buttonClicked }),
                Button(.{ .label = "Run",  .onclick = buttonClicked })
            }),
            try Expanded(TextArea(.{ .text = "Hello World!" }))
        })
    );

    try window.resize(800, 600);
    window.show();
    window.run();
}

fn buttonClicked(button: *Button_Impl) !void {
    std.log.info("You clicked button with text {s}", .{button.getLabel()});
}
```