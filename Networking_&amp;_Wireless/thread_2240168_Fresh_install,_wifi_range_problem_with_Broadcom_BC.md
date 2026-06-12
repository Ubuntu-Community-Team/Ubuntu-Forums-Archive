---
title: "Fresh install, wifi range problem with Broadcom BCM43142 [14e4:4365] (rev 01)"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by propserv on 2014-08-18
Hello,

I'm pretty sure i'm the thousandish one with a similar problem but i didn't find exactly mine on the forum so let me explain :

I installed Ubuntu 14.04.1 yesterday on a brand new laptop (HP Pavilion 17). For the record i did alongside the pre-installed windows 8 but i guess it doesn't matter.

Everything went as well as possible with UEFI and dual boot fun, and so i had my Ubuntu 14.04.1 (fresh install + updated) working perfectly.

Then i noticed that the wifi signal were somehow low. I've got 2 wifi spot in my home and whenever i was outside the 1.5 meters range of one of them, i got disconnected.

When i'm connected it works just great but range is really limited. Even at something like 20cm of one wifi spot i didn't get the full bars in the notification zone.

I checked the system settings and Ubuntu do use the proprietary broadcom driver. 

I'll be glad for any help you can provide !

Here is the result of the wireless info script (done when connected, laptop at 20cm of one spot) :

[ATTACH]255585[/ATTACH]

---

### Post by praseodym on 2014-08-18
Change the encryption mode in your router interface to pure WPA2-AES (CCMP). Try also
```

sudo iwconfig wlan0 power off
```

---

### Post by propserv on 2014-08-18
I did both and it seems that there is improvment. I'll try moving around  and powering off/on to see during the day to see if it stays that way.

Would you be kind enough to explain why those commands would have improved anything ?

---

### Post by praseodym on 2014-08-18
WPA2 is more stable. Disabling the Power-management increses the current available for the card.

---

### Post by propserv on 2014-08-19
Ok did some test, and it seems problem is still here. :(

Range improved a bit, but Wifi still goes down to less than 50% (judging by the notification icon) at around 1.5 meters. So i do get connected sometimes but even then it just disconnect randomly without the laptop moving a inch.
It also sometime takes a lot of time to connect.

I guess i went from plain outside range to barely in range.

(Just to be clear, every other devices i have can fully connect at this range, even another ubuntu laptop with different model of wireless card)

---

