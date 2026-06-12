---
title: "Samba mounts, links on share not working"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by arron on 2007-10-27
IIm mounting a samba share with

```
sudo smbmount //horus/Share /media/share -o auto,username="",password="",fmask=0777,dmask=0777
```

The mount connects and all with 7.10.  But any links on the server side instead of opening up the server side, tries to link to the local drive.  This workd great with same command to same server with 7.04.

Can anyone help?

---

### Post by YokohamaGaijin on 2007-10-27
sudo mount.smbfs //horus/Share /media/share -o lfs

Give that a shot.

---

### Post by arron on 2007-10-27
I found the problem.  With newer samba clients it can pick up more details from the server.  Add the following to the server config so it does not pick up the symbolic links as a local link, and goes to the server location instead.

ie a link in //server/share called music linked to -> /home/user/music on the server drive.  Before if u tried to open that via a samba mount on the server drive it would open //server/share/music.  With the new version it would try to open /home/user/music on the local drive..  I hope i explained it ok...

Anyhow, put this on the server /etc/samba/smb.conf in the [global] section, and it fixes it:

```
unix extensions = no
```

---

### Post by rmdegennaro on 2007-12-10
You guys are awesome!  And these forums are nearing Gentoo's reputation in forums.  I just moved to Ubuntu on production boxes, too hard to keep things from breaking with Gentoo.  And this is what I needed for one server.  Many thanks!

---

### Post by arron on 2007-12-12
Glad it helped you out!  Welcome to the community.

---

