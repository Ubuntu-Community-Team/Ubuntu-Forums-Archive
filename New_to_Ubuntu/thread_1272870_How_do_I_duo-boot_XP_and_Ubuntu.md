---
title: "****How do I duo-boot XP and Ubuntu???****"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by ubuntnoob512 on 2009-09-22
Go to this link for my computer's background:

[http://ubuntuforums.org/showthread.php?t=1272186](http://ubuntuforums.org/showthread.php?t=1272186)

Ok, my computer is now 100% ubuntu because I cleared the Hard Drive.

I want to also put windows XP pro 32 bit edition on there.

I have XP burned to a disk and on a flash drive with lots of other stuff on it.

Thanks a lot!

---

### Post by wojox on 2009-09-22
Just follow these steps:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by t0p on 2009-09-22
It's generally easier to install XP first, and then to install Ubuntu next to it.  This is because Ubuntu doesn't mind sharing but XP absolutely hates it.

But it can be done.  Check out [this tutorial]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm").

---

### Post by ubuntnoob512 on 2009-09-22
thanks both, hopefully next time i post i will be on windows

---

### Post by ubuntnoob512 on 2009-09-22
Wow, It takes forever to shrink the partion.
 
It has been 15 minutes.
 
I know this is normal because it is running off of a live cd but it still is a little to slow for my likeing.

---

### Post by ubuntnoob512 on 2009-09-22
Well, when I put the windows XP disk into my computer, i press f11 (boot menu) and my computer goes into ubuntu. I have repeated the process 3 times.

is this normal?

my computer recognizes the disk.

it is pirated so that may effect something.

please help!!

---

### Post by ubuntnoob512 on 2009-09-22
now it reconized there is a disk but when i try to boot from it
 
it says:
 
boot error
press any key to contnue
 
when i presss something the same message repeats.:confused:
 
:frown:

---

### Post by kansasnoob on 2009-09-22
So simple it worked for me the first time around:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by Darkwing-Duck on 2009-09-22
Setup a partition to run your windows install on. Once you install windows you will need to restore GRUB for a good dual boot. Here is a good tutorial for restoring GRUB.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

### Post by ubuntnoob512 on 2009-09-23
Yes, I have followed that link and i stopped on the XP install step.

That is my problem.

---

### Post by NightwishFan on 2009-09-23
I advise you do not pirate an OS.

So the problem is your Windows CD does not boot?

---

### Post by ubuntnoob512 on 2009-09-23
yes

---

### Post by urugTON on 2009-09-23
In your first post you wrote "I have XP burned to a disk".  Further posts indicate that the "disk" is a CD or DVD.  

Did you create the disk or is it an XP installation disk?

For this process to work, the CD/DVD has to be bootable.

---

### Post by ubuntnoob512 on 2009-09-23
Ok, I opened Nero in windows, copied the iso file into the burn list.
and pressed burn.

5 minutes later i take the disk out and i put it into my "wannabe ubuntu and XP dual boot computer" and it doesn't work.

---

### Post by ubuntnoob512 on 2009-09-23
Oh sorry, i forgot, it is a CD

---

### Post by urugTON on 2009-09-23
Sounds promising.  What was the iso?

---

### Post by ubuntnoob512 on 2009-09-23
i will post the link

it will take a sec to find it again

---

### Post by ubuntnoob512 on 2009-09-23
got it

[http://thepiratebay.org/torrent/4206516/TinyXP_Rev09_-_eXPerience](http://thepiratebay.org/torrent/4206516/TinyXP_Rev09_-_eXPerience)

---

### Post by urugTON on 2009-09-23
Well, according to the link, you should have a bootable CD.  

Your machine can obviously boot from a CD and you know how to boot from a CD since you've used a LiveCD to repartition the hard drive.  

I think that leaves the TinyXP CD you got through pirate bay from a user named eXPerience as the source of the problem.

Has this CD ever successfully booted?

---

### Post by ubuntnoob512 on 2009-09-23
Not the cd I burned but 2 friends downloaded the same thing from the same guy and there machines booted fine.

At the time, they had no OS on their computer when they put that on.

---

### Post by urugTON on 2009-09-23
My best guess at this point is that the CD is bad - download corrupted the file, burn didn't work correctly or the CD is dirty. 

You could repeat the download using Ubuntu and burn the CD again or if you have access to one of the CDs that your friends used you could give that a try.  If I were in your shoes, I'd try the friend's CD 1st.  

Good luck.

---

### Post by ubuntnoob512 on 2009-09-23
Ok, i will have one of my friends ship me the disk.
He lives like 16 hours away by car.

---

### Post by ubuntnoob512 on 2009-09-23
Actually I am re-downloading it to burn again with linux.

---

### Post by ubuntnoob512 on 2009-09-23
I repeated the process, it is doing the same thing with the other disk.

Maybe I burned it wrong?

---

### Post by pedro3005 on 2009-09-23
Yes, make sure you burn it as an image, and not just a data disc with the iso on it. To check, insert the cd and on linux explore it. Are there several files or just one (.iso)?

---

### Post by urugTON on 2009-09-23
Pedro - here I am trying to be soooo careful and you point out the obvious. :roll:

Good thought.

---

### Post by pedro3005 on 2009-09-23
So that means I was right or stupidly wrong?

---

### Post by ubuntnoob512 on 2009-09-23
it is an iso file

(one iso file)

---

### Post by pedro3005 on 2009-09-23
Well that won't work. Since you have NERO, check this out: [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)

---

### Post by ubuntnoob512 on 2009-09-24
thanks, i am at school rightnow and by bassed the internet security, i will do that once i get home.

---

### Post by ubuntnoob512 on 2009-09-24
ok, i burned it wrong. I downloaded active iso burner and it worked like a breese.
thanks all

---

### Post by urugTON on 2009-09-24
Glad you can boot the CD.

====================================================================================
I just got back online and I see that I may have inadvertently insulted pedro3005.  The rolling eyes in my response to his message were for me missing the obvious.  I never intended any insult to his reply, let alone implying that he was "stupidly wrong".  I apologize for any bad feelings I may have created.  There was no such intent on my part.

I'll send a private message to make certain that pedro3005 hears my apology.

---

### Post by ubuntnoob512 on 2009-09-24
Visit my new post: 

this one is up to date:

[http://ubuntuforums.org/showthread.php?t=1274638](http://ubuntuforums.org/showthread.php?t=1274638)

---

