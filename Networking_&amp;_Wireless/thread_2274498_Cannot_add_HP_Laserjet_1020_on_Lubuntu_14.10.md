---
title: "Cannot add HP Laserjet 1020 on Lubuntu 14.10"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by Harold_Sumrall on 2015-04-20
[SIZE=3]I have checked other threads and mostly were about not being able to print, 
but I am not able to discover my printer which is connected to a windows xp computer via usb.

[IMG]http://i19.servimg.com/u/f19/12/97/34/48/networ10.jpg[/IMG]

I want to add that HP 1020 to my lubuntu 14.10 computer.
I achieved this easily with ubuntu 14.04 and linux mint by installing hplip
But Lubuntu is giving me a hard time since it wont discover the printer.

[IMG]http://i19.servimg.com/u/f19/12/97/34/48/proble10.jpg[/IMG]

What am I doing wrong, any help ? :confused:
[/SIZE]

---

### Post by Vladlenin5000 on 2015-04-21
Are you sure the IP address is correct? It should be the same as the printer server, i.e., your Windows XP where the printer is connected. If correct then checking whether or not the printer is shared in XP should be the next step.

---

### Post by Harold_Sumrall on 2015-04-24
I realized there is no  "**Add Windows Printer via Samba**"
option in the left side, maybe because lubuntu guys felt they should not include the smbclient package for some reason

So I installed "**smbclient**"

> sudo apt-get install smbclient

This just enables the "**Add Windows Printer via Samba**" option

[IMG]http://i19.servimg.com/u/f19/12/97/34/48/printe10.jpg[/IMG]


Now find your printer "**shared**" name on xp and type the path

[IMG]http://i19.servimg.com/u/f19/12/97/34/48/hp_sha10.jpg[/IMG]

Now Add the printer...


[IMG]http://i19.servimg.com/u/f19/12/97/34/48/finall10.jpg[/IMG]

---

