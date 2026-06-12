---
title: "Cannot navigate an msdfs link on a samba server"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by vanadium on 2007-09-03
I can successfully mount a samba share. The share is mounted according to the following options in /etc/fstab

//files.server.be/vanadium /home/vanadium/mnt/files cifs user,noauto,credentials=/home/vanadium/.smbpasswd 0 0

However, the contents of the mounted directory is a link that is not operational:

$ ls -l mnt/files
total 0
lrwxrwxrwx 1 root root 28 2006-10-20 11:01 home -> msdfs:otherserver.be\vanadium

The people from the it department tell me that the fault is "the linux implementation of smbfs, that does not support dfs links. In the mean time, there is an alternative implementation for Linux that can do that:  http://linux-cifs.samba.org/"

Would that indeed be the issue? As far as I can see, cifs and mount.cifs are installed with Ubuntu Feisty, and mount-cifs reports version 1.10-3.0.24.

---

### Post by vanadium on 2008-05-20
I am bumping this thread. The issue is still there with Ubuntu Hardy. I would be surprised if this is a very rare issue, but it seems so as nobody seems able to shed light on this.

---

### Post by Sondar on 2008-06-18
I recently had a problem navigating a cifs/samba share. I found out that it was related to Microsoft's DFS, and so thought I'd share how I worked around the problem.

First, vanadium's IT department are correct. As the second link on this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183000](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183000) says, DFS support is not expected until version 2.6.25 of the kernel, or 1.53 of mount.cifs. I'm still on v2.6.22 (Gutsy) and v1.10-3 of the respective packages myself. Vanadium's link to linux-cifs may contain a version which includes DFS support, but I didn't look around too closely.

My problem was that I could connect to the server hosting the share, and navigate down the directory tree, but only for a few levels. After a while, I would encounter the error 'Object is remote'. I had no problems connecting to the share under Windows.

(Seems to be similar to the problems this guy has: [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/789009920931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/789009920931))

So under Windows I fired up Wireshark and repeated the whole procedure of connecting to the share and navigating down the tree. Just before the spot where the error would have occurred, I spotted an SMB packet request named GET_DFS_REFERRAL (which is how I first heard about DFS). The response to that contained the path to ANOTHER share - this time, the actual data I wanted, and not just a link pointing to the data.

Having found the address of the actual share server, I just used that instead of my original server address, and was able to connect without problem.

So, my advice to those trying to connect to DFS shares: try to find out the address of the server hosting the data, and not the address of the server hosting the LINK to the server hosting the data.

---

