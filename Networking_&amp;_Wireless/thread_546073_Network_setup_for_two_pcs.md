---
title: "Network setup for two pcs"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by geovino on 2007-09-08
I would like to network my two PCs, one with Ubuntu 7.04 and the other is Mint 3.0. They both are connected to a dsl modem and a hub to share the ethernet cables. 

How do I network them together?

---

### Post by matthewrdamon on 2007-09-08
You could use NFS.
First setup the NFS server:
sudo apt-get install nfs-kernel-server

then configure nfs:
gksudo gedit /etc/exports

add the line:
/dir/to/export <ip address of other computer>(rw,root_squash)

In the line above, use :
rw - read write
ro - read only 

Then restart the NFS server using:
sudo /etc/init.d/nfs-kernel-server restart

Then on the Mint computer create a directory for mounting nfs, then use the mount command to mount it:
mkdir /path/to/mounted/dir
sudo mount -t nfs <ip address of ubuntu computer>:/dir/to/export /path/to/mounted/dir

if Mint doesn't use sudo, you must first gain root to use the mount command

---

### Post by geovino on 2007-09-08
I just went to Administration > Shared folders and installed nfs. Can I do the rest in a gui instead of command line?

---

### Post by matthewrdamon on 2007-09-08
I believe that its possible to install/configure nfs from the gui, but as far as restarting the NFS server, to load the config, you need to do that from the command line.  
Also, I have never used Mint, but I am sure you can create the direcotry from the GUI.  If you can find it, i'll bet you can mount it that way too.  I find working on the CLI a lot easier though.  Personal preference I guess.

---

