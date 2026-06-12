---
title: "I want windows back but windowsxp cd won't boot on my pc (ubuntu). what do i need to?"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by ennoel03 on 2010-07-31
[COLOR=Black][FONT=Microsoft Sans Serif][SIZE=4][/SIZE][/FONT][/COLOR][SIZE=2]hello guys, please help me. here is my situation: a friend gave me a suggestion to replace my os to ubuntu. and when i found out about the complications (commands, unfamiliarity, etc.) i decided to switch back to windows. But i cant. what should i do first? it seems that a pc with ubuntu can't boot my windows xp installer. 
also, can i use an iso image to install xp back again, though ubuntu is quite good (without complications). :(
[/SIZE]

---

### Post by arochester on 2010-07-31
Have you set your computer to boot from the CD-Rom first, before the Hard Drive?

---

### Post by ronnielsen1 on 2010-07-31
Any computer will boot from a cd as long as your bios is set to boot from cd / dvd

> **BIOS is not set to boot from CD or DVD drive**

 Some  computers are set to boot directly from the hard drive.  This should be  as simple as entering the BIOS, enable booting from the CD-ROM drive,  and making sure that the CD-ROM is before the hard drive in the boot  order. 
The  most common way to enter the BIOS is to press the DELETE key when the  computer is first booted(this seems to be becoming standard).  On other  systems it could be a different key, or combination of keys like ESC,  F1, F2, F10, F12, Ctrl-Esc, Alt-Esc, Ctrl-Alt-Esc, Ctrl-Alt-Enter, Ins  or even others.  You might have to press, press and hold, or press  multiple times. The best way to find out the details of that is to look  in the users manual or search the manufactures website. 
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Have you thought about posting your complications? There's a lot of people here that could help. Linux is a great system but it does have a learning curve. Looks are easily changed whether you want it to look like windows 7, Xp, mac or something entirely different,. Did I mention no viruses or defrag?

---

### Post by amsterdamharu on 2010-07-31
> can i use an iso image to install xp back again
[http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/](http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/)
Basically you can use unetbootin to copy the needed files to usb or hard disk and then boot of the usb or hard disk as if it was the cd.

If you choose to put the files on your hard disk than put them on a partition that is not going to be installed on because during the installation you need to format the partition that windows will be installed on and that will wipe out the files needed for installation.

As for not booting of CD, this could be a problem with bios settings or a CD that isn't burned correctly/damaged.

---

### Post by limestone on 2010-07-31
The problem is that Windows xp don't recognize your hard drive with ext so.. Boot a Ubuntu cd and format your drive to ntfs and then you can boot Windows...

---

### Post by ajgreeny on 2010-07-31
> **pont.andersson said:**
> The problem is that Windows xp don't recognize your hard drive with ext so.. Boot a Ubuntu cd and format your drive to ntfs and then you can boot Windows...
That does not stop the winXP CD from booting surely; it just stops the installation happening as windows isn't clever enough to see the disk if it has a linux file system on it.

This sounds like a BIOS wrong setting to me, which will need to be put right for the ubuntu Live CD to boot, as well as the winXP CD.

---

### Post by Paul820 on 2010-07-31
> **ajgreeny said:**
> That does not stop the winXP CD from booting surely; it just stops the installation happening as windows isn't clever enough to see the disk if it has a linux file system on it.

This sounds like a BIOS wrong setting to me, which will need to be put right for the ubuntu Live CD to boot, as well as the winXP CD.

It doesn't stop the CD from booting, you are right. Windows should boot up and go through the usual steps. It will see the linux partitions but it displays as unknown. All you have to do is delete the partitions and get back to a raw drive, format, and install windows.

---

### Post by limestone on 2010-07-31
I have the same problem on my other computer.. If I don't have any partition formated to ntfs/fat32 or somithing Widnows I can't boot the Windows install cd, The cd boots but after the text "press any key to start the cd" nothing happens. Then I format a partition to ntfs and the cd will boot. 

Just my experience, don't know how it works with vista or 7

---

### Post by Paul820 on 2010-07-31
If you still can't get it to boot, get either this [http://www.dban.org/download]("http://www.dban.org/download") or this [http://www.killdisk.com/downloadfree.htm]("http://www.killdisk.com/downloadfree.htm")
and burn either to disc and use them to wipe your drive. You don't have to wipe the whole lot, just leave it running for a minute or two and then cancel. As long as the boot sectors are wiped windows will think it's RAW.

---

### Post by ennoel03 on 2010-07-31
so if i use gparted to format a partition to ntfs, what then? do i still need to mount it? if yes, how?

---

### Post by ennoel03 on 2010-07-31
and oh, btw, i already tried changing the bios boot setting so that it will boot cd's and flashdrives first but still ubuntu gets in the way. its a different thing when i insert the ubuntu cd, it boots normally.

---

### Post by theozzlives on 2010-07-31
Have you tried to boot the Ubuntu Live CD? It could be a drive gone bad.

---

### Post by Megaptera on 2010-07-31
Have you tried this:

To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:
Put the Windows disc in the disc drive, and then start the computer.
Press a key when you are prompted.
Select a language, a time, a currency, a keyboard or an input method, and then click Next.
Click Repair your computer.
Click the operating system that you want to repair, and then click Next.
In the System Recovery Options dialog box, click Command Prompt.
Type Bootrec.exe, and then press ENTER.
Note To start the computer from the Windows CD/ DVD, the computer must be configured to start from the DVD drive. For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.

---

### Post by Sef on 2010-07-31
Another possibility is that you have a bad XP disk.  Try Ubuntu's Live CD (or another one) and see if it boots up into it.  If it does, then the XP disk is bad.  

If not, (and the CD/DVD is set to boot first), then I would suspect a bad CD/DVD drive.

---

### Post by bodhi.zazen on 2010-07-31
Thread closed.

I assume you have a bad CD and if that is the case you need to contact Microsoft, your desktop/laptop manufacturer, or purchase a new copy of windows.

Be warned, if you can not obtain a restore CD from the manufacturer, you most likely will need to find and install many hardware drivers manually.

Otherwise, these forums are for Ubuntu support and as the general question as to how to boot a CD has been answered, if you need additional assistance with windows please use a windows forums or contact Microsoft.

---

