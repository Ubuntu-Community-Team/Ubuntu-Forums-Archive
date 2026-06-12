---
title: "USB Startup Disk Creator"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Calixte on 2009-11-11
I have Ubuntu karmic and I tried to install it on a USB pendrive. For some reason I can't even start with the default USB creator (see [http://ubuntuforums.org/showthread.php?t=1320738&highlight=errno+13](http://ubuntuforums.org/showthread.php?t=1320738&highlight=errno+13)) so I installed the KDE version of the program and tried that. It seems to work, but at the end I get
> Checksums do not match

I tried the program with the command line and got a list of error messages (while the program was working
```
calixte@Lucy:~$ sudo usb-creator-kde
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Error: "/tmp/ksocket-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Error: "/tmp/ksocket-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/knotify4
Error: "/var/tmp/kdecache-calixte" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-calixte" is owned by uid 1000 instead of uid 0.

```
That may be due to the fact I am running a KDE program on Gnome, I don't know. 

Anyways, any idea on what I should do?

---

### Post by ukripper on 2009-11-11
Go to terminal and try using your usb-creator from command line:
```
sudo usb-creator
```

if you get any error then post it on here.

---

### Post by Calixte on 2009-11-11
```
calixte@Lucy:~$ sudo usb-creator
[sudo] password for calixte: 
sudo: usb-creator: command not found
```
:???:

---

### Post by ukripper on 2009-11-11
can you try :
```
sudo usb-creator-gtk
```

---

### Post by delcera on 2011-11-23
Hello,

I've got the same issue as OP, only I'm using Oneiric and trying to make a USB of the same. I downloaded a fresh copy of it an hour or so ago, and keep getting checksum errors.

I ran 'sudo usb-creator-gtk' and got no errors on the terminal, but the checksum mismatch popup still came up.

Any suggestions?

---

### Post by oldos2er on 2011-11-24
Closed. Please start a new thread for your issue.

---

