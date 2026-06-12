---
title: "autofs + smbfs"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by gruadp on 2008-01-17
I try to mount my smb-share via autofs.  Mounting in fstab does not work, cause the network is not online yet when fstab is processed. Manually mounting the smb-share works perfect.

Fact is, I dont know how autofs works. I figured out the line to use for my smb-share:

```
matrix -fstyp=smbfs,credentials=/etc/smb.credentials.antimatrix,uid=1000,gid=1000,dmask=777,fmask=777 ://antimatrix/root
```


But I dont know where to put. There are several files that seems to be relevant:

/etc/auto.master
/etc/auto.smb

auto.smb is more a script than a configuration-file but some howtos or forum-threads insist on putting my config-line there, but it makes no sense to put a configline like this in a bash-script. SoI followed another howto and created my own configfile /etc/auto.auto and refer to it in auto.master

```
# cat /etc/auto.master
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
#/misc  /etc/auto.misc
#/net   /etc/auto.net
/mnt /etc/auto.auto --ghost

```

```
# cat /etc/auto.auto
matrix -fstyp=smbfs,credentials=/etc/smb.credentials.antimatrix,uid=1000,gid=1000,dmask=777,fmask=777 ://antimatrix/root

```

but I always get the following error:

```
Jan 17 10:17:16 mind automount[30243]: >> mount: special device //antimatrix/root does not exist
Jan 17 10:17:16 mind automount[30243]: failed to mount /mnt/matrix

```

And I dont even know if I'm on the right path. The error looks to me as if the system ignores that wwe are talkng about a smb-share here and takes //antimatrix/root as local device-name.

any hints greately appretiated,
thnx
peter

---

