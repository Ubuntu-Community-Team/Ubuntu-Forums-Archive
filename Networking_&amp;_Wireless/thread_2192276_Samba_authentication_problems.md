---
title: "Samba authentication problems"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by baburdock on 2013-12-07
Hello,

I'm running into Samba authentication problems and googling didn't help so far. Ubunty is Saucy, Samba is 3.6.18 and is configured to run as a stanalone server with security=user. There is no domain.

My problems occur locally, with smbclient on the server machine. Other Windows clients are not even involved  yet. The basic issue is that smbclient doesn't seem to recognize any user names.

Basically this is what happens:

```
tank@Vault:~$ smbclient '\\vault\v_Misc' -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::76d0:2bff:fe90:ca20%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.55 bcast=192.168.2.255 netmask=255.255.255.0
Client started (version 3.6.18).
Enter tank's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name vault<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name vault<0x20>
resolve_wins: Attempting wins lookup for name vault<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name vault<0x20>
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
Anonymous login successful
Domain=[HOUSE] OS=[Unix] Server=[Samba 3.6.18]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```

Here's what is shared (smbtree works fine as well):

```
tank@Vault:~$ smbclient -L localhost
Enter tank's password: 
Anonymous login successful
Domain=[HOUSE] OS=[Unix] Server=[Samba 3.6.18]

    Sharename       Type      Comment
    ---------       ----      -------
    v_Photo         Disk      Comment: /v/Photo
    v_Audio         Disk      Comment: /v/Audio
    v_Video         Disk      Comment: /v/Video
    v_Misc          Disk      Comment: /v/Misc
    IPC$            IPC       IPC Service (Vault)
Anonymous login successful
Domain=[HOUSE] OS=[Unix] Server=[Samba 3.6.18]

    Server               Comment
    ---------            -------
    DUNE                 Dune SMB server
    VAULT                Vault

    Workgroup            Master
    ---------            -------
    HOUSE                DUNE
```

Note that the v_* shares are usershares (they are zfs datasets auto shared by zfs at boot). The usershares look like this:

```
#VERSION 2
path=/v/Misc
comment=Comment: /v/Misc
usershare_acl=S-1-1-0:F
guest_ok=n
sharename=v_Misc
```

I'm using tdbsam as my Samba backend. It has several users:

```
keeper@Vault:~$ sudo pdbedit -L
carrot:1004:
keeper:1002:
tank:1003:
kiwi:1005:
hobo:1006:
```

And finally, here is my smb.conf:
```

#------------------------------------------------------------
[global]

workgroup = HOUSE
server string = Vault

# We will accept connection only from our LAN (and localhost)
hosts deny = all
hosts allow = 192.168.2.0/24 127.

dns proxy = no

# Log file
log file = /var/log/samba/log.%m
max log size = 1024
syslog = 0

# Authentication
security = user
encrypt passwords = true
passdb backend = tdbsam

map to guest = bad user
username map = /etc/samba/username.map

# Transient connection are read-only
read list = hobo

# Linux LAN options
socket options = SO_RCVBUF=8192
socket options = SO_SNDBUF=8192
socket options = IPTOS_LOWDELAY
socket options = TCP_NODELAY

# Usershares
usershare path = /var/lib/samba/usershares
usershare prefix allow list = /v
usershare owner only = False
usershare max shares = 128
usershare allow guests = yes

#------------------------------------------------------------

# We are not sharing home directories
; [homes]

# There are no printers connected to this machine
; [printers]

#------------------------------------------------------------

```

I would much appreciate help with this, it's an annoying problem.

---

