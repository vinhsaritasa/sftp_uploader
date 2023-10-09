For working program need `xclip`. Install it

```bash
sudo apt-get install xclip
```

Fill credentials to sftp in `config.ini`

Compile go files `go build -o sftp_uploader *.go` or use compiled binaries.

```bash
    mkdir -p bin
    # 64 bit - Windows
    GOOS=windows GOARCH=amd64 go build -o bin/app-amd64.exe *.go
    # 64-bit - Mac
    GOOS=darwin GOARCH=amd64 go build -o bin/app-amd64-darwin *.go
    # 64-bit - Mac ARM
    GOOS=darwin GOARCH=arm64 go build -o bin/app-arm64-darwin *.go
    # 64-bit - Linux
    GOOS=linux GOARCH=amd64 go build -o bin/app-amd64-linux *.go
    # 64-bit - Linux ARM
    GOOS=linux GOARCH=arm64 go build -o bin/app-arm64-linux *.go
```

Run:

```bash
$ ./sftp_uploader # for upload image from clipboard buffer
$ ./sftp_uploader -r # for upload image from stdin
```

Example with `cat`:

```bash
cat < /home/vinh/Pictures/my-file.png | sftp_uploader -r
```

Example with [flameshot](https://github.com/lupoDharkael/flameshot):

```bash
$ flameshot gui -r  | ./sftp_uploader -r
```
