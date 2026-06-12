---
title: "network suddenly stopped working"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by scottbot84 on 2006-11-06
Hi first problem I havn't been able to solve. I custom compiled a 2.6.17 kernel w/ the beyond4 patches for my sony vaio laptop. I had no module for my wpc11(linksys, rtl8180) and I was working on compiling a working module for my new kernel. 

Odly enough this isn't my problem. While working on this my on-board ethernet stopped working, and even when I boot w/ a working kernel(stock or custom) my wireless and ethernet won't work.The required modules are loaded if i look with lsmod. I have xubg-recuntu edgy installed w/ network-manager. Also even when i use kismet I can't detect my wireless network, although my card seems to go into monitor mode fine.

 My router is happily serving both my wired and wireless netowork clients.Even if i connect my cable modem to my laptop directly,nthing happens. Network manager attempts to connect yet can't aquire an address. even if i disable network-manager and enable my eth0 connection in /etc/network/interface" with no sucess.s,i still cannot aquire an address. I also reconfigured dhcp3-client with dpkg-reconfigure

 Nothing I was doing before the last restart should have affected anything. This is incredibly frustrating and i would rather not reinstall everything. If anyone has any ideas or any logfiles they'd like to see or i should check any help would be appreciated. 

P.s. compiled same kernel as mentioned above on a seperate system and everything works fine.

---

### Post by scottbot84 on 2006-11-06
OK problem fixed itself must have been something else.

---

