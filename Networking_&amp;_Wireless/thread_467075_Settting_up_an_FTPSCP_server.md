---
title: "Settting up an FTP/SCP server"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by jeffyee on 2007-06-07
Hi all,

I am new to Ubuntu and need some help setting up Ubutuntu 7.04 desktop version.

What I would like to do is setup up a FTP and SCP server.

According to the documentation that I found at ([https://help.ubuntu.com/7.04/server/C/ftp-server.html](https://help.ubuntu.com/7.04/server/C/ftp-server.html)), i need to run the command "sudo apt-get install vsftpd".  However when I try this I get:

<quote>
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package vsftpd
</quote>

After reading another documentation which said that apt-get should be replaced with "aptitude", I ran the same command replacing apt-get, and it yielded the following result.

<quote>
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended stat information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "vsftpd"
No packages will be installed, upgraded or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives.  After unpacking 0B will be used.
</quote>

Any help would be greatly appreciated.  Once I get the FTP setup, I'll need to setup a SCP server.

Thank you in advance
Jeff

---

### Post by jeffyee on 2007-06-07
I have an alternative to the FTP server.  Does anyone know how to setup a SCP server?  I am using Ubuntu 7.04 desktop edition

thanks
Jeff

---

