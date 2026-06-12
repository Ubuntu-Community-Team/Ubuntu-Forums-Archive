---
title: "ubuntu installation failed, what now"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Chuchu on 2009-10-24
OK, First I have to say I'm a total n00b at this but I thought I'd give it a try.

I tried installing Ubuntu, so that I could dual boot it along with Win XP home. I reserved 40 gigs for it. I was going to install it from a CD. And I think that that's my main problem. You see, I burned the CD with the maximum speed and then didn't bother checking it before trying to install. At 55% I got an error and the process ended. So now I've lost 40 gigs of my HDD. I know it's still there, just using a different file system that Windows doesn't recognize.

I burned a new CD and tried to install again. I now get a info as though I have Win XP and Ubuntu installed on my computer and have the option to install another (WTH??!!) Ubuntu besides those two or delete everything on the drive and install ubuntu. Now deleting everything is out of the picture, because I don't even know if I'll like Ubuntu enough.

So my question is, is it possible to format the partition that I reserved for Ubuntu before and install a new copy on it or set it to NTFS and use windows there for a while longer (untill 9.10 comes out prolly)?

And the second question, should I redownload the .iso since even when burning the second CD it gives me a few errors before I get it to work if I put it in while in Windows.

Appreciate the help!

---

### Post by peterinmalaga on 2009-10-24
I'm A Newbie too but I am fairly sure you have to start from scratch again. Also see these:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) 

Good luck. And do the burn at a SLOW speed.

---

### Post by Chuchu on 2009-10-24
> **peterinmalaga said:**
> I'm A Newbie too but I am fairly sure you have to start from scratch again. Also see these:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) 

Good luck. And do the burn at a SLOW speed.

Thanks for the first link. Already have the second. But that doesn't really answer my first question. I want to format the partition that supposedly has Ubuntu installed on it (when in fact I only got to 55%).

thanks anyway, I appreciate it.

---

### Post by RJARRRPCGP on 2009-10-24
Unless your CD drive is old, you should be fine at 40x.

52x is NOT recommended. Because 52x appears to not even be an official spec.

---

### Post by sliketymo on 2009-10-24
> **Chuchu said:**
> OK, First I have to say I'm a total n00b at this but I thought I'd give it a try.

I tried installing Ubuntu, so that I could dual boot it along with Win XP home. I reserved 40 gigs for it. I was going to install it from a CD. And I think that that's my main problem. You see, I burned the CD with the maximum speed and then didn't bother checking it before trying to install. At 55% I got an error and the process ended. So now I've lost 40 gigs of my HDD. I know it's still there, just using a different file system that Windows doesn't recognize.

I burned a new CD and tried to install again. I now get a info as though I have Win XP and Ubuntu installed on my computer and have the option to install another (WTH??!!) Ubuntu besides those two or delete everything on the drive and install ubuntu. Now deleting everything is out of the picture, because I don't even know if I'll like Ubuntu enough.

So my question is, is it possible to format the partition that I reserved for Ubuntu before and install a new copy on it or set it to NTFS and use windows there for a while longer (untill 9.10 comes out prolly)?

And the second question, should I redownload the .iso since even when burning the second CD it gives me a few errors before I get it to work if I put it in while in Windows.

Appreciate the help!
  

Just my two centavos.I would first boot up xp,then download and install EasyBcd.When you get the new .iso downloaded,check the md5sum(save you a lot of problems if the dl. is a good one).Boot up the new CD,start the installation.When you get to the point where it asks where you want to install it,choose "manual".Highlight the old Ubuntu partition,and delete it.Install your new Ubuntu in that free space.When you get to the end,it will show you what is going to be partitioned,and where everything is going to be installed.At the bottom of the window,click on the "Advanced" button.The next window will show you that it is going to install grub to hda0.choose to install grub to the \ root partition.Install. Boot up xp,and run EasyBCD.Add a linux entry,and choose the  \root partition to boot.save,and close.Reboot and choose Ubuntu.Kind of a long winded reply,but it may save you a few problems later on.:guitar:Rock On,bro.

---

### Post by cguy on 2009-10-24
Choose to manually partition the drive.
Then select the old 40GB partition reserved for ubuntu, set the FORMAT flag on and set "/" as the mount point.

I say it can't not work, but post pics if you run into trouble.

---

