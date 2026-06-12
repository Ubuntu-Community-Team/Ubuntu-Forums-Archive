---
title: "Shutdown hangs if CIFS filesystem mounted"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Dave_Rove on 2014-04-23
If I have a CIFS mount of a remote Samba filesystem, then my shutdown hangs for 2 minutes.

 So it's [this]("http://ubuntuforums.org/showthread.php?t=1739820") old problem. It's apparently because the shutdown process stops the network before it tries unmounting, causing the unmount to hang.

 A solution linked from that old thread, that *had *worked, was to create a file **/etc/init.d/umountcifs** containing the CIFS unmount command:

[B]#!/bin/sh
[ "$1" = "stop" ] && umount -a -t cifs -l[/B]

and link to it at the start of the "init.d" shutdown process like so:

[B]sudo ln -s /etc/init.d/umountcifs /etc/rc0.d/K02umountcifs
sudo ln -s /etc/init.d/umountcifs /etc/rc6.d/K02umountcifs
[/B]
Anyway, that solution doesn't work any more. It seems that the shutdown now cuts off the network before the "init.d" shutdown sequence even starts. Something to do with the way that this "upstart" thing works? So my unmount script needs to be executed even earlier somehow.

So how do I insert a script somewhere that executes *after* I select "Shut Down" from the desktop menu but *before* the init.d scripts execute?

---

### Post by Dave_Rove on 2014-04-24
Figured it out. It seems that it's possible to make the Lightdm login manager execute a script on logout, so I've put the CIFS (and NFS) umount there and it works fine. Which is unlike putting the umount at the start of the init.d shutdown sequence where it just hangs. Not ideal, but at least it will work with all Ubuntu desktops, KDE, Gnome, etc. Now my logout shuts down promptly instead of hanging for two minutes.

 (I am curious to know what happens between the lightdm logout and the start of the init.d shutdown sequence that kills the network. I thought nothing should be executed there, but evidently *something* is. )

Anyway, here's the details:

In file: **/etc/lightdm/lightdm.conf**
Add this line: **session-cleanup-script=/etc/lightdm/lightdm.conf.d/cleanup.sh**

Create a file:** /etc/lightdm/lightdm.conf.d/cleanup.sh**  containing:

[B]#!/bin/sh
umount -a -t cifs,nfs -l
[/B]

---

