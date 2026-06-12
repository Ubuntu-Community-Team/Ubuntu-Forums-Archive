---
title: "Samba, missing module vfs_nfs4acl_xattr // compile options for Ubuntu16.04 ?"
date: 2016-10-13
forum: Networking &amp; Wireless
---

### Post by uwe-richter on 2016-10-13
Hello all,


we're running 16.04 with it's Samba v4.3.11 - with no problems so far.
I want to use/try Samba shares on aleady working NFS4 mounts using it's NFS4-ACLs.


In the original Samba sources for v4.3.11 there is a VFS module source
  ./source3/modules/vfs_nfs4acl_xattr.c
but there is no such module for the current Ubuntu package below
  /usr/lib/x86_64-linux-gnu/samba/vfs/


I'd like to go with the current Ubuntu Samba package and 
want configure/make this version from the sources just to copy over the module.


Well, can anybody please give a hint what configure/make options
has been used for the current Ubuntu Samba package?




Thanks
With best regards
Uwe

---

