---
title: "USB 56k Modem Module in 8.04?"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by EmilyRose on 2008-05-11
I just upgraded from 7.10 and am very unhappy. I was using the Zoom external mini modem, which was using generic usb-modem module, I think. 

It no longer works in 8.04. Its an "unknown device" in my hardware info. Its not detected by anything, and does not create dev/ttyACM0 like it did before in 7.10. 

During boot up I get a message reading something about a generic linux usb module which does not/can not load, and am assuming that it is the problem. However I can't find that message in my syslog!! Just see it during boot up... do those messages you see during boot up print to somewhere besides /var/log/syslog.txt???

Is the usb-modem module included in 8.04? Is there a new version I can download from somewhere? If not, is there any way to downgrade to 7.10?? 

Lots of thanks in advance

---

### Post by jetsam on 2008-05-12
I probably can't help much with the hardware problem, but I can answer a few of your questions.  

> do those messages you see during boot up print to somewhere besides /var/log/syslog.txt???
You can view the bootup messages with:
```
dmesg
```

Make your particular message easier to find with:
```
dmesg | grep usb
```
...which will show just the bootup messages that contain the text "usb."

> If not, is there any way to downgrade to 7.10?? 
...There's no way to downgrade short of re-installing from the 7.10 disk.  That's a pain, and hopefully isn't necessary in your case.

---

