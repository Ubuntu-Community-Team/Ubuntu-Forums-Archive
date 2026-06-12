---
title: "Can I speed up traffic to local apt-mirror server when inside LAN?"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2016-02-01
Hi community!
I have an apt-mirror server in my LAN behind a *WRT1900AC* router.
When I use the internal server IP with its open port in sources.list and update the apt-get cache the speed is super fast.
I wanted to be able to connect to this apt-mirror from the Internet, so I started using a dynamic domain server name service ([www.dynu.com](www.dynu.com), which is great by the way!). I am now able to connect to the *apt-mirror* server even when I am connected to Internet.
Now, what I noticed is that when I'm connected to my LAN, the speed when updating the apt-get cache is much slower (about 4 times). Here is where I think there might be a way to speed things up. I thought the problem could be avoided by using *dnsmasq* but it did not help at all. 
Is there any suggestions on how to configure my laptop/router to redirect the traffic straight to the *apt-mirror* server when I am connected to my LAN?
Thanks!

---

