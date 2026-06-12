---
title: "Modules not loaded - etc/fstab cannot be mounted"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by madmaxou on 2010-04-11
Hi there,

when I boot my Ubuntu 9.04 this message is shown on the screen

```
One or more of the mounts listed in etc/fstab cannot yet be mounted:
swap: waiting for UUID=223a1fc1-cc7c-47ea-9b99-e6a45cff6fdb
Press ESC to enter recovery shell
```

Sometimes it shows a message that certain modules could not be loaded...

Nevertheless, after pressing ESC everything works quite normal but still it's annoying.

Thanks in advance (and please keep in mind that I'm an Ubuntu novice),

Madmaxou

---

### Post by Doctor Mike on 2010-04-11
> **madmaxou said:**
> Hi there,

when I boot my Ubuntu 9.04 this message is shown on the screen

```
One or more of the mounts listed in etc/fstab cannot yet be mounted:
swap: waiting for UUID=223a1fc1-cc7c-47ea-9b99-e6a45cff6fdb
Press ESC to enter recovery shell
```Sometimes it shows a message that certain modules could not be loaded...

Nevertheless, after pressing ESC everything works quite normal but still it's annoying.

Thanks in advance (and please keep in mind that I'm an Ubuntu novice),

MadmaxouOne of two things has likely happened. You have moved drives around or an update mucked up the uuid for a drive (swap most likely). It's likely that the uuid for a partition like the swap has changed or other non main partition. There's a code for checking the hardware uuid (I can't remember it, but you can find it) compare that output to the file system / etc / fstab. In my case the id was wrong as well as the partition id sdb5 instead of sdb2.

if you find a difference edit with root permission fstab to correct.

---

