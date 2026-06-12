---
title: "Cant read/write to external hard drive please help"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by civillianslave on 2009-11-26
Have tried NTFS config  tool but it doesnt work. I have an elements 160 gb ext hard drive which i cannot delete or add to, can anyone please help me as i am rather new to all this linux stuff.

---

### Post by coffeecat on 2009-11-26
What version of Ubuntu are you using? You shouldn't need any config tool. If you plug an external USB NTFS drive into Ubuntu it should be mounted read/write automatically and a browser window open on your desktop. I presume this is not happening?

What config tool were you using? What did you do? What happens when you plug your external drive in?

---

### Post by civillianslave on 2009-11-26
I am using Ubuntu 9.10

Tried using NTFS CONFIG too in my admin section.

When i connect my ext hard drive the icon for it appears and i can play files but cannot delete, move, change or add to hard drive. When i try to it says it is read only.

---

### Post by coffeecat on 2009-11-26
> **civillianslave said:**
> Tried using NTFS CONFIG too in my admin section.


Yes, but what did you do with it? ntfs-config doesn't come with a default install because 
99.9% of times it isn't needed. It could be that whatever you did in ntfs-config has caused this problem.

---

### Post by civillianslave on 2009-11-26
i only used that after the problem occurred. I never had this problem before upgrading, and no probs at all when using microsoft.

I looked up the problem on the ubuntu sites and someone recommended installing the NTFS thingy, you click a box in the app "enable write support for external device" alas this did not alter the problem one bit.

Someone suggested formatting the hard drive but i have nothing big enough, nor can i afford it either, to put everything onto while formatting the Hard drive

---

### Post by coffeecat on 2009-11-26
> **civillianslave said:**
> i only used that after the problem occurred. I never had this problem before upgrading, 

Oh dear. It's better to provide all relevant information to start with. :wink: Do you mean that your external NTFS drive worked with Jaunty, but that when you upgraded to Karmic it stopped working? And if so, was your upgrade an upgrade of the Jaunty install, or did you make a fresh installation of Karmic? Or something else?

---

### Post by civillianslave on 2009-11-26
I made a fresh install of the new ubuntu 9.10 32bit

---

### Post by coffeecat on 2009-11-26
> **civillianslave said:**
> I made a fresh install of the new ubuntu 9.10 32bit

OK, that's most unusual for NTFS not to work. I had a quick tinker with ntfs-config (without letting it do anything to my system! :rolleyes: ) and, as far as I can make out, it probably writes entries to a config file called /etc/fstab.

By the way, have you tried a reboot since you re-configured with ntfs-config?

So - navigate to /etc/fstab and double-click on it - it will open read-only in a text editor. Post the contents (please use [noparse]```

```[/noparse] tags otherwise it will be near-unreadable) and we'll take it from there.

One other question - you haven't said what Ubuntu you were using before the upgrade. Were you using 9.04/Jaunty, and were you able to read/write your drive in Jaunty?

---

### Post by civillianslave on 2009-11-26
I have tried reboot and nothing changed.

I think i was on the most recent Xubuntu before the 9.10 update.
I'm sorry don't know what you mean by the [code] thing, I am a newbie willing to learn though.

----------------------------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=da953910-396d-4782-966e-aec6ddb577b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e83438b9-3036-4351-949f-ca83ea9e3e60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by coffeecat on 2009-11-26
> **civillianslave said:**
> I'm sorry don't know what you mean by the ```
 thing, I am a newbie willing to learn though.

No problem. Have a look here for a guide to BB Code:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Anyway, to business.

Either I was wrong about the way ntfs-config works, or it failed to make a change to fstab, because there is no ntfs line in your fstab.

I've have to log out in a moment - I'm teaching some computer skills to an elderly neighbour who knows next to nothing about computers. ](*,)So I won't be back for 2-3 hours. In the meantime, go to Applications > Accessories > Terminal, and post the output of:

[code]sudo fdisk -l
```You'll need to copy and paste, and the keyboard shortcut for copy in the terminal is ctrl-shift-C. That will help us get a line into fstab for you, and hopefully someone else might contribute to this thread ([-o<) in case I am missing something obvious.

---

### Post by civillianslave on 2009-11-26
Thanks for the link.

Here is the info you asked for - 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb4759

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9358    75168103+  83  Linux
/dev/sda2            9359        9729     2980057+   5  Extended
/dev/sda5            9359        9729     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x276cb386

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

---

### Post by kansasnoob on 2009-11-26
I always install ntfsprogs:

```
sudo apt-get install ntfsprogs
```

Restart is required for changes to take effect.

I'd remove ntfs-config first.

---

### Post by kansasnoob on 2009-11-26
Oh, this:

> Device Boot Start End Blocks Id System
/dev/sdb1 1 19457 156288321 c W95 FAT32 (LBA)

Tells me we're barking up the wrong tree. That says the drive is formatted fat32, which is fine, but all the ntfs tools in the world aren't going to help.

Something regarding "permissions" I imagine but I'm not sure.

---

### Post by civillianslave on 2009-11-26
Cool, so any ideas how i can get permission or get the fat32 drive to let me delete and add stuff?

---

### Post by coffeecat on 2009-11-26
Im back. As you've now discovered your external drive is not formatted NTFS. It's formatted FAT32. The app ntfs-config will be no help here. But it's still puzzling why it is not automounted when you plug it in. Support for FAT32 in Ubuntu goes back to the dawn of time - very odd.

You mentioned Xubuntu at one point as an earlier install, but since you tagged your thread 'Ubuntu' that's what I assumed you were running. Are you sure you are running Ubuntu and not Xubuntu? If you are running Ubuntu you should be seeing three menus - Applications, Places, System - top left. Plug your drive in again. Even if nothing seems to happen, have a look in the Places menu for it.

---

### Post by civillianslave on 2009-11-26
cheers.I am using Ubuntu 9.10, the ext HD shows up, its mounted i can read from it but not delete or add to the hard drive.

---

### Post by kansasnoob on 2009-11-26
Consider this just thinking out loud, OK?

I use external storage drives a lot. I have "pmount" installed, it's in Synaptic. I also install "nautilus-gksu" which is also in Synaptic. I think both require a restart for the change to recognized.

When I connect the drive it shows up on the desktop and Nautilus launches and shows the content. If I'm going to edit the contents I close Nautilus and then right click the icon on the desktop and unmount.

Then I go to Computer and the drive is still there. Then I right click it and choose to open as Administrator which requires my password. Then I can do whatever I want!

I'm not sure if that will help you or not.

---

### Post by Don1500 on 2009-11-26
Have yoiu checked properties to see if you can change it to r/w? 
(Silly question I know but...)

Also, have you looked at it with G-Parted?

---

### Post by civillianslave on 2009-11-27
Hey [kansasnoob]("http://ubuntuforums.org/member.php?u=554595"), i tried what you suggested when i woke up this morning. Sadly the ext hard drive is still read only, even after trying out what you suggested.

[Don1500]("http://ubuntuforums.org/member.php?u=288932") have tried using G-Parted and sadly this was no help either, i have all the required programmes which it says i need for dealing with my ext hd (Fat32) but its still read only.:confused:

---

### Post by coffeecat on 2009-11-27
> **civillianslave said:**
> cheers.I am using Ubuntu 9.10, the ext HD shows up, its mounted i can read from it but not delete or add to the hard drive.

Apologies - you said earlier that it was mounted, but read-only.

Anyway, I may have found the answer. Let's hope so. Look at this post:

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8065784&postcount=24](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8065784&postcount=24)

Did you use the drive in Windows before you had this problem in Ubuntu? Try plugging it into a Windows machine and then make sure you use the 'safely remove' utility before unplugging it.

---

### Post by civillianslave on 2009-11-27
Thank you, i will use my flatmates PC when he gets home this afternoon then let y'all know the outcome. Been scanning the net for people with a similar problem, none of their solutions have worked out for me sadly. Will try this and cross my fingers.

---

### Post by coffeecat on 2009-11-27
> **civillianslave said:**
> Thank you, i will use my flatmates PC when he gets home this afternoon then let y'all know the outcome. Been scanning the net for people with a similar problem, none of their solutions have worked out for me sadly. Will try this and cross my fingers.

Good luck with that. If it doesn't work, post back. There are one or two other avenues to explore.

---

### Post by civillianslave on 2009-11-27
:KS:KS:KS:KS:KS Answer :D
:guitar:
Thank you for that last bit of advice, worked perfectly.(that's the last time I remove something without doing so safely on a computer)
Now I can clean up my ext hard drive, finally, get rid of some corrupt files etc.

A big thank you to all who chipped in on this. Now if i can just figure out why my mouse pointer goes nuts until i reboot when i turn on my laptop, all will be well in Ubuntu world:D

---

