---
title: "HP DV9000 w/ internal Broadcom card + Belkin usb wireless g"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by phillo on 2008-09-29
Using a dv9000 laptop with an internal Broadcom card and a belkin usb wireless g card.  i have been unsuccessful connecting the broadcom @ home to either a verizon 327w (which i bricked while attempting to upgrade the firmware in hopes of solving the problem) or a verizon westell 7500 (the replacement to the 327w).  fortunately the belkin connects to the home network.

Though I had to go through some hoops to get it there i know the broadcom is installed/working because i connected, on a couple of occasions, to wireless hot spots.  now for some reason the internal broadcom card won't see any networks, public, private whatever; clicking the 'network name' dropdown box in network connections shows nothing in the case of the broadcom and now the belkin.  if i manually enter my home network info into the belkin it connects w/no problem.  

i'm assuming this is a software/configuration issue but i have no idea what it could be.  new to linux, loving it, just want to figure this out.  main problem:  wireless cards not registering available wireless networks.  they did register before, so something changed, dunno what.  os is hardy 8.04, updated.

here is my network info:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:34:89:83
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:ff:63:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:17:3f:85:b2:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.33 multicast=yes wireless=IEEE

---

### Post by nixscripter on 2008-09-29
Looking at the last part, it looks like the driver for the Belkin wireless is not installed (there is no **driver=** part for **wlan1** like there is on **wlan0**).

Did you install a Ralink driver?  See if Ubuntu has it:

```
sudo modprobe rt73 rt2570
```

If it can't find them, instructions (two versions, in fact) are here: [http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

---

### Post by phillo on 2008-10-02
Thanks for the quick reply.  I've been trying lots of things, nothing works.  

I'm wondering if what I'm experiencing now is a hardware/driver conflict?  The internal Broadcom card worked immediately after the hardy 8.04 installation,  it detected wireless networks, it connected to all networks, the wireless light was blue; the only thing it WOULDN'T do is connect to our home network (wireless router/modem 327w). <-that was the reason i bought and connected the Belkin.  the belkin seemed to work no problem, connected to the home network BUT only the home network, no where else. after connecting the Belkin the Broadcom stopped detecting/connecting to networks and the wireless light is now000 red.

I followed 2 sets of instructions for installing the Belkin, neither seem to work, the Belkin driver isn't found anyway.  However, the Belkin does connect wirelessly to the home network (now a verizon westell 7500).

Is there any way to wipe out all wireless drivers and try reinstallation?  Would that potentially solve the problem?  do i have to reinstall hardy?

---

### Post by nixscripter on 2008-10-03
You don't have to re-install to stop it from loading drivers if that's the problem. Edit the file **/etc/modprobe.d/blacklist** and add entries like:

```
blacklist ndiswrapper
```

To disable that module. Generally, the only linux drivers that "fight" are those which attempt to control the same card as an ndiswrapper driver. You can get a listing of all the modules on your system with: ```
lsmod
```

See if blacklisting a few things works; it's a lot simpler (and more reversable) than a re-install.

---

