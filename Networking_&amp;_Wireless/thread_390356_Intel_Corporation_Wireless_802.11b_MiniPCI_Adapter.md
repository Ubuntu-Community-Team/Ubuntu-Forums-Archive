---
title: "Intel Corporation Wireless 802.11b MiniPCI Adapter not working"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by xnszxdotnet on 2007-03-21
I know that is question has been asked many times. I have also found the answer before on the forums but, now can't seen to find what I'm looking for.

lspci -v | less shows this:

02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 
01)
        Subsystem: Intel Corporation Wireless 802.11b MiniPCI Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

iwconfig shows this:

lo        no wireless extensions.

irda0     no wireless extensions.

eth1      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

I know that it can be done because I just had it working yesterday just fine. can someone point me in the right direction. I know that I have to blacklist something, I just don't know what.

thanx

---

### Post by chili555 on 2007-03-21
Please issue the command:```
lsmod | grep prism
```Add the result to /etc/modprobe.d/blacklist like this:```
blacklist prism2_whatever
```Leave off the .ko extension. Reboot and post back.

If there is no prism2 module loaded, we will troubleshoot from there.

---

### Post by xnszxdotnet on 2007-03-22
that did the trick.  :) 

thanx

---

