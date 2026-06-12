---
title: "How do I stress test my server network?"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by Higgins909 on 2015-03-08
I want to stress test my ubuntu server on my home network, how do I do so?
I remember once I had like 3 virtual boxes open and had them all ping it, but it was pretty cpu intensive and it kept
hitting the terminal limit or something, and it was only going 100Mb...

Thanks,
Higgins909

---

### Post by TheFu on 2015-03-10
Depends. What is it serving?  Simulate that sort of traffic using common test tools. There are network performance tools, disk I/O performance tools, web-site traffic tools .... simulate the type of traffic the server is supposed to serve.

Oh - and virtualbox is NOT a good solution for servers.

---

