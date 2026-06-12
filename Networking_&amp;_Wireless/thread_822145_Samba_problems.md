---
title: "Samba problems"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by Fiddlestx on 2008-06-07
Hello,
I am having a bit of trouble getting samba to work properly. When I try to map my network drive from my XP box i can see the server but I can't expand it to see any of the shares. If i right click and choose explore it will allow me to log in manually and view the files but it will not automatically authenticate with my windows login.

/etc/samba/smb.conf
```

[global]
workgroup = TREBUCHET
server string = %h devserver (Samba, Ubuntu)
wins support = yes
dns proxy = no
interfaces = eth0
bind interfaces only = true
 socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

log file = /var/log/samba/log.%m
syslog = 3
security = user
encrypt passwords = true
passdb backend = tdbsam

invalid users = root
unix password sync = yes
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast



[webserver]
	writeable = yes
	path = /var/www/
	force group = admin
	create mask = 0644
	force user = jeremy
	directory mask = 0755
	valid users = nobody,jcloutier



```

/var/log/samba/log.nmbd
```
[2008/06/07 23:32:14, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name TREBUCHET<1b> for the workgroup TREBUCHET.
  Unable to sync browse lists in this workgroup.
[2008/06/07 23:32:14, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/06/07 23:32:16, 0] nmbd/nmbd.c:main(711)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
```

/var/log/samba/smbd.log
```
2008/06/07 00:24:18, 0, pid=9113] smbd/server.c:main(1059)
  ERROR: failed to setup guest info.
```

---

