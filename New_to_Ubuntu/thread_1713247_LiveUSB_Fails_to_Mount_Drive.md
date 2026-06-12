---
title: "LiveUSB Fails to Mount Drive"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by mdclow on 2011-03-23
I am running Ubuntu 10.10 on a LiveUSB (4GB). It boots up fine and seems to be working fine. When I try to access my C drive I get an error message saying "can not mount C. Any advise?

---

### Post by yeats on 2011-03-23
Your C: drive in Windows is not called that in Ubuntu.  Go to the Places menu and see if you see an entry for your hard disk (it might look unfamiliar).  Double click it and see if that opens the Windows filesystem.

---

### Post by mdclow on 2011-03-24
[FONT=Times New Roman][SIZE=3]**Here are my Places:**[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Home folder[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Destktop[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Documents[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Music [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Pictures[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Video[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Downloads[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Computer[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=red]Preload (window C drive shows as "C: Preload")[/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]casper-rw[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]And here is the complete Error Message:[/FONT][/SIZE]

[LEFT][FONT=Times New Roman][SIZE=3]Error[/SIZE][/FONT][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]**Unable to mount Preload**[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]Error mounting: mount exited with exit code 16: Mount is[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]denied because the NTFS volume is already exclusively opened.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]The volume may be already mounted, or another software [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]may use it which [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]could be identified for example by the help of the 'fuser'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]command.[/FONT][/SIZE][/LEFT]

---

### Post by I2k4 on 2011-03-24
Interesting, because I've been using 4GB USB to try various verions, with no such problem.  From the message and the weird name "Preload" I get the idea some package you have installed with Ubuntu is accessing the hard drive and interfering with normal access via Nautilus or whatever.

I've made my share of goofs fooling around with USB installations, and the joy is that it's easy to dump it all and try again.  It might be worth either reinstalling clean, or even better trying a bare bones installation on a second USB (I've tested several Ubuntu versions pretty successfully on a 2GB USB drive with 1GB each of OS space and Persistence/Casper.)

---

### Post by mdclow on 2011-03-25
As nothing, readily apparent, seems to be wrong your suggestion to re-install is an excellent idea.  I did that last night and I can now access my C drive (Preload).  After doing the re-insall (setting aside 2 of 4GB, forgot the term) I immediately shut down Ubuntu, re-started to make sure I could still access C.  Yes, C was still accessibe.  I then began adding some programs and shut down after each install to make sure I could still access C drive.
 
I would consider this posted completed.  Thanks for your guidance.

---

### Post by I2k4 on 2011-03-25
Glad it works.  You should mark your thread "solved" in the title.

---

### Post by mdclow on 2011-03-26
Thanks for your help

---

