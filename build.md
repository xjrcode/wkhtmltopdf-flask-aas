# Build process

1 - Build image from X86 processor

docker buildx build --push --platform linux/amd64 -f Dockerfile_amd64 -t xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim-amd64 .

2 - Build image from Apple Silicon processor

docker buildx build --push --platform linux/arm64 -f Dockerfile_arm64 -t xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim-arm64 .

3 - Create manifest

docker manifest create xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim \
--amend xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim-amd64 \
--amend xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim-arm64

4 - Upload manifest

docker manifest push xjrcode/wkhtmltopdf-flask-aas:0.12.6-1-buster-slim