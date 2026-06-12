---
title: "Get live CD to just go to CLI?"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by lugoteehalt on 2010-07-10
Have very little space on hard drive so want the live CD to just produce a black screen, CLI.  No X, no Gnome.

Is this possible?  Thanks for any help.:)

---

### Post by Darkness Des on 2010-07-10
Ubuntu Server Edition is that. If you don't want a server, then don't install the packages. It's just Ubuntu but without the desktop environment.

---

### Post by Elfy on 2010-07-10
Are you talking about making anew install or accessing the system to do something?

---

### Post by Paqman on 2010-07-10
If what you want to do is install a command-line only system then you'll want to install using the Alternate CD, or better yet, the Minimal ISO. The LiveCD  isn't really designed to do this.

The Minimal ISO is especially good. How much space do you actually have the drive? A minimal install with gnome-core only takes up about 1.2GB when installed.

---

### Post by lugoteehalt on 2010-07-10
> **forestpiskie said:**
> Are you talking about making anew install or accessing the system to do something?Great thanks everyone!

I'm using the software computer VirtualBox.  Installed Debian Lenny 5 32 bit on it so I could continue to use Adobe flashplayer - which Adobe no longer supports 64 bit operating systems like mine on.  Installed Lenny with logical volume management, LVM.  But the root partition, /, is too small.

Upshot is I need to unmount the / "partion" but cannot do this because it is obviously in use.  So boot into VirtualBox with the live CD and use that to increase the size of the / virtual partition.

Surprisingly, at least to me this works.  But I have the problem that the / is too small for all the gnome type stuff, at least when I add the stuff necessary to do the LVM increase in the size of the / partition.

Sorry about this gibberish but you did ask.:)

So presumably I just need a minimal command line from the live CD then can install system-config-lvm and sort out the / virtual partion?

Edit:  Sorry, system-config-lvm is a graphical tool gor making lvm easy so have to have graphics.

Tried uninstalling firefox and that helped, but did not quite get there.  The thing filled up because I had to uncomment the stuff in /etc/apt/sources.list otherwise could not download sytem-config-sources.list.

---

### Post by Paqman on 2010-07-11
> **lugoteehalt said:**
> 
Edit:  Sorry, system-config-lvm is a graphical tool gor making lvm easy so have to have graphics.


Then from the command-line system install:
```
sudo apt-get install xorg gnome-core gdm system-config-lvm
```
That should give you a quick and dirty graphical environment to run the LVM tool in.

---

