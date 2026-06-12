---
title: "missing tun-device"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Pintel on 2008-05-17
I just updatet to Ubuntu 8.04. Now I am not longer able to run my openvpn. Also I installed the openvpn packages and put the keys and the configs back in the right directorys my openvpn does not run.

It seems that I have problems with the tun-device. I made a 
"sudo modeprobe tun" but I still cant find it with "ifconfig -a". It is just not there.

"lsmod | grep tun" put out: "tun 12672 0"

Any ideas? 

Pintel

---

