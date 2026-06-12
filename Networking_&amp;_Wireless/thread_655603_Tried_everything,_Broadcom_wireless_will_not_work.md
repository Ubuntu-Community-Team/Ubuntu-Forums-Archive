---
title: "Tried everything, Broadcom wireless will not work"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by downzero on 2008-01-01
I really feel as if I've tried everything.  ndiswrapper says my hardware is present (and at one time, I saw the blue LED come on) but it has NEVER worked.

I have an HP ZV6131US.  The processor, hard disk, and RAM have been upgraded but other than that, it's stock.

This is pretty much the last frontier when it comes to ditching windows forever.  

No matter what I do, there is no wireless connection displayed in my network manager, and I can't figure out how to get the LED display to come back on.

It is the Broadcom 4318 that everyone seems to have problems with.  Compaq's R4000 is the same as an HP ZV6000.

---

### Post by luisromangz on 2008-01-01
I have my broadcom wireless card working flawlessly on my compaq presario M2000, can you tell us the output of ifconfig and iwconfig?

---

### Post by kevdog on 2008-01-01
Id really recommend ndiswrapper for you.  Here is probably a good thread to take a look at.  It should be straight forward since this has been done a lot:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by downzero on 2008-01-02
> **kevdog said:**
> Id really recommend ndiswrapper for you.  Here is probably a good thread to take a look at.  It should be straight forward since this has been done a lot:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Did the entire process, it installed a bunch of stuff.  None of it made my wireless work.  There isn't even a wireless adapter shown in the network manager.

My wired NIC card and modem are shown in the network manager...just no wireless.

---

### Post by kevdog on 2008-01-02
Can you post lshw -C network.  This is Linux, cant always depend on the GUI.

---

### Post by downzero on 2008-01-03
> **kevdog said:**
> Can you post lshw -C network.  This is Linux, cant always depend on the GUI.

Agreed.  I know how to use dos, it's just tough to use a command prompt where all the commands are different.

I'll post the contents of that file for you ASAP.

I didn't expect everything to be configured with the GUI, and I really don't give a rat's *** what method I have to use to get firmware that works as long as my wireless cards works in  the linux environment so I can ditch windows forever.

---

### Post by SactoBob on 2008-01-03
It was a similar problem that got me into using no-hassle wireless bridges.
See [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871) for a hardware solution that will give you better performance and less hassle than a pci card.

---

