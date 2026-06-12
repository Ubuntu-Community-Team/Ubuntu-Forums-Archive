---
title: "New Install help (home)"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-17
Hi All.

I am running 10.04 and my setup is running like a dog. When typing this is appearing seconds later.

I have two large hd's and am in the middle of copying my /home to the second drive.

Could someone post a simple guide to reinstall 10.04 and use the copied /home folder to use a my separate /home folder on my new install.

All I can find are guides to setting up a new separate /home folder on the same drive.

Dont want to end up getting lost and screwing things up.

Would I also lose my compiz set up. I assume...my emails are also stored on /home as standard?

Cheers,

Spill.

---

### Post by d3ngar on 2011-05-17
Should be pretty easy to mount your second hard disk as the home folder during install. I'm quite sure it's an option when it comes to partitioning. I'd have a look at the manual configuration.

---

### Post by spillage2 on 2011-05-17
ok I have looked and it looks like i have to manually create each partition ie / /swap and /home.

if i just copy my current /home to my second hd how simple will it be to move it back.

can i just move it over then move it back through gnome or will it have to be move via terminal.

just worried if i do a fresh install i will lose all my emails and settings...

---

### Post by spillage2 on 2011-05-18
ok I have copied my home folder to my second drive.

sudo cp -R /home/user /media/second drive.


its all there ready to do whatever.

I cannot see that I can select that file on the setup and can only create a new home folder.

Believe me I have google my butt off trying to find out how to change my new setup to use the copy of my old home file.

Any help would be appreciated on how to do this..

---

### Post by wildmanne39 on 2011-05-18
> **spillage2 said:**
> ok I have copied my home folder to my second drive.

sudo cp -R /home/user /media/second drive.


its all there ready to do whatever.

I cannot see that I can select that file on the setup and can only create a new home folder.

Believe me I have google my butt off trying to find out how to change my new setup to use the copy of my old home file.

Any help would be appreciated on how to do this..Hi, you should be able to copy the contents of the old folder to your new one, it might give you permission denied, if it does post back here.

---

### Post by grahammechanical on 2011-05-18
I am sure that during the fresh install you choose to manually partition. You tell the installer to put Ubuntu on the first hard disc by giving that disc a mount point of / If you mark it to be formatted everything on that disc will be wiped. You can install over an existing install.

You give the second hard disc the mount point of /home but do not mark it to be formatted. Then the new install will see your home folder on the second hard disc.

I do not have two hard discs but I do have a /home partition and when I do a fresh install I do what I have just told you to do and I do not lose my data or my settings.

Assigning the mount points and being selective about formatting is the key to doing this. Also have a second copy if there is space.

Regards.

---

### Post by spillage2 on 2011-05-19
Thanks for the responses...

@ graham..yes it now make sense that by not formating /home on my second drive will not wipe all my data...I assume that it will just use the /home folder I have copied and not write a new version over the old one.

I am sorry but I do lack knowledge with regards to this..I may also make another copy on my second disc and change the folder name just in case.

Sorry to ask yet another question but would I need to edit my fstab file to auto mount my second drive at boot up or would this be done automatically on the fresh install?

---

