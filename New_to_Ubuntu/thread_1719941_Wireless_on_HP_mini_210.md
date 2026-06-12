---
title: "Wireless on HP mini 210"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by silliej on 2011-04-02
I installed ubuntu Netbook version 10.10 a long time ago on my hp mini210.

after I installed it, my wireless won't work. And after folowed several guides, still my wireless isn't working

when I use the command ¨sudo iwlist scan" in terminal, I see several networks but my card won't connect with them.

```

specs of my wireless card

[code]lshw -C network
``` *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:96:56:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:56000000-56003fff
[/code]I've tried any form of installing the broadcom STA driver, by the terminal and the regular installation.


somebody who knows the solution for this problem?

thanks,

Silliej

---

### Post by TeoBigusGeekus on 2011-04-02
Have you tried with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")?

---

### Post by silliej on 2011-04-02
> **TeoBigusGeekus said:**
> Have you tried with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")?

thanks for possible solution,

trying it now, 

let you know the results

---

### Post by BicyclerBoy on 2011-04-02
The exact h/w of this model range is very confused.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

My HP mini 110 1010 wifi network worked with live USB boot but failed after install-reboot.
Needed to change the driver from B45 to STA (or vice versa) & install the firmware package.

---

### Post by silliej on 2011-04-02
> **BicyclerBoy said:**
> The exact h/w of this model range is very confused.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

My HP mini 110 1010 wifi network worked with live USB boot but failed after install-reboot.
Needed to change the driver from B45 to STA (or vice versa) & install the firmware package.

I already tried changing driver to STA... didn't work. when i changed back to the old one, it won't work either... I am still trying with nDisWrapper

---

### Post by davidmohammed on 2011-04-02
if you are seeing various wireless Access Points then your driver probably is OK.

To check, try to connect to a wireless network.

Then in a terminal session type

dmesg

the last dozen of so lines should reflect what the wireless is try to do.  Can you copy and paste the output here in a reply?

---

