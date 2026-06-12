---
title: "interent"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by windows hater on 2009-01-26
hello i just recieved a wireless-n usb network adpater by linksys
and ubuntu doesnt even notice it

any help would be great

---

### Post by blueridgedog on 2009-01-26
This thread has some ideas:

[http://ubuntuforums.org/showthread.php?t=466807](http://ubuntuforums.org/showthread.php?t=466807)

---

### Post by handydan918 on 2009-01-26
To find out if Ubu notices the device, try a few of the following, and post the output back here. 

```
lsusb
lspci
lsmod
dmesg | tail -20

```

After all that, if you get ignored here, try researching ndiswrapper. Many wireless chips that aren't yet supported under linux will work under ndiswrapper.

---

