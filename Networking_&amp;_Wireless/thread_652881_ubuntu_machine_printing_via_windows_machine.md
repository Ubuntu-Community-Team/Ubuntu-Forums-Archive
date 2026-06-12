---
title: "ubuntu machine printing via windows machine"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by xodroolis on 2007-12-29
i have ubuntu gutsy installed in a machine
and windows xp in an other with a lexmark x75 on it
i have installed samba
i ve made the printer share ready through windows
i ve found the printer in ubuntu printer in these steps
1) Go to System -> Administration -> Printing
There choose the New Printer icon.
2) Select Network Printer and Windows Printer via Samba
i choosed the printer and after clicking on "verification" i get that the printer is accesible
BUT
when i choose to print a test page
i can see that ubuntu system is sending the page
and after a minute
windows get it and the window of lexmark pops up
and it says that the printing is started
i see the progress go from 0% to 100%
it says that the printing is finished
The printer in the whole process remains idle
P.S. the printer works just fine when i print through windows system.
any help?

---

### Post by buntu_hugenewbie11 on 2008-02-29
I have the same problem. 
Then when I check the printing error log I get the following errrors:

E [29/Feb/2008:18:31:37 +0000] CUPS-Delete-Printer: Unauthorized
E [29/Feb/2008:18:33:15 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [29/Feb/2008:18:33:15 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [29/Feb/2008:18:33:15 +0000] CUPS-Accept-Jobs: Unauthorized
E [29/Feb/2008:18:33:15 +0000] Resume-Printer: Unauthorized

Does somebody understand this??

---

### Post by xodroolis on 2008-02-29
i ve just noticed that in the properties window of the printer in ubuntu, in the status line of the general tab, it says
[COLOR="DarkRed"]ready: unable to start filter "rastertolxx74" - no such file or directory[/COLOR]
the same happens when i choose all-in-one and x73 drivers
does the same happens to you?

---

### Post by buntu_hugenewbie11 on 2008-02-29
No nothing at all like that.
Though I should make clear that I am trying to use a HP 4200 that is connected to the windows machine.
A coworker using debian and kde also seems to get the same error. So we are desperately trying to figure out how to print on this shared printer.

---

