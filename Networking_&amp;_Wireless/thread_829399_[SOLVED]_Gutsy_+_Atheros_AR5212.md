---
title: "[SOLVED] Gutsy + Atheros AR5212"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by groundskeeper on 2008-06-14
I upgraded from Feisty to Gutsy a few months ago and it broke my wireless ethernet. I pounded my head against it for a while and then gave up. I've been using Vista now for several months and want to get back to Ubuntu. I backed everything up to external HDD and have re-installed Gutsy from scratch (actually twice or three times now). I've gotten through issues with my T60's ATI X1400 graphics card, but the wireless card is still not working. I've found various howto threads/pages, but none of them seems to be applicable to my situation (AR5007, Hardy, Gutsy 64bit, etc.). I'm really going crazy trying to get this to work. Any help or just a referral to a HOWTO would be immensely appreciated.

:confused::mad:

---

### Post by groundskeeper on 2008-06-14
Wired network works fine. Roaming mode allows me to select my network (or my neighbors', but I don't know their network keys). I get an IP address in the correct range. Any attempt to access, for instance, google, without the wired network plugged in eventually times out with what appears to be a DNS error. I used to have trouble under Feisty with my router's internal DNS server and I'd have to remove the local addresses from the DNS server list before things would work, but that's not helping.

Please help.

---

### Post by trorion on 2008-06-14
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

worked for me but whenever I shut down I have to unclick on some things in "hardware manager" and then boot up twice to get it to work.  good luck!  (basically it amounts to using ndiswrapper)

---

### Post by groundskeeper on 2008-06-14
Thanks for the reply, but that's for an Atheros 5007EG; I have a different chipset. Also, it says the approach is deprecated for 32-bit OS users and then points 32-bit OS users to a different HOWTO that requires access to madwifi.org, which appears to be down. 

I swear this issue is trying to kill me. I gather from the large volume of traffic on the various threads that wireless networking is a common problem. It's very depressing; I used Edgy and Feisty for nearly a year before a printing problem prompted me to upgrade to Gutsy and now I'm completely lost. I really enjoyed using Linux, but I guess I'm just not smart enough to continue with it. I'm glad what you've got is working for you, but I must say what you descibe as "working" (unclick some things, reboot, reboot, reboot) seems pretty broken to me.

---

### Post by groundskeeper on 2008-06-14
I can't tell if what I've got is even supposed to work. What is the correct/current madwifi driver version? How do I find the version that I have installed? Is it normal for me to see the wireless networks and then have no luck actually connecting to them? Should I replace the ethernet card with the Intel PRO/Wireless 3945ABG? Should I replace the wireless access point (an ancient Orinoco that works fine with all other computers, and used to work with this computer)? Should I replace my computer with a different one? Should I try Hardy? Should I timewarp back to 2006 and install Edgy?

---

### Post by groundskeeper on 2008-06-14
> **trorion said:**
> [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

worked for me but whenever I shut down I have to unclick on some things in "hardware manager" and then boot up twice to get it to work.  good luck!  (basically it amounts to using ndiswrapper)

ndiswrapper worked! you are THE PERSON!!!!:guitar:

---

