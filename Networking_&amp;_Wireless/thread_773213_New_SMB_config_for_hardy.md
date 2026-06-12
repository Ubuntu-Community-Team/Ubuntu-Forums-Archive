---
title: "New SMB config for hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by cnschulz on 2008-04-28
Hi, 

I understand there has been some tighnening of SMB security in Hardy. Cool, except it broke my XBMC SMB connections!

I use(d) SHARE level connectivity and I could browse the network and connect with user and pass. When I upgraded to Hardy, the browsing still worked but the user/pass failed. (and i could find no log entries!!)

A little searching and debugging with smbclient lead me to try the "client lanman auth = yes" setting but this did not help and reported the same error (curiously, smb client was still suggesting to use that setting , athough it was set!)

So, I switched to USER level connectivity and smbclient reports no errors however my network browsing no longer works...

Can anyone help out with a solution that will enable network browsing *and* successfull user/pass authentication?

Is there a(n) Hardy upgrade step I missed with respect to SMB?

Below is my smb.conf globals section (before and after messing around)

Cheers

c.

---
<original file>
[global]
	workgroup = xxxxxx
	server string = %h
	interfaces = 127.0.0.0/8, eth0
	bind interfaces only = Yes
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384
	printcap name = cups
	os level = 64
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	printing = cups
	print command = 
	lpq command = %p
	lprm command = 

<after hardy upgrade, connects but no browsing>
[global]
	workgroup = xxxxxx
	server string = %h
	interfaces = 127.0.0.0/8, eth0
	bind interfaces only = Yes
	security = USER
	client lanman auth = yes
        ;client use lanman auth = yes
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384
	printcap name = cups
	os level = 64
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	printing = cups
	print command = 
	lpq command = %p
	lprm command =

---

### Post by lmellor on 2008-05-13
I wish I could help dude, fortunately for me I didn't do an upgrade for fear of something along these lines happening.  If anybody out there can be of any assistance I'd be a very happy man too as this is the only thing stopping me from shifting over to hardy permanently.

I'll post up my smb.conf too...


[global]
netbios name = UPSTAIRS
server string = 
workgroup = MELLOR
    announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
restrict anonymous = 0
    passdb backend = tdbsam
security = user
null passwords = no
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast
usershare owner only = False
wins support = yes
    printing = CUPS
printcap name = CUPS
    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[Large]
path = /media/sdb1
comment = no comment
valid users =
write list =
admin users =
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = yes
printable = no
share modes = no
locking = no

[My Documents]
path = /media/sdb1/My Documents
comment = no comment
valid users =
write list =
admin users =
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = yes
printable = no
share modes = no
locking = no

[Obese]
path = /media/sda6
comment = no comment
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = yes
printable = no
share modes = no
locking = no

---

### Post by cnschulz on 2008-05-13
Hi, 

thanks, i had forgotten about this post...

it seems to have rectified itself! i did reboot both windows and ubuntu pc's at the time (with no effect) however browsing does now work.

maybe it was fixed in the latest round of updates?

btw i had to change to USER authentication... thats the preferred method too.

---

### Post by lmellor on 2008-05-14
you may wanna look at [this]("http://ubuntuforums.org/showthread.php?t=780274")

helped me anyhow :)

---

