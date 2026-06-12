---
title: "Trouble mounting samba share"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by kidcharles on 2008-02-22
Hi all, I'm having a strange problem mounting a remote samba share onto a local directory. I can browse for the samba server in Places->Network without problem (by typing smb://servername in the location bar). I can transfer files and everything with this method. However, I'd like to do an rsync operation from the command line, so I wanted to mount one of the shares on the host to a local directory.

I tried:

```

sudo mount -t smbfs //servername/sharename /media/mountpoint

```

with a bunch of iterations (like adding -o username=username) and using 'cifs' instead of 'smbfs' and I keep getting errors. The username and password are the same on both machines, and the mountpoint on the local machine does exist. Using 'smbfs' I get:

```

7974: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

Using 'cifs' I get:

```

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

Why can I browse and read files using the GUI but I can't with the command line? What am I doing wrong here? Thanks.

---

