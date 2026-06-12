---
title: "DELL Inspiron 6400 WiFi not working"
date: 2016-01-23
forum: Networking &amp; Wireless
---

### Post by vime80gmail.com on 2016-01-23
Good evening. I just installed Ubuntu 15.10 on a DELL Inspiron 6400 and the wifi doesn't work. I read on this forum that other people had the same problem and i tried to fix it following the instruction already posted in the past but nothing worked for me. Is there someone that can help with this?
Thank you

---

### Post by howefield on 2016-01-23
Let's start by moving your thread to the "*Networking & Wireless*" forum.

---

### Post by Hadaka on 2016-01-24
Hi,please start by verifying your wifif card,
[URL="http://ubuntuforums.org/showthread.php?t=2214110"]http://ubuntuforums.org/showthread.php?t=2214110
[/URL]then from a working wired connection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

thanks

---

### Post by vime80gmail.com on 2016-01-24
Unfortunately i don't have a wired connection either. I tried to set up a pppoe connection but i couldn't... first steps in ubuntu!

---

### Post by Hadaka on 2016-01-24
Not a problem,we can load your b43 dirver without internet access.
Let's first verify that b43 will be the best driver for you. Please open
a terminal-ctrl/alt/t- then COPY and paste..
```
lspci -n | awk '/14e/{print$3}'
```
post the output
thanks

---

### Post by vime80gmail.com on 2016-01-26
```

1002:7145
14e4:170c
14e4:4311

```

Thank you

---

### Post by Hadaka on 2016-01-26
Hi, first drag and drop the b43 zip file at the bottom of this post to your Desktop
then right click it and choose 'Extract Here'
then open a terminal ..ctrl/alt/t and copy and paste one
line at a time.*ignore any file not found or minor error/warning.
this line may error, it is not a problem..contine and do each line.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
```   [ATTACH=CONFIG]266968[/ATTACH]

---

### Post by vime80gmail.com on 2016-01-28
It worked! Thank you very much for your help! Looking forward to work on Ubuntu now!

---

### Post by Hadaka on 2016-01-28
Great , glad to hear that worked for you !

Please log back in to your thread,first post and
click TOOLS then SOLVED.
thanks.

---

