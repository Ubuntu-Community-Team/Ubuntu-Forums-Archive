---
title: "Netgear WG511 v2 installed but hardware not present"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by derekge on 2008-04-16
This seems to be an branch of a very similar problem with wireless.  I'm using the Netgear WG511 v2 pcmcia card on my toshiba laptop running Xubuntu gutsy.  Ndiswrapper lists the driver as being installed but it is not present.  Here is what I have done so far:

- uninstalled network manager
- installed ndiswrapper
- blacklisted the following:
     #added these to troubleshoot netgear wg511
     blacklist prism
     blacklist prism54
     blacklist prism54pci
     blacklist prism54common
     blacklist p54pci
     blacklist p54usb
     blacklist p54common
- installed this driver via ndiswrapper: [ftp://downloads.netgear.com/files/wg511v300.zip](ftp://downloads.netgear.com/files/wg511v300.zip) 
- modprobed ndiswrapper
- ndiswrapper -m
- appended ndiswrapper to /etc/modules
- installed WICD (works with a wired connection now)
- switched between ndiswrapper driver and wext driver in WICD
- rebooted

Outputs:
[HTML][Q]derekge@xubuntu-laptop:~$ ndiswrapper -l
netwg511 : driver installed

derekge@xubuntu-laptop:~$ lspci | grep Marvell
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

derekge@xubuntu-laptop:~$ sudo lshw
 *-network UNCLAIMED
          description: Ethernet controller
          product: 88w8335 [Libertas] 802.11b/g Wireless
          vendor: Marvell Technology Group Ltd.
          physical id: 1
          bus info: pci@0000:07:00.0
          version: 03
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0[/Q][/HTML]


It's obvious that the hardware is not being recognized fully, the lights don't come on and there is no wlan) yet.  **How do I get the wg511 card to become wlan0 - that's the step I'm missing.**  Any replies are greatly appreciated - thanks.

---

