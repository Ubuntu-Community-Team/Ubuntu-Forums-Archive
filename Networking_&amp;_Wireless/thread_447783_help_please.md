---
title: "help please?"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by pmpdru on 2007-05-18
hello, yesterday my windows crashed for the last time, so i upgraded to linux. but now i cant get my wireless to work. ... my card is 802.11 b/g Wireless PCI card ... i was told to install ndiswrapper then open windows wireless driver to configure the card, but it cant recognize my card. can anyone give me a quick simple way to help me with my problem?

---

### Post by MeeMaw on 2007-05-18
There are many cards with many chipsets..... could you give us a little more information by opening a terminal and typing

sudo lspci

and posting the results here?  This command gives us information about your hardware and the chipset in your wireless card...... that way, we will know what directions to give you.    Thanks!

---

### Post by pmpdru on 2007-05-18
[http://paste.ubuntu-nl.org/21382/](http://paste.ubuntu-nl.org/21382/)

---

### Post by MeeMaw on 2007-05-18
OK, the one you are needing help with will be the Atheros card - AR5006x is the chipset.....
While I am getting a little better at configuring wireless, I need to let someone else with more experience guide you..... someone with MAD-WIFI experience (Multiband Atheros Drivers for Wifi)....

Also, we need to know which version of Ubuntu you are using.

---

### Post by pmpdru on 2007-05-18
7.04 feisty or w/e

---

### Post by blaamann on 2007-07-28
Read:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

