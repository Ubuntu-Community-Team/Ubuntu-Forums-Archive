---
title: "Gnome doesn't start"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by untenohne on 2009-03-08
Hi!

First of all sorry for my newbie question :(.

Problem:
My ubuntu doesn't start to the gnome environment anymore. Everything worked fine until I pulled of some HSDPA-device (it crashed).
The situation now is: The startup screen (with the ubunutu logo) start --> cursor blinking --> changes to tty1 (i can login there normal)

What I have tried:
Recoverymode (clean,dpkg,fsck,xfix)

I tried to start the xserver with "sudo startx" in the terminal:
..
0:..
..
8: /usr/bin/X11/X [0x8071101]
Saw signal 11. Server aborting.
giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error


Informations:
Wubi installation
Ubunutu 8.10, kernel 2.6.27-11-generic

What have i done? And what are my options? Or how can i give you more informations?

Thanks
untenohne

---

### Post by RomeReactor on 2009-03-08
Hi. Did you upgrade from Hardy, or is that a fresh install? Please post errors 0 thorugh 7.

Also, it's not a good idea to run the X server as root.

---

### Post by untenohne on 2009-03-08
Hi and thx for the fast reply!
I just tried root to get shure that there i nothing else wrong ;)!
And it is a fresh install!

Here is stderr
```
xauth:  error in locking authority file /home/stefan/.Xauthority
xauth:  error in locking authority file /home/stefan/.Xauthority
xauth:  error in locking authority file /home/stefan/.Xauthority
xauth:  error in locking authority file /home/stefan/.Xauthority

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-11-generic #1 SMP Thu
Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
       Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
       to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
       (++) from command line, (!!) notice, (II) informational,
       (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar  9 04:02:15 2009
(==) Using config file: "/etc/X11/xorg.conf"


Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f6c400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79ecc27]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79ba55a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79bd4fc]
5: /usr/bin/X11/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/bin/X11/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b73685]
8: /usr/bin/X11/X [0x8071101]
Saw signal 11.  Server aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/stefan/.Xauthority
```

Whould you say it is a problem of gnome or xserver or? Where should i start my research?

Thx
untenohne

---

### Post by RomeReactor on 2009-03-09
You might want to try post #2 [here]("http://www.linuxquestions.org/questions/ubuntu-63/x-server-wont-load-after-8.10-upgrade.-680377/"). As for this:
> xauth:  error in locking authority file /home/stefan/.Xauthority
run:
```
ls -la | grep .Xauthority
```
 and see if you're the owner (you should see your username reported twice); if not, you could run:
```
sudo chown USERNAME:USERNAME ~/.Xauthority
```
to reassign the file back to your account; change each USERNAME instance for your actual user name.

---

### Post by untenohne on 2009-03-09
> **RomeReactor said:**
> You might want to try post #2 [here]("http://www.linuxquestions.org/questions/ubuntu-63/x-server-wont-load-after-8.10-upgrade.-680377/"). As for this:

run:
```
ls -la | grep .Xauthority
```
 and see if you're the owner (you should see your username reported twice); if not, you could run:
```
sudo chown USERNAME:USERNAME ~/.Xauthority
```
to reassign the file back to your account; change each USERNAME instance for your actual user name.

PERFECT, worked for me!

muchas gracias ;)
untenohne

---

