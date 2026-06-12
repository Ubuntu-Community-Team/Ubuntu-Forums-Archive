---
title: "Install problem on LiveCD"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by zortec on 2009-05-31
I changed the boot order to my CD/RW drive in the bios and boot up to the main screen where you have several choices.  When I try to "Install Ubuntu", nothing happens. Also it does not allow me to "Check CD for defects" as the none of the options appear to be doing anything when I hit the enter key.  

After a minute or two, I am thrown into a terminal called Busybox.  When I attempt to exit, there is a kernel panic and I have to to do a "hard reset" to get out.  

Any help with this would be greatly appreciated.

---

### Post by Bradtek on 2009-05-31
First thing I would do is burn another CD and make sure you burn it as slow
as your burning software will allow

---

### Post by zortec on 2009-05-31
I will try burning a CD at 4x and using a different media.  The last one was at 10x, not sure if that is the problem though.  How does Linux deal with SATA drives?  I ask since that is the main disk I will be installing Ubuntu on.

Thanks for the suggestion.

---

### Post by philinux on 2009-05-31
10x is too fast thats the problem. There is a lot of compressed files in the iso. 4x is the recommended speed. You just burned a coaster. 

I always use cd rw's to avoid this.

---

### Post by mcduck on 2009-05-31
It's also a good idea to check the file you downloaded before even burning it into a disk (unless you downloaded it from a torrent, as bittorrent will check the file automatically) .

---

### Post by zortec on 2009-05-31
I am not having any luck.  The CD was burned at 4x and I downloaded it from United States Ubuntu cs.wisc.edu.  I selected the"Install Ubuntu" and was once again put in a terminal.  I really do not like having to "hard reset" the machine but that is the only solution I found to abort.  This is the errors when using the "exit" command:

cp: cannot create /root/var/log
Target filesystem doesn't have /sbin/init
No int found.  Try passing initbootarg

The only option that is working on the LiveCD is "Boot from hard disk" which takes me back into Windows.  

Is it possible that SATA is not recognized? That could be a place to start.

This is the first time I have ran into an issue with a LiveCD on Ubuntu and would like to get this resolved.  I want to get a working system.



Thanks

---

### Post by bacardiandwatermelon on 2009-05-31
If you have a spare flash drive you could chuck the ubuntu on there?

---

### Post by zortec on 2009-05-31
> If you have a spare flash drive you could chuck the ubuntu on there? 	

Thanks for the suggestion, but I do not have a spare flash drive.  I am trying the alternate installer.

---

### Post by NHArticleTen on 2009-05-31
Hi,

We would love to see you overcome your present difficulties, however after reviewing all your previous threads and posts we still don't know the make, model, specifications, and presently installed operating system(s) on the machine in question.

Through reading your past threads and posts I am led to believe that you should make the proper selection in your BIOS to operate the machine in 32 bit mode and perhaps see what that does.

You might also try another small distro like Puppy Linux or Damn Small Linux to see what happens with those.  They both do rather well at "discovering" hardware and firmware settings given that their creators wanted to produce a distro that would "just run" on a wide variety of machines.

---

### Post by zortec on 2009-05-31
> We would love to see you overcome your present difficulties, however after reviewing all your previous threads and posts we still don't know the make, model, specifications, and presently installed operating system(s) on the machine in question.

I am trying to install Ubuntu on an Intel Dual Core E2200 2.2 Ghz system.  It has 3GB RAM and currently has Windows XP.  I have one SATA drive that is 300GB.  I set aside 100GB for the Windows partition and created a new partition of 30GB for Ubuntu. 

> Through reading your past threads and posts I am led to believe that you should make the proper selection in your BIOS to operate the machine in 32 bit mode and perhaps see what that does.

I will check my BIOS to see if it is running in 32 bit.  The default settings have not been changed except for the boot order and I enabled USB support.

---

### Post by zortec on 2009-05-31
Now the alternate installer does not see the cdrom.  I really did not think I would have this much trouble.  

Are there any installation methods that work?  Just as I get past one step, there is another issue.  This is really painful.

---

### Post by zortec on 2009-05-31
*bump* I have not successfully installed Ubuntu and my SATA drive is not recognized.  Is there not anyone else with this issue? I cannot possibly be the only person with a SATA drive that Ubuntu does not pick up.

I am really at a loss for what is going on here.  I have spent my whole day trying to install Ubuntu.

---

### Post by bacardiandwatermelon on 2009-05-31
Ummm linux should be fine with sata drives, it deals with my scsi drives fine. I think that there might be a issue with the cd media. Do you burn alot of cds with that brand? I've had issues in the past with my cdrom reading certain cheap cds when I was trying to install xp back in the day...

---

