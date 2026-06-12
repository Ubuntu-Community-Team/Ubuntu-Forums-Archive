---
title: "trying to use a WG311v3 -looks fine, but wont connect!"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by asch246 on 2007-04-20
Hi,
I´ve installed Xubuntu 7.04 ´Fiesty Fawn´ on my computer, using the ´alternate cd´ (was previosly on windows 98- it&#347; a really old computer). The computer has a wired network card which is working fine, but the wireless card I only recently got (i never used it in win98) did not work at all. The card is a Netgear WG311v3 PCI NIC. 
I´ve followed the instructions here [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice))
But I used the latest version of ndiswrapper availiable (1.42) and the windows driver that is on the cd that came with the card (I used those instructions because it has the exact same chipset in that card, and I figured that would be ok). 
Any way, the ´Network settings´ thing shows the wireless card and I´ve put all the settings in (WEP 64-bit password, ssid, etc) and it seems to be working fine, that is until I actually try to use the connection. When I open Firefox to any webpage, I get the ´server not found¨ page. 

It´s actually a bit of a problem because I need to use the wireless connection asap -at the moment there´s a cable going accross our hllway, through the lounge room and into the study!

Please understand that previous to yesterday, I had NO experience with Linux.

Any suggestions?

If you need to see the terminal output for a command, just let me know!

Thanks

---

### Post by glaeven on 2007-04-20
ok, you seem to be in my situation. i am considering getting this card, and my system is about as old as yours.

the problem i see is that 1.42 isnt the latest version of ndiswrapper. i think its 1.9. check packages.ubuntu.com.

---

### Post by asch246 on 2007-04-20
Sorry.
To clarify, I downloaded the ndiswrapper file marked ´stable´ from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482") 
packages.ubuntu.com [refers to it as 1.9]("http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9") but if I follow the links through sourceforge, the [file is marked 1.42.]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=501514")

---

### Post by glaeven on 2007-04-20
ndiswrapper, and ndiswrapper-utils, and ndiswrapper-common are different. my mistake.

you do need all 3 though.

---

### Post by asch246 on 2007-04-21
sorry, but I dont understand what the difference is and which I did install. How do I install the other 2? is there a guide somewhere?

thanks for your help!

---

