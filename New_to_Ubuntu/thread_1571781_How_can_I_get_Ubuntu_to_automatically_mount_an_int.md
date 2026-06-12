---
title: "How can I get Ubuntu to automatically mount an internal hard drive on boot?"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-09-10
Hello Everybody,

I have just bought and installed a second internal sata hard drive in my computer. It's seen in the BIOS but not mounted automatically on boot up. This is a problem because I used it for Back in Time, which constantly complains that it can't find the disc that it's supposed to back up to.

Is there an easy way to have Ubuntu automatically mount this drive on boot up, like it does with the main drive?

Many thanks, as always,

Charlie

---

### Post by jtarin on 2010-09-10
Not too difficult. Issue a couple of commands and a little editing and you on your way....Oh one thing though...there's a [little documentation]("https://help.ubuntu.com/community/Fstab") you need to read before and then any questions on how to do the aforementioned, please post and we can help guide you through or advise.

EDIT: Can you see the drive in Nautilus file manager?

---

### Post by Peter09 on 2010-09-10
Yes,
you would normally do this by puting an entry in /etc/fstab for the drive in question. You will need to google fstab to find the syntax.
 
I have noticed an application called mountmanager (or similar) in the repositories, which I think does the same job, I have not used it in anger but might be worth a try.
 
 
[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)

---

### Post by sikander3786 on 2010-09-10
You'll have to mount all the partitions individually. What filesystem on the partitions? You can use NTFS Config tool for NTFS and for ext3/ext4, see this link.

[http://ubuntuforums.org/showthread.php?t=1482818](http://ubuntuforums.org/showthread.php?t=1482818)

---

### Post by coffeecat on 2010-09-10
> **sikander3786 said:**
> You can use NTFS Config tool for NTFS

Personally, I would advise people to steer clear of ntfsconfig. I was involved in a thread where ntfsconfig had managed to create an fstab entry for a ntfs partition to a mountpoint already in use and had thus made the system unbootable. :-s

Learning how to edit /etc/fstab is a little bewildering for the beginner, but worth trying. jtarin has already posted a link to the community documentation on fstab, but here it is again:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Charlie Chick on 2010-09-10
Thank you all for your responses. 

To answer some the questions posed: Yes, the drive shows up in COMPUTER and I formatted it as EXT 4, the same as my main drive. I'm not very confident at the command line or altering complex files, hence my question if there was a simple way to do it. If there isn't then I just have to persevere!

---

### Post by sikander3786 on 2010-09-10
> **coffeecat said:**
> Personally, I would advise people to steer clear of ntfsconfig. I was involved in a thread where ntfsconfig had managed to create an fstab entry for a ntfs partition to a mountpoint already in use and had thus made the system unbootable. :-s

Learning how to edit /etc/fstab is a little bewildering for the beginner, but worth trying. jtarin has already posted a link to the community documentation on fstab, but here it is again:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
I try to recommend the tools that I have personally used and that have worked for me. I am using NTFS config tool since Hardy and never had any problems. Thats what the tool is built for and thats why it is in the repositories.

Possible that it might have messed up the fstab sometimes but never for me. And isn't it possible that someone manually editing the fstab, types something wrong and makes his system unbootable? Possibilities are everywhere.

To the OP:

This is what I use for mounting ext4 drives. Simple enough I believe.

> 
First thing i would do is open a terminal, and type
blkid

find the drive and copy the UUID
then open up /etc/fstab with sudo permission and add a line similar to

UUID=<uuid> /place/to/mount ext4 defaults 0 2

that will get it to mount at the mount point (if that place exists) during boot
then a simple

sudo chown <username>:<username> /place/to/mount

should give you the permissions you need to read and write to it
at least thats what i always do, probably better ways to get it done, but its what i know


---

### Post by coffeecat on 2010-09-10
> **sikander3786 said:**
> Possible that it might have messed up the fstab sometimes but never for me. And isn't it possible that someone manually editing the fstab, types something wrong and makes his system unbootable? Possibilities are everywehre.

Oh yes, quite possible. But in this case the OP of the thread in question had never edited /etc/fstab until I showed him what to do in order to undo the damage apparently wrought by ntfs-config. Don't get me wrong - ntfs-config is an excellent idea and probably works well most of the time. But it is not an Ubuntu supported package - it's in the Universe repository. Use with caution.

---

### Post by jtarin on 2010-09-10
Please at least read the documentation so that you have a vague idea of what your doing when you ask for help and someone guides you.

---

### Post by sikander3786 on 2010-09-10
> **coffeecat said:**
> Oh yes, quite possible. But in this case the OP of the thread in question had never edited /etc/fstab until I showed him what to do in order to undo the damage apparently wrought by ntfs-config. Don't get me wrong - ntfs-config is an excellent idea and probably works well most of the time. But it is not an Ubuntu supported package - it's in the Universe repository. Use with caution.

:p We need some good new GUI tools, stable and reliable enough to attract the Windows GUI Users. I know command line and config files are the beauty of Linux but most of the newbies find themselves uncomfortable. At least thats what I think.

---

### Post by jtarin on 2010-09-10
> **Peter09 said:**
>  I have [COLOR="Red"]_not used it in anger_[/COLOR] but might be worth a try.Let us know when you do so we can get out of the way.:shock::lolflag:

---

### Post by Charlie Chick on 2010-09-10
> **jtarin said:**
> Please at least read the documentation so that you have a vague idea of what your doing when you ask for help and someone guides you.

I have. That's why I asked if there was an easier way to do it. I said in my original post that I'm not very comfortable with the command line or editing complex files. 

The other problem is that this is my main computer, used by the rest of the family. I don't want to mess it up and render it unuseable.

---

### Post by jtarin on 2010-09-10
> **Charlie Chick said:**
> I have. That's why I asked if there was an easier way to do it. I said in my original post that I'm not very comfortable with the command line or editing complex files. 

The other problem is that this is my main computer, used by the rest of the family. I don't want to mess it up and render it unuseable.
I was going to tell you an alternate way to mount your drive, not auto but manual but you didn't answer my question. Can you see the drive in the "Nautilus File Manager"side panel?

---

### Post by Charlie Chick on 2010-09-10
> **jtarin said:**
> I was going to tell you an alternate way to mount your drive, not auto but manual but you didn't answer my question. Can you see the drive in the "Nautilus File Manager"side panel?

Sorry, jtarin, I misunderstood you. Yes, it's visible in the panel on the left hand side.

---

### Post by jtarin on 2010-09-10
> **Charlie Chick said:**
> Sorry, jtarin, I misunderstood you. Yes, it's visible in the panel on the left hand side.
Then if you want it available all you need do is left-click on it and it will be on your desktop where it will be accessible or right-click and select mount and it will appear on the desktop where it will be accessible.Right-click on the desktop icon and select unmount when your finished or leave it and it will unmount when you log out or shutdown.This way you can avoid editing any files,reading any documentation or blow up the family computer.Personally I think installing an operating system of which I know little, is much riskier than editing a text file or a couple of commands in a terminal...but thats me...do it and pick up the pieces and try again until I get it right.:lolflag:

---

### Post by Charlie Chick on 2010-09-10
> **jtarin said:**
> Then if you want it available all you need do is left-click on it and it will be on your desktop where it will be accessible or right-click and select mount and it will appear on the desktop where it will be accessible.Right-click on the desktop icon and select unmount when your finished or leave it and it will unmount when you log out or shutdown.This way you can avoid editing any files,reading any documentation or blow up the family computer.Personally I think installing an operating system of which I know little, is much riskier than editing a text file or a couple of commands in a terminal...but thats me...do it and pick up the pieces and try again until I get it right.:lolflag:

That's what I've been doing to date. I was asking if there's a simple way of automating that.

---

### Post by coffeecat on 2010-09-10
> **Charlie Chick said:**
> I was asking if there's a simple way of automating that.

You know, you've identified something that I'm tempted to report as a papercut - the lack of a simple GUI tool to add entries to your fstab, at least for ext* partitions. There is ntfs-config but as you can see there has been a difference of opinion about its reliability. :wink: I believe Opensuse provides this functionality in its Yast utility but I could find nothing in the Ubuntu repositories to suit. I'm afraid it's down to editing fstab manually.

However, if you want help with this - you could look at the link sikander3786 provided, or I could give you the exact line to put in, but you need to go into the terminal first. Sorry! :p

Open a terminal and post the output of these two commands:

```
sudo fdisk -l
sudo blkid
```You will be prompted for your password for the first. It will appear not be going in when you type. It is - that's normal. Copy and paste the output into the message field and enclose the output in code tags by highlighting it and clicking the # icon just above the message field.

Also - important this - we need the contents of /etc/fstab. Double-click on the file and it will open read-only in a text editor. Copy and paste it and also enclose it in code tags.

---

### Post by Charlie Chick on 2010-09-10
Thanks coffeecat. I will do as you ask when I get home. I think that you have understood my problem. It's shame that there's no simple way of doing it, but then by raising these kinds of things we can help Ubuntu to get even better!

---

### Post by seawolf167 on 2010-09-10
I use PySDM to automatically mount my non-boot internal harddrives.

From their website:

"PySDM is a Storage Device Manager that allows full customization of hard disk mountpoints without manually access to fstab.

It also allows the creation of udev rules for dynamic configuration of storage  devices"

And their website itself:

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by jtarin on 2010-09-10
> **seawolf167 said:**
> I use PySDM to automatically mount my non-boot internal harddrives.


Now see...that's a great little tool. Do you use it everyday?:-k

---

### Post by coffeecat on 2010-09-10
> **seawolf167 said:**
> I use PySDM 

Looks interesting, but...

On their webpage, a screenshot shows a partition name as 'hda1' which is a bit prehistoric, and no mention of ext4. I wonder whether there's  been any development since 2005. The version on that page is 0.4.1 which is the version in the Lucid repository.

@seawolf167, will it deal with ext4 partitions which is what the OP needs?

---

### Post by Charlie Chick on 2010-09-10
> **coffeecat said:**
> You know, you've identified something that I'm tempted to report as a papercut - the lack of a simple GUI tool to add entries to your fstab, at least for ext* partitions. There is ntfs-config but as you can see there has been a difference of opinion about its reliability. :wink: I believe Opensuse provides this functionality in its Yast utility but I could find nothing in the Ubuntu repositories to suit. I'm afraid it's down to editing fstab manually.

However, if you want help with this - you could look at the link sikander3786 provided, or I could give you the exact line to put in, but you need to go into the terminal first. Sorry! :p

Open a terminal and post the output of these two commands:

```
sudo fdisk -l
sudo blkid
```You will be prompted for your password for the first. It will appear not be going in when you type. It is - that's normal. Copy and paste the output into the message field and enclose the output in code tags by highlighting it and clicking the # icon just above the message field.

Also - important this - we need the contents of /etc/fstab. Double-click on the file and it will open read-only in a text editor. Copy and paste it and also enclose it in code tags.

Here is the output of the first command:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000b22c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90454   726564864   83  Linux
/dev/sda2           90454       91202     6006785    5  Extended
/dev/sda5           90454       91202     6006784   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab037

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

and here's the output of the second command:

/dev/sda1: UUID="b4c9383f-4fb0-4ab5-b0b6-3534216b9934" TYPE="ext4" 
/dev/sda5: UUID="34d4d216-c204-467b-ab31-2edf93a42b22" TYPE="swap" 
/dev/sdb1: LABEL="Samsung 1TB back" UUID="f7741ae5-505f-44af-a4af-42f38fff906b" TYPE="ext4"

Here's the output of my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b4c9383f-4fb0-4ab5-b0b6-3534216b9934 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34d4d216-c204-467b-ab31-2edf93a42b22 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by jtarin on 2010-09-10
Interesting....you have a floppy drive?
> /dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

---

### Post by Charlie Chick on 2010-09-10
> **jtarin said:**
> Interesting....you have a floppy drive?

Yes, the computer's about 5 years old.

---

### Post by seawolf167 on 2010-09-10
> **coffeecat said:**
> Looks interesting, but...

On their webpage, a screenshot shows a partition name as 'hda1' which is a bit prehistoric, and no mention of ext4. I wonder whether there's  been any development since 2005. The version on that page is 0.4.1 which is the version in the Lucid repository.

@seawolf167, will it deal with ext4 partitions which is what the OP needs?

All pysdm does is provide a GUI for editing /etc/fstab, so ext4, sda1 (as well as hda1), etc. are all up-to-date and working

---

### Post by perspectoff on 2010-09-10
> **sikander3786 said:**
> :p We need some good new GUI tools, stable and reliable enough to attract the Windows GUI Users. I know command line and config files are the beauty of Linux but most of the newbies find themselves uncomfortable. At least thats what I think.

Well you're wrong!

You can't script with GUIs.

GUIs spring up constantly to layer over the command line, not vice versa. That's how X Windows came to exist way back in 1984 (Windows 1.0 didn't come until late 1985).

PS 

Use fstab.

I frankly don't believe in automatic hard drive and automatic partition mounting, because it is a security danger.

If I am working on one partition or hard drive in Linux, I don't want interplay between the Windows partition and the Linux partition, unless I set it up that way (using fstab) or enable it with a password (as is currently done in both Nautilus and Dolphin).

I am currently very happy with the way it is done in Ubuntu.

fstab really isn't that difficult.

Here's how I use it to mount Windows partitions:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29)

---

### Post by jtarin on 2010-09-10
As root backup your /etc/fstab before you start and rename it.
Here's is your new /etc/fstab.Save it to /etc/fstab. Do all work with the sudo(root) command. Reboot. Be happy
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=b4c9383f-4fb0-4ab5-b0b6-3534216b9934 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=34d4d216-c204-467b-ab31-2edf93a42b22 none swap sw 0 0
#Samsung 1TB back 
UUID=f7741ae5-505f-44af-a4af-42f38fff906b  /media/Samsung 1TB back  ext4 defaults,errors=remount-ro 0 2
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

---

### Post by Charlie Chick on 2010-09-10
> **jtarin said:**
> As root backup your /etc/fstab before you start and rename it.
Here's is your new /etc/fstab.Save it to /etc/fstab. Do all work with the sudo(root) command. Reboot. Be happy
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=b4c9383f-4fb0-4ab5-b0b6-3534216b9934 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=34d4d216-c204-467b-ab31-2edf93a42b22 none swap sw 0 0
#Samsung 1TB back 
UUID=f7741ae5-505f-44af-a4af-42f38fff906b  /media/Samsung 1TB back  ext4 errors=remount-ro 0 1
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

If I understand you correctly, I need to replace the contents of my fstab file with the contents you have provided above. Is that correct?

---

### Post by jtarin on 2010-09-10
Yes but look at it again I made one slight change. When done saving fstab and after rebooting you will need to change owner on the location "/media/Samsung 1TB back", so you as a user can write to it unless you only want to write to it as root then leave it unchanged.

```
sudo chown <username>:<username> /place/to/mount
```

---

### Post by jtarin on 2010-09-10
Don't forget to make the mount point before reboot.
```
sudo mkdir /path/to/mountpoint
```

---

### Post by coffeecat on 2010-09-10
@jtarin, there's a problem in the new fstab line:

> **jtarin said:**
> UUID=f7741ae5-505f-44af-a4af-42f38fff906b  /media/Samsung 1TB back  ext4 defaults,errors=remount-ro 0 2

The spaces in the mountpoint '/media/Samsung 1TB back' are not going to parse properly. I know the spaces were in the original partition label, but I don't think that will work.

@Charlie Chick, can I suggest changing that line to:

```
UUID=f7741ae5-505f-44af-a4af-42f38fff906b  /media/Samsung1TB  ext4 defaults,errors=remount-ro 0 2
```... and before you use it, make a mountpoint with:

```
sudo mkdir /media/Samsung1TB
```It won't matter that the mountpoint and partition label have different names. Spaces are often a problem.

**Edit:** @Charlie Chick, there's one more thing you have to do otherwise you won't be able to access that mounted partition with your ordinary account. Unless you do what I describe below, you'll need root authorisation every time you try to write a file - which is inconvenient.

Simply change ownership of /media/Samsung1TB, by...

```
sudo chown yourusername: /media/Samsung1TB
```Substitute your username for 'yourusername' and don't forget that trailing colon. This will work if you are the only user of the machine with only one account, but if you have other accounts more complicated steps are necessary.

---

### Post by jtarin on 2010-09-10
Coffecat I agree with you a 100% and hesitated writing it like that but...I have 1TB external that reads similar to that with spaces and I tried changing the name and had problems and had to change back, but it won't hurt to try. you can always reverse it.I was very surprised when mine was parsed like that.On my Slackware machine it's not like that.

---

### Post by coffeecat on 2010-09-10
> **jtarin said:**
>  you can always reverse it.

@jtarin, agreed. I posted an edit just as you were posting. All about ownership. Could you check what I posted and say whether you agree? :)

---

### Post by jtarin on 2010-09-10
Of course i agree...i posted the same thing earlier. :)

---

### Post by Charlie Chick on 2010-09-10
Thank you all for your help - much appreciated!

---

### Post by coffeecat on 2010-09-10
> **jtarin said:**
> Of course i agree...i posted the same thing earlier. :)

#-o:oops:

Nurse! Nurse! Can you see where I left my spectacles? 

:wink:

---

### Post by jtarin on 2010-09-10
And was it a success?

---

### Post by jtarin on 2010-09-10
> **coffeecat said:**
> #-o:oops:

Nurse! Nurse! Can you see where I left my spectacles? 

:wink:
I think you stepped out for beans and weenies for that one.:D

---

### Post by coffeecat on 2010-09-10
> **jtarin said:**
> beans and weenies

You know the one about two nations separated by a common language? I had to look that up.  Our nearest equivalent would be bangers and beans.

[http://www.bbcgoodfood.com/recipes/1275/bangers-and-beans-in-a-pan](http://www.bbcgoodfood.com/recipes/1275/bangers-and-beans-in-a-pan)

---

### Post by jtarin on 2010-09-10
Bangers did come to mind , but didn't know if my recollections were correct and too lazy to look it up.:)

EDIT:recipe link makes me hungry

---

### Post by baddnady23 on 2010-09-10
Couldn't you use ```
media/Samsung\ 1TB 
``` in the fstab line?

---

### Post by jtarin on 2010-09-10
What would that do for you?

---

### Post by baddnady23 on 2010-09-10
> **jtarin said:**
> What would that do for you?

The forward space would allow for the space in the name of the mount point, correct?

---

### Post by coffeecat on 2010-09-10
Why would you want a space in a mountpoint?

---

### Post by jtarin on 2010-09-10
Mine is not laid out like that and I have spaces in my mount point, so therein lies the_____________(extrapolate your own).

---

