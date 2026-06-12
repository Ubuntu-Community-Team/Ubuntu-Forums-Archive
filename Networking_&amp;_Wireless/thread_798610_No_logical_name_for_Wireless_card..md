---
title: "No logical name for Wireless card."
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by n2oboost1 on 2008-05-18
```
home@home-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:d0:dd:f0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.104 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
```

Any ideas on how to get the logical name for my wireless card?

---

### Post by theDaveTheRave on 2008-05-18
Hi n2oboost1

At least your system can "see" your wirless card, that means that you will be able to get it working.

a few questions,

is this a recent "failure" that occured after an update or is it your first foray into Ubuntu?

If it is a recent failure it has probably been broken by conflicts in downloaded drivers, you will now have 2 options.

Firstly.....

if you had to "play" with your system following someones howto, then I suggest that you go back to that howto and de-install all the additions that you made, and start again. I realise this is a pain, but it will guarantee that it should work again, and if not I'm sure that others have experienced the same issues... somewhere!

Second option.....

if the card "just worked" and you didn't have to fart around, other than the exception of turning on "restricted" drivers or similar. You will need to access the downloaded software via synaptic, and search for anything that may be related to the wireless (search for stuff like wireless or the name of your card vendor Broadcom). You will probably find that there are more than one driver installed on your system. Try to figure out which is the correct one, from reading various other threads, that relates to your system kernel. Tag this one for re-installation and remove the other.

You will then be asked to re-boot. With luck that should solve your problem, but if not get back to the forums and search for the broadcomdrivers.

Dave

---

