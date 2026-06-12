---
title: "Shared Printing: Win7 as Server, Linux Mint as Client"
date: 2019-04-01
forum: Networking &amp; Wireless
---

### Post by kotee on 2019-04-01
Despite I have a somewhat sideways distro from Ubuntu, it seems that the problem is not restricted to even Ubuntus, so I will be glad to have any responses here...

There are two computers in my LAN: Windows 7 Ultimate workstation with physically connected printer and Mint 19 laptop. The workstation is Ethernet-connected to a router with an internet connection; the laptop is connected to the router through Wi-Fi. 

I could establish bi-directional file sharing between computers by trial-and-error with help of some google results (namely, I had created a shared folder on Win7 and had successfully accessed it from Linux; then vice-versa).

Then goes the problem. The printer is set up as SHARED on Win7 machine, I can see it from Linux, but cannot make it to print anything. As for now, I discovered the following:

```

$ smbclient -L 192.168.0.100
WARNING: The "null passwords" option is deprecated
Enter LOCAL\kotee's password: 

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      &#1059;&#1076;&#1072;&#1083;&#1077;&#1085;&#1085;&#1099;&#1081; Admin
    C$              Disk      &#1057;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1085;&#1099;&#1081; &#1086;&#1073;&#1097;&#1080;&#1081; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;
    D$              Disk      &#1057;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1085;&#1099;&#1081; &#1086;&#1073;&#1097;&#1080;&#1081; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;
    F$              Disk      &#1057;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1085;&#1099;&#1081; &#1086;&#1073;&#1097;&#1080;&#1081; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;
    H$              Disk      &#1057;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1085;&#1099;&#1081; &#1086;&#1073;&#1097;&#1080;&#1081; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;
    hp1516          Printer   hp1516
    IPC$            IPC       &#1059;&#1076;&#1072;&#1083;&#1077;&#1085;&#1085;&#1099;&#1081; IPC
    print$          Disk      &#1044;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;&#1099; &#1087;&#1088;&#1080;&#1085;&#1090;&#1077;&#1088;&#1086;&#1074;
    Public          Disk      
    Users           Disk      
SMB1 disabled -- no workgroup available

```

```

$ smbtree -d10
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
Processing section "[global]"
doing parameter browseable = yes
doing parameter workgroup = local
doing parameter null passwords = yes
WARNING: The "null passwords" option is deprecated
doing parameter wins support = true
doing parameter local master = no
doing parameter domain master = no
doing parameter preferred master = no
doing parameter client min protocol = SMB2
doing parameter ntlm auth = no
doing parameter lanman auth = yes
doing parameter client ntlmv2 auth = yes
doing parameter server string = SOSAMBA
doing parameter load printers = yes
doing parameter printing = cups
doing parameter printcap name = cups
doing parameter use client driver = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = Bad Password
doing parameter usershare allow guests = yes
doing parameter usershare owner only = no
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter guest ok = yes
doing parameter guest account = kotee
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface wlp4s0 ip=192.168.0.102 bcast=192.168.0.255 netmask=255.255.255.0
internal_resolve_name: looking up LOCAL#1d (sitename (null))
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
Adding cache entry with key=[NBT/LOCAL#1D] and timeout=[&#1063;&#1090; &#1103;&#1085;&#1074;  1 03:00:00 1970 MSK] (-1554142136 seconds in the past)
no entry for LOCAL#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name LOCAL<0x1d>
getlmhostsent: lmhost entry: 192.168.0.100 ANTON-PC 
getlmhostsent: lmhost entry: 192.168.0.102 FUKMASHINA 
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LOCAL<0x1d>
parse_nmb: packet id = 28872
nmb packet from 192.168.0.100(35072) header: id=28872 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=LOCAL<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....d   hex 0000C0A80064
Got a positive name query response from 192.168.0.100 ( 192.168.0.100 )
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for LOCAL#1d: 192.168.0.100
Adding cache entry with key=[NBT/LOCAL#1D] and timeout=[&#1055;&#1085; &#1072;&#1087;&#1088;  1 21:19:56 2019 MSK] (660 seconds ahead)
internal_resolve_name: returning 1 addresses: 192.168.0.100:0 
Connecting to 192.168.0.100 at port 445
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
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
name_status_find: looking up *#00 at 192.168.0.100
Adding cache entry with key=[NBT/*#00.00.192.168.0.100] and timeout=[&#1063;&#1090; &#1103;&#1085;&#1074;  1 03:00:00 1970 MSK] (-1554142136 seconds in the past)
namecache_status_fetch: no entry for NBT/*#00.00.192.168.0.100 found.
getlmhostsent: lmhost entry: 192.168.0.100 ANTON-PC 
getlmhostsent: lmhost entry: 192.168.0.102 FUKMASHINA 
parse_nmb: packet id = 6380
nmb packet from 192.168.0.100(35072) header: id=6380 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .ANTON-PC          hex 06414E544F4E2D504320202020202020
    answers  10 char ...LOCAL           hex 0004004C4F43414C2020202020202020
    answers  20 char   ...ANTON-PC      hex 2020008400414E544F4E2D5043202020
    answers  30 char      ..LOCAL       hex 202020202004004C4F43414C20202020
    answers  40 char       ...LOCAL     hex 2020202020201E84004C4F43414C2020
    answers  50 char         .....__M   hex 20202020202020201D040001025F5F4D
    answers  60 char SBROWSE__.......   hex 5342524F5753455F5F02018400001FD0
    answers  70 char U#}.............   hex 55237D00000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
ANTON-PC#00: flags = 0x04
LOCAL#00: flags = 0x84
ANTON-PC#20: flags = 0x04
LOCAL#1e: flags = 0x84
LOCAL#1d: flags = 0x04
__MSBROWSE__#01: flags = 0x84
Adding cache entry with key=[NBT/*#00.00.192.168.0.100] and timeout=[&#1055;&#1085; &#1072;&#1087;&#1088;  1 21:19:56 2019 MSK] (660 seconds ahead)
namecache_status_store: entry NBT/*#00.00.192.168.0.100 store failed.
name_status_find: name found, name ANTON-PC ip address is 192.168.0.100
Connecting to 192.168.0.100 at port 445
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
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0

```

/etc/samba/smb.conf
```

[global]
    browseable = yes
    workgroup = local
    null passwords = yes
    wins support = true
    local master = no
    domain master = no
    preferred master = no
    client min protocol = SMB2
    ntlm auth = no
    lanman auth = yes
    client ntlmv2 auth = yes
    server string = XXXXXXXXX
    load printers = yes
    printing = cups
    printcap name = cups
    use client driver = yes
    log file = /var/log/samba/log.%m
    max log size = 1000
    panic action = /usr/share/samba/panic-action %d
    server role = standalone server
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = Bad Password
    usershare allow guests = yes
    usershare owner only = no
    security = user
    encrypt passwords = yes
    guest ok = yes
    guest account = kotee
    
[printers]
    comment = All Printers
;    browseable = yes
    path = /tmp
    printable = yes
    guest ok = yes
;    read only = yes
    create mask = 0700
    use client driver = yes

[temp]
    browseable = yes
    writeable = yes
    path = /home/kotee/tmp
    force user = kotee
    force group = kotee
    guest ok = yes

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no

```

/etc/cups/printers.conf
```

<DefaultPrinter hp1516>
UUID urn:uuid:c6754b09-0da3-31a3-6e5e-62b142083801
AuthInfoRequired username,password
Info HP Deskjet 1510
MakeModel HP Deskjet 1510 Series hpijs, 3.17.10
DeviceURI smb://Guest@192.168.0.100/hp1516
State Idle
StateTime 1554135072
ConfigTime 1554124735
Type 8425484
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</DefaultPrinter>

```

/etc/cups/cupsd.conf is default

I use this command to make a test print through terminal:
```

$ echo -en "asdfg\n" | smbclient "\\\\192.168.0.100\\hp1516" -c "print -" -N -U "Guest" -W LOCAL -d10
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
Processing section "[global]"
doing parameter browseable = yes
doing parameter workgroup = local
doing parameter null passwords = yes
WARNING: The "null passwords" option is deprecated
doing parameter wins support = true
doing parameter local master = no
doing parameter domain master = no
doing parameter preferred master = no
doing parameter client min protocol = SMB2
doing parameter ntlm auth = no
doing parameter lanman auth = yes
doing parameter client ntlmv2 auth = yes
doing parameter server string = XXXXXXXX
doing parameter load printers = yes
doing parameter printing = cups
doing parameter printcap name = cups
doing parameter use client driver = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = Bad Password
doing parameter usershare allow guests = yes
doing parameter usershare owner only = no
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter guest ok = yes
doing parameter guest account = kotee
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface wlp4s0 ip=192.168.0.102 bcast=192.168.0.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="XXXXXXXX"
Client started (version 4.7.6-Ubuntu).
Connecting to 192.168.0.100 at port 445
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
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
 session request ok
 negotiated dialect[SMB2_10] against server[192.168.0.100]
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Starting GENSEC mechanism spnego
Starting GENSEC submechanism ntlmssp
     negotiate: struct NEGOTIATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmNegotiate (1)
        NegotiateFlags           : 0x62088215 (1644724757)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               1: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        DomainNameLen            : 0x0000 (0)
        DomainNameMaxLen         : 0x0000 (0)
        DomainName               : *
            DomainName               : ''
        WorkstationLen           : 0x0000 (0)
        WorkstationMaxLen        : 0x0000 (0)
        Workstation              : *
            Workstation              : ''
        Version: struct ntlmssp_VERSION
            ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
            ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
            ProductBuild             : 0x0000 (0)
            Reserved: ARRAY(3)
                [0]                      : 0x00 (0)
                [1]                      : 0x00 (0)
                [2]                      : 0x00 (0)
            NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - using NTLM1
SPNEGO login failed: The attempted logon is invalid. This is either due to a bad username or authentication information.
session setup failed: NT_STATUS_LOGON_FAILURE

```

Another command without specifying an username
```

$ echo -en "asdfg\n" | smbclient "\\\\192.168.0.100\\hp1516" -c "print -" -N -d10
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
  tevent: 10
  auth_audit: 10
  auth_json_audit: 10
  kerberos: 10
  drs_repl: 10
Processing section "[global]"
doing parameter browseable = yes
doing parameter workgroup = local
doing parameter null passwords = yes
WARNING: The "null passwords" option is deprecated
doing parameter wins support = true
doing parameter local master = no
doing parameter domain master = no
doing parameter preferred master = no
doing parameter client min protocol = SMB2
doing parameter ntlm auth = no
doing parameter lanman auth = yes
doing parameter client ntlmv2 auth = yes
doing parameter server string = XXXXXX
doing parameter load printers = yes
doing parameter printing = cups
doing parameter printcap name = cups
doing parameter use client driver = yes
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter server role = standalone server
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = Bad Password
doing parameter usershare allow guests = yes
doing parameter usershare owner only = no
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter guest ok = yes
doing parameter guest account = kotee
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface wlp4s0 ip=192.168.0.102 bcast=192.168.0.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="XXXXXXXXXX"
Client started (version 4.7.6-Ubuntu).
Connecting to 192.168.0.100 at port 445
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
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
 session request ok
 negotiated dialect[SMB2_10] against server[192.168.0.100]
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Starting GENSEC mechanism spnego
Starting GENSEC submechanism ntlmssp
     negotiate: struct NEGOTIATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmNegotiate (1)
        NegotiateFlags           : 0x62088215 (1644724757)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               1: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        DomainNameLen            : 0x0000 (0)
        DomainNameMaxLen         : 0x0000 (0)
        DomainName               : *
            DomainName               : ''
        WorkstationLen           : 0x0000 (0)
        WorkstationMaxLen        : 0x0000 (0)
        Workstation              : *
            Workstation              : ''
        Version: struct ntlmssp_VERSION
            ProductMajorVersion      : NTLMSSP_WINDOWS_MAJOR_VERSION_6 (6)
            ProductMinorVersion      : NTLMSSP_WINDOWS_MINOR_VERSION_1 (1)
            ProductBuild             : 0x0000 (0)
            Reserved: ARRAY(3)
                [0]                      : 0x00 (0)
                [1]                      : 0x00 (0)
                [2]                      : 0x00 (0)
            NTLMRevisionCurrent      : NTLMSSP_REVISION_W2K3 (15)
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_TARGET_TYPE_SERVER
  NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - using NTLM1
 session setup ok
 tconx ok
map_open_params_to_ntcreate: fname = stdin-7154, deny_mode = 0x42, open_func = 0x12
map_open_params_to_ntcreate: file stdin-7154, access_mask = 0x12019f, share_mode = 0x3, create_disposition = 0x5, create_options = 0x40 private_flags = 0x0
NT_STATUS_ACCESS_DENIED opening remote file stdin-7154

```

When I press the button `Print Test Page' in system-config-printer it asks for username and password and no known combination of these do not have any effect --- it continues asking all the time. As soon as I press Cancel then, my Test Page in printer queue is `Held for authentification' and in printer properties NT_STATUS_ACCESS_DENIED is displayed.

Logs:
/var/log/samba/log.smbd
```

... (only those lines)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
[2019/04/01 17:25:05.324671,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
[2019/04/01 18:03:11.886409,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections

```

/var/log/samba/log.nmbd
```

... (same lines)
[2019/04/01 18:03:14.227989,  0] ../source3/nmbd/nmbd.c:58(terminate)
  Got SIGTERM: going down...
[2019/04/01 18:03:14.309438,  0] ../source3/nmbd/asyncdns.c:158(start_async_dns)
  started asyncdns process 4299
[2019/04/01 18:03:14.315341,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections

```

/var/log/cups/error_log
```

E [01/Apr/2019:00:09:15 +0300] [Job 74] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:00:09:29 +0300] [Job 74] Session setup failed: NT_STATUS_LOGON_FAILURE
E [01/Apr/2019:00:09:29 +0300] [Job 74] Session setup failed: NT_STATUS_ACCESS_DENIED
E [01/Apr/2019:00:09:29 +0300] [Job 74] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:00:12:20 +0300] [Job 75] Session setup failed: NT_STATUS_LOGON_FAILURE
E [01/Apr/2019:00:12:20 +0300] [Job 75] Session setup failed: NT_STATUS_ACCESS_DENIED
...........
E [01/Apr/2019:16:27:12 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:16:30:09 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:16:30:14 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:16:30:19 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:16:30:24 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page
E [01/Apr/2019:16:30:35 +0300] [Job 107] NT_STATUS_ACCESS_DENIED opening remote spool Test Page

```

Switching ufw dows not change anything. On Windows side Guest account is active and Password Protected Sharing is disabled. Printer permissions are set for Guest and I can print under Guest account locally on that Win7 machine with no problem. LOCAL is the name of workgroup.

So, what am I really need to do to finally get that linux printing work? With Windows on laptop - no problems, linux file sharing - no problems, but no printing. At all.

---

### Post by kotee on 2019-04-04
Looks like creating an user with the same username and password on both computers is mandatory; that is a hack, as for me.
[https://lists.samba.org/archive/samba/2019-April/222199.html](https://lists.samba.org/archive/samba/2019-April/222199.html)

---

