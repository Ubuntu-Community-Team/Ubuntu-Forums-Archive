---
title: "[SOLVED] Triple Boot Gone Wrong"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-21
Yesterday i tried to install OSX through Windows. Anyway to keep it short it rebooted my computer (install went wrong, so didn't install), and threw the following error upon boot up 

> Grub Loading Stage1.5

Grub Loading, please wait.....
Error 17  

Thanks to members on here I was able to fix that and reinstall Ubuntu and get it working correctly. 

Now upon trying to boot into Windows XP Home I get the following error: 
> Windows could not start because the following file is missing or corrupt: 

<Windows root>\system32\hal.dll. Please re-install a copy of the above file.

Now I'm not sure how to fix this one? Is it possible to get the file in Ubuntu and transfer? Or do I have to use Windows XP Recovery CD (which I cant because my netbook doesnt have a DVD/CD drive)?

I think its the Ubuntu gods telling me something. Get rid of Windows XP and just boot Ubuntu.:)

Final question is can you boot OSX from Ubuntu using a iso and Leopard HD install helper? 

Sorry if this is the wrong location for this thread, dont know where to put it.

---

### Post by bumanie on 2008-12-21
I cannot answer the question about OSX - never used it, nor any other apple OS. 

The error you are getting has probably been caused by the partition number of your windows installation being changed in boot.ini whilst you were attempting the triple boot. Are you able to mount the windows drive from ubuntu? If so please post the output of > sudo fdisk -l so that we can see which partition windows is on and tehn go about editing boot.ini or altering the partition number of windows to reflect what is in boot.ini

---

### Post by RookieUbuntuUser58 on 2008-12-21
I don't see an option in Ubuntu's Gparted disk manager to mount Windows partition. When I was reinstalling Ubuntu I did see that option in the installer though. If thats what your talking about. 

Heres the screenshot (Windows is the one with * under boot):

[[IMG]http://img187.imageshack.us/img187/7378/screenshotsi5.png[/IMG]](http://img187.imageshack.us/my.php?image=screenshotsi5.png)
[[IMG]http://img187.imageshack.us/img187/screenshotsi5.png/1/w640.png[/IMG]](http://g.imageshack.us/img187/screenshotsi5.png/1/)

---

### Post by bumanie on 2008-12-21
No that's not I was meaning exactly, however the screen shot you have sent gives me an idea of one problem that you will encounter. It's probably related to the problem as posted - windows is now within an extended partition - windows does not like booting from anything other than a primary partition and then prefers to be on the first partition - I assume it was originally on the first partition and is now in the extended partition due to the partitioning donw when trying to setup a triple boot. So now the main issue is getting windows out of the extended partiton. If you do that, it is likely that the original problem you posted will disappear (as in, I suspect boot.ini will then match teh partition number). Unfortunately, one cannot just delete an extended partition without deleting everything that is in the extended partition. Do you have an external hard drive large enough to copy windows to?

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **bumanie said:**
> No that's not I was meaning exactly, however the screen shot you have sent gives me an idea of one problem that you will encounter. It's probably related to the problem as posted - windows is now within an extended partition - windows does not like booting from anything other than a primary partition and then prefers to be on the first partition - I assume it was originally on the first partition and is now in the extended partition due to the partitioning donw when trying to setup a triple boot. So now the main issue is getting windows out of the extended partiton. If you do that, it is likely that the original problem you posted will disappear (as in, I suspect boot.ini will then match teh partition number). Unfortunately, one cannot just delete an extended partition without deleting everything that is in the extended partition. Do you have an external hard drive large enough to copy windows to?

I dont have a external HDD but if needed I will try to get one later this week, if all else fails. 

The funny thing is when I go to GParted the Windows partition is not under the extended partition. It looks like this:

Unallocated.......3.91GB 
/dev/sda2.........39.07GB (Windows Partition)
/dev/sda1.........22.90GB (Extended Partition)
Then in the extended partition you have
/dev/sda5.........21.42GB (Linux)
/dev/sda6..........1.39GB (Linux Swap)
/dev/sda7.........94.10GB (Linux /boot)
Then out of the extended partition again:
unallocated.......87.17GB

---

### Post by bumanie on 2008-12-21
Can you post a screenshot of the gparted GUI; fdisk -l certainly shows the extended partition as being sda1 and depite the order you have posted, gparted is showing the extended partition as being sda1 also - look at the drive letters not the order. A screenshot of gparted GUI will give confirmation.

---

### Post by albinootje on 2008-12-21
> **boost3d23 said:**
> I don't see an option in Ubuntu's Gparted disk manager to mount Windows partition. When I was reinstalling Ubuntu I did see that option in the installer though. If thats what your talking about. 

Heres the screenshot (Windows is the one with * under boot):

Can you mount the XP-partition manually ?
```

sudo mkdir /media/xp
sudo ntfs-3g /dev/sda2 /media/xp -o force

```
Post any errors.

---

### Post by logos34 on 2008-12-21
> **bumanie said:**
> It's probably related to the problem as posted - windows is now within an extended partition ...

look again--windows is on a primary, sda2.  The extended, sda1, starts at 5611

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **bumanie said:**
> Can you post a screenshot of the gparted GUI; fdisk -l certainly shows the extended partition as being sda1 and depite the order you have posted, gparted is showing the extended partition as being sda1 also - look at the drive letters not the order. A screenshot of gparted GUI will give confirmation.

Ahh I know what you mean now. How about I delete the sda1 extended partition and reinstall Ubuntu (since I have it on a USB Flash and its a easy install). Will that move Windows back to sda1 and get it working?

Heres the GParted screenshot:
[[IMG]http://img291.imageshack.us/img291/301/screenshotzt7.png[/IMG]](http://img291.imageshack.us/my.php?image=screenshotzt7.png)
[[IMG]http://img291.imageshack.us/img291/screenshotzt7.png/1/w640.png[/IMG]](http://g.imageshack.us/img291/screenshotzt7.png/1/)

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **albinootje said:**
> Can you mount the XP-partition manually ?
```

sudo mkdir /media/xp
sudo ntfs-3g /dev/sda2 /media/xp -o force

```
Post any errors.

This is what happens when I do that:

[[IMG]http://img253.imageshack.us/img253/7351/screenshot1ys9.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshot1ys9.png)
[[IMG]http://img253.imageshack.us/img253/screenshot1ys9.png/1/w640.png[/IMG]](http://g.imageshack.us/img253/screenshot1ys9.png/1/)

---

### Post by logos34 on 2008-12-21
Can you mount windows (see albinootje above)?

Why not check the boot.ini file--one of the causes of hal.dll error is wrong "DEFAULT" partition(x) entry...looks like you may originally have had a recovery partition in front of windows, so maybe that's the problem.  try the easiest things first

---

### Post by logos34 on 2008-12-21
there's a typo:

sudo **mount -t **ntfs-3g /dev/sda2 /media/xp -o force

---

### Post by albinootje on 2008-12-21
> **boost3d23 said:**
> This is what happens when I do that:


Good! :)
Now please check the content of /media/xp in the file-manager -> Places.

---

### Post by thefiestysoldier on 2008-12-21
try and use your windows cd to repair(not install)XP.

---

### Post by albinootje on 2008-12-21
> **logos34 said:**
> there's a typo:

sudo **mount -t **ntfs-3g /dev/sda2 /media/xp -o force

Typo ? No, check : ```
man ntfs-3g
```

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **albinootje said:**
> Good! :)
Now please check the content of /media/xp in the file-manager -> Places.

So was the original code you told me correct? Or is logos34 correction right?

By checking the contents of /media/xp in the file-manager -> Places; do you mean click on places then OS_install (new file created on desktop after following your code)? If so what do I look for or edit to get this working?

---

### Post by albinootje on 2008-12-21
> **boost3d23 said:**
> So was the original code you told me correct? Or is logos34 correction right?

By checking the contents of /media/xp in the file-manager -> Places; do you mean click on places then OS_install (new file created on desktop after following your code)? If so what do I look for?

It was okay like this.
In Places go to -> Computer -> Filesystem -> media -> xp

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **albinootje said:**
> It was okay like this.
In Places go to -> Computer -> Filesystem -> media -> xp

Okay done. Its the same thing that was in the file OS_Install on my desktop (that was created by your code). What do I do here?

BTW I owe all of you guys Thanks when this is done.:)

---

### Post by bumanie on 2008-12-21
Ah, the windows partition is not within the extended partition after all - this is good. I did miss the start numbers as logos34pointed out - sorry about that.

Not sure whether that will help. As windows is on the first primary partition, it should boot - may be the error is real. Windows often gives this error if has had a partition number changed - I don't know what partition it was noted as before and it will be different between how ubuntu sees it and how windows sees it. Can you mount the windows drive from places?
PS: Sorry, I'm at work and get interrupted at times.

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **bumanie said:**
> Ah, the windows partition is not within the extended partition after all - this is good. I did miss the start numbers as logos34pointed out - sorry about that.

Not sure whether that will help. As windows is on the first primary partition, it should boot - may be the error is real. Windows often gives this error if has had a partition number changed - I don't know what partition it was noted as before and it will be different between how ubuntu sees it and how windows sees it. Can you mount the windows drive from places?

Before Windows was sda1. Now as you see in the screenshots it is sda2. 

As for the mounting thing. I followed the code posted on here and entered the file albinootje suggested and I see all of my Windows stuff there (probably what you are refering to). Also the code created a file on my desktop named OS_Install with all my XP stuff (same thing albinootje instructions lead me to). Not sure what to do next.

---

### Post by bumanie on 2008-12-21
Is what you can see text or file icons?

---

### Post by caljohnsmith on 2008-12-21
boost3d23, that "missing hal.dll" is usually a classic symptom of when Windows boot.ini file points to wrong partition, which would likely be your situation since Windows is sda2. Please post the contents of your boot.ini file located in the sda2 Windows root partition.

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **bumanie said:**
> Is what you can see text or file icons?


Files with a few .bat, .sys, and one boot.ini file. Also all my Windows folders like Documents and Settings, Windows, and Program Files.

---

### Post by albinootje on 2008-12-21
> **boost3d23 said:**
> Before Windows was sda1. Now as you see in the screenshots it is sda2. 

As for the mounting thing. I followed the code posted on here and entered the file albinootje suggested and I see all of my Windows stuff there (probably what you are refering to). Also the code created a file on my desktop named OS_Install with all my XP stuff (same thing albinootje instructions lead me to). Not sure what to do next.

You wrote earlier on that you got a Windows error about a missing file.
I suggest you ask some Windows knowledgeable people (not me) for help how to fix this and/or use a search-engine to find out more about this.

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **caljohnsmith said:**
> boost3d23, that "missing hal.dll" is usually a classic symptom of when Windows boot.ini file points to wrong partition, which would likely be your situation since Windows is sda2. Please post the contents of your boot.ini file located in the sda2 Windows root partition.

Is this it? I found this in the location albinootje told me to go to (In Places go to -> Computer -> Filesystem -> media -> xp ).

[[IMG]http://img525.imageshack.us/img525/10/screenshot2ds6.png[/IMG]](http://imageshack.us)
[[IMG]http://img525.imageshack.us/img525/screenshot2ds6.png/1/w640.png[/IMG]](http://g.imageshack.us/img525/screenshot2ds6.png/1/)

---

### Post by logos34 on 2008-12-21
change both instances of partition(2) to partition(1)

use the nano editor in the terminal

---

### Post by caljohnsmith on 2008-12-21
> **logos34 said:**
> change both instances of partition(2) to partition(1)

use the nano editor in the terminal
+1. Windows doesn't count extended partitions, so your boot.ini file should use partition(1), boost3d23. :)

---

### Post by bumanie on 2008-12-21
Yeah, change the (2) to (1) in both places and it should boot again.

---

### Post by RookieUbuntuUser58 on 2008-12-21
It worked. I got to thank all of you guys for the help. I love these forums, so helpful. Thanks again, all of you get thanks points.:)

And I'm done trying to triple boot OSX after this experience.

---

### Post by caljohnsmith on 2008-12-21
Glad to hear Windows works now; cheers and hope you don't run into any other major problems with Windows or Ubuntu. :)

---

