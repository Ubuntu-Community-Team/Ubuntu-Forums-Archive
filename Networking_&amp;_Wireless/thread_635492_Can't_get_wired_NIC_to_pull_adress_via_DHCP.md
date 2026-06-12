---
title: "Can't get wired NIC to pull adress via DHCP"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by billmachon on 2007-12-08
I hope someone can help me.  I'm running a totally fresh install of Gutsy.

I have an Intel Pro 100/VE 82801BA/DAM/CA/CAM

This card is listed as supported.

Ubuntu sees my card, says it's running, but I can't get a DHCP address.

OpenSUSE 10.3 and DamnSmallLinux work pefect on this machine.  The same NIC works and picks up an address via DHCP.  So I know the card works with Linux, just not happening with Gutsy.

It's an onboard NIC if that matters.  It's not PCI... it's embedded on the mobo.
This is an old P3 machine.

I'm a Linux noob.  But I'm not afraid of the terminal.  I've searched the forums an can't find an answer to this.  I've tried things that I've read about.... ifconfig, modprobe, etc.  I did a lot of tinkering, no luck.  So I just reinstalled totally fresh.  Any advice?

Thanks

---

### Post by billmachon on 2007-12-10
I figured it out.  There was an IRQ conflict between acpi and eth0.  They were on the same IRQ #. 
It couldn't be resolved via hardware in the BIOS.
I re-installed Gutsy fresh, but at the installer main screen, hit F6, and entered pci=noacpi
This time, the installer connected to the network(wouldnt before), and then after the install, when I booted into Ubuntu for the first time, sure enough, the IRQ conflict was gone. ACPI had it's own, and eth0 had it's own.

Success!

---

