---
title: "Ubuntu 14.04.1 any wireless USB dongle working properly in AP|master mode?"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by bruacucunalsucri on 2014-10-21
Probably this question has an answer somewhere on the Internet but in a long working day I was not able to put my eyes on it...

I'm a very happy ubuntu user since 7.04 up to 14.04.1 on my Sony Vaio VGN-FW21Z.
I need now to create an AP on this laptop putting a wireless card in AP mode or Master mode (whatever it could be called) to connect an android device.
Unfortunately my current wireless card "Intel Corporation WiFi 5100 AGN, REV=0x54" works flawlessy as client but does NOT natively support AP|Master Mode (AFAIK).
I need another wireless card to cope with my need and an wireless USB dongle seems to me the perfect choice.
hostapd site or iwlwifi driver site are reporting how to find if an already owned card support AP|Master mode but _NOT a list of supported cards_.

Which wireless USB dongle should I buy being sure it is properly working in ubuntu 14.04.1 ???

I tried initially to implement everything on my native laptop. It DOES NOT work, or at least I am not able to implement it properly!
I've browsed this forum as well as many others on the internet for almost a day discovering that proper AP|Master Mode support is only possible with right combination of Hardware + Firmware + Driver + Software.  These are my conclusions up to now:
- Software: hostapd is requested but as of today it has official issues with 14.04 kernel...
- Driver: hostapd requires these drivers to work: madwifi or mac80211-based; my card is mac80211 based but...(see firmware)
- Firmware: the firmware code for my card distributed into linux-firmware package DOES NOT support AP|Master mode...
- Hardware: the Intel wireless chip I have should support AP|Master Mode...

Could someone point me in the right direction with one of these two options:
1) How to configure Ubuntu 14.04.1 into using "Intel Corporation WiFi 5100 AGN, REV=0x54" in AP|Master mode ?
2) Which wireless USB dongle should I buy being sure it is _properly_ working in ubuntu 14.04.1 ?

Thanks in advance to who could help me!

Ciao,
Gianni

---

### Post by bruacucunalsucri on 2014-10-21
All those of you having an USB wireless dongle can try to open a terminal and type:
$ iw list | more
Going down two or three pages and reporting what found in the section "Supported interface modes".
My current card (Intel 5100 AGN) is reporting:
	Supported interface modes:
		 * IBSS
		 * managed
		 * monitor
	software interface modes (can always be added):
		 * monitor

I am interested to cards having AP mode supported.

Ciao,
Gianni

---

