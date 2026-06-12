---
title: "Printing from Windows to Ubuntu Edgy"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by rlgoddard on 2006-11-17
Hi,

Since upgrading to Edgy, network printing has been officially borked.  I had a nice setup through Samba when I was using Dapper.  Windows detects the printer and shows that the print job got to the HP Deskjet 5650 that's connectd to Ubuntu Edsgy.  But 20-40 minutes passes before I have to kill whatever application I used to print, and the printer spits out a blank page.  I've tried all kinds of settings, but can't get it working.  Is there anything I need to change in cupsd.conf in order to be more compatible with Edgy?  I'm at my wit's end here ](*,)

Thanks for any help you may have for me!

Take care,
Russ

---

### Post by rlgoddard on 2006-12-08
I guess no one has the answer?

---

### Post by cesera on 2007-01-05
Have you come across the following link:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

I am just about to try it, will let you know if it works on my Edgy install.

---

### Post by Robin T Cox on 2007-01-06
I'm using Edgy with Samba in  a wired home network connected to a Windows 2000 Pro desktop. I have a HP 710C printer connected to my Edgy machine, and I set the whole thing up by following this thread:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

I haven't done anything beyond what it says in the above link.

---

### Post by cesera on 2007-01-08
> **Robin T Cox said:**
> I'm using Edgy with Samba in  a wired home network connected to a Windows 2000 Pro desktop. I have a HP 710C printer connected to my Edgy machine, and I set the whole thing up by following this thread:
 
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
 
I haven't done anything beyond what it says in the above link.
 
You have virtually the same setup as I have (Edgy + Win 2K Pro on wired network), only the printer is different I have a HP DeskJet 3748 and the link I mentioned in my previous post solved my problem (just skip the client machine bit). Backup your /etc/cups/cupsd.conf file before you replace it with the one in the link and give it a try. If it doesn't work just restore the backed up file and nothing has changed on your machine.

---

