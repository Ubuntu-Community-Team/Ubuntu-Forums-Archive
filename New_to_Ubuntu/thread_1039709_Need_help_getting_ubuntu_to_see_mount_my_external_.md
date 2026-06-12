---
title: "Need help getting ubuntu to see/ mount my external harddrive"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by billmik on 2009-01-14
I plug it in and nothing happens. I looked under computer and its not shown. Any special steps i need to do. Its a westerndigital eide in a enclosure.

---

### Post by jemate18 on 2009-01-14
> **billmik said:**
> I plug it in and nothing happens. I looked under computer and its not shown. Any special steps i need to do. Its a westerndigital eide in a enclosure.

Does it work in other PC? Check the USB ports and other related stuff

---

### Post by pieisgood4589 on 2009-01-14
Do the USBs recognize anything else, or nothing at all?

---

### Post by billmik on 2009-01-14
Yes it works on this computer under vista and ubunu recognizes my mp3 player under usb

---

### Post by kansasnoob on 2009-01-14
Install pmount from synaptic or:

```
sudo apt-get install pmount
```

Simple explanation from synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.


---

### Post by kansasnoob on 2009-01-14
One additional thing! Always be sure to unmount a drive before removing it!

---

### Post by billmik on 2009-01-14
Ok i installed pmount now what? i dont see anything different, and yes i did unmount it from vista.

---

### Post by kansasnoob on 2009-01-14
Well, you may have to restart for the change to take effect. Then plug in the drive and a little drive icon should pop up on the desktop.

---

### Post by billmik on 2009-01-14
That did it thanks for the help

---

