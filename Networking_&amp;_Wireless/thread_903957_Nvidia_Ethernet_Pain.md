---
title: "Nvidia Ethernet Pain"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by circusmonkey on 2008-08-28
Ethernet Pain 

I have a p5n32-e sli motherboard. it ran fiesty fawn 7.04 just fine.as per 
[http://tracylogan.com/index.cfm?event=showEntry&entryId=54B68B3D-0F10-768D-AA4C84EEDC35F5B6](http://tracylogan.com/index.cfm?event=showEntry&entryId=54B68B3D-0F10-768D-AA4C84EEDC35F5B6)
I upgraded to 8.04 , then I find out that people using my motherboard with the 680i nvidia ethernet connection have to run a fix so you can connect to the internet.As per the fix here 

[https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)



To get this settings permanent create (as root)  /etc/modprobe.d/config. Add the line:

options forcedeth msi=0 msix=0

and save. Then rebuild the initramfs with

update-initramfs -u -k $(uname -r)


I have ran the above and yet still I cannot connect to the internet , it seems this crappy mobo has difficulties with any new flavour of linux. Has anyone actually fixed this and got it to work ?

---

### Post by cleanse fold &amp; manipulate on 2008-09-11
Yes I've got it to work, however I followed the bug thread and rather than updating  /etc/modprobe.d/config  I created /etc/fmodprobe.d/orcedeth
as root with following

gksudo gedit /etc/fmodprobe.d/orcedeth

then added the line

options forcedeth msi=0 msix=0

and rebuild the initramfs as you mentioned.

This worked for me.

---

