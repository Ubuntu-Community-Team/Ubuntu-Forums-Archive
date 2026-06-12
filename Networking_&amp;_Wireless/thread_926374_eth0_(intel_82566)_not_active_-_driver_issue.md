---
title: "eth0 (intel 82566) not active - driver issue?"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-09-21
For some reason my intel 82566 NIC is not active.  I have wireless though.  I have a feeling it is because when I installed Ubuntu, the wireless was active, so it didn't keep searching for network cards.  Maybe?  

Anyway, lspci kicks out
```
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
```
so it is definitely there, and recognized as being there.  I need to know how to activate it so I can connect to a router and turn the wireless functionality back on!!  

Maybe it is a driver issue, I am not sure. Any help would be appreciated.

---

### Post by pytheas22 on 2008-09-21
The fact that a device appears in the output of 'lspci' doesn't mean that the system 'recognizes' it.  It just means that the hardware is present...having a driver to drive it is another story.

What does the output of 'lshw -C Network' say?

I have an Intel ethernet card (not sure of the exact type) in one machine that for some reason is 'disabled' by default--I have to use 'ifconfig' to bring it up.  Then it works fine.  Perhaps you have the same problem.

Ubuntu should have detected all network interfaces on your computer, so it's not because you have wireless that you have problems with the ethernet.

If you post the output of 'lshw -C Network,' that should help to figure out what's going on.

---

### Post by jimmy the saint on 2008-09-22
False alarm here.  Sorry about that.

Tip:  when unplugging an ethernet cable from one device in order to hook a laptop up to a router, be sure that you are unplugging the cable from the device, not the router!!

---

