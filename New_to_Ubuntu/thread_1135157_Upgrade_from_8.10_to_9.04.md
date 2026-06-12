---
title: "Upgrade from 8.10 to 9.04"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-04-24
Someone mentioned yesterday that only the people with problems are posting which tends to skew the impression that the upgrade isn't working properly.  Just wanted to add that I used the regular system upgrade to upgrade from Ibex (8.10) to Jackalope (9.04) and it ran perfectly.  NO issues no problems other than the servers were slammed and very busy and slow.  But it all went without problems and the new install is working perfectly. 

Good job to the Devs.

---

### Post by JoshuaRL on 2009-04-24
> **Desert Sailor said:**
> Someone mentioned yesterday that only the people with problems are posting which tends to skew the impression that the upgrade isn't working properly.  Just wanted to add that I used the regular system upgrade to upgrade from Ibex (8.10) to Jackalope (9.04) and it ran perfectly.  NO issues no problems other than the servers were slammed and very busy and slow.  But it all went without problems and the new install is working perfectly. 

Good job to the Devs.

:)

Really great to hear feedback like this.  I installed fresh and everything's working great.  Boots super quick, and things look pretty.

---

### Post by Marcelo Santos on 2009-04-24
This information about issues is true. I've made 3 migrations yesterday, and one of them was resulted in a raid0 partition that wasn't mounted at the first time.

When I investigated, I discovered that in the upgrade process, the raid device /dev/md0 was renamed to **/dev/md_d0** and because of this Samba did not work after the reboot.

To fix this, I issued the following commands:

mdadm --assemble /dev/md_d0 /dev/sdb1 /dev/sdc1 /dev/sdd1

and, edited my /etc/fstab to reflect the new name of raid device.

This took about 20 minutes to discover and fix... Them, there is no way to blame the ubuntu team or any other person because I never imagined that is possible to upgrade AN ENTIRE SYSTEM with a single command line.

I speak it because I'm a MCSE in a new company/job with a mission to upgrade about 32 servers runnig various linux flavors to Ubuntu Server.

In 1998 I worked with Linux, and in that time I was obliged to implement and use Microsoft products.... And now I have the opportunity to use my Microsoft knowledge to integrate these both operating systems in a mixed environment.

And to speak the truth... I'm loving it! The Linux world was evolved in some way that I never imagined... Great, great job guys!

Let me know if there is any additional info that I can share with the community to help with the future upgrade process.

Regards,

Marcelo Santos.

---

### Post by jdrodrig on 2009-04-24
> **Desert Sailor said:**
> Someone mentioned yesterday that only the people with problems are posting which tends to skew the impression that the upgrade isn't working properly.  Just wanted to add that I used the regular system upgrade to upgrade from Ibex (8.10) to Jackalope (9.04) and it ran perfectly.  NO issues no problems other than the servers were slammed and very busy and slow.  But it all went without problems and the new install is working perfectly. 

Good job to the Devs.

You wont find this type of post here because they are typically moved to Testimonials....=)

---

### Post by Sef on 2009-04-24
>  	Quote:
 	 	 		 			 				 					Originally Posted by **Desert Sailor** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7133338#post7133338") 				
 				[I]Someone mentioned yesterday that only the people with problems are posting which tends to skew the impression that the upgrade isn't working properly. Just wanted to add that I used the regular system upgrade to upgrade from Ibex (8.10) to Jackalope (9.04) and it ran perfectly. NO issues no problems other than the servers were slammed and very busy and slow. But it all went without problems and the new install is working perfectly. 

Good job to the Devs.[/I]
 			 		 	 	 
You wont find this type of post here because they are typically moved to Testimonials....=)

Correct.  If help is not being asked, then the thread will be moved to Testimonials and Experiences, if Ubuntu is being posted about.

---

### Post by newbuntuxx on 2009-04-24
I did the upgrade automatically and it worked fine. However, boot time is about 1 min (from when I push the power button until I have firefox open). 

I may need a fresh install for a quicker boot time.

Great Job development team!

---

### Post by BUKRITYA on 2009-04-24
My neubiness always managed to complicate things until I found a quick and easy way to fix it. Almost fool proof, yet superiorly advanced and sharp-looking.

You guys (dev guys) are the great shepherds.
Thank you.

---

### Post by newbuntuxx on 2009-05-04
Update: I did a fresh install (took 20 mins). Boot time improved a bit. It takes 40-45 seconds now (depending on how fast i type my user name and pass)

---

### Post by freak42 on 2009-05-04
my upgrade went fine, apart of some xorg config changes I had to do (wacom tablet support, which was noted in the release notes)

---

### Post by Insanity01 on 2009-05-04
> **newbuntuxx said:**
> I did the upgrade automatically and it worked fine. However, boot time is about 1 min (from when I push the power button until I have firefox open). 

I may need a fresh install for a quicker boot time.

Great Job development team!

yeah but u can't count the time ur bios detecs ur whole pc as boot time tbh :P
you can just start counting from when grub starts loading ur os ^^

---

