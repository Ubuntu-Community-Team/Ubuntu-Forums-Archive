---
title: "How to run scanner BearPaw 1200cs on Ubuntu"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Dedi Landsman on 2009-10-22
Hi, i was given a scanner Mustec BearPaw 1200 CS [so it is written on its panel]. I have plugged it in, pressed: Applications >Graphics > Xsane immage scanning program. in the window that apears, there is the choise:
** Mustec BearPaw  2448 TA Flatbed scanner [gt68xx:libsub:004:002]**
[why is it there is a discrepancy with the model's number?]
when i mark the button for that [the other choice is for video camera], and clich OK, i get the following small window message:
[B]Eror 
Faile to open device[/B] [B]gt68xx:libsub:004:002: invalid argument.
[/B]What is this? how to overcome it?
Thanks for any Help.

---

### Post by welshmike on 2010-10-15
Sorry about late reply but I had the same problem in 2008 on Ubuntu 8.04. I've recently bought a new PC and have been getting it up to speed on Ubuntu 10.04.
Digging deep I found an old forum message of mine at [http://ubuntuforums.org/showthread.php?t=903645](http://ubuntuforums.org/showthread.php?t=903645) message #5.
This is what I did today to get my BearPaw 1200CS working:
Copied file A1fw.usb from installation CD to desktop
Opened a terminal and ran the following command lines:
```
mike@mike-i3-notebook:~$ sudo cp /home/mike/Desktop/A1fw.usb /usr/share/sane/gt68xx/
[sudo] password for mike:
mike@mike-i3-notebook:~$ sudo chmod a+r /usr/share/sane/gt68xx/A1fw.usb
mike@mike-i3-notebook:~$
```

---

