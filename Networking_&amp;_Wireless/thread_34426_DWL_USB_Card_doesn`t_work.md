---
title: "DWL USB Card doesn`t work"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by cyanezs on 2005-05-14
Hi,
I just installed ubuntu and a i`m positive surprised about it.
The only problem I have i with my wi fi card: i cannot recognize it.
The card is a DWL -120 (D1) usb one (prism). I`ve first tried with wlan-ng tool, following the standard and forum instruction with no success. It only recognised when i connect the device (adding a new wlan)
After that, i put ndiswrapper and dlink official driver. It recognises when i plug the card to my usb port, but when i try to perfom any iwconfig command the system says: " SET failed on device wlan0 ; Invalid argument. "
The computer is a toshiba satellite 5205-s505 laptop.

Any ideas?
(if there is no solution, which cards (usb o pc cards) are totally compliant with ubuntu? the wi fi method is my primary network connection mode!!)

Regards,
Carlos Yáñez S.

---

### Post by ssam on 2005-05-14
i have found getting a dwl-122 a real pain, although some people have sucess with various methods.

i have found that the pcmcia cisco aironet 340 works very well. you dont even need to configure it, it just works, then if you do want to fiddle you can use the network preferences or iwconfig. i have not tried using WEP or WPA.

only trouble is that the 340 seems to cause interference with my sound card (on via epia). it buzzes when there is any network activity. i have tried earthing an shielding, but had no luck. on other machines there is not problem though.

i am currently bidding on a Netgear WG511 on ebay, which i think should work. i'll let people know.

there is a list of pcmcia cards at [http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS)

sam

---

