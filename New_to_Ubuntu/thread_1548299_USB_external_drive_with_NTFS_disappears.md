---
title: "USB external drive with NTFS disappears"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by ronbarak on 2010-08-08
[COLOR="Blue"]Hi,

I use Ubuntu 10.04 WUBI, where I have a USB external drive with NTFS mounted as follows:[/COLOR]

```
/dev/sdc1 on /media/931 GB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

[COLOR="Blue"]From time to time this disk's icon disappears from the panel, and if trying to access it, I get:[/COLOR]

```
$ sudo ls -ls /media/931\ GB/
ls: cannot access /media/931 GB/: Transport endpoint is not connected
```

[COLOR="Blue"]When I try to umount it, so I could disconnect the USB plug and reconnect it again, I get:[/COLOR]

```
$ sudo umount /media/931\ GB/
umount: /media/931 GB: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
$ sudo umount -f /media/931\ GB/
umount2: Device or resource busy
umount: /media/931 GB: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
```

[COLOR="Blue"]Alas,[/COLOR] lsof [COLOR="Blue"]or[/COLOR] fuser [COLOR="Blue"]do not reveal any process that has /dev/sdc1 or /media/931 GB[/COLOR]

[COLOR="Blue"]Sometimes, if I wait some times, another call to[/COLOR] sudo umount -f /media/931\ GB/ [COLOR="Blue"]will be successful.[/COLOR]

[COLOR="Blue"]Can you shed some light on the above occurrence ?
(Googling for key-words from the above didn't enlighten me) 

Thanks,
Ron.[/COLOR]

---

### Post by phyrexianhulk on 2010-08-20
I have exactly the same problem with an NTFS USB drive attached to my fileserver. I mounted it to /media/usb and since tonight it went missing with the same errors. even "ls" won't work in /media directory:

397430    ? d?????????  ? ?         ?            ?                ? usb
397004    ? d?????????  ? ?         ?            ?                ? usb2

Is there already a solution for this? Thanks!

---

### Post by phyrexianhulk on 2010-08-20
Okay, i fixed it now, but i don't know why it happened.

One of the servers users left a screen open with a prompt into /media/usb. Therefore the umount call told me that it was in use.

That however, does not explain why i was not able to 'ls' or change to the directory.

---

