---
title: "just having Ubuntu, but keeping my files?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by rocka120 on 2010-07-27
[SIZE=4]I have a dell dimension e510 with windows xp on it, and i was wondering if i could remove xp from it, put Ubuntu on it, but keep most of my files?[/SIZE]

---

### Post by Revolutionary101 on 2010-07-27
You would have to perform a backup of the files that you want to keep. I would suggest copying your files to an external HDD or a large flash drive. Then once you have removed Windows XP, and replaced it with Ubuntu, just copy yours files back onto the computer.

Another possibility is either dual booting or installing Ubuntu via Wubi. Both of these possibilities keep XP (and all the files) but also add Ubuntu to your HDD.

---

### Post by aidenscool09 on 2010-07-27
you could create a new partition, move all the files there, and then just install over the windows xp installation.

---

### Post by wojox on 2010-07-27
+1 for dual boot. Most of the stuff you take of XP and install on Ubuntu probably won't run correctly.

---

### Post by Deersindal on 2010-07-27
If you are planning on quitting Windows and not looking back, I would have to agree with Revolutionary and go with a backup and then reformat your hard drive.

If you are planning on keeping Windows around in order to play games, edit movies, etc., then you would probably want to do a dual boot.

It all depends on your situation, but I have a dual boot for now until I learn to live without windows, then I'm pulling the plug. :popcorn:

Edit:

> **wojox said:**
> +1 for dual boot. Most of the stuff you take of XP  and install on Ubuntu probably won't run correctly.

That might not be true for all occasions. While most of your proprietary files (exes, bats, vbs, and any files specific to a window program) will be broken, your media files (jpg, gif, png, mp3, m4a, mp4) should all be fine.

---

### Post by rocka120 on 2010-07-27
im mainly just trying to keep WOW. i really dont want to sit there for hours and hours waiting for it to download, lol. but i can
mind if i ask another question without starting a new thread?

---

### Post by wojox on 2010-07-27
> **Deersindal said:**
> If you are planning on quitting Windows and not looking back, I would have to agree with Revolutionary and go with a backup and then reformat your hard drive.

If you are planning on keeping Windows around in order to play games, edit movies, etc., then you would probably want to do a dual boot.

It all depends on your situation, but I have a dual boot for now until I learn to live without windows, then I'm pulling the plug. :popcorn:

Edit:



That might not be true for all occasions. While most of your proprietary files (exes, bats, vbs, and any files specific to a window program) will be broken, your media files (jpg, gif, png, mp3, m4a, mp4) should all be fine.

True to that. I didn't want to get into Wine either for the apps/programs.

---

### Post by wojox on 2010-07-27
> **rocka120 said:**
> im mainly just trying to keep WOW. i really dont want to sit there for hours and hours waiting for it to download, lol. but i can
mind if i ask another question without starting a new thread?

Fire away.

---

### Post by aidenscool09 on 2010-07-27
you should be able to run WOW with WINE, it's one of the mainly supported games through WINE, apparently Guild Wars has the best support, but WOW should work fine, best to dual boot to be safe though.

---

### Post by Deersindal on 2010-07-27
> **rocka120 said:**
> im mainly just trying to keep WOW.

In that case, I would suggest a dual boot. You *could* find a guide to doing it through wine.

Or maybe it's easier than I thought. 

[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

---

### Post by rocka120 on 2010-07-27
ok, thanks. i put Ubuntu on my hard disk using Unetbootin and i tried to install it, but everytime i try it says " installation failed. the installer encountered an unrecoverable error. a desktop session will now be run so that you may invetigate the problem or try installing again." then i try to install it from the desktop session and i get to step 4, the part where you partition the hard drive and when i click on forward a message pops up and says "no root file system is defined. please correct this from the partitioning menu" can you help me fix it?

---

### Post by k3lt01 on 2010-07-27
Another option is Windows within a VM within Ubuntu.

---

### Post by Wim Sturkenboom on 2010-07-27
> **rocka120 said:**
> ok, thanks. i put Ubuntu on my hard disk using Unetbootin and i tried to install it, but everytime i try it says " installation failed. the installer encountered an unrecoverable error. a desktop session will now be run so that you may invetigate the problem or try installing again." then i try to install it from the desktop session and i get to step 4, the part where you partition the hard drive and when i click on forward a message pops up and says "no root file system is defined. please correct this from the partitioning menu" can you help me fix it?
Go a step back and create two or three partitions. The one will be the swap partition of 2x size of memory (for a desktop I would limit it to 1GB max), the second one should be a root partition ( identified by **[COLOR="Red"]/[/COLOR]** ) and can take the rest of the space. It's advisable to create a third one in which case the size of the root partition will be somewhere between 20GB and 30GB (20 GB should already give you plenty of space to install extra applications and even 15GB or 10GB might do) and the remaining space will go to /home where users store their data like pictures, emails etc (compare documents and settings in windows).

Reason for creating a separate partition for /home is that a future reinstall will not wipe your data.

I unfortunately can't recall what the screens look like to give more accurate information. Somebody else can jump in there.

---

### Post by fr0styfr0st on 2010-07-27
what i did was i installed Ubuntu then once it was running i went on ubuntu and deleted all the files to do with windows and if you can navigate through your hard drive you should be able to find every thing you are looking for...

Hope this helps

---

