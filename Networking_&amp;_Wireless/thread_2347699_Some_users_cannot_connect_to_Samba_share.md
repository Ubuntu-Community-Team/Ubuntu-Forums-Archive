---
title: "Some users cannot connect to Samba share"
date: 2016-12-27
forum: Networking &amp; Wireless
---

### Post by ebsf on 2016-12-27
A LAN network resource configuration issue:

Ubuntu 16.04 server/workstation, Ubuntu 16.04 client/laptop.  Same two users on both, let's say A and B.  Samba is installed on both machines.  On the server, A and B are established as Samba users with the same passwords as each has on the system.  A server/workstation directory is specified as a writable Samba share with access granted to both users, and is established as a Local Network Share with both users granted create and delete permissions.

Here's the problem:  One can access the network share on the server/workstation from the client/laptop using A's credentials but not B's.  The shares are obviously visible and accessible, just only with one set of credentials.  What we need is for each user to be able to access the network directory with his own credentials, not others'.


Any thoughts on causes and solutions would be most appreciated.

---

### Post by TheFu on 2016-12-29
Use NFS for Unix-to-Unix file sharing. NFS is the native method. Almost all file system capabilities are available through NFS, so no need to go with a 20% solution like Samba/CIFS.

[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by ebsf on 2016-12-29
I since have established that the SAMBA failure generalizes to Windows and Ubuntu users.  Specifically, credentialed users can view but not access SAMBA shares with their own credentials; they can access SAMBA shares only with the shared directory owner's credentials.  I'll be posting a separate thread about this general failure and will attempt to link this thread.

---

### Post by TheFu on 2016-12-29
Samba and NFS can easily coexist, but NFS appears as native, mounted, storage and follows almost all expected file/directory permissions.

Just sayin'.  Go native when possible.  Plus, NFS is faster. Much faster.

---

