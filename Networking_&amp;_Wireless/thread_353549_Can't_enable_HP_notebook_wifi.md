---
title: "Can't enable HP notebook wifi"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by bpro on 2007-02-04
Using 6.10, lshw indicates that my wireless card is DISABLED.  (Driver appears fine.)  The wifi panel button on my HP Pavilion zv6000 enables it under Windows, but doesn't appear to do anything in Ubuntu.  Does anybody know how I can enable wifi on this particular notebook so I can get connected?

TIA...

---

### Post by p!=f on 2007-02-04
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)
Search these forums, there're many threads.

---

### Post by jml on 2007-02-04
One other possibility.  I had a similar problem with my HP nx6110.  Have you tested to see if the wireless card is actually on?  This sounds like a stupid question, but in Windows the wireless light is always on when it is turned on by the power switch.  This little blue light is apparently controlled by software.  In Linux, the little light only flashes briefly when data is either being transmitted or received.  I worked for over 30 minutes on my laptop before I realized my wireless card had been turned off!!  This may not be your problem, but I thought I would mention it.

Joe

---

### Post by bpro on 2007-02-05
> **p!=f said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)
Search these forums, there're many threads.

Yeah, but it didn't looks like that one applied because I *think* my driver's okay.  You could be right, though... it's the infamous Broadcom 4318.

---

### Post by bpro on 2007-02-05
> **jml said:**
> Have you tested to see if the wireless card is actually on?

That's what I thought too, Joe.  One of the guides implied that was the problem.  The thing is... in Windows the panel button turns it on and off (as reported by HP's WLAN Assistant).  But the button doesn't seem to do anything in Ubuntu.  I don't know how to turn it on if that button doesn't work!  Any hints?

---

