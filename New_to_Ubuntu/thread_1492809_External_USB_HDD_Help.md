---
title: "External USB HDD Help"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Jayjay402 on 2010-05-25
Hi,
I've used ubuntu a couple of times when my pc has broke, just as a live session to recover files and stuff.
I recently decided to get rid of windows completely and install ubuntu on it's own. I installed from an 9.04 edition and have upgraded to 10.04 lts.
I have a fairly old pc, amd athlon 3200, 768mb ram and two dvd drives. I have ubuntu installed on an internal 40gb hdd and have an 80gb hdd for other stuff, all of this is pata/ide drives.

I just bought an external 500gb sata hdd and a usb 2.0 enclosure for it.
I want to be able to use the hdd frequently on both the ubuntu pc and my ps3.

I don't know how to format the drive or what filesystem to use or how to set read/write permissions and a bunch of other stuff I've read about.

Could anyone help me out please?
Thanx! =]

---

### Post by inameiname on 2010-05-25
In my experience the easiest and most compatible format is NTFS for an external hard drive. FAT32 is okay if you only rarely use it, but as you said you plan to go frequently, NTFS is probably best. Of course I don't believe a PS3 supports it. Or at least less than a FAT32. Certainly not a Linux format.

---

### Post by new_tolinux on 2010-05-25
Probably your 500GB drive comes formatted as FAT32 and empty, so no real reason to format it again.
If you want to reformat it, you can do that for example with the info given in this link: [http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)
It is for a pen-drive, but it's the same idea for USB disks (which is just a big pendrive, apart from some different hardware).

If you want to use it on the PS3 I would recommend _not_ to format the drive ext3/ext4 (linux filesystems) because your PS3 can't read them (unless you managed to have it running linux ;))
FAT32 would be your only option to use it with both linux and your PS3.

Edit: another thread about formatting: [http://ubuntuforums.org/showthread.php?t=198876](http://ubuntuforums.org/showthread.php?t=198876)

---

### Post by inameiname on 2010-05-25
A word of warning though with FAT32, if you already don't know, you can't have say DVD-size ISOs on it, as there is a maximum file size constraint, so unless you just have a bunch of smaller than I think 4GB files on it, one idea might be partitioning it with both FAT32 and NTFS. Just an idea. This way you can load it up with whatever you want outside of your PS3, but have as much space as you want and think you'll need for your game system. IDK.

Good little link here:

[http://boardsus.playstation.com/t5/PlayStation-3-General/how-to-format-a-external-hard-drive-to-work-on-my-20GB-ps3/m-p/26979569](http://boardsus.playstation.com/t5/PlayStation-3-General/how-to-format-a-external-hard-drive-to-work-on-my-20GB-ps3/m-p/26979569)

---

### Post by new_tolinux on 2010-05-25
FAT32 can't take full-size DVD5-ISO files, because they're about 4400 megabyte (~4GiB). The limit of FAT32 is a hard 4 GiB (4096MiB), so it's just a bit less than a full-size DVD5 iso.

If you haven't got an ISO, you _can_ put complete DVD's on the drive, since each file on the average movie-DVD is ~1GB max.

---

### Post by Jayjay402 on 2010-05-25
Thanx for the prompt replies guys! =]
FAT32 it is then! I don't need to worry about file sizes, it's mostly music, photos and videos, probably nothing even over 2gb in size.

I'm still a little weary on the permissions and file and foler access.
I've been playing around with an 8gb usb pen before I crack on with the 500gb hdd, and ubuntu won't let me change certain things.

I right clicked on the drive, [properties]>[permissions]
It reads: 'The permissions of "[drive]" could not be determined.'

However what's weird is, when I right click in a blank area within the drive, the permissions are shown, but I can't change them, they just change back quickly.

---

### Post by ajgreeny on 2010-05-25
I think you can only change the permissions of the mount folder of the  fat32 or ntfs drive you are using, as neither file system will allow the standard linux file permissions.  Generally the permissions of such drives are for any logged on user read/write by default.

---

### Post by Jayjay402 on 2010-05-25
oh, ok, well that's good to know then. Thank-you! =]

Idk how this forum works exactly, but is there a way I can up-vote you guys or some kinda system like that?

---

### Post by inameiname on 2010-05-25
Hmmm, that is weird indeed. I've never had issues with permission in Karmic and Lucid with external hard drive and flash drives. 

Anyway, if you want to change permissions of things, (I think it works on drives too), just do the basic thing in the terminal:

sudo chown -R (your username) /(whatever location is)

that usually fixes things with me.

Back in Jaunty though, and on rare occasions with Karmic, there were weird things happening on random times with more than one usb drives which it would be unlocked and read/write capable one minute, and all of a sudden there is 'input/output error' and there's a lock icon on files on the drive. The only way I was able to fix that was to erase and re-format. Hopefully that's not your problem.

---

### Post by inameiname on 2010-05-25
Aww, nah, I have no idea. I've only been on here myself for just a month or so, so I'm still learning my way around it as well. I'm slowly learning things....

---

### Post by Jayjay402 on 2010-05-25
I've heard quite a bit about terminal, but don't even know how to get to it, how do I open it?

---

### Post by warfacegod on 2010-05-25
> **inameiname said:**
> Hmmm, that is weird indeed. I've never had issues with permission in Karmic and Lucid with external hard drive and flash drives. 

Anyway, if you want to change permissions of things, (I think it works on drives too), just do the basic thing in the terminal:

sudo chown -R (your username) /(whatever location is)

that usually fixes things with me.

Back in Jaunty though, and on rare occasions with Karmic, there were weird things happening on random times with more than one usb drives which it would be unlocked and read/write capable one minute, and all of a sudden there is 'input/output error' and there's a lock icon on files on the drive. The only way I was able to fix that was to erase and re-format. Hopefully that's not your problem.

The proper code would be:

```
sudo chown -R username:usergroup /media/drivename
```

Replacing username/group and drivename which can be found in the media folder as a string of numbers and letters, not the name that appears on the desktop.

Be forewarned though, I'm not sure if this code will work on a FAT32 or NTFS drive.

---

### Post by warfacegod on 2010-05-25
> **Jayjay402 said:**
> I've heard quite a bit about terminal, but don't even know how to get to it, how do I open it?

Applications> Accessories> Terminal

---

### Post by Jayjay402 on 2010-05-25
Ok, thanx for this new info.
As you can tell, I'm a complete n00b, where is this 'media folder' that you mentioned, I can't see it anywhere.

As for the terminal bit, thanx, i'm an idiot, I should have just looked harder!

---

### Post by inameiname on 2010-05-25
I've never tried that 'username:usergroup' way before...I'll have to try it. Thanks for the suggestion warfacegod.




And if you never use your 'Windows' key down there on the bottom left of your keyboard for anything in Ubuntu, I suggest making it useful, and one way is having it open a terminal for you. Just a suggestion.

Just copy and paste this in the terminal, and then it won't be as big of a nuisance when you need to use one:

gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"

---

### Post by Jayjay402 on 2010-05-25
> **inameiname said:**
> I've never tried that 'username:usergroup' way before...I'll have to try it. Thanks for the suggestion warfacegod.




And if you never use your 'Windows' key down there on the bottom left of your keyboard for anything in Ubuntu, I suggest making it useful, and one way is having it open a terminal for you. Just a suggestion.

Just copy and paste this in the terminal, and then it won't be as big of a nuisance when you need to use one:

gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"

Ha, cool, thanx! =]

---

### Post by inameiname on 2010-05-25
No prob. That shortcut changed my mind on the terminal. I hated it with a passion back then. hehe

---

### Post by Jayjay402 on 2010-05-25
I just looked in Disk Utility and my secondary internal 80gb hdd is formatted as ntfs, it's currently empty anyway, so what would be the best to format that as?

Also, can I not make desktop icons and have them still there when I next boot up?

---

### Post by warfacegod on 2010-05-25
> **Jayjay402 said:**
> Ok, thanx for this new info.
As you can tell, I'm a complete n00b, where is this 'media folder' that you mentioned, I can't see it anywhere.

As for the terminal bit, thanx, i'm an idiot, I should have just looked harder!

Places> Computer> Filesystem> media

If the 80 GB HDD is going to be used just in Linux, I suggest ext4

Normally an icon will stay on the desktop unless you delete it. If you want to set it as a link to a drive that doesn't automount then it won't work after you reboot.

---

### Post by Jayjay402 on 2010-05-25
Ok, I went to the media bit, but there is no test or anything, just the drives that I have plugged in. The usb pen is named what I named it when I had windows.

I'll format the 80gb hdd in ext4, thanx! =]

how do I make it so that a drive is always mounted? the 80gb currently doesn't automount for some reason.

---

### Post by warfacegod on 2010-05-25
Here's another cool trick:

```
sudo tune2fs -m x /dev/sd
```

By default, Ubuntu reserves 5% of every HDD connected to it. This will get that back for you.

x represents the % so if you want 0% reserved replace x with 0. You'll need to make sd relate to the appropriate drive. In your case it's probably going to be sd*b* (no italic) for that 80 GB HDD. You can also tell it use only a specific partition by adding the partition # to it. Example: sdb3.

I absolutely ***do not*** recommend doing this to the partition that your OS is installed on.

5% may not seem like allot but when you plug in, say a 1 TB external, it will automatically lose around 50 GB. That's way too much for my taste.

---

### Post by Morbius1 on 2010-05-25
You can't chmod or chown a Windows file type because there are no ownership or permissions bits to set. The only way to change those things is through a mount or in fstab.

When you plug it in it will automount with you as owner and with read / write permissions set to you only.

You can change that for FAT32 ( but not for NTFS ) by adding a line in fstab. For example I have a USB stick that I want to automount with a specific set of permissions when inserted:

(1) Create a mountpoint for the USB stick to live in.

Open Terminal 
Type mkdir /home/morbius/CORSAIR

(2) Add a line to fstab that will mount every time it's connected
```
LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=000,utf8,flush,noauto 0 0
```

---

### Post by warfacegod on 2010-05-25
> **Jayjay402 said:**
> Ok, I went to the media bit, but there is no test or anything, just the drives that I have plugged in. The usb pen is named what I named it when I had windows.

I'll format the 80gb hdd in ext4, thanx! =]

how do I make it so that a drive is always mounted? the 80gb currently doesn't automount for some reason.

You need to modify your fstab file. I'm not qualified to walk you through that but I know someone that is. I'll drop them a line.

---

### Post by Jayjay402 on 2010-05-25
> **Morbius1 said:**
> You can't chmod or chown a Windows file type because there are no ownership or permissions bits to set. The only way to change those things is through a mount or in fstab.

When you plug it in it will automount with you as owner and with read / write permissions set to you only.

You can change that for FAT32 ( but not for NTFS ) by adding a line in fstab. For example I have a USB stick that I want to automount with a specific set of permissions when inserted:

(1) Create a mountpoint for the USB stick to live in.

Open Terminal 
Type mkdir /home/morbius/CORSAIR

(2) Add a line to fstab that will mount every time it's connected
```
LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=000,utf8,flush,noauto 0 0
```

woah, whatx for the help but a little too fast for me,
(1) create mountpoint- Do some drives do that on their own? I think mine has, idk.

fstab? do I already have that or I have to get it from somewhere? Could you tell me which bits of your code I have to replace with what please? Thank-you.

---

### Post by warfacegod on 2010-05-25
Places> Computer> Filesytem> etc> fstab

---

### Post by Jayjay402 on 2010-05-25
ok, I got to fstab, but I can only open it, it's in read-only format, and I can't change its permissions because the owner is 'root', not me.

Thanx again for all the help guys! =]

---

### Post by Morbius1 on 2010-05-25
> **Jayjay402 said:**
> woah, whatx for the help but a little too fast for me,
(1) create mountpoint- Do some drives do that on their own? I think mine has, idk.

fstab? do I already have that or I have to get it from somewhere? Could you tell me which bits of your code I have to replace with what please? Thank-you.
The automounting of external drives will create a temporary mount point but you will need to make it permanent if you want to change the default permissions allowable for that drive. The question is do you need to change the default permissions of that external drive.

You already have an fstab - /etc/fstab.

If you really need to do that then insert the usb drive, open a Terminal and type:

```
sudo blkid -c /dev/null
```EDIT:
> ok, I got to fstab, but I can only open it, it's in read-only format,  and I can't change its permissions because the owner is 'root', not me.Open a Terminal and type:
```
 gksu gedit /etc/fstab
```

---

### Post by Jayjay402 on 2010-05-25
Actually that is a good question, if the default permissions are for me to read & write, then I'm good. But I just want to have more complete control over my hardware. atm, it seems like ubuntu is telling me that I can't do a whole bunch of things.
=S

Anyway, after that first step I get this:

jayen@jayen-desktop:~$ sudo blkid -c /dev/null
[sudo] password for jayen: 

and my password for ubuntu is: 000000 but it won't let me type anything!

The second bit you told me is useful, I still don't know exactly what to put where, you gave me this:

LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=000,utf8,flush,noauto 0 0


EDIT: I found that the password was typing, but I couldn't see it. Heres what I got after that:

jayen@jayen-desktop:~$ sudo blkid -c /dev/null
[sudo] password for jayen: 
Sorry, try again.
[sudo] password for jayen: 
/dev/sda1: UUID="9a36492c-e91d-4451-8d14-a1a1ae6952cb" TYPE="ext3" 
/dev/sda5: UUID="dac210e2-945c-4d53-9355-a6a317dfc111" TYPE="swap" 
/dev/sdb1: LABEL="80gb" UUID="aa52d102-2fd1-487f-ae87-1ddccb10268e" TYPE="ext4" 
/dev/sdc1: LABEL="60GB - Documents & Media" UUID="D660B09D60B085B1" TYPE="ntfs" 
/dev/sdd1: LABEL="JAYEN8GB" UUID="B001-05AB" TYPE="vfat" 
jayen@jayen-desktop:~$ ^C
jayen@jayen-desktop:~$


Also, after formatting the 80gb hdd to ext4 I'm finding that I can't do much with it. It's supposedly owned by root and permissions on it can't be changed either.

---

### Post by warfacegod on 2010-05-25
.01 Don't post your password. You should probably change it now.

.02 The Terminal won't show anything for your password but it goes in anyway. Just type it in and hit Enter.

---

### Post by Jayjay402 on 2010-05-25
> **warfacegod said:**
> .01 Don't post your password. You should probably change it now.

.02 The Terminal won't show anything for your password but it goes in anyway. Just type it in and hit Enter.

The password is only used on my pc, no online uses or anything, so it shouldn't matter.

Yeah, I've done that second bit now. I'm slowly getting somewhere! :)

---

### Post by Morbius1 on 2010-05-25
> Actually that is a good question, if the default permissions are for me  to read & write, then I'm goodThen you don't need to add anything in fstab for the external USB drive.

> I just looked in Disk Utility and my secondary internal 80gb hdd is  formatted as ntfs, it's currently empty anyway, so what would be the  best to format that as?

Also, can I not make desktop icons and have them still there when I next  boot up?     I assume that the 80gb hdd is this from blkid:
>  /dev/sdb1: LABEL="80gb" UUID="aa52d102-2fd1-487f-ae87-1ddccb10268e"  TYPE="ext4" If you want to automount that partition then use the following as a template:

STEP 1: Make a home for the partition to live in:
```
mkdir /home/jayen/80gb
```STEP 2: Add a line in fstab to have that partition mounted at boot:
```
LABEL=80gb /home/jayen/80gb ext4 defaults,noatime 0 2
```STEP 3: Test the new fstab:
```
sudo umount /media/80gb
sudo mount -a
```See if your partition is mounted to /home/jayen/80gb. You will have an icon on your desktop and it should persist through reboots.

---

### Post by Jayjay402 on 2010-05-25
I did step one, and it worked.

Step 2: idk if I did it right or not, this is what my fstab looks like now:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=9a36492c-e91d-4451-8d14-a1a1ae6952cb  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=dac210e2-945c-4d53-9355-a6a317dfc111  none            swap         defaults                    0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     ext4         defaults                    0  0  
/dev/sdc1                                  /media/sdc1     ntfs         defaults                    0  0  
/dev/sdd1                                  /media/sdd1     vfat         defaults                    0  0  
LABEL=80gb                                 /home/jayen/80gb ext4        defaults,noatime            0  2Step 3: I got this:
> jayen@jayen-desktop:~$ sudo umount /media/80gb
umount: /media/80gb: not found
jayen@jayen-desktop:~$ sudo mount -a
jayen@jayen-desktop:~$ I don't think it worked.

Anyway, I have to go now, I'll be back on tomorrow.

---

### Post by Morbius1 on 2010-05-25
It didn't work because you already have it mounted :
From your fstab:
>  /dev/sdb1                                  /media/sdb1     ext4          defaults                    0  0  The decision of where you want it mounted is up to you. I must have misunderstood your post - I thought you wanted help in automounting your partitions.

If you want it to mount to /media/sdb1 then remove the this line:
>  LABEL=80gb /home/jayen/80gb ext4         defaults,noatime            0  2 If you want it to mount to /home/jayden/80gb then remove this line:
>  /dev/sdb1       /media/sdb1     ext4          defaults                    0  0

---

### Post by Morbius1 on 2010-05-25
Well, it took me long enough but I think I found the source of your original problem. Your fstab line for the external usb device ( and I'm assuming that's your external USB drive ):
>  /dev/sdd1                                  /media/sdd1     vfat          defaults                    0  0  (1) That will only work if the usb drive is on when you boot

(2) It will mount with owner = root and with read / write access to root and read access only to everyone else.

If you remove that line it will automount with you as owner when it's turned on after you boot.

---

### Post by Jayjay402 on 2010-05-25
Ah, thanx! I get it now. I'm going to format all my external devices as fat32 now and keep them as automounts. Thanks for the help guys! =]

---

### Post by Leppie on 2010-05-28
> **Jayjay402 said:**
> I'm going to format all my external devices as fat32 now and keep them as automounts.
imo, it's easier to format the drive to ntfs and install ntfs-config.
ntfs-config will then take care of mounting the device whenever you plug it in.
and as a bonus, you can also provide access to the drive for other users by adding them to the "fuse" group:
```
sudo adduser <username> fuse
```

---

