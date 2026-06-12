---
title: "[SOLVED] Printing wireless to printer attached to Windows XP desktop"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Wally_dog on 2008-10-16
Well, as the title says, I would like some help printing wirelessly to a printer that is attached to a Windows XP desktop. Before I switched distros (previously used PCLinuxOS2008 GNOME), I was able to print to the printer by using PCLinuxOS' PrinterDrak installer. This made the install ridiculously easy. But now since I've switched to Ubuntu, it's not that easy, unfortunately. I am welcome to trying anything to print to it, but modifying the connection the printer has to the desktop is not an option (dad will be mad at me). So, a diagram of how I need to do this is here:


[Desktop]<--->[Printer]--->[COLOR="White"]w i r e l e s s[/COLOR]<---[Laptop]

I hope that makes sense... basically the printer is wired to the desktop and the laptop needs to be able to print wirelessly to the printer attached to the desktop. 

Desktop is running Windows XP Home Edition
Laptop is running Ubuntu 8.04 (fully updated as of Oct 16, 2008)

If there are any packages I can download to make this setup easy, please feel free to say so :) 

Thanks!

-Wally

---

### Post by Wally_dog on 2008-10-17
bump... anyone have an answer for me???

---

### Post by superprash2003 on 2008-10-17
hope this helps [http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by Wally_dog on 2008-10-17
Thanks, I'll see if this helps!

-Wally

---

### Post by Wally_dog on 2008-10-17
THANK YOU SOOOOOOO MUCH!!!! I can print now!!! I also used some basics that I learned from your guide to connect my dad's Windows laptop to our desktop's printer, so he's grateful to you too :) Thanks a lot!!!

---

### Post by cariboo on 2008-10-17
First off how are your computers networked? Do you use a router or are they connected via wirless.

If you are connected with a router, it is fairly simple, in Windows right click on the printer and select sharing, give the printer a name and your done. On your Ubuntu computer go to System-->Administration-->Printing and select windows printer via smb and just fill in what you need as you click forward.

The one thing that might be a problem is if the printer is not well supported in Linux, go here:

[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)

to check if your printer is supported.

Jim

---

