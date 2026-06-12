---
title: "File sharing autofs with sshfs"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Gokee2 on 2008-03-04
Hello all,

I am using autofs on a laptop to mount part of a server through sshfs.  (Mostly like [http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/](http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/)).  The laptop runs xubuntu gutsy.  I added a shortcut to the autofs mount on the sidebar of Thuner.

The problem is when the network is not connected on the laptop sshfs fails rather badly.  Thuner stops working I can`t even cd into the place the automount should be and sometimes "sudo /etc/init.d/autofs stop" does not work (stays forever at the stoping msg).  If I get the laptop connected to the network again and wait for sshfs to reconnect (I am using the reconnect option) then all returns to normal.

Is there any way to fix this and have sshfs gracefully umount if it runs into problems?  If not is there a better way to share the files?  I want the files to be encrypted during transit.

Thanks,

Gokee2

---

