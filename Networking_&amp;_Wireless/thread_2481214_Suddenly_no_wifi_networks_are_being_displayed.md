---
title: "Suddenly no wifi networks are being displayed"
date: 2022-11-22
forum: Networking &amp; Wireless
---

### Post by greenapplebee on 2022-11-22
I'm a complete Linux noob, but i really need to fix this issue by today. Even partial help to nudge me in the right direction is very appreciated.
Couple of months ago i installed ubuntu 20.04 on my laptop. Everything (including wifi of course) worked fine until yesterday, when i noticed that the wifi icon at the top right of the screen was not being displayed, and trying to search for any networks through the GUI gives no results. 
I have ran the command :
```
nmcli general status
```
```
STATE                       CONNECTIVITY     WIFI-HW  WIFI      WWAN-HW  WWAN
connected(local only)  limited                 enabled   enabled  enabled       enabled
```

and then the command:
```
nmcli device show
```
```
GENERAL.DEVICE       wlp4s0
GENERAL.TYPE         wifi
GENERAL.HWADDR       10:6F:D9:9D:8F:4B
GENERAL.MTU          1500
GENERAL.STATE        30(disconnected)
GENERAL.CONNECTION   --
GENERAL.CON-PATH     --
WIRED-PROPERTIES.CARRIER       off
```

I do not know how to proceed from here. I have been searching for a couple of hours on the internet but getting even the most basic information has proven to be hard (not even sure what the data displayed means).
Thanks to anyone who will take time to answer a probably very stupid post

---

### Post by chili555 on 2022-11-22
Let's gather a few more details. Please run and post:

```
rfkill list all
sudo dmesg | grep wlp

```
Thanks!

---

