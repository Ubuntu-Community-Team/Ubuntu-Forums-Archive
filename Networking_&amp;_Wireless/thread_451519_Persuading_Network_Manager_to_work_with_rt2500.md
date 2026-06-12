---
title: "Persuading Network Manager to work with rt2500"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Carandol on 2007-05-22
A small triumph! Well, it is for me :-) I've got my Edimax EW-7108PCg wifi card (a card with a rt2500 chipset) to work with Network Manager. It's possible this could help some other people who have been cursing on this list. 

First of all, I had to disable the linux rt2500 driver. I did this by editing /etc/modprobe.d/blacklist and adding the line 
> blacklist rt2500

Then I installed ndiswrapper and used it to install the Windows driver on the disk that came with the wifi card.

Then (and this is the bit that confused me for a while!) I had to edit /etc/modprobe.d/ndiswrapper, so that instead of reading 
> alias wlan0 ndiswrapper
it read
> alias ra0 ndiswrapper

I then rebooted, and there was Network Manager working fine! I even managed to connect to my University's VPN. 

Imagine my joy! :D

---

### Post by videodrome on 2007-05-25
If you could get it to work *without* ndiswrapper I'd be very happy.

---

### Post by Carandol on 2007-05-25
> **videodrome said:**
> If you could get it to work *without* ndiswrapper I'd be very happy.

Well, yes, but sadly I'm not a programmer, and from what I've read, the linux rt2500 driver lacks certain features that Network Manager needs. Hopefully, somebody out there is writing a new one even as we speak.

---

