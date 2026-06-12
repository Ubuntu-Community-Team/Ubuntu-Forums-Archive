---
title: "[SOLVED] Complete Linux Noob Needs Help With Wireless Setup"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by 449 on 2007-10-28
I just installed Ubuntu 7.10 Gusty onto my computer and need help setting up wireless. I have a Dynex Wireless Enhanced G Desktop Card. I have no clue where to go from here to get the drivers installed. Help would be greatly appreciated.

---

### Post by 449 on 2007-10-28
If my adapter is not listed in the sticky, do I need to buy one that is?

---

### Post by foolios on 2007-11-07
> **449 said:**
> I just installed Ubuntu 7.10 Gusty onto my computer and need help setting up wireless. I have a Dynex Wireless Enhanced G Desktop Card. I have no clue where to go from here to get the drivers installed. Help would be greatly appreciated.


I have the same questions, to your original post and your reply.
Have you found the answers to these questions?

Thanks in advance for your reply.

---

### Post by rustybronco on 2007-11-11
What is needed is very little to use this card, i'm running it from the live-cd at this moment.
you need to be able to connect to the internet. ( I use a 25 ft cable connected to my router ) 
First enable the software sources, system>administration>software sources, then go to system>administration>restricted drivers manager and enable firmware for the broadcom 43xx family, choose download drivers from the internet and you are almost done, you still have to setup your encryption in the router and for your card in 7.10 (I use wep because that's what the router is set at ) 
hope i'm not to late to help

---

### Post by rustybronco on 2007-11-11
lspci output for those needing it on this Dynex enhanced "g" desktop card (dx-wgpdtc), hope it helps you also
```
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

***EDIT*** running this card on my normal desktop setup, it took all of 2 minutes to get it up and running. nice card for $8.99 @ best buy. ( I think i'll go and get the last two they have for that money)

now to list the cards I know to work with 7.04-7.10 in the HCL.

---

### Post by foolios on 2007-11-25
> **rustybronco said:**
> lspci output for those needing it on this Dynex enhanced "g" desktop card (dx-wgpdtc), hope it helps you also
```
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

***EDIT*** running this card on my normal desktop setup, it took all of 2 minutes to get it up and running. nice card for $8.99 @ best buy. ( I think i'll go and get the last two they have for that money)

now to list the cards I know to work with 7.04-7.10 in the HCL.

How do I use that line of output to make mine work?

---

### Post by rustybronco on 2007-12-05
> **foolios said:**
> How do I use that line of output to make mine work? That line of code is just tells the chipset in that card (bcm4318) it does not enable anything.

---

### Post by ks1g on 2008-01-18
I can confirm rustybronco's instructions work with a Dynex DX-BNBC Wireless G (54 Mbit) card.  Box reads DX-BNBC ver. 1000.  Uses the broadcom 43xx driver from the restricted drivers package.  WPA-PSK encryption and authentication worked from the entries using the System-Administration-Network gui as well.  I did have to restart the network connection one time to get a DHCP assignment to take.  

Host system is an ancient Sony Vaio laptop running 7.10, 2.6.22-14 kernel.

---

### Post by Lantesh on 2008-05-18
> **ks1g said:**
> I can confirm rustybronco's instructions work with a Dynex DX-BNBC Wireless G (54 Mbit) card.  Box reads DX-BNBC ver. 1000.

Thank you ks1g.  After seeing your post, and how inexpensive this card is I went out and bought it for my brothers Toshiba laptop that I am working on.  It works great!...Toshiba Satellite A135-S7404 running Windows XP and Linux Mint Elyssa.  It's working flawlessly under either OS.  The built in Atheros unit would not work in either, as this was originally a Vista laptop.  Now thanks to the Dynex card Vista is history.

---

