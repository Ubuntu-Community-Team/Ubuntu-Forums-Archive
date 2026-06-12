---
title: "Can't print to windows shared printer"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by groovomata on 2007-03-22
Hello All,
I'm having a problem printing to a printer connected to a windows machine in a small office workgroup of four windows computers. I can connect to the network, can see the windows machine and can even browse some of it's directories, however I can't see it's printer - an HP 4318. 
Does anyone know what I should do to connect to this printer and successfully print to it?
I'm using a compaq V5000 with edgy.
Thanks in advance!
Erik.

---

### Post by bloodniece on 2007-03-22
Can the Windows-based PCs print to this one?
Just be sure the network printer is being shared from the Windows side.

---

### Post by JoxBG on 2007-03-22
Network printers do not show up in file-browser (nautilus). Go to System/Administration/Printing and add a printer. Choose network and SMB in dropdown box. You will go thorugh two authentication sessions, one for host and one for listed printers.

HTH,

Jox

---

### Post by groovomata on 2007-03-23
Thanks for your help folks. I discovered that under the connection tab of the printer properties in System, Administration, Printing; I can set the connection as a 'Windows Printer (SMB)' I entered my user name and password to access that resource and now it works perfectly!
Woo Hoo!
All the best,
Erik.

---

