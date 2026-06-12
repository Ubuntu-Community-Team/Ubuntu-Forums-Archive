---
title: "Need wireless help"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Rotarychainsaw on 2007-07-24
Hi, 
I just got an abit airpace PCIexpress card for my computer. The restricted driver manager caught it and it's in HAL so I think the OS knows it's there. 

here is my lshw -C network:
>  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:fa8f0000-fa8fffff irq:23


I read that this means that there is no driver associated with the card... Is there some kind of command to associate it? I also installed madwifi from SVN to see if that helped but it does the same thing. 

modinfo ath_pci: 
> filename:       /lib/modules/2.6.20-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r2598
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     E0AB8786BB39CB79C3942CF
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           tpc:Enable/disable per-packet transmit power control (TPC) capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)


---

### Post by kevdog on 2007-07-24
Im no expert on madwifi, but it does not support all atheros chipsets.  The only think I could find out of the widwifi website about support for abit cards was the following:

Abit ¶
AirPacer WLP-01 ¶
Chipset:	AR2425 (802.11b/g) AR5007EG
URL:	[http://www.abit.com/](http://www.abit.com/)...
Interface:	PCI-Express x1
Antenna Connector	SMA?
Device Information:	168c:001c
Notes:	has 2nd antenna connector (of type Hirose?), not supported by HAL as of 2007.05.09 Appears to be made by AzureWave?

Not sure if this is your card.  If you cant get madwifi to work, I would try ndiswrapper if you have winxp drivers.  Sorry I couldnt help you more!

---

### Post by Rotarychainsaw on 2007-07-24
Oh good call, that is my card. I thought all atheros were the same chip... Ok then off to ndiswrapper learning. thanks.

---

### Post by Rotarychainsaw on 2007-07-24
Well got it working using ndiswrapper. Had to use a version that was newer than the repo's but it seems to work. 2 problems that I will start looking to fix...
1. have to type sudo modprobe ndiswrapper every time I reboot
2. Can't use my wired network now>

any ideas while I search? thanks.

---

### Post by kevdog on 2007-07-24
Ok type the following commands if you have not done so to load the ndiswrapper module at boot:

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

As far as the wired connection, can you post:
lshw -C network 
/etc/network/interfaces
/etc/iftab


Thanks

---

### Post by Rotarychainsaw on 2007-07-24
Ah yes thanks. I think I got it under control. I added ndiswrapper to /etc/modules so now it starts. I think the eth0 shutting off maybe had something to do with network-manager or something but after randomly pushing buttons everything works as it's supposed to. 

Thanks again.

---

### Post by smoocat on 2007-07-25
> **Rotarychainsaw said:**
> Ah yes thanks. I think I got it under control. I added ndiswrapper to /etc/modules so now it starts. I think the eth0 shutting off maybe had something to do with network-manager or something but after randomly pushing buttons everything works as it's supposed to. 

Thanks again.

Hey there.. I've been trying in vain to get this card working under Feisty as well.. Tried Madwifi--no luck.  Ndiswrapper kept coughing up errors, too.  Could you tell me how you got it working (what steps/driver you used)?

Thanks a bunch--

---

### Post by coolkrish on 2007-08-11
Hi,

I am facing trouble getting this same card installed under AMD64. I cant seem to get unshield 0.5 compiled. I keep running into a fPIC issue. Could someone tell me how I can resolve this. 

Thanks

---

### Post by kevdog on 2007-08-11
Please start a new thread and I can help you.  Be sure to give me all the details about your wireless device and the results of lshw -C network when posting.

---

