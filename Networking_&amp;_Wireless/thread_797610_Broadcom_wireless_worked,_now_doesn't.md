---
title: "Broadcom wireless worked, now doesn't"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2008-05-17
I had my broadcom wireless working quick and easy the first time i installed Hardy Heron RC 1 on my laptop but then after some fuzzy starts, it just did not work. I then reinstalled Hardy and thought that everything would work off the bat like it did the first time, no dice.

sudo lspci -v shows me this about my card:
> 06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0

Not quite sure what to make of that but maybe you do. In the drivers manager, I have the "Broadcom b43 wireless driver" enabled and "In use". I am using a WEP key and I know this has caused problems in the past but when I first got it to work in Hardy, I used a WEP key and had no problems.

When I click the little network icon thing on the tast-bar I sometimes see the network I have running called "awesome". It tends to come and go. Even when I see it, if I run "iwlist wlan0 scan" I always get "no results".

Can someone please help me? I would love to get wireless working peachy keen and it did before, just not anymore...

---

### Post by sixstorm on 2008-05-17
> **shiznatix said:**
> I had my broadcom wireless working quick and easy the first time i installed Hardy Heron RC 1 on my laptop but then after some fuzzy starts, it just did not work. I then reinstalled Hardy and thought that everything would work off the bat like it did the first time, no dice.

sudo lspci -v shows me this about my card:


Not quite sure what to make of that but maybe you do. In the drivers manager, I have the "Broadcom b43 wireless driver" enabled and "In use". I am using a WEP key and I know this has caused problems in the past but when I first got it to work in Hardy, I used a WEP key and had no problems.

When I click the little network icon thing on the tast-bar I sometimes see the network I have running called "awesome". It tends to come and go. Even when I see it, if I run "iwlist wlan0 scan" I always get "no results".

Can someone please help me? I would love to get wireless working peachy keen and it did before, just not anymore...

I'll be honest man, Linux HATES Broadcom cards.  I have the exact same wireless card you have and have experience the same things.  It worked in the RC but not in the final version.  I believe an update broke my wireless card and/or drivers.  I've tried everything under the knowledgebase of these forums but have had no luck whatsoever.  This is the only thing that I hate about Linux right now because it's basically a necessity when it comes to installing Linux on your laptop, ya know?

I'll keep an eye out on this thread to see if somebody comes by with a miracle.

---

### Post by Ayuthia on 2008-05-17
> **shiznatix said:**
> I had my broadcom wireless working quick and easy the first time i installed Hardy Heron RC 1 on my laptop but then after some fuzzy starts, it just did not work. I then reinstalled Hardy and thought that everything would work off the bat like it did the first time, no dice.

sudo lspci -v shows me this about my card:


Not quite sure what to make of that but maybe you do. In the drivers manager, I have the "Broadcom b43 wireless driver" enabled and "In use". I am using a WEP key and I know this has caused problems in the past but when I first got it to work in Hardy, I used a WEP key and had no problems.

When I click the little network icon thing on the tast-bar I sometimes see the network I have running called "awesome". It tends to come and go. Even when I see it, if I run "iwlist wlan0 scan" I always get "no results".

Can someone please help me? I would love to get wireless working peachy keen and it did before, just not anymore...

Have you tried changing channels on your router?  I have this card and have had to change the channel twice during the past couple of months.

---

### Post by shiznatix on 2008-05-18
Halarious. I changed the channel and it all works. I even pick up other wireless networks now too.

Maybe it was from doing "sudo ifconfig wlan0 down" then back up but I don't care because I am sending this reply wirelessly.

So for anyone who has the same card or is maybe just having the same troubles try changing the channel and if that does not work try to up-down and wait a minute or 2. It did not pick up the connections right away but after a bit everything showed up and all is working just fine.

---

### Post by r76 on 2008-05-18
> **sixstorm said:**
> Linux HATES Broadcom cards.

;) now surely that's the wrong way round.

> **sixstorm said:**
> This is the only thing that I hate about Linux right now

Try not to get mad with linux - vent your anger in Broadcom's direction for not supplying linux drivers.  I had to buy a new laptop last autumn and made sure to get Intel wifi, after years of Broadcom-based frustration.

---

### Post by sixstorm on 2008-05-18
> **r76 said:**
> ;) now surely that's the wrong way round.



Try not to get mad with linux - vent your anger in Broadcom's direction for not supplying linux drivers.  I had to buy a new laptop last autumn and made sure to get Intel wifi, after years of Broadcom-based frustration.

I agree, I shouldn't get mad at Linux but rather BC.  

My problem with the same wireless card is that it's almost like it's shut completely off.  lspci can detect the card and everything, but when you go into Networking or left click on the networking icon, all you will see is Wired Networking.  WTF?

EDIT:  Finally found a guide around here that worked!  I'm a happy camper now.  :D

---

