---
title: "Hard Drive Properties settings"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by championboxes on 2009-02-28
Unfortunately I was playing around with my windows partition properties and not knowing the consequences I changed something and now I cant mount that partition...  

The thing I changed in properties was under the volume tab, and under settings I changed the Mount Point: to I think /media/WINDOWS now every time I try to mount that partition I get an error

```
Cannot mount volume
Details
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

Is there a way to change the Mount Point back to /media/disk?  Ive looked everywhere I thought it could be

---

### Post by NoReflex on 2009-02-28
Maybe you entered "/media/WINDOWS**/**" when you edited the mount point - at least that's what I understand from the error you posted.
Try to mount the partition from the command line :
   sudo mkdir /media/WINDOWS
   sudo mount /dev/hdax /media/WINDOWS
Also you might want to check the contents of /etc/fstab

Best wishes,
NoReflex

---

### Post by championboxes on 2009-02-28
[QUOTE=
   sudo mkdir /media/WINDOWS
   sudo mount /dev/hdax /media/WINDOWS
[/QUOTE]

I didnt get the mount /dev/hdax to work but I found in another thread
```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
``` just had to change it to sda2 and that done the trick! thanks for pointing me in the right direction

---

### Post by NoReflex on 2009-02-28
I should have mentioned hdax was a substitue for hda (IDE drive) - number x (which could be 1 ,2, 3) - sorry about that. sda2 points to the second SATA drive.

I'm glad you solved your problem.

Best wishes,
NoReflex

---

