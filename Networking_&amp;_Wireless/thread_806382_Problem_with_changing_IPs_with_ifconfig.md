---
title: "Problem with changing IPs with ifconfig"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Madman6510 on 2008-05-24
Hey, I'm trying to change the IP on my server to a static IP, so I do a ```
sudo ifconfig eth0 192.168.0.51
```

That works great, until someone resets the server, when it resets back to having (gasp) NO IP, which is apparently kinda bad, because this is a fileserver.

What I need to know is how to make the server's IP static, and stay the same, even when it gets reset.

---

### Post by bwhite82 on 2008-05-24
Insert the static IP in /etc/network/interfaces

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

