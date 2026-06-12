---
title: "samba update?"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by harumba on 2008-07-31
Hi, I have a samba problem :(

After installing some updates including  samba-common smbclient and  smbfs 3.0.24-2ubuntu1.7 I suddenly lost the ability to mount a remote directory through samba. I'm running 7.04 Feisty. The server is running Red Hat 3.3.3-7 and samba version 3.0.10-1.fc2. and I don't have admin privileges there.

When trying to mount manually with ```
mount /mnt/MNTPOINT
``` I get:

```
xxxx: protocol negotiation failed
SMB connection failed
```


I don't really know anything about samba, after some googling I also tried:

```
smbclient  //REMOTEHOST/DIR -d10
```

This is the output:
```

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
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = MSHOME
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter invalid users = root
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter socket options = TCP_NODELAY
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
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface ip=xxxxxxxx bcast=129.215.50.255 nmask=255.255.255.0
added interface ip=xxxxxxxx bcast=169.254.255.255 nmask=255.255.0.0
Netbios name list:-
my_netbios_names[0]="xxxxxxx"
Client started (version 3.0.24).
internal_resolve_name: looking up xxxxxxxx#20
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Cache entry with key = NBT/xxxxxxxx#20 couldn't be found
no entry for xxxxxxxxx#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name xxxxxxx<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name xxxxxxxx<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name xxxxxxxxx<0x20>
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for xxxxxxx#20: xxxxxxxxxxx:0
internal_resolve_name: returning 1 addresses: xxxxxxxxxx:0 
Connecting to xxxxxxxxxxxx at port 445
socket option SO_KEEPALIVE = 0
socket option SO_REUSEADDR = 0
socket option SO_BROADCAST = 0
socket option TCP_NODELAY = 1
socket option TCP_KEEPCNT = 9
socket option TCP_KEEPIDLE = 7200
socket option TCP_KEEPINTVL = 75
socket option IPTOS_LOWDELAY = 0
socket option IPTOS_THROUGHPUT = 0
socket option SO_SNDBUF = 16384
socket option SO_RCVBUF = 87380
socket option SO_SNDLOWAT = 1
socket option SO_RCVLOWAT = 1
socket option SO_SNDTIMEO = 0
socket option SO_RCVTIMEO = 0
 session request ok
write_socket(5,183)
write_socket(5,183) wrote 183
read_socket_with_timeout: timeout read. EOF from client.
receive_smb_raw: length < 0!
client_receive_smb failed
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
lang_tdb_init: /usr/share/samba/en_GB.UTF-8.msg: No such file or directory
protocol negotiation failed

```

Any help/pointers would be appreciated. Or is there a way to undo the update?

Thanks

---

### Post by dmizer on 2008-07-31
Is the Red Hat server hosting an AD?

If so, then this is probably a bug.  If not, you should take a look at the second link in my sig.

---

### Post by harumba on 2008-07-31
Thank you for your reply and the link dmizer. I finally just heard from the server admin and it turns out the problem was on that side. It is now fixed and my mount works fine. My samba updates were probably just an unhappy coincidence!

---

### Post by dmizer on 2008-07-31
> **harumba said:**
> Thank you for your reply and the link dmizer. I finally just heard from the server admin and it turns out the problem was on that side. It is now fixed and my mount works fine. My samba updates were probably just an unhappy coincidence!

Ah! Well, as long as you're working. Glad that was more painful for your server admin than it was for you ;)

---

