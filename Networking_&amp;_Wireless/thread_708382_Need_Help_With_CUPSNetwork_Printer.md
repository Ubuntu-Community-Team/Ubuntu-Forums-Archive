---
title: "Need Help With CUPS/Network Printer"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by cdv on 2008-02-26
Running Gutsy. Cannot connect to printer on XP machine. Error log shows that about every 5 seconds or so Gutsy/CUPS tries to connect to the printer. I don't know how to interpret the error messages. Here they are:

CUPS-Get-Printers
cupsdProcessIPPRequest: 16 status_code=0  (successful-ok)
cupsdReadClient: 16 POST / HTTP/1.1
cupsdAuthorize: No authentication data provided.

I'm on a dual boot machine with Vista/Ubuntu. Vista connects to the printer on my other machine with no problem. Other than this printer thing Gutsy works fine. Everything else I try under Gutsy works as advertised. Gutsy grabs the internet signal from my wireless router with no problem. Just can't make the printer on the other machine work.

---

### Post by Zill on 2008-02-26
AIUI CUPS (Common Unix Printing System) is only used for Linux-to-Linux connections.  Samba (SMB) should be used for Linux-to-Windows connections.

These links may help you set up printing from Ubuntu to XP, although I can't verify this as I don't let Windows anywhere near **my** PCs :-)

[http://ubuntuforums.org/showthread.php?t=54346]("http://ubuntuforums.org/showthread.php?t=54346")

[http://ubuntuforums.org/archive/index.php/t-32190.html]("http://ubuntuforums.org/archive/index.php/t-32190.html")

---

