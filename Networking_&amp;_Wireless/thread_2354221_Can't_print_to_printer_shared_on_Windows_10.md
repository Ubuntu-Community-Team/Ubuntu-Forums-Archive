---
title: "Can't print to printer shared on Windows 10"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by peyre on 2017-02-28
My wife leaves her computer on 24/7, so I've always used it as our print server.  That worked great on her old Windows 7 machine, but since she moved to Windows 10 I haven't been able to print to it from my Xubuntu machines.  I'm running the latest Xubuntu 64-bit.  I have a Microsoft .LIVE.COM account that's set up on her machine as an administrator, so there shouldn't be any permissions issues, and I've made sure that account is set up with permissions on the printer.  In the Printers section of Xubuntu, I can connect to the printer and install it, but when I try to print something to it, it fails out.  Any suggestions?

---

### Post by pdc on 2017-02-28
this ubuntu guide [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) may be of use to check through

In addition, Ubuntu provide this printing debugging wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) ...........

---

### Post by peyre on 2017-02-28
Hm, didn't find too much there.  Though [https://technet.microsoft.com/en-us/library/ff633412(v=ws.10).aspx]("https://technet.microsoft.com/en-us/library/ff633412(v=ws.10).aspx") does suggest opening ports in the firewall.  I followed those instructions, but I'm still failing to print.  The Job attributes show:
job-printer-state-message: Filter failed
job-printer-state-reasons: ['hplip.plugin-error']

That's about the closest I can find to an error message.

---

### Post by peyre on 2017-02-28
I've also tried turning the firewall off altogether.  I still get:
Printer Error
There was a problem processing document 'SMB: File and printer sharing ports should be open' (job 8). 

Bullsh*t, the ports are open--the firewall's turned off!

---

