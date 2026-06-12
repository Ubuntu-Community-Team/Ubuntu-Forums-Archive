---
title: "Can I access my files?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by sharks on 2010-12-22
Hello. Right now, I'm turning my system into a webserver using Ubuntu Server. My question to you would be, say, I've some files on my USB or any other folder, and all I see now is Command line interface in Ubuntu Server, is there any way that I can copy those files to the server?

---

### Post by Grenage on 2010-12-22
Of course; you just need to mount the USB drive, then copy the files over.  The server edition doesn't automatically mount USB drives, but you can install that functionality.

---

### Post by sharks on 2010-12-22
Pretty, can you let me know of that functionality?

Thanks Grenage!

---

### Post by Grenage on 2010-12-22
I believe the most common package is called *usbmount*, but the is another named *ivman*; I've not personally used either.

---

### Post by AndyCee on 2010-12-22
The documentation on automatic mounting for usb's is [here]("https://help.ubuntu.com/community/Mount/USB").

The short version is: ```
sudo aptitude install usbmount
```

Manually, if you know of your devices you can run:

```
sudo mount /dev/<devicename> /mnt
```

---

