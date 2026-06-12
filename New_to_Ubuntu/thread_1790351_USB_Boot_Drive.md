---
title: "USB Boot Drive"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Billisnice on 2011-06-24
When i try to create a start up USB for my dell mini 9 ver 10,04 netbook on a machine with Ubuntu 11.04 it stops two times and i have to put in my password and it says it is ready at the end but does not work.

I use System>admin>startup disk creator as it is working I get this msg  "system policy prevents installing the bootloader" two times. I am only one on the 11.04 machine with admin rights.

---

### Post by cariboo on 2011-06-25
It would help if you explained what doesn't work means, does it boot at all? Do you see the initial screen with the little man and keyboard? Does it seem to boot, then stop at a black screen?

---

### Post by Billisnice on 2011-06-25
It works on the flash drive awhile and ask for my password afterit reads "creating a persistent file" it works some more and says "creating an ext2 filesystem" stops again and ask for password and says "system policy prevents mounting." It now says it is complete and ready to run on other puters...

I put in the dell mint 9 and it loops saying

vesamenu.c32: not a com32r image
boot

I am not good at puter, hope this is what you need..thanks

---

### Post by varunendra on 2011-06-25
> **Billisnice said:**
> 
I put in the dell mint 9 and it loops saying

vesamenu.c32: not a com32r image
boot
I've once had the same problem a few days ago. I created the live usb flash from Linux Mint 11 KDE (64 bit). Creation finished without errors. But when I tried to boot the same system with that USB flash drive, it started booting, then gave the same error message (as much as I remember). Retried a few more times rebooting the system, but the result was same.

I didn't bother to troubleshoot the error though. I simply recreated the live flash using Ubuntu 10.04, and it worked.


**_EDIT_:** 
There seem to be a plenty of solutions/workarounds for this. Most of them accumulated here: [http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

Quick-Fix (needs to be done everytime you boot):
When you get this error, hit "tab" button on keyboard > type "live" > hit enter >> everything okay!!

Permanent fix: Downgrade syslinux to Ubuntu 10.04. (I don't understand myself what it means!! Just copy-paste? mabe.. ;))

---

### Post by Billisnice on 2011-06-25
I could not figure it out and downloaded unetbootin and it worked. After installing 10.10 netbook on my dell mini 9 and reboot I am getting  

GRUB RESCUE prompt

Now what? thanks

---

### Post by toor58 on 2011-06-25
Try the "dd" command. 

```
USB formatted to Fat32

Unmount  USB

In terminal: sudo dd if=/path/to/iso/ubuntu-10.04-desktop-i386.iso of=/dev/sd**X **bs=4M

sudo sync


```

The bold **X** is for your USB probably, sdb or sdb1,but use this command in terminal to make sure:

```
mount
```

Thuis will give you a good usb. If not then you have a corrupt download.

Good luck.

---

### Post by Billisnice on 2011-06-25
I am confused. I am a dumb butt


I boot from my USB drive and go to the terminal and type 

"sudo dd if=/path/to/iso/ubuntu-10.04-desktop-i386.iso of=/dev/sdX bs=4M"

"sudo sync"


then in the terminal I type "mount"? Or do i type mount first to find sd is? 

Without the "

---

### Post by Billisnice on 2011-06-25
I am not sure of which one I am looking for? sdb1 or sda2? May something else...thanks

Copy of terminal after typing in mount..

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/mmcblk0p1 on /media/81690032-c8cb-4acd-bbf1-744188ba5844 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
ubuntu@ubuntu:~$

---

### Post by Billisnice on 2011-06-25
Now i have a flash drive i can not delete files off of it with ubuntu or my xp machine,  and when i put in my mini and turn on it does not recognize any files on the USB. I been trying to get this fixed since yesterday, got about 12 hours of searching the net, ect. it is one bump after another.

I am going to reformat the mini with windows xp. Mark s. has done a lot of good, but he needs to back up, destroy unity for good and fix annoying bugs and work around's. Stop jumping from x to y.

---

### Post by varunendra on 2011-06-26
@Billisnice,
When toor58 suggested the dd command, he actually was suggesting another way to make the usb drive work, not a solution to your GRUB RESCUE prompt. He should have clarified it, as it could confuse anyone who has no idea what the command did. Besides, it was meant to be performed while booting from another media (Hard disk, cd, etc.) not the usb drive itself. You simply can not unmount the drive from where you are running the system!

[COLOR=DarkRed]So in short, after you successfully made the usb drive work (it does not matter you used unetbootin or whatever else), then your original problem for this thread was solved.[/COLOR] For GRUB RESCUE prompt, you should have searched other threads, or started a new one of your own if required.

The reason for your usb drive being unrecognizable again must be some mistake on your part (maybe the incorrect use of dd command or something alike that may have corrupted filesystem on it).

One more thing - you mentioned that you installed 10.10 on dell mini: > **Billisnice said:**
> ....After installing 10.10 netbook on my dell mini  9 and reboot I am getting  
GRUB RESCUE prompt
and then in your last post, you are criticizing unity:> **Billisnice said:**
> I am going to reformat the mini with windows xp. Mark s. has done a lot  of good, **but he needs to back up, destroy unity for good** and fix  annoying bugs and work around's. Stop jumping from x to y... I don't get it! :)
Unity is a feature of 11.04, not 10.10.

Anyway, now that you intend to reinstall XP on your dell mini, which is not a bad idea if it serves your purpose, I won't bug you with unsolicited advices. But be informed that if you can manage to make your usb drive work again as a live flash (it is really helpful to have a live disk around), you can always opt to dual-boot. Besides, if you choose to use entire disk for any linux install, then troubleshooting GRUB RESCUE prompt issue (if it occurs at all) is really easy.

---

### Post by Billisnice on 2011-06-26
I know it is 11.04, i have been using ubuntu since 5.04. I am trying to get 10.04 on the mini...Finally get it to boot off USB and after installing on mini i reboot to GRUB RESCUE. I am using the full erase and use the full hard drive install. 

I am so tired of thinking of this. When i went threw the install process after i enter the part about erase and install use the whole hard drive it did ask sometime about window xp with a check box but i did not chose it, like there was a piece of xp i could not get off the SSD with an erase and install...I got so upset me and the wife went to the movies. Is there a simple solution written somewhere? I am using 11.04 machine to create the USB drive.

---

### Post by varunendra on 2011-06-26
Sorry about your troubles. (although the way you told it actually amused me, sorry for that too :))

First off, if you got the USB working (10.04.2 LTS is good IMHO), I'd suggest to mark this thread as [solved], stating how you did it. This will help others having similar problem.

Secondly, for GRUB RESCUE prompt, you should start a new thread (you may wish to put a link to it here). This will help You getting more focussed help. Because those who can offer easy and precise help with that problem may not happen to see this thread due to its title.

I think the [official download site]("http://www.ubuntu.com/download/ubuntu/download") has a good tutorial with screenshots about howto's regarding installation ('show me how' buttons). If you think the previously installed XP related prompts during your setup are unusual, then mention them in your (new) thread.

As for re-creating a working Live USB, here's what I think should go without issues:

[LIST]
[*]As you mentioned, you already have got 10.04 (.2 LTS I guess). Burn it to a CD.
[*]Boot your 11.04 machine with that CD, then use its (10.04's) inbuilt startup disk creator to create live USB. (don't forget to format it to FAT32 beforehand).
[/LIST]
This way, you won't get problems from 11.04 as you were using 10.04 itself while Live USB creation. Of course I assume that your 11.04 machine has a CD writer installed. If not, then use unetbootin as you did before.

---

### Post by Billisnice on 2011-06-26
It is working now, i found that there was an option when installing under erase the whole drive that deleted a bit of xp that was still on the SSD. When i change it to erase the window xp also, it worked...I plugged into land connection and downloaded the drivers for wireless. It is working too

I have been pressing cancel for keying when i open a wireless connection, how to get rid of that option forever? Can i just press ok and leave the keying stuff blank?

---

### Post by varunendra on 2011-06-26
> **Billisnice said:**
> It is working now, i found that there was an option when installing under erase the whole drive that deleted a bit of xp that was still on the SSD. When i change it to erase the window xp also, it worked...I plugged into land connection and downloaded the drivers for wireless. It is working too..thank God! Finally.. :)

> **Billisnice said:**
> I have been pressing cancel for keying when i open a wireless connection, how to get rid of that option forever? Can i just press ok and leave the keying stuff blank?
Again, a different issue.... which I personally have not much idea about except that most often it happens due to WPA security method in use.

Is the mentioned connection unsecured (open), and still this key-box? If so, make sure the security type in Network Manager is set to "None". If it is secured, and you are unable to connect, try fiddling with security type in Network Manager. If I'm misunderstanding this new problem, please explain in detail (in a new thread preferably??). A screenshot may help too.

---

### Post by Billisnice on 2011-06-30
Just a side note. The mini 9 is working good, no issues with netbook ubuntu.

I had a 8gb SD card in the puter. It was formatting and putting the Ubuntu netbook on the SD card and not the SSD drive. I fixed it a few days ago, but today I noticed my SD card had the netbook system on it. I though that was strange. I never though it would recognize the SD card slot as a drive to put utuntu on.

Just my thoughts...

---

