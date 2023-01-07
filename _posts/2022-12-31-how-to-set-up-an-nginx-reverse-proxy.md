---
title: How to Set Up an Nginx Reverse Proxy
tags: nginx, proxy, reverse proxy
---

## 1. Introduction

Wikipedia define [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy)

> In computer networks, a reverse proxy is the application that sits in front of back-end applications and forwards client (e.g. browser) requests to those applications. Reverse proxies help increase scalability, performance, resilience and security. The resources returned to the client appear as if they originated from the web server itself.

> Large websites and content delivery networks use reverse proxies, together with other techniques, to balance the load between internal servers. Reverse proxies can keep a cache of static content, which further reduces the load on these internal servers and the internal network. It is also common for reverse proxies to add features such as compression or TLS encryption to the communication channel between the client and the reverse proxy.

> Reverse proxies are typically owned or managed by the web service, and they are accessed by clients from the public Internet. In contrast, a forward proxy is typically managed by a client (or their company) who is restricted to a private, internal network, except that the client can ask the forward proxy to retrieve resources from the public Internet on behalf of the client.

> Reverse proxy servers are implemented in popular open-source web servers such as Apache, Nginx, and Caddy. This software can inspect HTTP headers, which, for example, allows it to present a single IP address to the Internet while relaying requests to different internal servers based on the domain name of the HTTP request. Dedicated reverse proxy servers such as the open source software HAProxy and Squid are used by some of the biggest websites on the Internet.

Reverse Proxies are used to protect the server. A reverse proxy acts as a connection point for clients, users, and application servers. It manages all access policies and traffic routing, as well as protects the identity of the server that handles the request.

Load balancing for a website that receives a lot of requests is an example of a Reverse proxy use case. Assume that your website servers receive hundreds of requests at the same time. What do you think would happen if this happened? It wouldn't be able to process anything and would finally crash. As a result, load balancing requires numerous origin servers. A reverse proxy server intercepts all requests and ensures that traffic is distributed evenly across all of your servers. Reverse proxies can redirect extra traffic to other servers, allowing your website to stay up and running.

**Reverse Proxy Architecture:**

![Reverse Proxy Architecture](/assets//images/post/reseve-proxy-architecture.webp)

In this tutorial, we’ll show you what an Nginx reverse proxy is and how to set it up on your VPS.

## 2. Advantages/ disadvantages
### 2.1. Advantages
Let's delve into the reasons why this tool is so popular:
- Load Balancing
  > To handle popular websites that get millions of users every day, you can a reverse proxy since it provides a load balancing solution that helps distribute the incoming traffic evenly among the different servers. It eventually prevents any single server from becoming overloaded. In the event that a server fails completely, other servers can step up to handle the traffic.
- Protection From Attacks
  > A reverse proxy helps a website or service hide the IP address of its origin server(s), making it harder for attackers to leverage a targeted attack against them, such as a DDoS attack.
- Global Server Load Balancing (GSLB)
  > Using GSLB, a website can be distributed on several servers around the globe. A reverse proxy in such a case will help send clients to the server that’s geographically closest to them, decreasing the distances for requests and responses to be traveled, which eventually minimizes load times.
- Caching
  > A reverse proxy can also cache content, resulting in faster performance. For instance, if a user in India visits a reverse-proxied website with web servers in Londo, the user might actually connect to a local reverse proxy server in India, which will then have to communicate with an origin server in London.
- SSL Encryption
  > You can configure a reverse proxy to decrypt all incoming requests and encrypt all outgoing responses, freeing up valuable resources on the origin server.
### 2.2. Disadvantages

## 3. Setup

### 3.1. Install nginx
We’ll be using the apt command on Ubuntu 20.04:
```bash
sudo apt-get update
sudo apt-get install nginx
```
### 3.2. Create the Nginx Block Server
After install nginx, we need to create block server. Next step, we create a file called ```my-server.conf``` within the ```etc/nginx/conf.d``` directory to keep reverse proxy information. 
```bash
cd etc/nginx/conf.d
vi my-server.conf
```

### 3.3. Create the Nginx Reverse Proxy
```bash
cd etc/nginx/conf.d
```

### 3.4. Setup ssl

#### 3.4.1. Config ssl with certbot
The first step to using Let’s Encrypt to obtain an SSL certificate is to install the Certbot software on your server.

Install Certbot and it’s Nginx plugin with apt:
```bash
sudo apt install certbot python3-certbot-nginx
```
Certbot is now ready to use, but in order for it to automatically configure SSL for Nginx, we need to verify some of Nginx’s configuration.

Next step, we config ssl
#### 3.4.2. Config ssl with available ssl

We hope this post helps you.