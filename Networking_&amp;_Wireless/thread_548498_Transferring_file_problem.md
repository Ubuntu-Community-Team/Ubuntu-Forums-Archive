---
title: "Transferring file problem"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-09-11
Hi folks,

Server - Ubuntu 7.04 server amd64
rox - File Manager
IP - 192.168.0.10

Workstation - Ubuntu 7.04 desktop
nautilus - File Manager
IP -192.168.0.11

openssh-server and openssh-client installed on both PCs
ssh not yet installed.


On server
$ ssh -Y satimis@192.168.0.11 nautilus

started nautilus locally.  But I can't copy file from nautilus on rox, always indicating error


On worstation
$ ssh -Y satimis@192.10.11 rox
satimis@192.168.0.10's password:
```

/usr/bin/X11/xauth:  error in locking authority file /home/satimis/.Xauthority

(process:5189): Gdk-WARNING **: locale not supported by C library

(rox:5189): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
X11 connection rejected because of wrong authentication.
The application 'rox' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.

```
Where shall I check?  Do I need install ssh on both PCs?

TIA


B.R.
satimis

---

### Post by satimis on 2007-09-11
Hi folks,


Problem partially solved as follow;

On Sever

$ ls -l /home/satimis/.Xauthority```

--rw------ 1 root root ....... /home/satimis/.Xauthority
```

$ sudo chown satimis:satimis /home/satimis/.Xauthority
$ ls -l /home/satimis/.Xauthority```

--rw------ 1 satimis satimis ........ /home/satimis/.Xauthority
```

On workstation
$ ssh -Y satimis@192.168.0.10 rox

started rox file manager.

But still can't transfer file with drag-n-drop

warning;```

ERROR: No such file or directory

Done
There was one error.

```


satimis

---

### Post by clauguia on 2008-02-05
If your problem is transfering files, this is what you do:

On Workstation, open Nautilus (or your prefered file manager). Click on the address bar (on Nautilus, it's hidden: open it by clicking in the image of a white rectangle left to the location). Write :
fish://192.168.0.11 (the ip address of your server here)

and ENTER

put the name of the user and the password and OK

thus you will have a Nautilus window to your server home folder.

Open another nautilus and is just dragging and dropping.

For big files, though, I recommend using command line "scp -C" and for folders "scp -rC". Use "man scp" and "scp --help" for details.

---

### Post by satimis on 2008-02-05
> **clauguia said:**
> If your problem is transfering files, this is what you do:

On Workstation, open Nautilus (or your prefered file manager). Click on the address bar (on Nautilus, it's hidden: open it by clicking in the image of a white rectangle left to the location). Write :
fish://192.168.0.11 (the ip address of your server here)

and ENTER

put the name of the user and the password and OK

thus you will have a Nautilus window to your server home folder.

Open another nautilus and is just dragging and dropping.

For big files, though, I recommend using command line "scp -C" and for folders "scp -rC". Use "man scp" and "scp --help" for details.
Thanks for your advice.


Nautilus is not running on Ubuntu server.  A light-weight desktop, Fluxbox, and a light-weight file manager, ROX Filer, are installed.  IIRC Rox Filer can be forwarded to Ubuntu workstation but unable to drag file from it and drop the same onto Nautilus.  Finally I installed Rox Filers on the workstation to solve the problem.

For sizable file I'll run "scp" to do file transfer.


B.R.
satimis

---

