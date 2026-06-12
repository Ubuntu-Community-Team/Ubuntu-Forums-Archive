---
title: "why is this so HARD ????"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by bsmith1051 on 2006-08-11
I've just done a fresh install of Ubuntu 6.06 on a Compaq Presario 2100 laptop.  It's built-in wired ethernet was correctly detected and was used to download all initial updates.  The built-in wi-fi card was also detected -- "Broadcom 4306" -- but I've yet to get it to work.  Is the wrong driver being used?  How should I know?!

Obviously, I would appreciate some help here but I also want to ask some larger questions:

1. if a wireless card is detected during install, why isn't Network Manager (and it's GUI) automatically installed, too?

2. why does the wireless card default to 'inactive'?  Should I have left the ethernet cable unplugged during the install, would that have triggered a different configuration?

3. why is the one and only sticky note (in this "Wireless Support" forum) a highly specific discussion of a particular wi-fi interface, rather than a general purpose discussion about troubleshooting?  

I would love to see a sticky called, "What to do if your wireless network doesn't work."   Step #1 would be to get thee to a wired network connector and download/install the two Network Manager modules.  Step #2 would be determining if your card was being detected, at all.  Step #3 would be determining if you have the correct driver.  Etc.  [/rant]

As for my current situation, the card was working fine in Windows right up until the point I reinstalled with Ubuntu -- so I know it physically works.  It also shows-up in System > Administration > Networking, so I know it's detected.  Now that I have Network Manager running, it's showing no available networks even though I know I have one.  So how do I determine if I have the appropriate driver?

---

### Post by Zolox on 2006-08-11
What model of presario 2100 are you using im using 2108cl and after trying many things, I think using ndis wrapper and drivers downloaded from hp.com is what makes it semi work. Because when i hibernate then log back in it works. I don't know why but it works

---

### Post by bsmith1051 on 2006-08-11
I have the Presario 2195us.

I finally succeeded after following these directions,
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
and copying the latest Windows driver.

---

