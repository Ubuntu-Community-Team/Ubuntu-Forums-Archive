---
title: "Ubuntu-11.04 will not boot from boot disk"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Musicmaker384 on 2011-05-20
My father is in a bad financial situation right now and can't afford to buy a new computer, so I thought I'd try to fix the one he has. The current operation system, Windows XP SP2, is just about dead, so I thought I'd try installing Ubuntu 11.04 to try and save the computer's life. I downloaded the ISO image and burned it to a disk using Windows Disc Image Burner. Nothing went wrong. I popped the CD into the disk drive, restarted, and got to the main menu (Try Ubuntu without installing, check disk for errors, Install Ubuntu, etc.) I selected 'Install Ubuntu'. Now here's my problem. After I selected the Install option, I waited. And waited. And waited.......and kept waiting...for about ten minutes. Now, I've never booted from a boot disk before and really don't know that much about computers, but I'm sure booting into an operating system from a disk shouldn't take that long. I had no choice but to manually power off the computer. All I got after selecting the option was a little blinking cursor at the top left-hand corner of the screen. Can someone tell me why this is happening, and how I can fix it? 

PS - The same thing happened when I tried using Wubi. I cleared the filesystem using chkdsk, and it still happened.

---

### Post by josephmills on 2011-05-20
Hi there did you check the md5sum number? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
also what is the hardware that is in this beast?
can you get it to run as a "live cd" and open the terminal and type in ```
lshw
``` thanks

---

### Post by Musicmaker384 on 2011-05-20
That's the problem. It won't run as a Live CD. It won't run anything for that matter. It'll give me the main menu, then I'll select an option, and then it won't do anything.

---

### Post by wildmanne39 on 2011-05-20
[QUOTE=Musicmaker384;10839619]My father is in a bad financial situation right now and can't afford to buy a new computer, so I thought I'd try to fix the one he has. The current operation system, Windows XP SP2, is just about dead, so I thought I'd try installing Ubuntu 11.04 to try and save the computer's life. I downloaded the ISO image and burned it to a disk using Windows Disc Image Burner. Nothing went wrong. I popped the CD into the disk drive, restarted, and got to the main menu (Try Ubuntu without installing, check disk for errors, Install Ubuntu, etc.) I selected 'Install Ubuntu'. Now here's my problem. After I selected the Install option, I waited. And waited. And waited.......and kept waiting...for about ten minutes. Now, I've never booted from a boot disk before and really don't know that much about computers, but I'm sure booting into an operating system from a disk shouldn't take that long. I had no choice but to manually power off the computer. All I got after selecting the option was a little blinking cursor at the top left-hand corner of the screen. Can someone tell me why this is happening, and how I can fix it? 

PS - The same thing happened when I tried using Wubi. I cleared the filesystem using chkdsk, and it still happened.[/QUO     Hi, you can install it from a usb drive.

---

