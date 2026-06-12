---
title: "Trouble mounting USB devices."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-03
I seem to have a lot of trouble mounting my usb flash drive, or any usb device for that matter, to my machine. I googled up on it and did what I thought I was being told.

I edited /etc/fstab and added the line 
```
/dev/sda1     /mnt/USB     auto     noauto,owner,kuzu     0     0
```

and then mounted it via terminal. However, when I do this, instead of getting my usb devices, somehow I managed to mount the other hard drive I have in my machine for windows with a dual boot.

Anyone have any suggestions?

---

### Post by bhadotia on 2009-02-03
> **rgb96 said:**
> I seem to have a lot of trouble mounting my usb flash drive, or any usb device for that matter, to my machine. I googled up on it and did what I thought I was being told.

I edited /etc/fstab and added the line 
```
/dev/sda1     /mnt/USB     auto     noauto,owner,kuzu     0     0
```

and then mounted it via terminal. However, when I do this, instead of getting my usb devices, somehow I managed to mount the other hard drive I have in my machine for windows with a dual boot.

Anyone have any suggestions?

When you plug in your flash drive does it show up in nautilus (Places>Computer). Also /dev/sda is usually the primary HDD. I think you should try /dev/sdb1 instead (if you have more than one hard disk try a different letter after sd e.g., try 'c' if you have two HDDs because sda and sdb would be your HDDs)

---

### Post by rgb96 on 2009-02-03
No it does not show up in Nautilus, but the sdb sounds like a good idea. let me go try it.

---

### Post by rgb96 on 2009-02-03
Okay, now I'm getting this error when I try to mount via terminal

```
mount: /dev/sdb already mounted or /mnt/USB busy
```

but I still can't access the device, so that leads me to believe it is not already mounted. When I try to access it through Nautilus, I get an error message telling me that only the root user can mount it.

---

### Post by achase79 on 2009-02-03
it would be best if you used the uuid.  You can obtain the uuid with the blkid command.

fstab would look like:
```
UUID=xxx.yyy.zzz      /mnt/USB     auto     noauto,owner,kuzu     0     0
```
replacing "xxx.yyy.zzz" with the uuid of your flash drive

---

### Post by rgb96 on 2009-02-03
How am I to know which UUID corresponds with my USB flash drive?

Also, I tried blkid with my flash drive in, and with my flash drive out, and got the same results both times.

---

### Post by rgb96 on 2009-02-03
bump... anyone?

---

### Post by YesSir on 2009-02-04
There´s more going on here:

[http://ubuntuforums.org/showthread.php?t=857374&](http://ubuntuforums.org/showthread.php?t=857374&)

I´m still looking for the answer ;)

---

