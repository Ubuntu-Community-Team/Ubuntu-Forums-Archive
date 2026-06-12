---
title: "Belkin PCMCIA F5D7011B and Ubuntu 8.04"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by dsgg10 on 2008-08-27
Hi All,

Newbie to the linux world, but I have installed 8.04 on my old laptop. I have the belkin G+ F5D7011B PCMCIA wireless card. I have done the following

1. *sudo gpedit /etc/modprobe.d/blacklist* - the entry already exists for **blacklist bcm43xx** - So I havent changed this file

2. I installed the latest ndiswrapper packages (x2) from the ubuntu site
3. I installed the latest bcmwl5.inf and .sys files
4. *sudo ndiswrapper -i /home/dave/Drivers/bcmwl5.inf*
5. *sudo ndiswrapper -l* Which says **bcmwl5 : driver installed** device (14E4:4318) present (alternate driver: bcm43xx)
6. *sudo gpedit /etc/modules* and added ndiswrapper to the end of the file. 
7. *lspci* reports Network controller Broadcom Corp BCM4318  [Airforce One 54g] 802.g Wireless LAN Controller (rev 02)

I can create my wireless network, but it never gets any signal BUT  - the power light is not showing on the PCMCIA card itself!!

What else do I need to do?????

Regards

Dave

---

