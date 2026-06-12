---
title: "file permissions could not be determined"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by tadcan on 2010-04-13
I have a SD card which I am unable to change the permission for globally. It was previously set with read/write access, don't know how it changed.

When I right click on the file I am told 'file permissions could not be determined'. 

When I try to change the file permission of an single file, am am not allowed.

Edit. I tried to change the permissions as root. The SD cards permissions still cannot be determined. The files are supposed to have read/write access, however when I try to edit them, I'm not able to save the change.

```
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/jquery.js': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/recaptcha.js': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/LXF117_010.jpg': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/LXF117_011.jpg': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/tagline.png': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-most-common-linux-problems_files/LXF117_012.jpg': Read-only file system
chmod: changing permissions of `702A-9012/linux help/Tuxradar webpages/how-fix-m
```

---

### Post by Mykk on 2010-04-13
> **tadcan said:**
> I have a SD card which I am unable to change the permission for globally. It was previously set with read/write access, don't know how it changed.

When I right click on the file I am told 'file permissions could not be determined'. 

When I try to change the file permission of an single file, am am not allowed.

try running your file browser in gksudo

---

### Post by tadcan on 2010-04-13
I put nautilus in to run as root. Then selected the SD card. I can now access the permissions. I am told I have read/write to folders, but not files. I change the files and then close, but it does not keep the setting. 

Tried to delete a folder, it doesn't work.
I have copied the files over to the hard drive and I have full access there.

---

### Post by tadcan on 2010-04-13
not sure if its relevant, gksudo had a few errors 

after leaving gksudo, back to the same response when right click on permissions. 

```
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.1
Error loading document: Error opening file: Permission denied
led: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Error loading document: Error opening file: Permission denied
Error loading document: Error opening file: Permission denied
Error loading document: Error opening file: Permission denied
Error loading document: Error opening file: Permission denied

(gnome-help:2307): Yelp-WARNING **: Failed to load config file: No such file or directory


(gnome-help:2307): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2307): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2307): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnome-help:2307): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

```

---

### Post by Kir_B on 2010-04-13
I too, am having a very similar problem, only with all my usb sticks.

I don't know what brought this on, but it's been going on for the past week or so. I can't drag and drop anything into my usb's, unless I do it with Nautilus operating as root.

(Edit: For what caused this, see post #11, on page 2)

I hope you figure something out. I'll keep looking, but it appears to be a difficult search, because of the shear number of results. Off I go again.

Edit: Oh yeah, my transfer rate is down to about a half of a MB per second. I have encountered this before and it usually sorts it's self out after a reboot or two. Hopefully that works again, but it definitely isn't sorting the other issue out.

Good luck, Kirby :confused:

---

### Post by mcduck on 2010-04-13
If your drive is formatted in FAT or NTFS you won't be able to change the permissions, those are Winbows file systems and lack support for file ownersips & permissions as they are used in Linux.

The permissions for FAT and NTFS drives are set for the whole drive at the time it's mounted.

Edit: if the drive is automatically mounted by Ubuntu, you should have full permissions there. If you don't then you should be looking for what's wrong with the automounting process, not trying to fix the permissions directly on the drive (as that's impossible).

Of course if the drive is formatted in any Linux file system all the normal tools for changing ownership & permisaions will work just as expected. ;)

---

### Post by Kir_B on 2010-04-13
> **mcduck said:**
> If your drive is formatted in FAT or NTFS you won't be able to change the permissions, those are Winbows file systems and lack support for file ownersips & permissions as they are used in Linux.

The permissions for FAT and NTFS drives are set for the whole drive at the time it's mounted.

That's definitely not the issue for me, as the one stick has been completely windows free for six months.

I did loan one to a friend that uses windows and coincidently (I hope), have been having problems since about the time that I got it back.

If I have to format them, I will, if that will even help.

Kirby

---

### Post by mcduck on 2010-04-13
> **Kir_B said:**
> That's definitely not the issue for me, as the one stick has been completely windows free for six months.

I did loan one to a friend that uses windows and coincidently (I hope), have been having problems since about the time that I got it back.

If I have to format them, I will, if that will even help.

Kirby

By "Windows Free" do you mean that you have formatted the drive in Ext2 or other Linux file system? If you borrowed it to your friend who uses Windows, and he was able to use the drive, then it most certainly isn't formatted to any Linux filesystem.

It's not about Windows, it's about FAT and NTFS filesystems, and pretty much every USB drive you'll see is formatted in FAT..

Also, since you mentioned that the problem occurred after borrowing the drive to a friend, if the drive was unplugged without safely removing it in Windows it was probably marked as "unclean" (as unsafely removing the drive might have left it with broken files etc). At least for NTFS, that would make the drive to appear as read-only, might work like that for FAT as well. Plugging the drive in a Windows machine and then safely removing it will marked the drive as clean again and solve that problem. I don't know if there's any easy way to do that from Linux, though.

---

### Post by Kir_B on 2010-04-13
> **mcduck said:**
> By "Windows Free" do you mean that you have formatted the drive in Ext2 or other Linux file system? If you borrowed it to your friend who uses Windows, and he was able to use the drive, then it most certainly isn't formatted to any Linux filesystem.

It's not about Windows, it's about FAT and NTFS filesystems, and pretty much every USB drive you'll see is formatted in FAT..

Also, since you mentioned that the problem occurred after borrowing the drive to a friend, if the drive was unplugged without safely removing it in Windows it was probably marked as "unclean" (as unsafely removing the drive might have left it with broken files etc). At least for NTFS, that would make the drive to appear as read-only, might work like that for FAT as well. Plugging the drive in a Windows machine and then safely removing it will marked the drive as clean again and solve that problem. I don't know if there's any easy way to do that from Linux, though.

Thanks so much for the prompt response mcduck. 

My system is formatted to ext3, according to gparted, but I know that I've formatted at least one (if not all) of my usb's to fat, for use as a linux live usb.

I loaned it to him so he could view a video file that I'd downloaded for him, but to assume that it was improperly removed, is probably a safe assumption. His kid downloaded something to his laptop and then subsequently put some strange music files onto my usb (by strange, I mean assorted genre's from classical to current pop).

My computers hard drive is a dual boot Ubuntu and windoze vista, so I'll have to boot into the windoze side and safely remove them. As much as I hate to do that (I seem to have developed an allergy to M$), I will give it a go.

I'm going to have to find a way to uninstall whatever his kid installed to his laptop, as he's been having nothing but problems ever since and locating the items has proven to be quite challenging, as my three years of windows experience is quickly being purged from my brains cache, of course being replaced with the past six months of linux learning.

Thanks so much for the advice. Very much appreciated. Kirby

---

### Post by Kir_B on 2010-04-13
I just finished booting into windoze, then inserting each stick and safely removing them. I then booted back into my far superior Ubuntu, only to find that I still have the same the exact same problems. The problems are as follows: 

When I right click an item, the "move to trash" entry is greyed out, making it inaccessible.

When I try to delete something from the stick using the delete button on the keyboard, I get the following error:

There was an error deleting
File_name.xxx
Details: 
Error removing file: Permission denied

When trying to add a file to the sticks I get the following error:

There was an error copying the file into /media/usb0.
Details: 
Error opening file '/media/usb0/File_name.xxx': Permission denied

The quest continues. 

Thanks, it was worth the try. ](*,) Kirby  :-k

---

### Post by Kir_B on 2010-04-13
I've just tried my usb sticks in another computer we have, that is running Ubuntu karmic and it isn't plagued with the same issues. The "move to trash" works fine and isn't greyed out. I didn't bother checking to see if copying files to it would work, as I suspect that it's not having any of these issues. I know, I should have tried, but as usual, I'm in a hurry again.

The other issue I noticed, is that when I try to unmount the usb's on the machine that is plagued with issues all of a sudden, is that I'm now required to input my password in order to unmount it. Go figure.

So, I know now that there is something wrong with my system. I suspect that something has been removed from the system, as I updated windoze last week (just to be safe) and following the update windoze wouldn't start up and I then had to repair it. Upon fixing windoze, I got the H E double hockey sticks out of there and booted into Ubuntu, only to find that my system was, for whatever reason, unbootable (I have no idea what happened, as it was working fine less than an hour before.). I then ran a few commands in recovery mode (nothing that should've caused what happened next) and then I rebooted with what appeared to be pure success. Upon getting into my desktop, I noticed a few things missing. Nothing that couldn't be replaced (thankfully), but I was missing a few applications, which I then replaced via the Synaptic package manner.

So, I do believe that this is the cause of all of the current issues that I'm having, now that my memory is serving me (I'd forgotten all about this until I booted into windoze).

I'm not sure what could possibly be missing. Any suggestions would be very, very much appreciated.

Thanks all. Kirby

Edit: I forgot to mention that I'm not plagued with these issues when using Nautilus as root (sudo nautilus).

---

### Post by tadcan on 2010-04-14
The problem turned out to be very simple. The SD card has a little switch that locks the files. Like on the old floppy drive. Opps!

---

