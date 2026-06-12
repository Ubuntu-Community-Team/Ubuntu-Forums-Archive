---
title: "Fresh 20.04 can't connect to Samba on 19.10"
date: 2020-04-24
forum: Networking &amp; Wireless
---

### Post by shag00 on 2020-04-24
I have a small LAN of 4 PCs and have updated one of them to Kubuntu 20.04 but when I try to connect to any of the existing 19.10 samba servers I get this error: The file or folder smb://XXXXX.local/ does not exist.  From the file manager on the 20.04, when I click on the Network button I can see the samba servers listed, including the server on the client machine which is the 20.04 machine. I get the error message even if I attempt to connect to the server on the 20.04 from the 20.04 machine. Changing max protocol from NT1 to off makes no difference.  I am able to access Samba on the 19.10 PCs from the 20.04 PC. The 19.10 PCs can still connect to each other as normal.  Something has obviously changed in 20.04, does anybody know what it is.

---

### Post by TheFu on 2020-04-24
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes) has links to the Samba release notes.  No idea if that is useful or not.

---

### Post by martin-1963 on 2020-04-25
I'm not good at sharing Samba on a LAN in Ubuntu 20.04

---

### Post by SeijiSensei on 2020-04-25
Might I suggest you switch to NFS for Linux-to-Linux file sharing?  You can run an NFS server on the same machine as runs Samba.

---

### Post by shag00 on 2020-05-04
Actually a system update was released for 19.10 that fixes the problem.

---

