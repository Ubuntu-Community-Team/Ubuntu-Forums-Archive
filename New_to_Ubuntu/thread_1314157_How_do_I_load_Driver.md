---
title: "How do I load Driver"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Alex Beaton on 2009-11-04
How do I instal the driver for a wireless LAN card onto a laptop running Ubuntu 9.04. The card is a Buffalo Air Station g54. I used it on the laptop in MS Windows XP before changing to Ubuntu.
 
Please give simple and comprehensive instructions because I have only started using Ubuntu today.
 
Thankyou

---

### Post by ukripper on 2009-11-04
Read this - [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Installing drivers ain't same in Ubuntu as in windows.

---

### Post by Alex Beaton on 2009-11-05
Hi ukripper
 
Thanks for the link. I don't understand it but I did find a reference to the PCMCIA CARD which I'm using:-[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo#PCMCIA) and the card is WLI-CB-G54L.
 
But what do I do now?
 
regards
alex

---

### Post by porchrat on 2009-11-05
Welcome to the forums! Always great to see a new user.

If Ubuntu supports the card it should work automatically when Ubuntu starts up. Ubuntu should install the correct drivers and sort it all out for you.

If Ubuntu doesn't support the particular piece of hardware out of the box and you find that you can't get it working you could try ndiswrapper.

Ndiswrapper essentially allows you to install and use the WindowsXP drivers in Ubuntu.

It even has a GUI (graphical user interface) so you don't have to interact with it through the console. Perfect for new users.

It can sometimes cause problems. Personally I have never expereienced any problems using ndiswrapper. It works really well on old Intel wireless modules.

Hope this helps.

By the way here is a [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") if you need more help or are unsure don't hesitate to ask someone, that is what this community is here for.

---

