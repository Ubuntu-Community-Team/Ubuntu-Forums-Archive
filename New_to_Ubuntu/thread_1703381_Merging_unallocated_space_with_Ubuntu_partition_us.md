---
title: "Merging unallocated space with Ubuntu partition using Gparted"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Dry Lips on 2011-03-09
I've previously had a dual boot system with XP and Ubuntu,
and now I've finally decided to have a “clean” Ubuntu-only system. 
(Relatively speaking, I still use Wine and VirtualBox...) 
1. I've deleted the Windows partition using Disk Utility
2. I've updated the grub, writing "sudo update-grub" from
the Terminal and everything is fine so far. 
3. Now I want to be able to merge my unallocated space 
with my Ubuntu partition, but I've never used Gparted before,
so I'm stuck... Of course I use a LiveCD to boot from, 
so that the HDD isn't mounted. Could anyone help a noob out?

---

### Post by wizard10000 on 2011-03-09
If you've got the resources to do it it might be a better idea all the way around to reinstall, Dry Lips  ;)

I've got a couple reasons for suggesting this.  First, your installation doesn't have a separate /home partition and you'll probably find that useful at some point.  Here's what I'd suggest -

If you've got an external hard drive or a big USB flash drive just back up your home directory to that so you don't lose anything.  While you're doing that, do this before you're done -

```
dpkg --get-selections > installed-packages.txt
```

and copy that file to your thumb drive or external hard drive as well.  Remember that an untested backup isn't a backup at all, so make sure you can read the files on the backup media and that everything you want is there.

Next, boot from a live CD and run the installer.  Partition manually this time, please - and set the disk up this way:

sda1:  Ubuntu root partition doesn't need to be more than about 30gb.

sda2:  This should be the extended partition and should take up the rest of the disk.  Now we're gonna make partitions inside the extended partition.

sda5:  Swap partition.  For performance reasons you want this as close to the outside edge of the disk as you can get it.  You want the swap partition at least the size of installed RAM if you ever want to hibernate the machine - and disk space is cheap.  You don't need to go too big, though - your current 10gb swap partition is probably a bit too big - and there's no sense in wasting disk space.

sda6:  This should be your home partition and during the install should be mounted as /home.  All your data goes here and if you're not gonna install another OS you can make this partition take up the rest of the disk.  If you decide you want to do something else later you can always shrink this partition.

Okay, now you install Ubuntu, using sda1 as the root partition and sda6 as /home.  Let the installer run and when your shiny new OS is running you can restore your data.

Last but not least, put the installed-packages.txt back on the system and do this -

```
sudo dpkg --set-selections < installed-packages.txt && sudo apt-get dselect-upgrade
```

This will read your package selections from the text file and install them for you.

Hope this helps -

---

### Post by Dry Lips on 2011-03-09
> copy that file to your thumb drive or external hard drive as well. Remember that an untested backup isn't a backup at all, so make sure you can read the files on the backup media and that everything you want is there.My home directory is encrypted, would that complicate the issue? Also, I don't have
an external HDD, so I would have to use 3-4 DVD's to make the backup.

Thank you for replying!

---

### Post by wizard10000 on 2011-03-09
> **Dry Lips said:**
> My home directory is encrypted, would that complicate the issue? Also, I don't have
an external HDD, so I would have to use 3-4 DVD's to make the backup.

Thank you for replying!

No - the files would be unencrypted when you copied them from the encrypted drive.

cheers -

---

### Post by Dry Lips on 2011-03-09
Also, I see you're running Kubuntu... Would that “dpkg --get-selections > installed-packages.txt» thing work if I switched to Kubuntu in the process?

---

### Post by wizard10000 on 2011-03-09
> **Dry Lips said:**
> Also, I see you're running Kubuntu... Would that “dpkg --get-selections > installed-packages.txt» thing work if I switched to Kubuntu in the process?

Yes, but it'd also install all your GNOME packages.  If you're gonna switch desktop environments it'd be easier to just make a list of the stuff you want to reinstall.  Since most GNOME packages have a KDE equivalent the list would probably be pretty short.

---

### Post by Dry Lips on 2011-03-09
All right, I'm not entirely familiar with the differences
between Ubuntu/Kubuntu,  you can install exactly the
same software that you run with Ubuntu, right? Gimp,
Scribus, Blender, Inkscape, Oracle VM VirtualBox, 
Sigil, Bluefish, Bleachbit, Eric Python IDE, Skype, etc. 
Have you got the equivalent of Synaptic in Kubuntu?

When I first installed Ubuntu I also clicked on the 
advanced setup, because I wanted to create my 
partition manually, but I didn't figure it out, being
used to creating partitions in the windows installer... 
So I just used the idiot-safe setup...

---

### Post by Hakunka-Matata on 2011-03-09
@wizard10000:

Re: Post #2 , Brilliant, Thank You!

---

### Post by Dry Lips on 2011-03-09
Isn't it just possible to resize the sda5 partition 
to include the unallocated space? I've just found
out that I've got more stuff in my home directory
than I initally thought... What are the advantages 
of having a separate root partition?

---

### Post by wizard10000 on 2011-03-09
> **Dry Lips said:**
> Isn't it just possible to resize the sda5 partition 
to include the unallocated space? I've just found
out that I've got more stuff in my home directory
than I initally thought... What are the advantages 
of having a separate root partition?

The advantage is in having a separate /home partition, not a separate root  ;)

With a separate home partition you can reinstall the OS without blowing away all your data.

You could install a 30gb partition as sda1, resize sda2 and sda5 and go that way but I'd use a live CD to blow away just about everything that wasn't your home directory first.  Ideally you'd only have one directory in sda5, the one that matches your username.

But - you shouldn't be repartitioning *anything* without backing up your data first  ;)

---

### Post by MartyBuntu on 2011-03-09
> **Dry Lips said:**
> Isn't it just possible to resize the sda5 partition 
to include the unallocated space?


Good luck. I've never had success using **MERGE** on ext formatted drives.

---

### Post by Dry Lips on 2011-03-09
> But - you shouldn't be repartitioning *anything* without backing up your data first

Well, I've got the really important stuff backed up, 
but I found out that all my music, clip-art, etc, takes
up quite some space. This is stuff I *could* download 
again if the the home directory was messed up, but if
I managed to resize the partition and keeping that 
stuff intact, it would save me a lot of time. 

Let me see if I understand what you are suggesting:

**1**. Boot into LiveCD
**2**. Create a primary partition (for the root)
**3**. Once you have a primary partition, you can use the
rest of the unallocated space to resize sda2/5. 
(Is the reason why I seemed to be unable to resize 
sda5 that there is no sda1 on the HDD?)
**4**. Deleting the old root on sda5 (Would I have to use
sudo -something?)
**5**. Reinstalling on sda5, but that would also potentially
mess things up since there are a home directory there
from before...

Again, thank you for helping!

---

### Post by Dry Lips on 2011-03-09
Another thing... As I wrote earlier, my home is encrypted. 
Would I be able to access the old home directory at all?

---

### Post by wizard10000 on 2011-03-09
> **Dry Lips said:**
> Another thing... As I wrote earlier, my home is encrypted. 
Would I be able to access the old home directory at all?

This is an excellent point.  I don't *think* you'd be able to access your old home directory at all if you reinstalled the OS.  Decrypt the directory before you move a buncha stuff around  ;)

The reason you couldn't resize sda5 is that it's contained within sda2 - you have to resize sda2 first.

---

### Post by Dry Lips on 2011-03-09
> The reason you couldn't resize sda5 is that it's contained within sda2 - you have to resize sda2 first.Excactly, that explains it... Sda2 couldn't be resized at
all from within Gparted... Seems as if I need to look into
how to decrypt stuff... Do you have any hints on this?

---

### Post by wizard10000 on 2011-03-09
I'm afraid not - as I don't use encrypted folders but I'm sure someone else here can help out.

cheers -

---

### Post by Dry Lips on 2011-03-09
All right, thanks a lot for your help anyway. I'll do a little research
on encryption, and I'll post updates here when I have done the actual
repartitioning and have installed the OS again. Actually I now see that
having a separate root partition, is really helpful when you're doing a 
reinstall. I've been drooling over Kubuntu, (Kubuntu is so... shiny ;)) 
so I think this is perhaps a good opportunity to be able to check it out. 
I can then easily go back to Ubuntu if I don't find my way around it. 

Cheers!

---

### Post by Dry Lips on 2011-03-09
I've found a way to backup my home directory. 
I created the a partition for the root, plus a small partition
 that I used to copy the content of my home.
 
 But when I use Gparted, I'm not able to unmount sda2,
 so I'm not able to resize it... How come?

---

### Post by coffeecat on 2011-03-09
> **Dry Lips said:**
> But when I use Gparted, I'm not able to unmount sda2,
 so I'm not able to resize it... How come?

The partition sda2 is not actually mounted but locked because the logical swap partition inside it is in use by the live CD. Right-click on sda6, the swap partition, and choose 'swapoff'. Then you will be able to resize the extended partition sda2.

---

### Post by Dry Lips on 2011-03-09
I see, I thanks a lot! :)

---

### Post by wizard10000 on 2011-03-09
> **coffeecat said:**
> The partition sda2 is not actually mounted but locked because the logical swap partition inside it is in use by the live CD. Right-click on sda6, the swap partition, and choose 'swapoff'. Then you will be able to resize the extended partition sda2.

Now I learned something today.  I didn't know a live CD would use a swap partition if it found one  :)

---

### Post by coffeecat on 2011-03-09
> **wizard10000 said:**
> Now I learned something today.  I didn't know a live CD would use a swap partition if it found one  :)

Not just one. It'll grab two if it finds two. Possibly more. :) I think it simply latches onto every swap partition it can get its hands on. This is a common gotcha for people trying to resize an extended partition using the live CD. It's worth knowing about.

---

### Post by Dry Lips on 2011-03-10
**Update**:
All right, that swap drive thing solved it!
Last night I booted into the LiveCD and begun
resizing the partition. When it was done this 
morning, I could boot up as before, all the data
seems intact so far... :D

Now I've got two small partitions that is
unused so far, in addition to the big one. What I plan
to do is to set up Kubuntu on one of them, and when
I've figured out which flavour that'll be my main
OS, I'll do a reinstall with the root in a separate partition.
The partition that then will be left, I plan to use to test
out other distros. In other words, I'll be setting up a 
dual boot Linux/Linux system from now on. Perhaps I'll 
need help on this, but I'll save that for another thread:
[http://ubuntuforums.org/showthread.php?t=1704416](http://ubuntuforums.org/showthread.php?t=1704416)
[B]
Wizard10000[/B] & **Coffeecat**: Thank you so much for all
your kind advice!

---

### Post by Dry Lips on 2011-03-10
To sum all of this up, for the benefit of noobs like myself
 who might encounter the same problem:
 
  HOW TO REMOVE WINDOWS AND MAKE ALL REMAING SPACE AVAILABLE FOR UBUNTU. 

 **1.** Backup all you want to keep from your old windows partition.
 **2.** Delete it, using for instance System>Administration>Disk Utility
 **3.** Open a terminal and type “sudo update-grub”.
 **4.** Backup your Ubuntu home folder.
 **5.** Boot using an Ubuntu LiveCD (or memory stick)
 **6.** Open Gparted (System>Administration>Gparted)
 **7.** Right-click on the swap partition and choose “swapoff”.
 **8.** Select the extended partition, choose Partition>Resize/Move
 **9.** Drag it to encompass the unused space. Click apply (green check)
 **10.** Repeat point nine for your partition that is within the extended partition.  
 Point ten takes time, (several hours, depending on the size of your HDD).
 In addition, it could theoretically mess up your system so that you would have reinstall  
 your OS (you should have backed up important stuff before you attempt to do this).
 

 Voilà!

---

### Post by Hedgehog1 on 2011-03-10
Excellent Summary.

Thanks for the complete list of steps, that helps a lot for future readers.  And me, too.

***The Hedge***

:KS

p.s. The 'swapon'/'swapoff' can be a real bugger, can't it?

---

### Post by Dry Lips on 2011-03-11
> **Hedgehog1 said:**
> Excellent Summary.

Thanks for the complete list of steps, that helps a lot for future readers.  And me, too.

***The Hedge***

:KS

p.s. The 'swapon'/'swapoff' can be a real bugger, can't it?

Aye, I was totally blank! ;)

----

Another thing I didn't mention: [B]The summary above is
intended for removing Windows XP on a true Windows 
Xp/Ubuntu double boot system, (*not* wubi), 
where Ubuntu is installed on [/B]*one*[B] (extended) partiton 
and windows on the other. 
[/B]

---

