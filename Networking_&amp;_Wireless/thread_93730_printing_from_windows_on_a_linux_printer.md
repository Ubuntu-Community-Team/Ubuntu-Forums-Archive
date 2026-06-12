---
title: "printing from windows on a linux printer"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by racookier on 2005-11-22
I have a printer plugged to my ubuntu workstation, i print to other windows machines on my net, but the windows machines can't print to my linux printer

p.d. have "samba" and "cups" running](*,)

---

### Post by basketcase on 2005-11-22
Do you have the printer that is on the linux box installed correctly?  

I fought for a while with my setup at home (fedora core 3 and winxp).  Are your permissions correctly setup to allow the winxp user to print?

---

### Post by MartinG on 2005-11-22
Do you have the samba server running, or only the samba client? (You need the server, which is not installed automatically). And have you got the right ports open (137-139, 445)?

---

### Post by racookier on 2005-11-23
Yes i have samba server running, and the printer it's installed on linux box ok.
will review the link, and wait.:confused: (in fact printing from other linux machines works fine and printing to windows machines works fine) i follow steps listed on the "wiki" and on the "cups documentation", serach documentation... The windows machines can see the printer, but othing happens.

---

### Post by racookier on 2005-11-28
Finally.... I can print from windows machines

---

### Post by schdefan on 2005-11-28
It is not really necesary to use samba to share your printer in the windows clients. cups makes it very easy. Read here:
[NetworkPrintingFromWinXP]("https://wiki.ubuntu.com/NetworkPrintingFromWinXP?highlight=%28NetworkPrintingFromWinXP%29")  
If you do it this way you don't have to fight with permission in the smb.conf

schdefan

---

### Post by racookier on 2005-12-01
I try many docs in the wiki, but with this doc. i have "port is not available", but as i told, finally I can print from windows machines

Thank you very much for replies

---

### Post by KermitJr on 2005-12-12
[QUOTE=racookier]I try many docs in the wiki, but with this doc. i have "port is not available", but as i told, finally I can print from windows machines

Thank you very much for replies[/QUOTE]

Yes, but how did you fix it?  Always nice to close your posts with that for people searching.

---

### Post by WebsterTrivium on 2005-12-12
It's not necessary to get Samba and Cups working together to just share a printer, but if you want the printer driver to be provided by the linux machine to windows (So you don't have to do it manually, for those weird printers that don't have standard windows drivers, and then I don't have to dig for disks all the time.) you do need to get it all playing nice...

Which is what I'm trying to get working right now, anyone been through this that could offer a hand? I'm having issues with cupsaddsmb, NT_STATUS_NETWORK_ACCESS_DENIED
NT_STATUS_ACCESS_DENIED

problems on some on the smbclient commands it generates.

If anyone knows how to work with this, I would appreciate it!

---

