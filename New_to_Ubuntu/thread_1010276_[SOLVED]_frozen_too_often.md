---
title: "[SOLVED] frozen too often"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by andyubu on 2008-12-13
Hi there:

I just installed Ubuntu 8.04 LTS last week
Since then, I have to reinstall three times.

The computer is Shuttle xPC with 2 CPUs Pentium 4 and 2 G memory 
Windows XP Professional, HD 250 GB. Actually, this was the game machine of my son. Now, he's done with this machine and I use it to try ubuntu. 

I made the ISO cd of ubuntu 8.04 LTS and install from the CD
For the partition, I leave 80 G for Windows 
and install ubuntu on a 160 G partition with type "ext3 journal file" ("ext3" is exact, but the rest "journal file" might be something else, can't remember)
in each re-installation, I reformat this partition 
mount to / 

After installation, I received the message "No proprietary drivers are in use on this system" and 
the driver "ATI accelerated graphic driver" Status : Not in use 
I didn't enable this driver (for my use, there is no need to exploit all the capability of the card, I think the standard one is OK)

There is no more sound though all the sound & video programs run somoothly. I learn that it might due to some issues with the specific sound cards on Shuttle. I don't care either. I can listen to music and watch movie in XP 

Everything seems OK, except the computer freezes every one or two hours 

It happens even when the workload is very light 
(like when I open a folder, move a file from one folder to another)

Sometimes, it just freezes 

Sometimes, there is a static line on the screen 

When this happens, I use "Alt-PrtScr" R + E + I + S + U + B to reboot, so I don't think that I destroy anything 

When I go back to Windows, everything seems OK. 
 
I don't know if the problem is related to the sound and graphic  
cards. 

On this machine, I've installed 
apache2
mysql 
php5  
xdebug   
eclipse (PDT 1.03)
sun-java6-jdk

Any help as where to look at the problem, is very very welcome 

Regards

---

### Post by Michael.Godawski on 2008-12-13
You probably understand that it is hard to guess what might cause a pc freezing. The hardware combinations are countless, so are the compatibility issues.

All I can say is try the latest release of Ubuntu : intrepid 8.10.

I for myself had some crashes with hardy, but since intrepid not a single one, so it is definitely worth a try.

---

### Post by JKBurton on 2008-12-13
Yeah, random freeze-ups are a pain, no matter what operating system. As Michael said, there's little we can do for you beyond general recommendations. However the silver lining is that such freezes are not common anymore, and often changing versions like Michael recommended makes the problem vanish.

So I agree with his advice to download and install 8.10.  If you had already been running 8.10, I'd be recommending that you try 8.04 <grin>.

If you still get the freeze-ups, reinstall 8.10 again, this time without ANY optional packages until you know whether the base system works as/is. None of the tools you're installing should be causing it to freeze, but not adding any optional packages makes it easier to troubleshoot.

If you're still having trouble on a basic 8.10 install, post again and there will be some logfiles and such we can have you post.

Best of luck!

---

### Post by andyubu on 2008-12-14
Thank you Michael & JK 
I upgrade to Intrepid 
It works fine for 4 hours already 
Hope that it stays this way. 
Cheers
A.

---

