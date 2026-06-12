---
title: "boot problem with rtl8081 D-Link-DWL510"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by assan on 2008-01-08
Hello,
today i was installing 7.10 on desktop, everything was ok and them big problem.
Problem is with wireless network adapter D-Link DWL-510. After first boot after install I was manually configuring and it was ok. It found my Access Point, and problem occured when I was typing WEP pass. First attempt was my fault hex pass and asci input in window. After trying to correct system crashed. I rebooted several times with same result. In recovery mode there is strange massage. Kernel panic - not syncing : Fatal exepction was interrupt
Just above is source of problem I think. EIP: prism2_wep_encrypt+0x19d/0x250 [ieee80211_rtl] SS:ESP 0068:d8e9bcf0
It looks like system is trying to connect using wep and something it totally wrong. Maybe using prism2 wep encryption on rtl8081 card is source. I have no idea and asking for help.
Maybe I will try to remove for while wireless card and reboot?
BTW: this card was working ok on ubuntu 6.06
:confused:

---

### Post by assan on 2008-01-08
After removing wireless card system booted without problems, so trouble source is wireless configuration, help needed.
I will try to put back and then see what happens.
Well, without wireless card system boots without problems. After insertion hangs again. So problem is definitely in wifi configuration and particuralrly in WEP configuration.
Help needed.
I have reinstalled system and problem return exactly in the same moment. Probably there is bug in WEP configuration in Ubuntu 7.10, but some wise people must check it out.
Maybe I will switch to open network only with MAC filtration.

---

### Post by mrierab on 2008-04-05
Hi,

I'm have exactly the same  problem, the system hang when try to start a WEP connection with wifi card D-Link DWL-510 with L¡nux Mint (Ubuntu 7.10 based)

I test with a CD-Live other wifi Centronics card and run without problems, for this reason I think it's a problem with a card driver.

I'm lookink for the solution. Can help me?, Thanks ! :)

---

