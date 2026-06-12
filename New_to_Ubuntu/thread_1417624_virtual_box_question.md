---
title: "virtual box question"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by degarb on 2010-02-27
I am trying to do a "proof of concept"  for the dream OS.   Ubuntu and vbox, with a functional xp (probably works better out of box) or windows 2000 sp4 (better licensing).

So far, running xp as guest, it seems to freeze up vbox when any kid programs force video to 256 colors.  And I downloaded latest vlc 1.05 but didn't work.  (I installed guest host and experimental direct x, which i don't know if the problem.I

XP boots in 4 minutes flat, and 2000 in ten minutes, and doesn't recover well from crashes.   I could tolerate 2000 (install on as many home machines as I can buy and find a use for in our house), if it would fill all gaps in wine.  I wonder if there is a kernel extension  for 2000 to extend the functionality of it.  [http://sourceforge.net/projects/kernelex/](http://sourceforge.net/projects/kernelex/)

---

### Post by inclusivedisjunction on 2010-02-27
I think your question (if you can call it that) is outside the scope of VirtualBox. KernelEx does not "extend functionality" per se; it emulates API calls of newer versions of Windows on 98/ME. Nothing like this would help you in any way with your stability problems. Both boot times for XP and Windows 2000 are quite ridiculous; both should boot in less than a minute on any reasonable amount of hardware (ie Pentium 4 or higher). I assume you are either using an older computer, or have allocated more RAM to the guest than the host can safely provided. Have you installed the VirtualBox guest additions? This may address stability issues when switching video modes vs. the default VESA driver in XP.

---

### Post by theozzlives on 2010-02-27
All I hear is 2000 and XP, you do know this forum fixes Ubuntu problems right?

---

### Post by HotShotDJ on 2010-02-27
Which Ubuntu version are you running?  32 or 64 bit?  If you are running Karmic 64 bit, you may have serious issues running Windows (2000 and XP, I haven't tested Vista or Win7) under VirtualBox. Similar issues exist with VMWare. This is a known issue that is not likely to be fixed in Karmic.  However, the Kernel used in Lucid (2.6.32) fixes the problem(s).  Before you start screwing around with trying to "fix" things, you would probably be better off waiting until April when Lucid is scheduled for release.

---

### Post by degarb on 2010-02-27
> **inclusivedisjunction said:**
> I think your question (if you can call it that) is outside the scope of VirtualBox. KernelEx does not "extend functionality" per se; it emulates API calls of newer versions of Windows on 98/ME. Nothing like this would help you in any way with your stability problems. Both boot times for XP and Windows 2000 are quite ridiculous; both should boot in less than a minute on any reasonable amount of hardware (ie Pentium 4 or higher). I assume you are either using an older computer, or have allocated more RAM to the guest than the host can safely provided. Have you installed the VirtualBox guest additions? This may address stability issues when switching video modes vs. the default VESA driver in XP.


Interesting points.  To clarify, I am just testing on old equipment, which runs surprisingly well.  I think people now days freak out at waiting.  Well, in my day waiting 2 minutes for a picture to load and 6 minutes to boot was normal.  So, I take the minimum specs with grain of salt.   I got vlc to run, after 10 minutes it was trying to update itself.  It ran rather choppy in the vm. 

I also never ran 2000 before, only xp (and win 85 to win 95 to win me).  I read it cannot do all the kid games, but not really sure of the limitations over xp. 


Again, ubuntu as host and looking for vbox  to fullfill running all wine failing aps , until the day that ubuntu has enough market share to force all developers to write for Linux.   
This will depend on how helpful this community remains and future releases.  Hey, I am this close to buying a Ubuntu tee shirt to spread the word.   But still not all essential aps run on wine, and dual booting doesn't appeal for more than an emergency os, when the first wipes out.

---

