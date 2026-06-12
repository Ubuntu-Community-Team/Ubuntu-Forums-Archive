---
title: "samba - vista not executing exe's"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-05-24
until 2 days ago my vista was working with samba perfectly (apart from not so fast speeds i have always had) and then when powered up yesterday i couldn't execute .exe's in vista from my samba share. i am now having to copy them locally to execute them. i need this to work as i use my file server a lot. this is my smb.conf which was not modified when this went wrong:

> [global]
	guest account = home
	name resolve order = hosts wins bcast
	announce version = 5.0
	socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
	username map = /etc/samba/smbusers
	null passwords = yes
	encrypt passwords = true
	passdb backend = tdbsam
	wins support = true
	netbios name = SERVER
	printing = CUPS
	default = global
	workgroup = MSHOME
	os level = 20
	syslog only = yes
	' read only = no
	printcap name = CUPS
	syslog = 1
    ; General server settings


; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = no
    write list = root
    create mask = 0777
    directory mask = 0777

[printers]
	browseable = no
	writeable = yes
	printable = yes
	public = yes
	path = /tmp

[_matt]
	path = /data/storage/SHARE/_matt
	writeable = yes
	delete readonly = yes
	force group = root
	force user = root
	create mode = 0777
	public = yes
	allow hosts = 192.168.1.3,192.168.1.1,192.168.1.2
	directory mode = 0777
	guest account = matt
        browseable = yes
[My_Documents]
	path = /data/storage/SHARE/_matt/MATT/My_Documents
	writeable = yes
	delete readonly = yes
	force group = root
	force user = root
	create mode = 0777
	public = yes
	allow hosts = 192.168.1.3,192.168.1.1,192.168.1.2
	directory mode = 0777
	guest account = matt
        browseable = yes
[r]
	guest account = matt
	browseable = yes
	writeable = yes
	delete readonly = yes
	path = /data/storage
	force group = root
	force user = root
	public = yes
	create mode = 0777
	allow hosts = 192.168.1.3,192.168.1.1,192.168.1.2,192.168.1.9,192.168.1.15
	directory mode = 0777
[web]
    path = /data/storage/SHARE/web
	writeable = yes
	delete readonly = yes
	force group = root
	force user = root
	create mode = 0777
	public = yes
	allow hosts = 192.168.1.3,192.168.1.1,192.168.1.2
	directory mode = 0777
	guest account = matt
        browseable = yes
[_home]
	browseable = yes
	writeable = yes
	path = /data/storage/SHARE/_home
	force group = root
	create mask = 0777
	force user = root
	directory mask = 0777
	public = yes
[c]
    path = /
	writeable = yes
	delete readonly = yes
	force group = root
	force user = root
	create mode = 0777
	public = yes
	allow hosts = 192.168.1.3,192.168.1.1,192.168.1.2
	directory mode = 0777
	guest account = matt
        browseable = yes

Matt

---

