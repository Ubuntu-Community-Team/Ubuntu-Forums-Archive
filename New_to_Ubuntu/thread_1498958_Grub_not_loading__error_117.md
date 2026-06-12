---
title: "Grub not loading : error 117"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by ma3ahmed on 2010-06-01
this is the problem i was facing before... [http://ubuntuforums.org/showthread.php?p=9379182#post9379182](http://ubuntuforums.org/showthread.php?p=9379182#post9379182)

but nothing worked... then out of ideas... i tried to upgrade ubuntu to 10.04 ... but after the upgrade computer automatically restarted and now at startup  Grub does not loads and gives an error 117... help needed...

---

### Post by weirdtalk on 2010-06-01
You probably need to reinstall grub. Use a live cd (any distro) and run ```
$> sudo grub-install /dev/sda 
``` (replace sda with your hard drive if needed.) Then reboot.

---

### Post by ma3ahmed on 2010-06-02
thanks for the rply... i cant find my hard disk when i access from a live cd.. :S ... its not in /media and not in /dev ...

---

### Post by weirdtalk on 2010-06-02
It should be in dev at least. but if it is not in /media or /mnt then you need to mount it to see the files. I find the easiest way is to run gparted and let it do it's scan. This will tell you which name under /dev it is.

After you have that you can either use the commands I gave, or any of the methods here: [LINK]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by sandyd on 2010-06-02
can you run
```

sudo fdisk -l

```
please?

---

### Post by ma3ahmed on 2010-06-04
thnx every 1 for your help... i used a command i found surfing the net.. and it helped me mount my drive...

```
sudo e2fsck -b 32768 /dev/hda2
```

---

### Post by kansasnoob on 2010-06-04
> **ma3ahmed said:**
> thnx every 1 for your help... i used a command i found surfing the net.. and it helped me mount my drive...

```
sudo e2fsck -b 32768 /dev/hda2
```

So, is grub working now?

If not please use the Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ma3ahmed on 2010-06-05
Yes, its working perfectly fine....

---

