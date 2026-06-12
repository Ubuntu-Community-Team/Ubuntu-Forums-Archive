---
title: "Dell Latitude 610 laptop, Broadcom BCM4318"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by OldTymeToys on 2014-04-25
OK guys, I got Xubuntu installed and running... much faster than Ubuntu on this old thing!


Im running into a problem and being a newb, I'm having a tough time sorting it out. I'm having trouble getting my wireless card to work. I've read a bunch of threads on here regarding the Broadcom controllers, and that's what I've got. I'm just not sure the proper steps to take so I don't mess it up. Ndiswrapper, drivers, etc.- it's a bit over my head ATM. Hopefully, someone can walk me through this.

It is a Broadcom BCM4318 802.11g. Thanks!

---

### Post by varunendra on 2014-04-27
If you are sure you have a broadcom card, please read the sticky thread here : [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
Post back if the instructions there don't solve the problem completely. There is a known issue with BCM4318 cards which may require an additional step sometimes to detect available networks.

If unsure, please post the output of -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Iowan on 2014-04-27
Moved to Networking & Wireless.

---

### Post by OldTymeToys on 2014-04-29
> **varunendra said:**
> If you are sure you have a broadcom card, please read the sticky thread here : [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
Post back if the instructions there don't solve the problem completely. There is a known issue with BCM4318 cards which may require an additional step sometimes to detect available networks.

If unsure, please post the output of -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

Thanks for pointing me in the right direction! Worked perfectly!

---

### Post by varunendra on 2014-04-30
Please mark the thread as **[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")** then, using "Thread Tools" link above the top post. Thanks! :)

---

