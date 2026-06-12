---
title: "can't boot into ubuntu"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by libihero on 2010-11-29
my battery was running out, and my computer was trying to hibernate, but i think it powered off before it was done with the process.  now i can't boot into my ubuntu partition.  i attached a picture of the boot (the first two lines normally come up during boot)

---

### Post by karthick87 on 2010-11-29
Are u facing this problem after  updating your kernel?

---

### Post by libihero on 2010-11-29
no, it was working fine until it went into hibernate

---

### Post by karthick87 on 2010-11-29
I think your boot partition is not getting mounted.

---

### Post by philinux on 2010-11-29
> **libihero said:**
> my battery was running out, and my computer was trying to hibernate, but i think it powered off before it was done with the process.  now i can't boot into my ubuntu partition.  i attached a picture of the boot (the first two lines normally come up during boot)

Might be worth fsck'ing your partition from recovery mode or if that dosn't work then fsck from the livecd.

---

### Post by libihero on 2010-11-29
i dunno how to fsck, or what that even means :(

---

### Post by karthick87 on 2010-11-29
**FSCK - File System Check.**Boot your system using live cd and then open terminal and type ```
fsck.<filesystem> /dev/<device>
```[B]
Note:
[/B]Before running fsck unmount your partition first.

---

### Post by libihero on 2010-11-30
what should i put into <filesystem>?
i had already looked up previous threads and i put this into the terminal


sudo e2fsck -fvy /dev/sda4

it fixed the problem, but when i restart later it gives me the same error screen

---

### Post by karthick87 on 2010-11-30
Can you post the output of df -hT command.

```
df -hT

```

---

### Post by libihero on 2010-11-30
wow, right now it wont even let me load a live cd anymore.  i get an error:

"cant open dev/sda no medium found"

and i've tried multiple live cds...

---

### Post by libihero on 2010-11-30
finally got it to boot, this is the output

```
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    943M   24M  919M   3% /
none      devtmpfs    937M  296K  937M   1% /dev
/dev/sr0   iso9660    694M  694M     0 100% /cdrom
/dev/loop0
          squashfs    661M  661M     0 100% /rofs
none         tmpfs    943M  116K  943M   1% /dev/shm
tmpfs        tmpfs    943M   12K  943M   1% /tmp
none         tmpfs    943M   88K  943M   1% /var/run
none         tmpfs    943M     0  943M   0% /var/lock

```

---

### Post by libihero on 2010-11-30
ok i found out what filesystem is lol lets hope it works...

---

### Post by libihero on 2010-12-02
so it happened again even after putting

fsck.ext4 /dev/sda4

doing this did fix it temporarily, but it keeps happening.  does it have anything to do with the kernel?  i'm using the newest stable one (2.6.36), not the standard ubuntu one

---

### Post by libihero on 2010-12-03
so in my eternal cycle of fsck'ing from a live cd and trying to boot, i hit a roadblock.  now i cant boot, mount my hard drive, or fsck.  when i try to fsck i get this error:

```
fsck.ext4: Device or resource busy while trying to open /dev/sda4
Filesystem mounted or opened exclusively by another program?
```

and when i try to mount i get this:

```
 DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending 
```

normally at this point, i would just do a fresh install, but now i cant access my files :(

please help!!!!

---

### Post by libihero on 2010-12-03
solved this with some research.  i downloaded the slax distro and made a live cd out of it and fsck'd from there.  apparently my file system was broken, but for some reason the live cd wasnt detecting the breaks at all.  slax was able to, and now things r dandy :)
thanks for all your guys's help!

---

### Post by libihero on 2011-02-28
ok this happens A LOT to me lately. for both 10.10 and i went down to 10.04 and it still happens.... is there a reason its been happening??? i can fix it with a slax cd, but then later it'll get messed up again and i repeatedly have to bust out the slax cd to fix it.

---

### Post by alegomaster on 2011-02-28
Just reformat the hard drive and reinstall the OS.

---

### Post by libihero on 2011-03-01
i've done that like three times...

---

### Post by libihero on 2011-03-04
bump...

---

