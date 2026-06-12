---
title: "Intel 5100 Wireless card in Intrepid"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by ems5311 on 2008-10-31
Hey,
I had been having no luck getting my Intel 5100 card to work in Hardy (much like these guys in [this thread]("http://ubuntuforums.org/showthread.php?t=879134")), but many people in that thread reported that 8.10 picks up this wireless card right away.  After upgrading, I found out that this is certainly not the case.  My wireless card is still not working with ndiswrapper drivers (though it says "Hardware Present: Yes").

I uninstalled those drivers and followed some advice in that thread ([this one]("http://ubuntuforums.org/showpost.php?p=5657450&postcount=16") for example), but nothing has worked yet.  I have heard that a total reinstall from .iso will get wireless working, but that's something I really don't want to do.

Anyone else having this problem, or has anyone found a solution?  Thanks in advance.

---

### Post by luxanimi on 2008-10-31
suggestion.......install ubuntu again......
in my thinkpad sl300 the 5100 is working with intrepid....after the upgrade from 8.04 to 8.10 was not.......a fresh installation could help....:-)

---

### Post by apophis123 on 2008-11-01
Hi! 

I just solved this problem for me:

At first, download the firmware from here: [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz")

Extract it and copy it to '/usr/lib/firmware' (i had to create this directory).
Restart and thats it!

If this doesn't work for you: In another thread i read that some people just reinstalled the 'linux-firmware' package with adept. Didn't work for me though.

---

### Post by Cristatus on 2008-11-04
Does this solution work? I tried installing Intrepid, through WUBI, and the card did work, but when I shut down my machine and then start it back up again, I have to disassociate from my access point, and then put in the the password again.

Anybody have a similar issue?

(C)

---

### Post by Cristatus on 2008-11-15
Ok, I've got the 5100 to work, but I haven't restart my system yet, so I don't know if it's still got the same problems as above, but I've got another problem (that was also present when I installed Intrepid Ibex last time around) : the connections are very slow...!

I'm not talking about only downloading files from HTTP or FTP connections, but also just browsing on the internet.

(C)

---

### Post by thomasaaron on 2009-01-30
This suggestion did not work for me.

---

### Post by dimvcf on 2010-01-09
Hi 

I had the same problem with  Intel 5100 Wireless . I found the solution in [older thread]("http://ubuntuforums.org/archive/index.php/t-1017451.html")

Good luck.

---

