---
title: "Me TV"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by F.R Mostert on 2009-02-20
Hi I have installed Me TV but when I start it is says No tuner found.  I have tried for several weeks to setup tv in tV time with no succsess. I have a Philips SAA7130 Card that work well in windows,  This is the only program keeping me to Windows.

Regards

---

### Post by sdowney717 on 2009-02-20
supposedly VLC can be made to work with ATSC.

[http://forum.videolan.org/viewtopic.php?f=14&t=54908&start=0](http://forum.videolan.org/viewtopic.php?f=14&t=54908&start=0)

"The ATSC module is disabled in 0.9.8a but is working in 1.0.0 nightlies - although more testing is still needed."

[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

---

### Post by sdennie on 2009-02-20
What is the output of:

```

ls -l /dev/video*
groups

```

Are you sure you are pointing your programs at the right video device and you have permissions to read from it?

---

### Post by F.R Mostert on 2009-02-20
This is the output

tane@Tane:~$ sudo ls -l /dev/video*
[sudo] password for tane: 
crw-rw----+ 1 root video 81, 0 2009-02-20 14:21 /dev/video0
tane@Tane:~$

---

### Post by sdennie on 2009-02-20
And what about the output of:

```

groups

```

You can't read from /dev/video0 unless you are a member of the video group.

---

### Post by F.R Mostert on 2009-02-20
Sorry for late reply

tane@Tane:~$ groups
tane adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
tane@Tane:~$

---

