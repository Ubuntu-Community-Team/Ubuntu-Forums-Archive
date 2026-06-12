---
title: "fstab, mounting sharedwindows drives"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by onering on 2007-09-03
I have the following in my /etc/fstab file.  It does not mount the shared windows drive on boot.

```
UUID=c7706735-a9e2-4787-aab7-b1da315d01cc none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//mywinxp/test /shareddir smbfs
```



However, if I type the following at the command prompt, it mounts the drive just fine:
```
sudo mount -a
```


What is wrong with my fstab file?


/

---

### Post by Phurious on 2007-09-03
Not sure about your fstab.  In order for me to successfully mount a share from my XP workstation I use the line below in my fstab:

```
//192.168.1.52/Drobo /mnt/Drobo cifs username=<USERNAME>,password=<PASSWORD>,iocharset=utf8 0 0
```

I tried using smbfs, but it proved problematic for me, so I switched to cifs.

---

### Post by onering on 2007-09-03
> **Phurious said:**
> Not sure about your fstab.  In order for me to successfully mount a share from my XP workstation I use the line below in my fstab:

```
//192.168.1.52/Drobo /mnt/Drobo cifs username=<USERNAME>,password=<PASSWORD>,iocharset=utf8 0 0
```

I tried using smbfs, but it proved problematic for me, so I switched to cifs.


Phurious,
This worked!  

I have no idea why though.  
1) I don't have a password on the WIndowsXP box, so I used two qotes like this password="".  Is this correct?
2) Whatg is cifs ?
3) What does this mean: iocharset=utf8?

Anyone?

---

