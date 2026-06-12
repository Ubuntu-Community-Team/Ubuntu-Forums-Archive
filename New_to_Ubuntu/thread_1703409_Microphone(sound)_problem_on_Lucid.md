---
title: "Microphone(sound) problem on Lucid"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-03-09
Hi,

I have a sound problem for about one year already. My speaker works fine but not the mic (either internal or line-in). I'm currently on ubuntu 10.04 LTS.

Below is the output of my lspci:

Thanks in advance..

-alfa-

```


shah@shah-laptop:~$ lspc
lspci     lspcmcia  
shah@shah-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)



```

---

### Post by mastablasta on 2011-03-09
What kind of sound output/input do you have set in sound preferences?
 
Try setting analog duplex.
 
have you checked in alsamixer and made sure all barrs are high up? to get to alsa mixer open the terminal and type alsamixer
 
have you tried upgrading alsa? [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by alfa_80 on 2011-03-09
> **mastablasta said:**
> What kind of sound output/input do you have set in sound preferences?
 
Try setting analog duplex.
 
have you checked in alsamixer and made sure all barrs are high up? to get to alsa mixer open the terminal and type alsamixer
 
have you tried upgrading alsa? [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

There is no exactly analog duplex, but there is analog stereo duplex. I have done it and still got problem.

I've already the latest version of alsa I guess as the following output shows:

```

shah@shah-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jan 20 2011 for kernel 2.6.32-28-generic (SMP).

```The alsamixer bars are all up as in the screenshot below:


Any idea?

---

