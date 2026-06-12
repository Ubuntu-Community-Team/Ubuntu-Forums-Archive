---
title: "My Broadcom wireless driver saga is almost to end...with your help!"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Bluenoser81 on 2010-09-22
Hi folks,

I'm new to Ubuntu (tried it once back about 4-5 years ago but had so many hardware problems that I decided to wait awhile before I tried again).  So, I just bought an Acer Aspire 5251-1005 and decided to check out what 10.04 LTS was like. Presto! It worked! well almost...the wireless wasn't working for awhile and I did some research. Eventually figured out the drivers weren't installed during the installation because they are proprietary, and I take it that is against the free-license (or something like that). I ran "Hardware Drivers" from the menu and the driver "Broadcom SATA..." (something close to that) shows up.  When I clicked activate, it worked!

Now, here's the problem: every time I shut down and reboot, my wireless doesn't work anymore. The only solution I found was going back into "Hardware Drivers" and removing the Broadcom SATA driver and then reinstalling it. It will work fine again after I do this, so my question to you all is how do I simplify/automate/correct this irritation?

---

### Post by skyjacker on 2010-09-22
Are you running from a LIVE CD, or did you do a complete install from the CD?  The live Cd will not save changes that are made to it.  If you did an install, did you set up the name and password assigned to the wireless modem?

---

### Post by skyjacker on 2010-09-24
Bluuenoser81, If this answer solved your problem, please mark this thread "solved". To do this go to the "Thread tools" at the top and choose "Mark as solved". This will remove it from the listings as needing help. If it didn't help, get back to us and we will see if we can solve the problem. Thanks, skyjacker

---

### Post by Megaptera on 2010-09-24
Bluenoser,
Have you tried this?

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Bluenoser81 on 2010-10-11
Hi guys,

Thanks for the help and sorry I didn't respond sooner, I was having a heck of a time with the system.  After running updates to see if that would resolve anything, I couldn't boot back into Ubuntu because it said no operating system was found.  After struggling with that problem for a few weeks, giving up and recovering my Windows 7 partition, I thought I was done with Ubuntu forever (sorry I was disparaged so easily, but I'm pretty new to this and I'm a graduate student, so I don't have tons of time to tinker with things--it just has to work).  

The good news? The saga is over! For anyone who stumbles upon this post, the answer is Ubuntu 10.10.  10.10 includes the new open source wireless drivers directly from Broadcom (finally!), so you can choose to install 3rd party proprietary drivers when installing from the LiveCD (what I did from scratch).  These new drivers work like a charm.

---

