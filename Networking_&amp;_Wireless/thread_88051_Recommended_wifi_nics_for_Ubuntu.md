---
title: "Recommended wifi nics for Ubuntu"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by ripgut on 2005-11-09
I know there was a posting with a chart of recommended wifi nics for this distro, can someone point me to it? thank you :p

---

### Post by Kyral on 2005-11-09
Like WiFi Cards?

I know Atheros works :D

---

### Post by ripgut on 2005-11-09
Yes, wifi cards, pcmcia and pci  wifi nics

---

### Post by Kyral on 2005-11-09
Like I said, Atheros works via MadWifi (which is integrated into the Ubuntu Kernel). I dunno about other ones

---

### Post by ripgut on 2005-11-09
my friend has a Belkin usb wifi adaptor 
model # fsd7050 will this work in ubuntu, if not how can one go about getting it work? o.O

---

### Post by Kyral on 2005-11-09
NDiswrapper?

---

### Post by Doc.Caliban on 2005-11-09
[QUOTE=Kyral]Like I said, Atheros works via MadWifi (which is integrated into the Ubuntu Kernel). I dunno about other ones[/QUOTE]

I have a Gigabyte WIAG-02 (Atheros 5005) Mini-PCI NIC in my laptop that Ubuntu didn't detect.  Currently I'm using a spare 2200 but would like to get back to the Atheros card.  What's the quickets route to getting this done?

-Doc

---

### Post by Kyral on 2005-11-09
Hmmm...are you using the Ubuntu Kernel?

---

### Post by Agent86 on 2005-11-09
PCI cards based on the Ralink RT2500 chipset work. Breezy detects them out-of-the-box. If you need to also get WPA working, all that is needed is a text file edit, a couple of clicks on the System > Administration > Networking tool, and a reboot. No fiddling around with ndiswrapper or wpa_supplicant required.

I don't have direct experience with the PCMCIA, USB, or Mini-PCI RT2500 cards, so I can't vouch for them. But I have seen favorable messages from those who have used them. 

As a bonus, Ralink has released these drivers under the GPL, so by going with these cards, you're supporting Open Source and companies (like Ralink) that cooperate with the Open Source Movement.

Here is a list of cards based on the RT2500:

[http://ralink.rapla.net/](http://ralink.rapla.net/)

Please note that for some brands on the list (like D-Link, Belkin, and Linksys), the use of the RT2500 chipset is hardware version-dependent. In other words, if you don't get the the right hardware version of the D-Link card, you might not get the RT2500 chipset.

---

