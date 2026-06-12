---
title: "how can i get this wireless usb adapter to work?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-12-31
i have a installation CD for it, but its for windows.....

when i plug it in, nothing happens

its a linksys wireless usb adapter....

---

### Post by tuxxy on 2008-12-31
USB wireless adapters can be a pain, you couldcheck the hardware wiki for your model to see if its supported first.

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by oilchangeguy on 2008-12-31
> **hyperhopper said:**
> i have a installation CD for it, but its for windows.....

when i plug it in, nothing happens

its a linksys wireless usb adapter....

i'm running a linksys usb, and it works fine. have you tried to configure your wireless connection? just saying nothing happens is very vague. what have you done to make something happen?

---

### Post by hyperhopper on 2008-12-31
it lists netgear WPN311, 

but nothing else that i have

i have a NETgear WPN111, but when i plug it in, nothing happens!

i just have no clue what to do....

my wii connects to the wireless network in qquestion just fine!

in windows it automatically works out of the box!

---

### Post by oilchangeguy on 2008-12-31
> **hyperhopper said:**
> it lists netgear WPN311, 

but nothing else that i have

i have a NETgear WPN111, but when i plug it in, nothing happens!

i just have no clue what to do....

my wii connects to the wireless network in qquestion just fine!

in windows it automatically works out of the box!

see the two screened icon near the clock? that's the network manager. open it, highlight the wlan0 connection, click on configure, and follow the prompts.

---

### Post by hyperhopper on 2008-12-31
> **oilchangeguy said:**
> see the two screened icon near the clock? that's the network manager. open it, highlight the wlan0 connection, click on configure, and follow the prompts.
```
configuration could not be loaded
you are not allowed to access system information
```

i get this error when i click it!


also, what do you mean by open it?

when i left click, i get a grayed out "wired connection" and a "manual configuration" poping up in a menu

---

### Post by oilchangeguy on 2008-12-31
found this, about the error message. it's old, but still may help:
[http://ubuntuforums.org/showthread.php?t=423930](http://ubuntuforums.org/showthread.php?t=423930)

---

### Post by hyperhopper on 2008-12-31
> **oilchangeguy said:**
> found this, about the error message. it's old, but still may help:
[http://ubuntuforums.org/showthread.php?t=423930](http://ubuntuforums.org/showthread.php?t=423930)
the fix for that requires being online, and i cannot go online untill i fix it

circular reasoning works because circular reasoning works because circular reasoning works because circular reasoning works because circular reasoning works because ........

---

### Post by Tom--d on 2008-12-31
Can you post the outcome of lsusb please. (Go to Applications > Accessories > Terminal > lsusb > Post the outcome.)


Consider using Ndiswrapper. It wraps Windows Wireless drivers and get wireless on Linux. I use it :)

Go to Add/Remove and install Windows Wireless Drivers (You need a internet connection for like 2 seconds. Cable?)
Then on your CD. You need to find a .inf and .sys in the SAME folder. If so, go to System > Admin > Windows Wireless Drivers > Install > locate the .inf from the CD and Install! Should work.
Then go to the network Icon and you should see Wireless Access Points.

---

