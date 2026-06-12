---
title: "howto see available networks - Broadcom BCM4318 WiFi card"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by asnd16 on 2006-11-10
OK installed the newest version of ubuntu today and not too sure how to verify that my wireless card is working or how do I connect to a wireless network?  Is there a program that searches for available networks? Installed wifi radar but shows no signals. Sorry quiet the noob so I do aplogize if this a stupid question.

Ran lspci and it knows that it is a Broadcom BCM4318 soooo I Guess I am at the point of wondering how the hel* do I see/scan for other networks and thus connect to them after that. 

I have a HP Pavilion dv4000 (dv4035us) with a Broadcom Corporation BCM4318
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00578143&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00578143&lc=en&jumpid=reg_R1002_USEN")

---

### Post by drfalkor on 2006-11-10
try to follow this howto: [http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by ckonrad on 2006-11-10
The drivers for your card are proprietary so you need to use the windows drivers for your card with a wrapper program the best driver wrapper for wireless out there is called ndiswrapper.Try out this method it took me about 3 minutes to get my wireless working, just go here and follow the directions. [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
The author of that post has created a nice little shell script, it works best with a fresh install of ubuntu. It was the first thing i did when i installed ubuntu and took about 3 minutes to get my wireless working.

---

### Post by asnd16 on 2006-11-13
still got quite a few issues. . . . it worked the first day until I restarted then I culd no longer veiw wireless networks, then the second day was the same thing. . . How can I get it to work again??

---

