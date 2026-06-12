---
title: "anyone using Asus WL107G PCMCIA card for wireless?"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2006-09-10
Hi, I've been posting for the last week in an effort to get wireless working on my partner's laptop, to no avail. I haven't been getting replies to my posts though I'm sure someone smart here knows the answer or could help (even if only to eliminate something).

Anyway, here's a more specific direct appeal.

I have a **Ralink 2500** chipped **Asus WL107G PCMCIA** card and wondered if any other Ubuntu users were currently using this card. I've spent countless hours pouring over forum threads trying to help myself but haven't come across anything yet that I've been able to successfully use. 

I'd be very interested to hear of anyone else who is using this card (and any special set-up they have had to implement to get it working).

thanks

---

### Post by alanmzifa on 2006-09-12
just a bump

---

### Post by Hal Canary on 2007-05-08
I have the same network card, which I bought because it is supposedly supported by Linux.

I have an old Compaq Armada E500 laptop running XUbuntu 7.10.  It does not recognize the card.

When I insert the card, nothing happens.  When I run `dmesg`, I get no mesages at all related to the new card.

---

### Post by alanmzifa on 2007-05-09
> **Hal Canary said:**
> I have the same network card, which I bought because it is supposedly supported by Linux.

I have an old Compaq Armada E500 laptop running XUbuntu 7.10.  It does not recognize the card.

When I insert the card, nothing happens.  When I run `dmesg`, I get no mesages at all related to the new card.



*I got it working on Dapper Drake 6.06back in September, forgot about this thread.*


 If you check under my name for my other threads you should see some details of how I got it working. 
I think it was fully supported in 6.06 and 6.10 so it shouldn't be hard but 7.04 broke the wireless for most devices including anything with a Ralink 2500 chip-set.

---

### Post by Hal Canary on 2007-05-13
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus) says:
> Card works fine in Breezy with no special setup. Is not detected at install, but **if you go to network settings and put ra0 where it says lo it will be detected**. Probably have to manually put in the ssid. This card is recommended because of GPL drivers which are quickly advancing and will soon be in the official kernel.

I don't understand these instructions.  I am new to Ubuntu and would like to see some more detail, maybe some screenshots.

---

