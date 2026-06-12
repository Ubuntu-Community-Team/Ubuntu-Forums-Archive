---
title: "Boot problem in Ubuntu 10.10!?"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by StevaBg on 2010-11-21
Greetings to all!!!
Im absolute beginner and need help!
Im using Ubuntu 10.10 for a few months, i'v intslall it from canonical live cd and everything was ok till yesterday. Now im using Ubuntu live cd and "Try Ubuntu"  When im starting my pc and starting to boot show me many text lines but on the end show me this:

...Begin: Running /scripts/local-bottom   done.
   Begin: Running /scripts/init-bottom   mount: mounting /dev on/root/dev failed: No such file or directory
   Done.
   Mount: mounting /sys on/root/sys failed: No such file or directory
   Mount: mounting/ proc on/root/proc failed: No such file or directory
   Target filesystem doesn't have rquested /sbin/init.
   No init found. Try passing init= bootarg.

   BusyBox V1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) Built-in shell (ash)
   Enter 'hel' for a list of built-in commands.

   (initramfs)_When i try to start recovery mode its the same problem...
Please help me, thanks!!!

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> Greetings to all!!!
Im absolute beginner and need help!
Im using Ubuntu 10.10 for a few months, i'v intslall it from canonical live cd and everything was ok till yesterday. Now im using Ubuntu live cd and "Try Ubuntu"  When im starting my pc and starting to boot show me many text lines but on the end show me this:

...Begin: Running /scripts/local-bottom   done.
   Begin: Running /scripts/init-bottom   mount: mounting /dev on/root/dev failed: No such file or directory
   Done.
   Mount: mounting /sys on/root/sys failed: No such file or directory
   Mount: mounting/ proc on/root/proc failed: No such file or directory
   Target filesystem doesn't have rquested /sbin/init.
   No init found. Try passing init= bootarg.

   BusyBox V1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) Built-in shell (ash)
   Enter 'hel' for a list of built-in commands.

   (initramfs)_When i try to start recovery mode its the same problem...
Please help me, thanks!!!

Are you saying the Ubuntu CD no longer works to allow you to preview (try) Ubuntu?

I understand you're having problems with your installation.  Normally this can be repaired by using the Live CD to repair the problem.  The work will be compounded if your CD boot option is also broken.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> Are you saying the Ubuntu CD no longer works to allow you to preview (try) Ubuntu?

I understand you're having problems with your installation.  Normally this can be repaired by using the Live CD to repair the problem.  The work will be compounded if your CD boot option is also broken.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

No, i have installed Ubuntu but i cant boot it, nad now i use live cd and try ubuntu but i dont know how to repair and solve that problem....Sorry my english is not enough good but i hope You will understand me...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> No, i have installed Ubuntu but i cant boot it, nad now i use live cd and try ubuntu but i dont know how to repair and solve that problem....Sorry my english is not enough good but i hope You will understand me...

Boot to your Ubuntu lLive CD.  Mount your hard drive with the Ubuntu installation using the Places Menu.

Open a terminal window and type:

```
mount
```

Pick out the UUID and the specific drive (sda, sdb, etc) of your hard drive installation.  Now using that UUID reinstall Grub to that drive with:

```
sudo grub-install &#8211;root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdX
```

Make the &#8220;X&#8221; in the sdX the letter you see with your mount command (don't include a number for this parameter).


I got this information from a variation of using steps from this link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Quackers on 2010-11-21
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by StevaBg on 2010-11-21
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

For now its very slow, it say in terminal:

```

```ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information...```

```

---

### Post by StevaBg on 2010-11-21
For now its very slow, it say in terminal:

```

```ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information...```

```

---

### Post by Quackers on 2010-11-21
Hmm, something's definitely wrong :-( The boot script should take on a few seconds to run.

---

### Post by StevaBg on 2010-11-21
> **Quackers said:**
> Hmm, something's definitely wrong :-( The boot script should take on a few seconds to run.

Unfortunatly, its still searching :(

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> Unfortunatly, its still searching :(

What results do you get from the suggestion I gave you?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> Boot to your Ubuntu lLive CD.  Mount your hard drive with the Ubuntu installation using the Places Menu.

Open a terminal window and type:

```
mount
```Pick out the UUID and the specific drive (sda, sdb, etc) of your hard drive installation.  Now using that UUID reinstall Grub to that drive with:

```
sudo grub-install –root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdX
```Make the “X” in the sdX the letter you see with your mount command (don't include a number for this parameter).


I got this information from a variation of using steps from this link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")


When i do "mount"...

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda6 on /media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 type ext4 (rw,nosuid,nodev,uhelper=udisks)




```

and...

```
ubuntu@ubuntu:~$ sudo grub-install –root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdX
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

```

Probably i dont understand well, im totaly beginner....

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> When i do "mount"...

```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda6 on /media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 type ext4 (rw,nosuid,nodev,uhelper=udisks)




```

and...

```
ubuntu@ubuntu:~$ sudo grub-install –root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdX
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

```

Probably i dont understand well, im totaly beginner....

Looking at the output of your mount command it appears your Ubuntu is installed on /dev/sda6.  I mentioned that you need to change the “X” to the drive letter of your drive.  The drive letter of your drive is “a”.

Follow the steps again, but this time replace “a” for “X”.

Again, looking at the output from your update, your command will be:

```
sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```

Be sure to mount the drive by clicking on it in the Places menu before issuing the command.

Keep in mind the information for the command is taken from your "mount" command output.

If you have a problem and will do a followup based on what you actually did I can probably figure out what you’re doing wrong.  While it might take a few steps to identify what you’re doing wrong, the matter is very simple.  Again, if you’ll followup, we can easily get you up and running.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> Looking at the output of your mount command it appears your Ubuntu is installed on /dev/sda6.  I mentioned that you need to change the “X” to the drive letter of your drive.  The drive letter of your drive is “a”.

Follow the steps again, but this time replace “a” for “X”.

Again, looking at the output from your update, your command will be:

```
sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```Be sure to mount the drive by clicking on it in the Places menu before issuing the command.

Keep in mind the information for the command is taken from your "mount" command output.

If you have a problem and will do a followup based on what you actually did I can probably figure out what you’re doing wrong.  While it might take a few steps to identify what you’re doing wrong, the matter is very simple.  Again, if you’ll followup, we can easily get you up and running.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

When i try to mount from places it show me error window:

```
Unable to mount 30 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> When i try to mount from places it show me error window:

```
Unable to mount 30 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

I’m surprised that you’re having problems now and it mounted correctly the first time.  Did you try your new mount from freshly running the “Try Ubuntu” feature?  There’s a chance some of your other experiments might be interfering with the mount utility.

It’s be hard for anything else to succeed if you can’t get past this step.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> I’m surprised that you’re having problems now and it mounted correctly the first time.  Did you try your new mount from freshly running the “Try Ubuntu” feature?  There’s a chance some of your other experiments might be interfering with the mount utility.

It’s be hard for anything else to succeed if you can’t get past this step.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

I know..There is maybe some other and bigger problem and i like beginner cant fix it...
How can i reinstall or to do new install...!?

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> I know..There is maybe some other and bigger problem and i like beginner cant fix it...
How can i reinstall or to do new install...!?

A new install is simple.  Just click on "Install" rather than clicking on "Try" from the Ubuntu Live CD.

I would be glad to know the results of clicking on mounting your old installation drive from freshly booting into the "Try" option.  From your first followup I believe it would have worked had you performed the command given at the time.

It might not be so bad to spend a few messages fixing the glitch you have developed rather than starting over so quickly.  It might help you to see you have a robust OS.  For me, I'd hate to think I was using something that was so fragile and easily to become usable.

But again, starting over as well as performing a first install is very simple.  It's just a matter of clicking on the "Install" option and following the prompts.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> A new install is simple.  Just click on "Install" rather than clicking on "Try" from the Ubuntu Live CD.

I would be glad to know the results of clicking on mounting your old installation drive from freshly booting into the "Try" option.  From your first followup I believe it would have worked had you performed the command given at the time.

It might not be so bad to spend a few messages fixing the glitch you have developed rather than starting over so quickly.  It might help you to see you have a robust OS.  For me, I'd hate to think I was using something that was so fragile and easily to become usable.

But again, starting over as well as performing a first install is very simple.  It's just a matter of clicking on the "Install" option and following the prompts.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Everything i do what you and other said i was doing from liveCd and try ubuntu...And when i try to install and check to download packages and from third part on second window after i click on install it freez and loading and loading and loading without any progress for a long long time and i must shut down pc...Something is very wrong here...I dont know what to do...

---

### Post by StevaBg on 2010-11-21
> **StevaBg said:**
> Everything i do what you and other said i was doing from liveCd and try ubuntu...And when i try to install and check to download packages and from third part on second window after i click on install it freez and loading and loading and loading without any progress for a long long time and i must shut down pc...Something is very wrong here...I dont know what to do...


Can be problem with HD !?

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> Everything i do what you and other said i was doing from liveCd and try ubuntu...And when i try to install and check to download packages and from third part on second window after i click on install it freez and loading and loading and loading without any progress for a long long time and i must shut down pc...Something is very wrong here...I dont know what to do...

It's a difference from performing commands when you first boot the disk and after performing experiments and test that you don't understand.

I asked if you're able to boot to the Live CD and immediately click on your installation drive from the Places menu.  Someone else might have questions about the other steps they are giving you.  Please keep in mind that my suggestion is very specific.  But to the Live CD, then click on your hard drive and let us know if that works.

I worked the first time because you gave the expected output.  If it works this time open up a terminal window and run:

```
sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```

Shutdown the system and see what happens when you try to boot without the CD.  Give us the details and final results.

Keep in mind I'm speaking of a fresh boot with going to Places as your first step.

Also, I'm not disregarding or taking lightly the suggestions from the other users.  You might want to perform their suggestions from a fresh boot also and reply on their messages giving them the feedback they are looking for.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by oldfred on 2010-11-21
I am surprised the boot script did not run as it is really running from the liveCD and just posts error messages if it cannot mount or parse a folder.

You might try filecheck of your linux partitions. Do you also have windows, if so window chkdsk.

From liveCD so everything is unmounted
```
sudo e2fsck -C0 -p -f -v /dev/sda6
```
if errors:
```
sudo e2fsck -f -y -v /dev/sda6
```

if this shows other linux partitions run e2fsck on them also.
```
sudo fdisk -lu
```

If nothing is working, is hard drive older? Has it been giving any warning messages?

---

### Post by StevaBg on 2010-11-21
> **oldfred said:**
> I am surprised the boot script did not run as it is really running from the liveCD and just posts error messages if it cannot mount or parse a folder.

You might try filecheck of your linux partitions. Do you also have windows, if so window chkdsk.

From liveCD so everything is unmounted
```
sudo e2fsck -C0 -p -f -v /dev/sda6
```if errors:
```
sudo e2fsck -f -y -v /dev/sda6
```if this shows other linux partitions run e2fsck on them also.
```
sudo fdisk -lu
```If nothing is working, is hard drive older? Has it been giving any warning messages?

I have only Ubuntu not windows

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
/dev/sda6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? 

```

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> It's a difference from performing commands when you first boot the disk and after performing experiments and test that you don't understand.

I asked if you're able to boot to the Live CD and immediately click on your installation drive from the Places menu.  Someone else might have questions about the other steps they are giving you.  Please keep in mind that my suggestion is very specific.  But to the Live CD, then click on your hard drive and let us know if that works.

I worked the first time because you gave the expected output.  If it works this time open up a terminal window and run:

```
sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```Shutdown the system and see what happens when you try to boot without the CD.  Give us the details and final results.

Keep in mind I'm speaking of a fresh boot with going to Places as your first step.

Also, I'm not disregarding or taking lightly the suggestions from the other users.  You might want to perform their suggestions from a fresh boot also and reply on their messages giving them the feedback they are looking for.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

With Cd and without CD, on hard drive its the same, have no results...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> With Cd and without CD, on hard drive its the same, have no results...

StevaBg.  Please notice that I keep emphasizing from a fresh boot at the “Try” command before you do anything.  I’m asking you to test it and give the results.  I don’t know what you mean by on the CD or with the CD.  You’ve said you can boot to the CD.  Looking at your previous message it appears that you have booted to the CD.  However, I can’t tell from your message that you are performing the steps I’m giving you when you first boot.

You said:

> **StevaBg said:**
> I have only Ubuntu not windows

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
/dev/sda6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? 

```

That shows that you actually booted and performed something to mount the hard drive.  The system is saying it is mounted.  From most of what you type if you perform the steps I’m giving you, I believe you’d have success.

Step #1:  Reboot to the system from the “Try” command.
Step #2:  Click on the Hard Drive you have from the Places menu.
Step #3:  Open a terminal window and run the command:

```
 sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```

Step #4: Shutdown the system, then restart without the CD.

Will you let me know what happens at each one of those steps?  Again, let these be the only things you do from first booting to the Live CD.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> StevaBg.  Please notice that I keep emphasizing from a fresh boot at the “Try” command before you do anything.  I’m asking you to test it and give the results.  I don’t know what you mean by on the CD or with the CD.  You’ve said you can boot to the CD.  Looking at your previous message it appears that you have booted to the CD.  However, I can’t tell from your message that you are performing the steps I’m giving you when you first boot.

You said:



That shows that you actually booted and performed something to mount the hard drive.  The system is saying it is mounted.  From most of what you type if you perform the steps I’m giving you, I believe you’d have success.

Step #1:  Reboot to the system from the “Try” command.
Step #2:  Click on the Hard Drive you have from the Places menu.
Step #3:  Open a terminal window and run the command:

```
 sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```Step #4: Shutdown the system, then restart without the CD.

Will you let me know what happens at each one of those steps?  Again, let these be the only things you do from first booting to the Live CD.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Have another problem, cant restart or niether shut down, when i try it, just loading and loading and i must shut down with button...I do everything like you say but its the sam problam and that new one...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> Have another problem, cant restart or niether shut down, when i try it, just loading and loading and i must shut down with button...I do everything like you say but its the sam problam and that new one...

Are you saying you can't boot to the Ubuntu Live CD?  If you can't boot to the Live CD, you either have a serious problem with your computer, or your Live CD is corrupted.

What computer are you using to type on the message base?  Are you able to boot up your Live CD on that computer?  You have to first make sure you have a working Live CD.

Of course, you had one at one time because you showed output from having booted to the CD.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-21
Edit: reply posted in the wrong thread.

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> Are you saying you can't boot to the Ubuntu Live CD?  If you can't boot to the Live CD, you either have a serious problem with your computer, or your Live CD is corrupted.

What computer are you using to type on the message base?  Are you able to boot up your Live CD on that computer?  You have to first make sure you have a working Live CD.

Of course, you had one at one time because you showed output from having booted to the CD.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

When i put LiveCd i can only "Try Ubuntu" i cant install it, and now i can shutdown or restart system only with button...Cd is canonical i get Cd from [www.ubuntu.com](www.ubuntu.com) Ship IT, its original Cd...
Im afraid that maybe problem is with my HD...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> When i put LiveCd i can only "Try Ubuntu" i cant install it, and now i can shutdown or restart system only with button...Cd is canonical i get Cd from [www.ubuntu.com](www.ubuntu.com) Ship IT, its original Cd...
Im afraid that maybe problem is with my HD...

If you clicked on "Install" and continued with the various option, it's a good chance you've destroyed your previous installation.  I don't know if you've done that or not.

I have asked you many time to boot to the Live CD and click on "Try" then perform the steps I gave you.  Again, you shouldn't click on "Install" in an effort to fix an already installation.

I can't tell from your messages what your'e doing, since you don't reply specifically to the steps that are asked.

If you would boot to the Live CD and click on "Try" and not "Install", then perform the steps I gave you we may be able to tell if you've destroyed your previous installation.

You'll have to perform the steps one by one and let us know the results of each step.  Also, it's help if you would do that when you first boot up to the "Try Ubuntu" option.

Edit: By the way, if you're trying to perform an Install rather than a Repair or Recover, then that would involve a different series of steps.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> If you clicked on "Install" and continued with the various option, it's a good chance you've destroyed your previous installation.  I don't know if you've done that or not.

I have asked you many time to boot to the Live CD and click on "Try" then perform the steps I gave you.  Again, you shouldn't click on "Install" in an effort to fix an already installation.

I can't tell from your messages what your'e doing, since you don't reply specifically to the steps that are asked.

If you would boot to the Live CD and click on "Try" and not "Install", then perform the steps I gave you we may be able to tell if you've destroyed your previous installation.

You'll have to perform the steps one by one and let us know the results of each step.  Also, it's help if you would do that when you first boot up to the "Try Ubuntu" option.

Edit: By the way, if you're trying to perform an Install rather than a Repair or Recover, then that would involve a different series of steps.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

No! I'v try that and didnt work, i think that i tell you that, i'v try all steps you said, and there is the same problem!!! I just want to fix it, i didnt try to install but i jast said that is not possibble to install...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> No! I'v try that and didnt work, i think that i tell you that, i'v try all steps you said, and there is the same problem!!! I just want to fix it, i didnt try to install but i jast said that is not possibble to install...

When you say you tried that, please tell me what it is you're saying you did, if you don't mind.

If I can see where it's failing, I could probably help.  Most of your message appear to suggest that it fails when you click on "Try Ubuntu".

On one of your messages you gave me a command line you typed in a terminal window.  The command you typed in was incorrect and gave the appropriate response.

My suggestion was for you to perform each step one at a time and let us know the results.  You're saying you're doing this, but you're not.

You said you couldn't mount the drive, but you gave an output of a command line that showed the drive was mounted.  The "Try Ubuntu" feature won't mount something unless you invoke it, either from a terminal command line or from the Places menu.

You're saying in words that you are having problems with the English.  So, there's a good chance you might not be understanding what we are asking you to do.  Then without telling us exactly what you're doing, and how you're doing it, you're telling us you're doing it and it's not working.

A most important key if for you to perform each of the steps I gave you and give me the results of each step.  If you will do that we can see where things are going wrong and pick it up from there.  If you just say it's not working, we can't tell what you've done.  We can't tell what's not working.

I don't mean to impose.  I'm glad to help.  But I would need to know the results of each step, starting with clicking on "Try Ubuntu".

If you're having as much trouble understanding what I'm saying as I'm having understanding what you're saying, I can see the problem.  On just about every other one of your messages it appears that you say that you can't boot the Live CD into the "Try Ubuntu" feature.  Now in this message you mention that you were talking about something else.

I believe the resolution is simple, but I can't tell from your messages what you're actually doing on your computer.

The method I mention to you isn't the only method.  But I'm sure it would work if your system isn't corrupted.

Edit:  By the way, I'm curious how you would know that it's not possible to Install Ubuntu on your computer if you hadn't tried.  I don't believe it's not possible to install Ubuntu on your computer.  If that was the case, any thing we discussed would be moot.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
> **apollothethird said:**
> StevaBg.  Please notice that I keep emphasizing from a fresh boot at the “Try” command before you do anything.  I’m asking you to test it and give the results.  I don’t know what you mean by on the CD or with the CD.  You’ve said you can boot to the CD.  Looking at your previous message it appears that you have booted to the CD.  However, I can’t tell from your message that you are performing the steps I’m giving you when you first boot.

You said:



That shows that you actually booted and performed something to mount the hard drive.  The system is saying it is mounted.  From most of what you type if you perform the steps I’m giving you, I believe you’d have success.

Step #1:  Reboot to the system from the “Try” command.
Step #2:  Click on the Hard Drive you have from the Places menu.
Step #3:  Open a terminal window and run the command:

```
 sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
```Step 
#4: Shutdown the system, then restart without the CD.

Will you let me know what happens at each one of those steps?  Again, let these be the only things you do from first booting to the Live CD.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Sorry for misunderstanding!!!

Step #1: I cant always reboot system from "Try" then i must shut down Pc with the button then again try to reboot.
Step #2: When i click on hard drive (mount) from Places open me window "5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 " and in that window are two folders 1.-lost and found 2.-Stevica (my name-home folder).
Step #3: When i run that command in terminal show me this:
```
ubuntu@ubuntu:~$ sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

```
Step #4: I cant shut dow system i can only shut down wtih the button.

When i restart without Cd show me again same problem like i wrote on the beginig the thread, there is no results...

---

### Post by apollothethird on 2010-11-21
> **StevaBg said:**
> Sorry for misunderstanding!!!

Step #1: I cant always reboot system from "Try" then i must shut down Pc with the button then again try to reboot.
Step #2: When i click on hard drive (mount) from Places open me window "5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 " and in that window are two folders 1.-lost and found 2.-Stevica (my name-home folder).
Step #3: When i run that command in terminal show me this:
```
ubuntu@ubuntu:~$ sudo grub-install –root-directory=/media/5303ca47-5978-4cdd-bb94-eb5b9f5e9ab8 /dev/sda
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.

```
Step #4: I cant shut dow system i can only shut down wtih the button.

When i restart without Cd show me again same problem like i wrote on the beginig the thread, there is no results...

Actually the information you've presented shows good results.  It might not be exactly what you're looking for, but it sheds a lot of important light on the situation.

It appears that the partition is corrupted as to the reason you can’t boot to it.  I don’t know what you do between clicking on “Try” and clicking on the option to restart the system that sometimes causes the restart to fail.  But that’s another story.

I don’t know how much you have stored on in your home directory that you consider important.  If you have something you want to preserve I would suggest that you place a pen drive into usb slot and copy the directory.  If you don’t have anything in that folder that you want to keep, the next step is for you to use the Install option because there doesn’t appear to be anything salvageable in that partition.  You can choose that partition for your install.

If you have extremely important data that you want to spend a lot of time recovering, you might be able to recover the data from the partition, but it’ll take a lot of work and patience.  It might have to be done by a professional.

There are utilities on the Live CD that can be used to try to repair the drive found in the Disk Utility under the System -> Administration.  You could also download other utilities while booted into the Live CD.  But from the tone of your other messages it appears that the Install is relatively new and you might not have anything extremely critical on the partition.

If the latter is the case, you might proceed to Install, again, selecting that partition that you’ve just described as being virtually empty as your “/” install location.  Allow the system to format it to ext3 or ext4.  I believe ext4 would be your best choice.

By the way, none of the suggestions from this thread would have wiped your partition clean the way it happens to be.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-21
By the way, your &#8220;/dev/sda6&#8221; is on the sixth&#8217;s partition of your hard drive.  You have other partitions.  There&#8217;s a chance that your Ubuntu install is on one of the other partitions.  Your installation might still be intact.

Will you give us the output of this command:

```
fdisk -l
```

Will you click on some of the other Drives you see available in Places and tell us what you get from those?  There&#8217;s a good chance that you installed your &#8220;/home&#8221; drive on a separate partition.  This is the reason for having only one valid directory on that drive.

How many items are in your Places menu that says &#8220;Filesystem&#8221;?

If we find the right Filesystem I can try to walk you through the step of setting it up for your boot drive.

Again, I&#8217;m getting the information from: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Edit:  Does one of those Filesystem drives show a directory with folders by the names of: bin, boot, cdrom, dev, etc, root, sbin, etc...?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by StevaBg on 2010-11-21
I'v fixed up with Disk Utility, now everything is like before and ok, after 2 days, finaly...It was realy hard for beginner like me...:)
I want to thank everyone who was involved in fixing my problem especialy to James, and sorry for misunderstanding, its my fault!!!
Thanks, and till next problem ;) !

---

