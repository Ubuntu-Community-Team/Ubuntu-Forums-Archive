---
title: "Wubi install of Ubuntu 9.10 - bad sectors in hard drive"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by stickynote427 on 2009-11-08
I apologize for posting this thread, as I read that there are already many threads about it, but the solution someone was given is from two years ago (Aug 2007), so I wanted to ask the question myself.

I just installed Ubuntu 9.10 on my Windows XP SP3 computer last night. I restarted my computer and was given the choice to boot between Windows and Ubuntu, and Ubuntu started when I selected it.

Soon after I logged in and the Ubuntu desktop had loaded and everything, an icon appeared in the top bar (if there's any specific term for it; sorry, I haven't even looked at Linux-based OSes until yesterday, so I know nothing about them) that looked like a hard drive, if I remember correctly. I hovered over it and a notification bubble appeared telling me that something was wrong with my hard drive.

I double-clicked it to open it for more information, and I was told that my hard drive had bad sectors.

Now, the thread from August 2007 resolved this as a bug, but I'm not sure if this would still be the solution, considering I'm running a different version of Ubuntu than this other person was.

Thanks!
stickynote427

---

### Post by LewRockwell on 2009-11-08
now would be a good time to secure anything valuable off that hard drive

if you think the drive is close to failing you might want to prioritize your data recovery considering you might not secure all of it before the drive fails

we use Clonezilla to maintain recent clones so if there is a problem we just switch drives and continue on

.

---

### Post by Paqman on 2009-11-08
Make sure you install all the updates that are available. Earlier versions of the disk utility included with Karmic during development had a bug that caused them to report perfectly good drives as defective. If you're still getting the warning after you've run all your updates, then you need to start thinking about securing your data and replacing the disk.

Note that the disk utility will tell you exactly why it is reporting the disk as faulty. The bug i'm talking about related to to the number of reallocated bad sectors. It's no problem at all if your drive has a few bad sectors that have been remapped. I'd be more concerned if there were bad sectors that weren't being reallocated.

---

### Post by stickynote427 on 2009-11-08
Okay, thank you. When I get on that computer again, I will update everything (as I didn't do it last night; it was late and I wasn't really supposed to be up at 1 AM). By "securing your data", do you just mean to back it up on a different hard drive?

I will also look at the disk report (as I didn't really do that last night either) once I have the chance.

Thanks again!

---

### Post by Paqman on 2009-11-08
> **stickynote427 said:**
>  By "securing your data", do you just mean to back it up on a different hard drive?


Hard drive, DVD, USB stick, anything that isn't the drive in question.

Hard drives can and do fail. So this might be a good time to start thinking about a permanent way to protect your valuable data from the risk of drives failing.

---

### Post by phillw on 2009-11-08
> **stickynote427 said:**
> Okay, thank you. When I get on that computer again, I will update everything (as I didn't do it last night; it was late and I wasn't really supposed to be up at 1 AM). By "securing your data", do you just mean to back it up on a different hard drive?

I will also look at the disk report (as I didn't really do that last night either) once I have the chance.

Thanks again!


Hi,

Yes they mean backup your data to another hard drive, just in case it not a false alert on the errors being reported.

[http://clonezilla.org/](http://clonezilla.org/)  seems to be highly recommended by others on this site.

It's always good to have a backup :p

Phill.

---

### Post by stickynote427 on 2009-11-08
I'm sorry. The computer that I installed Ubuntu through Wubi on is insanely slow, so it was pretty much impossible for me to do anything while booted in Ubuntu.

I may just install Ubuntu through Wubi on my primary, Windows Vista computer. It has plenty of RAM and hard disk space, while the other one has less than 512 MB of RAM and only about 1 GB of free hard disk space. If that becomes the case, I will mark this thread as resolved.

---

