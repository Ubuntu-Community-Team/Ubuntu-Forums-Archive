---
title: "Karmic Remix on EeePC 900 battery issues"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by azebuski on 2009-11-03
I upgraded to Karmic a few days ago on my Asus 900 netbook.  Pretty much everything is perfect except for a few battery semi-issues.
  Whenever I reboot I get a notification error saying "Your battery is critically low (1.9%)  This may indicate an old or damaged battery."  Yet my battery if fully charged and lasts at least 2 hours.
  After a few hours of use, when I know my battery really is low and I plug in, the battery indicator says my battery is at 90% capacity and will take 20 hours to recharge.
  Anyone else with an Asus netbook having this happen?

---

### Post by Frantique on 2009-11-03
Confirmed. Same issue here.

---

### Post by jack57 on 2009-11-09
Same on Ubuntu 9.10 - Mine Asus is eeePC 900 earlier version (9.04) hasn't this feature, it showed pattery state right

---

### Post by dragonboss on 2009-11-09
This issue might be solved if the battery is fully depleted (from full charge) and recharged fully while in ubuntu this usually sets a range of sorts for the battery indicator.

---

### Post by Frantique on 2009-12-03
Sorry, I cannot confirm that a loading cycle (or even more) will fix this. The problem cames from a badly interpreted value. Anyway, I am looking forward for a solution. If you know something, inform us!

---

### Post by lblau on 2009-12-23
I also am experiencing this message, but my battery is behaving fine.

Anyone have a solution?

---

### Post by Matt G Dalian on 2010-04-01
Thought I'd post a reply:

I'm having the exact same issue with Ubuntu 9.10 on a ASUS eee PC Celeron 900 MHz.

I also had the same issue when I had Ubuntu Netbook Remix (9.10) installed on this same netbook.

It looks like this bug is not unique to ASUS, and other users have experienced it:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/518365](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/518365)

When I click on the Power Statistics for this battery (right click on battery icon and click on Power History) I see:
Energy when full: 0.8 Wh
Energy (design): 43.7 Wh

My battery is standard- Asus EEE PC 700/701/801/900/901/2G/4G/8G Black Hi-Capacity Battery (7.4V, 7200mAh, 6 Cells).

And I get about ~3h of battery life so it's working fine.

It's mostly a nuisance, but I did purchase a new battery right after I installed Ubuntu for the first time (on this netbook).
Also, I wanted to re-sell this laptop with Ubuntu still on it, and seeing that battery warning come on when you first turn on the computer doesn't help the sale!

Is there a way to edit some .conf file to fix this?

---

### Post by TheRitz on 2010-06-14
I am having similar issues on my Eee 900 (Celeron M) and 4400 battery. The battery itself is working just fine! 

At startup it states batterylevel is 1.9%. The indicator however shows the correct load. After a while it pops into the red (30%) but I can still use the machine for over an hour after that. So it looks like the battery indicator does not have a clue as to how full or empty the battery is.

If I can deliver logs or whatever I will be happy to do so. It is an annoying issue, but not life threatening ^_^

---

### Post by ibuclaw on 2010-06-14
In **gconf-editor**, browse to:
```
/apps/gnome-power-manager/general
```
And de-select the option **use_time_for_policy**

See if that makes any difference.

Regards

---

### Post by nordemoniac on 2011-05-23
The problem is that the EeePC is reporting it's battery capacity in percent. So it sends "100" to the OS, and the OS thinks it is "100mah", meaning the battery is toast.

AFAIK this is why you get this message. I have the same problem on all other OS than Xandros, which is crap really.

---

