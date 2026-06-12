---
title: "activating rt2400 and system crashes"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by turok on 2006-10-31
Hi, i used to have ubuntu 6.06 installed on my computer and my wireless was working fine. I decided to install ubuntu 6.10, i configured my rt2400 wireless card and when i activated it (using the "networking" tool provided) the system crashes. This didn't happen with the previous ubuntu version. What can i do to activate my wireless card ?, is there any whay of doing this from console ?
Thanks a lot

---

### Post by hairypete on 2006-10-31
I've had exactly the same problem - any ideas?

---

### Post by turok on 2006-10-31
hey, i was messing arround with the "iwconfig" command and i typed "sudo iwconfig ra0 essid on" and it crashed. I rebooted the computer and tryed again and it worked, it automatically conected to mi ap :|

---

### Post by turok on 2006-11-02
Well, after all it didn't work and now it continues crashing. Does anyone know what to do ?
thanks in advance

---

### Post by GreenAG on 2006-11-08
I also have a problem with the **rt2400** kernel module. My brand new **Edgy** crashed just after the installation, at the first boot.
So using a LiveCD I blacklisted the module and the system booted without any problems. Then I tried inserting the module into kernel manually:
```
sudo modprobe rt2400
```
But when I pressed Enter the system hung up.
After that I downloaded the rt2400's **latest CVS tarball** and compiled the newest  version of the module. Now I'm able to insert it into the kernel, but I can't assign any AP or essid to the **ra0 interface**, because those operations still crash the system.
There's definitely something wrong, probably with the **Ubuntu 6.10 stock kernel**. I haven't had any problems with the rt2400 module when I was using other distros with the 2.6.17 kernel.

---

### Post by sgartner on 2006-12-27
I too am suffering from an identical issue, namely the system crashes when I try and enable the wireless network in the network manager.

I am running 6.10 and have fully updated the system via the package manager.

I have a wireless card with an rt2400 chipset; I determined this by running the lspci command.

I have updated the driver via the package manger, yet the issue persists – i.e. the system crashes when I try and enable the wireless network.

Do I need to do something outside of the package manager, in the terminal for instance to resolve this issue.

Thanks. steve

---

### Post by dmccor1 on 2007-03-21
I am having the same problem on Edgy.  Every time I try to activate the wireless connection the whole OS locks up.  Does anyone have any suggestions on how to fix this issue short of buying and external wireless bridge or Wireless USB adaptor?
Thanks!

---

### Post by TheSpark on 2007-03-31
I would also like to know how to fix this! Would really like to start playing with streaming media server...

---

### Post by penduluum on 2008-02-19
Same problem in Gutsy.  Even using ndiswrapper.  Any ideas?  Even just a confirmation that there is no fix would be helpful at this point.

---

### Post by jhetrick62 on 2008-02-19
You say you had the same problem with Ndiswrapper?   Did you build the driver from the windows files properly AND, did you properly blacklist the linux auto-installed driver???

If you did build the ndiswrapper module properly but did not blacklist the proper auto-installed driver, odds are it is still loading that and super-ceding the ndiswrapper driver.  I just had this happen with a different ralink chipset this weekend.  Once properly blacklisted, the ndiswrapper driver should work.  

Now my chipset was different so maybe there is a critical bug, but just insure the above is correct first.

Jeff

---

