---
title: "After upgr. to Edgy: Forcedeth driver not working, unable to install nvnet"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by borq on 2006-11-01
Ola,

I've got a problem getting the networkdriver to work after an upgrade from Dapper to Edgy.

Shuttle XPC SN21G5
chipset: NVIDIA GeForce 6100 GPU and NVIDIA nForce 410 MCP
LAN controller: Integrated Fast Ethernet network controller with Realtek 8201 PHY

When installing 6.06 I couldn't get the forcedeth driver to work properly
After some fiddling around I got my network working with nvnet like described here:
[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)

Unfortunately this trick doesn't seem to work for Edgy / 6.10.
After the upgrade there was no eth0 to be found in ifconfig so I installed the linux-headers (gcc was still there) and tried to run the nforce package (NFORCE-Linux-x86-1.0-0310-pkg1.run)
It quits while trying to compile the driver, saying that it didn't install..

My question: should the NvNetInstallation trick work for Edgy too (my best guess then is that it would be gcc related, wrong version), or should I be able to get the forcedeth drivers to work (if so, could anyone give me a push in the right direction)

I'll try to post the results of lspci -v, dmesg and /var/log/nvidia*installer.log (more?) tomorrow if needed, but since switching between OS's and posting/ saving these results without networkaccess is quite a bi**h, I was hoping someone could lighten my path based only on this..

thanks!

---

### Post by borq on 2006-11-02
the right answer was:
"or should I be able to get the forcedeth drivers to work"

forcedeth now works fine, it just turned out that in my init.d i had a script (nvnet) which did a modprobe -r forcedeth.. ](*,) 

don't forget to rm /etc/modprobe.d/nvnet and change /etc/modprobe.d/blacklist too

sorry for my royal n00bness.. what a night of sleep can't do ;)

---

