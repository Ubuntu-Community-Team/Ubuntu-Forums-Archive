---
title: "Broadcom 4311"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by logan10 on 2013-09-06
Okay so I've looked this up quite extensively and I just don't know where else to turn. I recently installed 12.04 on a Dell Inspiron 1525 laptop and the wireless didn't work. Albeit weird, I installed Ubuntu regardless. I then logged on and found the wifi still not working. I did the whole rfkill list and whatnot to no avail. It was like I don't even have a wireless card as it didn't appear under sudo rfkill list all. But the wifi was working under windows 7 just moments before I made the switch. Help please?

On a side note, I am having the same exact issue with an HP Pavillion dv2000. Maybe it's a hardware issue, as they have similar switches? I know the switch is broken on the HP as it also didn't work in Windows, but there was a workaround with the HP wireless assistant. I've installed Ubuntu on countless computers, yet these two are the only ones that have given me a hard time, which is ironic since they're newer machines than a lot of the others.

---

### Post by logan10 on 2013-09-06
I looked it up more and found that both run the  Broadcom 4311 card, though the aforementioned methods did not work....help??

---

### Post by wildmanne39 on 2013-09-06
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe -v b43
```
Thanks

---

### Post by logan10 on 2013-09-07
it said "E: Unable to locate package linux-firmware-nonfree"

---

### Post by wildmanne39 on 2013-09-07
Did you have a wired internet connection when you ran the command?
Thanks

---

### Post by logan10 on 2013-09-07
I did have a wired connection when i ran the commands. Also at one point I got it to do the first two commands but nothing happened after I typed the last one

EDIT - After installing a fresh boot of Linux and following the above commands and then updating all packages and restarting, I have gotten the wifi to work flawlessly

---

### Post by wildmanne39 on 2013-09-07
Thats great!
Enjoy

---

