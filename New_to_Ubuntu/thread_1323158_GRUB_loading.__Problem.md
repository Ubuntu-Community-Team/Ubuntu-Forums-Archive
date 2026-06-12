---
title: "GRUB loading.  Problem"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Crosboro on 2009-11-11
I decided to try Ubuntu and installed the newest version on an IMB ThinkPad that has Windows XP. I did the install using the side-by-side option.  When rebooting, got to screen to select which to use, but nothing happened no matter what I clicked on.  So, I did a reinstall.
Now, after the initial ThinkPad screen, I get the following:

GRUB Loading.
error: no such partition
grub rescue>

Can anyone tell me what to enter here?  I have no idea and have searched through this forum but can't find the same issue.

Thanks for your help.

---

### Post by kansasnoob on 2009-11-11
If you can boot the live CD choose try Ubuntu without changes to your computer and then from the "Live Desktop" follow the steps in this link to post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Crosboro on 2009-11-11
> **kansasnoob said:**
> If you can boot the live CD choose try Ubuntu without changes to your computer and then from the "Live Desktop" follow the steps in this link to post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Nope, can't even boot.  Just the initial screen then the GRUB screen.  Have  tried with the CD in at start and then putting it in when I get this screen, and nothing.  
(I'm using another comp to post here).

---

### Post by Buuntu on 2009-11-11
Your grub is pointing to the old grub, which is now deleted.  
Best way to fix this is to use your Windows XP CD.  Once you have it, boot off of it by changing your boot priority.  After loading, enter the Recovery Console when it gives you the choice (usually you have to press R).  From there, type 'fixmbr' into the command prompt. Then restart and remove your XP CD.

**To change the boot priority, you will have to enter your BIOS setup when you first start your computer.  Usually there will be some indication of what to press.  Inside the setup, you need to change the boot priority so that CD/DVD is above hard disk.  Once you've done that, just make sure to save and exit.

---

### Post by kansasnoob on 2009-11-11
> **Crosboro said:**
> Nope, can't even boot.  Just the initial screen then the GRUB screen.  Have  tried with the CD in at start and then putting it in when I get this screen, and nothing.  
(I'm using another comp to post here).

Well you were obviously able to boot the live CD to install. I'm saying if you can get the live CD in again (should be possible to open the CD tray even while stalled as you describe), and then reboot (even if it means a hard reboot) then you should get the options screen again:

[ATTACH]135790[/ATTACH]

Note: Image shamelessly stolen from Herman's Dual Boot Guide:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Crosboro on 2009-11-11
> **Buuntu said:**
> Your grub is pointing to the old grub, which is now deleted.  
Best way to fix this is to use your Windows XP CD.  Once you have it, boot off of it by changing your boot priority.  After loading, enter the Recovery Console when it gives you the choice (usually you have to press R).  From there, type 'fixmbr' into the command prompt. Then restart and remove your XP CD.

**To change the boot priority, you will have to enter your BIOS setup when you first start your computer.  Usually there will be some indication of what to press.  Inside the setup, you need to change the boot priority so that CD/DVD is above hard disk.  Once you've done that, just make sure to save and exit.

Unfortunately, the XP CD is long gone--the comp is 5 years old and who knows where the CD is.  That's why I tried Ubuntu on this one, as I was just keeping it as a back-up.  
That being said, I don't understand why this would be the "old grub", as I downloaded the latest version.  I did change the boot order, but that didn't help.
Thanks for trying.

---

### Post by Crosboro on 2009-11-11
> **kansasnoob said:**
> Well you were obviously able to boot the live CD to install. I'm saying if you can get the live CD in again (should be possible to open the CD tray even while stalled as you describe), and then reboot (even if it means a hard reboot) then you should get the options screen again:

[ATTACH]135790[/ATTACH]

Note: Image shamelessly stolen from Herman's Dual Boot Guide:

[http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/%7Eherman546/index.html")


I was able to boot after the first installation, but after the second, was no longer able to.  I've tried with the CD in when I turn it on as well as after it starts, but still get only the initial and "grub" screens.
Thanks for trying.

---

### Post by Buuntu on 2009-11-12
You have to change the boot order so CD is listed above your hard disk.  

I recommend downloading a pirated version of XP then if you no longer have one, it can be a big help when dealing with a dual boot.  I don't mean to encourage piracy but it will be helpful ^^.

---

### Post by Crosboro on 2009-11-14
> **kansasnoob said:**
> Well you were obviously able to boot the live CD to install. I'm saying if you can get the live CD in again (should be possible to open the CD tray even while stalled as you describe), and then reboot (even if it means a hard reboot) then you should get the options screen again:

[ATTACH]135790[/ATTACH]

Note: Image shamelessly stolen from Herman's Dual Boot Guide:

[http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/%7Eherman546/index.html")


Ok, tried again today and found I had not moved the proper CD drive to the top of the list.  Did so and was able to get into Ubuntu using the trial basis.  I was going to install it again, and see that it's already installed twice, but they don't work.  So, I'm downloading it again and do another install.  Meanwhile, any input on how I can delet the two installations already there?  Thanks.

---

### Post by kansasnoob on 2009-11-14
> **Crosboro said:**
> Ok, tried again today and found I had not moved the proper CD drive to the top of the list.  Did so and was able to get into Ubuntu using the trial basis.  I was going to install it again, and see that it's already installed twice, but they don't work.  So, I'm downloading it again and do another install.  Meanwhile, any input on how I can delet the two installations already there?  Thanks.

Well you're making a very huge mess!

Now that you can boot the Live CD please post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

That will give us a starting point.

If you're impatient you'll only end up with a bigger mess!

---

### Post by sandyd on 2009-11-14
i cant remember exactly where, but if you look around in the menus of the livecd, there should be ann app called gparted

---

### Post by kansasnoob on 2009-11-14
> **carlee said:**
> i cant remember exactly where, but if you look around in the menus of the livecd, there should be ann app called gparted

I think the OP is going to need some specific help regarding what to delete, what to create, etc.

It may even be as simple as getting one of the Ubuntu installs to boot and then deleting the other.

I recently had a distant family member bring me their box and they'd tried to "upgrade" using the live CD several times. They had 8 Ubuntu's none of which booted and their Windows was crunched to where it had no free space.

A person can't just keep installing and installing without knowing what they're doing.

---

### Post by Crosboro on 2009-11-14
> **kansasnoob said:**
> Well you're making a very huge mess!

Now that you can boot the Live CD please post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

That will give us a starting point.

If you're impatient you'll only end up with a bigger mess!

Ok, startup gives me a screen with 5 options:
Try Ubuntu without any change to your computer
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk

Check disc and Test memory do just that.  Boot from first hard disk kicks me back the the frozen grub screen.  Try Ubuntu gets me to Ubuntu. 

No code anywhere that you mention above.  Where would I find that?

---

### Post by Crosboro on 2009-11-14
> **carlee said:**
> i cant remember exactly where, but if you look around in the menus of the livecd, there should be ann app called gparted

Ok, found the gparted app.  That shows:

/dev/sda1  with the label IBM_PRELOAD
/dev/sda2  and under that 4 sub-partitions with file sytems named
   ext4
   ext4
   linux-swap
   linux-swap

What would I do next?

---

### Post by Aratrix on 2009-11-14
You have to paste that code into a terminal. So what you need to do is:
1) use the live CD and choose the try ubuntu without any changes option
2) Open a terminal: Applications -> Accessories -> Terminal
3) in the window that opens, you will be able to type the code that Kansasnoob posted and hit enter.
4) copy the output back here on the forums.

---

### Post by ranch hand on 2009-11-14
You can get to the forums on the Live CD too.  Just work from there.

---

### Post by Crosboro on 2009-11-14
> **kansasnoob said:**
> Well you're making a very huge mess!

Now that you can boot the Live CD please post the output of:

```
sudo fdisk -l
```BTW that's a lower case L.

That will give us a starting point.

If you're impatient you'll only end up with a bigger mess!


Here's the output:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3977    31945221    7  HPFS/NTFS
/dev/sda2            3978        4864     7124827+   5  Extended
/dev/sda5            3978        4371     3164773+  83  Linux
/dev/sda6            4820        4864      361431   82  Linux swap / Solaris
/dev/sda7            4372        4792     3381651   83  Linux
/dev/sda8            4793        4819      216846   82  Linux swap / Solaris

Partition table entries are not in disk order

---

