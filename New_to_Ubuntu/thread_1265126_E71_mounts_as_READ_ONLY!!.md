---
title: "E71 mounts as READ ONLY!!"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by mayank.gulia on 2009-09-13
Dear all

Need some help. When I plug in my E71 and select the "mass storage" option, it mounts automatically on Ubuntu 9.04. Trouble is, it doesn't allow me to add or delete files. I have tried to change permissions using 
(chmod 777 /dev/sdb) but it doesn't help. I've tried editing /etc/fstab but that doesn't help either.

I've read many threads on this regarding pen drives. The usual consensus ends up being "format the pen drive". But since this is my phone being attached as a pen drive, formatting it obviously is not an option.

Any help would be appreciated.

Thanks.

Mayank

---

### Post by 3rdalbum on 2009-09-13
Change the permissions of the **mount point** (the location where the device mounts to, in /media) so your user can write to it.

---

### Post by mayank.gulia on 2009-09-13
Thanks for the response mate.
I plugged in my phone and realized it gets mounted on a automatically created folder "disk" which gets deleted when I unplug the phone. So after plugging the phone, I changed the rights using the following command.

sudo chmod 777 /media/disk

It gives me the following error: "chmod: changing permission of 'disk': Read only file system."

Please help. Thanks in advance.

---

### Post by mbzn on 2009-09-13
When the phone is on it usually mounts read only, Check your phone for a option to connect as a storage device, this should enable you to write to it.

---

### Post by mayank.gulia on 2009-09-13
I am already doing that. In fact, if I dont select the phone as a "mass storage" device, it doesn't even get mounted. I tried all options. However, when I select it as a mass storage device, it gets mounted.  I can browse the contents of my phone. Watch videos, listen to songs. I just cant edit/delete/add content. 

Another peculiar thing, I was trying out Kubuntu last week, which I gave up. But this wasn't happening in Kubuntu. Somehow, Ubuntu always does this. I dunno if this information helps. 

Looking forward to your reply.

---

### Post by mbzn on 2009-09-13
Try mounting another ntfs device (flashdrive or HDD), if that also mounts read only try System>Administration>NTFS Configuration Tool. Check the Enable write support for external device.

---

### Post by mayank.gulia on 2009-09-13
When I go to System --> Administration: I dont see an option that reads NTFS Configuration tool. My windows crashed a few months back so I have been using only ubuntu on my laptop. Hence I dont have access to any ntfs device right now.

Secondly, will a phone memory card be also formatted at "ntfs"? I thought it was always fat32!! I dont know for sure. Just, guessing.

---

### Post by mbzn on 2009-09-13
Not sure either, maybe you can download the ntfs configuration tool via Add/Remove. Not sure where you'll find it as I use ubuntu ultimate edition and it is pre-installed. It might be FAT32, not sure as gparted does not see my phone cards. Will check on my card reader and let you know.

Ok, my card is FAT16.

---

### Post by mayank.gulia on 2009-09-13
Thanks mate. Let me know if you run into something. I'll try out the ntfs configuration tool to see if it helps!!

---

