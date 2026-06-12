---
title: "NFS Create Mask?"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by hawk684 on 2007-09-08
I'm starting to drive myself crazy with this, hopefully one of you guys can help.  Is there a way to set a create mask for NFS like you do with SMB?  How would you create a multi user shared folder with NFS otherwise?  644 is useless for group projects and changing permissions on every file you create doesn't make any sense at all.

I'll put a summary of my situation here in case I'm just not doing something right.  I've got a Thecus N5200 NAS.  Supports NFS, SMB/CIFS, AFP, FTP.  If I mount the drive from my Ubuntu box as an NFS share it works just fine...until I try to access those files from a Windows machine via SMB.  They're owned by my Linux user not by the SMB user (guest).  If I force NFS to squash the user to the guest user, then I can't write to it because I'm not the guest user, I'm my linux user.  Mounting as SMBFS with fmode=0777,dmode=0777 works partially.  It solves the permission issue, but it freezes/ceases to work after a little while.  CIFS seems to be honoring the UNIX permissions no matter what I put in the options (file_mode=0777,dir_mode=0777 or noperm) so it's not much better than NFS.

The perfect solution would be something in /etc/exports that tells NFS, "I don't care who they think they are, when they create a file or directory set it 0777."  Something that just makes CIFS work as dumbly as SMB, "Everything is owned by guest with 0777" would work too.

Please help :confused:

EDIT:  Kind of solution.  Was able to set force create mode and force directory mode on the NAS box itself.  CIFS is now useful.  I'd still like to know if there's a good way to do this with NFS though (it's faster).

---

### Post by trriss on 2008-04-01
I realize this thread is kinda old, but I came upon it through google, and my idea is you might use these options:


all_squash
              Map  all  uids  and  gids  to the anonymous user. Useful for NFS-exported public FTP directories, news spool  directories, etc. The opposite option is no_all_squash, which is the default setting.

anonuid and anongid
              uid/gid of the anonimous user, can eg be the id of samba's guest user?

---

### Post by markba on 2008-05-26
> **trriss said:**
> I realize this thread is kinda old, but I came upon it through google, and my idea is you might use these options:


all_squash
              Map  all  uids  and  gids  to the anonymous user. Useful for NFS-exported public FTP directories, news spool  directories, etc. The opposite option is no_all_squash, which is the default setting.

anonuid and anongid
              uid/gid of the anonimous user, can eg be the id of samba's guest user?

I've tested this solution and it does not work, i.e. it is not solving the problem of this thread: the only this what happens, is that the owner of the file is anonimized. Permission on the modified/created file(s) stays the same.

Anyone with other suggestions?

---

### Post by trriss on 2008-05-27
> **markba said:**
> I've tested this solution and it does not work, i.e. it is not solving the problem of this thread: the only this what happens, is that the owner of the file is anonimized. Permission on the modified/created file(s) stays the same.

Anyone with other suggestions?

Sorry this didn't work for you, I thought it would solve things if all files on smb/cifs and nfs were owned/read by the same user (at least you'd be able to read/write)... If you really have to have a 777 mask this wouldn't work indeed...

There's ofcourse always the -less nice- option of using a script/cronjob to periodically set the permissions...

---

