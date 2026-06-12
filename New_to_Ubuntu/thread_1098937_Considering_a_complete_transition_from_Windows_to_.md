---
title: "Considering a complete transition from Windows to Ubuntu."
date: 2009-03-17
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-03-17
Hello everyone,

A few months back I partitioned my HDD and put Ubuntu 8.10 with Vista on ony laptop. I eventually removed it, because I could not for the life of me get the wireless working. When I took off the Ubuntu partition, the computer **** the bed, and I ended up recovering it. I would prefer it if this did not happen this time

I have recently figured out HOW to get it working, but I don't know if I want to do a complete transition. 

Today I tried to re-partition the HDD, but it only would allow 7 GB of space. That is a problem. I would like to go back to Linux, but I just don't know how without going completely from windows into Ubuntu. 


Also, the laptop is a Compaq Presario CQ50. It has 2 gigs of ram, a 160 GB HDD, and it is currently running Vista.


Is there a way for me to partition the HDD and have more then 7 GB of space?

---

### Post by bobmatino17 on 2009-03-17
select the "manual partitioning" option. it allows you to set what file system you want, what you want the new partition(s)(or old) size to be and all that good stuff.

---

### Post by HermanAB on 2009-03-17
First defrag the HDD in Windows, to ensure that all data is at the 'front' of the disk, then you can partition it manually.

Cheers,

Herman

---

### Post by .:Justus:. on 2009-03-17
> **RAZRBAKK said:**
> Hello everyone,

A few months back I partitioned my HDD and put Ubuntu 8.10 with Vista on ony laptop. I eventually removed it, because I could not for the life of me get the wireless working. When I took off the Ubuntu partition, the computer **** the bed, and I ended up recovering it. I would prefer it if this did not happen this time

I have recently figured out HOW to get it working, but I don't know if I want to do a complete transition. 

Today I tried to re-partition the HDD, but it only would allow 7 GB of space. That is a problem. I would like to go back to Linux, but I just don't know how without going completely from windows into Ubuntu. 


Also, the laptop is a Compaq Presario CQ50. It has 2 gigs of ram, a 160 GB HDD, and it is currently running Vista.


Is there a way for me to partition the HDD and have more then 7 GB of space?

You can manually set the partition size when you install it, if 7GB is the max, then that would mean you only have 7GB available , so i´d recommend you free up some hd space before partitioning , that way you´ll have more space for ubuntu.

---

### Post by RAZRBAKK on 2009-03-17
> **.:Justus:. said:**
> You can manually set the partition size when you install it, if 7GB is the max, then that would mean you only have 7GB available , so i´d recommend you free up some hd space before partitioning , that way you´ll have more space for ubuntu.

It tells me that I have 45% of the HDD free. Its Thats not 7 GB.

How do I defrag the HDD?

---

### Post by jaqrah on 2009-03-17
Start Menu>My Computer> Right click on C drive Properties>Tools>Defragment

---

### Post by .:Justus:. on 2009-03-17
> **RAZRBAKK said:**
> It tells me that I have 45% of the HDD free. Its Thats not 7 GB.

How do I defrag the HDD?

Either this:
> **jaqrah said:**
> Start Menu>My Computer> Right click on C drive Properties>Tools>Defragment

Or get Defraggler : [http://www.defraggler.com/](http://www.defraggler.com/)

When you are in the partition menu, one part of the HDD bar should be labeled windows vista and the other should be ubuntu.
Is there anything else on the bar? any gray spaces? are you able to increase the size of the ubuntu partition at all?

---

### Post by RAZRBAKK on 2009-03-17
It's currently defragging with the windows defragment software.

Hopefully this works.

Thanks guys!

I'll update as soon as it is done.

---

### Post by RAZRBAKK on 2009-03-17
> When you are in the partition menu, one part of the HDD bar should be labeled windows vista and the other should be ubuntu.
Is there anything else on the bar? any gray spaces? are you able to increase the size of the ubuntu partition at all?

At the moment Ubuntu is not installed. I'm going to create a partition for ubuntu once the defragment is done... hopefully.

Also, how do I go about a manual partition?

---

### Post by freesitebuilder on 2009-03-17
I use GPartEd - you can download a liveCD, boot from it to partition your drive manually. Someone (here on the forum, I think) recommended that I defrag at least twice to make sure all my Windows data was in one part of the disk. This has help on partitioning, installing and also on the benefits of a separate home partition:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by RAZRBAKK on 2009-03-17
How do you people feel about ubuntu in a virtual box?

---

### Post by RAZRBAKK on 2009-03-17
Another question: 

If I decide I do not want Ubuntu anymore, will I be able to remove it without the GRUB menu being affected like last time? Because last time I couldn't boot at all.

---

### Post by PukingPenguin on 2009-03-17
> **RAZRBAKK said:**
> How do you people feel about ubuntu in a virtual box?

To quote James Brown:
"I feel good!"

The only consideration with a virtual machine is the host should always be MORE reliable than the guest.
 This disqualifies Windows in all cases.


:popcorn:

---

### Post by PukingPenguin on 2009-03-17
> **RAZRBAKK said:**
> Another question: 

If I decide I do not want Ubuntu anymore, will I be able to remove it without the GRUB menu being affected like last time? Because last time I couldn't boot at all.

If you "uninstall" GRUB you will need to reinstall your (shudder) Windows boot loader.


How do you "feel" about Windows in a virtual machine?


;)

---

### Post by RAZRBAKK on 2009-03-17
> **PukingPenguin said:**
> If you "uninstall" GRUB you will need to reinstall your (shudder) Windows boot loader.


How do you "feel" about Windows in a virtual machine?


;)
I was thinking about Ubuntu in windows. As much as I am not a fan of windows, I don't know anything about ubuntu...

Defragment free'd up an extra 6 gigs of space. Still not enough.

I'm gonna try a manual partition.

---

### Post by MotleyPhule on 2009-03-17
[The GParted Live Cd]("http://gparted.sourceforge.net/livecd.php"), as mentioned, is useful for making a dual boot install; it's also useful if you need to uninstall Ubuntu at some point.  You can then just delete the Ubuntu partition using GParted and overwrite GRUB using your Vista CD as detailed here [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html").

Sounds like you have plenty of free space.  I don't know why you're having trouble accessing it unless it's hugely fragmented.  Sometimes a second defrag helps clear things up even more.  Getting rid of unnecessary programs followed by a defrag would help too.

---

### Post by RAZRBAKK on 2009-03-17
> **MotleyPhule said:**
> [The GParted Live Cd]("http://gparted.sourceforge.net/livecd.php"), as mentioned, is useful for making a dual boot install; it's also useful if you need to uninstall Ubuntu at some point.  You can then just delete the Ubuntu partition using GParted and overwrite GRUB using your Vista CD as detailed here [http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html").

Sounds like you have plenty of free space.  I don't know why you're having trouble accessing it unless it's hugely fragmented.  Sometimes a second defrag helps clear things up even more.  Getting rid of unnecessary programs followed by a defrag would help too.

I've done 3 defrags already, I'm not quite sure what the problem is...

---

### Post by Skol312000 on 2009-03-17
Woah woah, im gonna get rid ofwindows too, what is GrUD?  How can i avoid delteting it?  Unless its ok to delete.. I do t need anything from my hard drive...  Do i also need to defrag?  Its a new computer and theres nothing on it other then 20 songs and a movie and its in Ubuntu...?!?  Please help

---

### Post by RAZRBAKK on 2009-03-17
> **Skol312000 said:**
> Woah woah, im gonna get rid ofwindows too, what is GrUD?  How can i avoid delteting it?  Unless its ok to delete.. I do t need anything from my hard drive...  Do i also need to defrag?  Its a new computer and theres nothing on it other then 20 songs and a movie and its in Ubuntu...?!?  Please help
You should be good.

The GRUB menu is basically what you choose to run at the start. Like when you choose Windows or Ubuntu. I can't really help you with that stuff, I don' know too much about it.

I'm installing Ubuntu on a virtual box right now.

---

### Post by malditonuke on 2009-03-17
> **Skol312000 said:**
> I do t need anything from my hard drive...

My advice is that you check and double check your drive to make sure you don't delete anything you'll want later.  SOOO many times I thought that I had everything I needed, then... that file! ****, I forgot about it!

Also, if you have Windows on the machine already, and if you have plenty of room on the disk, then why bother erasing it?  It may come in handy just to have it...just in case.  RL example: I was having trouble with one of my USB flash cards in Ubuntu, and I needed to take care of it in 5 minutes.  I couldn't find a solution to my problem online, so I booted to Windows and fixed it there like I knew how.  My Windows partition only takes up a few gigs of space, and I have 250, so it doesn't hurt to leave it there...just in case. ;)

---

### Post by avtolle on 2009-03-17
Something to keep in mind; if the user has Vista, use the Vista tool to resize its partition. While some have used Gparted and it has worked, there are threads on this forum and elsewhere about corruption of the Vista installation when Gparted (or another partition manager) was used to resize the Vista partition.

---

### Post by Skol312000 on 2009-03-17
Wooooooooooooooow.    Im extremely confused right now!!!


I want to delete all OSs off my laptop (Vista and Ubuntu)!!!
after that i want to install only Ubuntu 64 bit!!!!

I do not want to delete Grub. I just want to do this and ot seems that every answer i get is different from the last!!




How do i do this as easy and safest way?  Please help?

Do i need to defrag before anything?  Please help!!!

---

### Post by Botbob89 on 2009-03-17
What you are wanting to do is pretty complicated to say the least, and I would just advise you know EXACTLY what you are doing before completely deleting everything like that!

If you really aren't sure, best thing to do is to get someone who can do it

---

### Post by Ericyzfr1 on 2009-03-17
If you have any doubt about what you want to accomplish, just make a back-up of your Vista that you can reinstall later if something goes wrong.

---

### Post by Botbob89 on 2009-03-17
Backups are a main area that needs to be addressed, but when it comes to what you are suggesting, you have to really make sure you know what you are doing, because all of a sudden you'll realise you've done irreparable damage to your computer, which I'm sure you DON'T want

---

### Post by Skol312000 on 2009-03-17
Omg. Why is this so hard?  I just want to wipe the OSs and then put i. 64 bit.... How can i do t? Is it really thT hard?  Is sure was easy to install

---

### Post by RAZRBAKK on 2009-03-17
> **Skol312000 said:**
> Omg. Why is this so hard?  I just want to wipe the OSs and then put i. 64 bit.... How can i do t? Is it really thT hard?  Is sure was easy to install

You will still want to back everything up. You don't want to end up with a computer with no operating system that won't boot up.

Now quit hijacking my thread!


What are the differences between Ubuntu and Xubuntu?

---

### Post by Skol312000 on 2009-03-17
Lol my bad,  i do have a restore cd with Vista on it... The safest way i can think of doing what i want is to put in live cd and when i choose what drivees installation partitions is to choose all of drives and all disk space....

Diff between kubuntu and ubuntu is desktop environment and other stuff u can search

---

### Post by Botbob89 on 2009-03-17
> **RAZRBAKK said:**
> You will still want to back everything up. You don't want to end up with a computer with no operating system that won't boot up.

Now quit hijacking my thread!


What are the differences between Ubuntu and Xubuntu?

There's quite a few differences to be quite honest...but the basics are in how they are organised, and more basic aesthetic differences, such as the desktop being different. The basic architecture of Ubuntu and Xubuntu is pretty much the same though.

---

### Post by malditonuke on 2009-03-17
> **Skol312000 said:**
> Omg. Why is this so hard?  I just want to wipe the OSs and then put i. 64 bit.... How can i do t? Is it really thT hard?  Is sure was easy to install

If you *really* want to just wipe and start with a fresh 64-bit Ubuntu, then boot with the Live CD, click install.  Let the guided partition use the whole drive for Ubuntu, or select manual partition to customize it how you like.

I started with 32-bit Ubuntu (because 32-bit was what I was used to) and switched to 64-bit later.  I used the Ubuntu 8.10 Live CD to manually partition the drive, erased the old Ubuntu partition and created a new Ubuntu partition.  The installer installed the 64-bit version in that partition and updated GRUB itself.

If you don't care about the data on the drive, then don't be afraid.  Just do it.  


P.S.  Have another computer (with internet access) on standby in case you need to ask for help.

---

### Post by RAZRBAKK on 2009-03-17
> **Botbob89 said:**
> There's quite a few differences to be quite honest...but the basics are in how they are organised, and more basic aesthetic differences, such as the gnome look being different. The basic architecture of Ubuntu and Xubuntu is pretty much the same though.


So, if I know Ubuntu, I can transition to Xubuntu without too many issues? I'm thinking about using Xubuntu because my partitioning software cant seem to pull off alot of memory, and Xubuntu appears to be a bit of a smaller OS.

---

### Post by Botbob89 on 2009-03-17
> **RAZRBAKK said:**
> So, if I know Ubuntu, I can transition to Xubuntu without too many issues? I'm thinking about using Xubuntu because my partitioning software cant seem to pull off alot of memory, and Xubuntu appears to be a bit of a smaller OS.

Xubuntu is pretty much a lightweight version of Ubuntu, designed to run for people in situations like yours. If you are confident with Ubuntu you won't have too many problems with Xubuntu

---

### Post by RAZRBAKK on 2009-03-17
> **Botbob89 said:**
> Xubuntu is pretty much a lightweight version of Ubuntu, designed to run for people in situations like yours. If you are confident with Ubuntu you won't have too many problems with Xubuntu

Awesome. 

Thanks!

---

### Post by presence1960 on 2009-03-17
> **Skol312000 said:**
> Wooooooooooooooow.    Im extremely confused right now!!!


I want to delete all OSs off my laptop (Vista and Ubuntu)!!!
after that i want to install only Ubuntu 64 bit!!!!

I do not want to delete Grub. I just want to do this and ot seems that every answer i get is different from the last!!




How do i do this as easy and safest way?  Please help?

Do i need to defrag before anything?  Please help!!!

Pop in the 64bit ubuntu Live CD,reboot & choose install. When the partitioner comes up choose use entire disk. This will wipe Windows and your 32bit Ubuntu off the disk. Your new 64 bit Ubuntu will have the entire disk and GRUB will be installed on it.

SKOL31200 not to make a big thing out of this but I have seen you ask the same question in about 6 or 7 threads. If you want to wipe your hard disk clean and have 64bit Ubuntu take the whole disk then use the Live CD.

---

### Post by presence1960 on 2009-03-17
> **Skol312000 said:**
> Omg. Why is this so hard?  I just want to wipe the OSs and then put i. 64 bit.... How can i do t? Is it really thT hard?  Is sure was easy to install

**It is not that hard!!** I have seen this answered for you in a few other threads. You are making it hard. Take the Live CD , put it in the optical drive, reboot...choose Install, when you get to the part where the partitioner comes up choose use entire disk. Case closed you will get what you want accomplished!

---

### Post by RAZRBAKK on 2009-03-17
This is some serious ********.

I did 4 disk defragments, and I checked to see how much I can partition, and it tells me its dropped about 1000 MB. This sucks!

---

### Post by Botbob89 on 2009-03-17
OK,  now you have utterly confused me, why are you defragmenting the drive if you are planning a clean install anyway?

---

### Post by RAZRBAKK on 2009-03-17
> **Botbob89 said:**
> OK,  now you have utterly confused me, why are you defragmenting the drive if you are planning a clean install anyway?

See, this is the problem, when someone comes in and hijacks the thread, you loose track of the OP. I am planning on partitioning to have Xunbuntu and Vista. For some reason, I have lost 3% of the space free space on my HDD. I do not know where it went... I haven't done anything!

---

### Post by Botbob89 on 2009-03-17
Ahhhhh apologies, that was me reading wrongly, sorry....

Well if you have a large HD that 3% was probably just junk backup and loading files that Windows no longer needs, I'm fairly sure no important files would have been lost in that

---

### Post by RAZRBAKK on 2009-03-17
> **Botbob89 said:**
> Ahhhhh apologies, that was me reading wrongly, sorry....

Well if you have a large HD that 3% was probably just junk backup and loading files that Windows no longer needs, I'm fairly sure no important files would have been lost in that

No I LOST it. I had 45% of the HD free, and now I only have 42%. 

Am I able to install and run Xubuntu with only 6 GB of space? 

This windows partitioner sucks...

---

### Post by Botbob89 on 2009-03-17
It's actually lost? Xubuntu can be installed with 6GB of space as far as I know, as long as you aren't planning on lots and lots of downloads and saves etc.

You may be a bit squeezed for space in the future, dependent on use of course

---

### Post by presence1960 on 2009-03-17
> **RAZRBAKK said:**
> See, this is the problem, when someone comes in and hijacks the thread, you loose track of the OP. I am planning on partitioning to have Xunbuntu and Vista. For some reason, I have lost 3% of the space free space on my HDD. I do not know where it went... I haven't done anything!

Sorry RAZRBACK... I couldn't bite my lip any longer with SKOLL312000. He has been going from thread to thread asking the same question. When I read it on this thread again it just got to me. My apologies.

---

### Post by RAZRBAKK on 2009-03-17
> **presence1960 said:**
> Sorry RAZRBACK... I couldn't bite my lip any longer with SKOLL312000. He has been going from thread to thread asking the same question. When I read it on this thread again it just got to me. My apologies.

It's cool man. His poor grammar made me cry a little. :lolflag:

---

### Post by hockman5 on 2009-03-18
To free up more sapce. Delete some of your old system restore points, turn system restore off, then see how much space you freed up. Then set everything back after you finish your install.
{edit} also do a disk cleanup to get rid of the temp crap. Go through your add and remove programs and uninstall the junk as well.

> **RAZRBAKK said:**
> This is some serious ********.

I did 4 disk defragments, and I checked to see how much I can partition, and it tells me its dropped about 1000 MB. This sucks!

---

### Post by hockman5 on 2009-03-18
> **Botbob89 said:**
> OK,  now you have utterly confused me, why are you defragmenting the drive if you are planning a clean install anyway?

That was a different poster doing the clean install.

---

### Post by Botbob89 on 2009-03-18
> **hockman5 said:**
> That was a different poster doing the clean install.
lol I know :P

We cleared that up

---

### Post by hockman5 on 2009-03-18
> **Botbob89 said:**
> lol I know :P

We cleared that up

sorry, caught that after the post.

---

### Post by hockman5 on 2009-03-18
Also Razrbakk,
   I have been doing a trial switch from windowsXP to Ubuntu. I am currently running a virtual XP machine on Ubuntu. It works pretty well but the more Windows applications you install on it, the slower it gets. Remember, the virtual machine is one file so it takes longer to access items within that one file. I have discovered that the only reason I need to even run the virtual machine is to use Quicken and Quickbooks. Everything else I have been able to accomplish in Ubuntu. I still have my original windows install  as a seperate partition but I rarely ever boot into windows anymore. I would highly recommend running virtual windows as opposed to running virtual Ubuntu, since Ubuntu is more stable.

---

### Post by Helios1276 on 2009-03-18
This thread is nuts!

@OP 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Vista does not like to be shrunk but there are ways around it. you _do not _ need to settle for xubuntu...

---

### Post by RAZRBAKK on 2009-03-18
> **Helios1276 said:**
> This thread is nuts!

@OP 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Vista does not like to be shrunk but there are ways around it. you _do not _ need to settle for xubuntu...

I tried everyting on that site. You know what happened? The space for partitioning got LOWER.

I don't think I'd be settling for Xubuntu. It'd be an upgrade for me. It does everything I need in an OS. 

As  musician, I need a highend recording program. Ardour 2 meets that. There are alot of really good things about Ubuntu, and I'm just gonna go for it. I'm fed up with windows.

---

### Post by Helios1276 on 2009-03-18
> **RAZRBAKK said:**
> I tried everyting on that site. You know what happened? The space for partitioning got LOWER.

I don't think I'd be settling for Xubuntu. It'd be an upgrade for me. It does everything I need in an OS. 

As  musician, I need a highend recording program. Ardour 2 meets that. There are alot of really good things about Ubuntu, and I'm just gonna go for it. I'm fed up with windows.

Those steps are not guaranteed to work but a fresh install of both OS's usually does the trick. I'm a musician myself and would have reservations about using Ardour in the 'high-end' sense but good luck and enjoy.

---

### Post by RAZRBAKK on 2009-03-18
> **Helios1276 said:**
> Those steps are not guaranteed to work but a fresh install of both OS's usually does the trick. I'm a musician myself and would have reservations about using Ardour in the 'high-end' sense but good luck and enjoy.

I would compare it to what I use on windows, which would be Reaper.

Also, somehow the approx. 10 GB partition that was used for the Recovery part of Vista has dissappeared. My computer is slowly killing itself, I think.

Plus I just enjoy Kubuntu...

---

### Post by Helios1276 on 2009-03-18
That is fair enough I suppose, just making sure  were not coming from pro-tools, cubase etc and setting yourself up for frustration.

---

### Post by RAZRBAKK on 2009-03-18
> **Helios1276 said:**
> That is fair enough I suppose, just making sure  were not coming from pro-tools, cubase etc and setting yourself up for frustration.

No. I use pro tools as an audio engineer part time, but I actually prefer the simpler DAWs when at home, just jamming a bit.

---

