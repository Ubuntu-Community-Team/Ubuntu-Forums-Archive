---
title: "External HDD Problem -  Continually Ejected"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by csad on 2010-09-15
Hi guys ):P Newbie here, both for the forum and for Ubuntu. Hope I'm posting to the right section. Please tell me if not.

I've only been using ubuntu lucid lynx now for barely over a month and am only slowly getting the hang of it. Unfortunately, I've encountered a weird but stubborn problem. 

Thing is, I have two external HDDs I want to use and which, after a bit of struggle, I figured out how to mount permanently with fstab.

One of those HDDs I use only seldom, so I just keep the parts of fstab pertaining to it as comment until I need it. That's why I don't know if the problem described below would apply to that HDD as well or not. (I can't try it out right now, and it doesn't matter right now anyway.)

For some reason, the system keeps more or less ejecting my HDD (clicking the folder of the hdd makes it look like it's blank), while the sidebar of nautilus keeps telling me that it's still mounted. At the same time, trying to *unmount* it gives out this error:
```

Unable to unmount data
umount: /media/data mount disagrees with the fstab

```Oh, and did I mention that, according to GParted and Disk Utility the drive is unmounted anyway (since it doesn't show on them), yet unplugging and re-plugging the device gives this error:

```

Unable to mount data
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /media/data
mount failed

```Another detail: If I do that (un-/re-plugging), it *does* show up on GParted and Disk Utility and I *can* use their "safe removal" option. But the unmount option of the nautilus sidebar? Not a chance.


For further explanation, this is what my fstab looks like:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=09697db7-5ef2-4ec4-a685-fbc71d399190 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ee6f0b21-fd46-46a4-98c9-347bc1b20df9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f1ebbbc4-0d9d-4a18-89b1-e60921809f27 none            swap    sw              0       0


#/dev/disk/by-uuid/01C9268811A1E480          /media/other   ntfs  rw,auto,users,nls=utf8,umask=007,gid=46  0  0
#/dev/disk/by-uuid/3048049F48046646          /media/Daten  ntfs  rw,auto,users,nls=utf8,umask=007,gid=46  0  0
#/dev/disk/by-uuid/34FC1E99FC1E5608          /media/music  ntfs  rw,auto,users,nls=utf8,umask=007,gid=46  0  0



/dev/disk/by-uuid/03782fff-7052-4d5f-b351-23502df57659          /media/data   ext4   defaults   0   2


```I should mention that, while I was setting up these two HDDs, weirdly, I really had to write the path to the uuids as you can see here. Simply writing UUID=xy did not work, which even I as a beginner know should not have been an issue, unless I'm missing something here.

The HDD gets ejected approximately every 24 hours, more or less, under normal use, while I noticed that, using Rhythmbox shortens this lifespan considerably to just some less than six hours or so. I would have assumed it was just something to do with the necessarily installed gst-bad and gst-ugly plugins, but getting rid of Rhythmbox and those plugins absolutely did not help.

A supporter at another forum suggested the cause could maybe found in  var/log/dmesg, but it turns out everything is as it should be there.

So as you can see, I'm at a complete loss. A restart seems to solve the problem temporarily, but I can't keep restarting the PC all the time. (The need to restart after every little change was after all one of the main reasons I left windows behind.)

I dread the day when I will need to work with that HDD for longer than just a few hours, which is, depending on how things work out, not that far off in the future.

So please, does anyone have any idea what the heck the problem could be? I'm getting completely frustrated.   ](*,)

Thanks in advance for any and all help. :)

---

