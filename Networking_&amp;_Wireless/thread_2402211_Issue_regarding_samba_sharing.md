---
title: "Issue regarding samba sharing"
date: 2018-09-27
forum: Networking &amp; Wireless
---

### Post by gnuyts on 2018-09-27
In our research group we have two servers: one has fedora 13 (server 1) as OS and another (server 2) had ubuntu LTS 16.04. On server 2 we have an external RAID system mounted, which should be accessible from server 1. For this purpose we made a specific user &#8220;shareuser&#8221; and enabled samba sharing on server 2 so that only this user has access to the shared mount. On server 1 /etc/fstab was edited so that the external RAID system would automatically get mounted using a credentials file containing the username and password of this &#8220;shareuser&#8221;. This worked perfectly until we upgraded our ubuntu LTS to 18.04. When we now want to mount the external RAID system on server 1 we get a &#8216;permission denied&#8217; error.

---

### Post by TheFu on 2018-09-27
NFS is the native file sharing protocol for Unix-to-Unix systems.  Best to use that. It provides native file permissions, groups, owners, and is a little faster than other protocols.

Ubuntu 18.04 Samba changed some defaults to more secure values.  These forums have workarounds for those, if you decide to stay with CIFS.  I think the change is outlined in the release notes too.  BTW, is Fedora 13 still supported? Considering they are on Fedora 28 now ... I bet not.   Fedora 13 EOL was in 2011.  Well beyond time to move, dude.   [https://fedoraproject.org/wiki/End_of_life](https://fedoraproject.org/wiki/End_of_life)

---

### Post by Morbius1 on 2018-09-27
Some obvious questions:

[1] Did you add &#8220;shareuser&#8221; to the samba password database:
```
sudo smbpasswd -a shareuser
```
[2] Do the Linux permissions on the shared folder ( mount point ? ) in Ubuntu allow shareuser access? And do the Linux permissions allow shareuser to traverse all the directories leading up to the shared folder?

In the event that a miracle did not happen and the issue was not any of the above we are going to need some more info:

[1] Post the fstab entry you are using to access the Ubuntu server.

[2] Need to see how the samba sever is configured on Ubuntu so posing the output of this command would be helpful:
```
testparm -s
```

---

