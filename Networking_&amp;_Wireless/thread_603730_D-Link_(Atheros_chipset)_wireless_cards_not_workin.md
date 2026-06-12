---
title: "D-Link (Atheros chipset) wireless cards not working"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by clashfan on 2007-11-05
I'm new to Ubuntu and I have a couple of D-Link wireless that just will not work in Ubuntu. I can get my Linksys wireless cards to work but not any of my D-Link cards. I believe the D-Link cards use the Atheros chipset. Ubuntu can detect the D-Link cards but will not connect to my router. I'm a total newbie to Ubuntu/Linux so any help will be appreciated. I'm running 7.10

---

### Post by l33t_3lv3n_g33k on 2007-11-05
If I remember correctly, not all D-Link cards are the same chipset.  I have a D-Link DWL-G132 that doesn't play with Network Manager.  I had to use [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/") with the Windows driver supplied on the D-Link website to get it up and running.  
 
Sadly, a recent update to the driver made the card *EXTREMELY *flaky.  Locked up the whole system after a random amount of time.
 
Anyhoo, enough of my sad tale...
 
What are the models of your D-Link cards?  They might be listed on the [List of Cards SUpported or Known to Work]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") at the ndiswrapper website.  Worth a shot.

---

### Post by dysolve on 2007-11-05
which dlink wireless card do you have? I used both ndiswrapper and madwifi to run both of mine, I found madwifi was more stable, madwifi is heaps easier to use but before I tell you had to install madwifi is your card really arteros card?

---

### Post by jdier on 2007-11-13
> **clashfan said:**
> I'm new to Ubuntu and I have a couple of D-Link wireless that just will not work in Ubuntu. I can get my Linksys wireless cards to work but not any of my D-Link cards. I believe the D-Link cards use the Atheros chipset. Ubuntu can detect the D-Link cards but will not connect to my router. I'm a total newbie to Ubuntu/Linux so any help will be appreciated. I'm running 7.10

How can I not help out a fellow fan of The Only Band that Ever Mattered?

I struggled with my DWL-G650 which is also Atheros.  I stumbled on [www.madwifi.org](www.madwifi.org) and within 15 minutes (just following the newbie section) I was up and running.  Take it slow and go step by step.  It was really easy!

---

