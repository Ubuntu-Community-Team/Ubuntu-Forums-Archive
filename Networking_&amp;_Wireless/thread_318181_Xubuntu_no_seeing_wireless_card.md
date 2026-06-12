---
title: "Xubuntu no seeing wireless card"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by BPerkins on 2006-12-13
I am very new to linux and I have put xubuntu on an old HP with 64 megs of ram.  I bought a d-link wda-1320 and placed it in the place of the stock modem.  I booted and it thought it still had a modem not a wifi card.  So I reinstalled the system and it saw the card. I followed the setup and I even turned off the wep on my router to make it simpler.  It said it was configured sucessfuly but when the install was finished and I looked at the network area it still thought it had a modem.  What is my problem, do I need a driver?

Thanks

---

### Post by FrodoB on 2006-12-13
Did you install using the Alternate CD? If so then:

1) Have the install CD ready for use.

2) Open a terminal command prompt and type the following:

sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

If you did not install using the Alternate CD them provide the output of:

lspci -v

---

