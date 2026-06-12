---
title: "XP Machines &quot;unbrowseable&quot;"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by mikeg113 on 2008-02-06
I am unable to browse to my XP machines from Ubuntu 7.10 machines. Although, I am able to access them by going to Places-->Connect to Server and typing in the IP address of the specific XP machine. This would be okay except that I have a shared printer on one of the XP machines I would like to access from Ubuntu. I have samba, smbfs and winbind installed. what am I missing?

---

### Post by patryk77 on 2008-02-07
This may help:

[quote=https://help.ubuntu.com/community/WindowsXPPrinter]Prior to setting up the printer in Ubuntu, ensure the printer is installed and shared on the Windows XP machine.

To add the printer in Ubuntu,

   1.

      Go to System -> Administration -> Printing and open the New Printer icon.
   2.

      Select Network Printer and Windows Printer (SMB)
         1.

            At Host, enter the computer name or IP-address of the Windows XP machine.
         2.

            At Printer, enter the share name of the printer.
         3.

            At Username, enter guest.
   3.

      Test it!

If it doesn't work, on the XP box:

   1.

      Go to Control panel -> Printers & faxes
   2.

      Right-click on Printer -> Properties -> Ports tab
   3.

      Uncheck "enable bidirectional support"
[/quote]

---

### Post by mikeg113 on 2008-02-07
Thanks, that's what I ended up doing. I just replaced the NETBIOS name with the IP address in the printer configuration and it worked. :)

---

