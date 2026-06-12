---
title: "How To: safely unmount, or power down a PCMCIA EVDO broadband wireless card?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by stackable1 on 2008-01-25
Hello all 

Now that this forum site helped me to get my Verizon PC5750 EVDO wireless card working in Gutsy - how do I power it down or unmount it safely?  So I can for example connect to an 802.11g or wired Ethernet connection w/o a restart?    I'm not a total nube but close...Lol   thanks for any response.](*,)

Stackable

---

### Post by hahahan on 2008-01-25
Stackable1,

Use the networkmanger to disable the pcmcia device or from terminal :
sudo ifconfig eth1 down. 
eth1 has to be replaced with your card's name.
I never had any damage whilst ejecting and reinjecting pcmcia devices without power them down.

---

