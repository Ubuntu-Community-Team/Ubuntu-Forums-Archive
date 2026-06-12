---
title: "Add a partition for Meerkat alpha-beta"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-06-03
If I add another partition to my current "boot" drive, can I simply download Maverick Meerkate ver. 10.10 and will Grub2

1 - find it?

2 - allow me to boot to it 

or

3 - to my production box of Lucid Lynx 10.04?

Thanks, community.

---

### Post by nhasian on 2010-06-03
i usually wait until alpha3 before jumping onto Ubuntu+1

yes you can create a new partition for Meerkat.  do not share your home partition if you have one, but you can share the swap partition between OSes.

grub will pick up both versions.

---

### Post by Mark_in_Hollywood on 2010-06-03
As I am completely unfamiliar as to how partitons get "shared", please explain whether that gets handled by Grub/Ubuntu automatically on an installation or do I have to open a terminal and set that up or go into System/Admin and 'check' something.

Sorry to be such a 'noob, but here I am.

---

### Post by nhasian on 2010-06-03
> **Mark_in_Hollywood said:**
> Sorry to be such a 'noob, but here I am.

I have to strongly advise you not to use a developmental version of Meerkat.

if your /home is inside your root partition then nothing to worry about just make a new root partition for the new operating system.  a lot of people like to make /home a separate partition so i wanted to make sure you dont use the same partition for different versions of ubuntu.  The installer will automatically see and use the swap partition on the hard disk.  its okay for both Ubuntus to use the same swap partition.

---

### Post by philinux on 2010-06-03
> **nhasian said:**
> I have to strongly advise you not to use a developmental version of Meerkat.



+1 See in here.
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Mark_in_Hollywood on 2010-06-03
Yes, I have / and /home in separate partitions. So I should wait?

As long as the +1 in on it's own partion and my producttion / and /home, etc. are "safe" I have no fear of trying it. Or should I? I'm not clear on what you are saying, yet.

---

### Post by philinux on 2010-06-03
> **Mark_in_Hollywood said:**
> Yes, I have / and /home in separate partitions. So I should wait?

As long as the +1 in on it's own partion and my producttion / and /home, etc. are "safe" I have no fear of trying it. Or should I? I'm not clear on what you are saying, yet.

If you are prepared for major breakage, of the meerkat install, then test away. Just make sure not to format your existing partitions when using the Manual partition phase of the install. Also being a single hard drive you should have no problems with grub2.
Read up on dual booting.

Optionally you could use Virtualbox and test it that way.

---

### Post by ajgreeny on 2010-06-03
Everyone is saying that it is OK to try meekat as long as you do not use your current home partition as the home partition in meerkat.  Install it as a simple, single /root partition, and then make links to the data folders, if you must, but make sure you keep all the configuration hidden files and folders separate, and do not link to those as well, or you could be in trouble.

Whatever you do decide, always make sure you have good backups of all your files before you do anything.

Actually, make sure you have good backups even if you decide to do nothing:- you know it makes sense!

---

### Post by srs5694 on 2010-06-03
> **nhasian said:**
> yes you can create a new partition for Meerkat.  do not share your home partition if you have one, but you can share the swap partition between OSes.

Actually, you can safely share the /home partition; but in this sort of situation, it's safest to use separate user subdirectories in /home for each installed distribution or version. For instance, /home/mark for the main system and /home/markmeer for the new installation. This is most easily done by specifying a different username for each system, but there are other ways to do it.

That said, given the sorts of questions Mark is asking, I'd have to agree that using an alpha-test distribution is not the wisest course of action. Is there any particular reason you want to use this pre-release software, Mark? If you have a specific need, there may be an easier or safer way to satisfy it.

---

### Post by Mark_in_Hollywood on 2010-06-03
Thank you, one and all. Having had the sage advice I'm going to wait or install a 2nd drive solely for testing of future software. I'm marking this as solved, although that's a misnomer in this instance.

---

### Post by philinux on 2010-06-03
You've forgotten one safe option and thats by using virtualbox.

---

