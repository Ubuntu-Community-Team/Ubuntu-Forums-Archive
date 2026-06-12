---
title: "Read only mount in Samba"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by tim_jones on 2008-04-29
I could connect in 7.10 and 7.04, but since I switched to 8.04 it will only mount in read only.
I go to places-> Connect to Server...
Put in IP address of server(Debian 4.0 running Samba for our Windows computers)
Put in the folder   /data
Put in the user    user
enter the domain   domain

When I connected in the previous versions it would ask for a password.  It dose not do that in 8.04.  It connects me to the server, but I have read only privileges while I should have full access.  
One other strange thing is that once I go to access the SMB folder, another folder appears on the desktop and in the network part of the places menu.   

I have also made a drive in fstab,  it will connect me with read only privileges as well.

---

### Post by MrMunkily on 2008-05-01
Same problem here - driving me nuts.

I found it already reported on launchpad w/no response yet.
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/221387](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/221387)

---

