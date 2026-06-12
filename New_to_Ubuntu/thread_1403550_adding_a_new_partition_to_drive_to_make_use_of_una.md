---
title: "adding a new partition to drive to make use of unavailable space?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-10
The drive I'm using right now is 160 gb.  Due to some bios limitation only 137 GB are available.  Although when I ```
sudo fdisk -l
``` linux recognizes the full capacity of the drive.

I don't know exactly why it works like this but after a great deal of research with some complicated explanations about LBA or something I hope you will trust me that this is the case.  Also there are no BIOS updates for this computer I've already checked.

So the solution suggested to me was to pop the drive out of this laptop and connect it to a desktop via an external case.  Then partition it into two 80gb drives or some other amount that adds up to 160.  I was told that linux should recognize this as 2 different drives and I should be able to use the total capacity.

Well I finally picked up a means to connect this drive to my desktop.  Before I pop it out I want to know if there is anything I should do to make sure I don't mess up what I already have on here.  

I have an external I can connect to this via USB but I don't know how to save an image of this disk.

I'm also looking for tips on the partitioning. Will linux recognize the partitions as two drives?  Is this going to work?

---

### Post by oldfred on 2010-02-10
I thought the BIOS limit was for booting. That the boot partition had to be inside the 137 limit. When the limit was smaller, older still computers it was the main reason to have a separate /boot partition. As long as you partition to boot from is inside the 137 limit you should be ok.

---

### Post by hortstu on 2010-02-10
Fred,

That may be the case... I'm not sure.  I plan on trying to get this done today and looking for all the advice I can get first.

---

### Post by mwcrowley on 2010-02-10
First things first, back up your data.  If you want to go as far as getting a disk image [http://clonezilla.org/clonezilla-live/]("http://clonezilla.org/clonezilla-live/") is a good way to go.
Otherwise, backup data, boot a livecd, use gparted to shrink the partition below the LBA limitations, create a new second partition and format it, ext3 is a good stable choice.  Enjoy.

---

### Post by hortstu on 2010-02-10
[QUOTE=mwcrowley]First things first, back up your data. If you want to go as far as getting a disk image [http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/) is a good way to go.
Otherwise, backup data, boot a livecd, use gparted to shrink the partition below the LBA limitations, create a new second partition and format it, ext3 is a good stable choice. Enjoy.[/QUOTE]

Is this the easiest way to do a backup image?  I do have an external USB with plenty of room on it.

---

### Post by oldfred on 2010-02-11
I rarely do a full image as /home has data and the hidden setting for just about everything. If you had to customize something like xorg, samba, network etc there may be a few config files that you would want to save. I also export my installed applications list so I can recreate that easily. Then I can do a full reinstall and recreate my system easily. But if you are not sure a full backup is safer, if you have lots of room on another drive you can just cp or rsync everything.

---

### Post by mwcrowley on 2010-02-11
I would agree with oldfred.  A disk image would take time.  Backup home directory, installed applications list, and if you have edited any config files take a moment and back them up.  As a blanket approach, backup your /etc directory, it doesn't contain all your config files, but between your home directory and the /etc directory, that should cover most.

And remember to back up all the hidden files in your home directory.  If you just copy and paste the visible files in your home directory, you'll skip the hidden config files.

---

### Post by hortstu on 2010-02-11
Thanks fred and mw,

I should have mentioned I'm a bit of a newb so I need a more in depth explanation or a link that does that.  This computer doesn't have too much on it at this point... I just don't want to have to resetup everything if something is lost or damaged.

---

### Post by oldfred on 2010-02-11
Here is some info on package backup. If you have not had to edit any config files that is good and then you do not have to worry. When I edit config files I make a copy in a /home location so my copy of home includes those.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

 All of above boils down to this file which I copy into /home also occasionally. Excludes those listed to uninstall
    dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections  > ubuntu-files
which includes everything.

---

### Post by egalvan on 2010-02-11
The size limitations are basically for software that uses BIOS calls to the hard drive.
Obviously the BIOS does this, so when initial booting, the entire drive cannot be seen. 
This is why it's more properly called the BIOS limit.
(OK, so Microsoft uses the BIOS, so it also has this limit...
but that's another kettle of fish)

Linux software does not use BIOS calls,
 so Linux DOES NOT HAVE THIS LIMIT.

Once you boot GRUB, or any kernel, you have FULL access to the drive.

So using a LiveCD and GRUB is perfectly safe, and will allow you to manipulate the partitions as needed.


Of course, manipulating partitions always has it's own risks,
so

**MAKE BACKUPS **of data you cannot stand/afford to lose.

---

### Post by egalvan on 2010-02-11
> **oldfred said:**
> I thought the** BIOS limit was for booting. That the boot partition had to be inside the 137 limit. **When the limit was smaller, older still computers it was the main reason to have a separate /boot partition. As long as you partition to boot from is inside the 137 limit you should be ok.

Yes, absolutly, kinda-sorta...:)

The boot code that depends on the BIOS calls can only see the drive that is inside the BIOS limits.

The MBR boot loader is one such piece of software,
and GRUB stage1.5 was like this.
GRUB stage2 does not use BIOS.

Yes, in the older, more limited days, It was much easer to have the boot files, such as GRUB and /boot, inside the BIOS limits.
100MB-200MB was usually more than enough.
This left room for Microsoft products if needed...


These tricks allowed me to use tera-byte sized drives on old machines with BIOS limited to 528MB...
(More than one Microsoftie's jaw hit the floor in those days...)

---

### Post by egalvan on 2010-02-11
And if anyone is interested,
here is a good website for more info on the DRIVE LIMITS.

[http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm](http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm)

---

### Post by hortstu on 2010-02-11
egalvan,

when I "sudo fdsik -l" I get 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfd06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris
```

but when I start up gparted it says...

sda1 = 143.25
sda2 = 5.8
sda5 = 5.8

total = almost 154... so I guess I'm accessing all 160 then.  I guess it's a good thing I asked or would have really been wasting time here.  While I have your help though are these partition sizes adequate?  Any suggestions for partition management would be appreciated.

---

### Post by hortstu on 2010-02-11
> **egalvan said:**
> And if anyone is interested,
here is a good website for more info on the DRIVE LIMITS.

[http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm](http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm)

Thanks egalvan,

That is the clearest explanation I've ever seen on this.

---

### Post by oldfred on 2010-02-11
If you get 5 responses on recommended partitioning schemes you will only get about 10 different versions.:D

For the first 3 years of using Ubuntu I just had root & swap with a smallish shared NTFS as I was dual booting windows XP. Now I have a separate /home and /data.

root only needs to be 10-20GB without your data or if you have home separate. Swap can be 2GB or your RAM size if you want to hibernate.

[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by hortstu on 2010-02-11
Thanks for those two links old fred... one better than the next and definitely what I need at this stage.

---

### Post by egalvan on 2010-02-13
> **hortstu said:**
> egalvan,

when I "sudo fdsik -l" I get 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfd06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris
```

but when I start up gparted it says...

[B]sda1 = 143.25
sda2 = 5.8
sda5 = 5.8
[/B]
total = almost 154... so I guess I'm accessing all 160 then.  I guess it's a good thing I asked or would have really been wasting time here.   are these partition sizes adequate?  Any suggestions for partition management would be appreciated.

OK, even worse :)   

sda2 is an **EXTENDED** partition, that is 5.8GB in size.

sda5 is a **LOGICAL** partition, that is fully contained **INSIDE** sda2.

Extended partitions can be thought of a container.
Logical partitions reside "inside" extended partitions.

An extended partition can have many logical partitions "inside".

so the "total" is closer to 149GB.

Don't worry too much. fdisk says you have a 160GB drive,
and software and hardware and techies and engineers and marketing types have different ways of "measuring" bytes. :) 

And as oldfred says, 5 answers will net you 10 different opinions.
It's a good setup you have at the moment, and time will show you what you need and want.
Experience is a great teacher.

Cheers

Ernest Galvan

---

### Post by hortstu on 2010-02-13
Thanks egalvan,

I've learned a lot about partitions over the last 24 hours... apparently not enough though.

---

