---
title: "Apache Access Log, whats this mean"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by skozzy on 2008-08-08
Recently I setup Xampp and opened a port on my router so Myself and a mate could work on a webpage project. In the access log I seem to be getting a lot of internet users trying to connect and the log records a few things I need advice on.

> 75.127.97.213 - - [09/Aug/2008:02:25:29 +1000] "CONNECT 85.17.6.78:6667 HTTP/1.0" 405 408
83.149.112.40 - - [09/Aug/2008:02:25:30 +1000] "CONNECT 72.20.25.230:6667 HTTP/1.0" 405 410
38.106.96.204 - - [09/Aug/2008:02:25:30 +1000] "CONNECT 85.17.6.78:6667 HTTP/1.0" 405 408
38.106.96.204 - - [09/Aug/2008:02:25:30 +1000] "POST [http://85.17.6.78:6667/](http://85.17.6.78:6667/) HTTP/1.0" 200 163


Can someone explain what could be going on here, to me it looks like someone is connecting to my computer to connect to another computer.

---

### Post by skozzy on 2008-08-08
Well maybe I have found the answer, but not entirly sure. But on one of the IRC servers I connect to, they do a quick port scan for a proxy server that could allow other people to attempt DOS attacks.

I tried connecting to the IRC server and roughly the same time index is a recording in the access_log from apache2. So to me that a sign I worked it out.

---

