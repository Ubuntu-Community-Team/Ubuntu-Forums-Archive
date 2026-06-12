---
title: "2 ubuntu computer and samba"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by mitjab on 2008-08-17
I have problem with samba. If one computer is windows then samba is visible. If botah computer are running ubuntu linux then samba is not visible.

Any idea why?

my conf file of laptop computer

```

[global]
	name resolve order = hosts wins bcast
	socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
	announce version = 5.0
	username map = /etc/samba/smbusers
	null passwords = true
	passdb backend = tdbsam
	wins support = true
	netbios name = MITJA-LAPTOP
	printing = CUPS
	workgroup = DOMA
	syslog only = yes
	os level = 20
	printcap name = CUPS
	security = user
	syslog = 1

[homes]
	browseable = no
	locking = no
	printable = no
	writable = yes
	comment = Home dirctory
	valid users = %S
	veto files = /*.{*}/.*/mail/bin/
	share modes = no
	create mode = 0600
	directory mode = 0755

[all]
	comment = ALL
	writeable = yes
	path = /media/samba

[netlogon]
	locking = no
	printable = no
	writable = no
	path = /home/netlogon
	guest ok = no
	comment = Network Logon Service
	share modes = no
	public = no

[profiles]
	browseable = no
	locking = no
	printable = no
	writable = yes
	path = /var/samba/profiles
	guest ok = no
	directory mask = 0700
	comment = User Profiles
	create mode = 0600
	public = no

[printers]
	printable = yes
	locking = no
	writable = no
	path = /var/spool/samba
	guest ok = no
	comment = All Printers
	share modes = no
	public = no

[pdf_documents]
	guest ok = yes
	comment = Converted PDF Documents
	writeable = yes
	path = /home/pdf-documents

[pdf_printer]
	lpq command = 
	printable = yes
	print command = /usr/bin/gsambadpdf %s %u
	printing = bsd
	path = /tmp
	guest ok = yes
	comment = PDF Printer Service
	lprm command = 
	use client driver = yes


```

---

### Post by cariboo on 2008-08-17
The only thing that sticks out is that you have:

```
browseable = no
```

In both Homes and Profiles, I have it set to yes in Homes.

To check if you have any errors in your /etc/samba/smb.conf run:

```
testparm
```

In a terminal.

Jim

---

### Post by loboc on 2008-08-17
NFS is faster than SAMBA for UBUNTU TO UBUNTU you can setup NFS and SAMBA for the same directory and use the one thats applicable depending on which OS you boot the client into

---

### Post by dmizer on 2008-08-17
> **loboc said:**
> NFS is faster than SAMBA for UBUNTU TO UBUNTU you can setup NFS and SAMBA for the same directory and use the one thats applicable depending on which OS you boot the client into

I suggest this as well.  There is a good howto linked in my signature.

---

### Post by mitjab on 2008-08-18
I change browsable to yes and run testparm. I get no errors but i still can not see other ubuntu.

I install NFS. Everything is OK but how can i connect to other ubuntu. In network i still can not see other ubuntu.

---

