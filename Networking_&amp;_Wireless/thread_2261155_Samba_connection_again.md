---
title: "Samba connection again"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by andras-merenyinet on 2015-01-16
Hi guys,

I know that there are a lot of discussion about samba, I checked all relevant without success. That is why I decided to begin a next one. Please help me!

I'm on Ubuntu 14.04.1 LTS server. Before I used former stables and there was no problem with smb.
My local linux users have permissions to connect to shared folders instead I get > session setup failed: NT_STATUS_LOGON_FAILURE in case of using smbclient and no user accepted from Windows or Mac clients.
Please find details:

> 
andras@snurf:~$ smbstatus


Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED


Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED


No locked files


> 
andras@snurf:~$ smbclient \\\\snurf\\Samba **** -d5 2>smblog.log
session setup failed: NT_STATUS_LOGON_FAILURE


smblog.log
> 
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
  scavenger: 5
  dns: 5
  ldb: 5
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
  scavenger: 5
  dns: 5
  ldb: 5
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter max log size = 1000
doing parameter obey pam restrictions = yes
doing parameter socket options = TCP_NODELAY
doing parameter server role = standalone server
doing parameter netbios name = snurf
doing parameter unix password sync = yes
doing parameter dns proxy = no
doing parameter map to guest = bad user
doing parameter pam password change = yes
doing parameter auto services = global
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter log file = /var/log/samba/log.%m
doing parameter usershare allow guests = yes
doing parameter syslog = 0
doing parameter wins support = true
doing parameter passdb backend = tdbsam
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter os level = 20
pm_process() returned Yes
Finding user global
Trying _Get_Pwnam(), username as lowercase is global
Trying _Get_Pwnam(), username as uppercase is GLOBAL
Checking combinations of 0 uppercase letters in global
Get_Pwnam_internals didn't find user [global]!
added interface eth0 ip=192.168.1.12 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="SNURF"
Client started (version 4.1.6-Ubuntu).
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for 
no entry for snurf#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name snurf<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name snurf<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
wins_srv_is_dead: 127.0.0.1 is alive
resolve_wins: using WINS server 127.0.0.1 and tag '*'
nmb packet from 127.0.0.1(35072) header: id=3582 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=SNURF<20> rr_type=32 rr_class=1 ttl=258774
    answers   0 char `.....   hex 6000C0A8010C
Got a positive name query response from 127.0.0.1 ( 192.168.1.12 )
namecache_store: storing 1 address for snurf#20: 192.168.1.12
Connecting to 192.168.1.12 at port 445
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
	SO_REUSEPORT = 0
	SO_SNDBUF = 2626560
	SO_RCVBUF = 1061808
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	TCP_QUICKACK = 1
	TCP_DEFER_ACCEPT = 0
 session request ok
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure


Samba port is open (scanned from a Mac client, 192.168.1.12 is IP of snurf server):
> 
Port Scan has started…


Port Scanning host: 192.168.1.12


	Open TCP Port: 	445    		microsoft-ds
Port Scan has completed…


I do not have any idea, please help.

Thank you,
M.A.

---

### Post by andras-merenyinet on 2015-01-17
One more detail.
Samba users are created with smbpasswd as root.
> andras@snurf:~$ sudo smbpasswd -a andras -D3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c: pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
New SMB password:
Retype new SMB password:
Forcing Primary Group to 'Domain Users' for andras

But later smbpasswd as local user:
> andras@snurf:~$ smbpasswd -D3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c: pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.12 bcast=192.168.1.255 netmask=255.255.255.0
Old SMB password:
New SMB password:
Retype new SMB password:
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE

I really don't know how to solve my Samba issue.
As a last try Samba was purged, and installed, users recreated without noteworthy result.

---

