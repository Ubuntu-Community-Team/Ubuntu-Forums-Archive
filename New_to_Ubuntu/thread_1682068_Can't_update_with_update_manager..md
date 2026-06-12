---
title: "Can't update with update manager."
date: 2011-02-05
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-05
Hi, I just installed Ubuntu 10.10 and when I try to use the update Manager to update the recommended 252 updates, I get an error saying "Failed to download package files", with the details as shown below.

```

Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.5-0ubuntu0.10.10.1_all.deb The HTTP server sent an invalid Content-Range header [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.10.1_i386.deb Bad header line [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/media-player-info/media-player-info_12-1~maverick1_all.deb Bad header line [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.13.1-0ubuntu6_i386.deb Bad header line [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_1.6.4-0ubuntu1.1_i386.deb Bad header line [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.6.4-0ubuntu1.1_i386.deb Bad header line [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.5.4~dfsg-1ubuntu8.2_i386.deb Got a single header line over 360 chars [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.5.4~dfsg-1ubuntu8.2_i386.deb Bad header line [IP: 91.189.88.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_1.6.4-0ubuntu1.1_i386.deb Got a single header line over 360 chars [IP: 91.189.88.30 80]

```

---

### Post by waynefoutz on 2011-02-05
System/Administration/Software Sources, in the button that says "Download from" click "other" then "select best server"

---

### Post by flee0308 on 2011-02-05
Thanks bro, I solved the problem.

---

