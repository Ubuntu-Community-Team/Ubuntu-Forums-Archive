---
title: "mobile broadband worries"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by bodyharvester on 2009-07-08
ive got a dell mini which i got for free by signing up to vodafone mobile broadband

ive tested ubuntu 9.04 desktop from the cd and liked it, it showed from my wireless that bi was in range oif two connections both with a password

the MObile Broadband connection however listed Vodafone Mobile (contract) but with no signal bar and i could mot connect to it

if i install the netbook remix tonight then will i have the connection? or will i not?

i do need the VMC software for the vodafone mobile connect thing tp work so if i download that tonight put it on a usb and install it after installing the netbook remix will i get a connection to the vodafone ntework?

sorry for the rushed question but ive got to go to the gym now so i cant reply for an hour or two till i get back

---

### Post by cozmicharlie on 2009-07-08
Go here and follow the instructions below [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Support for mobile broadband is native in the linux kernel in 9.04.  After you install make sure and update your system.  You should then be able to plug your device in and connect even without installing vmc software. After you plug it in go to the network device aplet (in the upper panel on gnome - it looks like 2 computer monitors)and you should see the broadband listed.  Check it and it should connect.  To make it so it connects when you plug it in, right click on the network icon in the upper panel>network device aplet>mobile broadband and your device should be listed - mark the box to connect automatically.  You don't need the vmc software to connect but, do install the vmc software since it does give you more control and options.  I am not sure but my guess is that Dell has added it to the repository (check synaptic package manager).  I am sure you can find a how-to on the Dell web site or forums or do a search on these forums.

---

