---
title: "Acer Aspire 4310 can't connect to internet period."
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by mkesadaran on 2008-04-08
ok so my dad just bought me this acer aspire 4310 in indonesia. i was psyched at first and then i realized a few things were wrong. for one, vista was supposed to be installed but mines was xp ( stupid indonesians gave me a bootlegged copy of xp too. dont take offense im indonesian). so i realized that there was no way i was going to get vista anytime soon (i dont like vista but i didnt want to go google  hunting for drivers). alt f10 didnt work and customer service wouldnt gimme a damn recovery disk since it was purchased outside the country (even though i have an international warranty..) so i got pissed off and went driver hunting and i miraculously got all my drivers working (before i couldnt even connect to the internet wirelessly. i still need my bluetooth driver.) so now im all happy that i dont have to bring wires up to my laptop and guess what, i found out my xp was bootlegged. i got all pissed again and i didnt feel like having an illegal xp so i knew about ubuntu and thought it was pretty sick and all so i burned the cd and tried it on my laptop.

i checked for cd errors there was none so i started it up and immediately loved the interface. i was ready to make a permanent switch to ubuntu and then guess what.. internet didnt work on ubuntu (7.10 btw) i was ready to cry. neither wired or wireless worked and i even tried to put in the settings manually. all it did when i plugged in the wire was flash acquiring network connection or something like that and it did that for like 9 hours and never stopped. wireless didnt even come up. so please come help me. i care more about my wi fi but i guess solving the wired connection first will be more helpful so thank you and please help. keep in mind that both wired and wireless worked on xp.

---

### Post by mkesadaran on 2008-04-09
anyone please i need help

---

### Post by sheffrem on 2008-04-09
Hi There,
Since you were able to install the wifi and networkcard in Xp , you dont mind giving details about you r Wifi and Network cards. Details like Manufacturer, card Name annything describing the cards, I guess you should have these info since you were able to search google for the drivers, But the most important on is the Network card, Wifi can easely be fixed with a package called ndiswrapper by using the windows driver if you still have them. So give details about your cards.

---

### Post by mkesadaran on 2008-04-09
according to device manager, i have

wired: broadcom netlink gigabit ethernet

wireless: broadcom 802.11g network adapter

yea idk if that'll help tho. i managed to get drivers cuz many people wer having trouble with this laptop so yea. ill be willing to provide any info u need. just tell me how if its too complicated.  tyvm

---

### Post by sheffrem on 2008-04-09
Well dont know much in the command lines to check the PCI devices but Click on System>Preferences>Hardwareinformation

There you should see in the list an unrecognized network devices both wifi and the other card may be the names will have broadcom in them. Then let us know.

Note: What do you get when you Click System>Administration>Network

Do you see any device.???

---

### Post by mkesadaran on 2008-04-09
uhm yea it doesnt say "device unrecognized" per say but it says unknown on descriptions or anything like that and on network i cant find any devices.

---

### Post by kutjara on 2008-04-09
I'm using an Aspire 4315 with Ubuntu 8.04 beta. It works very well with both wired and wireless networking. It's interesting that you have a Broadcom wireless card, since I thought most of the 4000 series machines use the Atheroa AR5007EG wireless card. I don't even know what wired card I've got, because it just worked with the default installation. It sounds like the Indonesian-market specification is slightly different.

For Broadcom cards, the best solution appears to be using ndiswrapper together with the Windows XP drivers you downloaded. Ndiswrapper is essentially a translation program that communicates between the Windows drivers and Ubuntu. If you search on the forums for Broadcom and ndiswrapper, you'll find several howto threads telling you how to set things up.

The other method of getting wireless to work is via madwifi. Madwifi create their own drivers for popular wireless cards, and some cards work better with this than with ndiswrapper. I use madwifi drivers with the Atheros card in my 4315. Again, you can search on the forums for madwifi for guides on setting it up with your card.

---

### Post by mkesadaran on 2008-04-09
yea but i cant even connect to the internet so how do i download

---

### Post by kutjara on 2008-04-09
> **mkesadaran said:**
> yea but i cant even connect to the internet so how do i download

That's a problem alright. You'll need to get access to an Internet-connected machine to get the packages you need. There really isn't any other way of doing it. Once you're on an Internet-connected machine, you can save the files to a flash drive or burn them onto a CD to use on your machine.

The Ubuntu install disk may have a copy of ndiswrapper on it that can be installed using the Synaptics Package Manager or apt-get, but this will be an older version. Much better to get the latest one directly from the developers' site. If you really can't connect to the Net, though, using the one on the install CD may be your only option.

---

