---
title: "Is there any way to see everything that happens during the boot process?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-05-20
Is there any way to see exactly what is happening during boot up?  Like all of the messages and everything that loads?  Instead of seeing that purple screen with the Ubuntu logo?

---

### Post by cafejunkie on 2011-05-20
Yes there is (and one of the first things I do after a new ubuntu install)
You need to comment out the "quiet splash" line in the /etc/default/grub file
Then run:
```
$ sudo update grub
```
and
```
$ sudo update-initramfs -u
```

---

### Post by begin on 2011-05-20
Or you  can just click the right cursor from the keyboard

---

### Post by Paqman on 2011-05-20
The system logs lots of stuff, including the boot process. Have a browse through the System Log Viewer.

---

