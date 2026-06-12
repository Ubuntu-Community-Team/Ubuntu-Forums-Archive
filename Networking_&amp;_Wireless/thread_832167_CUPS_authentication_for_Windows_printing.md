---
title: "CUPS authentication for Windows printing"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by cbraxton on 2008-06-17
I'm trying to set up Ubuntu 8.04 (Server edition) to share printers with Windows via the CUPS interface. The cupsd.conf file has been modified to accept incoming connections from the entire network ("Listen *:631"), and printers can be listed from the local Windows systems using the URL:

  [http://server-name:631/printers/printer-name](http://server-name:631/printers/printer-name)

However, when adding the printer to a Windows system using the same URL, it initially finds the printer, but then pops up a dialog box asking for authentication. Three "Security Options" are given; "Use Anonymous Account," "Automatically Use the Windows Logon Name," and "Use the Specified User Account."

None of these options work, access is always denied to the printer no matter what user account is used. Have tried Samba accounts, Linux accounts, and also tried using the "lppasswd" command to add a specific CUPS account. No soap.

In searching for info on this, I have additionally added a "cupsys" user account that belongs to the "shadow" group, but that didn't make any difference either. 

Anyone know how to get this working?

---

