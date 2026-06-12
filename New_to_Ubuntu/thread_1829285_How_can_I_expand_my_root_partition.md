---
title: "How can I expand my root partition?"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-20
Here is the scenario: I logged in to windows 7 on my laptop, shrank down the primary partition hoping that I can expand my Ubuntu partition, but apparently I can't, I have tried using a program called "GParted Partition Editor", the program is working fine, but it says this in a pop up windows:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-13.png[/IMG]

And as you can see in the picture above, I have unmounted all the other partition, so any tips on how I can expand my partition, thanks in advance!

---

### Post by westie457 on 2011-08-20
> **the-new-x said:**
> Here is the scenario: I logged in to windows 7 on my laptop, shrank down the primary partition hoping that I can expand my Ubuntu partition, but apparently I can't, I have tried using a program called "GParted Partition Editor", the program is working fine, but it says this in a pop up windows:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-13.png[/IMG]

And as you can see in the picture above, I have unmounted all the other partition, so any tips on how I can expand my partition, thanks in advance!

Hi. What you are trying to do must be done using a Livecd. Either a Gparted one or the one you used to do your original installation.

use the information in this thread for guidance. Ignore the bits for the Windows partition. You have already done that.

[http://ubuntuforums.org/showthread.php?t=1798827](http://ubuntuforums.org/showthread.php?t=1798827)

---

### Post by dave01945 on 2011-08-20
you will need to do it using a live cd/usb either of ubuntu or i believe gparted does a live cd version on there website 

you can't resize a partition while it's mounted and you can't unmount root because your whole system is using it

it's also advised to backup anything important just incase something goes wrong

also this is going to take some time because gparted will copy the entire filesystem as it moves it

---

### Post by the-new-x on 2011-08-20
OK thanks for the replies guys, and about the live cd, can I use an external HDD instead?

---

### Post by Basher101 on 2011-08-20
your problem is that your ext4 filesystem is ***behind*** your unallocated partition...you will have to move the partition, which will take hours looking at the size of it. A fresh install would be alot faster, but then again, how much data do you have that you dont want to reinstall again?

ps. you can make your usb HDD to a live usb with Unetbootin (ubuntu) or Universal-USB installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") for windows. I got better expirience using the universal usb installer from windows to make bootable USB drives (or sticks). just make a 1-2 GB partition that will be formatted to FAT32 from the program.

---

### Post by the-new-x on 2011-08-20
> **Basher101 said:**
> your problem is that your ext4 filesystem is ***behind*** your unallocated partition...you will have to move the partition, which will take hours looking at the size of it. A fresh install would be alot faster, but then again, how much data do you have that you dont want to reinstall again?

ps. you can make your usb HDD to a live usb with Unetbootin (ubuntu) or Universal-USB installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") for windows. I got better expirience using the universal usb installer from windows to make bootable USB drives (or sticks). just make a 1-2 GB partition that will be formatted to FAT32 from the program.
Well, it is not the installed applications that I am worried about, it is just that I have a 256kb connection, which makes it a pain in the *** re-download all of my programs (more than 10 GB). So I guess I will have to wait for hours then. Thanks for the reply.
P.S. can I backup my installed programs? (Don't judge me, I never used a backup in my life!)

---

### Post by gandaran on 2011-08-20
> **the-new-x said:**
> Well, it is not the installed applications that I am worried about, it is just that I have a 256kb connection, which makes it a pain in the *** re-download all of my programs (more than 10 GB). So I guess I will have to wait for hours then. Thanks for the reply.
P.S. can I backup my installed programs? (Don't judge me, I never used a backup in my life!)
you can copy or backup all downloaded programs from package manager and ubuntu updates from /var/cache/apt/archives (if you haven't cleaned them up yet) then after re-installing ubuntu (same ubuntu release!) put them in same location and use the normal procedure to install the packages and updates, it wont download anything from internet if the packages are already where they should be.

---

### Post by beew on 2011-08-20
> **gandaran said:**
> you can copy or backup all downloaded programs from package manager and ubuntu updates from /var/cache/apt/archives (if you haven't cleaned them up yet) then after re-installing ubuntu (same ubuntu release!) put them in same location and use the normal procedure to install the packages and updates, it wont download anything from internet if the packages are already where they should be.


Provided OP has not cleaned the cache. I clean mine regularly so there is nothing in the cache.

---

### Post by beew on 2011-08-20
Well I had a similar situation when I removed Windows XP from one of my machines. It seemed to me that moving Ubuntu's boot partition liek that was kind of risky (I don't know if it was just coincident, but I tried to expand Ubuntu's / partition in a similar situation by moving its left end to the left in an external drive installation, afterwords the drive became unbootable with lots of io errors, but expanding to the right by moving the right end was ok, done it many times), so instead of expanding Ubuntu I installed another Linux in the unallocated space left by XP.

---

### Post by the-new-x on 2011-08-20
Well, this leaves me with 1 question, can I copy and paste the entire partition to an HDD (And by that I mean copying everything in the / directory) and then just delete the partitions and make a new one, install Ubutnu, and then paste of all of the stuff!?
And thanks for the replies!

---

### Post by gandaran on 2011-08-20
> **beew said:**
> Provided OP has not cleaned the cache. I clean mine regularly so there is nothing in the cache.
true, I clean mine too to save root partition space but only after coping every one to a folder in a Data partition in case I need to reinstall, my internet data plan is limited to 4GB downloads.
```
sudo apt-get clean
```
most ubuntu users don't know about this so I believe OP still has the cache intact.

---

### Post by the-new-x on 2011-08-20
> **gandaran said:**
> true, I clean mine too to save root partition space but only after coping every one to a folder in a Data partition in case I need to reinstall, my internet data plan is limited to 4GB downloads.
```
sudo apt-get clean
```
most ubuntu users don't know about this so I believe OP still has the cache intact.
As ironic as this might sound, I too don't know what op is, well to be honest, I am still new to the Linux world, been a windows user for all of my life, I have installed Ubuntu a couple of weeks ago, and it is my first Linux distro!
So if you don't mind explaining a little bit about OP, I would be grateful!

---

### Post by beew on 2011-08-20
OP just mean original poster, that is you. :)

---

### Post by the-new-x on 2011-08-20
> **beew said:**
> OP just mean original poster, that is you. :)
And I had to bombard myself for being a noob in Linux just for that, WOW!!
And thanks for clarifying, but still, if I completely copy everything in the root partition, then completely delete the Ubuntu partition, and then install a new fresh copy of Ubuntu, and paste everything that I have copied to the root partition, will that work and will I get all of my software back!?

---

### Post by Basher101 on 2011-08-20
Theoretically, yes. The only issue could be grub and fstab, thus bootloader and mount. since you made a fresh install on a new partition, you must then edit your fstab so mounting works (maybe it works out of the box, maybo not)

---

### Post by dave01945 on 2011-08-20
it shouldn't take too long i resized a 20gb partition the other day and that took half hour so for your 100gb partition should be about 2.5hrs depending on the speed of you hdd

---

### Post by Basher101 on 2011-08-20
Moving the partition is your best option as it seems. Copying all over to one hdd and then back again could even take longer. Glad we all could help

---

### Post by the-new-x on 2011-08-21
Thanks for the help guys, and Basher101, did you miss the part where I  said that I am still somehow in a noob in Linux, and that this is my  first Linux distro, so if you don't mind, please explain to me a bit  more about grub and fstab, and how I can edit my fstab so that the  mounting works!
Again, thanks for the help guys!

---

### Post by westie457 on 2011-08-21
> **the-new-x said:**
> Thanks for the help guys, and Basher101, did you miss the part where I  said that I am still somehow in a noob in Linux, and that this is my  first Linux distro, so if you don't mind, please explain to me a bit  more about grub and fstab, and how I can edit my fstab so that the  mounting works!
Again, thanks for the help guys!

Once you have moved the partition and exited Gparted open a terminal (command-line interface - cli)

type in ```
sudo update-grub
```
and hit enter. You will be asked for your password.

NOTHING will show on the screen as you type however the keystrokes will be registering.

The updating of Grub might not be necessary but it never hurts to run it.after doing work on partitions.

With the update to Grub done fstab should be okay as well. If not come back here and ask for more help.

---

### Post by Wim Sturkenboom on 2011-08-21
I'm not sure what the exact purpose of the excercise is, but I'm surprised that nobody has mentioned on of the following options
[LIST]
[*]Use the partition as a data partition and mount that partition somewhere in the user's home directory; this will work very well if you're the only user. Probably the most efficient if it comes to flexibility (no space in the / directory anymore? Simply move some files from the home directory into the mounted partition).
[*]Use the partition as the home partition; copy the user directories (preserving the permissions) and mount it on /home (modification of fstab). Once it works, unmount, cleanup the home directory and that space is available for / again. 
[/LIST]

---

### Post by the-new-x on 2011-08-21
> **westie457 said:**
> Once you have moved the partition and exited Gparted open a terminal (command-line interface - cli)

type in ```
sudo update-grub
```
and hit enter. You will be asked for your password.

NOTHING will show on the screen as you type however the keystrokes will be registering.

The updating of Grub might not be necessary but it never hurts to run it.after doing work on partitions.

With the update to Grub done fstab should be okay as well. If not come back here and ask for more help.
I'm a noob, but not that much of a noob, what I meant of my question is that what exactly is the role of grub and fstab, and how do they work. And thanks for the reply!

---

### Post by the-new-x on 2011-08-21
> **Wim Sturkenboom said:**
> I'm not sure what the exact purpose of the excercise is, but I'm surprised that nobody has mentioned on of the following options
[LIST]
[*]Use the partition as a data partition and mount that partition somewhere in the user's home directory; this will work very well if you're the only user. Probably the most efficient if it comes to flexibility (no space in the / directory anymore? Simply move some files from the home directory into the mounted partition).
[*]Use the partition as the home partition; copy the user directories (preserving the permissions) and mount it on /home (modification of fstab). Once it works, unmount, cleanup the home directory and that space is available for / again. 
[/LIST]
It is true that I am the only user on this computer, but I think that expanding is a better option!

---

### Post by Wim Sturkenboom on 2011-08-21
That's OK. It's your system and you know your needs.

Just make sure that you have backups in case you ever have to do a re-install (which will wipe all your data) ;)

---

### Post by the-new-x on 2011-08-21
> **Wim Sturkenboom said:**
> That's OK. It's your system and you know your needs.

Just make sure that you have backups in case you ever have to do a re-install (which will wipe all your data) ;)
Will do, thanks for the help!

---

