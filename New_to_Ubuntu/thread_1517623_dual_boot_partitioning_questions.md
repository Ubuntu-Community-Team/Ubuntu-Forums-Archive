---
title: "dual boot partitioning questions"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by sprocket10 on 2010-06-25
I've finally decided to give Ubuntu 10.04 a go w/ a win7/ubuntu dual boot setup (first time linux user). I know I want to have my partitions setup something like this:

win7 (~100GB)
shared storage (~120GB) - for music, photos, vids, etc.
Swap (~2GB)
Ubuntu 10.04 (~ 98GB)

I've got my win7 partition shrunk to the right size. Now, I'm using the partition tool in the ubuntu liveCD to setup my other partitions, but I don't know some of the settings:

For instance:
For my Ubuntu 10.04 partition I have:
- Primary
- Installed at the end of "free space"
- 98GB size
- Ext4 filesystem
- / (mount point)

My concern is regarding the setting for the remaining partitions. I'm doing this all in the ubuntu installer, btw:

Swap:
- Logical?
- Installed at the end of "free space"
- 2GB size
- "Swap"

Storage:
- Logical?
- NTFS
- 120GB size

Are they "Logical" ? I'm pretty confident the swap is from my searches, but I don't know about the storage area. Any other settings I should know about? I keep exiting the install when I reach another setting I don't know about.

---

### Post by mk1w86 on 2010-06-25
In my own setup the Windows 7 and the Ubuntu root partitions are primary and everything else (swap + storage partitions) is logical.

However, you would probably be fine if all your partitions were logical, you might as well do this for the data and swap partitions in case you want more in future (you cannot have more than four primary partitions).

---

### Post by mikechant on 2010-06-25
Any Ubuntu partitions or Windows data partitions will work quite happily as primary or logical partitions, but you are limited to a maximum of four primary partitions. However, one primary partition can be an extended partition containing a number of logical partitions.

In my view, the most flexible scheme is to have the first primary partition for windows (or the first two if you have a windows recovery partition), then to have the rest of the disc as one extended partition. This partition in your case would contain three logical partitions - the shared data partition, the main ubuntu partition and the swap partition. Later you could repartition the extended partition to have (say) extra logical partitions for a new ubuntu release or a seperate /home.

---

### Post by sprocket10 on 2010-06-25
Well....good news! The dual boot seems to be working fine. Last time I tried it, grub and the windows bootloader interfered and I had to jump ship on ubuntu. Anyway, I've had a few misfires w/ lucid lynx: I select Ubuntu from the grub list, and it will glitch - display red and blue pixels across the top of my screen and I'll have to manually shut off and restart it. Hopefully this will happen less and less.

After I installed ubuntu, I installed about 190MB of updates, and now I have 2 ubuntu selection options in the grub list. I'm guessing these are the kernel editions. How do I take the old option off the list? I don't want the list to keep growing longer. Or is it that big a deal / cause me a headache ?

---

### Post by mk1w86 on 2010-06-25
> **sprocket10 said:**
> Well....good news! The dual boot seems to be working fine. Last time I tried it, grub and the windows bootloader interfered and I had to jump ship on ubuntu. Anyway, I've had a few misfires w/ lucid lynx: I select Ubuntu from the grub list, and it will glitch - display red and blue pixels across the top of my screen and I'll have to manually shut off and restart it. Hopefully this will happen less and less.

After I installed ubuntu, I installed about 190MB of updates, and now I have 2 ubuntu selection options in the grub list. I'm guessing these are the kernel editions. How do I take the old option off the list? I don't want the list to keep growing longer. Or is it that big a deal / cause me a headache ?

It is probably worth keeping the older kernel entries in case you need to boot an older version for whatever reason.  If you find the long list does cause you problems though you can uninstall the older kernels from your system and their boot entries will automatically be removed, it is worth keeping one kernel previous to your current version though. ;)

---

### Post by sprocket10 on 2010-06-25
ok. will keep them. 

Next issue to resolve:
I still haven't got the storage partition figured out. Aren't I supposed to use the gparted tool or something. When I open Administration -> Disk Utility I see my storage partition, but I cannot format it. I'm not sure what to do now :confused:

---

### Post by Kixtosh on 2010-06-25
> **sprocket10 said:**
> ... After I installed ubuntu, I installed about 190MB of updates, and now I have 2 ubuntu selection options in the grub list. I'm guessing these are the kernel editions. How do I take the old option off the list? ...Wow! Well, you are a lot more daring than I was for my first install, what with sizing the partitions manually and all that! That still gives me a headache when I think of it!

Anyway, the 190MB of updates is fairly standard, and yes, as you guessed, it did include a new kernel. I eventually remove the old entries from grub by uninstalling them using the synaptic package manager (I'll be doing it myself in a minute, but some Xubuntu areas are a bit different from regular Ubuntu).

1) You'll be asked for your password, then, 
2) the Synaptic Pkg Manager window will appear. 
3) In the "search" box, type "linux-image".
4) Then click on the "S" to the left of the "Package" column. This should order the results with those installed listed first.
5) The different Linux kernel images that you see in the grub list shoud be right there. You can click on the unwanted ones.
6) A menu list will appear, and you can either check them for removal, or for complete removal (I'm not sure which is best ... sorry).
7) Click the apply button on the top of your screen. It should be removed.

Best of luck!

---

### Post by mk1w86 on 2010-06-25
> **sprocket10 said:**
> ok. will keep them. 

Next issue to resolve:
I still haven't got the storage partition figured out. Aren't I supposed to use the gparted tool or something. When I open Administration -> Disk Utility I see my storage partition, but I cannot format it. I'm not sure what to do now :confused:

Gparted is not installed by default, to install it run:

> sudo aptitude install gparted

You can then find it under System > Administration > GParted

I have never really used Disk Utility before and have only just realised now you can even use it to edit partitions. :-o

---

### Post by sprocket10 on 2010-06-25
hmmmm....now I got another issue. I guess I need to change some partitions?

It won't let me format this unused space as NTFS.

Since my storage area is going to be a "logical" partition, why is it assuming I'm making a "primary" one?

---

### Post by oldfred on 2010-06-25
Once you have formated your NTFS partition you will want to permanently mount it to make it easy to use.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

You create a mount point and edit fstab. 
```
mkdir /home/fred/shared
```
This is my fstab entry for a mount of shared in my home.

```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

```
After updating fstab run this if no errors it just returns your to terminal.
```
sudo mount -a
```

I moved my firefox & thunderbird profiles to my shared partition so I have the same bookmarks, emails etc in both windows and Ubuntu.

---

### Post by Kixtosh on 2010-06-25
There may be issues trying to use Gparted to edit partitions while the system is running, since some of the partitions will be in use at the time, so you might want to use the Ubuntu LiveCD for this (Gparted is on that). If it takes too long to load the LiveCD (it does on my older laptops), you could download Puppy Linux instead: it has Gparted too, and because it never needs to be installed (it's intended to run only in RAM), it's very fast to start up.

Puppy is a useful tool to have around anyway in my opinion, since you never have to install it, or add it to GRUB. Anytime you boot from from your CD drive, it will start up automatically, before GRUB starts. If the Puppy disk is not in the CD drive, GRUB will start normally. If you allow Puppy to save it's small files to the hard drive on exiting, after the first time using it, it will find it's saved settings in those tiny compressed files and will start even faster every other time you might want to use it for Gparted, or anything else.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

I seen it suggested frequently that you defragment your Windows partitions at least three times before modifying them, by the way.

---

### Post by sprocket10 on 2010-06-25
Using the LiveCD didn't work either. I got the same error as when I ran GParted in Ubuntu. :mad:

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> hmmmm....now I got another issue. I guess I need to change some partitions?

It won't let me format this unused space as NTFS.

Since my storage area is going to be a "logical" partition, why is it assuming I'm making a "primary" one?

From the attached thumbnail you have already used up all 4 possible primary partitions, that is what is stopping you.

Try right clicking the swap partition, select swapoff, then delete it, then delete the extended partition, then recreate the extended taking up all unallocated space. In the new extended partition create the NTFS and swap partitions as required. Should work OK.

You should be able to do this without booting from the cd, as only swap is affected by the work you're trying and is not totally necessary to have a swap partition (but is desirable).

Edit: remember to turn swap back on after this and edit the swap partition uuid in /etc/fstab to the new one before rebooting the installation.

---

### Post by sprocket10 on 2010-06-25
Ok, I tried that, but for some reason, whenever I make the extended partition, it automatically creates a 2.34 MB partition outside the extended partition. I'm not sure why it does that, but that's not what I'm trying to do!

Screenshots show before and after

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> Ok, I tried that, but for some reason, whenever I make the extended partition, it automatically creates a 2.34 MB partition outside the extended partition. I'm not sure why it does that, but that's not what I'm trying to do!

Screenshots show before and after

No its only 2 **M**B (ie very small) and is to do with aligning the partitions to cylinder boundaries, its OK to leave it.

Edit: I originally read 2 MB as 2GB but your post isn't showing as having been editted. Was it?

---

### Post by sprocket10 on 2010-06-25
Yeah, it was an edit. I realized it later. Oops :P

Should I leave the "round to cylinders" box unchecked?

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> Yeah, it was an edit. I realized it later. Oops :P

Should I leave the "round to cylinders" box unchecked?

Try, but I'm not sure if it has any bad consequences. I usually tolerate such small amounts of unallocated space "just in case".

---

### Post by sprocket10 on 2010-06-25
Well, I think I got it. But, now there's another 7.5 MB space at the end of the extended partition.

---

### Post by yetiman64 on 2010-06-25
That looks workable however before rebooting,

1st turn on swap if you already haven't,

In terminal

```
sudo blkid | grep swap && gksudo gedit /etc/fstab
```enter password where necessary,

In the terminal highlight the uuid for swap, right click and select copy.
 In gedit highlight the existing uuid for swap and right click and select paste. **Ensure no qotation marks are highlighted when doing this.**
Save /etc/fstab file and close gedit.

This updates the uuid for the swap partition and will prevent an error on your next boot.

---

### Post by wilee-nilee on 2010-06-25
> **sprocket10 said:**
> Well, I think I got it. But, now there's another 7.5 MB space at the end of the extended partition.

If it's working don't mess with it. What happened here is that in trying to preformat the Ubuntu install you didn't put Ubuntu inside a extended partition, if you had then you would have been able to have that shared partition an primary ntfs, which it should be.

A screenshot of your screenshot the sda5 is inside a extended sda4 when the whole Ubuntu should have been inside sda4 with the swap sda5.
[ATTACH]161541[/ATTACH]

---

### Post by sprocket10 on 2010-06-25
Well, I guess next I need to make the shared partition mounted permanently? Now, I've read oldfred's post but I don't understand it yet. I was also reading this for help: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) on setting up my dual boot. I think all that's left is migrating my data/files into the storage partition.

It seems like I have too many things mounted. Is it normal to be able to access the windows partition like I can now? I really only care about being able to see the storage partition while in ubuntu.

wilee-nilee: I'm guessing there's no option to correct it other than reinstalling ubuntu?

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> It seems like I have too many things mounted. Is it normal to be able to access the windows partition like I can now? I really only care about being able to see the storage partition while in ubuntu.

Yes its normal Ubuntu has ntfs support natively.

> Well, I guess next I need to make the shared partition mounted  permanently?```
sudo apt-get install ntfs-config
``` when installed go to System > Administration > NTFS Configuration Tool and run it, select the NTFS partitions needed (recommend you **don't** tick win 7 partition) and enable write support for internal drives. This will put the required entries into fstab for you to automatically mount the NTFS partition on each boot (much safer than manual editing etc).

re wilee-nilee's comments, I agree your setup is not optimal (but it is workable). If you consider reinstalling Ubuntu later on. consider as a setup

sda1 Dell Utility (as is)
sda2 Win 7       (as is)
sda3 NTFS Storage (Primary)
sda4 Extended (remainder of drive -Primary)

within sda4
sda5  Swap
sda6 /
sda7 /Home  (it's a good idea to have a separate home partition for future reinstalls etc)

On the installer when reinstalling Ubuntu choose the manual (Advanced) option to allocate the partitions etc.

---

### Post by sprocket10 on 2010-06-25
As far as the "/" and the "/home" partitions, does ubuntu install on one or the other or both?

I'm gonna redo the install and get it right this time!



One more thing:
Since ubuntu natively recognizes NTFS, all I should have to do is drag and drop my windows 7 stuff into the shared partition, right? Then reattach all the pointers (not sure the technical term): such as iTunes music library, etc.

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> As far as the "/" and the "/home" partitions, does ubuntu install on one or the other or both?

I'm gonna redo the install and get it right this time!

The automatic installer only creates /, but if you use gparted and create /home as well, you will have to use the Advanced option during install (actually I'm glad to hear you're willing to do the reinstall, as I believe you'll likely get a much better end result). It will install system files to / and your personal files to /home (separates the 2)

Just remember not to touch sda1 and sda2, delete the whole backend from the live cd and do the partitioning and the reinstall in one fell swoop, when you reboot Win 7 will be back in the menu.

> One more thing:
Since ubuntu natively recognizes NTFS, all I should have to do is drag  and drop my windows 7 stuff into the shared partition, right? Then  reattach all the pointers (not sure the technical term): such as iTunes  music library, etc.Yes both Win 7 and Ubuntu can access the partition contents. 

The term is "shortcuts" in Win7 and "links" in Ubuntu. 

Do your dragging and dropping of contents from Windows though, I recommend you don't access the Windows system partition from Ubuntu (particularly writing or moving files,  only reading is OK, as it can cause errors on the OS drive in Windows - just a precaution mind).

---

### Post by sprocket10 on 2010-06-25
How big should the "/" and "/home" partitions be?

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> How big should the "/" and "/home" partitions be?

A good figure for / is ~10 GB (could be as low as 5GB but I always allow for system expansion/additions etc over time).  

/home will depend on how much you store there, anywhere from 5 to 30 GB (you could tend towards the lower end with a shared NTFS partition (maybe 15 to allow for doing work in Ubuntu). Really does depend on how much you are going to work in Ubuntu. 

Just remember if you allow too little now it's a big job to sort it out later.

---

### Post by sprocket10 on 2010-06-25
Alright, how does this look?

---

### Post by yetiman64 on 2010-06-25
IMO that's an extremely big / partition, you'd probably be better to reduce it to 10 or 12 and increase the /home to take up the rest (that'd give you ~7 to 9 GB more storage when working in Ubuntu). Even on a very big install you'd be likely to not use more than about 7 or 8 GB.

Ubuntu tends to not need near as much as Windows installs for the system to get the same or similar capability.  

But the layout looks good now and you could leave it as is if you really wish to.


Edit: jsut noted NTFS is sda4 and extended is sda3. Would be better to get them around the other way.

---

### Post by sprocket10 on 2010-06-25
Is there a way to easily change this or will I have to reinstall again? I couldn't get the installer to format a NTFS by itself, I had to use Gparted afterward to create the NTFS partition.

---

### Post by yetiman64 on 2010-06-25
> **sprocket10 said:**
> Is there a way to easily change this or will I have to reinstall again? I couldn't get the installer to format a NTFS by itself, I had to use Gparted afterward to create the NTFS partition.

If that's after a full install then leave it, it is OK. I thought you might be on a live cd and the  partitions were blank; in that case it's very easy to change them to a neater layout. 

What you've got is perfectly OK. Don't even consider the / size comments if you've done a full reinstall.

Do both systems boot OK from the grub bootscreen?

---

### Post by sprocket10 on 2010-06-25
Whew! OK, I'm glad cuz I really don't wanna reinstall. And yes, both OS's load correctly. This is so much better than last time I tried Ubuntu. I guess there was some kind of fix in the updates I downloaded since last time. I'm so glad because that was such a headache.

It still stinks that I can't go all-Ubuntu yet, but I'll keep trying. I still need windows for: gaming and dvd/bluray backup. I sure hope Ubuntu keeps gaining momentum!

On a side note: I'm likely going to have to break out my Fortran book for a college class :shock:. Is there a standard Fortran compiler I can use in Ubuntu?

---

### Post by yetiman64 on 2010-06-26
> Fortran book for a college class :shock: Fortran is some sort of foreign language isn't it ;), no seriously I'll leave that to someone who knows it :). You could do a search in Synaptic Package Manager though (use fortran as search input) and look for compilers as a starting point.

BTW you can if feeling adventurous resize partitions with the OS in from a live cd, best left till you're a bit more confident with Ubuntu and partitioning in general. If you try this sort of thing, do full data backups first as problems can occur.

Glad to hear it's working for you. Enjoy your Ubuntu and cheers for now, yetiman64.

---

### Post by perspectoff on 2010-06-26
I'm going to throw in my 2 cents.

I no longer keep data on the computer itself, but on an external network hard drive. 

Over the years I have accumulated many OSs on many computers, and probably now have 20 partitions with 15 or so OSs. 

There is a safety factor in keeping data on a central server that can be accessed (and given access controls) by/for many different computers and OSs.

Also, should a particular OS or computer be compromised, there is an added level of security by keeping sensitive data separately. 

A 1 Tb hard drive is only about 150 bucks these days, and can be shared between several Windows computers/OSs and linux OSs.

Further, it is portable and can be taken from place to place.

In the end this became more desirable to me than having a storage partition on the same hard drive as the OS...

My (now slightly dated) methods of partitioning, editing GRUB bootloader config files, and chainloading bootloaders is at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

and

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

