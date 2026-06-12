---
title: "Can't use printer shared by NAS"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by EricDB on 2008-01-30
I have a SimpleShare 250 NAS device which also acts as a print server.  I've had no trouble accessing the file share, but I cannot get Ubuntu 7.10 to recognize the printer.  Here's what I've tried so far:

I open up Printer Configuration, click "New Printer", and it shows me "Searching for printers" for about 20 seconds.  Then it has me select a connection; I choose "Windows Printer via SAMBA". 

Then I click browse, WORKGROUP shows up in the list, under WORKGROUP I see SimpleShare, and under that I see the printer, "HP-LaserJet-30".  I select that and click "OK".

Then I click "Verify".  At that point, the app seems to hang (the main window, but not the New Printer dialog, turns gray).  Then it comes up with, "Inaccessible--this print share is not accessible".

My wife's XP machine has no problem printing to this printer.  And obviously mine can at least see it...but it can't connect for some reason.

How can I troubleshoot this?  Thanks!

---

### Post by EricDB on 2008-01-31
I've tried prepending the printer pool name "SimplePool" to the printer location, but that had no effect.  Could the fact that the fileshare pool and printer pool are both named "SimplePool" cause a problem?  

Doesn't seem to affect windows, though...

---

### Post by EricDB on 2008-02-03
I finally stumbled upon the answer on my own...so in case anyone searches this, here's what worked for me:

After browsing (successfully!) for the printer, here's what Ubuntu filled in for me:

smb://WORKGROUP/SIMPLESHARE/HP-LaserJet-30

Changing it to:

smb://192.168.1.102/HP-LaserJet-30

...(replacing "/WORKGROUP/SIMPLESHARE" with the IP address of the SimpleShare device) solved the problem.  No idea why, but it does work.

---

### Post by AVH on 2008-03-19
Thanks. You solved my problem.

Alan

---

