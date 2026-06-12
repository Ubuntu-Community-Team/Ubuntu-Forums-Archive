---
title: "Printing Problems"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by tr6c on 2007-05-05
Hello friends, I have been trying to print to my HP PSC1210 printer through my windows xp pro computer and have been unable. My Linux version is feisty fawn. I am absolutely new to Linux so please be patient. The test pages actually show up in the print que on the xp machine the printer light flashes seems like it is going to print but does nothing. I have been working on this for some time now and really need some help. 
I have read some posts on this problem but do not understand half of what is being said. I tried to open the print.conf file but could not because it is owned by "cups" ?? I like this OS but seems needlessly difficult. 
Thank you all for your help.

---

### Post by zek725 on 2007-05-06
> **tr6c said:**
> Hello friends, I have been trying to print to my HP PSC1210 printer through my windows xp pro computer and have been unable. 
Are you printing remotely from Ubuntu to a printer that's running Windows?

Try this solution to delete the print jobs from WinXP: [http://searchwincomputing.techtarget.com/tip/0,289483,sid68_gci1039959,00.html](http://searchwincomputing.techtarget.com/tip/0,289483,sid68_gci1039959,00.html)
The ```
%Winroot%System32SpoolPrinters
``` will not work on WinXP so try this ```
%Systemroot%\System32\Spool\Printers
``` or just find the files in** Step 4.**

From your WinXP print server, Access the printer's properties and disable **bidirectional support**. Restart just to make sure.

additional link: [http://support.microsoft.com/kb/216221](http://support.microsoft.com/kb/216221)

---

### Post by tr6c on 2007-05-11
Thanks for your help! I turned off bidirectional support and now I can print fine.

---

