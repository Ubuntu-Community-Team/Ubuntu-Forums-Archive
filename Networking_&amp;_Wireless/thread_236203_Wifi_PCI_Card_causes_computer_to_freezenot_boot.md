---
title: "Wifi PCI Card causes computer to freeze/not boot"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by blindspy on 2006-08-14
I've got a Belkin F5D7000 PCI wifi card that shows as ra0 in iwconfig and freezes if I try to use it. There are 2 versions of the card and 2 different chipsets. A Broadcom chipset (which I've used before and set the computer up with the correct packages to use this) and also Ralink RT2500 chipset which is included in the kernel with dapper. Since lspci shows *"0000:01:06.0 Network controller: RaLink: Unknown device 0301"* and the card shows up as ra0 in iwconfig, i'm guessing its the Ralink chipset. The card shows up in iwconfig just fine.

I've used this page as reference with no luck:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Here is my interfaces:
```
iface ra0 inet dhcp
wireless-essid *MY ESSID*
wireless-key *MY WEP KEY*
auto ra0
```

---

### Post by JDAAINOKI on 2006-08-14
I'm also using the rt2500 card. I tracked my problem down to the video and wifi pci sharing the same IRQ.  For some reason that IRQ was being disabled on boot (as far as wifi was concerned), but it remained open for video. There shouldn't be a problem with IRQ sharing w/ PCI, but thats getting a bit above my level.  Do a cat /proc/interrupts and see if your card is sharing and IRQ. Then do a dmesg | grep XXX (enter your cards IRQ in place of XXX). If it is disabled you can try switching your adapters driver to vesa in the xorg.conf.  That worked for me for now until a fix comes around.

Jay

---

### Post by blindspy on 2006-08-14
I'm not sure which one it is?

```
           CPU0
  0:    3313809    IO-APIC-edge  timer
  1:       4016    IO-APIC-edge  i8042
  7:          0    IO-APIC-edge  parport0
  8:          3    IO-APIC-edge  rtc
  9:          1   IO-APIC-level  acpi
 12:     512024    IO-APIC-edge  i8042
 14:     165678    IO-APIC-edge  ide0
 15:     281009    IO-APIC-edge  ide1
169:      15391   IO-APIC-level  uhci_hcd:usb3
177:     822341   IO-APIC-level  uhci_hcd:usb1, i915@pci:0000:00:02.0
185:          0   IO-APIC-level  uhci_hcd:usb2
193:          6   IO-APIC-level  ehci_hcd:usb4
201:    1418477   IO-APIC-level  Intel 82801DB-ICH4, eth0
NMI:          0
LOC:    3313689
ERR:          0
MIS:          0
```

---

### Post by JDAAINOKI on 2006-08-15
Blind, 
I've seen this card via google w/ Atheros, rt2500, and Broadcom chipsets. If you do have the rt2500 version check the ```
uname -v
``` and look for SMP in the kernel version. I know from my time using Gentoo the older rt2500 open source drivers don't work well with SMP.  The rt2500 that comes with dapper is dated 2005. You can either recompile the kernel w/out SMP or just follow the instructions here:  [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-85062aa61d00599364b7ccf7b5539aa11c9dd3b7]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-85062aa61d00599364b7ccf7b5539aa11c9dd3b7")
 
on how to get an updated rt2500 (use the nightly CVS release). Go ahead and read through the instructions and grab the RutilT too. I would follow the instructions closely from section 3 down, but don't worry about anything pertaining to RaConfig...I would suggest just going with the RutilT instead.  Let me know if any of this helps you at all. Do you know what version of the card you actually have? Try an lshw -businfo. Also, even if you don't have SMP I would update the driver anyway.

Good Luck,
Jason

---

### Post by mozetti on 2006-08-15
> **JDAAINOKI said:**
> I know from my time using Gentoo the older rt2500 open source drivers don't work well with SMP.  The rt2500 that comes with dapper is dated 2005.

Or, at least in my case, the rt2500 open source drivers didn't work at all with a SMP kernel in Breezy. So, I just went without an SMP kernel. I used a GRUB kernel option (i think it was ht=on, or something similar) to turn on hyper-threading in Breezy.

---

### Post by blindspy on 2006-08-15
Thanks for the posts! Yea I'm not using an SMP kernel. I used the lshw -businfo command but it only returned the same information I already know (that it is an RaLink ra0 Wireless interface. I will try the RutilT and newer version of the driver and report back.

---

### Post by JDAAINOKI on 2006-08-15
I had a problem with my wifi mini-pci sharing an IRQ with my video adapter.  For some reason that IRQ would be disabled during boot for my wireless card, but the video was fine.  All looked ok but I couldn't get the card to receive anything or find any APs....I guess because the card couldn't send an interrupt.   I was able to get the card up and running with the recovery mode image (cli only) or sometimes the "irqpoll" appended to the booted image would work (it would hang most of the time).  So, I changed the video driver to vesa in the xorg.conf file and now my wifi has it's very own IRQ under cat /proc/interrupts and all works ok.  I also had updated the drivers, but that alone didn't work. I'm looking for a fix to switch back to the VIA drivers for my video, but nothing yet. I don't even see your wifi in the proc/interrupts you posted.  You could try a "dmesg | grep Dis" to see if any IRQs are being disabled. Also, try to boot up with the recovery mode image and bring up your interface there. Ping your AP and google to see if your up. 

Good Luck,
Jay

---

### Post by blindspy on 2006-08-15
Yea that is weird that my card doesnt show in the IRQ list. I will boot in single user mode like you suggested and see if it still botches up my computer and also change the video mode just in case.

---

