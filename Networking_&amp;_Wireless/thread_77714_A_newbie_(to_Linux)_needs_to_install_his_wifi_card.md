---
title: "A newbie (to Linux) needs to install his wifi card in Breezy"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by Great Briton on 2005-10-17
I have a Belkin 802.11g Wifi card which uses the Ralink RT2500 chipset. I installed Breezy and the card was not installed. I can see the card in device manager. I have been told a couple of different ways to from here. I tried downloading the Linux drivers from the Ralink website from [here]("http://www.ralinktech.com/supp-1.htm") in Windows and transferred it to Breezy. In Breezy I unpacked it and went to make.

The make file requested the kernal source, and provided a default path. I just hit enter, and the source could not be found. What should I do? Will it involve compiling a kernal?

Don't forget to make your reply easy for a Linux mewbie to understand.

Cheers,
GB

---

### Post by Quirky on 2005-10-17
I followed the Wiki entry to set up my conceptronic card (also a rt2500 card) for hoary. I doubt much has changed. Full instructions here:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)

My advice is follow the driver install section then skip the RaConfig section, it just adds problems than it solves. Editting /etc/networks/interfaces is much more reliable and easier to debug  (the rt2500 driver documentation recommends this approach too). Get an insecure network up and running first, then add WEP, then try WPA if you are feeling brave.

---

