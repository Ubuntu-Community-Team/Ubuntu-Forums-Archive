---
title: "Wireless on Ubuntu Server Edition"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by eddr on 2007-07-25
Hi,

I'm very new to setting up a linux machine, so please bear with me!

I've just installed Ubuntu Server Edition 7.04 onto a machine with a 3COM wireless card that IS supported by Ubuntu (according to the list of supported network cards).

Having failed to get the card working in the server edition, I booted into the Ubuntu DESKTOP edition and the network card worked first time. I managed to browse the web etc and had no problems.

I have copied the contents of /etc/network/interfaces in the desktop edition to my server edition and restarted the Networking service, but the interfaces wlan0 and ath0 fail to appear in the server edition.  They don't appear in the output of 'ifconfig' and I get the message 'No wireless extensions' when trying 'iwconfig'.

Since I know the card is supported, and proven that it works with the Desktop edition, can anyone offer any advice about how to kick-start it in the Server edition? Being relatively new to Ubuntu and Linux in general I don't quite know where next to look.

Any advice greatly appreciated!

Thanks,
Edd

---

### Post by fred93 on 2008-02-01
I have similar problem with Ubuntu Server 7.04 except I have an EnGenius Wireless PCI Adapter with an Atheros chipset.

I have installed madwifi and tried using wlanconfig but it can't detect my wireless card. I find this strange because when I installed Ubuntu Server, during the setup it detected the wireless card and asked if I wanted to use it during the setup. I didn't want to use it during the setup because I wanted to use the wired ethernet card but now that linux is installed it won't detect it.

This may not answer eddr's problem but may have same fix/result.

---

### Post by Unrequited on 2008-04-11
I'm having similar issues with a netgear wg511t. I can only assume that wireless is not supported without addition packages in the server edition.

---

### Post by Iowan on 2008-04-11
@eddr
I can't tell you how to do it - but see what driver the desktop is using, then see if the server has it, too.

---

### Post by fred93 on 2008-04-12
Try changing the kernal to 'generic' instead of 'server'. It in theory should not affect the working of linux though, but the 'generic' kernal is what Ubuntu Desktop edition uses.

This solved the problem I was having.

---

