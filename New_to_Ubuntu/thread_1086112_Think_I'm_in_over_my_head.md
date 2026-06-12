---
title: "Think I'm in over my head"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-03
Installed 8.10 last night. The 1st problem I noticed is that I can no longer boot into XP. It goes directly into Unbuntu. My main problem is that I'm very new, and a lot of the terminology used here in the forums is foreign to me. I've only used Windows O.S in the past. I originally partioned my H.D. for 8.10. I probably should have just went with the the standard install rather then manual.  A few contributers suggested that I do a fresh install. Since I don't have access to XP, can i delete the existing partitions from unbuntu, so there are no partitions before i reinstall?  if so, any one mind pointing me in the right direction on a how to? to re-install, do i simply run the install all over again from the CD, or do i need to remove the existing O.S.?  Sorry for all the questions.  I guess I was hoping that with my limited knowledge that I'd be able to get a turn key O.S....should have known better.

---

### Post by llamabr on 2009-03-03
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

You don't need to delete your os, doing a fresh install will do so for you.

You're very close to a turn key os.  You only made a little mistake.  Don't make it again, and you're on your way.

---

### Post by taurus on 2009-03-03
If you want to reinstall, you do not need to remove the current partitions.  Boot from the LiveCD and tell the installer to use the whole disk when you get to the partition part.  But if you want to remove/delete the partitions first, then you can use gparted (System -> Administration -> Partition Editor) to delete all the partitions on your harddrive.  You probably need to unmount the swap partition (click that partition with the right button and use the swapoff to unmount it) first before you can delete it.  Then, create one partition that takes up the whole harddrive and format it to ext3.  Save it and now do the install.

---

### Post by llamabr on 2009-03-03
But note that the above advice is only if you want to delete, or resize your partition.  If your partition sizes are correct, then you're just ready to go.

---

### Post by Sef on 2009-03-03
Have you dual booted or simply installed Ubuntu over XP?  To find out which one you did, follow these directions:

Applications > Accessories > Terminal

then copy and paste or type this code in the terminal:

```
sudo fdisk -l
``` (Small L)

Then copy and paste the results in a new post here.

---

### Post by donkyhotay on 2009-03-03
Kind of obvious but when your computer is turning on you should have 2-3 seconds of seeing the GRUB bootloader prompting to you press ESC key. When you do so it will show you a list of all the currently installed OS's and allow you to boot into the one that want. You can also modify GRUB to make windows the default if no key is pressed rather then ubuntu but I don't know how to do that since I ubuntu is the only OS I have. (c: Now if you don't have an option for XP then you have a more serious issue and should begin following the advice the others have posted here.

---

### Post by lindsay7 on 2009-03-03
You might try this. Download the "Startup Manager" from the synaptic package manager. It should show up under Administration. Run it and it should give you the start up options to either set a default start up or prompt for one.

---

### Post by presence1960 on 2009-03-03
> **js@lloyd said:**
> Installed 8.10 last night. The 1st problem I noticed is that I can no longer boot into XP. It goes directly into Unbuntu. My main problem is that I'm very new, and a lot of the terminology used here in the forums is foreign to me. I've only used Windows O.S in the past. I originally partioned my H.D. for 8.10. I probably should have just went with the the standard install rather then manual.  A few contributers suggested that I do a fresh install. Since I don't have access to XP, can i delete the existing partitions from unbuntu, so there are no partitions before i reinstall?  if so, any one mind pointing me in the right direction on a how to? to re-install, do i simply run the install all over again from the CD, or do i need to remove the existing O.S.?  Sorry for all the questions.  I guess I was hoping that with my limited knowledge that I'd be able to get a turn key O.S....should have known better.

Before you do anything especially deleting or formatting partitions, why don't you run the command Sef asked you to run, then post the results. If your Windows install is still in tact it may just be a simple editing of the menu.lst file to get your windows to show up on grub menu.

Don't get discouraged, mistakes are a great way to learn. If you are like a lot of people your initial windows day were probably just the same. Linux is not as hard as you think, it is just different than what you have been accustomed to. Most people hate or resist change. Hang in there and reap the benefits of Linux.

---

### Post by js@lloyd on 2009-03-03
Ok. First, here is what I see when I hit Esc while it's loading.

Ubuntu 8.10, kernel 2.6.27-7 generic
Ubuntu 8.10, kernel 2.6.27-7 generic (recovery mode)
Ubuntu 8.10, memtest 86+

results for sudo fdisk -1

jsinlloyd@jsinlloyd-desktop:~$ sudo fdisk -l
[sudo] password for jsinlloyd: 

It doesn't allow me to type anything in the password area.  

Do i need to boot from the Live CD for this?  I did this yesterday, and these were the results.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb5feb5f

Device Boot Start End Blocks Id System
/dev/sda2 * 1 14593 117218241 f W95 Ext'd (LBA)
/dev/sda5 5743 14593 71095626 7 HPFS/NTFS
/dev/sda6 1 249 1999998 82 Linux swap / Solaris
/dev/sda7 250 5742 44122491 83 Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by presence1960 on 2009-03-03
JS, well grub is actually installed, it is just missing the info to load windows. I don't have the time right now but I can tell you it is most likely a simple matter of adding the Windows info to your menu.lst file so windows will show up in grub. Hopefully someone else will be able to help you now, if not be patient. Don't go formatting or reinstalling for now.

---

### Post by lisati on 2009-03-03
> **js@lloyd said:**
> 
jsinlloyd@jsinlloyd-desktop:~$ sudo fdisk -l
[sudo] password for jsinlloyd: 

It doesn't allow me to type anything in the password area.  

When sudo asks for a password, just type it in: it won't show up on the screen but will still be accepted. This a normal part of Ubuntu's security.

---

### Post by rafac24 on 2009-03-03
On the Terminal, when it requests your password, it doesnt actually show that it is typing but it is registering the keystrokes. So just type your password and press the Enter button anyway.

---

### Post by neanderthalman on 2009-03-03
Open a terminal window, and type the following command.

```
gksu gedit /boot/grub/menu.lst
```

This will open up the grub configuration file with root privileges.

Scroll down towards the bottom, and find a number of entries that look something like this:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ead73abd-0e3b-41c8-9cab-3e683e08f502
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ead73abd-0e3b-41c8-9cab-3e683e08f502 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

Paste in the following entry after what is there, and it will add an entry to load windows - assuming windows is located on the first partition of the first hard drive.

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Save the file, close the editor, and restart the computer.  When the grub menu appears, there should be an option at the end of the list to load windows.

---

### Post by js@lloyd on 2009-03-04
Well, i tried the prior post, but no luck.  Do i need to make changes from Professional to Home Edition?  Also, mine shows as (hd0,6), not (hd0,0).  I tried both, but no luck.  

Also, now I can't connect to the Internet, but I'll worry about that later.  One last thing, not sure if this has anything to do with the issue. It takes quite a long time to shut down....5 minutes or so.  

I have all day open, so I hope I can dial all this in today.

---

### Post by Big_Croc7 on 2009-03-04
What exactly is it you want to do?  If you're trying to restore access to your Windows installation, it looks like you probably have it on here:

/dev/sda5 5743 14593 71095626 7 HPFS/NTFS

So, you need to edit the Grub menu and add this
```

title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```
It's hd(0,4) instead of 5 because Grub starts at 0 and Linux starts at 1.

It's probably a good idea to copy the file first:
cp /boot/grub/menu.lst ~/menu.lst

---

### Post by Big_Croc7 on 2009-03-04
Do you have an entry like that already?  It might help if you post the whole file here.

---

### Post by js@lloyd on 2009-03-04
Still no luck.  Here's what i have.

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
timeout		3 
 
## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 
 
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
# kopt=root=UUID=f844df1e-afeb-4607-a528-46887fb06c6e ro 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=f844df1e-afeb-4607-a528-46887fb06c6e 
 
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
 
title		Ubuntu 8.10, kernel 2.6.27-7-generic 
uuid		f844df1e-afeb-4607-a528-46887fb06c6e 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f844df1e-afeb-4607-a528-46887fb06c6e ro quiet splash  
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 
 
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
uuid		f844df1e-afeb-4607-a528-46887fb06c6e 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f844df1e-afeb-4607-a528-46887fb06c6e ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 
 
title		Ubuntu 8.10, memtest86+ 
uuid		f844df1e-afeb-4607-a528-46887fb06c6e 
kernel		/boot/memtest86+.bin 
quiet 
 
# title		Windows XP Professional 
# root		(hd0,4) 
# makeactive 
# chainloader	+1 
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by chamber on 2009-03-04
> # title Windows XP Professional 
# root (hd0,4) 
# makeactive 
# chainloader +1 
### END DEBIAN AUTOMAGIC KERNELS LIST

Try removing the #'s

---

### Post by cc8balla on 2009-03-04
> **chamber said:**
> Try removing the #'s

Exactly, when you have ##'s its commenting out what you want, and the file will just ignore what's after the #.

---

### Post by js@lloyd on 2009-03-04
That seemed to work, but I still have a problem.
I choose Windows XP Professional, but I get this,

Error 12: Invalid device requested
Press any key to continue

As I mentioned earlier, I have XP Home Edition...not sure if that makes a difference.

Thanks for all the help thus far.  I really appreciate it.

---

### Post by s.fox on 2009-03-04
What happens if you press a key?

---

### Post by js@lloyd on 2009-03-04
It just reverts me back to the selection options...Ubuntu generic, recovery mode, memtest86+ and XP Professional.

---

### Post by js@lloyd on 2009-03-04
So close, yet so far.  Can anyone provide any help with resloving this problem? 

Thanks.

---

### Post by avtolle on 2009-03-04
First, you added the entry for your XP (go ahead and rename it to XP Home Edition) in the wrong place; those lines should go below the End... line. Once you move them, uncomment them (IIRC). Then try it again.

---

### Post by stchman on 2009-03-04
When you installed Ubuntu did you first partition your drive?  If you selected whole disk then Windows is gone.

---

### Post by js@lloyd on 2009-03-04
> **avtolle said:**
> First, you added the entry for your XP (go ahead and rename it to XP Home Edition) in the wrong place; those lines should go below the End... line. Once you move them, uncomment them (IIRC). Then try it again.

Is removing the # 'uncommenting' them?  
Should it look like this, ?

### END DEBIAN AUTOMAGIC KERNELS LIST
 title Windows XP Home Editition 
 root (hd0,4) 
 makeactive 
 chainloader +1

---

### Post by s.fox on 2009-03-04
Hi,

Removing the #'s will uncomment the line.  

P.S It looks fine to me

---

### Post by js@lloyd on 2009-03-04
I went ahead and changed it, to how I typed it above, but still the same result when I try to boot XP. 
Error 12: Invalid device requested
Press any key to continue
Takes me back to my options to boot, below it says use arrow keys to select......to boot teh selected OS, 'e' to edit the commands before booting, or 'c' for a command-line.  
If i choose 'e', this is the result
root (hd0,4)
makeactive
chainloader +1

---

### Post by jocheem67 on 2009-03-04
Maybe go inti ubuntu and install gparted:

> sudo apt-get install gparted 
( in the terminal )

then 

> sudo gparted
( type your password )

Then at least you can examine your drives...which will give you clarity in if and where your ntfs-partition is stored.

---

### Post by gletob on 2009-03-04
> **jocheem67 said:**
> Maybe go inti ubuntu and install gparted:


( in the terminal )

then 


( type your password )

Then at least you can examine your drives...which will give you clarity in if and where your ntfs-partition is stored.

That's already been accomplished with the sudo fdisk -l command.

To the OP (js@lloyd) do you still have your original XP cd?
Don't do anything with it YET.

---

### Post by MasterNetra on 2009-03-04
Fyi you can display code in your messages without issue by putting between
 [ code ] and [ /code ] just remove the spaces.

Just thought you should know. :)

---

### Post by mlentink on 2009-03-04
> **js@lloyd said:**
> So close, yet so far.  Can anyone provide any help with resloving this problem? 

To all (incl mod's): this thread is continued at: [http://ubuntuforums.org/showthread.php?t=1087123&page=2](http://ubuntuforums.org/showthread.php?t=1087123&page=2)

Please close this one...

---

### Post by js@lloyd on 2009-03-05
> **gletob said:**
> That's already been accomplished with the sudo fdisk -l command.

To the OP (js@lloyd) do you still have your original XP cd?
Don't do anything with it YET.

Yes, I do still have my XP cd. Thanks..JS

---

### Post by jocheem67 on 2009-03-05
[http://img91.imageshack.us/img91/6167/91835870.png](http://img91.imageshack.us/img91/6167/91835870.png)

As you can see my partitions are all primary, there is no need to create logical ones up to a certain amount on one drive.

You could reinstall xp firstly, leave an amount of space unassigned and install ubuntu on the free space later on.

[https://help.ubuntu.com/8.10/switching/installing.html](https://help.ubuntu.com/8.10/switching/installing.html)

A good guide, it's the official one.

good luck

---

