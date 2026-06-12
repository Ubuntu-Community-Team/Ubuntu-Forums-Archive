---
title: "Can't Access Windows/Samba Shares Unless I Hangup Internet Connection"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Malac on 2007-02-12
I have searched for this on the forum and whilst I get loads of tutorials how to set up samba/windows shares, none of them seem to mention this.
It's probably something really simple like a replace defaultroute in a text file somewhere but I don't know.
So, I have one "server/gateway" machine(Ubuntu 6.10) which is sharing it's internet connection with three other machines(all Windows XP) all works fine in this respect.
The three XP machines can all see shares on the Ubuntu gateway pc whether it is connected to the internet or not but the Ubuntu pc cannot see the shares on the 3 XP machines until I hangup the internet connection then as if by magic all the shares are available and I can browse the LAN.
I am not that knowledgeable about the processes that take place but I assume it's some sort of routing problem, like it is trying to find the shares on the ppp0 (internet connection) instead of eth0 until ppp0 is taken down.
The LAN is using fixed IP and the internet is via USB ADSL dialup on ppp0 with Dynamic IP set via DHCP of providers servers.
Any more info required let me know.
Thanks.

---

### Post by ukripper on 2007-02-13
Are you running web or FTP server? If you are then probably samba is confused with your services.

Also, try re-installing samba from scratch :

$ sudo apt-get remove samba
$ sudo apt-get install samba

---

