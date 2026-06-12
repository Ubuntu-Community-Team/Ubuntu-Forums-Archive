---
title: "CD Drive No Longer Automounts"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by eutectic22 on 2010-10-09
Originally I had only one CD drive and all was good.  I could insert a CD into the drive, and after a few moments I had access to the CD.  I recently added a DVD burner to the computer.  When I insert media into the DVD drive the media is automatically recognized.  However, now whenever I insert a CD into the CD drive it is not mounted like is was before I added the DVD drive.  The CD drive/media does show up in Places, and I can mount the CD manually.

I have seen references to fstab but mine does not even have an entry for the DVD drive so I am not sure how the DVD drive gets automatically mounted when media in inserted.

My fstab is

```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0779004e-39da-4c8b-8741-cb76da72dd9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af36ff22-06a9-4bf1-b834-1796331a2dba none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I would like for the CD drive to be mounted automatically like it was originally. How can I make that happen?

---

