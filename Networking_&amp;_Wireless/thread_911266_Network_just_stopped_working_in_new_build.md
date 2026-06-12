---
title: "Network just stopped working in new build"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2008-09-05
I built a new system last night and everything was working fine, I started to mess with xorg.conf to get my video/mouse configured the way I wanted. After messing with the mouse configuration the network seemed to stop working.

On a side note, if it makes any difference, I pulled the hard drive from a Dell E1705 laptop and put it in this desktop without reinstalling to see if it worked and it did, I would like to keep it that way for now but can reinstall if necessary. 

Any suggestions on where I should start troubleshooting?

---

### Post by puppywhacker on 2008-09-05
since you transplanted the HDD you need to make sure that the network driver modules are loaded. you have to modprobe the module matching your network interface card.

1. the network card exists in the system
lspci | grep Ethernet

2. driver modules loaded
dmesg | grep eth

3. the physical link is up
sudo mii-tool

after that you might want to troubleshoot your ip-settings

---

