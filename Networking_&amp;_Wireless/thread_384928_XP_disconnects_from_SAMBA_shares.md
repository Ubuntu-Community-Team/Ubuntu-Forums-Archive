---
title: "XP disconnects from SAMBA shares"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by xadhatter on 2007-03-15
I am running a very simple Samba (3.0.22) file server on Xubuntu 6.10 with a few Windows XP boxes as clients.  The windows machines can browse the server and mount the share fine, however, after a few hours they loose the connection and the only way to fix it is to restart samba.  Below is my smb.conf file and a log file. Any help would be greatly appreciated.

-- smb.conf --
[global]
	workgroup = HOME
	server string = File Server %v
	log file = /var/log/samba/log.%m
	max log size = 50
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	interfaces = lo eth0
	bind interfaces only = yes
	hosts allow = 127.0.0.1 192.168.1.0/24
	hosts deny = 0.0.0.0/0
	security = share
	guest account = agent
	guest ok = yes

[backups]
	comment = Data Backups
	writeable = yes
	browseable = yes
	public = yes
	create mode = 0777
	guest ok = yes
	path = /mnt/backups

I was looking through the logs and this is the only thing thats looked useful.

-- log.192.168.56 --
[2007/03/14 09:39:06, 1] smbd/service.c:make_connection_snum(693)
  192.168.1. (192.168.1.56) connect to service backups initially as user agent (uid=1000, gid=1000) (pid 4918)
[2007/03/14 12:29:15, 1] smbd/service.c:close_cnum(890)
  192.168.1.56 (192.168.1.56) closed connection to service backups

---

