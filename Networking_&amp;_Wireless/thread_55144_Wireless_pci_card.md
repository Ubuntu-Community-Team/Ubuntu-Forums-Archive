---
title: "Wireless pci card"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by Jerrac on 2005-08-07
What is a good cheap wireless pci card that is supported automatically by Ubuntu? Preferably 802.11g, but 802.11b will work as well. 

Thanks! :D

---

### Post by humina on 2005-09-03
I would also like to know.  Unfortunately since nobody responded, I think you might be in trouble :(

---

### Post by 0vermind on 2005-09-03
I would have no clue, I'm going to watch this post cause I myself would like to know as well. I have has troubles with a linksys card and was told it can be done but I gave up (could not get it to work)!!!

Good luck (don't think it's possible without hours of hard work  ](*,))

---

### Post by Picklegnome on 2005-09-03
This is the Hardware Compatibility Page that you should look at:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

Belkin Wireless Cards (802.11b) are cheap, but you have to get a version 2, not the latest version 3.

---

### Post by joepotter on 2005-09-03
[QUOTE=Jerrac]What is a good cheap wireless pci card that is supported automatically by Ubuntu? Preferably 802.11g, but 802.11b will work as well. 

Thanks! :D[/QUOTE]



Anything based on the rt2500 chip set is great. The drivers are GPL and in the Breezy kernel --- ready to go.

The list is at;

[http://ralink.rapla.net/](http://ralink.rapla.net/)


I have several in our lab and just ordered 5 more of the MSI card from computers4sure.com


Good luck.

---

### Post by 0vermind on 2005-09-03
Sweet my Adapter is on the list it is WUSB54G (Wireless-G USB Network Adapter). Yeah, I wonder... would anyone know how to configure the WUSB54G?? If you do please reply to my post: **No networking support??** :(

---

### Post by escuchamezz on 2005-09-03
are you guys trying to configure wireless cards in linux? oh no good luck, cause you'll need it  :-|

---

### Post by joepotter on 2005-09-04
[QUOTE=escuchamezz]are you guys trying to configure wireless cards in linux? oh no good luck, cause you'll need it  :-|[/QUOTE]


Luck? 

I put all kinds of wireless cards in boxes at work. No card is all that hard, even my $ 15 USD card by Trendnet took only 30 minuets to set up with ndiswrapper.

I even set up a card that requires the firmware to be flashed with each reboot.

It just takes reading the how-to page.

---

### Post by joepotter on 2005-09-04
[QUOTE=0vermind]Sweet my Adapter is on the list it is WUSB54G (Wireless-G USB Network Adapter). Yeah, I wonder... would anyone know how to configure the WUSB54G?? If you do please reply to my post: **No networking support??** :([/QUOTE]


[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)


Be sure you really have a rt2500 chip as the version numbers on some of these cards are real important. Try the lspci command.

---

