---
title: "How do i extract/move a file into a directory from a usb stick??"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by edisonmax on 2011-06-15
My previous thread asked this but got no proper answer, so i will try and ask it again.

How do i extract/move a file into a directory from a usb stick??

And can anyone direct me to a website that shows you  how to navigate around the BASH Linux command line interface, i dont know how to find the file which is on the USB stick??

---

### Post by sanderd17 on 2011-06-15
[http://linuxcommand.org/](http://linuxcommand.org/)

The best site (IMHO) for learning the basic shell commands.

After you read that, extracting can be done with the tar program. type
```

tar --help

```
to see the possible options of tar.

---

### Post by _0R10N on 2011-06-15
Well, when plug and external device to your system Ubuntu mounts it under /media/ by default. So you could execute

```
ls /media
```

and see your device already mounted.

So, let's assume it's been mounted as /media/disk1, if you run

```
ls /media/disk1
```

it will list the files and folder you have in the USB stick.

Therefore, once you've located where Ubuntu mounted your device, operating with it is as simple as with any other folder (since Ubuntu will treat it as a regular folder).

Regards!

---

### Post by ajgreeny on 2011-06-15
> **edisonmax said:**
> My previous thread asked this but got no proper answer, so i will try and ask it again.

How do i extract/move a file into a directory from a usb stick??

And can anyone direct me to a website that shows you  how to navigate around the BASH Linux command line interface, i dont know how to find the file which is on the USB stick??
You can probably do it more simply with nautilus, the file manager of ubuntu, or is this a server with no GUI?

---

### Post by edisonmax on 2011-06-16
> **ajgreeny said:**
> You can probably do it more simply with nautilus, the file manager of ubuntu, or is this a server with no GUI?

Yes this is a server, sorry I should have said this in the original post, and yes there is no GUI

---

### Post by sanderd17 on 2011-06-16
Did you read the tutorial I gave? And did it work?

If you have any questions, just ask them.

---

