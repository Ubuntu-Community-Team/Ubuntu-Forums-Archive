---
title: "Lost Grub"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by SuchetBargoti on 2011-07-21
I re-formatted my linux partition, because I wanted to re-install the system. To do this I went into windows 7 disk management and deleted the drive. I also download EasyBCD software which allowed my to get the computer to boot straight to windows. 
I then went through the process of installing ubuntu 11.04 and then went successfully. But now when I restart the computer, I no longer see the grub menu and it boots straight away into windows. 
How do I get back the option of choosing to boot into Ubuntu or Windows?

---

### Post by SuchetBargoti on 2011-07-21
UPDATE: 
I tried to go on EasyBCD on Windows 7 and added linux drive as an option. Now when I restart I have the option of picking Windows or Linux (but not in that purple menu I was used to, and not other options such as start in recovery mode).

---

### Post by jjex22 on 2011-07-21
Hi there, as long as you didnt ask it not to ubuntu has installed grub 2 on it's partition, easy bcd is just before it in the boot order. go into easy bcd -> edit boot menu and by right clicking remove anything other than the windows entry.
 
Next go to 'Add new entry' -> Linux/bsd and use 

Type Grub2
Name Ubuntu 11.04 (or whatever you like)
Device *the place where you installed it probably partition 2 or 3, it will say that it's a linux partition 
 
 
For future referance you don't need to use the windows CD for partitioning, run the ubuntu cd as a live cd by clicking try now and then run Gparted. This is amuch better utility and will let you set up your drive how you want it before installing. You can ofcourse also do this from the ubuntu installer, but the full Gparted program is more full featured I find. 
 
(if using Gparted from a live CD and you find you cant move resize or delete a swap or extended partition, right click on your swap partition and "swap off")

---

### Post by jjex22 on 2011-07-21
Sorry i forgot you get to the recovery mode either by not shutting your windows system down properly (not recommended) or by pressing F8 hope that helps! 
 
once you are in ubuntu sudo update grub should make grub your default bootloader again, if you want it to be

---

