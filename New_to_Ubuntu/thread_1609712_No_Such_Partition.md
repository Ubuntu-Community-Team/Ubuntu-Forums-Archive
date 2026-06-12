---
title: "No Such Partition"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by MadDogTen on 2010-10-30
Ok, So I am REALLY new at Ubuntu, and do stupid things like this on a Monthly bases and I usually just reinstall Windows 7, however I have important files/programs on there installed making me not want to reinstall.

Now to the Problem:
Today while installing a Game, I didn't have enough space to install it on Windows 7, and I had 100 GB for Ubuntu (Didn't think I would ever use 100 GB for Windows, but I did), So I deleted the Ubuntu Partition and added it to the Windows Partition. After Installing the Game I decided I would restart my Computer, and when it was starting I got the "No Such Partition" error.

Right now I'm using the computer with the Ubuntu Live CD.

So, My question is, is there anyway to fix this without having to Reinstall Ubuntu?

Oh, and I don't have a Windows Disk. 
I had the Newest Ubuntu Version Installed (10.10 I think it was).

---

### Post by Rex Bouwense on 2010-10-30
I read your post twice.  What happens when you try to boot your computer?  Is it correct to say that you cannot boot either Windows 7 or Ubuntu 10.10?

---

### Post by xjesse on 2010-10-30
The Live cd has an application called gparted. Use it to format the partition to NTFS so Windows can read it.

---

### Post by MadDogTen on 2010-10-30
> **Rex Bouwense said:**
> I read your post twice.  What happens when you try to boot your computer?  Is it correct to say that you cannot boot either Windows 7 or Ubuntu 10.10?
Sorry about that.

I deleted the Ubuntu Partition to get the space that was used for it, and now Cannot boot Windows 7. 

When I turn on the computer I get "No Such Partition".

---

### Post by MadDogTen on 2010-10-30
> **xjesse said:**
> The Live cd has an application called gparted. Use it to format the partition to NTFS so Windows can read it.
The Windows Partition is already NTFS.

---

### Post by xjesse on 2010-10-30
I can never edit my post anymore, why?
Anyways, forget what I said. It seems you have no boot loader. You were relying on GRUB2 to boot up your Windows.

Now, unless you have an Windows CD which I know you said you don't, I recommend just reinstalling Ubuntu once again along side Windows. This time however, give Ubuntu maybe 20GB or less. Ubuntu doesn't need a whole lot that way you have a boot loader *and* you will still be dual booting. Does this make sense? I hope so. :lol:

---

### Post by MadDogTen on 2010-10-30
> **xjesse said:**
> I can never edit my post anymore, why?
Anyways, forget what I said. It seems you have no boot loader. You were relying on GRUB2 to boot up your Windows.

Now, unless you have an Windows CD which I know you said you don't, I recommend just reinstalling Ubuntu once again along side Windows. This time however, give Ubuntu maybe 20GB or less. Ubuntu doesn't need a whole lot that way you have a boot loader *and* you will still be dual booting. Does this make sense? I hope so. :lol:
Ya, I understand.

I guess I will if thats the only way Possible without the Windows Disk (It was quite annoying having to Choose between the both yo boot).
Thanks!

---

### Post by fleder on 2010-10-30
Just to get us an overview, could you post the console output of the command
```
sudo parted /dev/sda print
```...assuming that /dev/sda is the hard drive which this all is about, i.e. the one your Windows partiton is located on?

You can open the console with CTRL+ALT+T or with ALT+F2 and typing in ```
gnome-termial
```fleder

EDIT: xjesse's suggestion seems good, try that one first.

---

### Post by Rex Bouwense on 2010-10-30
> **MadDogTen said:**
> Sorry about that.

I deleted the Ubuntu Partition to get the space that was used for it, and now Cannot boot Windows 7. 

When I turn on the computer I get "No Such Partition".

It sounds like you deleted GRUB when you deleted the Ubuntu partition.  Without that. you cannot boot.  You can try to reinstall Ubuntu on a smaller partition to get GRUB back.  Hopefully, it will let you boot both Windows Ubuntu.
xjesse beat me to it.  I type with two fingers.

---

### Post by MadDogTen on 2010-10-30
I'm just screwing up left and right.

So, I was going to Re-install Ubuntu like you said.The Install Started, and Not long after it had an error. (I'm pretty sure it was because the disk was dirty.) So, I cleaned the Disk, Started it all back up, then it was showing the previous 20 GB it tried to use for the Failed Install.

I deleted the Partition, tried to add it back to the windows one, and it had an error. So I just said forget it and Tried to Install it Again on the windows Partition and Deal with that problem later.

However, now the 1st option I had before to Install Side by Side is gone.



Me and computers just don't go together.

---

### Post by MadDogTen on 2010-10-30
Ok, So are there any other ways then having to install Ubuntu?

---

### Post by MadDogTen on 2010-10-30
> **fleder said:**
> Just to get us an overview, could you post the console output of the command
```
sudo parted /dev/sda print
```...assuming that /dev/sda is the hard drive which this all is about, i.e. the one your Windows partiton is located on?

You can open the console with CTRL+ALT+T or with ALT+F2 and typing in ```
gnome-termial
```fleder

EDIT: xjesse's suggestion seems good, try that one first.
Ok did that.

Here are the results:
Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs
 2      106MB   192GB  192GB   primary  ntfs         boot
 4      192GB   213GB  20.2GB  primary  ext4
 3      213GB   320GB  107GB   primary  ntfs


Number 4 being the one I talked about 2 posts above.
#2 is My Windows Partition. #3 My Storage Partition. #1 is the system reserve.

---

### Post by Quackers on 2010-10-30
If all you want is to get Windows booting you can do it from the Ubuntu Live CD by installing lilo.
Have a look at post number 3 here

[http://ubuntuforums.org/showthread.php?t=1581328&highlight=repair+windows+bootloader+lilo](http://ubuntuforums.org/showthread.php?t=1581328&highlight=repair+windows+bootloader+lilo)

---

### Post by MadDogTen on 2010-10-31
My Friend let me Borrow his Windows 7 Disk, but when I tried to use it to repair mine, it said it was for a diff version of windows 7 and wouldn't work.

> **Quackers said:**
> If all you want is to get Windows booting you can do it from the Ubuntu Live CD by installing lilo.
Have a look at post number 3 here

[http://ubuntuforums.org/showthread.php?t=1581328&highlight=repair+windows+bootloader+lilo](http://ubuntuforums.org/showthread.php?t=1581328&highlight=repair+windows+bootloader+lilo)
I did that, and because  I know have the Windows Disk and was able to Access the Command Prompt, I did his Windows 7 Fix.

However, Now when starting my computer I get "BOOTMGR is missing".

---

### Post by MadDogTen on 2010-10-31
I'm screwed. Plain and Simple.

I found other Forums on the Newest Problem, tryed what they said, and now Iv messed it up even more.

I was told to bypass the part where is said it isn't the right verion of windows because it would still work. So I did, then ran the repair.

Now, my Windows Partition, or what used to be my Windows Partition, is labled as "Unknown" and I cannot access it.

When I start my compter, I get "Requiered Device is Inaccessible", Status 0XC0000225

and even better, I think this Ubuntu disk is now messed up from switching it with the Windows disk so much, because now It says there is an error and goes to the Ubuntu Live part of the disk and when I click the button to install Ubuntu nothing happens (I guess I can try cleaning it again).


So, I won't do anything else to try to fix it until one of you guys answer. Also, IDK if anyone is willing/if there is a way, but if there is a way to "take control" of my computer from your end, and you have the time, tell me, so you can see what you can do.

---

### Post by Mark Phelps on 2010-10-31
> **MadDogTen said:**
> I did that, and because  I know have the Windows Disk and was able to Access the Command Prompt, I did his Windows 7 Fix.

However, Now when starting my computer I get "BOOTMGR is missing".

Did you try it only once? Asking because the Win7 repair procedure often requires three passes -- that's right, three --before it fixes everything.  If you don't do all three, you're left in an intermediate state.  

So, if you didn't do three passess, boot from the Win7 CD/DVD and try it again -- three times.

---

### Post by MadDogTen on 2010-10-31
> **Mark Phelps said:**
> Did you try it only once? Asking because the Win7 repair procedure often requires three passes -- that's right, three --before it fixes everything.  If you don't do all three, you're left in an intermediate state.  

So, if you didn't do three passess, boot from the Win7 CD/DVD and try it again -- three times.

I did it the first time and it asked to restart and got that error, and Tried it again and that time it said it couldn't fix it.



However, I have a (Slightly) Good Update, I WAS able to Install Ubuntu on the 20GB partition, However, I still have the same problem with Windows when trying to Load it.

---

### Post by Quackers on 2010-10-31
Does the grub menu show at startup?

---

### Post by MadDogTen on 2010-10-31
> **Quackers said:**
> Does the grub menu show at startup?
Not anymore.

A deferent error showed up after I tried Windows Repair, Better enplaned in a Above post.

But as I said, I got Ubuntu installed and it seams to allow Dual Boot, however Clicking on the Windows boot still comes up with that error.

---

### Post by MadDogTen on 2010-11-03
I'm still having the problem if anyone can help.

---

