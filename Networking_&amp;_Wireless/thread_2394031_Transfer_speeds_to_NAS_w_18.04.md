---
title: "Transfer speeds to NAS w 18.04"
date: 2018-06-11
forum: Networking &amp; Wireless
---

### Post by ckronengold on 2018-06-11
Very strange (at least to me) behavior when transferring files from my Ubuntu 18.04 box to my Synology 1515+

Using the Ubuntu desktop, dragging a folder to the mounted NAS folder transfers at about 30-35 Mbs. 
But using my Windows 10 machine to access the same shared folder on Ubuntu and copy to the same folder on the NAS, I get 100+ Mbs. 

Is this a Samba vs NFS vs??? thing? 

Thanks in advance.

---

### Post by TheFu on 2018-06-11
TL;DR - don't use FUSE mounting like GVFS. Use a real mount (i.e. manually modify the fstab file).  Could also be a DNS/name resolution issue.  If your network isn't correctly setup for IP, the clients and servers have to try multiple different ways to "find" each other.  Use the IP address to remove this problem until you fix the network.  [https://ubuntuforums.org/showthread.php?t=2350197](https://ubuntuforums.org/showthread.php?t=2350197)

Long version.
Can't tell. You didn't say how the storage is connected, mounted, or anything about the network.  Using a GUI to mount/access remote storage is usually the slowest method under any Unix.  This is due to gvfs being used, which isn't a "real mount." It is using either GIO or FUSE.  On Unix, end-users aren't allowed to mount storage - this is a security thing. FUSE is a way to get around that. There are performance impacts.

If you want the greatest performance, use NFS (the native method for all Unix-based OSes), manually mount the storage in the fstab and don't use a GUI to drag-n-drop files around.  Use the shell.  
Don't use wifi. Try to use GigE (or better) wired networking with as few as possible network hopes between both devices.

Also, what is Mbs?   Is that MBps or Mbps?  Network and disk performance is always done using Mbps, but GUI devs almost always insist on using bytes. Not a big deal, but clarity and consistency matter.

Most commercial small-biz NAS products will be tuned for Windows.

You can test the network using iperf3.
You can test the disk performance using bonnie++.  Best to do this testing directly on the machine connected to the disks, no network involvement.

---

