---
title: "Wonky Broadcom Wirless"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by Tdraket on 2008-02-04
I have a dell inspiron 1501.  I have installed and used both ndiswrapper and the bcm restricted drivers successfully in the past.  

     Anyway one day my wireless decided to just stop working right.  It would see wireless networks and would "connect"(i use the quotes because it couldn't have any form of communication for more than 50 seconds.) and would stay "connected" but I couldn't use the net or even communicate with the router.  

      I proceeded to figure out if something got wiggled loose inside and just took the card out and put it back in.  At that point it decided to stop even finding networks.  So I've reinstalled ubuntu about 8 times using both ndiswrapper and the restricted drivers.  I figured there might be some issue with the card so I ordered a new one from dell and today I received it today.  To my great dismay it seems to have the same issue.  No wireless.  

      The computer recognizes my card.  I lspci and I see "05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)"  It wouldn't have asked me to install the restricted bcmxx drivers if it didn't see the card.  I've tried scanning with iwlist and it just says it can't find any SSID's.  It claims to have scanning abilites because it says "eth1 no scanning results".  

      I'm sure I plugged everything in right.  I mean all there is to do is plug it in the slot and match up the black and white wire with their respective socket.  I just wanna know if there is a way to fix this or is it some hardware malfunction on the motherboard level.

---

### Post by jan quark on 2008-02-04
hey one question

I have the same dell laptop with the same broadcom card

how did you managed to install the drivers with the ndiswrapper

I had only really only success with the fwcutter method

and I have occasional lags during my internet usage

I have tried out every ndiswrapper guide in the whole universe and nothing except the fwcutter worked for me

tell me your secret

---

### Post by Tdraket on 2008-02-04
I just followed the generic guides to installing the driver.  I blacklisted the bcmxx driver and then normally installed the way you do with any driver in ndiswrapper.  I guess this goes to show how inconsistent dell's hardware is.  My friend has the same laptop as me, but his wireless works just fine.

---

