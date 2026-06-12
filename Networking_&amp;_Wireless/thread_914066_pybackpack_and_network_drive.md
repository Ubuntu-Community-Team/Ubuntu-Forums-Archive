---
title: "pybackpack and network drive"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by le_vainqueur on 2008-09-08
I am trying to use pybackpack to backup my research to a network drive.  I am quite sure I have everything configured properly.  When I go to sync, I get the following output:

> Mon Sep  8 12:50:02 2008: Backing up to ****
Fatal Error: Truncated header string (problem probably originated remotely)

Couldn't start up the remote connection by executing

    ssh -C **** rdiff-backup --server

Remember that, under the default settings, rdiff-backup must be
installed in the PATH on the remote system.  See the man page for more
information on this.  This message may also be displayed if the remote
version of rdiff-backup is quite different from the local version (1.1.15).

I am not able to install anything on the server since it is a school network.  The wording of this message ("under the default settings") suggests that there may be a way around this.  Any insights as to whether or not this is possible?

---

### Post by le_vainqueur on 2008-09-09
*bump*

---

