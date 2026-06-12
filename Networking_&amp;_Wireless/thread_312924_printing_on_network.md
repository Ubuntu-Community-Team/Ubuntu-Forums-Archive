---
title: "printing on network"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by spx3 on 2006-12-05
hello
i have ubuntu 6.10 on my laptop,
also i am connected to a hub where i have another
computer connected and that computer has attached
a printer.
but the problem is that the computer with the attached
printer has windows on it.
now my question is what can i read or do to be able
to print on the printer from my ubuntu laptop?

---

### Post by gerick on 2006-12-05
[Printing to Windows XP printer from Ubuntu]("https://help.ubuntu.com/community/WindowsXPPrinter")

> Prior to setting up the printer in Ubuntu, ensure the printer is installed and shared on the Windows XP machine. 

To add the printer in Ubuntu, Go to System -> Administration -> Printing and open the New Printer icon. Select Network Printer and Windows Printer (SMB) 

At Host, enter the computer name or IP-address of the Windows XP machine. 
At Printer, enter the share name of the printer. 
At Username, enter guest. 

Test it! 

If it doesn't work, on the XP box: 

Go to Control panel -> Printers & faxes 
Right-click on Printer -> Properties -> Ports tab 
Uncheck "enable bidirectional support"

Note: On my WinXP machine, I had disabled the Guest account, so I had to use an existing WinXP account when adding the network printer under KDE.

---

