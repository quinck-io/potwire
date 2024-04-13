# potwire

Potwire (Protobufs Over The Wire) is a concept for achieving **type-safe** full-stack client-server communication using Protocol Buffers over the wire. It is inspired by [Hotwire](https://hotwire.dev/), a set of tools to write web apps by sending HTML over the wire.

The goal of potwire is to provide a fast, standard, and safe method for data transfer between web or mobile clients and servers.

# Overview

## Potwire VS REST

REST is a common way to communicate between clients and servers. It is based on the HTTP protocol and uses JSON for data serialization. However, REST has some drawbacks:

- **No type safety**: JSON is a dynamic format, so it is easy to make mistakes when defining data structures.
- **Slow**: JSON is not the most efficient format for data serialization.
- **OpenAPI**: To ensure that clients and servers are using the same data structures, OpenAPI is used to define the API. However, OpenAPI does not guarantee that both sides are using the same data structures.

Potwire aims to solve these problems by using **Protocol Buffers** for data exchange between clients and servers, providing strong type safety and fast data serialization.

## Why protobufs?

[Protocol Buffers](https://protobuf.dev/) is a language-agnostic data serialization format developed by Google. It is designed to be fast, efficient, and extensible. It is widely used in server-to-server communication, but not as much in client-server communication.

The main advantage of using Protocol Buffers is that it provides a **type-safe** way to define data structures. This means that the data structures are defined in a `.proto` file, and the **generated code** in the client and server will ensure that the data structures are used correctly.

[gRPC](http://grpc.io) is commonly used for server-to-server communication with Protocol Buffers due to its efficiency and support for a lot of languages (both as clients and servers). However, gRPC relies on HTTP/2, which is not fully supported by browser.

## How does it work?

There is a way to use Protobuf and have generated clients and servers using HTTP/1.1 (supported by browsers): [ConnectRPC](https://connectrpc.com/), a library that generates client and server code for Protocol Buffers, and uses HTTP/1.1 for communication. It has **native support for browser clients** and several server languages (Node.js, Go).

A nice feature of ConnectRPC is that it is compatible with gRPC clients, so you can have a ConnectRPC server and both ConnectRPC and gRPC clients (useful for mobile clients).