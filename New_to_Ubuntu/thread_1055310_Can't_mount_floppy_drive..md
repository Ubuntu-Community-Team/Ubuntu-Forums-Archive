---
title: "Can't mount floppy drive."
date: 2009-01-30
forum: New to Ubuntu
---

### Post by rgb96 on 2009-01-30
Okay so, the NIC on my computer went bad and wouldn't let me get on the network anymore, so we had to replace it. IT was out of stock so we scrounged around the lab at work and managed to find one to put in there so we didn't have to wait for one. Thing is, the drivers came on floppy disks, and I'm having a devil of a time trying to access the floppies.

I edited my /etc/fstab and added 

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and then did 
```
sudo mount /dev/fd0
```

but I still couldn't access the disk. I also read a couple of places that if that didn't work, all you needed to type in was 
```
sudo modprobe floppy
```

but when I try that I get this error
```
WARNING: /etc/modprobe.conf line1: ignoring bad line starting with 'options'
```

and when I look at /etc/modprobe.conf all that is in it is
```
options wctdm24xx8
```

I'm relatively new to Linux and Ubuntu (about 4 weeks) but I had to start using it for this job. I'm using Ubuntu 8.10. Any information would be greatly appreciated, since this computer isn't worth anything in a network hardware testing lab if it can't connect to the network to test any thing.

---

### Post by rgb96 on 2009-01-30
bump... Anybody?

---

### Post by Dirjel on 2009-02-01
> **shazbut said:**
> If you're on 8.10, I hit the same bug today.  Got my answer from here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651")
The floppy module is not loaded by default.  To load for this session only do:
```
sudo modprobe floppy
```
To fix for all sessions you'll need to add ```
floppy
``` to the end of /etc/modules file.

I just added floppy to /etc/modules.  Worked for me.

---

