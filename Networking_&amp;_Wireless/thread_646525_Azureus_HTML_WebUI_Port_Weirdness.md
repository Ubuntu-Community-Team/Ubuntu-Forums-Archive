---
title: "Azureus HTML WebUI Port Weirdness"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by debillin on 2007-12-21
I've installed Azureus and the HTML WebUI successfully.  I have forwarded the port 6886 through my router to my computer.  I can successfully access the UI from my home computer using either localhost:6886 or my cable modem's IP, let's say 123.123.123.123:6886.  However, when I try to access it from work, using the previous mentioned cable modem IP, the request times out.  I even tried changing the WebUI  port to 49255 and forwarded it through my router, to no avail.

Any ideas?  I think it's weird that I can access it from my home computer using my global IP, but using that same IP at work, it times out.  I can access my apache web server on the same box, no problem.

Please help!  Thanks in advance!

---

### Post by debillin on 2007-12-21
oh yeah, I've also configured iptables to accept tcp connections on both the 6886 port and the 49255 port

---

