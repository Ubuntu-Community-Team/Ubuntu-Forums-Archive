---
title: "Sony DSC-S650 not recognised by Ubuntu 10.4 LTS"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by deadlytackler on 2010-12-31
Hi,
I was trying to download photographs from my Sony digital camera, but My computer is not recognising it. Am using Ubuntu 10.4 LTS
I tried to download thru F-spot, Camera & digiKam but none were able to solve the puzzle.
I tried to mount it but getting this:-

$ sudo mkdir /mnt/camera
$ sudo mount /dev/sr1 /mnt/camera -t vfat -o umask=000
mount: block device /dev/sr1 is write-protected, mounting read-only
mount: /dev/sr1: can't read superblock

May i request to help me on

1. How can I unblock device?
2. What's the way to remove write protect?
3. How to read superblock?

Regards

---

### Post by Paqman on 2010-12-31
Lets back up a couple of steps. You're plugging in a camera over USB, yes? Does the camera have any  settings in it's menus regarding how it presents itself to the PC? What actually happens when you plug it in? Anything at all?

If you think the camera is set up properly and nothing happens when you plug it in, then can you please post the output of this command:
```
lsusb
```

---

