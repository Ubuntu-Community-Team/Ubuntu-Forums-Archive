---
title: "NFS Permission Denied"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by YellowSnot on 2008-05-15
I can't seem to mount my nfs share. The server is running on 192.168.1.54. I set up the share using nautilus, by right clicking the directory and selecting share, and allowing the ip (192.168.1.30) of my client. This added the following line to /etc/exports:
```

/media/sdb1 192.168.1.54(rw) 192.168.1.30(rw)
```

After a reboot (several now), I try to run this command from the client:
```

sudo mount 192.168.1.54:/media/sdb1 /media/sdb1
```

and I get this output:
```
mount.nfs: 192.168.1.54:/media/sdb1 failed, reason given by server: Permission denied
```

I've checked the following logs on the server:
/var/log/syslog
/var/log/auth.log
/var/log/messages

but they don't contain anything related to the issue. ( I though syslog usually reported when permission was denied)

However, my client machine's syslog contains this:
```
May 15 14:37:30 panda mountd[5989]: mount request from unknown host 192.168.1.54 for /media/sdb1 (/media/sdb1)
```

Where am I going wrong here?

---

