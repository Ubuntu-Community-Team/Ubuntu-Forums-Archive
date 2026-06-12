---
title: "Very Strange"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by mrmeetze on 2006-08-16
Okay, so I'm a little new to Ubuntu, and somewhat familar with Linux.  I have never seen anything weird happen with my Linux systems that I couldn't find on a forum and fix it.  However this one blows me away.

I couldn't get Eth0 working, so I bought a new NIC card (even Windows Xp Pro wasn't picking up my Eth).  Put in the NIC card booted up, and disabled Eth0 and Eth1.  Then I enable Eth1 again and voila!  Internet works fine.  No problems.  Even as I am talking to you there is no problems with my internet... BUT here is where the weird part comes in...

Right now, though I'm online, I HAVE to leave my Network Settings GUI open.  If I close it I can't go anywhere on the internet via Mozilla Firefox.  :confused: :confused:  GAIM works fine.  I can chat with everyone, but browsing the net will not work.
:-k 
Maybe this is more of a Mozilla Firefox problem, or something wrong with my configuration?  Any suggestions are welcome please.

Danke!
M. Meetze

---

### Post by Seldoms on 2006-08-16
Open firefox type about:config in search bar hit enter.

In filter type ipv4

and change from false to true

---

### Post by mrmeetze on 2006-08-17
Okay I just did that, but I don't see ipv4.  And when I type "ipv4" in the filter, it gives me "network.dns.ipv4OnlyDomains" but does not have a value string of false or true?  here is what i have:

network.dns.ipv4OnlyDomains   default    string   .doubleclick.net

:confused: 

do i just change default to true?


danke
-meetze

---

### Post by mrmeetze on 2006-08-17
hey I think I figured out what the problem was... maybe it was because I didn't reboot?  It works fine now after I rebooted.

Thank you anyways!
-M. Meetze

---

