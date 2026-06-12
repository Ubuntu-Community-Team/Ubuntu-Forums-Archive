---
title: "Madwifi not working correctly after new HDD + gutsy install"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by Tidder on 2008-04-21
Bizarre problem I am having.  Let me start with a little background.  I've had Gutsy 64-bit loaded on my laptop for a few months, with Atheros AR5212 (actually an AR5005GS if I remember correctly) working fine after building madwifi from svn r3367.  Just purchased a new HDD, and decided to go ahead with a fresh install of gutsy 64.  After fresh install, downloaded madwifi's newest svn (r3559) and I cannot connect to any networks.  Network manager sees the networks around me, including mine.  Trying to connect to my network does not work. Using iwconfig to connect manually also does not work. So I removed madwifi drivers, and checked out r3367 from svn.  Same version I had working previously on this same laptop.  Same issue.  I've checked my syslog, and it's identical to the syslog on my old HDD as far as any madwifi or ath notifications go.  Popping back in the old hard drive and booting into ubuntu, my atheros card works fine!  What the HECK is going on here?  I've checked to make sure linux-restricted-modules are not loading ath_hal, and I've noticed on my old hard drive, linux-restricted-modules aren't even loaded, so I removed from the new HDD as well. But same problem.  What am I doing wrong here?  /etc/network/interfaces is identical on both HDDs.  What else can I check between drives?  ath_hal versions are the same, other ath components are the same svn revision number between drives.

I'm definitely lost here...

---

### Post by Tidder on 2008-04-24
Think I figured it out.  I originally had Feisty loaded, and upgraded to Gutsy.  I think there is an issue with Gutsy that is preventing me from getting my wireless working, that wasn't there originally because of the upgrade.

Hardy was just released though, and is working fine.  So I'm just going to forget this ever happened. :)

---

### Post by SandmanXC on 2008-04-24
I've had Gutsy and upgraded to Hardy. I also have an Atheros AR6007 i think. I used madwifi and now i don't have any access to the wireless interface. What should i do??

---

