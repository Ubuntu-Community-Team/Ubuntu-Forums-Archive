---
title: "Some questions about ubuntu"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by ninjachicken on 2009-12-27
So I just downloaded Ubuntu 9.10 this morning and installed it on my laptop as it's primary OS. Some more information about it, my laptop is a Dell Inspiron E1505 it came with windows XP media center. When I booted it up for the first time I tried to connect to my wireless router, alas I could not get it set up no matter how hard I tried. If anyone could enlighten me on how to go about setting up my wireless connection once again I would be thoroughly excited. Now on to my second matter that I would love to get some help with. I recently had seen a friend of mine with a 3d cube desktop and burning windows (the main reason why I wanted to switch to Ubuntu.) that I would like to try and recreate if at all possible. If anyone has information on part or all of this I would greatly appreciate an e-mail or a reply to this thread.

---

### Post by Cheesemill on 2009-12-27
For info about using Compiz (for the cube and burning windows) check this thread:
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by ninjachicken on 2009-12-27
Thank you very much that was extremely helpful and informative on the cube desktop and the burning windows.

---

### Post by sandyd on 2009-12-27
whats your wireless card model.

---

### Post by lotharmat on 2009-12-27
To find out what wireless card you have please could you post the results of the following commands (paste into the terminal; applications --> accessories --> terminal)

```
lspci
```

```
lsusb
```

---

### Post by Zoot7 on 2009-12-27
Chances are you've a Broadcom or "Dell" wireless card. They're not known for being Linux friendly really. 
Normally to get it to work you'll have to plug it into your router and enable the driver that is necessary for the wireless card via the "Hardware Drivers" tool.

---

### Post by sandyd on 2009-12-27
its a
 Dell wireless 1390 802.11g. which seems to be a broadcom card (correct me if im wrong)

options (one click install)
1. [URL="apt:/b43-fwcutter"][b43-fwcutter]
[/URL] 2. [[Broadcom STA drivers (wl)]]("apt:/bcmwl-kernel-source")

#2 reccomended.

---

### Post by ninjachicken on 2009-12-28
Thank you all for the information I did have to have it plugged in via Ethernet and that get hardware updates. You have all been a great help in every way.

---

