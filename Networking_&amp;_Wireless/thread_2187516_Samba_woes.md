---
title: "Samba woes"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by c-m on 2013-11-12
Recently installed a fresh copy of 13.10 and found that I can't get Samba to work correctly at all.

I've set up two shares that are partitions on a USB connected drive.

My ubuntu machine is not appearing at all on the local network.

In fact on the samba machine itself I can't even access the shares via samba.

Here's the config file:

```

[global]
;	netbios name = home
	server string = Samba file and print server
	workgroup = workgroup
	security = user
	hosts allow = 127. 192.168.1.
	interfaces = 127.0.0.1/8 192.168.1.0/24
	bind interfaces only = yes
	remote announce = 192.168.1.255
	remote browse sync = 192.168.1.255
	printcap name = cups
;	load printers = yes
	cups options = raw
;	printing = cups
;	guest account = nobody
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 6
	password level = 6
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
;	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = wins lmhosts bcast
;	wins support = no
;	wins proxy = no
	dns proxy = no
;	preserve case = yes
;	short preserve case = yes
	client use spnego = no
	client signing = no
	client schannel = no
;	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes

;	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no

;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
	username map = /etc/samba/smbusers
;	passdb backend = tdbsam
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no
;	winbind refresh tickets = no
;	winbind offline logon = no
;	guest ok = no

[homes]
	comment = Home Directories
	path = /home
	valid users = %U
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	locking = no
	strict locking = no

[profiles]
	comment = User Profiles
	path = /var/lib/samba/profiles
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	create mode = 0600
	directory mask = 0700
	locking = no
	strict locking = no

[printers]
	comment = All Printers
	path = /var/spool/samba
;	browseable = yes
;	writable = No
;	guest ok = no
	printable = yes
	locking = no
	strict locking = no

[pdf-documents]
	path = /var/lib/samba/pdf-documents
	comment = Converted PDF Documents
	admin users = %U
;	available = yes
;	browseable = yes
	writeable = yes
	guest ok = yes
	locking = no
	strict locking = no

[pdf-printer]
	path = /tmp
	comment = PDF Printer Service
	printable = yes
	guest ok = yes
	use client driver = yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	lprm command = 

[MacBackup]
	path = /media/carl/MacBackup
	comment = Backups
	valid users = carl
	write list = carl
	admin users = carl
	writeable = yes
;	available = yes
;	browseable = yes
;	printable = no
	locking = no
	strict locking = no

[SAMSUNG]
	path = /media/carl/SAMSUNG
	writeable = yes
;	browseable = yes
	valid users = carl, smbguest
```

---

### Post by bab1 on 2013-11-12
> **c-m said:**
> Recently installed a fresh copy of 13.10 and found that I can't get Samba to work correctly at all.

I've set up two shares that are partitions on a USB connected drive.

My ubuntu machine is not appearing at all on the local network.

In fact on the samba machine itself I can't even access the shares via samba.

Have you tried Samba using the default smb.conf file.  How did you create the current smb.conf file?  I see this: gadmin-samba and I cringe.  Do not use gadmin-samba.  Using it will just give you endless hours of frustration.

I'd just follow this: [http://www.jonathanmoeller.com/screed/?p=4169]("http://www.jonathanmoeller.com/screed/?p=4169")

---

### Post by c-m on 2013-11-12
Fine, but how do I get a standard smb.conf?

I've tried ```
sudo touch /etc/samba.conf
``` But there is no change in the config file.

Even purging and re-installing samba doesn't remove the config file.

---

### Post by bab1 on 2013-11-12
> **c-m said:**
> Fine, but how do I get a standard smb.conf?

I've tried ```
sudo touch /etc/samba.conf
``` But there is no change in the config file.

Even purging and re-installing samba doesn't remove the config file.

The smb.conf file is at /etc/samba.  That would make the correct path ```
/etc/samba/smb.conf
``` Touch only changes the access time on the file.  It won't change any of the content.  There is no reason to remove Samba just to change the smb.conf file.  I usually make a copy of the original before I modify it.  I  am attaching an unmolested copy here for you to use.

You will have to rename the file and place it in the /etc/samba directory.  Make sure that the ownership and permissions are just as the original file is (was).

---

### Post by c-m on 2013-11-13
Thanks.

I did already find that one though. It different to the original with all that commenting.

Anyway, i've reconfigured it but it still doesn't change anything. I still can't even see the computer on the network or access shares.

---

### Post by bab1 on 2013-11-13
> **c-m said:**
> Thanks.

I did already find that one though. It different to the original with all that commenting.

The commenting is how it comes by default.
> 

Anyway, i've reconfigured it but it still doesn't change anything. I still can't even see the computer on the network or access shares.

Post the output of these commands ```
smbtree -d3

testparm -s

net usershare info --long

cat /etc/hosts


```

---

### Post by c-m on 2013-11-13
Here we go. Some of it is quite long.


```
carl@home:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::222:4dff:fe54:86c1%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.64 bcast=192.168.1.255 netmask=255.255.255.0
Enter carl's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: using WINS server 192.168.1.1 and tag '*'
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
Connecting to host=192.168.1.254
Connecting to 192.168.1.254 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
HOME
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
Connecting to host=192.168.1.254
Connecting to 192.168.1.254 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\BTHUB3         		BT Home Hub 3.0A File Server
Connecting to host=BTHUB3
resolve_wins: Attempting wins lookup for name BTHUB3<0x20>
resolve_wins: using WINS server 192.168.1.1 and tag '*'
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_hosts: Attempting host lookup for name BTHUB3<0x20>
Connecting to 92.242.132.15 at port 445
Connecting to 92.242.132.15 at port 139
Error connecting to 92.242.132.15 (Success)
cli_start_connection: failed to connect to BTHUB3<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
carl@home:~$ 

```


```
carl@home:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[tmp]"
Processing section "[MacBackup]"
Processing section "[SAMSUNG]"
Loaded services file OK.
'winbind separator = +' might cause problems with group membership.
Server role: ROLE_STANDALONE
[global]
	server string = Samba Server
	obey pam restrictions = Yes
	password server = PDC BDC
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
	unix password sync = Yes
	log file = /var/log/samba/log.%m
	max log size = 10
	name resolve order = wins lmhosts host bcast
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = No
	dns proxy = No
	wins server = 192.168.1.1
	remote announce = 192.168.1.255
	remote browse sync = 192.168.1.1 192.168.1.2
	template homedir = /home/%U
	template shell = /bin/bash
	winbind separator = +
	winbind cache time = 15
	winbind enum users = Yes
	winbind enum groups = Yes
	winbind use default domain = Yes
	idmap config * : range = 10000-20000
	idmap config * : backend = tdb
	hosts allow = 192.168.1., 127.
	case sensitive = No

[homes]
	comment = Home Directories
	valid users = %D+%S
	read only = No
	create mask = 0664
	directory mask = 0775
	browseable = No

[tmp]
	comment = Temporary file space
	path = /tmp
	read only = No
	guest ok = Yes

[MacBackup]
	comment = Backups
	path = /media/carl/MacBackup
	valid users = carl
	admin users = carl
	write list = carl
	read only = No
	locking = No
	strict locking = No

[SAMSUNG]
	path = /media/carl/SAMSUNG
	valid users = carl
	admin users = carl
	write list = carl
	read only = No
	locking = No
	strict locking = No

```


```
carl@home:~$ net usershare info --long
[SAMSUNG]
path=/media/carl/SAMSUNG
comment=
usershare_acl=S-1-1-0:R,S-1-5-21-2713149048-334291725-384866979-1002:F,
guest_ok=n
 
```

```
carl@home:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	home

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
 
```

---

### Post by bab1 on 2013-11-13
Try using the file as it was supplied.  Don't use WINS and don't modify the name resolve order.  In fact you only need the host and bcast parameters.  In addition you have defined the Samsung share 2 ways.  Pick one method or the other.

Post the: smbtree -d3 again.

---

### Post by c-m on 2013-11-13
Now I should only have the samsung share defined once. It was shared via the desktop so I removed that.

I've used your file. Here's the output I get:

```
carl@home:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::222:4dff:fe54:86c1%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.64 bcast=192.168.1.255 netmask=255.255.255.0
Enter carl's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
Connecting to host=192.168.1.254
Connecting to 192.168.1.254 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
HOME
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
Connecting to host=192.168.1.254
Connecting to 192.168.1.254 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\BTHUB3         		BT Home Hub 3.0A File Server
Connecting to host=BTHUB3
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_wins: Attempting wins lookup for name BTHUB3<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BTHUB3<0x20>
Connecting to 92.242.132.15 at port 445
Connecting to 92.242.132.15 at port 139
Error connecting to 92.242.132.15 (Success)
cli_start_connection: failed to connect to BTHUB3<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
carl@home:~$ 
 
```

---

### Post by c-m on 2013-11-13
I got it working by adding the line:

```
  name resolve order = bcast host 
```

Thanks for the help before.

---

