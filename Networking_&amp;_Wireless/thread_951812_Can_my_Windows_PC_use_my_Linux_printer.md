---
title: "Can my Windows PC use my Linux printer?"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Rocktman2 on 2008-10-18
I found this article on linux-mag.com. It's a few years old, but I was wondering if it's still viable?

Can my Windows PC use my Linux printer?

Yes, it’s very easy to share your Linux printer. Here’s what to do:

   1. Install TCP/IP print services on the PC. For example, under Windows XP, click “Start,” “Control Panel,” “Add or Remove Programs,” and choose “Add/Remove Windows Components.” Then check “Other Network File and Print Services,” click on “Next” and then “Finish.”

   2. Connect to the printer. Again, under Windows XP, click “Start,” “Printers and Faxes,” “Add a Printer,” and “Next.” Select “Local printer,” uncheck “Automatically detect,” then click “Next.” Create a new “LPR port,” and click “Next.” 

Enter the name or address of the Linux printer host and the name of the Linux printer, and click “OK.” Select the manufacturer and model of the printer, and click “Next”. Finally, set the printer’s name and decide if you want it to be the default printer for your computer. Click “Next.”

Try to print a test page. If nothing prints, click on “Troubleshoot” to diagnose the problem. If you cannot connect, check /etc/printcap to be sure that the printer is defined. If it is, then check /etc/lpd.perm, /etc/hosts.lpd, and /etc/lpd.conf. Also, make sure your PC’s name is in DNS or /etc/hosts.

---

