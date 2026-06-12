---
title: "Can not browse ubuntu samba shares even on host machine"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by DrP on 2007-12-21
Hi 

I like many am experiencing a problem with samba network shares.  I have two PC's networking through a adsl modem router.  All running Ubuntu 7.1.  Setup samba on both machines.  Installed winbind and edited the firstater inbound setup file to allow netbiod broadcasts on both machines.  In short everything was working nicely.  Until about a month ago.  Something change on one pc that now I can't browse it.  cant even browse the shares locally.  the following link is the prob I have.

[http://ubuntuforums.org/showthread.php?t=644299&highlight=directory+contents+could+displayed](http://ubuntuforums.org/showthread.php?t=644299&highlight=directory+contents+could+displayed)

Problem is I can't work out the problem (yet), but I am not giving up.  Tried many things, removing samba and all networking debs, then reinstall, editing smb.conf, etc.  Now I am analysing the logs.  I deleted the samba logs to capture the error when trying to browse the shares (by the way i can see the workgroup and then the pc host name, and even the shares but when I try to go into the share(s) directory is when i get the error).  this is what I get.

[2007/12/21 23:02:42, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2007/12/21 23:02:42, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2007/12/21 23:02:42, 0] smbd/service.c:make_connection_snum(1003)
  '/home/drp/Videos' does not exist or permission denied when connecting to [Videos] Error was Permission denied

Also checked permissions and good.

I know many out there are after answers like me, but no one has solved.  Looking for people who wish to help so we can all finally get the answer.

Cheers,

DrP.

---

