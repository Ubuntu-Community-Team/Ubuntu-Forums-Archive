---
title: "Network printing not working"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Tribis on 2008-07-02
I'm trying to install a network printer that is attached to a Vista machine, the Windows machine works perfectly. The problem is the Ubuntu 8.04 machine.

I can find the network, find the printer, choose the drivers, set the naming, and thats it. Once I try to go past this point it asks for a "localhost password". This password is not my root or actual user password.

I am using 'System > Administration > Printing' and do not want to have to go through CUPS. I have tried the following command as both a user and as root and receive the following.

```
adduser cupsys shadow
```
```
adduser: The user `cupsys' does not exist.
```

BTW I have used CUPS and its the same deal except that it asks for both username and password; root with its password works and I am able to add the printer but nothing prints.

---

### Post by superprash2003 on 2008-07-02
you could try doing this via samba.. editing the smb.conf file etc.. have you tried that?

---

### Post by Tribis on 2008-07-02
I logged in as root and set it so that my user account could manage printers. 

I was able to add the printer using 'System > Administration > Printing' without any password pop-ups :D. But now that I actually have the printer installed its not actually printing. Trying to print a test page does nothing, and Ubuntu just sits there saying "processing" in the print queue.

The printer is an HP LaserJet 3390 connected to a Vista machine; the printer is properly shared as I am able to use it in a Windows XP machine, a Vista laptop, and an OS X laptop.

---

### Post by Tribis on 2008-07-02
> **Tribis said:**
> I logged in as root and set it so that my user account could manage printers. 

I was able to add the printer using 'System > Administration > Printing' without any password pop-ups :D. But now that I actually have the printer installed its not actually printing. Trying to print a test page does nothing, and Ubuntu just sits there saying "processing" in the print queue.

The printer is an HP LaserJet 3390 connected to a Vista machine; the printer is properly shared as I am able to use it in a Windows XP machine, a Vista laptop, and an OS X laptop.

I was able to solve this issue using this method: [http://ubuntuforums.org/showpost.php?p=5188287&postcount=13](http://ubuntuforums.org/showpost.php?p=5188287&postcount=13)

Someone explain to me why I can't use the traditional SAMBA address and instead had to replace the domain and PC names with the computers IP address for it to work properly.

---

