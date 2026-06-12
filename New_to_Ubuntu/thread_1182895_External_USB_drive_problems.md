---
title: "External USB drive problems"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by arferbeer on 2009-06-09
I've been using Ubuntu for some time and one of the great pluses for me is that it just works as I have little time for messing with it. 

However, since I updated to 9.04 my FreeAgent external USB drive is no longer listed in "Places" or appears on my desktop unless unplug the usb cable and replug it. I guess this is not a huge issue, but I store my music on there and reaching round the back of my machine or the device every time I want to use it is beginning to annoy me (I just leave it plugged in).

Can someone please tell what I need to do to make sure this drive is mounted automatically on boot up. 

Failing that, a workaround would be to use commands to mount it manually. I've spent a little time looking on the forums but I cannot find anything that tells me how to do that (probably not looking in the right place - my bad)

Thanks for any help.

---

### Post by ajgreeny on 2009-06-09
You could always add a line to /etc/fstab to mount it at boot time, but I'm not sure whether or not that may cause problems if the disk then starts to automount again at some time in the future. Here is a list of commands, and lines for fstab to mount partitions, either manually or at boot.  Just change the dev names to your own rather than these old ones of mine, and make sure mount points specified exist.

Change partition info (eg /dev/hdb1, etc) and path (eg /media/xxxx) to suit the situation, and make sure either that it exists or you have made the mount point first.

Automount linux partition. Add line to /etc/fstab:-
/dev/hdb1 /media/linux ext3 defaults 0 1

Automount fat32 windows. Add line to /etc/fstab:-
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0
or
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
or
/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0

Automount ntfs windows. Add line to /etc/fstab:-
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
or
/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

To mount manually use the following commands:-

Manual mount linux:-
sudo mount /dev/hdb1 /media/linux/ -t ext3

Manual mount fat32 windows:-
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000


Manual mount ntfs windows:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Mount an iso file:-
sudo mount -o loop -t iso9660 path/to/file.iso /mount/path

However, it would make more sense to try harder to find out why it is not automounting any more.

---

### Post by abhiroopb on 2009-06-09
I'm a little confused...

What exactly happens, does it randomnly dismount or does it not mount on bootup, or does it not mount when plugged in.

All three VERY different problems.

---

### Post by arferbeer on 2009-06-09
Thanks for the replies folks. 

One thing I should have mentioned is that I am talking about an external HD connected via usb. This used to automount and now doesn't.

I was running on 8.04 with no problems. The drive was mounted on boot up and usable. The problem I have now is that when the machine boots, my external drive is nowhere to be found - there is no icon for it on my desktop nor the Places pulldown. I'm pretty sure there used to be. At the moment the only way I know to enable it is to unplug the usb cable connecting it to PC and then plug it in again. Within seconds I get an icon on the desktop and an entry in the Places pulldown.

I'm baffled as to why this has suddenly started happening and I'm hoping someone can help me cure it.

Not sure if it's relevant, but the machine is dual-boot with a windoze xp instance on an second internal HD.

Thanks for any help.

---

### Post by abhiroopb on 2009-06-09
Similar problem to yours...?

[http://ubuntuforums.org/showthread.php?t=1128849](http://ubuntuforums.org/showthread.php?t=1128849)

---

### Post by arferbeer on 2009-06-09
Nice one, looks like the issue and has a few things to try. Thanks.

---

