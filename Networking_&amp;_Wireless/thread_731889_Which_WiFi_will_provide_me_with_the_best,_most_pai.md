---
title: "Which WiFi will provide me with the best, most painless operation?"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by KeeperOS on 2008-03-22
I'm thinking of getting myself a Dell Vostro 1400 M which I was informed comes without Windows Vista but with FreeDOS for me to install pretty much whatever I want.
What I want to install in it is Ubuntu **8.04** or, to be more precise, **Kubuntu 8.04**, for start w/KDE3.5.9 and later on when available KDE4.1.

Now seeing as there could be a million ways to screw sth up and since they are enabling wireless internet within the campus which I plan on using, what are the pitfalls that I should be wary about and what the safe bets?
In the specs they say that they offer these WiFi solutions:
> [B][I]Dell Wireless 1390 802.11b/g Mini Card Wireless
Dell Wireless 1490 802.11a/b/g Mini Card Wireless
Dell Wireless 1505 Wireless-N Mini Card
Intel Pro/Wireless 3945 802.11 a/b/g Mini Card Wireless
Intel 4965AGN Wireless-N Mini Card[/I][/B]Which of these will work the best in Ubuntu and offer me the best functionality (as in, get the greatest range as well as the most consistent, even across reboots, stable connection)?

Thanks!!!

---

### Post by Hightide on 2008-03-22
Hi KeeperOS

As a starter I would have a look at the ubuntu wireless supported cards [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

regards

:)

---

### Post by EricDB on 2008-03-22
My Dell XPS m1210 uses the Intel Pro/Wireless 3945 802.11 a/b/g, and **after I switched from NetowrkManager to Wicd**, it's been reliable and very low-maintenance.

---

### Post by KeeperOS on 2008-03-22
> **Hightide said:**
> Hi KeeperOS

As a starter I would have a look at the ubuntu wireless supported cards [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

regards

:)
I did but they were both outdated and incomplete/inconclusive so, here I am.

I gather that the 3945 802.11 a/b/g will probably work fine but, wont I be missing on the new N protocol?
If the wifi on campus will be supporting the N protocol won't that mean that with 802.11n I'd be able to get a better reception and a faster connection (I think they have a T3 connection or sth on campus...)?

Please help/educate me

---

### Post by ugm6hr on 2008-03-22
All the Dell branded cards are Broadcom's.

They are all best avoided.

I would recommend the 3945 too, cos it works well.  Not sure about the other Intel card, although Intel are big supporters of Linux, so I suspect that if it is not already supported, a driver will become available at some point.

Best to check out the Intel website for details.

LINK:
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

EDIT: From that link: 
> The iwlwifi project can be found in kernels 2.6.24 and up

So I think you should be OK.  I can't remember what kernel Gutsy uses, but I think it is newer than that (at work on Windows at present :(

---

### Post by KeeperOS on 2008-03-22
Hardy Beta uses 2.6.24-12.13 kernel (based on 2.6.24.3) and I'll buy it probably after Hardy will be released so, I think I'm cool.

So, does anybody think that I'd be better of with choosing the tried and true 3945 or the new and improved(?) 4965?

---

### Post by kevdog on 2008-03-22
See if any of those cards are Atheros Based Chipsets.  They are very reliable and work with the madwifi drivers.  If you want to see a poll about the most problematic chipsets, check this out:
[http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)

Broadcom, Atheros, Intel, and Ra are the predominant chipsets.  Of the 4 predominant, atheros has the least problems.

---

