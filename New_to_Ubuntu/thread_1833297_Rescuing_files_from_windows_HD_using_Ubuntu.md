---
title: "Rescuing files from windows HD using Ubuntu"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by gymnost on 2011-08-25
Hi all,
 
I've had a windows system go down (XP), and it refuses to reboot (actually, reboots continually) if I try to load windows. The system is ancient and I won't cry if it stays dead but I want to rescue some files from the hard drive. The hard drive is functional, I can see everything from the DOS prompt if I boot from a recovery CD. 
 
So I'm currently trying ubuntu (11.04) as a means of getting the files off. I've burned a Live Cd and have been booting off the CD without installing. It seems to run fine (though it occasionally asks for username and password when I try to carry out some operations), and I can see both my Windows hard drive and USB drive. However, the hard drive is currently designated as "read-only" and I can't remove anything, which is not so good. I can mount and unmount it okay, though that doesn't really change anything. It's driving me nuts, I can see everything I want, I just can't remove it from the machine.
 
1) Is there any way I can get the files off successfully while running Ubuntu off the CD?
 
2) If not, is installing Ubuntu on the machine likely to change the situation? Can I install ubuntu properly without internet access? Will installing ubuntu affect the Windows partition at all?
 
My computer skills are fairly basic, and I'm totally new to Ubuntu and Linux in general. The system is not currently connected to the net, though I can figure out how to connect once I have ubuntu installed. 
 
Any help you can provide would be most appreciated.

---

### Post by coffeecat on 2011-08-25
Two things:

> **gymnost said:**
> I've burned a Live Cd and have been booting off the CD without installing. It seems to run fine (though it occasionally asks for username and password when I try to carry out some operations)

If the live CD is prompting you for a username and password then it is faulty. There is a username and password for the live session, but the only time you should see a prompt for them is if you log out and in again. And you can't do this in the 11.04 live session from the GUI - you have to know some advanced tricks. So I suspect the CD is faulty. Did you check the md5sum of the downloaded ISO? Also - if you tap any key when the two small icons appear at the bottom of the screen when you first boot the CD, you can choose a disc integrity check from the text menu. Or - it might be something as simple as a speck of dust on the CD.

Long story short - don't do data recovery or anything critical from a live Ubuntu session that is prompting you for username and password.

> **gymnost said:**
> However, the hard drive is currently designated as "read-only" and I can't remove anything, which is not so good.

If it's mounted read-only then you should be able to copy things from it, so I don't follow that. Can you clarify exactly what is happening? What is important to know is that if a NTFS filesystem is damaged (which it sounds as though it might be), Ubuntu will refuse to mount it at all. This is a failsafe to prevent further damage to the filesystem. The only effective way to repair a NTFS filesystem is with chkdsk in Windows.

Are you able to remove the hard drive and put it in a USB enclosure? And do you have access to another Windows machine? If yes to both I suggest you run a chkdsk on the affected partition.

---

### Post by dniMretsaM on 2011-08-25
> **coffeecat said:**
> If it's mounted read-only then you should be able to copy things from it, so I don't follow that. Can you clarify exactly what is happening? What is important to know is that if a NTFS filesystem is damaged (which it sounds as though it might be), Ubuntu will refuse to mount it at all. This is a failsafe to prevent further damage to the filesystem. The only effective way to repair a NTFS filesystem is with chkdsk in Windows.

I'm guessing he's trying to move the files, not copy them. That wouldn't work because it would be trying to remove them from the Windows HD and that's not possible in read only (at least I don't think so, I don't have much experience with such things).

---

### Post by gymnost on 2011-08-25
> Long story short - don't do data recovery or anything critical from a live Ubuntu session that is prompting you for username and password.

 
That's useful to know. I'll try those checks you mentioned, or burn another disk. 
 
> If it's mounted read-only then you should be able to copy things from it, so I don't follow that. Can you clarify exactly what is happening? What is important to know is that if a NTFS filesystem is damaged (which it sounds as though it might be), Ubuntu will refuse to mount it at all.
 
When I drag and drop (or copy/paste) the files of interest from the hard drive to my USB, it displays an error. When I check for details, it says (something along the lines of) "File system is read-only". It is possible that the disk is damaged (see below) but it definitely seems to be mounting and unmounting okay, from what I can tell.
 
> Are you able to remove the hard drive and put it in a USB enclosure? And do you have access to another Windows machine? If yes to both I suggest you run a chkdsk on the affected partition.
 
No (I don't have a USB enclosure), and yes. Though I might purchase a USB enclosure if nothing else is working. Someone more technologically inclined than me ran a chkdsk using a windows recovery CD. The initial problems were (likely) caused by a viral infection so I wouldn't be surprised if there is damage to the drive, and I don't know if the chkdsk has resolved the problems or not. 
 
Thank you for your advice!

---

### Post by F.G. on 2011-08-25
sounds odd.  i've never had any trouble copying stuff from a windows partition with a live disk.  i'd suggest trying to download and burn another copy.
you could try right clicking on the highlighted folders and click on copy.  then right click in the folder you want to copy them too and click paste. this does actually work for whole directories of stuff.

---

### Post by gymnost on 2011-08-25
> **dniMretsaM said:**
> I'm guessing he's trying to move the files, not copy them. That wouldn't work because it would be trying to remove them from the Windows HD and that's not possible in read only (at least I don't think so, I don't have much experience with such things).
 
Good suggestion. However, I've tried both, and it doesn't work either way! 
 
[QUOTE=F.G.]sounds odd. i've never had any trouble copying stuff from a windows partition with a live disk. i'd suggest trying to download and burn another copy.
you could try right clicking on the highlighted folders and click on copy. then right click in the folder you want to copy them too and click paste. this does actually work for whole directories of stuff. [/QUOTE]
 
I'll defintiely try this when I have access to the machine again. Hopefully the trouble I'm having is due to a dodgy CD, and doesn't indicate that the HD is totally rooted.

---

