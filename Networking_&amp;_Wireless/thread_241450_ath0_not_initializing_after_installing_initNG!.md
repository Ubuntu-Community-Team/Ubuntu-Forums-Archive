---
title: "ath0 not initializing after installing initNG?!"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by resolv on 2006-08-22
Hi 

I've installed InitNG and I've lost my ath0. The module is not loading.Afeter dmsg i got this; 

[COLOR="Red"][ 32.823146] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[ 32.826605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[ 33.326393] wlan: 0.8.6.0 (EXPERIMENTAL) 
[ 33.327654] ath_rate_sample: Unknown symbol ath_hal_computetxtime 
[ 33.330459] ath_pci: Unknown symbol ath_rate_tx_complete 
[ 33.330868] ath_pci: Unknown symbol _ath_hal_attach 
[ 33.331539] ath_pci: Unknown symbol ath_rate_attach 
[ 33.332008] ath_pci: Unknown symbol ath_rate_newassoc 
[ 33.332091] ath_pci: Unknown symbol ath_hal_computetxtime 
[ 33.332430] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register 
[ 33.332811] ath_pci: Unknown symbol ath_hal_mhz2ieee 
[ 33.333056] ath_pci: Unknown symbol ath_hal_detach 
[ 33.334217] ath_pci: Unknown symbol ath_hal_probe 
[ 33.334740] ath_pci: Unknown symbol ath_rate_node_cleanup 
[ 33.334833] ath_pci: Unknown symbol ath_rate_detach 
[ 33.336264] ath_pci: Unknown symbol ath_rate_node_init 
[ 33.336551] ath_pci: Unknown symbol ath_rate_findrate 
[ 33.336678] ath_pci: Unknown symbol ath_hal_init_channels 
[ 33.337276] ath_pci: Unknown symbol ath_rate_newstate 
[ 33.337372] ath_pci: Unknown symbol ath_rate_setupxtxdesc 
[ 33.337535] ath_pci: Unknown symbol ath_hal_getwirelessmodes 
[ 33.393181] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004) 
[ 33.395441] 8139cp: pci dev 0000:02:07.0 (id 10ec:8139 rev 10) is not an 8139 C+ compatible chip 
[ 33.395448] 8139cp: Try the "8139too" driver instead. 
[ 33.410636] 8139too Fast Ethernet driver 0.9.27 
[ 33.412952] GSI 20 sharing vector 0xD9 and IRQ 20 
[ 33.412960] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 23 (level, low) -> IRQ[/COLOR]

Without InitNG my ath0 was mormaly waking up. I don't know realy how to solve this. Drivers are in place at /lib/modules/"core" and they up too date even work wiht normal core, without InintNG. 

I was looking to solve this and found nothing. Meaby someone can help me! please!

---

### Post by resolv on 2006-08-24
Well, time to say 'by by ubuntu, kubuntu, xubuntu ect...' It's slow, needs to much time for evertyhing to work and it's slow, and it's slow. Support and coumunity is perfect but it's not enought. Ubuntu is for Desktps, right? Is shoud be easy and fast! and it's not so easy and not so fast.  

I've tried Debian with Gnome and it's 2 times faster?! Now its time to try Gentoo/Sabayon  

ps. I got Fujitsu Siemens Amilo 1650G with 1 GB Ram and ubuntu takes about 3 times longer to boot than Windows XP !!! Even after installing InitNG its not so fast. And I would not mentioned Kubuntu witch is even worst! I've tried 3bbit and 64, 64 is a bit faster but not as fast as Windows XP32 bit?! I wonder why? 

Debian with Gnome is fast! Very Fast ! Almoust like Windows;) haha;) 

I'm still not convincet shoud I use Linux for Desktop. I prefer to see linux as a my server but still nothing beats BSD especialy OpenBDS witch Is the beast and only for me:) 

Sorry for off topic. By by

---

### Post by tturrisi on 2006-08-24
[https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

---

### Post by hajk on 2006-08-26
Try "sudo depmod -a", then reboot.

---

### Post by ygfperson on 2006-08-28
> **hajk said:**
> Try "sudo depmod -a", then reboot.

I had a similar problem with the atheros wireless (didn't involve initng or kde though) and that fixed it.

---

### Post by dolny on 2006-08-29
I'll try that, can you explain what does depmod -a exactly do? For learning purposes :) Thx.

---

### Post by hajk on 2006-08-29
> **dolny said:**
> I'll try that, can you explain what does depmod -a exactly do? For learning purposes :) Thx.

Well, if it's for learning purposes, then I'll direct you to the "man depmod" command...;)

---

