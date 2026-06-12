---
title: "Cannot Ping Gateway"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by oz3087 on 2008-12-28
Hi,

I have installed Ubuntu 8.10 on a Dell 5150 laptop and cannot ping the gateway or access the internet unless the following is keyed into a terminal session. I previously loaded a Dell 9400 laptop without any issues!

"sudo ifconig eth0 192.168.1.106 netmask 255.255.255.0"
"sudo ifconfig eth0 up"
"sudo route add default gw 192.168.1.254" 

Is it possible to make these settings permanent?

Thanks,

Neil.

---

### Post by RealPSL on 2008-12-28
This might help you establish that static ip address configuration

[http://www.cyberciti.biz/faq/ubuntu-static-ip/]("http://www.cyberciti.biz/faq/ubuntu-static-ip/")

---

### Post by oz3087 on 2008-12-29
Hi,

Thanks. I found the root cause. The IP allocated by the DSL router was a static IP for another computer on our home network. Once this was corrected the problem disappeared.

Regards,

Neil.

---

