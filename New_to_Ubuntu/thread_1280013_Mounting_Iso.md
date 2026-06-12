---
title: "Mounting Iso"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by raceon4 on 2009-10-01
I can't for the life of me understand the directions to mount an iso file any help?

---

### Post by alphaniner on 2009-10-01
```
sudo mount -o loop /path/to/file.iso /path/to/[COLOR="Red"]mountpoint[/COLOR]
```

[COLOR="Red"]mountpoint[/COLOR] must be an existing folder, preferably empty.

For example, say I have foo.iso in my home folder, and I want to mount it on the empty folder bar in the /mnt directory:

```
sudo mount -o loop /home/alphaniner/foo.iso /mnt/bar
```

---

### Post by BQAggie2006 on 2009-10-01
Found on: [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

From a terminal: 

1) Create a directory to mount your ISO to
```
sudo mkdir /media/iso
```2) Mount your ISO:
```
sudo mount isofile.iso /media/iso -t iso9660 -o loop
```Breakdown of this command:

[LIST]
[*]mount - mount command
[*]isofile.iso - the ISO you want to mount
[*]/media/iso - the directory you created in step 1 to mount the ISO to
[*]-t iso9660 - the filesystem type
[*]-o loop - options flag calling the loop option
[/LIST]

---

### Post by scragar on 2009-10-01
Or as an alternative install gmountiso

Much easier if you ask me.

---

