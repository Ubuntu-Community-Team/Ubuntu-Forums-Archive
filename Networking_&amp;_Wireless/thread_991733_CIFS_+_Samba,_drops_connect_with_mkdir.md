---
title: "CIFS + Samba, drops connect with mkdir"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by J2000_ca on 2008-11-24
I have my system setup to mount a samba share with libpam-mount. It works however if I try mkdir folder1; mkdir folder1/folder2 I get
> mkdir: cannot create directory `folder1/folder2': Permission denied


Samba Log
> [2008/11/24 03:12:33, 1] /usr/ports/net/samba/w-samba-3.0.32/samba-3.0.32/source/smbd/service.c:make_connection_snum(1033)
  192.168.1.31 (192.168.1.31) connect to service user initially as user user (uid=1005, gid=1005) (pid 1402)
[2008/11/24 03:23:17, 1] /usr/ports/net/samba/w-samba-3.0.32/samba-3.0.32/source/smbd/service.c:close_cnum(1230)
  192.168.1.31 (192.168.1.31) closed connection to service user
[2008/11/24 03:23:20, 1] /usr/ports/net/samba/w-samba-3.0.32/samba-3.0.32/source/smbd/service.c:make_connection_snum(1033)
  192.168.1.31 (192.168.1.31) connect to service user initially as user user (uid=1005, gid=1005) (pid 4657)



Dmesg
> [ 3213.586926]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: For smb_command 50
[ 3213.586930]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: Sending smb of length 84
[ 3213.587675]  /build/buildd/linux-2.6.27/fs/cifs/connect.c: rfc1002 length 0x27
[ 3213.587691]  /build/buildd/linux-2.6.27/fs/cifs/connect.c: invalid transact2 word count
[ 3213.588786]  /build/buildd/linux-2.6.27/fs/cifs/netmisc.c: Mapping smb error code 2 to POSIX err -2
[ 3213.588794]  /build/buildd/linux-2.6.27/fs/cifs/cifssmb.c: Send error in QPathInfo = -2
[ 3213.588799]  /build/buildd/linux-2.6.27/fs/cifs/dir.c: CIFS VFS: leaving cifs_lookup (xid = 1146291) rc = 0
[ 3213.588805]  /build/buildd/linux-2.6.27/fs/cifs/dir.c: CIFS VFS: in cifs_create as Xid: 1146292 with uid: 1000
[ 3213.588811]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: For smb_command 162
[ 3213.588814]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: Sending smb of length 96
[ 3213.589968]  /build/buildd/linux-2.6.27/fs/cifs/connect.c: rfc1002 length 0x6b
[ 3213.590764]  /build/buildd/linux-2.6.27/fs/cifs/cifssmb.c: In SetUID/GID/Mode
[ 3213.590770]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: For smb_command 50
[ 3213.590773]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: Sending smb of length 186
[ 3213.591322]  /build/buildd/linux-2.6.27/fs/cifs/connect.c: rfc1002 length 0x3e
[ 3213.591346]  /build/buildd/linux-2.6.27/fs/cifs/inode.c: Getting info on /test
[ 3213.591356]  /build/buildd/linux-2.6.27/fs/cifs/cifssmb.c: In QPathInfo (Unix) the path /test
[ 3213.591364]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: For smb_command 50
[ 3213.591372]  /build/buildd/linux-2.6.27/fs/cifs/transport.c: Sending smb of length 84
[ 3213.591890]  /build/buildd/linux-2.6.27/fs/cifs/connect.c: rfc1002 length 0xa4
[ 3213.591908]  /build/buildd/linux-2.6.27/fs/cifs/inode.c: Old time 0
[ 3213.591911]  /build/buildd/linux-2.6.27/fs/cifs/inode.c: New time 728397
[ 3213.591914]  /build/buildd/linux-2.6.27/fs/cifs/inode.c: Size 0 and blocks 0
[ 3213.591921]  /build/buildd/linux-2.6.27/fs/cifs/dir.c: Exclusive Oplock inode f0e3d224
[ 3213.591926]  /build/buildd/linux-2.6.27/fs/cifs/dir.c: CIFS VFS: leaving cifs_create (xid = 1146292) rc = 0
[ 3213.591948]  /build/buildd/linux-2.6.27/fs/cifs/file.c: CIFS VFS: in cifs_open as Xid: 1146293 with uid: 1000
[ 3213.591962]  /build/buildd/linux-2.6.27/fs/cifs/file.c: CIFS VFS: leaving cifs_open (xid = 1146293) rc = 0
[ 3213.591980]  /build/buildd/linux-2.6.27/fs/cifs/file.c: Flush inode f0e3d224 file f14f4540 rc 0


---

