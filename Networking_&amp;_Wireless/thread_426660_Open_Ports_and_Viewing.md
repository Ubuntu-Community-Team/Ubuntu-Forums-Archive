---
title: "Open Ports and Viewing"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by ScottMorris on 2007-04-28
Hi there, I'm trying to find a command line tool that can scan the ports on my computer and tell me which ones are listening.  I have looked at something like [FONT="Courier New"]netcat[/FONT] but it didn't work - unless I used it wrong.  I know there is a graphical utility but I try to use as much command line tools as possible to get into the feel of it.  Does the graphical program just use an external program or does it have its own built in algorithm?  What is a good program to do this with?

---

### Post by aidanr on 2007-04-28
[http://whatsmyip.org/ports/](http://whatsmyip.org/ports/)

also check out netstat (man netstat)

---

### Post by ScottMorris on 2007-04-30
I had no luck with netstat, is there any other program?

---

### Post by lrhaugen on 2007-05-16
Hi, try nmap (man nmap) to scan for port status.
Sorry for the late answer....

---

### Post by ScottMorris on 2007-05-16
> **lrhaugen said:**
> Hi, try nmap (man nmap) to scan for port status.
Sorry for the late answer....

Hey, thanks, nmap  did the trick :)

---

### Post by jonallport on 2007-05-17
NMAP is the de-facto port scanner (i've just tried 4 times to type scanner and kept typing snaccer, Freudian, I must be hungry!).  There is a GUI Front End (NMAPFE) for you click-happy types.

---

