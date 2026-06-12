---
title: "ideal smb.conf template"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by techboyjk on 2007-03-15
:KS 

I have to deploy several basic ubuntu servers that will act as a nas for windows based www servers, and will also act as a www server for the files that the windows based www server puts on it. Basically, the server will interface with the network 3 different ways, 

-apache server routed to public network eth0, hosting /data as its root directory
-samba server, routed to private network eth1,  sharing /data that a windows 2003 server will mount as a network drive
-samba server, routed to private network eth2, sharing /data that a ubuntu server will mount and move files to /backup

Unless someone wants talk about it, im not so concerned with my apache configuration. What I'm looking for advise on is my samba config. To my understanding, i don't need two different instances of samba for my windows and backup shares. I just need to configure the routing table to send data destined for the windows 2003 server down one nic and the data destined for the backup server down the other nic. If that is the case, I can mark that and move on with my questions about the samba config. 

For these servers, which could be as many as 10 of them, I want to create a template smb.conf file that I can alter prior to installation to harmonize with server dependant variables, like IP, servername, etc. So my goal is to write the best template file, understand what each option means, and know how to tweak it. Alot I have learned and will learn by reading other posts on this forum, but I'd like to start a thread about my own goals. SO far, I've put together the following rough beginners markup of what i understand so far. 

The machines machines that will be acting as the nas (what this config is for), will be something  similar to a celeron 600 w/ 512MB Ram, 2x40GB ide in a raid 1 mirror (OS drive) and 2x700GB in a raid 1 mirror (data drive aka /data). Also the OS I'm working with now is Dapper because I've had bad luck with edgy on older systems. Dapper seems to be the most stable out now, and it has all the functionality I need on the disk. I'm hoping a basic server install of Dapper with Apache and Samba should be enough to stand up a reliable file server that multiple www servers can transfer files to, as well as many http clients can download files from.  I don't expect http requests to ask for more than 10mbps simultaneously... at least not for a while, and in which case, the work will probably be offloaded to another server.

Ok, here is my starter smb.conf

```


[global]

	workgroup = lan
	server string =
	security = user
	encrypt passwords = true
	passdb backend = tdbsam guest	
	unix password sync = no
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUnix\spassword:* %n\n *Retype\snew\sUnix\spassword:* %n\n
	pam password change = no
	preserve case = yes
	short preserve case = yes
	include = /home/samba/etc/smb.conf.%m
	socket options = TCP_NODELAY
	domain master = auto
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	template shell = /bin/bash
	only user =
	guest account = nobody
	invalid users = root  
	dns proxy = no
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	obey pam restrictions = yes
	

[data01]
	
	path = /data
	available = yes
	public = yes
	browseable = yes
	writeable = yes
	valid users = fileserver
	create mask = 0765
	dir mask = 0765


```

---

### Post by techboyjk on 2007-03-16
anybody?

---

### Post by techboyjk on 2007-04-06
bmp?

---

