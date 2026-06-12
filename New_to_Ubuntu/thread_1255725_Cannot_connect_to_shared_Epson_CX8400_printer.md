---
title: "Cannot connect to shared Epson CX8400 printer"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by cjdahl60 on 2009-09-01
I am running Ubuntu 9.04 on a laptop and connect to my home network of Windows PCs.  One of the PCs has a shared Epson Stylus CX8400 printer connected to it.  All of the Windows PCs can print to this shared Epson.

I configured a new printer in Ubuntu, using a device URI of smb:/{workgroup}/{computer name}/{printer share name}.  When I attempt to send a test page, the job times out with an error message "Idle - Connection failed; NT_STATUS_ACCESS_DENIED."

I've verified that all of the share permissions are correct on the host Windows machine.  All of the WIndows PCs have no problems.  I'm new to Ubuntu, so I'm probably missing something obvious, but any suggestions would be greatly appreciated.

---

### Post by st33med on 2009-09-01
Windows Printers can be setup easily. Go to System >> Administration >> Printing and click New Printer. Go to Windows Printer via Samba and click browse.  Click on the shared network you use click the printer, and hit OK. The rest should be obvious. :)

---

