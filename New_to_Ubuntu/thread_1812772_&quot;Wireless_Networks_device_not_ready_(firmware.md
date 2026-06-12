---
title: "&quot;Wireless Networks device not ready (firmware missing)&quot; Please Help.!"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by johnl2219 on 2011-07-26
OK So i am a complete newbie to Ubuntu, I've installed Ubuntu 11.04 on a side partition on my Hp mini, next to windows. I've tried countless things to connect it to a wireless network and nothing seems to work. Please help..! Thanks.  :D

---

### Post by skatinjj on 2011-07-26
Can you open the terminal and post the output of this:

```
lspci
```

---

### Post by katakaio on 2011-07-26
If it's anything like my HP, you'll need the b43-fwcutter package. Check [this thread]("http://ubuntuforums.org/showthread.php?t=1812789&highlight=fwcutter") out for the details. Basically, the tool will extract the firmware you need (so long as it's a BCM43xx wireless card) and get your wireless running. Do follow skatinjj's advice first and tell us what your lspci returns.

---

### Post by Roter1337 on 2011-07-26
Yes, Tell us the output, and also connect to the ethernet and try running jockey-gtk through terminal

---

### Post by wildmanne39 on 2011-07-27
Hi, you might as well run all these commands it will save some time.
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

