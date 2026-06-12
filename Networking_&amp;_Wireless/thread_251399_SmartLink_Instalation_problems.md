---
title: "SmartLink Instalation problems"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by LinuxUnder on 2006-09-05
Hi there, I have a SmartLink pci modem on my desktop and I´m using Ubuntu 6.06. I found a website that I can download individually .deb packages for ubuntu in any of its versions. When I installed it appears to go everything all right also it makes the symbolic link port, but when I tried to configure it with wvdialconf, I wasn´t able to beacuse it didn´t found it, what can I do? or maybe someone could send me a link of repositories where I can donwload the drivers and let the system install it for me.

Thanks in advance

---

### Post by _duncan_ on 2006-09-09
Hi. I was able to get on-line using a smartlink pci modem by just following this how-to:

[Howto Conexant and SmartLink modem]("http://www.ubuntuforums.org/showthread.php?t=190728").

I couldn't get wvdial to work on both Ubuntu Breezy 5.10 and Dapper Drake 6.06, but **pppconfig** (together with **pon** and **poff** commands) works just fine. The graphical gnome-PPP also doesn't seem to work.

I remember that even with the symbolic link set, pppconfig still couldn't auto-detect the modem. But manually typing **/dev/modem** should do the trick. Of course I'm assuming that the driver was compiled correctly following the instructions on the how-to.

---

