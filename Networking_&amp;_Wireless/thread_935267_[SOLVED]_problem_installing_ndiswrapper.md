---
title: "[SOLVED] problem installing ndiswrapper"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by EdenFuchs on 2008-10-01
I'm trying to operate my Atheros AR5007 with Ubuntu 8.04.1, with no Internet connection.
I understood that in order to install the drivers I first need to install ndiswrapper.

I looked in the forum and found the link - []("http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog"). It is a wonderful manual, and it all went well including copying and un-tar-ing the file I downloaded in another PC, and including distclean. When I typed the "make" command, it said after a few lines:
[COLOR="Blue"]***CFLAGS was changed in "/home/eden/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop.[/COLOR]

From then on things did not go so well.

Any advice?

BTW - I don't know if this is relevant, but I have installed the build-essential already.

---

### Post by Partyboi2 on 2008-10-01
You can install ndiswrapper from the ubuntu cd. Stick the cd in the drive and from a terminal 
```
sudo apt-cdrom add
```
```
sudo apt-get update 
```then install
ndiswrapper-util, ndiswrapper-common and  ndisgtk
```
sudo apt-get install ndiswrapper-util ndiswrapper-common ndisgtk
```then to start type
```
ndisgtk
```

---

### Post by EdenFuchs on 2008-10-02
thanks,

some problem - when I typed "sudo apt-get update" I got:
- a bunch (around 20) of: 
[COLOR="Navy"]Err [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) hardy-updates/.... Translation-en_US
  Could not resolve 'il.archive.ubuntu.com' [/COLOR]

then: 
[COLOR="Navy"]Reading package lists... Done[/COLOR]

and then a bunch of: 
[COLOR="Navy"]W: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/hardy/](http://il.archive.ubuntu.com/ubuntu/dists/hardy/).... /Translation-en_US.bz2   Could not resolve 'il.archive.ubuntu.com'[/COLOR]

then finaly:
[COLOR="Navy"]W: You may want to run apt-get update to correct these problems[/COLOR]

---

### Post by Partyboi2 on 2008-10-02
They are failing cause you need a working internet connection to reach the ubuntu repos , so don't worry about them, just go ahead and install those packages[FONT=monospace]
[/FONT]```
sudo apt-get install ndiswrapper-util ndiswrapper-common ndisgtk
```

---

### Post by EdenFuchs on 2008-10-02
Thanks, seems like it worked.
Should I verify it works? How?

---

### Post by Partyboi2 on 2008-10-02
> **EdenFuchs said:**
> Thanks, seems like it worked.
Should I verify it works? How?
In the terminal type[FONT=monospace]
[/FONT]```
ndisgtk
```

---

### Post by EdenFuchs on 2008-10-10
thank you. sorry for the time-gap. family stuff..

ok.
i typed "sudo ndisgtk" and it opened a small window named "Wireless Network Drivers".
This means i'm ok, right?

---

### Post by Partyboi2 on 2008-10-10
It means that you now have ndiswrapper installed. You will need to configure it for your needs.

---

### Post by EdenFuchs on 2008-10-11
thank you!

---

