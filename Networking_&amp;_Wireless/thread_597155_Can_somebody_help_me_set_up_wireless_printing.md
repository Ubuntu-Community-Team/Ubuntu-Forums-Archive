---
title: "Can somebody help me set up wireless printing?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by aeonwings on 2007-10-30
I have 2 computers, 1 Ubuntu, the other Windows Vista. The printer is attached to a router which connects to a Vista desktop. I'd like to set up my Ubuntu Laptop to print wireless. How can I set this up? I've been trying with no luck. I've installed CUPS already, but can't seemed to set it up. My config:

Name of desktop: DESKTOP-PC (IP: 192.168.1.109)
Printer: HP Photosmart 7960
Router: Linksys (DHCP)

Don't know what else I need to provide, let me know what else I need to set it up. Thanks in Advance.



UPDATE: No freaking way! it's so simple. after minutes of asking for help, I try to do it one more time and it works!! if anyone is wondering this is how I did it.
Note: must have Samba and CUPS installed and configured.
go to SYSTEM>ADMINISTRATION>PRINTING
add new printer....select "network printer" pick Windows Printer (SMB)
it's going to ask for a password ( I didn't enter in any) hit "connect"
click on arrow to the right of box and you should see your Windows computer that your printer is attached to. Do the same for "printer" below. Everything should come up automatically.
If not, then you didn't configure Samba right. If that's the case go here > [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by jonathanmotes on 2007-11-07
Congrats! Don't forget to mark this solved (using the thread tools dropdown)!

---

