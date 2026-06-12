---
title: "Wubi Ubuntu won't boot"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by zirch on 2011-08-24
My Wubi install of Ubuntu 11.04 has been working fine until two days ago when I can't boot into it. When I tried to boot into Ubuntu, a screen said:
"init: plymouth main process (264) killed by BUS signal"
followed by more info, but I don't know what it all means. I am not sure if the number in the bracket is correct or what does it mean. After that, the screen just 'froze'.

I tried rebooting in recovery mode as well, but the same message was given. My Windows boots like normal.

I've found this thread: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It seems that there have been some problems with Wubi installs after Grub bootloader updates. But it also states that for the 11.04 release, there should be no more problems. Anyway, I tried the suggested solutions, but it still won't work.

I don't know what is wrong. Please help.

---

### Post by bcbc on 2011-08-24
You could use [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) to backup your data from windows (just point it at \ubuntu\disks\root.disk)

You could try [fsck'ing]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") the root.disk. 

It's a bit of a strange error, since it mounts and boots... so I'm not sure what to suggest other than the fsck. You could run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") although I'm not sure this will tell us much, but maybe it will provide some clues.

---

### Post by zirch on 2011-08-24
Running fsck gives:
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/win/ubuntu/disks/root.disk: recovering journal
/win/ubuntu/disks/root.disk: clean, 358326/650240 files, 2281837/2621440 blocks

Boot Info Script gives the attached file: _[ATTACH]200684[/ATTACH]_

---

### Post by bcbc on 2011-08-24
> **zirch said:**
> Running fsck gives:
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/win/ubuntu/disks/root.disk: recovering journal
/win/ubuntu/disks/root.disk: clean, 358326/650240 files, 2281837/2621440 blocks

Boot Info Script gives the attached file: _[ATTACH]200684[/ATTACH]_

It looks like there was some corruption. The bootinfoscript looks okay (except for the /win umount error, and your grub edits which won't hurt). Does it boot now, or still the same prob?

---

### Post by zirch on 2011-08-24
Still the same problem. I'm booting now from a USB.
Any idea what else could have gone wrong? Or how do I restore it? Do I need to reinstall wubi?

By the way, is there supposed to be anything in /ubuntu/disks/boot/grub folder?

---

### Post by bcbc on 2011-08-24
> **zirch said:**
> Still the same problem. I'm booting now from a USB.
Any idea what else could have gone wrong? Or how do I restore it? Do I need to reinstall wubi?

By the way, is there supposed to be anything in /ubuntu/disks/boot/grub folder?

Not really sure what could have gone wrong. When you run it in recovery mode, does it also freeze? What's the last message it shows?

There's nothing in /ubuntu/disks/boot/ or /ubuntu/disks/boot/grub anymore. It's a relic from grub-legacy days.

You could chroot into the install and try updating packages. I don't know if it would make a difference - unless there was some packaging error. Depending on how much time you've invested in tweaking it, it's probably easier to backup and reinstall. (Reinstalling will deleted the current install so you have to make sure you get everything you need off it).

One other thing you can try is to check how much free space is on the root.disk. That could be a reason for it not booting:
```
sudo mkdir -p /media/win
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
df -h
```
Check how much space is available on /dev/loop1 or probably /dev/loop2

PS after you're done:
```
sudo umount /mnt
sudo umount /media/win
```

---

### Post by zirch on 2011-08-24
When I tried to boot in recovery mode, the same thing occurred. It gave:
init: plymouth main process ( 308 ) killed by BUS signal
[ 26.580204] Kernel panic - not syncing: Attempted to kill init!
[ 26.580280] Pid: 1, comm: init Not tainted 2.6.38-11-generic #48-Ubuntu
mountall: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

And it just stopped there. Running boot in the grub prompt gives:
error: no loaded kernel

Also, when trying to boot into Ubuntu, there was this
Try(hd0,0) FAT32: No WUBILDR
Try(hd0,1) NTFS5: error "prefix" is not set

I got the above message when booting, even before, when I could still boot into Ubuntu. It just flashed very quickly, and as there did not seem to be any problem, I ignored it. Could this mean something?

I checked the hard disk space and there is still 815Mb left.

---

### Post by bcbc on 2011-08-24
Do you have any older kernels you can boot? you're getting a kernel panic for whatever reason.

Is that 815MB free on the root.disk? That should be okay.

Those other messages: Try (hd0,0)... and the "prefix" not set are harmless and don't indicate any issue.

I'm going to go offline now. I'm not sure what else to suggest. If you have an older kernel try that.

The only other thing I would suggest is to run chkdsk from windows just in case there is some ntfs corruption. But honestly it seems like that's not very likely.

---

### Post by zirch on 2011-08-24
> **bcbc said:**
> Do you have any older kernels you can boot? you're getting a kernel panic for whatever reason.

Is that 815MB free on the root.disk? That should be okay.

Those other messages: Try (hd0,0)... and the "prefix" not set are harmless and don't indicate any issue.

I'm going to go offline now. I'm not sure what else to suggest. If you have an older kernel try that.

The only other thing I would suggest is to run chkdsk from windows just in case there is some ntfs corruption. But honestly it seems like that's not very likely.

Okay. Thanks for the help so far. I'll continue to try.

---

### Post by zirch on 2011-08-24
I tried booting from Ubuntu, Linux 2.6.38-10-generic and 2.6.38-8-generic, but still the same problem.

---

### Post by zirch on 2011-08-24
How do I chroot into the Wubi installation of Ubuntu?

I tried these but it wouldn't work:

```
sudo mkdir /mnt/windows /mnt/temp
sudo mount /dev/sda2 /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/temp

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

---

### Post by bcbc on 2011-08-24
Did you replace the wubildr and do you have a backup of the old one? 

I think if every kernel is causing panic there must be some fundamental problem. Do you recall whether you were getting kernel panic before trying to repair?

---

### Post by zirch on 2011-08-25
> **bcbc said:**
> The only other thing I would suggest is to run chkdsk from windows just in case there is some ntfs corruption.

Yes, I replaced the wubildr and I have a backup of the old one. And yes, there was kernel panic even before I tried repairing.

Looks like you were right. I just didn't know what else to do, I thought of backing up and reinstalling. But I couldn't access my files through ext2read. It gave an error message saying the root.disk was corrupted. I then ran a chkdsk scan in Windows and sure enough, there was corruption. 

However, I could still mount root.disk from within Ubuntu Live USB and I managed to copy almost all the files (I just 'select all' and 'copy paste'; there was an error message saying I couldn't copy certain files).

After a chkdsk scan and fix process, I rebooted into Windows and the root.disk file was 'empty'. Its size was 0kb. Looks like everything in it was deleted. And I don't think it can be recovered. I do have a previous backup of root.disk though.

So, I thought of replacing the root.disk with the backup. I did, and I can now boot into Ubuntu again. But are there any problems associated with this method? How can I check? Or should I do something else?

Also, how do I use the files that I copied earlier from the corrupted root.disk (when I booted from the USB)? Can I just paste and replace into the root directory, so that I can have the same setup before the corruption thing happened?

---

### Post by bcbc on 2011-08-25
> **zirch said:**
> Yes, I replaced the wubildr and I have a backup of the old one. And yes, there was kernel panic even before I tried repairing.

Looks like you were right. I just don't know what else to do, I thought of backing up and reinstalling. But I can't access my files through ext2read. It gave an error message saying the root.disk was corrupted. I then ran chkdsk in Windows and sure enough, there was corruption. After the scan and fix process, I rebooted into Windows and the root.disk file is 'empty'. It's size is 0kb. Looks like everything in it was deleted. And I don't think it can be recovered. I do have a previous backup of root.disk though.

So, I thought of replacing the root.disk with the backup. I did, and I can now boot into Ubuntu again. But is there any problem associated with this method? How can I check? Or should I do something else?

It's great that you have a backup of the root.disk. There's no problem copying it back into the \ubuntu\disks directory and running it as you have done.

Regarding the corrupted root.disk, if chkdsk left you with an empty file, I think there's no hope of recovery. That's really the down side of Wubi - all your eggs are in one basket with the virtual disk. If there's a problem you can lose it all. It's not clear to me why some people suffer root.disk corruption - I understand that many do hard shutdown's if the system hangs (I believe that this is the main cause) but in some cases there has been corruption and the users haven't seen any hanging or done any forced shutdowns. 

So I generally recommend people who use wubi keep regular backups and consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") or installing direct once they decide that they want to keep using Ubuntu on a permanent basis.

---

### Post by zirch on 2011-08-25
I don't know either why there was corruption. I did a check a few months ago and it was fine.

Anyway, thanks **bcbc**. I'm experimenting with wubi and ubuntu right now. I may make a direct installation in the future. Perhaps when Ubuntu 11.10 final is released.

---

