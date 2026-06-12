---
title: "networking issue with ubuntu server in virtualbox"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Gungy on 2008-12-02
Hello, i m currently trying to setup an ubuntu server ( hardy heron, some image that was already configured vor the virtual box) in my virtualbox, it is starting fine and i also configured my eth1 with ```
ifconfig eth1 192.168.2.39
```. 
my problem now is, that i cant get access from my ubuntu server to the internet nor to my host system, a ```
ping 192.168.2.39
``` in ubuntu is working fine, a ```
ping 192.168.2.1
``` (router adress) is giving an DESTINATION HOST UNREACHABLE to me. A ping to some external ip is giving me a NETWORK UNREACHABLE.

Any ideas how to get my ubuntu server to connect to the internet?

setup: windows xp as host ( 192.168.2.34 with dhcp)
       router (192.168.2.1)
       ubuntu as guest ( 192.168.2.39 no dhcp i guess)

thx in advance

i hope its the right forum here, i m a total newbie

---

### Post by superprash2003 on 2008-12-02
thats because you havent specified your gateway . Follow this [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html) instead of eth0 use eth1 and instead of 192.168.1.10 use 192.168.2.39 and instead of 192.168.1.1 use 192.168.2.1

---

