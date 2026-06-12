---
title: "Print to a Samba Printer"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2008-08-20
I do not know if I am doing this right, but I am trying to connect to a Lexmark X3350 connected to a windows machine.

I assume the printers path it smb://lexmark3 (the printer's name is Lexmark3) or smb://hostname/lexmark3

I get an error dialog when I try to connect

---

### Post by wyliecoyoteuk on 2008-08-20
Is the printer shared from windows?
Do you have smbclient installed?

the Samba path should be smb://servername/sharename

It might be best to use smb://<ipaddressofserver>/sharename

Also needs file and printer sharing on the windows box, and permissions to access the shared printer.

---

### Post by RealG187 on 2008-08-20
I can access Samba shares but not the printer, I had trouble connecting to it in Vista though too, althogh it is shared...

---

