---
title: "HowTo: Find Device Node"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by YUbnyEjczqPdLOKKXKTq on 2010-09-04
I am a noob at linux.  I want to execute this command for a USB thumb drive.
```
sudo mkfs.vfat /dev/sdXXX  # replace XXX with your device node
```How do I determine the device node (i.e., XXX), please?

---

### Post by nagaprathyush on 2010-09-04
I am a noob myself and i donno if u call that number as device node or something :D
Try "man fdisk" for options. At the command prompt type "sudo fdisk -l" to list the device nodes.
You can also try "cat /proc/partitions" and see what the output is like. I generally login as root and then type "fdisk /dev/sda", then at the  command prompt type "p" which prints out the information about the hard  disk partitions, type "q" to quit.
Hope that helps):P

---

### Post by QLee on 2010-09-04
[QUOTE=YUbnyEjczqPdLOKKXKTq]...How do I determine the device node (i.e., XXX), please?[/QUOTE]

Enter sudo fdisk -l (that's a lower case L, not a 1) in a terminal window, will give you a list of the nodes on your system.

---

### Post by YUbnyEjczqPdLOKKXKTq on 2010-09-04
Thanks guys. ):P

I chose not to login as root and just use

```
sudo fdisk -l
```as suggested.  It worked just fine.

---

