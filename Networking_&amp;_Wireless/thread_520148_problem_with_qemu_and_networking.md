---
title: "problem with qemu and networking"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by crixtiano on 2007-08-07
hi friends,

I'm having problems to configure network with qemu (Linux Ubuntu Feisty as host and Windows XP as guest).

I'm following the commands bellow:

> 	
$ sudo su - 
# aptitude install uml-utilities
# mkdir -p /dev/net
# mknod /dev/net/tun c 10 200
# modprobe tun
# echo 'tun' >> /etc/modules
# chgrp users /dev/net/tun
# chmod g+w /dev/net/tun
# exit
$ qemu -m 190  -win2k-hack -boot c hd_winxp.img


In guest OS I configure Windows XP :

> 
IP 172.20.0.2
MASK 255.255.0.0
GETWAY 192.168.0.1


But , if I do in guest OS the command:

> c:\> ping 172.20.0.1

the guest OS can't "see" the host 172.20.0.1

Why?

Please, may someone help me?

---

