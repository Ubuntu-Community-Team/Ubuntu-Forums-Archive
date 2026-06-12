---
title: "Can't write to second hard drive"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by kramer65 on 2009-09-11
Hello,


I've got a second hard drive in my pc (/media/sdb1) which I want to use for backups. I'm trying to transfer a document to it by simply dragging and dropping it into there, but it says I can't.

I guess I've got no rights, or maybe I am not the owner. It would be great if somebody could help me on the way..?

---

### Post by talsemgeest on 2009-09-11
> **kramer65 said:**
> Hello,


I've got a second hard drive in my pc (/media/sdb1) which I want to use for backups. I'm trying to transfer a document to it by simply dragging and dropping it into there, but it says I can't.

I guess I've got no rights, or maybe I am not the owner. It would be great if somebody could help me on the way..?
If all the drive is for is backups, you should be safe doing a chmod 777: ```
sudo chmod 777 /media/sdb1
```

---

### Post by nothingspecial on 2009-09-11
You might want to make sure you own the drive

```
sudo chown -R username:username /media/sdb1
```

I wouldn`t use 777 permissions for backups.

Are you sure it`s not /media/disk1 listed in fdisk as /dev/sdb1?

---

### Post by kramer65 on 2009-09-11
That is great! Thank you!

I didn't imagine it to be so easy.. :)

Thanks again!


[edit] 
Wait. I didn't see the answer f nothing special yet. 

I just did "sudo chown -R username:username /media/sdb1"

What else do I need to set the chmod to in order to have it safe..?

---

### Post by Mostly.Harmless on 2009-09-11
[SIZE=3]Hey guys Im having the same problem. Ive done some background reading and Ive found some hit and miss solutions.

Im not trying to hijack this thread, I just though theres a few of these around so It would be better to do it here rather than make another new HD thread .

Ive reformatted it 1000 times, Ive used all sorts of file types. 

-FYI, Its a samsung 1tb, this hard drive is a 2nd internal hard drive. It is not used to boot. I have another 500GB HD for that which appears to be working. It is called Filesystem I think

-Im using GPARTED

I can usually get it to appear, but I get the usual "you cant do anything with this because access is denied" errors.

So I guess my questions would be:

What file type? (Ive read around and ext3 seems to be the best)

I want the whole Tb to be one whole block, no need for partitions or other complications, Should it be a primary, extended or logical partition?

And I guess how to get rid of that "access denied" errors

Any help appreciated, thanks.

(also, Im a ubuntu/linux beginner)
[/SIZE]

---

### Post by talsemgeest on 2009-09-11
> **kramer65 said:**
> That is great! Thank you!

I didn't imagine it to be so easy.. :)

Thanks again!


[edit] 
Wait. I didn't see the answer f nothing special yet. 

I just did "sudo chown -R username:username /media/sdb1"

What else do I need to set the chmod to in order to have it safe..?
If it works, then that should be fine.

Also to nothingspecial: Why wouldn't you use 777 for backups. Isn't it best for it to be easy to restore, even from another account?

---

### Post by Mostly.Harmless on 2009-09-11
Wow, I didnt think that message would come out so sporadic.

In my background reading, most people helping ask for this so I thought I would post it in advance:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db44a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    5  Extended
/dev/sda5               1      121601   976759969+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003758a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60050   482351593+  83  Linux
/dev/sdb2           60051       60801     6032407+   5  Extended
/dev/sdb5           60051       60801     6032376   82  Linux swap / Solaris
chris@chris-desktop:~$ 


Also, There is nothing on the Samsung TB, so reformatting or wiping is no problem.

/Thanks

---

### Post by nothingspecial on 2009-09-11
> **kramer65 said:**
> That is great! Thank you!

I didn't imagine it to be so easy.. :)

Thanks again!


[edit] 
Wait. I didn't see the answer f nothing special yet. 

I just did "sudo chown -R username:username /media/sdb1"

What else do I need to set the chmod to in order to have it safe..?

Well it depends on who else has access to the computer. For example I don`t mind my wife and kids viewing a backup drive but I don`t want them removing anything by accident. 755 would be my preference.

---

### Post by Mostly.Harmless on 2009-09-11
And this one:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=614e793e-4089-438f-b0a1-2f58d2aea0a9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=76b3ad15-2249-426f-af70-668be3aefa42 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by nothingspecial on 2009-09-11
Does the drive appear in /media ?

---

### Post by Mostly.Harmless on 2009-09-11
Not sure exactly what your asking, but it is currently displayed in the computer places, nothing can be done/put on to it

Im currently removing the "extended" partition system on it and re partitioning it to just a "Primary Partition" using the bog standard ext3 format. This seems to be the best place to start.

---

