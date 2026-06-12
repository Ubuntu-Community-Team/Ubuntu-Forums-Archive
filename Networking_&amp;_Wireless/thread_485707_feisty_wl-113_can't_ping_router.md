---
title: "feisty wl-113 can't ping router"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by v3ng3ful on 2007-06-27
Hello to everyone,
I'm new to ubuntu and need your help. After hours of trying and following guides, i finaly got my wl-113 sitecom wireless usb working ^^. Although i have a strange problem. I have a second pc with wired connection. It is very strange.. i can ping from wireless to wired pc, and vise versa, but wireless pc cannot ping to router! The wired pc can create succesful connections with router, the wireless pc isn't possible to connect making me unable to connect to internet. I can show u any information if you want, but i 'm so noob that i dont know the commands -.-  . If you have any idea plz inform me :D
Ubuntu feisty 7.04 
thnx

---

### Post by crashovaride on 2007-06-28
do an iwconfig eth# (possibly 1) and see if your networking card is in monitor mode. If it is, you should run the following command:

iwconfig eth# essid "accesspoint" key "yourkey" mode="managed"

I have noticed that if you have set your wep key improperly Linux will not pick it up, and windows will. So, hopefully that has pointed you in the right direction.

good luck.

---

### Post by Austin_KW on 2007-06-28
Restart networking or reboot.  Probably just stale information (routing/arp cache)

---

