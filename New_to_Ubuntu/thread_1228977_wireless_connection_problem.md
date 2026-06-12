---
title: "wireless connection problem"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by knarfman on 2009-08-01
just wondering if someone has any ideas....

installed current version ubuntu on my HP HDX18 (x64) on dual boot. also installed wireless router between my XP destop and my laptop wireless. all was working day before yesterday (i.e. when in ubuntu could get wireless connection to internet) but for some reason yesterday it told me could not connect to wireless. could still connect wirelessly in Vista however - so, am a bit confused as i did not make any changes and can still connect in one OS and not the other ??  :(

in an attempt to fix this, i stupidly deleted eth0 under the "wired setting" in edit connections when clicking on wireless network connections icon (top righthand icons on (my) screen). was thinking maybe it would reset when rebooted. no such luck.

in any case, i took ethernet connection from wireless router and plugged it into laptop and now have established internet connection running in ubuntu but the point is i want a wireless connection for my laptop obviously.

as i am new to linux and not a brainiac with computers, i am a bit confused as to why i can run a wireless connection in Vista and it will no longer work in Ubuntu (even before deleting the eth0 connection). 

oh yeah, i set up a dual link/connection between my broadband router and wireless router: desktop (XP)<-->broadband router<-->wireless router<-->wireless laptop (vista)

if any one could help me figure this out, i would be grateful. 

thanx lots.

---

### Post by LookTJ on 2009-08-01
Post
```
lspci | grep network -i
```Or:
(just in case you use a usb to connect wirelessly)```
lsusb
```:)

EDIT: Also, it might be a firmware/driver issue

---

### Post by knarfman on 2009-08-01
OMG, that just ***TOTALLY*** painlessly fixed my problem.

thanx a million ..... you rock! LOL. :D

---

### Post by knarfman on 2009-08-02
I may have spoken too soon -- while that command worked to reestablish an internet connection, I can no longer access my LAN XP desktop from my laptop. When I activated the Firestarter firewall, it is telling me I still have **no eth0**. I went through the firestarter GUI wizard and tried numerous combinations but to no avail.

The upthread terminal window fix did add some connection but not the eth0 which was there previously. (Not using a wireless USB connection).

Does anyone have any idea how to restablish this so I can reconnect to my network AND keep my internet connection going?? :confused::confused:  

Help!!!

---

