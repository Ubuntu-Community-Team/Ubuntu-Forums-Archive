---
title: "Samba smbd service not running"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by koozoop on 2015-07-25
Hello. I'm new to linux and I've come across a problem with samba installation. I installed lubuntu 14.04 on a pc to use as media server. Everything runs fine apart from samba. When I first installed samba everything went smooth. I created a user with password, shares etc and I could access my files through samba from my windows 7 pc and my android tv box. Two days ago I noticed that samba service was not running anymore. The 
> pgrep -l mbd output is > 2016 nmbd process only. From webmin I can see YES/YES on nmbd start at boot/running now but YES/NO on smbd and samba-ad-dc. When I CLI > service smbd restart I get > stop: Unknown instance:
smbd start/running, process 20094 but service will not start. 

My /etc/samba/smb.conf is:


> [global]

    workgroup = kzoophome

    server string = Media Server

    security = user
    map to guest = Bad User

    log file = /var/log/samba/%m.log

    max log size = 50


    interfaces = 192.168.157.126/24


    dns proxy = no
    username map = /etc/samba/smbusers
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody


[movies]
    path = /media/movies
    guest ok = yes
    only guest = yes
    writeable = yes
;    browseable = yes


[printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
;    guest ok = no
;    read only = yes
    create mask = 0700


Any help would be appreciated. Thank u in advance!

---

### Post by bab1 on 2015-07-25
> **koozoop said:**
> ```
service smbd restart 
```
When I CLI  I get  but service will not start. 


Only root can restart smbd.  Try this```
sudo service smbd restart
```
Or if the process is not running at all use this```
sudo service smbd start
```

---

### Post by koozoop on 2015-07-25
Sorry, I forgot to mention that before any command I issue I sudo su. Thanks for the response anyway!

---

### Post by koozoop on 2015-08-03
Still haven't managed it... Any ideas?

---

### Post by bab1 on 2015-08-03
> **koozoop said:**
> Still haven't managed it... Any ideas?
Are you asking for guesses????

What have you tried?  What errors show up in the error logs (at /var/log/)?  Is the machine wired or wireless?  Are you sure you have connectivity with the network.  Samba is very stable.  The smbd/nmbd daemons don't usually die from internal to the service problems after a successful installation.

---

### Post by koozoop on 2015-08-04
Hello again. Thank you for your patience. The outcome of ***pgrep -l mbd ***and* **service smbd restart ***is the same as above (first post). Only ***nmbd*** process running. The output of /var/log/samba/smbd.log is:

[TABLE="width: 500"]
[TR]
[TD][2015/08/04 13:07:49.634497,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/08/04 13:07:49.642962,  0] ../source3/auth/auth_util.c:786(get_guest_info3)
  SamInfo3_for_guest: Unable to locate guest account [nobody]!
[2015/08/04 13:07:49.643207,  0] ../source3/auth/auth_util.c:855(make_new_session_info_guest)
  get_guest_info3 failed with NT_STATUS_NO_SUCH_USER
[2015/08/04 13:07:49.643350,  0] ../source3/smbd/server.c:1448(main)
  ERROR: failed to setup guest info.
[/TD]
[/TR]
[/TABLE]
(it is a repeating pattern so I'm posting the last lines...) It is a wired network and samba was successfully installed and used to work just fine for the first days between my android kodi box, my windows pc and the ubuntu server.

---

### Post by bab1 on 2015-08-04
> **koozoop said:**
> Hello again. Thank you for your patience. The outcome of ***pgrep -l mbd ***and* **service smbd restart ***is the same as above (first post). Only ***nmbd*** process running. The output of /var/log/samba/smbd.log is:

[TABLE="width: 500"]
[TR]
[TD][2015/08/04 13:07:49.634497,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[COLOR="#FF0000"][B][2015/08/04 13:07:49.642962,  0] ../source3/auth/auth_util.c:786(get_guest_info3)
  SamInfo3_for_guest: Unable to locate guest account [nobody]!
[2015/08/04 13:07:49.643207,  0] ../source3/auth/auth_util.c:855(make_new_session_info_guest)
  get_guest_info3 failed with NT_STATUS_NO_SUCH_USER
[2015/08/04 13:07:49.643350,  0] ../source3/smbd/server.c:1448(main)
  ERROR: failed to setup guest info.[/B][/COLOR]
[/TD]
[/TR]
[/TABLE]
(it is a repeating pattern so I'm posting the last lines...) It is a wired network and samba was successfully installed and used to work just fine for the first days between my android kodi box, my windows pc and the ubuntu server.
Please post the output of text data using the [noparse]```

```[/noparse] code blocks.  The easiest way is to click on the [SIZE=6]** # **[/SIZE] icon at the top of the advanced editor and place the data in between the code blocks.

I think the error (in red) that you show should be addressed. 

Post the complete output of  this command (you may have to scroll back to get it all)```
testparm -sv
```

Let's also make sure that there is a user ***nobody ***.  Post the output of this```
getent passwd nobody
```...and this too```
sudo pdbedit -L 
```

Also one last command to see if smbd is really dead.  Post the output of this (when smbd has failed)```
ps -ef | grep mbd
```

---

### Post by koozoop on 2015-08-05
The output of ***testparm -sv***:

```
**> testparm -sv**
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[movies]"
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    dos charset = CP850
    unix charset = UTF-8
    workgroup = KZOOPHOME
    realm = 
    netbios name = LNX-HOMESERVER
    netbios aliases = 
    netbios scope = 
    server string = Media Server
    interfaces = 192.168.157.126/24
    bind interfaces only = No
    server role = auto
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
    passdb backend = tdbsam
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
    username map = /etc/samba/smbusers
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
    log file = /var/log/samba/%m.log
    max log size = 50
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
    name resolve order = lmhosts, wins, host, bcast
    max ttl = 259200
    max wins ttl = 518400
    min wins ttl = 21600
    time server = No
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
    os level = 20
    lm announce = Auto
    lm interval = 60
    preferred master = No
    local master = Yes
    domain master = Auto
    browse list = Yes
    enhanced browsing = Yes
    dns proxy = No
    wins proxy = No
    wins server = 
    wins support = No
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
    server services = 
    dcerpc endpoint servers = 
    spn update command = 
    share backend = 
    tls enabled = No
    tls keyfile = 
    tls certfile = 
    tls cafile = 
    tls crlfile = 
    tls dh params file = 
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
    map archive = Yes
    map hidden = No
    map system = No
    map readonly = yes
    mangled names = Yes
    store dos attributes = No
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
    vfs objects = 
    msdfs root = No
    msdfs proxy = 
    ntvfs handler = 

[movies]
    path = /media/movies
    read only = No
    guest only = Yes
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No
```
***getent passwd nobody ***gives no output,

***pdbedit -L*** output:

```
**> sudo pdbedit -L**
koozoop:1000:koozoop
```

and finally the output of ***ps -ef | grep mbd***: 

```
**> ps -ef | grep mbd**
root      1976     1  0 Aug04 ?        00:00:01 nmbd -D
root     28738 28473  0 16:08 ?        00:00:00 sh -c (ps -ef | grep mbd) 2>&1
root     28742 28738  0 16:08 ?        00:00:00 sh -c (ps -ef | grep mbd) 2>&1
root     28744 28742  0 16:08 ?        00:00:00 grep mbd
```

---

### Post by bab1 on 2015-08-05
> **koozoop said:**
> The output of ***testparm -sv***:

```
map to guest = Bad User
guest account = nobody
/CODE]
***getent passwd nobody ***gives no output,

This is part of the problem.  It is bigger than just Samba.  The user *nobody * is a Linux system user.  The output of the above command should return this[CODE]$ getent passwd nobody
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
```
This user is always uid=65534:gid=65534.  This is the last number in the 16bit sequence that holds all users.  This user added on all Ubuntu installs by default.  If you don't have this user lots of processes will fail.  I would add this to the /etc/paswd file.  I usually edit this file manually, but if you are uncomfortable doing that, you can use the scripts the act on the /etc/passwd (e.g. adduser or useradd).

I noticed you modified the smb.conf file.  Most installs can just use the default smb.conf with changes such as *netbios name* and* workgroup name*.  Then you can just add the shares you need.  I would suggest reverting to that configuration.> 

... the output of ***ps -ef | grep mbd***: 

```
**> ps -ef | grep mbd**
root      1976     1  0 Aug04 ?        00:00:01 nmbd -D
[COLOR="#FF0000"][B]root     28738 28473  0 16:08 ?        00:00:00 sh -c (ps -ef | grep mbd) 2>&1
root     28742 28738  0 16:08 ?        00:00:00 sh -c (ps -ef | grep mbd) 2>&1[/B][/COLOR]
root     28744 28742  0 16:08 ?        00:00:00 grep mbd
```
What is the above in red?

In the end I think if you add the user nobody back to the /etc/passwd file and use the default smb.conf file with just the changes I have outlined you will be successful in running Samba (smbd).

---

### Post by koozoop on 2015-08-06
The pseudo user ***nobody*** was the problem! Everything works as intended after I added ***nobody*** to ***/etc/passwd*** and samba service is running just fine! 

Thank u for your help bab1!

---

### Post by bab1 on 2015-08-06
> **koozoop said:**
> The pseudo user ***nobody*** was the problem! Everything works as intended after I added ***nobody*** to ***/etc/passwd*** and samba service is running just fine! 

Thank u for your help bab1!

Understand that this is not a "pseudo user".  It is a system user.  This means it has no interactive login.  Other than that the user performs just as any other user other than the root user, which has special powers.  The other types of users are:  The root user (uid=0) and mortal users (humans that have an interactive login).  Glad I could help you cure the problem.  I still wonder how the user ***nobody*** got deleted.

---

### Post by koozoop on 2015-08-06
Maybe it had something to do with my owncloud setup. I will try to reproduce the installation steps on a virtual machine and see if sth goes wrong...

Many thanks!

---

