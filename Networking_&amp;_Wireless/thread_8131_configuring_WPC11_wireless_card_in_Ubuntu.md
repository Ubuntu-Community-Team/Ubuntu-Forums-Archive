---
title: "configuring WPC11 wireless card in Ubuntu"
date: 2004-12-14
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2004-12-14
Can anyone help me get this up and running?
I have the above card in the PCMCIA slot of a HP Omnibook 6000 laptop. 
When I boot up and insert the card, the two lights come on but no beeps.

/sbin/cardctl ident gives the correct info for the card

When I type lsmod the orinoco/hermes drivers are not listed, but when I modprobe orinoco, orinoco_cs and hermes they get added to the list. 

I just can't figure out what to do next. In the System Tools/Network Tools window there are entries for eth0 (network card) and lo only. 

I've found info on this card with another distro and other cards with Ubuntu, but not this combination.

[edit] I got it installed and now it appears in the Network tools program. However, when I click on the configure button, it refuses my root password. I tried it X amount of times, and the same root password works for everything else. WTH?[/edit]

---

### Post by pickarooney on 2004-12-15
Well, I had to change the root password to be able to run the network config tool (!) and now when I select eth1 from teh list and click on configure it tells me the interface doesn't exist. When I rebooted, the root password had changed back to the previous value. Totally weird.

I managed to attribute an IP address and subnet mask to the card, so it's fully functioning. I still can't connect to the router though, ping fails. The router is set up to accept a signal from the network card and from its IP address. 

Anyone know what else I need to configure?

---

### Post by mc_cgp on 2005-02-20
[QUOTE=pickarooney]Well, I had to change the root password to be able to run the network config tool (!) and now when I select eth1 from teh list and click on configure it tells me the interface doesn't exist. When I rebooted, the root password had changed back to the previous value. Totally weird.

I managed to attribute an IP address and subnet mask to the card, so it's fully functioning. I still can't connect to the router though, ping fails. The router is set up to accept a signal from the network card and from its IP address. 

Anyone know what else I need to configure?[/QUOTE]


Hi did you get this card to work?

Mine works OK in SuSE but would like to go to Gnome 2.10
TIA
MC

---

