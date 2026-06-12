---
title: "CUPS or Samba? (Win host &amp; Ubuntu guest - wireless printer)"
date: 2017-10-10
forum: Networking &amp; Wireless
---

### Post by afrenz on 2017-10-10
I have Win 10 host and Ubuntu 16.04 guest (VBox 5.1.28). I would like to print from guest to wireless HP printer. 

Any pointers on how to get started? 

Ultimately, I'd like to also have a shared folder, but that is probably another post for help.

TiA!

---

### Post by SeijiSensei on 2017-10-10
If the printer sits directly on the network, you should be able to connect to it with CUPS.  Try opening [http://localhost:631/](http://localhost:631/) on the Ubuntu machine, then follow the steps to add a printer. Often it will be discovered automatically, though you might have to add it manually via its IP address.

Are you running the VM with the network interface in "bridged" mode?  That might make things easier since then the VM and the printer will be in the same IP subnet.

---

### Post by afrenz on 2017-10-10
Printer is wirelessly connected via Fronter router.

In VB one NAT was installed. Three other adapters or disabled.

---

### Post by SeijiSensei on 2017-10-10
Try switching to "bridged" mode and see if CUPS can find the printer.

---

### Post by afrenz on 2017-10-10
> **SeijiSensei said:**
> Try switching to "bridged" mode and see if CUPS can find the printer.
You are pretty smart! That worked!! Thanks ;)

Now I want to figure out how to share a folder (win10 host & ubuntu 16.04 guest). Should I change to the title or submit a new post?

Do I need to do something to give you credit for solving my issue?

Thank you!

EDIT: I'll mark it solved and try 'shared folder' thing via searching. Thanks again.

---

