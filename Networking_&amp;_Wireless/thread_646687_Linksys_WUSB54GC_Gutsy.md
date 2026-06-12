---
title: "Linksys WUSB54GC Gutsy"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Kopachris on 2007-12-21
So I want to put Ubuntu Gutsy on my PC.  The only wireless card I have for it is a Linksys WUSB54GC.  I basically want a sum of how well the card works in Gutsy, or if it doesn't, a sum of how I can make it work.  There are all kinds of threads out there about this particular card, but I don't have the time or patience to read each and every one of them.  (Actually that's not entirely true, I do have to time.  I have 6-10 weeks until the Ubuntu CDs get here.)  Can someone give me a summary?
Hardware:
Oldish AMD Athlon processor
1 GB RAM
ASUS Motherboard
ATI All-in-wonder Radeon 64 MB video card
Audigy Sound blaster 24 bit
Linksys WUSB54GC USB wireless card

That's the most detailed description of my hardware I can give you until I get back home.  Merry Christmas!

---

### Post by mLes-_- on 2007-12-21
Your going to be in the same boat as me... I have the exact same system as yours except I have and Nvidia card and a Linksys wusb54gSc v2.  I got it to work and connect to my wireless.  I did the updates and it stopped working.  I havent been able to fix it since. hahaha

---

### Post by Kopachris on 2007-12-22
Well...  That's not encouraging...

---

### Post by Kopachris on 2008-01-10
For future reference, the networking in Ubuntu Gutsy works very well.  The WUSB54GC works straight out of the box.  Simply plug it in, go up to the little network thingy in the toolbar and select a network.  Now, why doesn't Gutsy work on PPC?  W/e, it matters not.

P.S. I figured out what processor it was: an Athlon XP

---

### Post by Vadi on 2008-01-10
They dropped support for PPC, Since pretty much no company is supporting it as a desktop CPU anymore.

---

### Post by Maricaibo on 2008-01-16
WUSB54GC does indeed work in Gutsy out of the box.

Just spent all day trying to get it to work in Fiesty, Gutsy, using NDISWRAPPER but I saw this post and viola! Working wireless...but it WAS right after a fresh install so for those already running Gutsy your results may vary-

There have been a few posts on the WUSB54GC not working at boot, that it must be removed until after logging in and then plugged in. I think the real cause is the wireless stack not loading at boot- regardless of the NIC being used. I modified my /etc/rc.local file to initialize the card at boot and it works for me. See my post at [http://ubuntuforums.org/showthread.php?t=571188&page=18]("http://ubuntuforums.org/showthread.php?t=571188&page=18"). Note there is an entry in the rc.local file for a WEP key. If you're not using WEP security you should be.

---

