---
title: "Network Printer Troubleshooting"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by donkeyjaws on 2007-03-04
Please help me to get my network printer working.  


I use Ubuntu Dapper on a Windows network. The printer is a Toshiba eStudio350.  It has a built in print server/file server.  I have tried using the CUPS web interface  ([http://localhost:631](http://localhost:631)) and the "system-administration-printing-add printer" method. The CUPS administration thing detects my printer and seems to install just fine.  Same thing with the other method,  I choose Network Printer-Windows Printer(SMB) Then It prompts me for a password. This also seems to work fine until I actually try to print something.  I got my driver from the Toshiba website I used their ppd file even though it is for the estudio450.  No matter how I try to configure the printer, whenever I press print, my machine acts like everyhing is fine, (I see the little printer icon in the tray)  it just never prints.  Below is the var/log/cups/error.log.


Here are my questions:

How can I be sure that my driver is correct, and installed properly?
Are there other logs I can look at?
Am I looking at the right logs?








I [04/Mar/2007:12:24:40 -0800] Started "/usr/lib/cups/daemon/cups-driverd" (pid=9881)
I [04/Mar/2007:12:24:52 -0800] Started "/usr/lib/cups/daemon/cups-deviced" (pid=9888)
I [04/Mar/2007:12:25:13 -0800] Adding start banner page "none" to job 116.
I [04/Mar/2007:12:25:13 -0800] Adding end banner page "none" to job 116.
I [04/Mar/2007:12:25:13 -0800] Job 116 queued on "e-ST450-452-Series-PS-1" by "Tony".
I [04/Mar/2007:12:25:13 -0800] Started filter /usr/lib/cups/filter/pstops (PID 9917) for job 116.
I [04/Mar/2007:12:25:13 -0800] Started backend /usr/lib/cups/backend/smb (PID 9918) for job 116.
E [04/Mar/2007:12:25:15 -0800] [Job 116] No %%BoundingBox: comment in header!

---

