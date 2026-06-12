---
title: "Hardy killing my router??"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by upforthedownstroke on 2008-05-01
Hey all, I just upgraded from Gutsy (which worked like a charm with my wireless network) to Hardy yesterday and I've had some issues. The driver system is a little weird; I used to run the ipw3945 restricted driver for my Intel PROWireless 3945 card and now that's not the package running... How do I find out what driver is running?

Also, I used to use airodump-ng and aircrack-ng as diagnostic tools for my network and others using the ipwraw driver for monitor mode support, which no longer works at the terminal using modprobe ipwraw. Perhaps I need to reinstall/update the packages? This is no big deal though.

The real problem has to do with my wireless router itself. I attempt to connect to my network with my Hardy laptop and my router resets its own power immediately. I have a crappy 2Wire Homeportal 1000SW DSL Modem/WAP, which according to AT&T (my ISP) is due to be replaced. However, my Xubuntu Gutsy desktop (via Ethernet) and my WinBloze XP laptop (wireless) both connect to this same router with no issues, as it was in the past. 

Why in hell would a client that hasn't even been able to authenticate itself on my network be forcing a refresh of my router??

HELP!

---

### Post by Nepherte on 2008-05-01
In Hardy, the ipw3945 driver has been replaced by iwl3945. So that should be the driver you are using.

---

