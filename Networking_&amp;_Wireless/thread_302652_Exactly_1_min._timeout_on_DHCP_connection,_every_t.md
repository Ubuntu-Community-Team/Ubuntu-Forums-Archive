---
title: "Exactly 1 min. timeout on DHCP connection, every time"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by outofnicks on 2006-11-18
I'm using a shared dialup connection from an iMac running OSX Panther to my PC running Ubuntu, because I can't figure out the modem driver nightmare. That's another issue which I don't want to discuss right now but I'm having a wierd problem with the connection on a new install of Kubuntu, on the same PC but another partition. The shared connection has worked just fine in Ubuntu for almost a year now, but in Kubuntu, it times out after exactly one minute, repeatedly. I don't know where to start on a solution to this problem, can someone give me a pointer or two please?

---

### Post by Amitava on 2006-11-19
It is the common problem with dial-up connection, follow the trick

**ping -i 300 [www.ubuntuforums.org](www.ubuntuforums.org) > /dev/null &**

this trick will keep ur connection up...i used to do it with my CDMA mobile 2 internet connection.

---

### Post by outofnicks on 2006-11-19
Thanks for the reply Amitava, but it's not a problem with my dialup connection. That works fine on the Mac, and on the shared connection to my PC when I'm in Ubuntu. I have the Network Settings configured for a basic DHCP Ethernet connection with a crossover cable from the Mac to the PC. But when booted into Kubuntu, on the same PC (same hard drive but different partition) and with exactly the same configuration, the connection times out after exactly one minute.  This is a fresh install of Kubuntu--what's weird is before installing, it worked fine using the live CD. 

I think my problem will be solved when I just add kubuntu-desktop to my Ubuntu installation, I didn't realize I could do that when I installed Kubuntu on another partition. I'll have to haul my computer to a friend's house with a DSL connection. I've been happy with Ubuntu for almost a year now but after taking a look at Kubuntu I like KDE much better.

---

### Post by outofnicks on 2006-11-20
> I think my problem will be solved when I just add kubuntu-desktop to my Ubuntu installation, I didn't realize I could do that when I installed Kubuntu on another partition. I'll have to haul my computer to a friend's house with a DSL connection. I've been happy with Ubuntu for almost a year now but after taking a look at Kubuntu I like KDE much better.

This has been done, problem resolved. Well not actually RESOLVED--I didn't figure out why the ethernet connection timed out like that, but have no reason to now.

---

