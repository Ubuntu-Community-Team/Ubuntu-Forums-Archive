---
title: "Please help me! Total Noob to ubuntu"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by Akatzman2 on 2011-04-25
Hi all,
I am a total Noob to ubuntu. My computer ( lenovo r61i) was being a bit funky today, so i rebooted it twice without letting the OS fully load, while my iPhone was plugged in charging. Now I am getting a terrifying error. It says; 

Target filesystem doesn't have requested /sbin/init

No init found. Try passing init= bootarg

Please help!!! I am a total noob, and it's finals week! How screwed am I?

---

### Post by jtarin on 2011-04-25
Do you have the Live CD? [Reinstall Grub]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT").Questions??? Ask.

---

### Post by Akatzman2 on 2011-04-25
> **jtarin said:**
> Do you have the Live CD? [Reinstall Grub]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT").Questions??? Ask.

I don't have the livecd. Can I burn it? Any inkling what the he'll is going on with my PC? I should also add I recently ( within a month) had a new HD put in

---

### Post by jtarin on 2011-04-25
> **Akatzman2 said:**
> I don't have the livecd. Can I burn it? Any inkling what the he'll is going on with my PC? I should also add I recently ( within a month) had a new HD put inYes you can burn it.You can't interrupt any OS during boot without some repercussions....and you did it twice.

---

### Post by collisionystm on 2011-04-25
> **Akatzman2 said:**
> I don't have the livecd. Can I burn it? Any inkling what the he'll is going on with my PC? I should also add I recently ( within a month) had a new HD put in

Sounds to me like a permission problem. I am sure when the computer booted and needed to access the init directory, permissions were being changed on the folder as part of the normal bootup. Shutting it off in the middle has caused a lockout. Can you access any kind of terminal or command line? You can check and set permissions for the directory.

---

### Post by jtarin on 2011-04-25
[Here's a viable solution to try once you have a live CD.]("http://ubuntuforums.org/showthread.php?t=1167710")

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> Sounds to me like a permission problem. I am sure when the computer booted and needed to access the init directory, permissions were being changed on the folder as part of the normal bootup. Shutting it off in the middle has caused a lockout. Can you access any kind of terminal or command line? You can check and set permissions for the directory.

I'm guessing I can probably get to the comlime, not sure how to access though ( been a windows user for 10+ years)

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> Sounds to me like a permission problem. I am sure when the computer booted and needed to access the init directory, permissions were being changed on the folder as part of the normal bootup. Shutting it off in the middle has caused a lockout. Can you access any kind of terminal or command line? You can check and set permissions for the directory.

Scratch that, I'm at the command line. How could I check permissions?

---

### Post by collisionystm on 2011-04-25
Use ls -lh to check current

 sudo chmod 777 -R /sbin/init

That will hopefully fix. Reboot

---

### Post by ikt on 2011-04-25
[http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)

> **Akatzman2 said:**
> Scratch that, I'm at the command line. How could I check permissions?

The command line you are at when the system fails to boot is not very useful, I highly advise to make a LiveCD or USB and boot off of that and fix the problem through that environment.

---

### Post by collisionystm on 2011-04-25
> **collisionystm said:**
> Use ls -lh to check current

 sudo chmod 777 -R /sbin/init

That will hopefully fix. Reboot

My droid bath. Was dieing lol. Had to type fast.

```

ls- lh

```

Will list the folders and show their current permissions.
permissions are divided into 3 groups. Owner, group and others.

The 777 is going to provide full ace's to all 3, which normally is unethical but in this situation I doubt security is a high concern ;)

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> Use ls -lh to check current

 sudo chmod 777 -R /sbin/init

That will hopefully fix. Reboot

Sudo isn't being recognized as a valid command?I typed it ls - lh and get 

Partition hd0, msdos5: unknown filesystem
Partition hd0, msdos1: Filesystem type ext2 - Last modification time 2011-3-05 04:04:55 Saturday, UUID ....

---

### Post by collisionystm on 2011-04-25
Damn. I guess your not in the linux kernel. Your just in the grub prompt. You either need to find a way to manually edit your grub or track down a live cd, fast!

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> Damn. I guess your not in the linux kernel. Your just in the grub prompt. You either need to find a way to manually edit your grub or track down a live cd, fast!

Nuts! I am on the grub thing, no clue how to manually edit that.  And in class trying to fix this thing while on my iPhone. Nuts. Guess I'll burn the LiveCD when I get home? I'm hoping my computer isn't royally in the crapper. Thanks for your help thus far, I'm sure panicked me will have more questions shortly. Trying to breathe....

---

### Post by collisionystm on 2011-04-25
Lol you will be fine. All your files can be recovered. The worst that can happen is your custom programs might need a reinstall. If you can't fix grub, just make backup your home folder to another drive with the live cd and make a mental note of the programs you need to put back on. All your program settings are saved in hidden folders in your /home/username/

---

### Post by collisionystm on 2011-04-25
If you are reinstalling I strongly suggest you do not use the 11.04 beta. It needs a few weeks to get some updates.

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> Lol you will be fine. All your files can be recovered. The worst that can happen is your custom programs might need a reinstall. If you can't fix grub, just make backup your home folder to another drive with the live cd and make a mental note of the programs you need to put back on. All your program settings are saved in hidden folders in your /home/username/

I could care less about custom programs, as long as all my class notes are still saved. What liveCD version do you recommend I burn? Thanks for all your help btw... Hopefully this will be a simple permissions fix issue

---

### Post by collisionystm on 2011-04-25
> **Akatzman2 said:**
> I could care less about custom programs, as long as all my class notes are still saved. What liveCD version do you recommend I burn? Thanks for all your help btw... Hopefully this will be a simple permissions fix issue

I personally think 10.04 is the best. 

I will most likely be off here when you get home. Just go to [www.ubuntu.com](www.ubuntu.com) download desktop version 10.04

Boot your laptop with it. You may need to press f12 to elect a boot device at the bios prompt. Choose cdrom drive.

Choose to 'try ubuntu'

Go to 'places' and click on your drive to mount it

Now open terminal

```

sudo bash

```
```

cd /media

```
find your harddrive
```

chmod 777 -R /media/yourhardrive/sbin/init/

```

If that fails....
 
Google 'repair ubuntu grub with live cd'

---

### Post by Akatzman2 on 2011-04-25
> **collisionystm said:**
> If you are reinstalling I strongly suggest you do not use the 11.04 beta. It needs a few weeks to get some updates.



Thanks for all your help :) I'll give it a run at home and let you know what happens

---

### Post by jtarin on 2011-04-25
```
**collisionystm **If that fails....

Google 'repair ubuntu grub with live cd' 
```Or click the link in my first post.

---

### Post by Akatzman2 on 2011-04-26
Hey guys,
I'm having no luck.... I think it's cause I'm not sure what my HD name is. Dumb, i know. How do I figure it out?

---

### Post by nebileix on 2011-04-26
> **Akatzman2 said:**
> Hey guys,
I'm having no luck.... I think it's cause I'm not sure what my HD name is. Dumb, i know. How do I figure it out?

```
sudo fdisk -l
```

check for the disk size.

---

### Post by Pand5461 on 2011-04-26
Or launch System -> Administration -> Disk Utility (in Ubuntu 10.10 or earlier). This will show your disk partitioning.

---

### Post by Akatzman2 on 2011-04-26
> **Pand5461 said:**
> Or launch System -> Administration -> Disk Utility (in Ubuntu 10.10 or earlier). This will show your disk partitioning.


SO I took a screenshot of the disk partitioning. What's the name I am supposed to use for my HD when I run all the suggested stuff by you guys for this?

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Pand5461 on 2011-04-26
So your HD is /dev/sda and the main Linux partition is /dev/sda1. You can mount it by ```
sudo mount /dev/sda1 /mnt 
```Hope this will help. Good luck!

---

### Post by Akatzman2 on 2011-04-26
> **ikt said:**
> [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)



The command line you are at when the system fails to boot is not very useful, I highly advise to make a LiveCD or USB and boot off of that and fix the problem through that environment.


I tried using the fix suggested at this link, and got the same error that the person got here ( [http://ubuntuforums.org/showthread.php?t=1167710](http://ubuntuforums.org/showthread.php?t=1167710)). I used the suggestion to  cat /proc/mounts, and got some output that means nothing to me. ( screenshot attatched). What do I do next?

---

### Post by Pand5461 on 2011-04-26
Try reinstalling GRUB as jtarin suggested. BTW, Alt+PrtScr makes a screenshot of the active window.

---

### Post by Akatzman2 on 2011-04-26
> **Pand5461 said:**
> Try reinstalling GRUB as jtarin suggested. BTW, Alt+PrtScr makes a screenshot of the active window.

How do I reinstall grub? My big concern here is that I have a semester of lecture notes on my hd, will that mess it up?

---

### Post by Pand5461 on 2011-04-26
See the first reply in this thread.

---

### Post by Akatzman2 on 2011-04-26
> **Pand5461 said:**
> See the first reply in this thread.

I've tried that with mounting sda1, and once I mount it and run all the other commands listed, nothing happens. at all.

---

### Post by nebileix on 2011-04-26
follow this command step by step:

```
sudo mount /dev/sda1 /mnt
```
```
sudo mount --bind /dev /mnt/dev
```
```
sudo mount --bind /dev/pts /mnt/dev/pts
```
```
sudo mount --bind /proc /mnt/proc
```
```
sudo mount --bind /sys /mnt/sys
```
```
sudo chroot /mnt
```
```
update-grub
```
u should see something like this
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done

once u see that, u can restart the machine.

---

### Post by Pand5461 on 2011-04-26
> **Akatzman2 said:**
> I've tried that with mounting sda1, and once I mount it and run all the other commands listed, nothing happens. at all.

Can you mount your Linux partition? If yes, you can just copy important data and program settings (the latter are in hidden folders in home dir - press Ctrl+H in Nautilus to show hidden items) to an external drive and do a fresh install.

---

### Post by Akatzman2 on 2011-04-26
> **nebileix said:**
> follow this command step by step:

```
sudo mount /dev/sda1 /mnt
``````
sudo mount --bind /dev /mnt/dev
``````
sudo mount --bind /dev/pts /mnt/dev/pts
``````
sudo mount --bind /proc /mnt/proc
``````
sudo mount --bind /sys /mnt/sys
``````
sudo chroot /mnt
``````
update-grub
```u should see something like this


once u see that, u can restart the machine.

I promise, I literally typed this in verbatim and saw no output. I can do it again and send you a screenshot?

---

### Post by Akatzman2 on 2011-04-26
> **Pand5461 said:**
> Can you mount your Linux partition? If yes, you can just copy important data and program settings (the latter are in hidden folders in home dir - press Ctrl+H in Nautilus to show hidden items) to an external drive and do a fresh install.

When I try and mount that partition (sda1, right), it acts like it's mounting it, but nothing happens. Just keeps trying?

---

### Post by Akatzman2 on 2011-04-26
> **Akatzman2 said:**
> I promise, I literally typed this in verbatim and saw no output. I can do it again and send you a screenshot?
Screenshot attached. What am I missing?

---

### Post by collisionystm on 2011-04-26
:popcorn:> **Akatzman2 said:**
> Screenshot attached. What am I missing?


use 

```

sudo bash

```

and then do your mount code minus using SUDO

---

### Post by Akatzman2 on 2011-04-26
> **collisionystm said:**
> :popcorn:


use 

```

sudo bash

```and then do your mount code minus using SUDO


Still nothing. Screenshot attatched .

---

### Post by Pand5461 on 2011-04-26
> **Akatzman2 said:**
> Still nothing. Screenshot attatched .

when you do
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
what do you see?

---

### Post by Akatzman2 on 2011-04-26
> **Pand5461 said:**
> when you do
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```what do you see?

It still shows up as nothing. I type it in, press enter, then nada

---

### Post by collisionystm on 2011-04-26
> **Akatzman2 said:**
> It still shows up as nothing. I type it in, press enter, then nada


you could have already re-installed by now lol

---

### Post by 3177 on 2011-04-26
Sounds to me like the OP originally had his computer boot usb first.

---

### Post by Akatzman2 on 2011-04-26
> **collisionystm said:**
> you could have already re-installed by now lol
 Well I tried taking the CD out and rebooting the pc, and it's still failing. So I'm thinking, negative  on that.

---

### Post by Akatzman2 on 2011-04-26
> **3177 said:**
> Sounds to me like the OP originally had his computer boot usb first.

My cousin is the one that initially set up the Ubuntu OS for me, are you saying I need to go back to him on this?

---

### Post by 3177 on 2011-04-26
> **Akatzman2 said:**
> My cousin is the one that initially set up the Ubuntu OS for me, are you saying I need to go back to him on this?
no
boot order is in the bios.
not the OS.

---

### Post by collisionystm on 2011-04-26
No, you just need to change your boot order in the bios to load the cdrom drive first. Or yeah, if its easier have your cousin fix it for you. Make sure he backs up all your stuff.

When you start your computer, keep tapping ESC or F12 

It might load a boot option menu

Choose CDROM

---

### Post by Akatzman2 on 2011-04-26
> **collisionystm said:**
> No, you just need to change your boot order in the bios to load the cdrom drive first. Or yeah, if its easier have your cousin fix it for you. Make sure he backs up all your stuff.

When you start your computer, keep tapping ESC or F12 

It might load a boot option menu

Choose CDROM
I'd prefer not to go to my cousin... Matter of pride/ not being ridiculed.
Not sure how to proceed...When I got into the boot menu I had

 two choices. 1. Atapi CD0:HL-DT-ST DVDRAM GSA-T
2. ATA HDDO: WDC WD2500BEKT-00PVMT

---

### Post by Sef on 2011-04-26
> 1. Atapi CD0:HL-DT-ST DVDRAM GSA-T

I would choose number 1.

---

### Post by collisionystm on 2011-04-26
> **Akatzman2 said:**
> I'd prefer not to go to my cousin... Matter of pride/ not being ridiculed.
Not sure how to proceed...When I got into the boot menu I had

 two choices. 1. Atapi CD0:HL-DT-ST DVDRAM GSA-T
2. ATA HDDO: WDC WD2500BEKT-00PVMT


DONT ACCIDENTALLY RE-INSTALL WITHOUT BACKING UP YOUR STUFF!!!!!!!!!

Grab a usb drive and back your stuff up with the 'Try Ubuntu' option!

---

### Post by Akatzman2 on 2011-04-26
> **collisionystm said:**
> DONT ACCIDENTALLY RE-INSTALL WITHOUT BACKING UP YOUR STUFF!!!!!!!!!

Grab a usb drive and back your stuff up with the 'Try Ubuntu' option!

Ahh scary! Thanks for warning me, this was my biggest fear. How do I access all the old files On my hd?

---

### Post by collisionystm on 2011-04-26
Just hit "Try Ubuntu' at the menu prompt. Insert a USB hard drive. Go to Places, Go to your Hard drive and home directory

Copy your username folder to the drive.

---

### Post by Falcon1002 on 2011-04-26
If that does not work you can try using the command:
```
sudo mount -t ext2 /dev/sda1 /media 
```
You might need to replace the ext2 part with ext3.

That should mount your hard drive at /media.
You then can use nautilus to navigate to /media/home.

---

### Post by Akatzman2 on 2011-04-26
> **jtarin said:**
> Do you have the Live CD? [Reinstall Grub]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT").Questions??? Ask.


So this is incredibly embarrassing. As a hail Mary, I tried the instructions at this link once more. Replaced the # sign with a 1. It WENT! but then when I try and mount the critical directories it won't recognize them. Where am I ffing up? ( so sorry I'm such a pain, thanks for bearing with me)

---

### Post by jtarin on 2011-04-26
> **Akatzman2 said:**
> So this is incredibly embarrassing. As a hail Mary, I tried the instructions at this link once more. **_Replaced the # sign with a 1._** It WENT! but then when I try and mount the critical directories it won't recognize them. Where am I ffing up? ( so sorry I'm such a pain, thanks for bearing with me)

Where does it say in the link I gave you anything about a "#" sign?????? Please give me the step number.
If your talking about step 4 the # is not part of the command.Only the parts in bold are commands.

---

### Post by Akatzman2 on 2011-04-26
> **jtarin said:**
> Where does it say in the link I gave you anything about a "#" sign?????? Please give me the step number.
If your talking about step 4 the # is not part of the command.Only the parts in bold are commands.

I'm talking about that step. Outside of that, everything is failing. I can't even mount my hd, when I try it says its busy

---

### Post by nebileix on 2011-04-27
Dear OP,

U might need to do things step by step and attached screenshot so as we can help u more efficently.

First, boot from livecd and post screenshot of this command ```
sudo fdisk -l
```

---

