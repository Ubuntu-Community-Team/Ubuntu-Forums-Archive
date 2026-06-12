---
title: "Download Manager with Multi proxy support"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by oneofth3m on 2007-07-05
I have been using Ubuntu for a while and currently running Ubuntu 7.04.


I would like to know if there are any download managers for linux that support multiple proxies like FlashGet and NetTransport for windows

They along with regular features of download manager like resume and downloading file from multiple locations support MultiProxy.

Since we have restricted bandwidth for each user by using these download managers in windows we can increase the download speed.

I would like to know if any such  download manager is available for LINUX.

---

### Post by kidders on 2007-07-06
Hi there,

I'm not altogether sure I'm understanding your post correctly, but if what you're looking to do is download a (probably large) large file using more than one HTTP proxy at the same time, I would run two or more **curl**s concurrently, and simply concatenate the results. For instance, if you had a 1kiB file you wanted to grab using two proxies...

```
http_proxy=proxy1:8080 curl -o part1 -r 0-511 http://www.host.com/file
http_proxy=proxy2:3128 curl -o part2 -r 512- http://www.host.com/file
```

---

