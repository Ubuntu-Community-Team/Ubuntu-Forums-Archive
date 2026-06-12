---
title: "need proprietary drivers"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-09-26
hi, i've installed Ubuntu today.  problem is - i can't use the wireless (proprietary drivers), i just can't see them at all.  on the live USB it works fine no problems, it's just the installed version.  i changed the software dependencies to include the live USB and now i can see the driver i need, but can't install it (something about can't fetch the driver).  i can't connect to the internet (cause i can't get the wireless) and i don't have ethernet, so no internet what-so-ever...

i'm running a 64-bit ubuntu.
i've read the other posts about it and it didn't work for me...
thanks for your help

---

### Post by LowSky on 2010-09-27
Hi, can you open terminal from the accessories menu under applications and type the following command:
```
lspci
``` 
and then copy and paste the results here.. By the way that is a lowercase L as in LSPCI this way we know what driver you might need.

this link might help
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by daveboy23 on 2010-09-27
lspci

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)

01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)

03:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)

7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)

7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)

7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)

7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)

7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

this is what i got.  thanks for the help

---

### Post by bkratz on 2010-09-27
the Broadcom 4357 uses the STA driver. Instructions for getting it from the live CD are in this thread. Pay particular attention to post 19 and on, but read the whole thread.

[http://ubuntuforums.org/showthread.php?t=1578443&page=2](http://ubuntuforums.org/showthread.php?t=1578443&page=2)

---

### Post by daveboy23 on 2010-09-27
great, thank you so much for your help.
how do you inform the ubuntu people of this problem so it would work auto in 10.10?

---

### Post by andrewthomas on 2010-09-27
> **daveboy23 said:**
> 
how do you inform the ubuntu people of this problem so it would work auto in 10.10?
File a bug.

If your problem is solved, please mark the thread as [SOLVED] using the thread tools menu.

---

### Post by gordintoronto on 2010-09-27
It is, in fact, solved in 10.10.

---

