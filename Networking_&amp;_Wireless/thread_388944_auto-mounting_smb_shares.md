---
title: "auto-mounting smb shares?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by neocookie on 2007-03-20
Hi guys

I've set up an Ubuntu machine on a box with a tape drive to do daily backups, which works great. This machine connects to a couple of windows shares to do a backup, and then those machines are turned off. These shares are defined as mount points in /etc/fstab.

The next morning those connections are gone, and I have to ssh into the Ubuntu machine and 'sudo mount -a' to get everything connected again, even though the backup machine gets switched off every night and back on every morning.

Is there any way I can set something up to monitor when those shares come back online and mount them automatically?

Thanks.

---

### Post by bubblenut on 2007-03-20
You need to set the mounts to be auto in their options. Check out this short article [How to edit and understand /etc/fstab](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by gosh on 2007-03-20
You can also take a look at the use of fusesmb: [http://www.ubuntuforums.org/showthread.php?t=304131](http://www.ubuntuforums.org/showthread.php?t=304131)

It's about xubuntu, but works also on Gnome.

---

### Post by neocookie on 2007-03-20
thanks bubblenut, thats perfect!

---

### Post by neocookie on 2007-03-20
I've done that, and my partitions are now loading with: "auto,user,exec,rw,async"

It looks as though they're loading with permissions for only the "root" user. I've written a small PHP script which needs access to these shares, but it runs under a different user, and I can't get it to run as root.

Is there any way I can mount them as a different user, or change the permissions so my script can read them?

---

### Post by neocookie on 2007-03-22
Checked this morning, and the shares aren't loading automatically. The server is left on, while the shares are on machines that are switched off at night. I have to reboot the server once the other machines are on and issue a "sudo mount -a" once its back up to gain access again.

Any other ideas on how I can get them to mount automatically? This is essentially a head-less system, and I'm trying to automate as much as I can.

---

