---
title: "Error 22: No such partition + Usplash errors?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Deltoid on 2009-03-27
Hi everyone, I'm a complete Linux newbie that's recently been captivated by his housemate's Ubuntu laptop.  I tried "helping" her by updating her OS, but now have hit a bit of a snag.

After upgrading 7.10 to 8.04 and restarting, I'm getting "Error 22: No such partition" on trying to boot up the computer.

I did a little research around the forums/Google trying to figure things out and made a little progress.  I downloaded the Live CD and managed to boot up OK using that.  I also managed to hit "e" when loading up the computer and changing the root (hd0,6) to root (hd0,0) - which I THINK is the correct partition for my friend's laptop.

Now though, I have two problems:

1) How do I permanently change the (hd6,0) to (hd0,0), instead of manually changing it every time I boot up?

2) When I modify the above settings and boot up the computer, I get to a Kubuntu loading screen, then I'm hit with a new error saying "usplash: Setting mode 1280x1024 failed..."  Again I read around this topic and I think it has to do with my friend's widescreen laptop (1280x800) not being supported by the default Ubuntu config.  How am I supposed to change this though?

I'd really appreciate any help out there!  I'm really keen to get my friend's laptop up and running as soon as I can - especially as she put her trust in me to upgrade/fix it!

---

### Post by Deltoid on 2009-03-27
Hey, I hate to have to bump this post, but I'd really appreciate some help if anyone's able to provide it.  I've been refreshing the page for the past 30 mins hoping someone might respond.

---

### Post by desperado665 on 2009-03-27
your partition problems can be solved by first finding out exactly where your boot partition is. Boot your kubuntu livecd and from konsole enter:

```

sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1

```

One of the above commands should return your main Kubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:

```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```

If you are sure that the correct boot partition is at hd0,0 then you should be able to change to the correct partition by editing your menu.lst file.

```

gksu kate /boot/grub/menu.lst

```

That should fix your grub issues. As far as your Usplash error, I don't have the knowledge to help you there. But I will look to see what I can find out for you.

---

### Post by Deltoid on 2009-03-27
Thanks a lot dude for your help.  I'm booting up the computer now and will let you know how things go.

---

### Post by Deltoid on 2009-03-27
OK I tried what you told me to do, and sure enough it is (hd0,0).  I got to the "gksu kate /boot/grub/menu.lst" stage, but nothing really happened.  I thought "ok, well maybe nothing was supposed to happen".  I restarted the computer but I still am faced with the same Error 22 code.  I can still get around this by editing the boot commands on the spot, but I was hoping there would be a way to permanently set the (hd0,0).

Any further thoughts/suggestions?

---

### Post by Deltoid on 2009-03-27
For the usplash error, it might help if I reproduce the error message in full here:

```
Starting up ...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1024x864 failed
usplash: Using mode 1024x768
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/8f9464e4-6148-4146-991c-b02c7170b788 does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of commands.

(initramfs)
```

Oh, and I'm not sure if this makes a difference, but I used a Ubuntu CD even though the laptop primarily runs Kubuntu (with the Ubuntu interface also installed).

---

### Post by desperado665 on 2009-03-27
Ok did you use the second set of codes?

```

sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

That should reinstall grub to the correct partition.

---

### Post by Deltoid on 2009-03-27
Yep, sure did.  I got more of a "confirmatory" message after entering that suggested that it worked, but after restarting nothing really changed.  I'll try again now and see if I can copy out the message that came up after I typed in the second set of codes.

---

### Post by desperado665 on 2009-03-27
You can also try the following:

```

nano /boot/grub/menu.lst

```

That should open your menu.lst with a text editor. You should see something like this:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fc634ac-1f31-43b2-a9dd-23f2a2915e49

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

After ## ## End Default Options ## Where you see UUID and a long number, replace with root (hd0,0)

Example:
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		0fc634ac-1f31-43b2-a9dd-23f2a2915e49   
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

Change to:
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc634ac-1f31-43b2-a9dd-23f2a2915e49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

---

### Post by Deltoid on 2009-03-27
```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded. suceeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2/boot/grub/menu.lst"... suceeded
Done.

grub>
```

Just tried your nano idea.  It opened up menu.lst in a text editor, but it's a blank document...?

In the meantime, I'm downloading and burning a Kubuntu LiveCD to use, to see if that makes any difference.

---

### Post by desperado665 on 2009-03-27
ok, it's in an odd place... lol. try this:

```

nano /boot/grub/stage2/boot/grub/menu.lst

```

---

### Post by Deltoid on 2009-03-27
Really appreciate your help here, but unfortunately I still can't find that menu.lst file you're talking about.

On a slightly different front, I managed to figure out why gksu wasn't working... it wasn't installed!  Just installed it now, so yay I have a GUI for a text editor, but still, no menu.lst to edit!

> **desperado665 said:**
> ok, it's in an odd place... lol. try this:

```

nano /boot/grub/stage2/boot/grub/menu.lst

```

---

### Post by drs305 on 2009-03-27
> **Deltoid said:**
> 
Just tried your nano idea.  It opened up menu.lst in a text editor, but it's a blank document...?

You are probably looking at the live cd's /boot and not your real system /boot partition.

Try mounting your real system partition with the following and then open menu.lst:
```

sudo mkdir /mnt/temp  # if it doesn't exist
sudo mount /dev/sdXX /mnt/temp  # replace sdXX with the actual location of your system partition (for instance sdb1)
cd /mnt/temp
gksudo gedit boot/grub/menu.lst   # note no "/" before "boot"
or
kdesu kate boot/grub/menu.lst  # same note as above

```

You should also make sure the correct UUID is listed:
```

sudo blkid  # check your system partition UUID is listed in the entries

```
Your *real* fstab should now appear. Make the changes, save and reboot.

---

### Post by Deltoid on 2009-03-27
Great, that sounds good.  One quick question though: how do I find out the actual location of my system's partition?

---

### Post by drs305 on 2009-03-28
> **Deltoid said:**
> Great, that sounds good.  One quick question though: how do I find out the actual location of my system's partition?

Here are a couple of commands that can help. The first will list all your *mounted* partitions. It is a good way to view these partitions, especially regarding disk size, use and availability. Unfortunately, as I said, it only reports on *mounted* partitions so in this case it probably won't see your system partition when running the livecd.
```
df -Th
```

The second command that can help displays the devices, mounted or not, plus the partition format and the UUIDs. The UUIDs are listed in fstab and in menu.lst so being able to verify them is important.
```
sudo blkid  # or "sudo blkid -c /dev/null" if you think the UUIDs may have changed
```

The first drive will be *sda*, the second *sdb*, etc. The first partition is 1, the second 2, etc. So the second partition on the second drive would be sdb2. (Note: when using "sudo grub" to set menu.lst parameters, the partition's are identified a bit differently. The first drive is 0, the first partition is 0, so in our previous example the the second partition on the second drive is registered as 1,1 - but only when running "sudo grub" for our purposes).

To determine which drive/partition is your system partition, you can run the "sudo blkid" command. Your windows partition will be formatted NTFS, your ubuntu partition will be ext3. If you still aren't sure, you can mount any of the partitions you discover and then run the "df -Th" command.
To mount an ext3 device to explore it or edit files on that partition:
```
sudo mkdir /mnt/test  # you can name it anything
sudo mount /dev/sd**[COLOR="DarkRed"]XX[/COLOR]** /mnt/test  # substitute the actual device designation (such as sd**[COLOR="DarkRed"]b1[/COLOR]**)
df -Th
```

---

### Post by Deltoid on 2009-03-28
Thanks again for your help.  I'm not quite sure I understand what you mean after your last post.  I tried running your sudo blkid and this is what I got:

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="760dd72c-0765-428f-aa30-b04642fdee76" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="358845ae-37b5-400d-be73-aba06a4dda13" TYPE="swap" 
/dev/loop0: TYPE="squashfs"
```

What then should I put for the sdXX that you referred to previously?

---

### Post by Deltoid on 2009-03-28
Nvm, I just tried using sda1 and it worked!  Making the changes now.

---

### Post by Deltoid on 2009-03-28
OK, just loaded up menu.lst and this is what I got:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8f9464e4-6148-4146-991c-b02c7170b788 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8f9464e4-6148-4146-991c-b02c7170b788 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=8f9464e4-6148-4146-991c-b02c7170b788 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f9464e4-6148-4146-991c-b02c7170b788 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f9464e4-6148-4146-991c-b02c7170b788 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I'm changing all the (hd0,6) to (hd0,0).  I think this just might work.

---

### Post by Deltoid on 2009-03-28
Fantastic!  That trick solved my grub problems!  If I could give props on these forums I'd definitely dish them out to desperado665 and drs305.

The battle's not quite over yet though, because I'm still having usplash issues.  Any suggestions on how I can solve that?

---

### Post by drs305 on 2009-03-28
> **Deltoid said:**
> The battle's not quite over yet though, because I'm still having usplash issues.  Any suggestions on how I can solve that?

Good news about making progress. As to the usplash issues:

Startup-Manager is a gui app that can tweak various gurb menu settings. It has a section for setting resolutions and usplash themes.
To install startupmanager (universe repository enabled):
```
sudo apt-get install startupmanager
```
To run:
```
gksudo startupmanager  # or System > Administration > StartUp-Manager
```

Tweaking the settings may help solve your usplash issues.

There is a link in my signature line about using StartUp-Manager.

---

### Post by Deltoid on 2009-03-28
I couldn't install startupmanager using the method you suggested, but I did manage to get it via Applications>Add/Remove and searching for it.

After executing it in Terminal, this is what I get:

```
ubuntu@ubuntu:~$ gksudo startupmanager
Grub2 not detected
Searching for GRUB installation directory ... Grub Legacy not detected
Usplash detected
Splashy not detected
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###
```

I'm assuming this may have something to do with the application not reading from the true drive and from the LiveCD instead?  I tried mounting the image like you suggested before, but that still didn't work with the startup manager.

```
ubuntu@ubuntu:~$ cd /mnt/temp
ubuntu@ubuntu:/mnt/temp$ gksudo startupmanager
Grub2 not detected
Searching for GRUB installation directory ... Grub Legacy not detected
Usplash detected
Splashy not detected
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###
```

---

### Post by drs305 on 2009-03-28
I thought you were now able to boot into your normal ubuntu install and just had some video problems you wanted to tweak. As you discovered, startupmanager won't work from the livecd - at least run normally, There may be a way to get it to edit the mounted menu.lst but I haven't experimented with that.

---

### Post by Deltoid on 2009-03-28
> **drs305 said:**
> I thought you were now able to boot into your normal ubuntu install and just had some video problems you wanted to tweak. As you discovered, startupmanager won't work from the livecd - at least run normally, There may be a way to get it to edit the mounted menu.lst but I haven't experimented with that.

Hmm... well thanks anyway for your help.  I'm gonna keep scouring the web trying to figure out how to solve my error.  If anyone else has any suggestions, I'm definitely open to listening.

---

### Post by Deltoid on 2009-03-28
I've spent hours trying to upgrade this laptop and fix the problems the upgrade has created.  I'm starting to lose hope...

I need any seasoned Ubuntu user's advice here: Before embarking on the upgrade I thought it was wise to create a full backup of the laptop on to my external HD.  I used HUBackup for this because it seemed simplest.  I'm a little wary about the backup though, because I know HUBackup doesn't backup the *entire* contents of the HD and only certain portions of the HD.  I didn't bother changing the default settings when I made the backup.

Am I safe to assume that all of the personal files (documents, photos, etc) are in the backup I made?

And if I proceed to do a clean install of Ubuntu with the upgraded OS, will I still be able to restore the files I made in HUBackup?  Horror stories like [this one]("http://ubuntuforums.org/showthread.php?t=997186") make me quite wary!

---

### Post by Deltoid on 2009-03-28
Great news.  I fixed it.

Turns out usplash was just a red herring.  The real problem was still to do with my menu.lst pointing the in the wrong direction.

Using the information in the this thread and from this one [here]("http://ubuntuforums.org/showthread.php?t=813090"), I suspected if my root was pointing in the wrong direction, my UUID might be as well.

I ran "sudo blkid" and found my UUID to be different from the UUID in menu.lst.  I then commented out the old UUID in menu.lst, duplicated that line, and replaced the UUID with the one from "sudo blkid".  And viola!  Here I am with a non-LiveCD boot writing this post.

Thanks again to everyone for their help.  I've heard before that Ubuntu support forums are great, and I now can personally vouch for that.

---

