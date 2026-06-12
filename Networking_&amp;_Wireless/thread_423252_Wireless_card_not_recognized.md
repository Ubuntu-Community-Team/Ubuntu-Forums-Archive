---
title: "Wireless card not recognized"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by shahgols on 2007-04-25
Hi everyone, 

I just installed Feisty and my Broadcom BCM4306 is not recognized.  lspci shows:

02:03.0 Non-VGA unclassified device: Broadcom Corporation Unknown device 0000 (rev 03)

Any help would be greatly appreciated.

---

### Post by Buffalo Soldier on 2007-04-25
This is what I got from [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

At the bottom of the page:

> Tried Ndiswrapper - no good. Tried bcm43XX-fwcutter which worked fine with BCM43xx driver. Ubuntu 6.10 on Compaq M2045AP laptop. Wireless NEVER worked on XP with this laptop
I have zero experience with this network card, sorry for not being able to help any more than this.

---

### Post by shahgols on 2007-04-25
Hi Buffalo Soldier, thanks for the link.  I tried that approach and I still have the same problem...lspci shows that my card is not recognized.  I tried using some other distribution live CDs and they all report the same thing.  I just reinstalled Vector Linux on another partition and that too says the same thing.  Yesterday, the old Vector Linux was showing BCM4306 when I ran lspci.  :(  I am totally bummed, I have a feeling this problem is going to be a bugger.

---

