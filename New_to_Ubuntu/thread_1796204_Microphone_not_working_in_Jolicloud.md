---
title: "Microphone not working in Jolicloud"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by PommieB on 2011-07-03
Hello everyone,

I'm running Jolicloud 1.2 on a Toshiba Satellite Pro L630-14J with a HDA Intel sound card and a Intel Ibex Peak HDMI chip. Despite my best efforts, I cannot get it to recognise the internal microphone, and all I get over a Skype test call is static. 

This is the output of "sudo lspci -v -nn > lspci", if it helps:

> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



Any help would be greatly appreciated!

---

### Post by Glupoi652 on 2011-07-03
Go under Sound (if you're using Unity, just type in sound, and it should pop up) or if you are using Gnome 2.x interface, go under System>Preferences (or that menu under preferences, sorry, right now Im using fedora 15, and I can't see the menu as I am going through this by memory) >Sound.  go to the Input tab, and experiment with that, see if you can't get anything.  If that fails, then go to ubuntu software center, and go try to redownload alsa and pulseaudio drivers.  See if that helps :D

---

