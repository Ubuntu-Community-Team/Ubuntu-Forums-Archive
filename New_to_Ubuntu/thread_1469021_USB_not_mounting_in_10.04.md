---
title: "USB not mounting in 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by waterlessland on 2010-05-01
I have recently installed Ubuntu 10.04 and am completely happy with its performance, however i cannot get any USB device to mount, and tips would be helpful. Running a Dell Studio 1555

---

### Post by 3rdalbum on 2010-05-01
Are these USB devices formatted as NTFS or as fat32? (by default most USB flash drives are formatted to fat32).

Also can you plug one in, wait 30 seconds, and then post the output of this command:

```
dmesg
```

---

### Post by Jon Monreal on 2010-05-01
Hello,

Could you try going to a terminal, typing
```
ls -l /dev/disk/by-id/*usb*
```
and posting the output here.

Thanks.

---

### Post by The Thunder Chimp on 2010-05-01
Is the "usbmount" package installed in Synaptic. I used to have that problem in Karmic, and that was the solution.

---

### Post by frereonline on 2011-11-09
Amazing, I run Lucid and just checked in Synaptic if usbmount was installed: it wasn't!
I suppose Synaptic will have removed the usbmount package last time I uninstalled something, although I can't remember when this would have happened...
Thanks a lot for help folks!!!

Best vibes from Madrid 8-)

---

