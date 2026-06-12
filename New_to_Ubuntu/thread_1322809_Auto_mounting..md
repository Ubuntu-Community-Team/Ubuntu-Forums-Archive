---
title: "Auto mounting."
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Duckywan on 2009-11-11
Running 9.10, want to mount my two new 1.5tb drives. Was using [this]("https://help.ubuntu.com/community/InstallingANewHardDrive") guide, but I'm a little lost. 

I get this error when I try and load them after editing fstab.
> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sdb1What I have in fstab:
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/sdb1   ext3    defaults     0        2
/dev/sdc1    /media/sdc1   ext3    defaults     0        2

Not sure what I've done wrong (however I've probably screwed up somewhere), but I need help :p

---

### Post by Claus7 on 2009-11-11
Hello and welcome as I can see that this is your very first post to the forums!

So regarding your problem. Could I ask why did you use the guide as from what I know disks can be mounted automatically in karmic?

Since you cannot mount them automatically and you are sure about it then I would suggest you to do this:

plug your external drives to your pc and then in order to mount them do it as root. That means that in front of the command mount, you should type the word sudo. Then when you press enter you will be asked to use your root password.

An example of a device plugged in /dev/sdb1 would be:

```
sudo mount /dev/sdb1 /media/sdb1
```

In case this cause you any problems then I would try to do this: 

```
cd /media
sudo mkdir test
sudo mount /dev/sdb1 /media/test
```

Regards!

---

### Post by Duckywan on 2009-11-11
They're internal drives, They were just formated and when I clicked on them it asked for authentication. 

I can mount them without those lines in fstab.

But thank you for the welcome :)

---

### Post by Claus7 on 2009-11-11
Hello,

it's my pleasure! Glad that you solved your problem by removing those lines from fstab. You can mark this thread as solved then.

Regards and happy ubuntu-ing!

---

### Post by sisco311 on 2009-11-11
Linux now prefers to use UUID (Universally Unique Identifier), LABEL, or symlinks to identify media storage devices on a system. Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots.
[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

Try this guide: 
[http://psychocats.net/ubuntu/mountlinux]("http://psychocats.net/ubuntu/mountlinux")

---

