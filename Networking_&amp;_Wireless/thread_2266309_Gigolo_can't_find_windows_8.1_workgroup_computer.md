---
title: "Gigolo can't find windows 8.1 workgroup computer"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by jason170 on 2015-02-21
hello,
I am running xubuntu 14.10 on a macbook 2.1.  I have set up my windows 8.1 and my xubuntu on the same workgroup.  I can access my xubuntu smb workgroup shares (made in system-config-samba) on my windows 8.1 computer.  I can access my windows 8.1 and my xubuntu shares on my android phone through es file explorer.

I can trying with gigolo to access my windows share.  I do not use static IP so I want to connect using the computer name.  The computer does not show up under the network side panel, and I cannot connect to it using the connect dialog.  I can connect using the IP, but not while using the computer name.  It does not display any shares and posts an authentication failure when I manually type in the share.

I have read alot of tutorials but cannot find the answer to this.  Please help.

---

### Post by jason170 on 2015-02-22
I have tried the diagnostic:

```
GVFS_SMB_DEBUG=60 /usr/lib/gvfs/gvfsd -r
```

and in a seperate terminal running:

```
gvfs-mount smb://server/share
```

The code I received in the first window is:

```

jason@Snowy:~$ GVFS_SMB_DEBUG=60 /usr/lib/gvfs/gvfsd -r
### SMB: g_vfs_backend_smb_init: default workgroup = 'NULL'
INFO: Current debug levels:
  all: 60
  tdb: 60
  printdrivers: 60
  lanman: 60
  smb: 60
  rpc_parse: 60
  rpc_srv: 60
  rpc_cli: 60
  passdb: 60
  sam: 60
  auth: 60
  winbind: 60
  vfs: 60
  idmap: 60
  quota: 60
  acls: 60
  locking: 60
  msdfs: 60
  dmapi: 60
  registry: 60
  scavenger: 60
  dns: 60
  ldb: 60
Using netbios name SNOWY.
Using workgroup BEARFAMILY.
### SMB: do_mount - URI = smb://lightning/my%20music
### SMB: do_mount - try #0 
smbc_stat(smb://lightning/my%20music)
### SMB: auth_callback - anonymous pass
### SMB: auth_callback - out: last_user = 'jason', last_domain = 'BEARFAMILY'
SMBC_server: server_n=[lightning] server=[lightning]
 -> server_n=[lightning] server=[lightning]
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up lightning#20 (sitename (null))
no entry for lightning#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name lightning<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name lightning<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
samba_tevent: Schedule immediate event "tevent_req_trigger": 0x7f71600085d0
resolve_hosts: Attempting host lookup for name lightning<0x20>
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 2 addresses for lightning#20: 198.105.254.17,198.105.244.117
Adding cache entry with key=[NBT/LIGHTNING#20] and timeout=[Sun Feb 22 06:40:26 PM 2015 CST] (660 seconds ahead)
internal_resolve_name: returning 2 addresses: 198.105.254.17:0 198.105.244.117:0 
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000b1e0
Connecting to 198.105.254.17 at port 445
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160009870
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000b8c0
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000bbe0
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600076f0
samba_tevent: Running timer event 0x7f716000b8c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000c590
Connecting to 198.105.254.17 at port 139
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000cba0
samba_tevent: Ending timer event 0x7f716000b8c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160009870 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000b780
samba_tevent: Ending timer event 0x7f7160009870 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000bbe0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000d420
Connecting to 198.105.244.117 at port 445
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000da30
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000dd80
samba_tevent: Ending timer event 0x7f716000bbe0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000dd80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000e6c0
Connecting to 198.105.244.117 at port 139
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000bbc0
samba_tevent: Ending timer event 0x7f716000dd80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000cba0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000dc40
samba_tevent: Ending timer event 0x7f716000cba0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000da30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000edb0
samba_tevent: Ending timer event 0x7f716000da30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000b780 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000f0a0
samba_tevent: Ending timer event 0x7f716000b780 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000bbc0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000f390
samba_tevent: Ending timer event 0x7f716000bbc0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000dc40 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000f610
samba_tevent: Ending timer event 0x7f716000dc40 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000edb0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000f900
samba_tevent: Ending timer event 0x7f716000edb0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000f390 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000fbf0
samba_tevent: Ending timer event 0x7f716000f390 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000f0a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716000fee0
samba_tevent: Ending timer event 0x7f716000f0a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000f610 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600101d0
samba_tevent: Ending timer event 0x7f716000f610 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000f900 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600104c0
samba_tevent: Ending timer event 0x7f716000f900 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000fbf0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600107b0
samba_tevent: Ending timer event 0x7f716000fbf0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000fee0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160010aa0
samba_tevent: Ending timer event 0x7f716000fee0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600101d0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160010d90
samba_tevent: Ending timer event 0x7f71600101d0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600104c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011080
samba_tevent: Ending timer event 0x7f71600104c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600107b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011370
samba_tevent: Ending timer event 0x7f71600107b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160010aa0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011660
samba_tevent: Ending timer event 0x7f7160010aa0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160010d90 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011950
samba_tevent: Ending timer event 0x7f7160010d90 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011080 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011c40
samba_tevent: Ending timer event 0x7f7160011080 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011370 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160011f30
samba_tevent: Ending timer event 0x7f7160011370 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011660 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160012220
samba_tevent: Ending timer event 0x7f7160011660 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011950 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160012510
samba_tevent: Ending timer event 0x7f7160011950 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011c40 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160012800
samba_tevent: Ending timer event 0x7f7160011c40 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160011f30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160012af0
samba_tevent: Ending timer event 0x7f7160011f30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160012220 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160012de0
samba_tevent: Ending timer event 0x7f7160012220 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160012510 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600130d0
samba_tevent: Ending timer event 0x7f7160012510 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160012800 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600133c0
samba_tevent: Ending timer event 0x7f7160012800 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160012af0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600136b0
samba_tevent: Ending timer event 0x7f7160012af0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160012de0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600139a0
samba_tevent: Ending timer event 0x7f7160012de0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600130d0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160013c90
samba_tevent: Ending timer event 0x7f71600130d0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600133c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160013f80
samba_tevent: Ending timer event 0x7f71600133c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600136b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160014270
samba_tevent: Ending timer event 0x7f71600136b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600139a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160014560
samba_tevent: Ending timer event 0x7f71600139a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160013c90 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160014850
samba_tevent: Ending timer event 0x7f7160013c90 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160013f80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160014b40
samba_tevent: Ending timer event 0x7f7160013f80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160014270 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160014e30
samba_tevent: Ending timer event 0x7f7160014270 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160014560 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160015120
samba_tevent: Ending timer event 0x7f7160014560 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160014850 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160015410
samba_tevent: Ending timer event 0x7f7160014850 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160014b40 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160015700
samba_tevent: Ending timer event 0x7f7160014b40 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160014e30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600159f0
samba_tevent: Ending timer event 0x7f7160014e30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160015120 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160015ce0
samba_tevent: Ending timer event 0x7f7160015120 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160015410 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160015fd0
samba_tevent: Ending timer event 0x7f7160015410 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160015700 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600162c0
samba_tevent: Ending timer event 0x7f7160015700 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600159f0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600165b0
samba_tevent: Ending timer event 0x7f71600159f0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160015ce0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600168a0
samba_tevent: Ending timer event 0x7f7160015ce0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160015fd0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160016b90
samba_tevent: Ending timer event 0x7f7160015fd0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600162c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160016e80
samba_tevent: Ending timer event 0x7f71600162c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600165b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160017170
samba_tevent: Ending timer event 0x7f71600165b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600168a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160017460
samba_tevent: Ending timer event 0x7f71600168a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160016b90 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160017750
samba_tevent: Ending timer event 0x7f7160016b90 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160016e80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160017a40
samba_tevent: Ending timer event 0x7f7160016e80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160017170 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160017d30
samba_tevent: Ending timer event 0x7f7160017170 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160017460 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160018020
samba_tevent: Ending timer event 0x7f7160017460 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160017750 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160018310
samba_tevent: Ending timer event 0x7f7160017750 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160017a40 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160018600
samba_tevent: Ending timer event 0x7f7160017a40 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160017d30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600188f0
samba_tevent: Ending timer event 0x7f7160017d30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160018020 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160018be0
samba_tevent: Ending timer event 0x7f7160018020 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160018310 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160018ed0
samba_tevent: Ending timer event 0x7f7160018310 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160018600 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600191c0
samba_tevent: Ending timer event 0x7f7160018600 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600188f0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600194b0
samba_tevent: Ending timer event 0x7f71600188f0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160018be0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f71600197a0
samba_tevent: Ending timer event 0x7f7160018be0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160018ed0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160019a90
samba_tevent: Ending timer event 0x7f7160018ed0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600191c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160019d80
samba_tevent: Ending timer event 0x7f71600191c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600194b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001a070
samba_tevent: Ending timer event 0x7f71600194b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f71600197a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001a360
samba_tevent: Ending timer event 0x7f71600197a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160019a90 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001a650
samba_tevent: Ending timer event 0x7f7160019a90 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f7160019d80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001a940
samba_tevent: Ending timer event 0x7f7160019d80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001a070 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001ac30
samba_tevent: Ending timer event 0x7f716001a070 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001a360 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001af20
samba_tevent: Ending timer event 0x7f716001a360 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001a650 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001b210
samba_tevent: Ending timer event 0x7f716001a650 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001a940 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001b500
samba_tevent: Ending timer event 0x7f716001a940 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001ac30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001b7f0
samba_tevent: Ending timer event 0x7f716001ac30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001af20 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001bae0
samba_tevent: Ending timer event 0x7f716001af20 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001b210 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001bdd0
samba_tevent: Ending timer event 0x7f716001b210 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001b500 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001c0c0
samba_tevent: Ending timer event 0x7f716001b500 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001b7f0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001c3b0
samba_tevent: Ending timer event 0x7f716001b7f0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001bae0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001c6a0
samba_tevent: Ending timer event 0x7f716001bae0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001bdd0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001c990
samba_tevent: Ending timer event 0x7f716001bdd0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001c0c0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001cc80
samba_tevent: Ending timer event 0x7f716001c0c0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001c3b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001cf70
samba_tevent: Ending timer event 0x7f716001c3b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001c6a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001d260
samba_tevent: Ending timer event 0x7f716001c6a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001c990 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001d550
samba_tevent: Ending timer event 0x7f716001c990 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001cc80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001d840
samba_tevent: Ending timer event 0x7f716001cc80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001cf70 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001db30
samba_tevent: Ending timer event 0x7f716001cf70 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001d260 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001de20
samba_tevent: Ending timer event 0x7f716001d260 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001d550 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001e110
samba_tevent: Ending timer event 0x7f716001d550 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001d840 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001e400
samba_tevent: Ending timer event 0x7f716001d840 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001db30 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001e6f0
samba_tevent: Ending timer event 0x7f716001db30 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001de20 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001e9e0
samba_tevent: Ending timer event 0x7f716001de20 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001e110 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001ecd0
samba_tevent: Ending timer event 0x7f716001e110 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001e400 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001efc0
samba_tevent: Ending timer event 0x7f716001e400 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001e6f0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001f2b0
samba_tevent: Ending timer event 0x7f716001e6f0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001e9e0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001f5a0
samba_tevent: Ending timer event 0x7f716001e9e0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001ecd0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001f890
samba_tevent: Ending timer event 0x7f716001ecd0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001efc0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001fb80
samba_tevent: Ending timer event 0x7f716001efc0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001f2b0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f716001fe70
samba_tevent: Ending timer event 0x7f716001f2b0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001f5a0 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160020160
samba_tevent: Ending timer event 0x7f716001f5a0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001f890 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160020450
samba_tevent: Ending timer event 0x7f716001f890 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001fb80 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160020740
samba_tevent: Ending timer event 0x7f716001fb80 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716001fe70 "tevent_req_timedout"
samba_tevent: Added timed event "tevent_req_timedout": 0x7f7160020a30
samba_tevent: Ending timer event 0x7f716001fe70 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000b1e0 "tevent_req_timedout"
samba_tevent: Destroying timer event 0x7f7160020160 "tevent_req_timedout"
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f716000b5b0] mpx_fde[(nil)] fd[10] - disabling
samba_tevent: Ending timer event 0x7f716000b1e0 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000c590 "tevent_req_timedout"
samba_tevent: Destroying timer event 0x7f7160020450 "tevent_req_timedout"
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f716000cab0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: Ending timer event 0x7f716000c590 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000d420 "tevent_req_timedout"
samba_tevent: Destroying timer event 0x7f7160020740 "tevent_req_timedout"
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f716000d940] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: Ending timer event 0x7f716000d420 "tevent_req_timedout"
samba_tevent: Running timer event 0x7f716000e6c0 "tevent_req_timedout"
samba_tevent: Destroying timer event 0x7f7160020a30 "tevent_req_timedout"
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f716000ea90] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: Destroying timer event 0x7f71600076f0 "tevent_req_timedout"
samba_tevent: Ending timer event 0x7f716000e6c0 "tevent_req_timedout"
map_errno_from_nt_status: 32 bit codes: code=c00000b5
### SMB: do_mount - [smb://lightning/my%20music; 0] res = -1, cancelled = 0, errno = [110] 'Connection timed out' 
### SMB: do_mount - (errno != EPERM && errno != EACCES), cancelled = 0, breaking

** (gvfsd:5960): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to mount Windows share: Connection timed out


```


Any help is appreciated.  I am a linux newb.

---

### Post by bab1 on 2015-02-23
This doesn't look good to me (it's part of your last post)```
[COLOR="#FF0000"]remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 2 addresses for lightning#20: 198.105.254.17,198.105.244.117[/COLOR]
```..duplicates are always troubling,

Your original debug is really set to -d4 which is really more than you need to diagnose your problem.  It create unneeded error lines that tend to obscure the real problem. 

It's easier to just issue the command at the terminal and turn on the debug in one line.  Post the output of this terminal command ```
smbclient -d3 -L <server_name>
```...where <server_name> is the name of the server you were looking for.  This will output the similar debug info.

Another command you can use will scan the entire SMB network for data is```
smbtree -d3
```

---

### Post by jason170 on 2015-02-23
Trying
```
smbtree -d3
```

I got:

```
jason@Snowy:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:e951:26d6:d40:ce3b bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.119 bcast=192.168.1.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name BEARFAMILY<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcac50] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name BEARFAMILY<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcaa60] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.119 ( 192.168.1.119 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcac50] mpx_fde[(nil)] fd[7] - disabling
```


Trying:
```
smbclient -d3 -L <server_name>
```

I got:
```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:e951:26d6:d40:ce3b bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.119 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name Lightning<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name Lightning<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name Lightning<0x20>
Connecting to 198.105.254.17 at port 445
Connecting to 198.105.254.17 at port 139
Connecting to 198.105.244.117 at port 445
Connecting to 198.105.244.117 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370d290] mpx_fde[(nil)] fd[6] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370e410] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370ef90] mpx_fde[(nil)] fd[8] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370fa20] mpx_fde[(nil)] fd[9] - disabling
Connection to Lightning failed (Error NT_STATUS_IO_TIMEOUT)


```

---

### Post by bab1 on 2015-02-23
> **jason170 said:**
> Trying
```
smbtree -d3
```

I got:

```
jason@Snowy:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:e951:26d6:d40:ce3b bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.119 bcast=192.168.1.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name BEARFAMILY<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcac50] mpx_fde[(nil)] fd[7] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name BEARFAMILY<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name BEARFAMILY<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcaa60] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.119 ( 192.168.1.119 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f59cadcac50] mpx_fde[(nil)] fd[7] - disabling
```


Trying:
```
smbclient -d3 -L <server_name>
```

I got:
```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:e951:26d6:d40:ce3b bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.119 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name Lightning<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name Lightning<0x20>

[COLOR="#800080"]resolve_wins: WINS server resolution selected and **no WINS servers listed.**[/COLOR]

[COLOR="#FF0000"]resolve_hosts: Attempting host lookup for name Lightning<0x20>
Connecting to 198.105.254.17 at port 445
Connecting to 198.105.254.17 at port 139
Connecting to 198.105.244.117 at port 445
Connecting to 198.105.244.117 at port 139[/COLOR]

[COLOR="#008000"][B]samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370d290] mpx_fde[(nil)] fd[6] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370e410] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370ef90] mpx_fde[(nil)] fd[8] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f4c7370fa20] mpx_fde[(nil)] fd[9] - disabling[/B][/COLOR]

[COLOR="#0000FF"]**Connection to Lightning failed (Error NT_STATUS_IO_TIMEOUT)**[/COLOR]


```

As WINS is incorrectly confingured (purple) this is most likely causing Samba to look to a non-existing Samba host (red) which in turn is causing the response (green) resulting in the system to hang (shown in blue).

In short, samba, is mis-configured,  causes samba to be directed to an internet site 198.105.254.17.  Samba is LAN based only.  No Internet connections allowed.  The IP address 198.105.254.17 resolves to  Search Guide Inc.  Is this your ISP?

Post the output of this so we can see the configuration```
cat /etc/samba/smb.conf
```...do you have a untouched copy of smb.conf?

Might as well post this too```
testparam -s
```

It is entirely possible that there is more than one problem, but this is a good start at fixing your network problems.

---

### Post by jason170 on 2015-02-23
Search Guide inc is not my ISP.  Suddenlink is my ISP.

```
cat /etc/samba/smb.conf
```
results in:
```
jason@Snowy:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = bearfamily

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
    log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
    max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
    syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
    panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
    server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

    obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
    unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
    pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
    map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

;    wins support = no
    security = user
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody
    username map = /etc/samba/smbusers
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody
[printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin




[Music]
    path = /home/jason/Music
    writeable = yes
;    browseable = yes
    valid users = jason

[Documents]
    path = /home/jason/Documents
    writeable = yes
;    browseable = yes
    valid users = jason
jason@Snowy:~$ 


```

for:
```
testparam -s
```
I got an error so I tried

```
testparm -s
```


I get:

```

jason@Snowy:~$ testparam -s
No command 'testparam' found, did you mean:
 Command 'testparm' from package 'samba-common-bin' (main)
testparam: command not found
jason@Snowy:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = BEARFAMILY
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Music]
    path = /home/jason/Music
    valid users = jason
    read only = No

[Documents]
    path = /home/jason/Documents
    valid users = jason
    read only = No
jason@Snowy:~$ 


```

Thank you for your help.

---

### Post by bab1 on 2015-02-23
Hmmmm, not what I expected to see.

Sorry for the typo.  :-(

What do you have returned from this command```
testparm -sv|grep "name res"
```

---

### Post by jason170 on 2015-02-23
No problem.  At least the correct one was suggested.


```
jason@Snowy:~$ testparm -sv|grep "name res"
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
    name resolve order = lmhosts, wins, host, bcast
jason@Snowy:~$ 
 
```

---

### Post by bab1 on 2015-02-23
> **jason170 said:**
> No problem.  At least the correct one was suggested.


```
jason@Snowy:~$ testparm -sv|grep "name res"
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
    name resolve order = lmhosts, wins, host, bcast
jason@Snowy:~$ 
 
```

I would add this line to the [global] section of the smb.conf file```
name resolve order = host, bcast
```

You won't see the line you are replacing.  The default doesn't have to be declared.

Once that is done you can restart the smbd daemon with this command```

sudo service smbd restart
```

The try the smbclient command again```
smbclient -d3 -L Lightning
```

Post what is returned again.

---

### Post by jason170 on 2015-02-23
This is what I get.

```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:4870:5d0d:83dd:f6d3 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.118 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_hosts: Attempting host lookup for name Lightning<0x20>
Connecting to 198.105.254.17 at port 445
Connecting to 198.105.254.17 at port 139
Connecting to 198.105.244.117 at port 445
Connecting to 198.105.244.117 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b1190] mpx_fde[(nil)] fd[6] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b2310] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b2e90] mpx_fde[(nil)] fd[8] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b3920] mpx_fde[(nil)] fd[9] - disabling
Connection to Lightning failed (Error NT_STATUS_IO_TIMEOUT)
jason@Snowy:~$ 

thanks



```

---

### Post by bab1 on 2015-02-23
> **jason170 said:**
> This is what I get.

```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:4870:5d0d:83dd:f6d3 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.118 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_hosts: Attempting host lookup for name Lightning<0x20>
Connecting to 198.105.254.17 at port 445
Connecting to 198.105.254.17 at port 139
Connecting to 198.105.244.117 at port 445
Connecting to 198.105.244.117 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b1190] mpx_fde[(nil)] fd[6] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b2310] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b2e90] mpx_fde[(nil)] fd[8] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f44994b3920] mpx_fde[(nil)] fd[9] - disabling
Connection to Lightning failed (Error NT_STATUS_IO_TIMEOUT)
jason@Snowy:~$ 

thanks



```

We are getting closer!  Edit the smb.conf file and remove the *host * parameter from the line we just put in.  It should look like this now```

 name resolve order = bcast
```

Restart the smbd daemon and try it again.

---

### Post by jason170 on 2015-02-24
This is what I get:
```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:8862:da68:59d5:725e bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.118 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name Lightning<0x20>
Got a positive name query response from 192.168.1.116 ( 192.168.1.116 )
Connecting to 192.168.1.116 at port 445
Connecting to 192.168.1.116 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fd09dce9480] mpx_fde[(nil)] fd[8] - disabling
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
jason@Snowy:~$ 


```

Thanks for all your help

---

### Post by bab1 on 2015-02-24
> **jason170 said:**
> This is what I get:
```
jason@Snowy:~$ smbclient -d3 -L Lightning
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fd9b:cc70:b02:0:21e:52ff:fe76:3f7 bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fd9b:cc70:b02:0:8862:da68:59d5:725e bcast= netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.118 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 4.1.11-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name Lightning<0x20>
Got a positive name query response from 192.168.1.116 ( 192.168.1.116 )
Connecting to 192.168.1.116 at port 445
Connecting to 192.168.1.116 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fd09dce9480] mpx_fde[(nil)] fd[8] - disabling
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
jason@Snowy:~$ 


```

Thanks for all your help

The only error now is a share logon failure. Is the user jason configured to be able to use the share?

As you can see Samba finds the SMB server Lightning ```
name_resolve_bcast: Attempting broadcast lookup for name Lightning<0x20>
Got a positive name query response from 192.168.1.116 ( 192.168.1.116 )
Connecting to 192.168.1.116 at port 445
Connecting to 192.168.1.116 at port 139
```...but can't authenticate the user```

samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fd09dce9480] mpx_fde[(nil)] fd[8] - disabling
...
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```
I don't know what is needed to configure SMB share users on a Windows machine.  I only have one old Windows Vista machine and the users on that machine use the same name as the users on my Linux machines.

Try making a share open to everyone.

---

### Post by jason170 on 2015-02-26
Hello,
You are right that:
```
smbclient -d3 -L Lightning
```

Is giving me an authentication error.  My logon name and PW is different on my windows computer.

When I use the follow code it logs on correctly:

```
smbclient \\\\server\\share -U username -W domain mypassword
```

Thank you for all your help.  I appreciate it.

---

