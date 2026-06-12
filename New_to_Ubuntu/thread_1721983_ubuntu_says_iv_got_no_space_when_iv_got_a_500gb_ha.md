---
title: "ubuntu says iv got no space when iv got a 500gb hard drive? HELP PLEASE!!!"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by alexgwebb on 2011-04-05
im a total noobie when it comes to Linux, iv had ubuntu for a week and im seriously impressed, i partitioned my hard drive when i got my comp, 200 and 300gb. iv got the 200gb for windows and the 300gb for ubuntu but now its saying i have no space in /home file system. and only says iv got 10 gb space in there... how do i allocate all of the 300gb in there??? PLEASE HELP!!!

---

### Post by eriktheblu on 2011-04-05
Boot with your Ubuntu CD, and run Gparted. This should give you a visual on your partitions, and allow you to adjust their size. Make sure you unmount any, and turn off swap before trying to adjust anything.

If you need further assistance, post a screenshot (Alt + Print Screen) of Gparted in this thread.

---

### Post by alexgwebb on 2011-04-05
Thanks for the help. I don't have the CD so I installed GParted from the software centre, and I cant exactly work out what partition to change, is the logical partition the "/home file system" in that part. thanks alot for the help (sorry im retarded)

---

### Post by alexgwebb on 2011-04-05
> **alexgwebb said:**
> Thanks for the help. I don't have the CD so I installed GParted from the software centre, and I cant exactly work out what partition to change, is the logical partition the "/home file system" in that part. thanks alot for the help (sorry im retarded)
Oooo and for some reason the "Alt + Prt Sc" shortcut isnt working, that why full screen shots, sorry

---

### Post by XubuRoxMySox on 2011-04-05
Ubuntu doesn't need alot of of space for the OS. But the "**[COLOR="Blue"]/home[/COLOR]**" partition is where all your stuff is kept (music, pictures, documents, settings, e-mail folders and settings, stuff like that). 

300 GB is awesome! I have an 80-gig drive and tons of room for lotsa stuff. That's because I partitioned my hard drive to give Xubuntu (the partition name - or mount point - is "**[COLOR="Blue"]/[/COLOR]**") 20 gigs (waaaaay more than it needs), 1 gig for "**[COLOR="Blue"]swap[/COLOR]**" (that's 2X my machine's RAM) and the rest is "**[COLOR="Blue"]/home[/COLOR]**".

You can give Windows 200 gigs, then use the remaining 100 GB as follows:

a **[COLOR="Blue"]swap[/COLOR]** partition equal to about 2X your computer's RAM, then 10 GB (still way more than it really needs) as "**[COLOR="Blue"]/[/COLOR]**", and the remainder as "**[COLOR="Blue"]/home[/COLOR]**". 

Having a separate /home partition makes upgrading super-easy, too! I can completely re-install my Xubuntu without losing my settings, bookmarks, e-mail folders, documents, pics, music, etc. I simply choose *"Do Not Format this Partition"* during installation.

Hope that helps,
Robin

---

### Post by Mark Phelps on 2011-04-05
Unless I missed something (hard to read such small print these days ...) all of your partitions, except the Extended partition, are formatted NTFS.

The ONLY way you can install Ubuntu into an NTFS partition is using Wubi -- and the default space for Wubi installs is very small.

The Wubi Guide linked below has instructions for expanding the space you allocated via Wubi, in Section 8.9:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by eriktheblu on 2011-04-05
Yup, you've got Wubi.

I would suggest scrapping it and doing a proper install. Are you ready for an upgrade? 

1. Back your files
2. Get yourself an Ubuntu CD
3. Boot from the CD (you may need to change your BIOS options)
4. delete sda5 (the ntfs partition inside your extended partition)
5. create your new partition(s) in ext format (recommend EXT4) inside your extended partition (I prefer ~20 GB for /, swap equal to system memory, largish /home, and some unformatted space between partitions)

---

### Post by alexgwebb on 2011-04-05
Cheers, Im formating my comp and only using ubuntu... windows is ****

---

