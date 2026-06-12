---
title: "Broadcom Wireless Issues"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by bradhawk08 on 2007-11-14
Hello all,

I know there are many different posts out there about this but I don't know which one fits my situation, so I was hoping you guys could help.  

I just installed a fresh copy of Ubuntu Server 7.10 (Gusty Gibbon) on my desktop computer in hopes of setting up a webserver.  I am able to connect to the internet when I plug in the ethernet cable, but I'm trying to connect wirelessly.  

The wireless card is a Linksys PCI Adapter Wireless-G WMP54G

I followed The Perfect Server - Ubuntu Gusty Gibbon 7.10

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

to install ubuntu and I tried the Gusty guide on wikipedia to try to fix the problem

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

when typing lspci | grep Broadcom i get the following

02:09.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I manually set up all the parameters for the wireless card in the 

/etc/network/interfaces file according to "The Perfect Server" tutorial mention above.  

Does anyone know the proper fix?  Thanks

---

### Post by spd106 on 2007-11-15
First I have to question the use of a wireless card in a server. You do know it's not considered to be a reliable method of communication? It might be acceptable for a client PC, but it's certainly not recommended for a server. I'm sure you have your reasons, though it's certainly worth a second thought.

That said, first you need to verify that the cards firmware has been installed and works. There should be some bcm*.fw files in the /lib/firmware or /lib/firmware/`uname -r` folder. 

Also you should not see any bcm43xx error messages in dmesg.

When configuring the interfaces file you need to know the name of the wireless interface (probably eth1). Run iwconfig to find it, then add it the interfaces file with similar address and subnet mask details. 

If you are using encryption then you will have to add that too. I recommend that you use the Wireless Security sticky as a guide.

---

