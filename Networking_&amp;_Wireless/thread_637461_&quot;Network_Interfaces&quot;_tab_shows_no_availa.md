---
title: "&quot;Network Interfaces&quot; tab shows no available network interfaces"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by hoboghost on 2007-12-11
I am a newb to linux and I just completed my first install of Kubuntu 7.04.

I had tried installing linuxmce (I failed) but while troubleshooting I did successfully download drivers from internet, so I am not sure why I can't get to the internet now.

I am plugged in a wireless router that is connected to the dsl modem.  The router runs a dhcp server.  All other computers on the network are connecting without problem to the router.


After googling some, and trying to follow this guide[http://kudos.berlios.de/kf/kisimlar/network.html]("http://kudos.berlios.de/kf/kisimlar/network.html")
I wonder if there is something wrong with my install.  IN admin mode under network settings, at the "Network Interfaces" tab there should be a list, or at least "eth0" correct?  Mine is greyed out and empty.   

[IMG]http://img.photobucket.com/albums/v499/hobostreet/DSCF1630-1.jpg[/IMG]
I also have an abit airpace WLP-01 wireless card installed (but i have not set up drivers for it yet, so that shouldn't even be detected--thus the tyring to connect through ethernet cable first)
Any help you can give me would be much appreciated.

---

### Post by hoboghost on 2007-12-11
OK.  So it is not grayed out when I am in admin mode, but it is still empty.  And when I right-click on the empty space it gives me an error mesage:  "The application KDE Control Module (Kcmshell) crashed and caused the signal 11 (SIGSEGV)."

---

### Post by kevdog on 2007-12-11
Can you post lshw -C network?

---

### Post by hoboghost on 2007-12-13
> **kevdog said:**
> Can you post lshw -C network?

Ok, I did that command in konsole and got this:

*-network UNCLAIMED
   description: Ethernet controller
   product:  Atheros Communications, Inc.
  vendor:  Atheros Communicaitons, Inc.
  physical id: 0
  bus info: pci@03:00.0
  Version: 01
  Width: 64 bits
  clock: 33MHz
  capabilities: cap_list
  configuration:  latency=0
  resources: iomemory:fddf0000-fddfffff irq:21

thanks if in advance

---

### Post by hoboghost on 2007-12-13
ok I fixed it.  My onboard lan was disabled.  Not sure why.  But fixed it.  thanks.

---

