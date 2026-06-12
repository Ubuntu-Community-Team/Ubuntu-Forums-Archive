---
title: "Can't install ubuntu"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by zigzagff17 on 2009-01-24
Ok, I formated my HD from a vista recovery disk, then replaced that disk with ubuntu disk, set up to boot from cd/dvd, and all i get is 
missing bootmgr, prest ctr alt del to reboot.

---

### Post by SunnyRabbiera on 2009-01-24
might be a bad burn.
What are your computer specs?

---

### Post by theozzlives on 2009-01-24
Sounds like a bad CD.

---

### Post by zigzagff17 on 2009-01-24
i put the dvd into my other computer and ubuntu popped up no problem.  I can access the dvd from the command prompt on the system i want to install it on as well.  how can i make sure its a good burn??? I used nero to burn it ... just selected everything to burn and burned it 

Z

---

### Post by zigzagff17 on 2009-01-24
i can even access the menu in dos/recovery, i typed wubi ... nothing really happened, and menu.exe brought up the menu, had the choice to either 'Demo and Full installation', Install inside windows', or Learn more.  Did i format my HD wrong ... all i did was 'format c:'

Z

---

### Post by zigzagff17 on 2009-01-24
something is happening .. used 'umenu.exe' and click install through windows ... got a menu and clicked install .. so now its
checking installation files and calculating checksums :D

---

### Post by ubhi on 2009-01-24
either this is ur cd/dvd problem or you can try one thing... just load ur cmos settings default & then make first boot device to cd/dvd & then try once...

---

### Post by zigzagff17 on 2009-01-24
what is error reading ubibcd ??
ok ... told me to remove dvd and reboot to finish installation ... guess what!
BOOTMGR is Missing
Press Ctrl Alt Del to restart
AGAIN!

I am offically really stumped now
I can access menu and stuff start install but don't want to boot properly.

---

### Post by zigzagff17 on 2009-01-24
ok i tried that ... boots from cd/dvd fist but then goes on to 
BOOTMGR is Missing
Press Ctrl Alt Del to restart

Z

---

### Post by carml on 2009-01-24
Maybe you didn't finish to install Windows Vista on your PC,because in my opinion looks like something went wrong with the MBR(Master Boot Record),where the OS are registered for booting. :confused:

---

### Post by zigzagff17 on 2009-01-24
how do i solve that ... i thought formatting the HD would have cleaned all that up.

---

### Post by zigzagff17 on 2009-01-24
Well i just discovered another problem ... with my HD, i went into the bios and did a HD self test ... got test #1-07 FAIL , apparently that isn't good!

Z

---

### Post by carml on 2009-01-24
Even more bas news for you,as you say.
Anyway a problem withthe MBR can be solved using Supergrub,an iso you have  to download,or if you want to do a dual boot,first install Windows,then Ubuntu.
Tell us what is your decision so we can help you at our best:)

---

### Post by zigzagff17 on 2009-01-24
Well i can't install anything ... i would like to install linux first then windows vista afterwards if possible.

---

### Post by zigzagff17 on 2009-01-24
ok i am running chkdsk on the C: drive, apparently i had to Unmount it ... its ntfs format.

Z

---

### Post by zigzagff17 on 2009-01-24
what is the supergrub all about ... where do i get it and how do i use it if necessary

---

### Post by carml on 2009-01-24
Supergrub is a software meant to correct problems with the list of OS installed:e.g. one has a PC with Windows and want to make a dual boot,if something goes wrong and he can't access Windows,he can use Supergrub to fix that problem. :)

---

### Post by carml on 2009-01-24
It's better install Windows first,then Ubuntu on a same hard disk,because(also personal experience) Windows overwrites the list of installed not MS OS.:KS

---

### Post by zigzagff17 on 2009-01-24
ok ... i jot supergrub burned to disk, i just have to wait for this chkdsk to finish ... then try to get window back on there somehow.

Z

---

