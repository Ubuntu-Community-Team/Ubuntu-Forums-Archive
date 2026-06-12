---
title: "Ubuntu Natty will reinstalling older kernal fix my wireless?"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by KBD47 on 2011-09-06
Recent updates have made my wireless buggy in Natty. I'm getting slow connections and it will show I'm connected but wireless won't work. My wireless worked fine before recent updates, so I'm wonder if there is some way to back up my system to an earlier kernal or otherwise move back to an earlier state when my wireless worked well.
Thanks!
KBD

---

### Post by TBABill on 2011-09-06
Have you tried booting into an older kernel listed in Grub's menu or do you only have a single kernel to choose from?

---

### Post by wildmanne39 on 2011-09-06
Hi, also if you want to  work on why it is not working right since the upgrade post the results of these commands please:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by KBD47 on 2011-09-19
Thanks guys! I should have remembered the grub menu.

---

