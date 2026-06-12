---
title: "Intel Integrated Graphics Controller (rev 12) VGA only boots low-graphics mode"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by K-ROK33 on 2010-08-23
I recently put together my own computer in an attempt to become more familiar with the process, specifically for the purpose of running Ubuntu 64bit lucid w/ a virtual Win 7.  I can only get Ubuntu 64bit lucid to run in low-graphics mode though, which really puts a damper on things.  I'm using a Biostar TH55B mobo with the IGP on the Intel i3-530 w/ 8GB RAM and I can load win 7 ultimate and run with no problems, so it's not a hardware issue.  I've read many posts about the new intel chipset drivers not working with lucid, but none of the fixes seem to help my problem.  I'm fairly new to the whole linux process, so any info would be helpful.  Can I provide anything else?  Thx

Also, then it first boots, I get this:
(EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): No valid modes.
(EE) Screens(s) found, but none have a usable configuration

---

### Post by gordintoronto on 2010-08-23
Sometimes it's because Ubuntu does not recognize your monitor. What monitor?

---

### Post by K-ROK33 on 2010-08-23
I'm pretty sure it's not the monitor either.  I have 2 vga monitors, a 19" samsung syncmaster 912n and a standard 17" dell monitor.  Prior to the new mobo and processor, both monitors were recognized by ubuntu at their standard resolution. Now i'm only getting 800x600 low graphics.

---

### Post by Baldrick_NZ on 2010-08-24
> **K-ROK33 said:**
> I'm pretty sure it's not the monitor either.  I have 2 vga monitors, a 19" samsung syncmaster 912n and a standard 17" dell monitor.  Prior to the new mobo and processor, both monitors were recognized by ubuntu at their standard resolution. Now i'm only getting 800x600 low graphics.

Graphics chipset isn't SiS, is it?

go terminal, then type lspci which should give a read out of your chipset. Post the output here if you like so someone can better help the diagnosis.

Cheers.

---

### Post by K-ROK33 on 2010-08-24
Here's my output from lspci. I guess I could have posted it before. Sorry!
 
```

[SIZE=2]\desktop:~$ lspci[/SIZE]
 
[SIZE=2]00:00.0 Host bridge: Intel Corporation Device 0069 (rev 12)[/SIZE]
 
[SIZE=2]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)[/SIZE]
 
[SIZE=2]00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)[/SIZE]
 
[SIZE=2]00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)[/SIZE]
 
[SIZE=2]00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)[/SIZE]
 
[SIZE=2]00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)[/SIZE]
 
[SIZE=2]00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)[/SIZE]
 
[SIZE=2]00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)[/SIZE]
 
[SIZE=2]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/SIZE]
 
[SIZE=2]03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller[/SIZE]
 

```

---

### Post by Baldrick_NZ on 2010-08-26
> **K-ROK33 said:**
> Here's my output from lspci. I guess I could have posted it before. Sorry!
 
```

[SIZE=2]\desktop:~$ lspci[/SIZE]
 
[SIZE=2]00:00.0 Host bridge: Intel Corporation Device 0069 (rev 12)[/SIZE]
 
[SIZE=2]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)[/SIZE]
 
[SIZE=2]00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)[/SIZE]
 
[SIZE=2]00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)[/SIZE]
 
[SIZE=2]00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)[/SIZE]
 
[SIZE=2]00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)[/SIZE]
 
[SIZE=2]00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)[/SIZE]
 
[SIZE=2]00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)[/SIZE]
 
[SIZE=2]00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)[/SIZE]
 
[SIZE=2]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/SIZE]
 
[SIZE=2]03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller[/SIZE]
 

```

Nope, not SiS. Most graphics cards are supported, but generally not SiS. Maybe do a thorough search of this forum using "Intel Corporation Core Processor Integrated Graphics Controller (rev 12)" as keywords? May help produce some threads worth considering.

---

