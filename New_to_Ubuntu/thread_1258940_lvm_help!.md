---
title: "lvm help!"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by emarkd on 2009-09-05
Hello all,

I'm not very familiar with using LVM and I've got a problem. I had a 3-disk lvm group called 'media'. One of the disks failed and now I can't access the other two. When I run 'sudo vgdisplay', I get:

```

  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Volume group "media" not found

```

What now?  How do I remove that disk from the group and recover what the others contain?

Thanks for your time,
-Mark

---

### Post by emarkd on 2009-09-05
Ok, based on some reading I've done, I ran

```
sudo vgreduce --removemissing media
```

which did something.  Now with vgdisplay, I get this:

 ```
--- Volume group ---
  VG Name               media
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.16 TB
  PE Size               4.00 MB
  Total PE              305238
  Alloc PE / Size       0 / 0   
  Free  PE / Size       305238 / 1.16 TB
  VG UUID               Oa0mqS-Q500-YqHL-pfvG-l7zR-qEW7-eRtW0w
```

but I still can't mount it.  The block level device I used to mount to at /dev/media/media is gone and I don't know why or how to recover it.

Anybody help?

---

### Post by unutbu on 2009-09-05
Have you tried this? [http://specialkevin.com/?p=97](http://specialkevin.com/?p=97)
(In particular, did you run the 
```

sudo vgchange -ay
```
before trying to mount any logical volumes?

What does "lvscan" show?

PS. I believe after the vgchange command -- if it is successful --
the logical volumes should become available in /dev/mapper. 
I would look there for something to mount along with the /dev/VolGroup00/LogVol00 that the link above mentions.

---

### Post by emarkd on 2009-09-05
the vgchange command yielded this:

```
0 logical volume(s) in volume group "media" now active
```

lvscan doesn't see the volume at all

---

### Post by unutbu on 2009-09-05
I'm sorry, I don't know... :(

---

### Post by emarkd on 2009-09-05
Thanks anyway for trying.  I'm going about this in a different direction now and will post another thread.

-Mark

---

### Post by lfhb on 2011-10-15
In case others are trying to recover from the bring, steps within this result after a short google worked for me.  Hope it helps others here.


[http://www.microdevsys.com/WordPress/2011/09/19/linux-lvm-recovering-a-lost-volume/](http://www.microdevsys.com/WordPress/2011/09/19/linux-lvm-recovering-a-lost-volume/)

L...

---

### Post by Brushstroke on 2011-10-15
[LEFT]Why did you revive a thread from two years ago? O_o
[/LEFT]

---

