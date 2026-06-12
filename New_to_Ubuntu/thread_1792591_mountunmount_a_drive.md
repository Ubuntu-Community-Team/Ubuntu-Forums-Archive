---
title: "mount/unmount a drive??"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by camotte on 2011-06-28
yesterday was my first day with ubuntu, and so far has been great, but when i was trying to mount a drive that could let me access my windows .jpg and .mp3 files i think i messed up my fstab, the drive keeps mounting on start up and i still cant see any of my files, any help would be greatfull

i know there are many theards sorting this type of problems out but i couldnt make it work on mine

pd sorry for my english and my nooby questions!

---

### Post by Morbius1 on 2011-06-28
Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by camotte on 2011-06-28
/dev/loop0: UUID="7c4b9487-5965-473d-b7c5-e81d7a0dfa9c" TYPE="ext4" 
/dev/sda1: LABEL="Recovery" UUID="F83C1AC43C1A7E36" TYPE="ntfs" 
/dev/sda2: UUID="3E7EF20D7EF1BDA9" TYPE="ntfs" 


proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda1 /media/Recovery ntfs defaults,nls=utf8,umask=0222 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda1 on /media/Recovery type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/harry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harry)

---

### Post by jerome1232 on 2011-06-28
Since you are using Wubi, your windows Disk should be located at /host I believe.

Just open your file browser, Click "File System" in the left hand pane, look for a host folder and look around in there. It should be your primary Windows partition.

---

### Post by Morbius1 on 2011-06-28
You are using Wubi ( Installed within Windows ). Your Windows partition is mounted here:
>  /dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,all  ow_other,blksize=4096)

So go to a terminal ant type:
```
nautilus /host
```
Do you see your Windows partition now?

---

### Post by camotte on 2011-06-28
thank you! i can see my files now, but i guess i had nothing to do with? i just had to type **nautilus /host** all along?

and why keeps poping up the recovery drive when theres no information in there? 

and is there any way to create a shortcut to my drive or i have to go trough terminal everytime

---

### Post by Paqman on 2011-06-28
> **camotte said:**
> 
and is there any way to create a shortcut to my drive or i have to go trough terminal everytime

You don't have to use the terminal at all. This command:
```
nautilus /host
```

...just launches the file browser (Nautilus) and tells it to open in the folder /host. When you're in that folder just hit Ctrl-D and it will create a bookmark for /host, so that you can go straight to it from the Places menu or the list on the left hand side of the file browser.

---

### Post by camotte on 2011-06-28
thank you! really appreciated!

---

### Post by jerome1232 on 2011-06-28
As for the recovery partitions, that's probably a factory restore feature put in buy your manafacturer and your just accidentally added it to fstab when you were messing around with fstab tools.


Just open a terminal, run the follow command which will open a text editor with fstab in it, then put a "#" symbol in front of the line with the word recovery in it, save then close it, next reboot it won't pop up.


Be sure to put the "#" symbol in front of the correct line, you put it on the wrong one and your system will probably not boot the next time you start up, just a word of caution.


```
gksu gedit /etc/fstab
```

What you see should look like this (I highlighted the line in question in red)

```
proc /proc proc nodev,noexec,nosuid 0 0
[COLOR="Red"]/dev/sda1 /media/Recovery ntfs defaults,nls=utf8,umask=0222 0 0[/COLOR]
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
```

you want it to look like this

```
proc /proc proc nodev,noexec,nosuid 0 0
[COLOR="Red"]#/dev/sda1 /media/Recovery ntfs defaults,nls=utf8,umask=0222 0 0[/COLOR]
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
```

---

