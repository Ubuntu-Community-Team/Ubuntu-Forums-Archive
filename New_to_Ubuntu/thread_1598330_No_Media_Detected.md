---
title: "No Media Detected"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by mherr on 2010-10-16
I installed ubuntu on this computer about 4 weeks ago using one of its two CD drives. I have been experimenting with it since then. Along the line, I upgraded to 10.4.

At some point, the CD stopped working. The 2nd CD drive works fine. When I reference the nonworking CD drive with Disk Utility, it sees it and describes it accurately. However, no matter what is in it, it states No Media Detected. I have tried using a CD Lens Cleaner, but that didn't work.

I have run into this problem in the past with a Windows computer and Microsoft has a fix-it program on their website that solved the problem, so I am confident that the problem is soluble.

---

### Post by robsoles on 2010-10-18
Welcome to UF.

Are you in a position to temporarily install Windows to a drive or partition and try that Windows program that fixed it previously again?

Can you try the DVD/CD-ROM unit with another PC?


What is the name of the fixit program on the MS website? Maybe information about that program can help someone identify a simile for Linux.

---

### Post by mherr on 2010-10-21
> **robsoles said:**
> Welcome to UF.

"Are you in a position to temporarily install Windows to a drive or partition and try that Windows program that fixed it previously again?" 

When I installed Ubuntu, I installed it over the complete hard drive of an old XP machine. I don't see a reinstalled windows in the future.

"Can you try the DVD/CD-ROM unit with another PC?" Pulling the drive from one machine and putting it in another is beyond my current competence.


"What is the name of the fixit program on the MS website? Maybe information about that program can help someone identify a simile for Linux." 

On the website, [http://support.microsoft.com/fixit](http://support.microsoft.com/fixit), it is the first "Fix It" entry on the page.

---

### Post by robsoles on 2010-10-21
:) Good attempt at quoting but I nearly missed your response amongst the quote of me there! Don't worry, I spotted it.

I don't think it will turn out to be the exact same problem that the 'fixit' program from MS fixed in the past - reviewing what they say the problems are that it can fix and what else I can find about it, it looks like it just corrects errors in a Windows registry (and some driver info) so as to enable their OS to read/write it again.

The only way to prove that either way, as far as I can see, is to somehow execute their fixit program and I think it won't be a good thing to try in wine nor a VM - only from an installation of Windows would I expect it to have a chance of proving me wrong.


I think it is worth your while to boot this PC from a LiveCD of 10.04 LTS, using the CD-ROM you know works as the boot drive, and then try accessing a couple of CD/DVDs in the currently failed unit - if it is a software issue with your current install on the PC then booting from the LiveCD should easily access the drive.

Attempting to boot using the drive that is currently failed could perhaps reveal a software issue/failure if the LiveCD session boots successfully from this drive as well.

The fact that the drive is recognised properly by 'Disk Utility' yet media is never recognised in the unit makes me think the unit's optical system may have died.

Something else may prompt me to think of something else you/we can try but at this point, without direct access to the equipment, I am stumped.

---

