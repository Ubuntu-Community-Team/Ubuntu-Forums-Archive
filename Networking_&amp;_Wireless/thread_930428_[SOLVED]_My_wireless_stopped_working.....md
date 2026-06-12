---
title: "[SOLVED] My wireless stopped working...."
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by roland0702 on 2008-09-26
I'm using Ubuntu 8.04. My wireless was working beautifully for the past month since I purchased my new computer; now it doesn't even recognize wifi signals. :(

My wireless device is:

Intel Corporation PRO/Wireless 3945ABG Network connection (rev 02)
I'm using the Dell Inspiron Labtop 1525

Anyone out there who can help me?

Kevin

---

### Post by willca on 2008-09-26
run the following 

sudo iwlist wlan0 scan

Does it see networks around?

Are you using some encryption in your wifi network?

---

### Post by roland0702 on 2008-09-26
The response I get is:

wlan0      Interface doesn't support scanning.



> **willca said:**
> run the following 

sudo iwlist wlan0 scan

Does it see networks around?

Are you using some encryption in your wifi network?

---

### Post by roland0702 on 2008-09-26
I'm using the WEP 64/128 bit Hex encryption.

---

### Post by Crafty Kisses on 2008-09-26
I'd also like to see the results of this command:
```
lshw -C network
```

---

### Post by willca on 2008-09-26
Normally when you get this...

wlan0 Interface doesn't support scanning 

by running sudo iwlist wlan0 scan
it means the wifi nic is not loaded, driverwise

You might need to redo the installation if you used Hardware Drivers feature of Hardy or ndiswrapper.

---

### Post by roland0702 on 2008-09-26
Here it is:


WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d1:ad:45
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945




> **Codename said:**
> I'd also like to see the results of this command:
```
lshw -C network
```

---

### Post by roland0702 on 2008-09-26
Ok. I'll give that a try. Thanks willca.

Kevin

> **willca said:**
> Normally when you get this...

wlan0 Interface doesn't support scanning 

by running sudo iwlist wlan0 scan
it means the wifi nic is not loaded, driverwise

You might need to redo the installation if you used Hardware Drivers feature of Hardy or ndiswrapper.

---

### Post by roland0702 on 2008-09-26
Do you know how to install the driver? I certainly don't. I downloaded the iwlwifi-1.0.0-1.tgz from Intel for the Kernel Linux 2.2.24-19-generic.

I also have my original installation disc; the 8.04 Hard disc. I see a cd-rom upgrade option on the disc, but when I double click and select run in terminal, no good.

I have no idea why this wireless stopped working, could it be from Ubuntu updates possible?

Thanks for the help and any future help.




> **roland0702 said:**
> Ok. I'll give that a try. Thanks willca.

Kevin

---

### Post by roland0702 on 2008-09-27
Hey everyone. I solved the problem. I'm a big idiot, because on the side of my computer is a switch that turns my wireless scan on and off. 

Thanks to everyone that helped me.

---

