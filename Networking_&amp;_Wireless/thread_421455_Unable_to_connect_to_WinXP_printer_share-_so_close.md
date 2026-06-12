---
title: "Unable to connect to WinXP printer share- so close"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by sb73542 on 2007-04-24
Hello,

I'm using Kubuntu 7.04 to try to connect to a Windows XP shared printer on a workgroup.  This should work fine and not require changes on the Windows machine because Mandriva 2007.1 was able to connect to this shared printer without any trouble.  I use the KDE Print Wizard, I pick "SMB Shared Printer (Windows)", I use Anonymous (also tried Guest) access, I "Scan" for networked printers, and the MSHOME workgroup appears and the machine name below that, but when I click on the machine, I get an error "NT_STATUS_ACCESS_DENIED".  And that's as far as I can get.  I should mention that I can use Konqueror on Kubuntu to browse to file shares on the same machine without any trouble, the WinXP machine isn't highly secured or anything.  Any suggestions?

Thanks a lot!

---

### Post by deadlines on 2007-04-24
You might try connecting via TCP/Socket, HP JetDirect, Raw Connection using the printer's IP (assuming this is a networked printer).  I've always had issues attempting to connect to my printers here at work by name, but this method always seems to do the trick.

---

