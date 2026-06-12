---
title: "Ubuntu machine no longer found in Workgroup"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by JSTREETE on 2013-12-28
Hello,

Sorry, I am not too experienced in linux but I had this setup working and it suddenly does not.

I have 3 devices on my network:
* Vista pc
* Ubuntu 13.10 pc
* Apple Tv with xbmc

I had been able to share from both my Windows machine and Ubuntu machine to my AppleTv without problem but now suddenly it cannot see my Ubuntu machine in the Workgroup.  I also can no longer see it from my Windows pc.  (also not able to see windows machine from ubuntu)

I am able to ping the Ubuntu pc and even remotely control it with VNC.

I checked my smb.conf global settings and it is still set to Workgroup.

I checked to make sure Samba is still running and it looks like it is.

Any help would be greatly appreciated.

Thanks.

---

### Post by bab1 on 2013-12-28
> **JSTREETE said:**
> Hello,

Sorry, I am not too experienced in linux but I had this setup working and it suddenly does not.

I have 3 devices on my network:
* Vista pc
* Ubuntu 13.10 pc
* Apple Tv with xbmc

I had been able to share from both my Windows machine and Ubuntu machine to my AppleTv without problem but now suddenly it cannot see my Ubuntu machine in the Workgroup.  I also can no longer see it from my Windows pc.  (also not able to see windows machine from ubuntu)

I am able to ping the Ubuntu pc and even remotely control it with VNC.

I checked my smb.conf global settings and it is still set to Workgroup.

I checked to make sure Samba is still running and it looks like it is.

Any help would be greatly appreciated.

Thanks.

From the Ubuntu host post the output of these 3 CLI commands```

pgrep -l mbd

smbtree -d3

cat /etc/samba/smb.conf
```

---

### Post by JSTREETE on 2014-01-02
```
jeff@JEFF-UBUNTU:~$ pgrep -l mbd
990 smbd
1004 smbd
1502 nmbd
```

```

jeff@JEFF-UBUNTU:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21a:a0ff:fec2:ac7f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.171 bcast=192.168.255.255 netmask=255.255.0.0
Enter jeff's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\JEFF-UBUNTU    		Samba 3.6.18
Connecting to host=JEFF-UBUNTU
resolve_lmhosts: Attempting lmhosts lookup for name JEFF-UBUNTU<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name JEFF-UBUNTU<0x20>
resolve_wins: Attempting wins lookup for name JEFF-UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name JEFF-UBUNTU<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\JEFF-UBUNTU\NewShare       	
		\\JEFF-UBUNTU\APPLE-MOVIES   	
		\\JEFF-UBUNTU\test           	For testing only, please
		\\JEFF-UBUNTU\IPC$           	IPC Service (Samba 3.6.18)
```


```
jeff@JEFF-UBUNTU:~$ cat /etc/samba/smb.conf
[global]
	workgroup = WORKGROUP
[test]
	comment = For testing only, please
	path = /home/jeff/APPLE-MOVIES
	read only = no
	guest ok = yes
```

---

### Post by JSTREETE on 2014-01-02
sorry, just realized I had been playing with smb.conf.  Let me put the old file back and rerun the tests.

---

### Post by bab1 on 2014-01-02
> **JSTREETE said:**
> jeff@JEFF-UBUNTU:~$ ```
pgrep -l mbd
990 smbd
1004 smbd
1502 nmbd
```
The servers are up and running correctly> 


jeff@JEFF-UBUNTU:~$ ```
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21a:a0ff:fec2:ac7f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.171 bcast=192.168.255.255 netmask=255.255.0.0
Enter jeff's password: 

name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure [COLOR="#FF0000"]<--User (or annon) can't be authenticated[/COLOR]


name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )

name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure [COLOR="#FF0000"]<--Again the user (or annon) can't be authenticated[/COLOR]
WORKGROUP

name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.171 ( 192.168.1.171 )
Connecting to host=192.168.1.171
Connecting to 192.168.1.171 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure  [COLOR="#FF0000"]<--Again the user (or annon) can't be authenticated but the server is displayed[/COLOR]
	\\JEFF-UBUNTU    		Samba 3.6.18
Connecting to host=JEFF-UBUNTU

resolve_wins: Attempting wins lookup for name JEFF-UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed. [COLOR="#FF0000"]<-- Why this?  It isn't needed.[/COLOR]

resolve_hosts: Attempting host lookup for name JEFF-UBUNTU<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure   [COLOR="#FF0000"]<--Same user (or annon) failure[/COLOR]
		\\JEFF-UBUNTU\NewShare       	
		\\JEFF-UBUNTU\APPLE-MOVIES   	
		\\JEFF-UBUNTU\test           	For testing only, please
		\\JEFF-UBUNTU\IPC$           	IPC Service (Samba 3.6.18)[COLOR="#FF0000"]This is an earlier version of Samba3 than the Ubuntu package --???[/COLOR] 
```

See my comments in [COLOR="#FF0000"]red[/COLOR] above.
> 

jeff@JEFF-UBUNTU:~$ cat /etc/samba/smb.conf
[global]
	workgroup = WORKGROUP
[test]
	comment = For testing only, please
	path = /home/jeff/APPLE-MOVIES
	read only = no
	guest ok = yes
Hmmm, I think this is incomplete so I can't comment on any settings.  It doesn't coincide with the smbtree output.

The main problem is the user or anonymous (user nobody) can't be authenticated.  This means no useful data will be displayed.

[COLOR="#0000FF"]Edit:  I see your comment, but no update. :-([/COLOR]

---

