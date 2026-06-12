---
title: "Linksys WPC54G v1.2 Causing Hard Crash"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by Slodeine on 2007-01-01
I recently dual-booted Ubuntu with Windows 2000 on my main desktop computer and was pleasantly surprised by the level of compatibility and out-of-the-box utility that Ubuntu provided.  I was amazed that my wireless network connection worked without configuration and that I could connect to other computers on my home network instantly.

However, I've really wanted Ubuntu on a Toshiba A45-S120 laptop I own, so I shrunk my Windows XP partition and dual-booted again.  Now I run into problems.  I use a Linksys WPC54G v1.2 PC Card to wirelessly connect to my router.  I've searched the forum for other difficulties with this card, but my problem seems to be unique.  Here are the symptoms:

I can boot into Ubuntu without problems.  The card's power indicator lights, but not link.  However, if I attempt to modify the wireless connection preferences, the computer goes into a hard lock upon clicking "OK."  Neither the keyboard nor the mouse respond and the only option is to forcibly shut down (by holding the power button). 

The same problem occurs if I boot into Ubuntu sans card and then subsequently plug the card in.  Instantly, the computer hard-locks (I don't even need to attempt to change preferences).

:-k

Any suggestions?

---

### Post by Slodeine on 2007-01-01
To clarify (and shamelessly bump), I'm running Edgy Eft and have installed and configured ndiswrapper for the card.

I could really use some help here.  Might it be advisable to move to Dapper Drake?

---

### Post by Slodeine on 2007-01-01
```
dhclient eth1
``` also causes lockup.  It seems that anything attempting to access the card's configuration will cause the problem.

Does anybody have any idea what's happening here?

---

### Post by alex_mayorga on 2007-04-19
> **Slodeine said:**
> I recently dual-booted Ubuntu with Windows 2000 on my main desktop computer and was pleasantly surprised by the level of compatibility and out-of-the-box utility that Ubuntu provided.  I was amazed that my wireless network connection worked without configuration and that I could connect to other computers on my home network instantly.

However, I've really wanted Ubuntu on a Toshiba A45-S120 laptop I own, so I shrunk my Windows XP partition and dual-booted again.  Now I run into problems.  I use a Linksys WPC54G v1.2 PC Card to wirelessly connect to my router.  I've searched the forum for other difficulties with this card, but my problem seems to be unique.  Here are the symptoms:

I can boot into Ubuntu without problems.  The card's power indicator lights, but not link.  However, if I attempt to modify the wireless connection preferences, the computer goes into a hard lock upon clicking "OK."  Neither the keyboard nor the mouse respond and the only option is to forcibly shut down (by holding the power button). 

The same problem occurs if I boot into Ubuntu sans card and then subsequently plug the card in.  Instantly, the computer hard-locks (I don't even need to attempt to change preferences).

:-k

Any suggestions?
Slodeine,

I'm seeing that same crash with a WPC54G version 2 on my Latitude CPxJ in Feisty. I've filed [https://bugs.launchpad.net/ubuntu/+bug/107864](https://bugs.launchpad.net/ubuntu/+bug/107864) for it, in case you're interested.

---

### Post by Nuberdrive on 2008-05-23
i too seem to have the same problem on my hp laptop. i am curently running windows again on it becuase i was so fed up with the exact same crash i got as described above. does anyone have a solution for this? im having a really hard time. im re installing ubuntu back onto the laptop soon, so im going to need some help. it would me most appreicated.

---

### Post by Nuberdrive on 2008-05-23
sorry, fogot to say im running feisty.

---

