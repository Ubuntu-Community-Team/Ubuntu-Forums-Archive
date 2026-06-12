---
title: "installing drivers for pci wireless card"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Hellcom on 2008-12-27
I have an edimax EW-7728IN that uses a rt2860 ralink chipset. I'm trying to install the drivers for it in 8.10. However, I'm having a bit of trouble. I've followed instructions that come with the downloaded driver. This is what I've done so far:

*Downloaded RT2860PCI  drivers from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

*Extracted from tar file

*installed build-essential

*entered the command 'make' in a terminal - it compiled it without errors

*copied RT2860STA.dat to /etc/Wireless/RT2860STA/ in sudo

*entered the command 'modprobe rt2860sta' in sudo

*rebooted

*now I have no idea why the wireless card won't work - HELP!

---

### Post by Hellcom on 2008-12-27
Ah, got it. This is what I did:

*Downloaded RT2860PCI drivers from [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

*Extracted from tar file

*installed build-essential

*cd 2008_0918_RT2860_Linux_STA_v1.8.0.0

*sudo make

*sudo make install

*sudo reboot

*yay, it works

---

### Post by pacco on 2009-01-03
Thanks for this tut,i was having major fits with this card:)

---

### Post by Zaytoven on 2009-01-06
holy crap. this worked PERFECTLY for me LOL

---

### Post by Zaytoven on 2009-01-06
holy S.... this worked perfectly for me LOL. Its been what i've been looking for all week. WOOOOH got my wireless going just in time before school starts :-D

---

