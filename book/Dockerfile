# Stage 1: Build the book
FROM peaceiris/mdbook:latest AS builder

WORKDIR /book

# Copy mdBook config and table of contents
COPY book/book.toml .
COPY book/src/SUMMARY.md src/SUMMARY.md

# Copy all chapter files into the mdBook src directory
COPY ch*.md src/

# Build the book
RUN mdbook build

# Stage 2: Serve with nginx
FROM nginx:alpine

COPY --from=builder /book/output /usr/share/nginx/html

EXPOSE 80
