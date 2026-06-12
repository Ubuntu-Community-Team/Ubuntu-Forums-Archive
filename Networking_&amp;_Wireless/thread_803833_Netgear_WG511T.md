---
title: "Netgear WG511T"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by littlewild on 2008-05-22
Hi, just need to ask a pretty newbie question. 

I have just upgraded my dell laptop from Ubuntu 7.10 to 8.04. Everything seems to work fine except my Netgear WG511T card. 

I have checked to see that the madwifi drivers are installed correctly but I am unable to load the module ath_pci using modprobe. It says the module ath_pci is not found. Any one knows what I am missing here?

By the way the device shows up in lspci as:

```

04:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```

Any help will be much appreciated.

---

### Post by chili555 on 2008-05-22
I believe it's ath_pci and not ath-pci.

---

### Post by littlewild on 2008-05-23
> **chili555 said:**
> I believe it's ath_pci and not ath-pci.

Oh that was a typo in the post. I tried to load the module ath_pci, not ath-pci.

Any way I thought they are the same? modprobe treats - and _ as the same for convenience's sake.

---

### Post by littlewild on 2008-05-23
A clean installation of Ubuntu 8.04 fixed the problem. The card now works right from start.

Guess the upgrade process from 7.10 to 8.04 screwed up some of the paths/modules. I am not sure what was changed, if any one knows feel free to send a pm.

---

