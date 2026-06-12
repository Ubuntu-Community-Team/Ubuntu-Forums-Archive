---
title: "DBus Error org.gtk.Private.RemoteVolumeMonitor.Failed:"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2010-11-16
I've got a problem, my laptop on 10.10 seems to of crashed while I was out and not it won't boot up.

Running Ubuntu via the Live CD and try to open my hard-drive I receive the follow message:

DBus Error org.gtk.Private.RemoteVolumeMonitor.Failed:An operation is already pending

I'm not able to mount the hard-drive.

Anyone able to help me with this problem?

---

### Post by kalos on 2010-11-20
A couple things to try.

[LIST=1]
[*]Open a terminal and run gconf-editor
[*]Browse to 'apps / nautilus / preferences'
[*][LIST]
[*]- uncheck 'media_automount'
[*]- uncheck 'media_automount_open'
[/LIST]
[/LIST]
And try again.

If that doesn't work, you can try these terminal commands. If you're uncertain or have troubles, then post the results of the cat commands.

```

# list mounted drives. if your drive is in here, you need to unmount it with umount (not the missing n)
cat /etc/mtab

# list out your drives. one should be something like /dev/sda1
# if so, then
cat /etc/fstab

# try to mount it
sudo mkdir /mnt/harddrive
sudo mount -t auto /dev/sdyourdrive /mnt/harddrive

```

---

### Post by juzeza on 2011-01-23
I am having a similar problem mounting my hard drive.

My main hard drive is unmounted and I don't know how to remount it.

I ran the code you provided and here are the results:

cat /etc/mtab

/home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0

cat /etc/fstab

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0



 
Any insight as to what to do next? 

Thank you!

---

### Post by Juanchis on 2011-02-11
I'm from Costa Rica, my first language is spanish, please correct my mistakes. I'm a new user too, so...
I have the same problem. Ubuntu was working well, someday i turned on my computer and it doesn't work anymore. My grub shows all the version of the kernel but when i select one doesn't boot a terminal or something like that. When i use a liveCD, i can't mount my file system, when i try, it shows just the same message from the title. Please help me, I really want the information in my hard disc and i don't wanto to use PhotoRec because it's very annoying to select one by one each file, including the ones from google crhome cache...

---

### Post by charliehagies on 2011-02-13
Had the same problem on a brand new Netbook MSI U160dxh with 10.10 (Maverick) installed, did the following to resolve the problem...

[LIST=1]
[*]Tried booting with USB Stick (Maverick) received error as above in title > "DBus Error org.gtk.Private.RemoteVolumeMonitor.Failed:" when trying to repair a partition 
[/LIST]

Searched the forum and followed the following advice 

> A couple things to try.
Open a terminal and run gconf-editor
Browse to 'apps / nautilus / preferences'
- uncheck 'media_automount'
- uncheck 'media_automount_open'
And try again.

If that doesn't work, you can try these terminal commands. If you're uncertain or have troubles, then post the results of the cat commands.

Code:
# list mounted drives. if your drive is in here, you need to unmount it with umount (not the missing n)
cat /etc/mtab

# list out your drives. one should be something like /dev/sda1
# if so, then
cat /etc/fstab

# try to mount it
sudo mkdir /mnt/harddrive
sudo mount -t auto /dev/sdyourdrive /mnt/harddrive


Unfortunately this did not work.



**Solved using the following process:**

[LIST]
[*]Booted 10.04 (Lucid) version on a **DVD** (not USB).
[*]Opened GParted Application (to check the file system....) System -> Administration -> Gparted
[LIST]
[*]Click on the partition that "/" under the mount point
[*]Open Menu Above **Partion -> Check** (this will not work if the partition is mounted or not highlighted)
[*]Click on the TICK to apply the process, (relax on a large drive this takes some time) once the proces is complete close the GParted application.
[/LIST]
[/LIST]

 Shutdown and restarted the system ... it WORKED Perfectly. :D

Seems to be a problem with Maverick and the latest updates that "e2fsck" get an exclusive lock on the file partition to repair it.

Hope this helps

---

### Post by phallusocracy on 2011-12-28
tried the GParted thing. failed. these are the Details from the failure. any insight?



GParted 0.5.1
 Libparted 2.2
    **Check and repair file system (ext4) on /dev/sda1**  00:00:00    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 2048
end: 300556287
size: 300554240 (143.32 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )             ***e2fsck -f -y -v /dev/sda1***             [I]Filesystem mounted or opened exclusively by another program?
[/I]       [I]e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1 
[/I]             ========================================

---

