---
title: "Ubuntu won't start after repartitioning"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-02-22
Hello, I repartitioned my drives last night to give Ubuntu more space. I took 20 gigabytes away from Windows partition and added them to my ext3 drive. The only problem was there was an extended partition with swap under it. I couldn't move that partition with gparted so I deleted it and created a linux swap partition.

The only problem is, now I get to the splash screen with the bar going back and forth across the window, but after that I get a black screen. Any idea what I did wrong?

---

### Post by benerivo on 2009-02-22
It may be that it fails at the point where it tries to mount swap, but it's looking for the old swap partition that now no longer exists. If you load the live cd, you can use gparted to find out what the new swap partition name is, and then mount the root partition and edit the /etc/fstab file correct it. You can also check /var/log/dmesg.log to look for any error messages at the end.

---

### Post by egalvan on 2009-02-22
> **benerivo said:**
> It may be that it fails at the point where it tries to mount swap, but it's looking for the old swap partition that now no longer exists... load the live cd, use gparted to find out what the new swap partition name is, and then mount the root partition and edit the /etc/fstab file correct it. You can also check /var/log/dmesg.log to look for any error messages at the end.

Deleting and re-creating a swap partition may or may not change the drive designation, but it WILL change the UUID which is used by GRUB and most everything else in *nix these days, including 'fstab'.

You need to find the new UUID and replace the old one in fstab.

Note: I don't use UUID's, I use LABEL instead.
LABEL will not change unless the user changes them.
No more UUID problems for me!

my fstab swap entry:
[B]
LABEL=swap none swap sw 0 0[/B]

---

### Post by ronaldrand on 2009-02-22
> **benerivo said:**
> It may be that it fails at the point where it tries to mount swap, but it's looking for the old swap partition that now no longer exists. If you load the live cd, you can use gparted to find out what the new swap partition name is, and then mount the root partition and edit the /etc/fstab file correct it. You can also check /var/log/dmesg.log to look for any error messages at the end.

No dmesg.log (or dmesg) was created.

Here is my /etc/fstab file:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
/dev/sda4     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
/dev/sda1       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda3
# /dev/sda3      none            swap        sw          0   0

```

Here is the result of fdisk:
```
ubuntu@ubuntu:/media/sda4/etc$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd23d125d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12446    99972463+   7  HPFS/NTFS
/dev/sda2           12447       13973    12265627+   7  HPFS/NTFS
/dev/sda3           13974       14234     2096482+  82  Linux swap / Solaris
/dev/sda4           14235       19457    41953747+  83  Linux

```

As you can see, I tried commenting out the swap disk in fstab. It didn't help.

---

### Post by ronaldrand on 2009-02-22
> **egalvan said:**
> Deleting and re-creating a swap partition may or may not change the drive designation, but it WILL change the UUID which is used by GRUB and most everything else in *nix these days, including 'fstab'.

You need to find the new UUID and replace the old one in fstab.

Note: I don't use UUID's, I use LABEL instead.
LABEL will not change unless the user changes them.
No more UUID problems for me!

my fstab swap entry:
[B]
LABEL=swap none swap sw 0 0[/B]

I first tried changing the UUID's and that gave the same result. The only one that changed was the swap drive.

LABEL -- how do I do that on a dual-boot system?

---

### Post by benerivo on 2009-02-22
I think you can set a LABEL using gparted.

Have you tried to boot using recovery mode? I think this should boot with messages displayed, rather than with the 'splash' screen, and so maybe you can spot an error message.

---

### Post by egalvan on 2009-02-22
> **ronaldrand said:**
> I first tried changing the UUID's and that gave the same result. The only one that changed was the swap drive.

LABEL -- how do I do that on a dual-boot system?

Single-boot, dual-boot, doesn't matter.
Labels are partition-specific names you assign.

More on that later. For now,
your fdisk and fstab seem to agree that sda3 is your swap partition.
so the problem is probably something else.

Have you tried booting into 'rescue mode" ?

If not, try it and accept the 'fix-it' options.

When you wiped that extended partition, were you ABSOLUTELY sure there was nothing but a 'swap' there?

At this point, I don't think this is a 'missing swap' problem.

ErnestG


P.S.
All my *nixes dual-boot at least Windows, a few also triple/quaduple boot other *nixes.
All use drive labels.

---

### Post by egalvan on 2009-02-22
Oh, and the EASIEST way to assign labels is with MS Windows, especially 2k/XP. How Sad.

Right click on the drive you want to rename, then input the name.
PREFERABLY with no spaces.

The latest versions of gparted also have a good label option.
slightly older versions would wipe the partition after setting a label. USE WITH CAUTION.

---

### Post by ronaldrand on 2009-02-22
I'm going through recovery mode. It's hanging for a long time on "setting preliminary keymap". Is that normal?

---

### Post by ronaldrand on 2009-02-22
I got into recovery mode. Doing an fsck now. I didn't see any errors except for read-only errors loading some libraries (I think.)

---

### Post by caljohnsmith on 2009-02-22
Losing the Ubuntu splash screen is a common symptom of when the UUID of your swap partition changes, because the /boot/initrd images are all hard-coded with the swap UUID. Therefore, I would recommend reassigning the old swap UUID to your new swap partition so you won't have to regenerate all your initrd images to use the new UUID, nor do you have to change any system files. Then you should get back your Ubuntu splash screen. If you would like to do that, how about posting:
```
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
```
And we can work from there if you want.

---

### Post by ronaldrand on 2009-02-22
[QUOTE=egalvan;6782014]
If not, try it and accept the 'fix-it' options.
[QUOTE]

Do you mean "Try to fix X-Server"? Because that's all I see.

---

### Post by ronaldrand on 2009-02-22
> **caljohnsmith said:**
> Losing the Ubuntu splash screen is a common symptom of when the UUID of your swap partition changes, because the /boot/initrd images are all hard-coded with the swap UUID. Therefore, I would recommend reassigning the old swap UUID to your new swap partition so you won't have to regenerate all your initrd images to use the new UUID, nor do you have to change any system files. Then you should get back your Ubuntu splash screen. If you would like to do that, how about posting:
```
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
```
And we can work from there if you want.

I do get the splash screen. I get a black screen after that. I was able to log into my partition using recovery mode. All my apps started up. Anyway, here is what you asked for:

```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="2AEAC0BC36D0443A" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda3: UUID="ca178b54-ebda-4cee-a462-66f80a5140ac" TYPE="swap" 
/dev/sda4: UUID="f5b0a249-9e3f-476e-adad-736c7f19c019" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

```

```

ubuntu@ubuntu:~$ cat /mnt/sda4/etc/initramfs-tools/conf.d/resume
RESUME=UUID=13a75aa5-5833-4e53-9ef4-1f217c1843de

```

Thanks!

---

### Post by caljohnsmith on 2009-02-22
OK, how about doing:
```
sudo mkswap -L "swap" -U 13a75aa5-5833-4e53-9ef4-1f217c1843de /dev/sda3

```
Then you should be able to use Ernest's entry in your fstab for swap:
```
LABEL=swap none swap sw 0 0
```
Try adding that entry to your fstab, reboot, let us know if you get the splash screen, and also post the output of:
```
sudo blkid -c /dev/null
cat /etc/fstab
free
```

---

### Post by egalvan on 2009-02-22
Never Fear, caljohnsmith is here!
All boot problems quake with fear!
Their annihilation is near!

OK, enough of that...

What does the line

```
cat /etc/initramfs-tools/conf.d/resume

```
give us?

What does that UUID point to?

Many thanks, caljonhsmith...

ErnestG

---

### Post by caljohnsmith on 2009-02-22
> **egalvan said:**
> 
What does the line

```
cat /etc/initramfs-tools/conf.d/resume

```
give us?

What does that UUID point to?

Hi Ernest, I believe that file is for when you "suspend" your computer, it writes the RAM to the file/partition specified in that resume file. But that's also the file used to determine the UUID of swap when creating the initrd images, and as I mentioned in my first post, once the images are created, they are hard-coded with that swap UUID. So instead of changing the /etc/fstab file, the above resume file, and regenerating all the initrd images to use a new swap UUID, usually it is much simpler and easier to just reassign the original swap UUID to the new swap partition. Then everything should work OK again, assuming there are no other issues. :)

---

### Post by ronaldrand on 2009-02-22
> **caljohnsmith said:**
> OK, how about doing:
```
sudo mkswap -L "swap" -U 13a75aa5-5833-4e53-9ef4-1f217c1843de /dev/sda3

```
Then you should be able to use Ernest's entry in your fstab for swap:
```
LABEL=swap none swap sw 0 0
```


Okay, did that. I still get the black screen.

> 
Try adding that entry to your fstab, reboot, let us know if you get the splash screen, and also post the output of:
```
sudo blkid -c /dev/null
cat /etc/fstab
free
```

I always get a splash screen. I get a black screen after the splash screen finishes loading.

```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="2AEAC0BC36D0443A" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda3: LABEL="swap" UUID="13a75aa5-5833-4e53-9ef4-1f217c1843de" TYPE="swap" 
/dev/sda4: UUID="f5b0a249-9e3f-476e-adad-736c7f19c019" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

```

```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```

---

### Post by egalvan on 2009-02-22
> **caljohnsmith said:**
> Hi Ernest, I believe that file is for when you "suspend" your computer, it writes the RAM to the file/partition specified in that resume file. But that's also the file used to determine the UUID of swap when creating the initrd images,

OK, got that... swap is used for 'suspend' and hibernate, so this make perfect sense. Thanks.


>  as I mentioned in my first post, once the images are created, they are hard-coded with that swap UUID. So instead of changing the /etc/fstab file, the above resume file, and regenerating all the initrd images to use a new swap UUID, just reassign the original swap UUID to the new swap partition. Then everything should work OK again, assuming there are no other issues. :)

OK, this again makes sense.

But running 

```
cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=**c53ffb77-1161-4c00-8fd3-6523e78db3e9**

```

on my machine returns a UUID that I don't recognize. (not that I would, it's far too long).

```
sudo blkid -c /dev/null
/dev/sda1: UUID="**805424F85424F318**" LABEL="gx280-xp" TYPE="ntfs" 
/dev/sda5: UUID="**0933d680-d893-40fa-a01d-3c819f0b2ea3**" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="**3119f61a-7ab2-4b91-b9c8-44fa795dfae5**" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" LABEL="swap" UUID="**7f9f938e-90da-4c2d-a75a-bd680b97aa4e**" 

```

top shows:
Swap: 2899692k total,  0k used.

ErnestG

---

### Post by caljohnsmith on 2009-02-22
It sounds like you probably have a different issue, ronaldrand, than just a problem with your swap UUID changing. Also, you didn't post the output of the "free" command; does that show you have swap space again? Is it safe to assume you got the Ubuntu splash screen with the progress bar before deleting/recreating your swap partition? How about trying this: first reboot, and then on start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
vga=normal
```
Press enter to save the change, and finally "b" to boot. Does that make any difference?

**Ernest**: I'm curious then, are you able to "suspend" your computer since your swap UUID does not agree with what is in the resume file?

---

### Post by egalvan on 2009-02-22
> **caljohnsmith said:**
> 
**Ernest**: I'm curious then, are you able to "suspend" your computer since your swap UUID does not agree with what is in the resume file?

I haven't tried "suspend" on this machine... it's sorta my "work" machine here in my bedroom.

Let me try it... back in a few...

Maybe ronald has similiar problems?

---

### Post by egalvan on 2009-02-22
OK, I'm back...

Boy, I'm embarrassed by this...

How does one "suspend" a desktop?

There's no handy "suspend" button...

Then again, the BIOS sometimes has options for the power button?

Oh well..

ErnestG

---

### Post by ronaldrand on 2009-02-22
> **caljohnsmith said:**
> It sounds like you probably have a different issue, ronaldrand, than just a problem with your swap UUID changing. Also, you didn't post the output of the "free" command; does that show you have swap space again?

Sorry, here it is. I'm running off the Ubuntu live CD.

```

ubuntu@ubuntu:/mnt/sda4/boot/grub$ free
             total       used       free     shared    buffers     cached
Mem:       2007256     760360    1246896          0      85460     471980
-/+ buffers/cache:     202920    1804336
Swap:      2096472          0    2096472

```

> 
 Is it safe to assume you got the Ubuntu splash screen with the progress bar before deleting/recreating your swap partition?

Yes, everything was running fantastically before.


**Ernest**: I'm curious then, are you able to "suspend" your computer since your swap UUID does not agree with what is in the resume file?
> 
 How about trying this: first reboot, and then on start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
vga=normal
```
Press enter to save the change, and finally "b" to boot. Does that make any difference?


Thanks. I'll try it.

---

### Post by ronaldrand on 2009-02-22
This time I tried without the splash screen and without quiet mode. I got this prompt:

resume: Could not stat the resume device file '/dev/sda5'
Please type in the full path name to try again
or press ENTER to boot the system:

After manually putting in /dev/sda5 it seemed to boot up normally, although not in the right resolution. Any idea where sda5 is saved?

Update: I reinstalled uswsusp and that made that error go away.

---

### Post by caljohnsmith on 2009-02-22
Ronaldrand, so you don't get that error after reinstalling uswsusp, but what about the Ubuntu splash screen with the progress bar? Are you still missing that?

---

### Post by ronaldrand on 2009-02-22
> **caljohnsmith said:**
> Ronaldrand, so you don't get that error after reinstalling uswsusp, but what about the Ubuntu splash screen with the progress bar? Are you still missing that?

Mostly everything is good now. There were lots of little issues I had to fix, like rebuilding the top panel and installing Nvidia drivers, reconfiguring my Virtualbox drive, etc. But now the splash screen stops, and even though I have quiet set, it goes into ouput and the first line reads &#8220;Reading files needed to boot&#8221; and then it proceeds until login.

It's annoying and I would like to fix it. The only fix I found on the internet didn't work for me. Any ideas?

P.S. Thank you (and the other guys) for all your help.

---

### Post by caljohnsmith on 2009-02-22
How about trying:
```
sudo update-initramfs -u -k all
```
Then reboot, and let me know if anything changes.

---

### Post by ronaldrand on 2009-02-22
Same thing. :(

---

### Post by caljohnsmith on 2009-02-23
When you ran the "update-initramfs" command, were you booted into your Ubuntu install? Some of the commands you've been posting are from your Live CD, so are you having trouble even booting into your Ubuntu install? If you can still boot into your Ubuntu install OK, please post the output of all the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
free
```

---

### Post by ronaldrand on 2009-02-23
> **caljohnsmith said:**
> When you ran the "update-initramfs" command, were you booted into your Ubuntu install? Some of the commands you've been posting are from your Live CD, so are you having trouble even booting into your Ubuntu install? If you can still boot into your Ubuntu install OK, please post the output of all the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
free
```

Good morning to you! Yes, I'm in my Ubuntu install and I ran the update-intramfs from the Ubuntu install. Here's what you requested.

```

[ubuntu] ~$ sudo blkid -c /dev/null
/dev/sda1: UUID="2AEAC0BC36D0443A" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="PRESARIO_RP" TYPE="ntfs" 
/dev/sda3: LABEL="swap-here" UUID="fa43b6e7-7e49-4f82-a0c4-faf2a932e2cc" TYPE="swap" 
/dev/sda4: UUID="f5b0a249-9e3f-476e-adad-736c7f19c019" TYPE="ext3" 

[ubuntu] ~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
/dev/sda4     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
/dev/sda1       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda3
UUID=fa43b6e7-7e49-4f82-a0c4-faf2a932e2cc none swap sw 0 0

[ubuntu] ~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=fa43b6e7-7e49-4f82-a0c4-faf2a932e2cc

```

---

