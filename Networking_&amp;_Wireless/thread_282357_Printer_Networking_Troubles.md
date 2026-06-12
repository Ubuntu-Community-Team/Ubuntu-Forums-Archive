---
title: "Printer Networking Troubles"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by ldvader on 2006-10-22
I have an HP DeskJet F340 printer. It is plugged into my WinXP machine and is being shared to my Network. My Labtop is running Ubuntu and connects to my network through a cable/router. SMB is working fine and files are being shared. I run the Printer setup in Ubuntu and it detects my networked printer. When I click to print a test page, everything works fine. My Windows system detects the printer request and fires up my printer, but then nothing prints. The job just sits in que. No Error Messages. Any suggestions?

---

### Post by KingArthur10 on 2006-10-24
On your XP machine, do you have a firewall program running such as ZoneAlarm?  If so, this can block incomming traffic to the printer (I had this problem myself long ago).  I would try disabling Zonealarm (or other firewall) for a minute and sending a print request.  If it works, then adjust the settings until you can still send print requests, but are still protected.

---

