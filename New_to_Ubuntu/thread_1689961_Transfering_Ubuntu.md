---
title: "Transfering Ubuntu"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by beew on 2011-02-17
Hi,

I have an installation of Ubuntu 10.10 on an external hard drive. I want to transfer (or rather, create a clone) of this system (not just the data files) to the internal drive of some Pc. I think that would involve creating a copy of the whole system in the external drive and restore it in the PC. What is the simplest way to go about it? I would want to do it in such a way that the backup should be small,--so that it doesn't copy unused space in the partition.
Also the system is formatted in ext4 and apparently it is not supported by clonezilla.

Since I haven't done this before and it seems quite involve a step by step help would be much appreciate.

Thanks in advance.

---

### Post by davidmohammed on 2011-02-17
welcome to the forums

clonezilla will work for you - it does support ext4

try this [how-to]("http://www.wikihow.com/Use-Clonezilla") to get you going.

---

### Post by sydbat on 2011-02-17
> **beew said:**
> Hi,

I have an installation of Ubuntu 10.10 on an external hard drive. I want to transfer (or rather, create a clone) of this system (not just the data files) to the internal drive of some Pc. I think that would involve creating a copy of the whole system in the external drive and restore it in the PC. What is the simplest way to go about it? I would want to do it in such a way that the backup should be small,--so that it doesn't copy unused space in the partition.
Also the system is formatted in ext4 and apparently it is not supported by clonezilla.

Since I haven't done this before and it seems quite involve a step by step help would be much appreciate.

Thanks in advance.Similar to the answer I gave in your other thread, just use the LiveCD and make sure everything is unmounted before copying from the external drive to the internal drive.

---

### Post by beew on 2011-02-20
> **sydbat said:**
> Similar to the answer I gave in your other thread, just use the LiveCD and make sure everything is unmounted before copying from the external drive to the internal drive.

Sorry you may have been thinking about someone else, I don't remember having another thread on this and I don't remember reading your answer. I just did a search and nothing shows up. But then maybe I am being forgetful..

---

### Post by sydbat on 2011-02-21
> **beew said:**
> Sorry you may have been thinking about someone else, I don't remember having another thread on this and I don't remember reading your answer. I just did a search and nothing shows up. But then maybe I am being forgetful..Yup...it was you...[http://ubuntuforums.org/showthread.php?t=1689956](http://ubuntuforums.org/showthread.php?t=1689956)

---

### Post by beew on 2011-02-22
That one is about deleting xp in a dual boot, but this thread is about moving Ubuntu from an external hard drive to an internal one. I am not sure it is the same question.

In any event I don't see how your advice on that thread apply here. The Ubuntu installation is on a different drive and the internal hard drive is going to be wiped.

On that thread, you said delete Windows and reformat the ntfs partition in ext3 and then grow Ubuntu into it, I am not sure that can be done either because the ntfs partition is immediately to the left of the Ubuntu boot partition (/) and so the only way to expand Ubuntu would be by moving the left end of the / partition to the left  and gparted wants that expanding the / partition this way might result in the system not bootable (expanding the right end of the / partition to the right at the expanse of the /hone partition is fine, I have done it many times) I am simply going to delete Windows and put some other distro on the vacant partition instead of expanding the Ubuntu one.

In any event that has nothing to do with this thread, as far as I can tell.

---

### Post by sydbat on 2011-02-22
> **beew said:**
> That one is about deleting xp in a dual boot, but this thread is about moving Ubuntu from an external hard drive to an internal one. I am not sure it is the same question.

In any event I don't see how your advice on that thread apply here. The Ubuntu installation is on a different drive and the internal hard drive is going to be wiped.

On that thread, you said delete Windows and reformat the ntfs partition in ext3 and then grow Ubuntu into it, I am not sure that can be done either because the ntfs partition is immediately to the left of the Ubuntu boot partition (/) and so the only way to expand Ubuntu would be by moving the left end of the / partition to the left  and gparted wants that expanding the / partition this way might result in the system not bootable (expanding to the right end of the / partition to the left at the expanse of the /hone partition is fine, I have done it many times) I am simply going to delete Windows and put some other distro on the vacant partition instead of expanding the Ubuntu one.

In any event that has nothing to do with this thread, as far as I can tell.It does...really.

That thread - format the old NTFS to ext3/4 then copy / paste the Ubuntu / partition to it. Then remove the old / and grow /home into it. This is what I did without any problem. Make back ups first!

This thread - Copy / paste the / and /home from the external to the internal HDD. Linux is not Windows so it will read the new hardware and run fine...as opposed to Windows which is hardware dependant.

---

### Post by beew on 2011-02-22
> **davidmohammed said:**
> welcome to the forums

clonezilla will work for you - it does support ext4

try this [how-to]("http://www.wikihow.com/Use-Clonezilla") to get you going.


OK, apparently clonezilla images the entire partition instead of just the part with data on it. Partimage is more efficient in that it would create image only on the used part, but strangely it doesn't support ext4 (thus making it pretty useless for recent Linux distros unless you go out of your way to format the hard drive as ext3). 

Does anyone know something that works like Partimage in that regard but supports ext4?

Thanks.

---

### Post by beew on 2011-02-22
> **sydbat said:**
> It does...really.

That thread - format the old NTFS to ext3/4 then copy / paste the Ubuntu / partition to it. Then remove the old / and grow /home into it. This is what I did without any problem. Make back ups first!

This thread - Copy / paste the / and /home from the external to the internal HDD. Linux is not Windows so it will read the new hardware and run fine...as opposed to Windows which is hardware dependant.


You mean copying and pasting the whole partition?? Sorry, that is rather new to me. :)

P.S. I understand Linux is hardware independent (for the most part), have been running the external installation as a portable on different computers for a while.

---

### Post by HermanAB on 2011-02-22
Howdy,

If the two machines are identical, then you can use clonezilla or dd and netcat.

If the two machines are different, use remastersys.

---

### Post by sydbat on 2011-02-22
> **beew said:**
> You mean copying and pasting the whole partition?? Sorry, that is rather new to me. :)No problem. When I did it I got a bit confused too.

So...it isn't the whole partition that gets moved with the copy / paste...just the files. 

Everything has to be unmounted to do the formatting. 

Therefore, you can move an install from eg. a 250GB drive to a larger or smaller drive without too many problems (as long as the total files fit).

I have subsequently found, however, that moving /home is easiest, then do a clean install of the OS on /. I followed this tutorial before doing anything - [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366).

EDIT - HermanAB has a couple of good suggestions too.

---

### Post by beew on 2011-02-22
> **HermanAB said:**
> Howdy,

If the two machines are identical, then you can use clonezilla or dd and netcat.

If the two machines are different, use remastersys.

There is only one machine. The isntallation copied from has no machine, it is in an external drive. I plug it in different machines, boot into it and can run Ubuntu from there. It works kind of like a live usb except it is a full install and I can do kernel update and other system upgrade on that. Now I want to make a copy of this and make it a permenant install in one of my laptops.

---

### Post by bill516 on 2011-02-22
Clonezilla should work nicely for you.  It has for me.  If you would like to watch a video that will show you how it works, go to the Clonezilla website, "Related Articles" and then click "Clonezilla Image of Hard Disk".  That will give you a pretty good idea of just how Clonezilla can be used to do what I understand you want to do.

Clonezilla is a darned good tool to have around!

---

### Post by beew on 2011-02-22
> **sydbat said:**
> No problem. When I did it I got a bit confused too.

So...it isn't the whole partition that gets moved with the copy / paste...just the files. 

Everything has to be unmounted to do the formatting. 

Therefore, you can move an install from eg. a 250GB drive to a larger or smaller drive without too many problems (as long as the total files fit).

I have subsequently found, however, that moving /home is easiest, then do a clean install of the OS on /. I followed this tutorial before doing anything - [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366).

EDIT - HermanAB has a couple of good suggestions too.


Thanks will check this out. But if you just copy the files will the structure (I don't really know what structure) be properly preserved?

I know the normal way would be to back up the home partition and reinstall the OS. But in this case the /home partition really isn't worth saving, I have no crucial data so I am planning to wipe it (the internal drive) anyway.  it is the / partition  from the external drive with all the installed software and the right versions ( I use a lot of ppas and have a few things install from source) that I want to move over.

---

### Post by sydbat on 2011-02-22
> **beew said:**
> Thanks will check this out. But if you just copy the files will the structure (I don't really know what structure) be properly preserved?

I know the normal way would be to back up the home partition and reinstall the OS. But in this case the /home partition really isn't worth saving, it is the / partition with all the installed software and versions that I want to move over.Structure should be preserved.

And even though the /home partition may not have personal files on it, it does have configuration files for your installed apps in /. Saving the hidden files (.) is a good idea.

And the link I have in my previous post tells how to make a file of all your installed apps that can then be re-added to a new install easily (with dependencies and everything).

EDIT - reading your edited post, I understand why you want to just move / to the internal drive. I am not sure if the link I posted covers PPA retention. Remastersys might be a better bet.

---

