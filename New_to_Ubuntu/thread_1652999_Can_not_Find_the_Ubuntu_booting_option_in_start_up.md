---
title: "Can not Find the Ubuntu booting option in start up"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by adhi007 on 2010-12-26
Hi my PC have win7 OS. Now i installed ubuntu 10.10 as another OS.
Now i can not find the ubuntu booting option in start up.
Help me guys...
Thanks in Advance

---

### Post by karthick87 on 2010-12-26
Welcome to ubuntuforums :)

Can you boot into ubuntu??Do you mean your GRUB menu is missing??

---

### Post by adhi007 on 2010-12-26
thanks karthik..
i didn't get ur qun?
now when i start the the pc..it take to win7 automatically.
it'll not ask which os u wish to start..
this is the problem i have..

---

### Post by karthick87 on 2010-12-26
Boot from a live ubuntu cd and post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code (#) tags..

---

### Post by adhi007 on 2010-12-26
i think it need internet connection...
at present i need help for offline pc..

---

### Post by karthick87 on 2010-12-26
Did you installed ubuntu inside windows using wubi??

---

### Post by adhi007 on 2010-12-26
No...i did extra partion of 20gb..and i installed there..

---

### Post by tushar maroo on 2010-12-26
i think ubuntu installation was faied or there is some problem..........just check with live cd that ubuntu you have install in 20 gb partition is there or not.......and if not there then install it again and if it is there then go to trial mode of ubuntu via live cd and open terminal and try
**GUI**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD 
[*]Go through all the process until you reach "[!!!] Disk Partition" 
[*]Select Manual Partition 
[*]Mount your appropriate linux partions  / /boot swap .....  
[*]**DO NOT FORMAT THEM.** 
[*]Finish the manual partition 
[*]Say "Yes" when it asks you to save the changes 
[*]It will give you errors saying that "the system couldn't install ....." after that 
[*]Ignore them, keep select "continue" until you get back to the Ubuntu installation menu 
[*]Jump to "Install Grub ...." 
[*]Once it is finished, just restart your computer 
[/LIST]
 
**Command line**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD 
[*]Open a terminal window or switch to a tty. 
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary. 
[*]Type "grub" 
[*]Type  "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use  whatever your computer spits out for the following lines. 
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu. 
[*]Type  "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever  your hard disk + partition nr is, to install GRUB to a partition. 
[*]Quit grub by typing "quit". 
[*]Reboot and remove the bootable CD. :popcorn:
[/LIST]

---

### Post by adhi007 on 2010-12-26
> **tushar maroo said:**
> i think ubuntu installation was faied or there is some problem..........just check with live cd that ubuntu you have install in 20 gb partition is there or not.......and if not there then install it again and if it is there then go to trial mode of ubuntu via live cd and open terminal and try
**GUI**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD 
[*]Go through all the process until you reach "[!!!] Disk Partition" 
[*]Select Manual Partition 
[*]Mount your appropriate linux partions  / /boot swap .....  
[*]**DO NOT FORMAT THEM.** 
[*]Finish the manual partition 
[*]Say "Yes" when it asks you to save the changes 
[*]It will give you errors saying that "the system couldn't install ....." after that 
[*]Ignore them, keep select "continue" until you get back to the Ubuntu installation menu 
[*]Jump to "Install Grub ...." 
[*]Once it is finished, just restart your computer 
[/LIST]
 
**Command line**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD 
[*]Open a terminal window or switch to a tty. 
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary. 
[*]Type "grub" 
[*]Type  "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use  whatever your computer spits out for the following lines. 
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu. 
[*]Type  "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever  your hard disk + partition nr is, to install GRUB to a partition. 
[*]Quit grub by typing "quit". 
[*]Reboot and remove the bootable CD. :popcorn:
[/LIST]
Thanks __thushar...I'll try..
am sure installation was sucessed..and all the ubuntu  folders are there in that partion..i checked yesterday itself..now i'll do the remaining steps..

---

