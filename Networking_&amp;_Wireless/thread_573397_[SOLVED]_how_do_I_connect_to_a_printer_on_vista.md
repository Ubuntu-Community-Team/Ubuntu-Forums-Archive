---
title: "[SOLVED] how do I connect to a printer on vista?"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by winkerbean on 2007-10-11
Hi,

I'm trying to access the printer on a Vista machine from Xubuntu.  The Vista machine has the server name "BO".  When I go into Applications->Settings->Printing on Xubuntu, I select "New Printer" and Enter the printer's name, "Samsung".  I select "Windows Printer via SAMBA", since the printer is marked as shared on Vista.  When I enter the smb address, smb://BO/Samsung, and click "Verify", I receive the message:
[INDENT]This print share is not accessible.[/INDENT]
Any thoughts?

---

### Post by cmnorton on 2007-10-11
If this printer is a network printer with its own IP address, you should be able to go through CUPS System->Administration->Printing and define a Jet-Direct printer on the Vista system.  You might also be able to do this if it is attached, and I am not as clear as to how to do that.

---

### Post by winkerbean on 2007-10-12
I got it!  I needed to add "WORKGROUP" to the beginning of my smb:// address.  Thanks.

---

