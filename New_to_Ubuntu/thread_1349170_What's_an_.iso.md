---
title: "What's an .iso?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by grief -l on 2009-12-08
I read the wiki so I know what it's supposed to be but it's got me confused.
 
I jumped into linux with an ubuntu iso and ran it from the CD. But since I had no wireless network I thought maybe it needs to be installed, so I did that, dual boot with XP which lights up the wireless usb no problem. Installing didn't help - still no wireless -the light on the dongle doesn't come on. So I followed some how-to's here hoping to build and install drivers for the dongle.
 
At one stage I was instructed to reboot, which I did, only to find my screen resolution was down to 800 x 600 and no way to get back to 1024 x 768! No problem, I thought, I'll just reinstall and wipe out everything Packman gobbled up. Not so! Now the CD also has only three resolution choices 800 x 600 being the best I can get.
 
Just to check I ran Puppy and Freespire from the CDs and they both run at 1024 x 768 as does XP.
 
How does screwing up the installed code affect what's on the instilation disk?

---

### Post by bradleypariah on 2009-12-08
Well, the dongle thing is probably a chipset issue.  Not all wireless dongles are compatible with Linux.  I know the D-Link USB dongles work, but brands such as Belkin do not.

As far as your resolution issues go, you'll be joining the club.  Tell you what, there IS a way to fix it.  It's a bit weird and you'll have to download the .iso file of ubuntu 8.04 to fix your 9.10 install (like I said, it's weird).
Click this link and follow the first post's instructions.  You should be all fixed up.
[**Fixing low screen resolution for legacy hardware**]("http://ubuntuforums.org/showthread.php?t=1320785")

Sorry about your wireless problems.  Did it work with Puppy?  If not, I think we have our answer about whether or not it's a compatible chipset.
The good folks at Fry's Electronics can guide you to an educated purchase when it comes to stuff like this.

---

### Post by MelDJ on 2009-12-08
to answer the thread title, a .iso is an image of a cd. think of it to be like a zip of a cd

---

### Post by Marvin666 on 2009-12-08
I've made iso's of hard drives, and flash drives as well. It's just sector by sector copy, so it's an exact replia of every bit on the drive.

---

### Post by grief -l on 2009-12-08
Thanks, but I'm not stressed about fixing the dongle or resolution (both work in XP), I do want to know how the .iso on the CD knows what happened to the installed version?

---

### Post by bradleypariah on 2009-12-09
Well, that .iso file is actually *writable*.  A CD with an .iso file is not "finalized".

Your live CD has to be able to interact and adapt on the fly.
This is why you're able to actually be productive from the CD alone.  
You can install software, play music, write code/documents, and ultimately, make permanent changes to the operating system.

That being said...

Idea 1) I guess it's logical to believe whatever "decision" your installed OS made that changed your graphics options - the .iso would do the same.  It wasn't necessarily the OS that changed your .iso.

Idea 2) From my understanding, unless you manually flash your RAM, there could be a lot of stored information in there that the CD is referencing to, seeing as valid, functional Operating System data.

Idea 3) During re-installation, one of your ext partitions (for whatever reason) was not formatted.   Instead it was kept intact and every file in there is now being used.

Anybody got any other ideas?

---

### Post by grief -l on 2009-12-12
Thank you, that's the kind of answer I was looking for. I actually went back and formatted that ext4 space with the 8.10 CD and I see it doesn't clean out the whole partition. There's still 200 + Mb left which I assumed was formatting code. Before installing 8.10 I ran the 9.10 CD live again and it's still 800 X 600 so probably has been written to in spite it being a 'closed session'.
 
Installing 8.10 didn't fix it either and I've never flashed anything before so I guess I'll just have to live with guessing what buttons have dropped of the screen.
 
Gabe

---

