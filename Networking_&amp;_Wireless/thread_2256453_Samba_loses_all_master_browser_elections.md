---
title: "Samba loses all master browser elections"
date: 2014-12-12
forum: Networking &amp; Wireless
---

### Post by Adunamia on 2014-12-12
I have been wrestling with this issue for a while now and have tried everything I found about this issue. After about 1-2 days, any windows machine will be unable to resolve explorer requests by hostname (IP and FQDN still work). When I look to see if the samba AD DC is in net view, it does not appear. Samba does not appear to even be ATTEMPTING to participate in elections despite the options being set in my smb.conf (see below). Any help is greatly appreciated. I have tried changing resolve order, disabling wins, setting host file entries for static hosts, but nothing seems to stick. Local windows 7 pro computers are winning elections and if I force them all off, name resolution through explorer still does not work (windows 8 pro machines don't seem to win the elections). Supposedly, I should be seeing entries in my log files about the browser election (as it should be forced when samba starts), but I have not seen anything relevant in log files (went as far as log level 10 at one point). Everything else seems to be working (DNS lookups, file shares, etc.) and I can still access the shares if I map by IP or FQDN, but I would like to not have to rely on this if possible. Windows firewall is off, the default gateway is set to allow all traffic on ports 135-139, 445 on TCP and UDP, and UFW/IPtables are not active. smbtree/net view show all computers as expected EXCEPT for the DC and it's shares. If I perform net view Samba-DC, it sees all shares as expected, however.

I have removed workgroup and realm names for privacy, but they are resolving correctly through DNS and all other services, so I believe those are fine.

/etc/samba/smb.conf:
```

[global]
        workgroup = OURWORKGROUP
        realm =OURREALM
        netbios name = Samba-DC
        server string = %h
        security = user
        map to guest = Bad User
        encrypt passwords = yes
        server role = active directory domain controller
        server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, ntp_signd, winbind, kcc, dnsupdate, smb
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, u$
        idmap_ldb:use rfc2307 = yes
        name resolve order = wins lmhosts hosts bcast
        wins support = yes
        os level = 255
        domain master = yes
        preferred master = yes
        localmaster = yes
        bind interfaces only = false
        time server = yes
        dns proxy = yes
        log level = 3
        log file = /var/log/samba/log.%m
[netlogon]
        path = /var/lib/samba/sysvol/OURREALM/scripts
        read only = No
        browseable = yes
[sysvol]
        path = /var/lib/samba/sysvol
        read only = No
        browseable = yes
[Users]
        path = /mnt/file_storage/Users
        read only = No
        force create mode = 0775
        force directory mode = 0775

[Shared]
        path = /mnt/file_storage/Shared
        read only = No
        force create mode = 0775
        force directory mode = 0775

[Backups]
        path = /mnt/file_storage/Backups
        read only = No

```

Output of testparm -s -v:
```
        dos charset = CP850
        unix charset = UTF-8
        workgroup = OURWORKGROUP
        realm = OURREALM
        netbios name =Samba-DC
        netbios aliases =
        netbios scope =
        server string = %h
        interfaces =
        bind interfaces only = No
        server role = active directory domain controller
        security = USER
        auth methods =
        encrypt passwords = Yes
        client schannel = Auto
        server schannel = Auto
        allow trusted domains = Yes
        map to guest = Bad User
        null passwords = No
        obey pam restrictions = No
        password server = *
        smb passwd file = /etc/samba/smbpasswd
        private dir = /var/lib/samba/private
        passdb backend = samba_dsdb
        algorithmic rid base = 1000
        root directory =
        guest account = nobody
        enable privileges = Yes
        pam password change = No
        passwd program =
        passwd chat = *new*password* %n\n *new*password* %n\n *changed*
        passwd chat debug = No
        passwd chat timeout = 2
        check password script =
        username map =
        username level = 0
        unix password sync = No
        restrict anonymous = 0
        lanman auth = No
        ntlm auth = Yes
        client NTLMv2 auth = Yes
        client lanman auth = No
        client plaintext auth = No
        client use spnego principal = No
        preload modules =
        dedicated keytab file =
        kerberos method = default
        map untrusted to domain = No
        log level = 2
        syslog = 1
        syslog only = No
        log file = /var/log/samba/log.%m
        max log size = 5000
        debug timestamp = Yes
        debug prefix timestamp = No
        debug hires timestamp = Yes
        debug pid = No
        debug uid = No
        debug class = No
        enable core files = Yes
        smb ports = 445, 139
        large readwrite = Yes
        server max protocol = SMB3
        server min protocol = LANMAN1
        client max protocol = NT1
        client min protocol = CORE
        unicode = Yes
        min receivefile size = 0
        read raw = Yes
        write raw = Yes
        disable netbios = No
        reset on zero vc = No
        log writeable files on exit = No
        defer sharing violations = Yes
        nt pipe support = Yes
        nt status support = Yes
        max mux = 50
        max xmit = 16644
        name resolve order = wins, lmhosts, hosts, bcast
        max ttl = 259200
        max wins ttl = 518400
        min wins ttl = 21600
        time server = Yes
        unix extensions = Yes
        use spnego = Yes
        client signing = default
        server signing = default
        client use spnego = Yes
        client ldap sasl wrapping = plain
        enable asu support = No
        svcctl list =
        cldap port = 0
        dgram port = 0
        nbt port = 0
        krb5 port = 0
        kpasswd port = 0
        web port = 0
        rpc big endian = No
        deadtime = 0
        getwd cache = Yes
        keepalive = 300
        lpq cache time = 30
        max smbd processes = 0
        max disk size = 0
        max open files = 16384
        socket options = TCP_NODELAY
        use mmap = Yes
        use ntdb = No
        hostname lookups = No
        name cache timeout = 660
        ctdbd socket =
        cluster addresses =
        clustering = No
        ctdb timeout = 0
        ctdb locktime warn threshold = 0
        smb2 max read = 1048576
        smb2 max write = 1048576
        smb2 max trans = 1048576
        smb2 max credits = 8192
        load printers = Yes
        printcap cache time = 750
        printcap name =
        cups server =
        cups encrypt = No
        cups connection timeout = 30
        iprint server =
        disable spoolss = No
        addport command =
        enumports command =
        addprinter command =
        deleteprinter command =
        show add printer wizard = Yes
        os2 driver map =
        mangling method = hash2
        mangle prefix = 1
        max stat cache size = 256
        stat cache = Yes
        machine password timeout = 604800
        add user script =
        rename user script =
        delete user script =
        add group script =
        delete group script =
        add user to group script =
        delete user from group script =
        set primary group script =
        add machine script =
        shutdown script =
        abort shutdown script =
        username map script =
        username map cache time = 0
        logon script =
        logon path = \\%N\%U\profile
        logon drive =
        logon home = \\%N\%U
        domain logons = No
        init logon delayed hosts =
        init logon delay = 100
        os level = 255
        lm announce = Auto
        lm interval = 60
        preferred master = Yes
        local master = Yes
        domain master = Yes
        browse list = Yes
        enhanced browsing = Yes
        dns proxy = Yes
        wins proxy = No
        wins server =
        wins support = Yes
        wins hook =
        lock spin time = 200
        oplock break wait time = 0
        ldap admin dn =
        ldap delete dn = No
        ldap group suffix =
        ldap idmap suffix =
        ldap machine suffix =
        ldap passwd sync = no
        ldap replication sleep = 1000
        ldap suffix =
        ldap ssl = start tls
        ldap ssl ads = No
        ldap deref = auto
        ldap follow referral = Auto
        ldap timeout = 15
        ldap connection timeout = 2
        ldap page size = 1024
        ldap user suffix =
        ldap debug level = 0
        ldap debug threshold = 10
        eventlog list =
        add share command =
        change share command =
        delete share command =
        preload =
        lock directory = /var/run/samba
        state directory = /var/lib/samba
        cache directory = /var/cache/samba
        pid directory = /var/run/samba
        ntp signd socket directory =
        utmp directory =
        wtmp directory =
        utmp = No
        default service =
        message command =
        get quota command =
        set quota command =
        remote announce =
        remote browse sync =
        nbt client socket address = 0.0.0.0
        nmbd bind explicit broadcast = Yes
        homedir map = auto.home
        afs username map =
        afs token lifetime = 604800
        log nt token command =
        NIS homedir = No
        registry shares = No
        usershare allow guests = No
        usershare max shares = 100
        usershare owner only = Yes
        usershare path = /var/lib/samba/usershares
        usershare prefix allow list =
        usershare prefix deny list =
        usershare template share =
        async smb echo handler = No
        panic action =
        perfcount module =
        host msdfs = Yes
        passdb expand explicit = No
        idmap backend = tdb
        idmap cache time = 604800
        idmap negative cache time = 120
        idmap uid =
        idmap gid =
        template homedir = /home/%D/%U
        template shell = /bin/false
        winbind separator = \
        winbind cache time = 300
        winbind reconnect delay = 30
        winbind max clients = 200
        winbind enum users = No
        winbind enum groups = No
        winbind use default domain = No
        winbind trusted domains only = No
        winbind nested groups = Yes
        winbind expand groups = 1
        winbind nss info = template
        winbind refresh tickets = No
        winbind offline logon = No
        winbind normalize names = No
        winbind rpc only = No
        create krb5 conf = Yes
        ncalrpc dir = /var/run/samba/ncalrpc
        winbind max domain connections = 1
        winbindd socket directory =
        winbindd privileged socket directory =
        winbind sealed pipes = No
        allow dns updates = disabled
        dns forwarder =
        dns update command =
        nsupdate command =
        rndc command =
        multicast dns register = Yes
        samba kcc command =
        server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, ntp_signd, winbind, kcc, dnsupdate, smb
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
        spn update command =
        share backend =
        tls enabled = No
        tls keyfile =
        tls certfile =
        tls cafile =
        tls crlfile =
        tls dh params file =
        rpc_server:tcpip = no
        rpc_daemon:spoolssd = embedded
        rpc_server:spoolss = embedded
        rpc_server:winreg = embedded
        rpc_server:ntsvcs = embedded
        rpc_server:eventlog = embedded
        rpc_server:srvsvc = embedded
        rpc_server:svcctl = embedded
        rpc_server:default = external
        idmap_ldb:use rfc2307 = yes
        idmap config * : backend = tdb
        comment =
        path =
        username =
        invalid users =
        valid users =
        admin users =
        read list =
        write list =
        force user =
        force group =
        read only = Yes
        acl check permissions = Yes
        acl group control = No
        acl map full control = Yes
        acl allow execute always = No
        create mask = 0744
        force create mode = 00
        directory mask = 0755
        force directory mode = 00
        force unknown acl user = No
        inherit permissions = No
        inherit acls = No
        inherit owner = No
        guest only = No
        administrative share = No
        guest ok = No
        only user = No
        hosts allow =
        hosts deny =
        allocation roundup size = 1048576
        aio read size = 0
        aio write size = 0
        aio write behind =
        ea support = No
        nt acl support = Yes
        profile acls = No
        map acl inherit = No
        afs share = No
        smb encrypt = default
        durable handles = Yes
        block size = 1024
        change notify = Yes
        directory name cache size = 100
        kernel change notify = Yes
        max connections = 0
        min print space = 0
        strict allocate = No
        strict sync = No
        sync always = No
        use sendfile = No
        write cache size = 0
        max reported print jobs = 0
        max print jobs = 1000
        printable = No
        print notify backchannel = Yes
        print ok = No
        printing = cups
        cups options =
        print command =
        lpq command = %p
        lprm command =
        lppause command =
        lpresume command =
        queuepause command =
        queueresume command =
        printer name =
        use client driver = No
        default devmode = Yes
        force printername = No
        printjob username = %U
        default case = lower
        case sensitive = Auto
        preserve case = Yes
        short preserve case = Yes
        mangling char = ~
        hide dot files = Yes
        hide special files = No
        hide unreadable = No
        hide unwriteable files = No
        delete veto files = No
        veto files =
        hide files =
        veto oplock files =
        map archive = No
        map hidden = No
        map system = No
        map readonly = no
        mangled names = Yes
        store dos attributes = Yes
        dmapi support = No
        browseable = Yes
        access based share enum = No
        blocking locks = Yes
        csc policy = manual
        fake oplocks = No
        kernel oplocks = No
        kernel share modes = Yes
        locking = Yes
        oplocks = Yes
        level2 oplocks = Yes
        oplock contention limit = 2
        posix locking = Yes
        strict locking = Auto
        dfree cache time = 0
        dfree command =
        copy =
        preexec =
        preexec close = No
        postexec =
        root preexec =
        root preexec close = No
        root postexec =
        available = Yes
        volume =
        fstype = NTFS
        wide links = No
        follow symlinks = Yes
        dont descend =
        magic script =
        magic output =
        delete readonly = No
        dos filemode = No
        dos filetimes = Yes
        dos filetime resolution = No
        fake directory create times = No
        vfs objects = dfs_samba4, acl_xattr
        msdfs root = No
        msdfs proxy =
        ntvfs handler =

[netlogon]
        path = /var/lib/samba/sysvol/OURREALM/scripts
        read only = No

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

[Users]
        path = /mnt/file_storage/Users
        read only = No
        force create mode = 0775
        force directory mode = 0775

[Shared]
        path = /mnt/file_storage/Shared
        read only = No
        force create mode = 0775
        force directory mode = 0775

[Backups]
        path = /mnt/file_storage/Backups
        read only = No

```

---

### Post by bab1 on 2014-12-13
> **Adunamia said:**
> I have been wrestling with this issue for a while now and have tried everything I found about this issue. After about 1-2 days, any windows machine will be unable to resolve explorer requests by hostname (IP and FQDN still work). 

Samba, WIndows Sharing use NETBIOS_NAMES or IP addresses to locate SMB/CIFS resources (i.e. shares or hosts).  The format is  [COLOR="#0000FF"]//NETBIOS_NAME[/COLOR][COLOR="#FF0000"]/SHARE_NAME[/COLOR] for all shares and*[COLOR="#0000FF"] //NETBIOS_NAME [/COLOR]**[COLOR="#008000"]<one-char-suffix>[/COLOR]*** for servers, master-browsers or clients.  The hostname is converted in Samba by the *nmbd *daemon (process).  Of course IP addresses need no name resolution.  Hostnames are resolved as I have said.  FQDN are not used in this scheme.  What do you mean by  "... FQDN still work"?  How does it work?  How are you using the FQDN?  To login?  
> 
When I look to see if the samba AD DC is in net view, it does not appear. Samba does not appear to even be ATTEMPTING to participate in elections despite the options being set in my smb.conf (see below). Any help is greatly appreciated. 

This is not a MASTER_BROWSER (MB) problem per se.  The location of the MB should not make any difference on a single subnet network.  Are you running a multi-segment network?
> 
I have tried changing resolve order, disabling wins, setting host file entries for static hosts, but nothing seems to stick. Local windows 7 pro computers are winning elections and if I force them all off, name resolution through explorer still does not work (windows 8 pro machines don't seem to win the elections). Supposedly, I should be seeing entries in my log files about the browser election (as it should be forced when samba starts), but I have not seen anything relevant in log files (went as far as log level 10 at one point). Everything else seems to be working (DNS lookups, file shares, etc.) and I can still access the shares if I map by IP or FQDN, but I would like to not have to rely on this if possible. Windows firewall is off, the default gateway is set to allow all traffic on ports 135-139, 445 on TCP and UDP, and UFW/IPtables are not active. smbtree/net view show all computers as expected EXCEPT for the DC and it's shares. If I perform net view Samba-DC, it sees all shares as expected, however.

The election you are referring to only happens when the host that is the MB is turned off.  Then there is an election to create a new MB.  Until the that MB goes offline there will be no further election.  Just starting Samba does not force an election.  

Wherever the MB resides all browsing should work unless the announcements of hosts entering or leaving the network are not broadcast across the entire network.  In short the problem is not the election of a MB but the population of the MB browse list.  I would check to see if Windows NETBIOS over TCP (NBT) is functioning correctly. 

If you have a single segment network then WINS is not needed or recommended.   My suggestion is to start with the default global section of the smb.conf and work out the problems in an individual manner.
> 
I have removed workgroup and realm names for privacy, but they are resolving correctly through DNS and all other services, so I believe those are fine.

Realm names?  That's Kerbros and not relevant.  Workgroup names are not resolved by DNS at all.  They are announced as SMB/CIFS resources using NETBIOS_NAMES.  Neither are important to the problem other that to state that the workgroup name should be 15 characters or less.  This is a SMB/CIFS limitation. 

The questions boil down to:  How are you broadcasting the NETBIOS_NAMES?  What is the IP addressing scheme for the network (single number range or multiple separate ranges)?

I would be interested in what smbtree really shows.  Post the output of```
smbtree -d3
```...you can obscure the workgroup if you like, but there really are no "security" implications showing it.  None of this should be available outside of your LAN.

---

### Post by Adunamia on 2014-12-15
Thanks for the input so far. If I navigate to \\PC.mydomain.com, the path will still resolve. It appears to only be NetBIOS/WINS which is having issues. Unfortunately, this is a multi-subnet environment and the use of WINS would be very helpful. From what I read in the samba documentation, toggling the preferred master to yes looked to force an election which Samba starts, apparently this is not the case.

The current IP scheme is 10.X.X.X with a 255.0.0.0 subnet. We have other subnets from other locations, but getting resolution working on this range is the critical component.

smbtree -d3 output:
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=10.10.1.101 bcast=10.255.255.255 netmask=255.0.0.0
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name RSICNC<0x1d>
[COLOR="#FF0000"]Got a positive name query response from 10.10.1.105 ( 10.10.1.105 )[/COLOR]
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 10.10.4.4 ( 10.10.4.4 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.4 at port 445
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
        \\TOM3-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name TOM3-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TOM3-PC<0x20>
resolve_hosts: Attempting host lookup for name TOM3-PC<0x20>
resolve_hosts: getaddrinfo failed for name TOM3-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name TOM3-PC<0x20>
Got a positive name query response from 10.10.4.126 ( 10.10.4.126 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.126 at port 445
Doing spnego session setup (blob length=42)
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
        \\SHIPPING-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SHIPPING-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SHIPPING-PC<0x20>
resolve_hosts: Attempting host lookup for name SHIPPING-PC<0x20>
resolve_hosts: getaddrinfo failed for name SHIPPING-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SHIPPING-PC<0x20>
Got a positive name query response from 10.10.4.13 ( 10.10.4.13 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.13 at port 445
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
        \\REY-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name REY-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name REY-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name REY-LAPTOP<0x20>
resolve_hosts: getaddrinfo failed for name REY-LAPTOP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name REY-LAPTOP<0x20>
Got a positive name query response from 10.10.4.4 ( 10.10.4.4 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.4 at port 445
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
        \\QUALITY-LAPTOP1
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name QUALITY-LAPTOP1<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name QUALITY-LAPTOP1<0x20>
resolve_hosts: Attempting host lookup for name QUALITY-LAPTOP1<0x20>
resolve_hosts: getaddrinfo failed for name QUALITY-LAPTOP1 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name QUALITY-LAPTOP1<0x20>
Got a positive name query response from 10.10.4.82 ( 10.10.4.82 10.10.4.182 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.82 at port 445
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
        \\PATRICK-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name PATRICK-LAPTOP<0x20>
resolve_hosts: getaddrinfo failed for name PATRICK-LAPTOP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PATRICK-LAPTOP<0x20>
Got a positive name query response from 10.10.4.160 ( 10.10.4.160 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.160 at port 445
Connecting to 10.10.4.160 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b6afe0] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b6a880] mpx_fde[(nil)] fd[18] - disabling
        \\MACHINECTRLPORT
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MACHINECTRLPORT<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MACHINECTRLPORT<0x20>
resolve_hosts: Attempting host lookup for name MACHINECTRLPORT<0x20>
resolve_hosts: getaddrinfo failed for name MACHINECTRLPORT [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MACHINECTRLPORT<0x20>
Got a positive name query response from 10.10.4.86 ( 10.10.4.86 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.86 at port 445
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
        \\HPTRAVELLINGCAD
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name HPTRAVELLINGCAD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HPTRAVELLINGCAD<0x20>
resolve_hosts: Attempting host lookup for name HPTRAVELLINGCAD<0x20>
resolve_hosts: getaddrinfo failed for name HPTRAVELLINGCAD [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name HPTRAVELLINGCAD<0x20>
Got a positive name query response from 10.10.4.148 ( 10.10.4.148 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.148 at port 445
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
        \\CAD-PC1
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name CAD-PC1<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CAD-PC1<0x20>
resolve_hosts: Attempting host lookup for name CAD-PC1<0x20>
resolve_hosts: getaddrinfo failed for name CAD-PC1 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CAD-PC1<0x20>
Got a positive name query response from 10.10.4.89 ( 10.10.4.89 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.89 at port 445
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
RSICNC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name RSICNC<0x1d>
Got a positive name query response from 10.10.1.105 ( 10.10.1.105 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\RSI-TIMECLOCK
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSI-TIMECLOCK<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RSI-TIMECLOCK<0x20>
resolve_hosts: Attempting host lookup for name RSI-TIMECLOCK<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\RSI-TIMECLOCK\IPC$            Remote IPC
                \\RSI-TIMECLOCK\C$              Default share
                \\RSI-TIMECLOCK\ADMIN$          Remote Admin
        \\PATRICK-GATEWAY
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-GATEWAY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-GATEWAY<0x20>
resolve_hosts: Attempting host lookup for name PATRICK-GATEWAY<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.3 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\PATRICK-GATEWAY\print$                Printer Drivers
                \\PATRICK-GATEWAY\Patrick's Media
                \\PATRICK-GATEWAY\OKI C3200n            OKI C3200n
                \\PATRICK-GATEWAY\K$                    Default share
                \\PATRICK-GATEWAY\IPC$                  Remote IPC
                \\PATRICK-GATEWAY\C$                    Default share
                \\PATRICK-GATEWAY\ADMIN$                Remote Admin
        \\MIKE-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MIKE-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MIKE-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name MIKE-LAPTOP<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.23 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\MIKE-LAPTOP\print$            Printer Drivers
                \\MIKE-LAPTOP\IPC$              Remote IPC
                \\MIKE-LAPTOP\C$                Default share
                \\MIKE-LAPTOP\ADMIN$            Remote Admin
        \\MICHAEL-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name MICHAEL-LAPTOP<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.46 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\MICHAEL-LAPTOP\Users
                \\MICHAEL-LAPTOP\IPC$                   Remote IPC
                \\MICHAEL-LAPTOP\E$                     Default share
                \\MICHAEL-LAPTOP\D$                     Default share
                \\MICHAEL-LAPTOP\C$                     Default share
                \\MICHAEL-LAPTOP\ADMIN$                 Remote Admin
MAIN
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MAIN<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MAIN<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MAIN<0x1d>
Got a positive name query response from 10.10.9.1 ( 10.10.9.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.9.1 at port 445
Connecting to 10.10.9.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b75310] mpx_fde[(nil)] fd[34] - disabling
Doing spnego session setup (blob length=42)
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
        \\SUPERVISOR-WAND
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SUPERVISOR-WAND<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SUPERVISOR-WAND<0x20>
resolve_hosts: Attempting host lookup for name SUPERVISOR-WAND<0x20>
resolve_hosts: getaddrinfo failed for name SUPERVISOR-WAND [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SUPERVISOR-WAND<0x20>
Got a positive name query response from 10.10.9.1 ( 10.10.9.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.9.1 at port 445
Connecting to 10.10.9.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b78fc0] mpx_fde[(nil)] fd[36] - disabling
Doing spnego session setup (blob length=42)
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
        \\QIS-CALIPER
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name QIS-CALIPER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name QIS-CALIPER<0x20>
resolve_hosts: Attempting host lookup for name QIS-CALIPER<0x20>
resolve_hosts: getaddrinfo failed for name QIS-CALIPER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name QIS-CALIPER<0x20>
Got a positive name query response from 10.10.7.1 ( 10.10.7.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.7.1 at port 445
Connecting to 10.10.7.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b7a630] mpx_fde[(nil)] fd[37] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b79ed0] mpx_fde[(nil)] fd[38] - disabling
        \\PHIL-WORK-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WORK-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WORK-PC<0x20>
resolve_hosts: Attempting host lookup for name PHIL-WORK-PC<0x20>
resolve_hosts: getaddrinfo failed for name PHIL-WORK-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PHIL-WORK-PC<0x20>
Got a positive name query response from 10.10.4.105 ( 10.10.4.105 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.105 at port 445
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
        \\MARY-HP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MARY-HP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MARY-HP<0x20>
resolve_hosts: Attempting host lookup for name MARY-HP<0x20>
resolve_hosts: getaddrinfo failed for name MARY-HP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MARY-HP<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f84e4b7bfb0] mpx_fde[(nil)] fd[40] - disabling
        \\CADD
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name CADD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CADD<0x20>
resolve_hosts: Attempting host lookup for name CADD<0x20>
resolve_hosts: getaddrinfo failed for name CADD [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CADD<0x20>
Got a positive name query response from 10.10.4.25 ( 10.10.4.25 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.25 at port 445
Doing spnego session setup (blob length=106)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=cadd$@REALM
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: No logon servers

```

There are currently 3 workgroups which will be seen: RSICNC (Samba), MAIN (Old workgroup), and WORKGROUP (Isolated computers). Highlighted above is what I've been seeing. 10.10.1.105 is the current Master Browser, but all entries should be resolving to 10.10.1.101. The DC does not show up in this output.

---

### Post by bab1 on 2014-12-15
> **Adunamia said:**
> Thanks for the input so far. If I navigate to \\PC.mydomain.com, the path will still resolve.

Navigate in what manner.  I don't believe \\ps.mydomain is a legitimate UNC.  It is certainly not a SMB resource.
> 
It appears to only be NetBIOS/WINS which is having issues. Unfortunately, this is a multi-subnet environment and the use of WINS would be very helpfl. 

On a multi segment network WINS is mandatory.
> 
From what I read in the samba documentation, toggling the preferred master to yes looked to force an election which Samba starts, apparently this is not the case.

From all that I have read the Preferred Master Browser PMB doesn't work as advertised.  You don't really need it anyway.  If you turn all the clients off then the server will become the MB.  Since the server will be up 24/7 it will continue to be the MB until shutdown.
> 
The current IP scheme is 10.X.X.X with a 255.0.0.0 subnet.  We have other subnets from other locations, but getting resolution working on this range is the critical component.

The 10,0.0.0 /8 is the NETWORK.  You can subnet the network.  The the IP address range is private (for LAN use only) 
Explain how the "subnets from other locations" fit in.  What is the network topology.  SMB/CIFS is a local network only technology.  You can't use Samba over the Internet without using a VPN.  That would still put those clients in the 10.0.0.0/8 network.
> 
There are currently 3 workgroups which will be seen: RSICNC (Samba), MAIN (Old workgroup), and WORKGROUP (Isolated computers).

I see these.  How is the workgroup named WORKGROUP isolated?  The IP range is still in the 10.0.0.0/8 network.
> 
Highlighted above is what I've been seeing. [The IP address] 10.10.1.105 is the current Master Browser, but all entries should be resolving to 10.10.1.101. The DC does not show up in this output.
What you have highlighted is the request for the workgroup ID (<0x1d>).    At the present time all of the NETBIOS NAMES are located via broadcast (bcast).
I don't see any request for the MB name.  It would look something like this```
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
```

At this point I only see one (1) network (e.g. 10.0.0.0/8 (255.0.0.0)).  I don't see any reason for the unnecessary complication of running a WINS server.  I would remove all WINS configuration (clients and server) and set the "name resolution = host bcast" to begin with.  It's entirely possible that a WINS misconfiguration is what is causing your problem.

---

### Post by Adunamia on 2014-12-15
Sorry, I was unclear. Currently the network is a simple 10.X.X.X/8 network, but this will be segmented into multiple subnets as VPN locations are brought online so this would be nice to have working. However, for simplicity sake, I removed all wins configuration.
smb.conf with wins options commented out. The remaining options are needed to maintain functionality. Even so, I'm not seeing the DC show up in then network.
```
[global]
        workgroup = RSICNC
        realm = REALM
        netbios name = Samba-DC
        server string = %h
        security = user
        map to guest = Bad User
        encrypt passwords = yes
        server role = active directory domain controller
        server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, ntp_signd, winbind, kcc, dnsupdate, smb
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, u$
        idmap_ldb:use rfc2307 = yes
        name resolve order = lmhosts hosts bcast
#       wins support = yes
#       os level = 255
#       domain master = yes
#       preferred master = yes
#       localmaster = yes
        bind interfaces only = false
#       time server = yes
#       dns proxy = yes
#       log level = 3
#       log file = /var/log/samba/log.%m

```
New output of smbtree -d3:
```
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name RSICNC<0x1d>
Got a positive name query response from 10.10.1.105 ( 10.10.1.105 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 10.10.4.4 ( 10.10.4.4 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.4 at port 445
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
        \\TOM3-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name TOM3-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TOM3-PC<0x20>
resolve_hosts: Attempting host lookup for name TOM3-PC<0x20>
resolve_hosts: getaddrinfo failed for name TOM3-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name TOM3-PC<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b00c40] mpx_fde[(nil)] fd[10] - disabling
        \\SHIPPING-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SHIPPING-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SHIPPING-PC<0x20>
resolve_hosts: Attempting host lookup for name SHIPPING-PC<0x20>
resolve_hosts: getaddrinfo failed for name SHIPPING-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SHIPPING-PC<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b00fa0] mpx_fde[(nil)] fd[10] - disabling
        \\REY-LASER
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name REY-LASER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name REY-LASER<0x20>
resolve_hosts: Attempting host lookup for name REY-LASER<0x20>
resolve_hosts: getaddrinfo failed for name REY-LASER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name REY-LASER<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b011b0] mpx_fde[(nil)] fd[10] - disabling
        \\REY-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name REY-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name REY-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name REY-LAPTOP<0x20>
resolve_hosts: getaddrinfo failed for name REY-LAPTOP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name REY-LAPTOP<0x20>
Got a positive name query response from 10.10.4.4 ( 10.10.4.4 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.4 at port 445
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
        \\QUALITY-LAPTOP1
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name QUALITY-LAPTOP1<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name QUALITY-LAPTOP1<0x20>
resolve_hosts: Attempting host lookup for name QUALITY-LAPTOP1<0x20>
resolve_hosts: getaddrinfo failed for name QUALITY-LAPTOP1 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name QUALITY-LAPTOP1<0x20>
Got a positive name query response from 10.10.4.82 ( 10.10.4.82 10.10.4.182 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.82 at port 445
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
        \\MACHINECTRLPORT
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MACHINECTRLPORT<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MACHINECTRLPORT<0x20>
resolve_hosts: Attempting host lookup for name MACHINECTRLPORT<0x20>
resolve_hosts: getaddrinfo failed for name MACHINECTRLPORT [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MACHINECTRLPORT<0x20>
Got a positive name query response from 10.10.4.86 ( 10.10.4.86 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.86 at port 445
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
        \\HPTRAVELLINGCAD
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name HPTRAVELLINGCAD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HPTRAVELLINGCAD<0x20>
resolve_hosts: Attempting host lookup for name HPTRAVELLINGCAD<0x20>
resolve_hosts: getaddrinfo failed for name HPTRAVELLINGCAD [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name HPTRAVELLINGCAD<0x20>
Got a positive name query response from 10.10.4.148 ( 10.10.4.148 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.148 at port 445
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
        \\CAD-PC1
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name CAD-PC1<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CAD-PC1<0x20>
resolve_hosts: Attempting host lookup for name CAD-PC1<0x20>
resolve_hosts: getaddrinfo failed for name CAD-PC1 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CAD-PC1<0x20>
Got a positive name query response from 10.10.4.89 ( 10.10.4.89 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.89 at port 445
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
RSICNC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name RSICNC<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name RSICNC<0x1d>
Got a positive name query response from 10.10.1.105 ( 10.10.1.105 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\RSI-TIMECLOCK
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name RSI-TIMECLOCK<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name RSI-TIMECLOCK<0x20>
resolve_hosts: Attempting host lookup for name RSI-TIMECLOCK<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.1.105 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\RSI-TIMECLOCK\IPC$            Remote IPC
                \\RSI-TIMECLOCK\C$              Default share
                \\RSI-TIMECLOCK\ADMIN$          Remote Admin
        \\PATRICK-GATEWAY
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-GATEWAY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PATRICK-GATEWAY<0x20>
resolve_hosts: Attempting host lookup for name PATRICK-GATEWAY<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.3 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: No logon servers
        \\MIKE-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MIKE-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MIKE-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name MIKE-LAPTOP<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.23 at port 445
Doing spnego session setup (blob length=120)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\MIKE-LAPTOP\print$            Printer Drivers
                \\MIKE-LAPTOP\IPC$              Remote IPC
                \\MIKE-LAPTOP\C$                Default share
                \\MIKE-LAPTOP\ADMIN$            Remote Admin
        \\MICHAEL-LAPTOP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-LAPTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-LAPTOP<0x20>
resolve_hosts: Attempting host lookup for name MICHAEL-LAPTOP<0x20>
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.46 at port 445
Connecting to 10.10.4.46 at port 139
MAIN
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MAIN<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name MAIN<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MAIN<0x1d>
Got a positive name query response from 10.10.9.1 ( 10.10.9.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.9.1 at port 445
Connecting to 10.10.9.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b0ee30] mpx_fde[(nil)] fd[28] - disabling
Doing spnego session setup (blob length=42)
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
        \\SUPERVISOR-WAND
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SUPERVISOR-WAND<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SUPERVISOR-WAND<0x20>
resolve_hosts: Attempting host lookup for name SUPERVISOR-WAND<0x20>
resolve_hosts: getaddrinfo failed for name SUPERVISOR-WAND [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SUPERVISOR-WAND<0x20>
Got a positive name query response from 10.10.9.1 ( 10.10.9.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.9.1 at port 445
Connecting to 10.10.9.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b107e0] mpx_fde[(nil)] fd[30] - disabling
Doing spnego session setup (blob length=42)
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
        \\QIS-CALIPER
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name QIS-CALIPER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name QIS-CALIPER<0x20>
resolve_hosts: Attempting host lookup for name QIS-CALIPER<0x20>
resolve_hosts: getaddrinfo failed for name QIS-CALIPER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name QIS-CALIPER<0x20>
Got a positive name query response from 10.10.7.1 ( 10.10.7.1 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.7.1 at port 445
Connecting to 10.10.7.1 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b11f10] mpx_fde[(nil)] fd[31] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f0946b117b0] mpx_fde[(nil)] fd[32] - disabling
        \\PHIL-WORK-PC
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WORK-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WORK-PC<0x20>
resolve_hosts: Attempting host lookup for name PHIL-WORK-PC<0x20>
resolve_hosts: getaddrinfo failed for name PHIL-WORK-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name PHIL-WORK-PC<0x20>
Got a positive name query response from 10.10.4.105 ( 10.10.4.105 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.105 at port 445
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
        \\MARY-HP
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MARY-HP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MARY-HP<0x20>
resolve_hosts: Attempting host lookup for name MARY-HP<0x20>
resolve_hosts: getaddrinfo failed for name MARY-HP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MARY-HP<0x20>
Got a positive name query response from 10.10.4.125 ( 10.10.4.125 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.125 at port 445
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
        \\CADD
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name CADD<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CADD<0x20>
resolve_hosts: Attempting host lookup for name CADD<0x20>
resolve_hosts: getaddrinfo failed for name CADD [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CADD<0x20>
Got a positive name query response from 10.10.4.25 ( 10.10.4.25 )
tdb(/var/run/samba/gencache_notrans.tdb): tdb_open_ex: could not open file /var/run/samba/gencache_notrans.tdb: Permission denied
Connecting to 10.10.4.25 at port 445
Doing spnego session setup (blob length=106)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.2.840.113554.1.2.2.3
got OID=1.3.6.1.4.1.311.2.2.10
got principal=cadd$@REALM
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: No logon servers

```
I'm still not seeing the Samba-DC in this output, or net view from one of the RSICNC computers. WORKGROUP isn't physically isolated in anyway, but they are computers which are not on the domain to be kept separate as they mostly are machining front ends which we want to have separate from all other domain activity.

---

### Post by bab1 on 2014-12-15
Have you restarted the smbd service```
sudo service smbd restart
```...or rebooted the machine?

Is this host a testbed or a live production machine?

---

### Post by Adunamia on 2014-12-15
It is a live production server. It isn't under heavy load most times, so an occasional reboot isn't too big of a deal as it will usually go unnoticed. I restarted all samba services as well as rebooting the server, same output.

---

### Post by bab1 on 2014-12-15
Are all the services running?  What is the output of this```
pgrep -l mbd
```

You should have 2 smbd and 1 nmbd daemons running/

---

### Post by Adunamia on 2014-12-15
```
pgrep -l mbd
```
does not return anything

however, if I try to manually start the services....
```
$ sudo service smbd start
smbd start/running, process 2230
$ sudo service nmbd start
start: Job is already running: nmbd
$ sudo service smbd start
smbd start/running, process 2341

```

smbd does not seem to stay running, but if I look at the logs, the only complaint is:
```
[2014/12/15 16:19:12.644526,  0] ../source3/smbd/server.c:1250(main)
  server role = 'active directory domain controller' not compatible with running smbd standalone.
  You should start 'samba' instead, and it will control starting smbd if required
[2014/12/15 16:19:12,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.

```

ps aux shows:
```
root         1  0.4  0.0  33640  2960 ?        Ss   16:22   0:03 /sbin/init
root         2  0.0  0.0      0     0 ?        S    16:22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/0:0]
root         5  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/0:0H]
root         6  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/u12:0]
root         7  0.1  0.0      0     0 ?        S    16:22   0:00 [rcu_sched]
root         8  0.1  0.0      0     0 ?        S    16:22   0:01 [rcuos/0]
root         9  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuos/1]
root        10  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuos/2]
root        11  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuos/3]
root        12  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuos/4]
root        13  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuos/5]
root        14  0.0  0.0      0     0 ?        S    16:22   0:00 [rcu_bh]
root        15  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/0]
root        16  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/1]
root        17  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/2]
root        18  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/3]
root        19  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/4]
root        20  0.0  0.0      0     0 ?        S    16:22   0:00 [rcuob/5]
root        21  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/0]
root        22  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/0]
root        23  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/1]
root        24  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/1]
root        25  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/1]
root        26  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/1:0]
root        27  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/1:0H]
root        28  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/2]
root        29  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/2]
root        30  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/2]
root        31  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/2:0]
root        32  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/2:0H]
root        33  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/3]
root        34  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/3]
root        35  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/3]
root        36  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/3:0]
root        37  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/3:0H]
root        38  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/4]
root        39  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/4]
root        40  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/4]
root        41  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/4:0]
root        42  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/4:0H]
root        43  0.0  0.0      0     0 ?        S    16:22   0:00 [watchdog/5]
root        44  0.0  0.0      0     0 ?        S    16:22   0:00 [migration/5]
root        45  0.0  0.0      0     0 ?        S    16:22   0:00 [ksoftirqd/5]
root        46  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/5:0]
root        47  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/5:0H]
root        48  0.0  0.0      0     0 ?        S<   16:22   0:00 [khelper]
root        49  0.0  0.0      0     0 ?        S    16:22   0:00 [kdevtmpfs]
root        50  0.0  0.0      0     0 ?        S<   16:22   0:00 [netns]
root        51  0.0  0.0      0     0 ?        S    16:22   0:00 [xenwatch]
root        52  0.0  0.0      0     0 ?        S    16:22   0:00 [xenbus]
root        53  0.0  0.0      0     0 ?        S<   16:22   0:00 [writeback]
root        54  0.0  0.0      0     0 ?        S<   16:22   0:00 [kintegrityd]
root        55  0.0  0.0      0     0 ?        S<   16:22   0:00 [bioset]
root        56  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/u13:0]
root        57  0.0  0.0      0     0 ?        S<   16:22   0:00 [kblockd]
root        58  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/4:1]
root        59  0.0  0.0      0     0 ?        S<   16:22   0:00 [ata_sff]
root        60  0.0  0.0      0     0 ?        S    16:22   0:00 [khubd]
root        61  0.0  0.0      0     0 ?        S<   16:22   0:00 [md]
root        62  0.0  0.0      0     0 ?        S<   16:22   0:00 [devfreq_wq]
root        63  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/2:1]
root        64  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/0:1]
root        66  0.0  0.0      0     0 ?        S    16:22   0:00 [khungtaskd]
root        67  0.0  0.0      0     0 ?        S    16:22   0:00 [kswapd0]
root        68  0.0  0.0      0     0 ?        SN   16:22   0:00 [ksmd]
root        69  0.0  0.0      0     0 ?        S    16:22   0:00 [fsnotify_mark]
root        70  0.0  0.0      0     0 ?        S    16:22   0:00 [ecryptfs-kthrea]
root        71  0.0  0.0      0     0 ?        S<   16:22   0:00 [crypto]
root        83  0.0  0.0      0     0 ?        S<   16:22   0:00 [kthrotld]
root        84  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/u12:1]
root        85  0.0  0.0      0     0 ?        S    16:22   0:00 [khvcd]
root        86  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/3:1]
root        87  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/5:1]
root        88  0.0  0.0      0     0 ?        S    16:22   0:00 [kworker/1:1]
root       108  0.0  0.0      0     0 ?        S<   16:22   0:00 [deferwq]
root       109  0.0  0.0      0     0 ?        S<   16:22   0:00 [charger_manager]
root       170  0.0  0.0      0     0 ?        S    16:22   0:00 [jbd2/xvda1-8]
root       171  0.0  0.0      0     0 ?        S<   16:22   0:00 [ext4-rsv-conver]
root       331  0.0  0.0  19476   648 ?        S    16:22   0:00 upstart-udev-bridge --daemon
root       340  0.0  0.0  51732  1924 ?        Ss   16:22   0:00 /lib/systemd/systemd-udevd --daemon
root       486  0.0  0.0  15260   408 ?        S    16:22   0:00 upstart-socket-bridge --daemon
root       523  0.0  0.0      0     0 ?        S    16:22   0:00 [jbd2/xvdb1-8]
root       524  0.0  0.0      0     0 ?        S<   16:22   0:00 [ext4-rsv-conver]
root       698  0.0  0.0  15408   724 ?        S    16:22   0:00 upstart-file-bridge --daemon
syslog     728  0.0  0.0 255844  1296 ?        Ssl  16:22   0:00 rsyslogd
message+   750  0.0  0.0  39356  1448 ?        Ss   16:22   0:00 dbus-daemon --system --fork
root       780  0.0  0.0  15820   964 tty4     Ss+  16:22   0:00 /sbin/getty -8 38400 tty4
root       783  0.0  0.0  15820   956 tty5     Ss+  16:22   0:00 /sbin/getty -8 38400 tty5
root       790  0.0  0.0  15820   952 tty2     Ss+  16:22   0:00 /sbin/getty -8 38400 tty2
root       791  0.0  0.0  15820   960 tty3     Ss+  16:22   0:00 /sbin/getty -8 38400 tty3
root       793  0.0  0.0  15820   956 tty6     Ss+  16:22   0:00 /sbin/getty -8 38400 tty6
root       799  0.0  0.5 496372 44284 ?        Ss   16:22   0:00 samba -D
root       809  0.0  0.0  43452  1756 ?        Ss   16:22   0:00 /lib/systemd/systemd-logind
root       819  0.0  0.0   4364   648 ?        Ss   16:22   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socke
root       824  0.0  0.0  23656   880 ?        Ss   16:22   0:00 cron
daemon     825  0.0  0.0  19140   160 ?        Ss   16:22   0:00 atd
root       864  0.0  0.0  61364  3076 ?        Ss   16:22   0:00 /usr/sbin/sshd -D
root       905  0.0  0.0  19308   804 ?        Ss   16:22   0:00 /usr/sbin/irqbalance
dhcpd      923  0.0  0.0  19652  6700 ?        Ss   16:22   0:00 dhcpd -user dhcpd -group dhcpd -f -q -4 -pf /run/
root       995  0.0  0.0      0     0 ?        S<   16:22   0:00 [kworker/u13:1]
ntp       1010  0.0  0.0  31444  2148 ?        Ss   16:22   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 107:115
root      1100  0.0  0.0  17972  1564 ?        S    16:22   0:00 /bin/bash /usr/sbin/xe-daemon -p /var/run/xe-daem
bind      1205  0.8  0.8 862640 73400 ?        Ssl  16:22   0:06 /usr/sbin/named -u bind
root      1304  0.0  0.4 507272 37740 ?        S    16:22   0:00 samba -D
root      1305  0.0  0.4 500524 34884 ?        S    16:22   0:00 samba -D
root      1306  0.0  0.3 496372 32384 ?        S    16:22   0:00 samba -D
root      1307  0.1  0.4 507496 37904 ?        S    16:22   0:01 samba -D
root      1308  0.0  0.4 496372 34016 ?        S    16:22   0:00 samba -D
root      1309  0.0  0.4 506804 36556 ?        S    16:22   0:00 samba -D
root      1310  0.0  0.4 496372 33888 ?        S    16:22   0:00 samba -D
root      1311  0.0  0.3 496372 32552 ?        S    16:22   0:00 samba -D
root      1312  0.0  0.4 499200 34152 ?        S    16:22   0:00 samba -D
root      1313  0.0  0.5 496372 41280 ?        S    16:22   0:00 samba -D
root      1314  0.0  0.4 496372 33444 ?        S    16:22   0:00 samba -D
root      1315  0.1  0.4 496372 33004 ?        S    16:22   0:01 samba -D
root      1341  0.0  0.0      0     0 ?        S    16:22   0:00 [kauditd]
root      1343  0.0  0.0 3148992 3984 ?        Sl   16:22   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1408  0.0  0.0 279760  3428 ?        Sl   16:22   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1427  0.0  0.4 500600 35768 ?        S    16:22   0:00 samba -D
admin     1458  0.0  0.0  24440   580 ?        S    16:22   0:00 dbus-launch --sh-syntax --exit-with-session
admin     1484  0.0  0.0  39248  1280 ?        Ss   16:22   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-ad
admin     1486  0.0  0.0  10616   316 ?        Ss   16:22   0:00 /usr/bin/ssh-agent -s
admin     1512  0.0  0.0 192444  3028 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfsd
admin     1516  0.0  0.0 345664  3144 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1001/gvfs -f -
admin     1528  0.0  0.0 147340  7848 ?        S    16:22   0:00 openbox --config-file /home/admin/.config/openbox
admin     1531  0.0  0.0  61856  2552 ?        S    16:22   0:00 xscreensaver -no-splash
admin     1532  0.0  0.1 357760 11292 ?        Sl   16:22   0:00 lxpanel --profile LXDE
admin     1533  0.0  0.2 561564 24428 ?        Sl   16:22   0:00 pcmanfm --desktop --profile LXDE
admin     1539  0.0  0.0  10616   316 ?        Ss   16:22   0:00 /usr/bin/ssh-agent -s
admin     1541  0.0  0.1 307484  8360 ?        Sl   16:22   0:00 /usr/lib/notification-daemon/notification-daemon
admin     1548  0.0  0.0 294640  4796 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
admin     1549  0.0  0.0 204020  3100 ?        Ssl  16:22   0:00 /usr/lib/x86_64-linux-gnu/menu-cache/menu-cached
root      1556  0.0  0.0 371264  4852 ?        Sl   16:22   0:00 /usr/lib/udisks2/udisksd --no-debug
admin     1563  0.0  0.0 337324  3092 ?        Sl   16:22   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
admin     1569  0.0  0.0  39116  1788 ?        S    16:22   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/acces
admin     1572  0.0  0.0 208212  3280 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
admin     1574  0.0  0.0 124912  3320 ?        Sl   16:22   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gno
admin     1579  0.0  0.0 281768  3360 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
admin     1586  0.0  0.0 196048  2984 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
admin     1602  0.0  0.0 428948  3812 ?        Sl   16:22   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.1 /org/gtk
root      1608  0.0  0.3  88888 24992 ?        Ss   16:22   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/
root      1612  0.0  0.0  12788   844 hvc0     Ss+  16:22   0:00 /sbin/getty -L hvc0 9600 linux
root      1614  0.0  0.0  15820   964 tty1     Ss+  16:22   0:00 /sbin/getty -8 38400 tty1
root      1650  0.0  0.4 507280 37156 ?        S    16:22   0:00 samba -D
admin     1702  0.0  0.0  22784  4128 pts/1    Ss   16:22   0:00 -bash
root      1754  0.0  0.4 507324 37208 ?        S    16:23   0:00 samba -D
root      1756  0.0  0.4 507324 37096 ?        S    16:23   0:00 samba -D
root      1758  0.0  0.4 507324 36876 ?        S    16:23   0:00 samba -D
root      1763  0.0  0.4 507324 36876 ?        S    16:24   0:00 samba -D
root      1849  0.0  0.4 507248 37048 ?        S    16:25   0:00 samba -D
root      1851  0.0  0.4 507324 36892 ?        S    16:26   0:00 samba -D
root      1901  0.0  0.4 507324 37056 ?        S    16:26   0:00 samba -D
root      1902  0.0  0.4 507324 36864 ?        S    16:27   0:00 samba -D
root      2023  0.0  0.4 507324 36632 ?        S    16:29   0:00 samba -D
root      2110  0.0  0.4 507324 36892 ?        S    16:30   0:00 samba -D
root      2111  0.0  0.4 507324 36888 ?        S    16:30   0:00 samba -D
root      2219  0.0  0.4 507324 36868 ?        S    16:31   0:00 samba -D
admin     2386 30.4  0.0  32832  2580 ?        SN   16:32   0:48 fiberlamp -root
root      2387  0.0  0.4 507248 35612 ?        S    16:32   0:00 samba -D
root      2510  0.0  0.0   4344   360 ?        S    16:34   0:00 sleep 60
admin     2514  0.0  0.0  18448  1312 pts/1    R+   16:35   0:00 ps aux

```

---

### Post by bab1 on 2014-12-15
> **Adunamia said:**
> ```
pgrep -l mbd
```
does not return anything


Pgrep should have returned something.  Since you are using Samba4 as a DC you are not using *smbd* for sharing, but you should still be running *nmbd*.  I believe you should have seen at least something like this```
$ pgrep -l mbd
918 nmbd

```
> 

however, if I try to manually start the services....
```
$ sudo service smbd start
smbd start/running, process 2230
$ sudo service nmbd start
start: Job is already running: nmbd
$ sudo service smbd start
smbd start/running, process 2341

```

smbd does not seem to stay running, but if I look at the logs, the only complaint is:
```
[2014/12/15 16:19:12.644526,  0] ../source3/smbd/server.c:1250(main)
  server role = 'active directory domain controller' not compatible with running smbd standalone.
  You should start 'samba' instead, and it will control starting smbd if required
[2014/12/15 16:19:12,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.

```
Due to you running Samba4 as a DC.  Is this host the DC for the entire network; or do you have a Windows Server running as the DC for all the logins and DNS etc.?> 

ps aux shows:
```
root         1  0.4  0.0  33640  2960 ?        Ss   16:22   0:03 /sbin/init
root      1304  0.0  0.4 507272 37740 ?        S    16:22   0:00 samba -D
root      1305  0.0  0.4 500524 34884 ?        S    16:22   0:00 samba -D
root      1306  0.0  0.3 496372 32384 ?        S    16:22   0:00 samba -D
root      1307  0.1  0.4 507496 37904 ?        S    16:22   0:01 samba -D
root      1308  0.0  0.4 496372 34016 ?        S    16:22   0:00 samba -D
root      1309  0.0  0.4 506804 36556 ?        S    16:22   0:00 samba -D
root      1310  0.0  0.4 496372 33888 ?        S    16:22   0:00 samba -D
root      1311  0.0  0.3 496372 32552 ?        S    16:22   0:00 samba -D
root      1312  0.0  0.4 499200 34152 ?        S    16:22   0:00 samba -D
root      1313  0.0  0.5 496372 41280 ?        S    16:22   0:00 samba -D
root      1314  0.0  0.4 496372 33444 ?        S    16:22   0:00 samba -D


See if the nmbd daemon is running with this command[CODE] ps aux|grep nmbd
```


[COLOR="#0000FF"]Edit: I think before we go any further I need to know whether you are provisioning Samba4 to be the domain AD-DC for this network.  There are multiple smb.conf files and 2 distinct methods for managing samba shares (smbd-nmbd or samba).

Is this a AD-DC for a domain or a standalone member server in an existing domain?[/COLOR]-

---

### Post by Adunamia on 2014-12-17
Samba is acting as the AD DC for the network. There are no other windows servers on the network currently.
```
 ps aux|grep nmbd
```
Only returns the grep process.

---

### Post by bab1 on 2014-12-17
> **Adunamia said:**
> Samba is acting as the AD DC for the network. There are no other windows servers on the network currently.
```
 ps aux|grep nmbd
```
Only returns the grep process.

It turns out that this is correct for a Samba4 AD-DC installation.  No *smbd* and no *nmbd*.  When using Samba4 as a AD-DC the server process (daemon) used is *samba*.  You saw as ***samba -D***.  This daemon is still a work in progress.  Although it will eventually replace all the functions of the earlier Samba3 daemons *smbd* and *nmbd*, at the present time it does not.  No browsing for shares with the daemon *samba -D*.

If you absolutely need to be able to browse to the shares you have created then you will need to add a separate Samba4 member server and run smbd/nmbd or use a Windows machine to host the shares.  You should never have the Samba AD-DC server win any MB elections as it has no browsing support at this time.  WINS is another story.  It's unclear to me as to whether it is needed for Windows 7 or 8.  If WINS is needed you should add that to the Samba4 member server not the AD-DC server.

You can read about this at:
[https://wiki.samba.org/index.php/Samba_4.x_Readme_First]("https://wiki.samba.org/index.php/Samba_4.x_Readme_First")

[https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server]("https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server")

---

### Post by Adunamia on 2014-12-17
The way I read it, it sounds as if the functions of the nmbd daemon are built into the samba process. It doesn't (as far as I saw) state that browsing isn't supported, but that nmbd browsing would cause duplicate thread issues. It did state that only some of these features are included (wasn't very specific), but browsing works just fine within about 24-48 hours of an ipconfig /release /renew, so browsing seems to be supported in some capacity; maybe I'm missing something here? I doubt you would be privy to exactly which features of the nmbd daemon are or are not supported, but something seems off here. 

edit:
After thinking about the fact that the nmbd daemon technically shouldn't be running, but will be handled by the samba process, I stopped the service. Typically, a ipconfig /release /renew would be needed on the client PC to have browsing work again, but after killing the nmbd process on the server and refreshing the share on the client, it resolves properly. The DC still does not show up in net view or smbtree, but the network discovery is not of concern to me so long as the name resolves properly. Most configuration tutorials show manual start/stop of the nmbd service, so I wouldn't be surprised if it was often getting started while setting up/troubleshooting issues. I'm going to make sure nmbd isn't launched manually for a while and see if that fixes the main issue (name not resolving properly). If push comes to shove, I can set a cron job to kill it every so often. I'll play around with this to see if it holds water and post back in a few days. Thanks for all the help so far, bab1!

---

### Post by Adunamia on 2014-12-19
It's looking like this has resolved the issue. Without waiting weeks to post back, I would typically be seeing issues by now. The DC still does not show up in net view/smbtree, but that isn't an issue for the environment here. Thanks again for the help BAB1! I was starting to pull my hair out and it was awesome to get a second (better) pair of eyes on it.

To summarize for anyone who may stumble across this in the future:
If samba is acting as an AD DC, launching the nmbd service manually will cause issues (same goes for any samba service other than samba itself). Stopping the service will allow clients to browse by host name successfully.

---

