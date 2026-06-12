---
title: "Can't connect to Samba: Error NT_STATUS_BAD_NETWORK_NAME/ERRinvnetname"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by W. Irving on 2014-02-11
Trying to set up Samba 3.4.7 on Lucid server edition.
Gone so far I'm using the minimal smb.conf from [https://www.samba.org/samba/docs/using_samba/ch12.html:](https://www.samba.org/samba/docs/using_samba/ch12.html:)

```
[global]
    workgroup = EXAMPLE
    security = user
    browsable = yes
    local master = yes
[homes]
    guest ok = no
    browsable = no
[temp]
    path = /tmp
    public = yes
```

But I can't connect to Samba even on localhost, and I can't figure out why. Not sure exactly how Samba works, but apparently it's trying to make a hostname lookup to the client (i.e. itself), which fails because it's doing the lookup on an empty host name!
Sometimes smbclient returns Error NT_STATUS_BAD_NETWORK_NAME, sometimes ERRinvnetname, as below.
mungo has IP 192.168.1.253.
Apparently 192.168.1.154 is responding to this empty host name query. This is a network printer!

```
wirving@mungo:~$ smbclient -d10 ////mungo
INFO: Current debug levels:
  all: True/10
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
  registry: False/0
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = EXAMPLE
doing parameter security = user
doing parameter browsable = yes
doing parameter local master = yes
pm_process() returned Yes
lp_servicenumber: couldn't find homes
set_server_role: role = ROLE_STANDALONE
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8
Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface eth0 ip=fe80::227:eff:fe02:9ac%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.253 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="MUNGO"
Client started (version 3.4.7).
Enter wirving's password:
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found
sitename_fetch: No stored sitename for
internal_resolve_name: looking up #20 (sitename (null))
Returning expired cache entry: key = NBT/#20, value = 192.168.1.154:0, timeout = Sun Feb  9 20:35:25 2014
no entry for #20 found.
resolve_lmhosts: Attempting lmhosts lookup for name <0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name <0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name <0x20>
resolve_hosts: getaddrinfo failed for name  [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name <0x20>
bind succeeded on port 0
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 1
        SO_BROADCAST = 1
        Could not test socket option TCP_NODELAY.
        Could not test socket option TCP_KEEPCNT.
        Could not test socket option TCP_KEEPIDLE.
        Could not test socket option TCP_KEEPINTVL.
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_SNDBUF = 112640
        SO_RCVBUF = 112640
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
Sending a packet of len 50 to (192.168.1.255) on port 137
read_udp_v4_socket: ip 192.168.1.154 port 35072 read: 62
parse_nmb: packet id = 25217
Received a packet of len 62 from (192.168.1.154) port 137
nmb packet from 192.168.1.154(137) header: id=25217 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name= <20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char ......   hex 0000C0A8019A
Got a positive name query response from 192.168.1.154 ( 192.168.1.154 )
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for #20: 192.168.1.154
Adding cache entry with key = NBT/#20; value = 192.168.1.154:0 and timeout = Tue Feb 11 22:10:00 2014
 (660 seconds ahead)
internal_resolve_name: returning 1 addresses: 192.168.1.154:0
s3_event: Added timed event "tevent_req_timedout": 0x21a862b8
s3_event: Added timed event "tevent_req_timedout": 0x21a86a78
Running timed event "tevent_req_timedout" 0x21a862b8
s3_event: Destroying timer event 0x21a862b8 "tevent_req_timedout"
s3_event: Added timed event "tevent_req_timedout": 0x21a862b8
Connecting to 192.168.1.154 at port 445
s3_event: Added timed event "tevent_req_timedout": 0x21a87150
connect returned Connection refused
s3_event: Destroying timer event 0x21a87150 "tevent_req_timedout"
s3_event: Destroying timer event 0x21a862b8 "tevent_req_timedout"
Running timed event "tevent_req_timedout" 0x21a86a78
s3_event: Destroying timer event 0x21a86a78 "tevent_req_timedout"
s3_event: Added timed event "tevent_req_timedout": 0x21a86e80
Connecting to 192.168.1.154 at port 139
s3_event: Added timed event "tevent_req_timedout": 0x21a87760
s3_event: Destroying timer event 0x21a87760 "tevent_req_timedout"
s3_event: Destroying timer event 0x21a86e80 "tevent_req_timedout"
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
        SO_SNDBUF = 16384
        SO_RCVBUF = 87380
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
write_socket(5,72)
write_socket(5,72) wrote 72
Sent session request
got smb length of 0
size=0
smb_com=0x0
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=0
smb_flg2=0
smb_tid=0
smb_pid=0
smb_uid=0
smb_mid=0
smt_wct=0
smb_bcc=0
 session request ok
cli_chain_cork: mid=2
handle_incoming_pdu: got mid 2
write_socket(5,164)
write_socket(5,164) wrote 164
got smb length of 86
size=86
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=128
smb_flg2=32768
smb_tid=0
smb_pid=6116
smb_uid=100
smb_mid=3
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=45
[0000] 00 43 00 41 00 4E 00 4F   00 4E 00 00 00 43 00 41   .C.A.N.O .N...C.A
[0010] 00 4E 00 4F 00 4E 00 00   00 57 00 4F 00 52 00 4B   .N.O.N.. .W.O.R.K
[0020] 00 47 00 52 00 4F 00 55   00 50 00 00 00           .G.R.O.U .P...
cli_init_creds: user wirving domain EXAMPLE
Domain=[WORKGROUP] OS=[CANON] Server=[CANON]
 session setup ok
cli_chain_cork: mid=4
handle_incoming_pdu: got mid 4
lang_tdb_init: /usr/share/samba/sv_SE.UTF-8.msg: No such file or directory
tree connect failed: ERRinvnetname
```

Can anyone please shed some light on this lunacy? I've been trying for three days to get it working.

nmblookup doesn't seem to have any trouble..
```
wirving@mungo:~$ nmblookup mungo
querying mungo on 192.168.1.255
192.168.1.253 mungo<00>
```

---

