# example

## 1,介绍

现在（2025/1/25）的example和一年以前演示的功能已经不一样了。

这段代码实现了一个简单的 HTTP(S) 服务器，能够处理文件上传（`multipart/form-data`），记录日志，并支持基本的错误处理和目录映射。代码主要依赖 `httplib` 库来简化 HTTP 服务的实现。

如果你想上传文件到这个服务器，你可以通过发送一个 `POST` 请求到 `/multipart` 路径，使用 `multipart/form-data` 格式。

## 2，使用

### 上传文件的步骤

1. 我写了一个 HTML 表单（text.html）来选择文件并上传。

   这个表单会将文件上传到 `http://localhost:8080/multipart`，使用 `POST` 请求，并且表单的 `enctype="multipart/form-data"` 属性指定了文件上传的格式。

2. **发送请求：**

   - 当你在浏览器中打开这个 HTML 文件，并选择一个文件进行上传后，表单会向服务器发送一个 `POST` 请求，上传文件到 `/multipart` 路径。
   - 服务器会接收请求，并将文件内容以 `multipart/form-data` 格式解析。然后，服务器会返回一个包含请求头和文件内容详细信息的响应。

3. **服务器的响应：**

   - 服务器会处理文件上传请求，并将请求的详细信息（如请求头、文件信息等）返回给客户端。这些信息会显示在浏览器中（例如文件的 `name`、`filename`、`content type` 和文件的字节大小）。
   - 如果上传过程成功，浏览器会显示服务器返回的内容。

### 使用 `curl` 上传文件

如果你想通过命令行工具 `curl` 上传文件，也可以使用以下命令：

```bash
curl -X POST -F "file=@path_to_your_file" http://localhost:8080/multipart
```

这里的 `path_to_your_file` 是你想上传的文件的路径。`curl` 会自动将文件作为 `multipart/form-data` 格式提交。