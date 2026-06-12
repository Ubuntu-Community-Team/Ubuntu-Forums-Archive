---
title: "samba tree connect failed: NT_STATUS_PIPE_BROKEN"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by giovanni-viscuso on 2013-11-10
Hi,

when i try to connect to my WD MyBookLive i receive the error:

giovanni@Giovanni-HP:/etc/samba$ sudo mount --verbose -a
mount: proc già montato su /proc
mount: UUID=29E7-9965 già montato su /boot/efi
mount.cifs kernel mount options: ip=192.168.1.64,unc=\\192.168.1.64\Film,guest,iocharset=utf8,uid=1000,ver=1,user=,pass=********
mount error(11): Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

i have tried to connect to the server with smbclient but here i receive NT_STATUS_PIPE_BROKEN:

giovanni@Giovanni-HP:/etc/samba$ sudo smbclient -L 192.168.1.64 -U% -d 5
INFO: Current debug levels:
  all: 5
  tdb: 5
  printdrivers: 5
  lanman: 5
  smb: 5
  rpc_parse: 5
  rpc_srv: 5
  rpc_cli: 5
  passdb: 5
  sam: 5
  auth: 5
  winbind: 5
  vfs: 5
  idmap: 5
  quota: 5
  acls: 5
  locking: 5
  msdfs: 5
  dmapi: 5
  registry: 5
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 5
  tdb: 5
  printdrivers: 5
  lanman: 5
  smb: 5
  rpc_parse: 5
  rpc_srv: 5
  rpc_cli: 5
  passdb: 5
  sam: 5
  auth: 5
  winbind: 5
  vfs: 5
  idmap: 5
  quota: 5
  acls: 5
  locking: 5
  msdfs: 5
  dmapi: 5
  registry: 5
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
doing parameter server role = dc
Unknown parameter encountered: "server role"
Ignoring unknown parameter "server role"
doing parameter realm = WORKGROUP.local
pm_process() returned Yes
Substituting charset 'UTF-8' for LOCALE
added interface wlan0 ip=fe80::ba76:3fff:fe94:4f2%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.73 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="GIOVANNI-HP"
Client started (version 3.6.18).
Connecting to 192.168.1.64 at port 445
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 0
	SO_BROADCAST = 0
	TCP_NODELAY = 1
	TCP_KEEPCNT = 9
	TCP_KEEPIDLE = 7200
	TCP_KEEPINTVL = 75
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 23400
	SO_RCVBUF = 87380
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	TCP_QUICKACK = 1
 session request ok
Substituting charset 'UTF-8' for LOCALE
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.5]
 session setup ok
tree connect failed: NT_STATUS_PIPE_BROKEN


It work 2 or 3 week ago, i haven't changed notthing on storage HEEEELP MEEEE!!!!!!

---

### Post by dentaku65 on 2013-11-11
Hi Giovanni,
where is supposed to be mounted this?
>  mount.cifs kernel mount options: ip=192.168.1.64,unc=\\192.168.1.64\Film,guest,ioch arset=utf8,uid=1000,ver=1,user=,pass=********
I suggest to remove the entry from /etc/fstab for the moment, and try to mount it manually; seems that the error is regarding two or more connections on the same host and with the same user

---

