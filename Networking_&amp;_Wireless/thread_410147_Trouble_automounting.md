---
title: "Trouble automounting"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by dlm8751 on 2007-04-15
I cannot get ubuntu laptop's autofs to mount my ubuntu server's export.

Here's the export on the server:
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home 192.168.1.1/24(rw,no_root_squash,async)
/media/music/music 192.168.1.1/24(rw,no_root_squash,async)


Here's the laptop's auto.master.
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/home2 /etc/auto.home2


Here's the laptop's auto.home2
mcreynoldsd -rw,soft,rsize=8192,wsize-8192 tera:/home


Manual mounting works fine. the auto mounting does not.

---

