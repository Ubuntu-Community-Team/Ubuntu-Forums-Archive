---
title: "Ndiswrapper Walkthrough"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by M$LOL on 2007-02-11
Can someone give me a simple walkthrough for ndiswrapper? I'm trying to use the one on the Ubuntu 6.10 x64 CD, but I keep getting errors. The adapter is a Philips CPWUA054.

Thanks.

---

### Post by Metaljaz on 2007-02-11
Try this Wiki. Should be pretty simple. If you need more help post back.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by M$LOL on 2007-02-14
OK, now how do I know what version [this card]("http://www.komplett.ie/k/ki.asp?sku=322308") is? It seems that it needs to be v. 5100 for it to work out of the box.

---

### Post by chili555 on 2007-02-14
Does this help?

[http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)

---

### Post by Metaljaz on 2007-02-14
well if you need to install drivers outside of the native drivers what really matters is the chipset of the card.
in the terminal window type:

lspci

check network controller: and you should see the name of the card and the chipset. something like this:
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
(In this example the card is a Broadcom Corporation card with the BCM4306 chipset)
Then find the drivers for the chipset.
Post the results and we can go from there.

---

