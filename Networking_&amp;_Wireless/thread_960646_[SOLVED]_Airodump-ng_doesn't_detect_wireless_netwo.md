---
title: "[SOLVED] Airodump-ng doesn't detect wireless networks"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by t0p on 2008-10-27
As the title says, airodump-ng isn't detecting wireless networks.  I need some help/advice troubleshooting this, as I'm an aircrack newbie.  I'm using the aircrack-ng suite on an eeepc running ubuntu 8.04.1.

When I run kismet, it detects 3 or 4 local wireless APs.  But when I run airodump-ng, it detects nothing at all.  This is despite the fact that I killed all the processes identified by airmon-ng as potentially problematic.

When I'd just installed airodump-ng, a fortnight ago, it worked fine.  This problem surfaced just a few days ago.  And I'm not sure what I can do about it.

---

### Post by guest_user on 2008-11-01
got the same problem here

---

### Post by t0p on 2008-11-04
Okay, I'm marking this as "solved" because I've discovered why airodump-ng wasn't working.  Of course, now I have another problem that needs solving - how to make it work properly!! - but anyway, here we go.

I have discovered that, to make airodump-ng work on my Eeepc running Hardy, **I must first connect the Eeepc to a wireless network**.  I'm not kidding. And the really weird thing is this: once airodump-ng and whatever is working, I can then disconnect from the wireless network and airodump-ng will continue working.  I just need to be connected to a network in order for airodump-ng to *start*.

So fine, I now know why airodump-ng wasn't picking anything up.  Problem solved.  Whoopie!  But now I want to know **how can I fix this ridiculous behaviour?**  Because it is truly daft - if I am pentesting someone's wireless network, chances are there won't be any local networks for me to join before I fire up the aircrack-ng suite.  So I won't be able to start my pentesting tools.  So I won't be pentesting anything...

If anyone can shed any light on *why* my system is behaving in this way and *how* I can fix it, I will be forever grateful.

:confused:

---

### Post by guest_user on 2008-11-04
erm then I don't think you should put it as solved in the title else no one would come in here to give you solutions.

---

### Post by t0p on 2008-11-05
> **guest_user said:**
> erm then I don't think you should put it as solved in the title else no one would come in here to give you solutions.

LOL yeah I know, but 1. It *is* solved, after a fashion.  I know why airodump-ng wasn't responding.  I fixed *that* problem; 2. I know that no one's going to come along and tell me how to fix all this.  My previous post was tilting at windmills really.  Though I live in hope...

---

### Post by sapto on 2010-08-05
Can you help me?Can I run airo dump on win 7?I have Atheros ar5b91 in lap top...is that compatibility?Thanks

---

### Post by chaeo on 2010-12-12
Had this same problem myself.

airmon-ng start wifi0 1

...where '1' is a channel number. 1 works fine to kick it into life
and detect other channels via the:

airodump-ng ath3

(Where ath3 = whatever you use)

---

