---
title: "How do I find the MAC address for my wireless card?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by Ginigrace on 2007-06-22
I have Unbutu 7.04 running on a HP laptop. How do I find the MAC address for my wireless card which happens to be the nefarious BCM4381 (AirForce One 54g) 802.11g. I have been unable to find on-line instructions that work.

I have found the card under System, Preferences, Hardware Information, but there is no MAC number under any of its tabs. When I click on the little arrow to the left of it,  the item WLAN Interface appears directly under the BCM4318 card and when I click on the advanced tab for WLAN Interface I find the term "net.80211.mac_address" "long" and a number. This number does not look anything like the on-line examples for MAC addresses I've seen? Regardless is this the number I'm looking for?

Thanks!

---

### Post by kevdog on 2007-06-22
Please post output of:
lshw -C network

---

### Post by Ginigrace on 2007-06-22
This is embarrassing -- after I posted my how to find the MAC address question, I kept looking and found instructions to type ifconfig into the terminal. I did and the MAC address was there. Sorry!

---

### Post by Havok_CR on 2007-06-22
From the Spanish Wikipedia:

> Linux

Visualizar la dirección MAC:

En sistemas tipo Unix (Linux, FreeBSD, AIX, etc.) se ejecutará el comando **ifconfig** para conocer la información relacionada con las interfaces de red, donde aparecerá listada la dirección MAC correspondiente a cada una.

Resume:
In Linux type in a terminal:
**ifconfig**

And you will visualize the MAC address.

Bye!

EDIT: I posted too late :'(

---

