---
title: "Floppy won't work in Jaunty"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by gizmobay on 2009-06-24
I'm having a problem getting my floppy drive to work properly. I checked /dev/fd0 and this is created. I'm also getting a mount point in the media directory; however, when I click on the floppy0 folder the folder displays nothing in the floppy and it doesn't even turn on or spin. I added floppy to the /etc/modules and rebooted with the floppy in and it complained about a non system disk so it can see it and spin but once I get logged in nothing. I checked group and my username is in the floppy group. I have a dual boot and the floppy works in windows. dmesg | grep floppy shows nothing. I'm a bit confused at to why this doesn't work.

---

### Post by gizmobay on 2009-06-24
Okay, it works if I manually mount the floppy to the mount point. I was expecting it to be like a usb that is once you click to open it would automatically mount. Will I have to mount and umount manually each time?

---

### Post by plucky on 2009-06-24
Post output from a terminal of ```
cat /etc/fstab
```

The floppy should mount with a double click.

---

### Post by gizmobay on 2009-06-24
The relevant parts of the fstab are below.

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks for the help.

---

### Post by egalvan on 2009-06-24
> **gizmobay said:**
> The relevant parts of the fstab are below.


```
/dev/fd0   /media/floppy0  auto  rw,user,noauto,exec,utf8 0 0
```


I've got a working floppy drive (rare, I know)
seems we have the same fstab entry...

this was set up during install...

```
/dev/fd0	/media/floppy0	auto rw,user,noauto,exec,utf8	0 0
```

so your problem lies elsewhere.

---

### Post by LewRockwell on 2009-06-24
thirty year old technology and we still haven't figured out how to master it and keep it mastered

```
sudo who keeps breaking this stuff?
```

---

### Post by gizmobay on 2009-06-24
I have a bunch of blank labeled floppies I'm trying to get rid of and I don't know what's on them so I want to view first before I trash them. Hopefully, I can just mount and then pop them in and out and refresh.

---

### Post by kansasnoob on 2009-06-25
Try installing fdutils either from synaptic or:

```
sudo apt-get install fdutils
```

---

