---
title: "file sharing ubuntu -lubuntu"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by ryan138 on 2015-02-04
Hi everyone,

I am new and was wondering if anyone can answer the following questions?
1. Ubuntu works fine out of the box sharing files with windows. Why does Lubuntu not?
2. Is it specific packages that are needed?
3. Is it a difference because lubuntu uses pcfman and Ubuntu does not?

Thank you in advance and sorry if this has been asked before.

Ryan

---

### Post by bab1 on 2015-02-05
> **ryan138 said:**
> Hi everyone,

I am new and was wondering if anyone can answer the following questions?
1. Ubuntu works fine out of the box sharing files with windows. Why does Lubuntu not?
2. Is it specific packages that are needed?
3. Is it a difference because lubuntu uses pcfman and Ubuntu does not?

Thank you in advance and sorry if this has been asked before.

Ryan
Ubuntu uses Unity which is built using Gnome libraries.  The file sharing is handled by Gnome's gvfs package.  The package named **gigolo** is available and should be used on Lubuntu for file sharing.

So the answers to your questions are:
1.  Lubuntu has no gvfs or application that uses gvfs installed

2. Gigolo

3. Yes (see above).

---

### Post by ryan138 on 2015-02-05
[QUOTE=bab1;13222343]Ubuntu uses Unity which is built using Gnome libraries.  The file sharing is handled by Gnome's gvfs package.  The package named **gigolo** is available and should be used on Lubuntu for file sharing.

So the answers to your questions are:
1.  Lubuntu has no gvfs or application that uses gvfs installed

2. Gigolo

3. Yes (see above).

I will give it a try.

Thank you

---

### Post by Morbius1 on 2015-02-05
>  1. Ubuntu works fine out of the box sharing files with windows. Why does Lubuntu not?
[COLOR=#0000cd]Are you trying to access someone else's share?[/COLOR]

PCManFM is a curious thing. It's missing a "Browse Network" bookmark. It's not that it can't browse the network it's just missing the bookmark. But you can create one: Go to the path bar in PCManFM and enter:
```
network:///
```
Then immediately go to Bookmarks > Add to Bookmarks and you will end up with a bookmark ( which you can rename to Browse Network if you wish ) on the left side panel.

[COLOR=#0000cd]Or are you trying to create a samba share within PCManFM?[/COLOR]

Nautius in Ubuntu has something called nautilus-share which does this. Lubuntu ( along with Xubuntu ) has no counterpart. 

So you can either  create "Classic" samba shares: [COLOR=#000000]You actually already have an application to do that already installed it's just hidden. Run this command:
```
shares-admin
```[/COLOR]
If you don't have samba installed it will prompt you to install it.

Or change PCManFM so that it can create a samba usershsare sorta kinda like nautilus does: [http://ubuntuforums.org/showthread.php?t=2257136](http://ubuntuforums.org/showthread.php?t=2257136)

---

### Post by ryan138 on 2015-02-05
> **ryan138 said:**
> [QUOTE=bab1;13222343]Ubuntu uses Unity which is built using Gnome libraries.  The file sharing is handled by Gnome's gvfs package.  The package named **gigolo** is available and should be used on Lubuntu for file sharing.

So the answers to your questions are:
1.  Lubuntu has no gvfs or application that uses gvfs installed

2. Gigolo

3. Yes (see above).

I will give it a try.

Thank you
Using Gigolo, I just cannot connect even using the IP of the window box < \\192.168.69.157\share> even though I know that share and security permissions are correct on the windows 7 box. It's like it does not like the password.

---

### Post by bab1 on 2015-02-05
> **ryan138 said:**
> [QUOTE=ryan138;13222354]
Using Gigolo, I just cannot connect even using the IP of the window box < \\192.168.69.157\share> even though I know that share and security permissions are correct on the windows 7 box. It's like it does not like the password.

Post the output of this terminal command```
smbclient -d3 -L 192.168.69.157
```

You can also use this command for diagnosis```
smbtree -d3
```

What I'm looking for is why you can't connect to the share.  It sounds like Gigolo shows the share.  Am I correct about that?

---

### Post by ryan138 on 2015-02-05
> **bab1 said:**
> [QUOTE=ryan138;13222707]

Post the output of this terminal command```
smbclient -d3 -L 192.168.69.157
```

You can also use this command for diagnosis```
smbtree -d3
```

What I'm looking for is why you can't connect to the share.  It sounds like Gigolo shows the share.  Am I correct about that?

No, Gigolo only sees floppy

I did make sure Samba was installed but the firwewall unlocking stummped me that I has seen mentioned in another post.

Here are the outputs for you. I ran both for you:

ryan@LXLE14:~$ smbclient -d3 -L 192.168.69.157
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: Can't determine ip for broadcast address 192.168.0.0/24
Client started (version 4.1.6-Ubuntu).
Enter ryan's password: 
Connecting to 192.168.69.157 at port 445
cli_session_setup: NT1 session setup failed: NT_STATUS_INVALID_PARAMETER
session setup failed: NT_STATUS_INVALID_PARAMETER
ryan@LXLE14:~$ 

==================================

ryan@LXLE14:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: Can't determine ip for broadcast address 192.168.0.0/24
Enter ryan's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa9320] mpx_fde[(nil)] fd[7] - disabling
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa9340] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa92a0] mpx_fde[(nil)] fd[7] - disabling
ryan@LXLE14:~$

---

### Post by ryan138 on 2015-02-05
Here is my ifconfig:

ryan@LXLE14:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:4f:62:92  
          inet addr:192.168.69.113  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe4f:6292/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37015799 (37.0 MB)  TX bytes:1561610 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936088 (1.9 MB)  TX bytes:1936088 (1.9 MB)

ryan@LXLE14:~$

---

### Post by bab1 on 2015-02-05
> **ryan138 said:**
> [QUOTE=bab1;13222715]

No, Gigolo only sees floppy

I did make sure Samba was installed but the firwewall unlocking stummped me that I has seen mentioned in another post.

Here are the outputs for you. I ran both for you:

```
ryan@LXLE14:~$ smbclient -d3 -L 192.168.69.157
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: Can't determine ip for broadcast address 192.168.0.0/24
Client started (version 4.1.6-Ubuntu).
Enter ryan's password: 
Connecting to 192.168.69.157 at port 445
cli_session_setup: NT1 session setup failed: NT_STATUS_INVALID_PARAMETER
session setup failed: NT_STATUS_INVALID_PARAMETER
ryan@LXLE14:~$ 
```


```
ryan@LXLE14:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: Can't determine ip for broadcast address 192.168.0.0/24
Enter ryan's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa9320] mpx_fde[(nil)] fd[7] - disabling
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa9340] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3473aa92a0] mpx_fde[(nil)] fd[7] - disabling
ryan@LXLE14:~$
```

It looks like the problem is not Gigolo.  Post the output of ```
cat /etc/samba/smb.conf
```

Please use the [noparse]```
  
```[/noparse] to contain the fixed width text formatting.  You can do this by clicking on the [SIZE=6]**#**[/SIZE] icon at the top  of the **Advanced Reply** editor and pasting the code inside the code blocks.

---

### Post by ryan138 on 2015-02-05
Here you go. I hope this is correct:

```
ryan@LXLE14:~$ cat /etc/samba/smb.conf

[global]
    netbios name = Samba24
    server string = Samba file and print server
    workgroup = workgroup
    security = user
    hosts allow = 127. 192.168.69.
    interfaces = 127.0.0.1/8 192.168.0.0/24
    bind interfaces only = yes
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = cups
;    load printers = yes
    cups options = raw
;    printing = cups
;    guest account = nobody
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 6
    password level = 6
    encrypt passwords = no
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
;    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
    username map = /etc/samba/smbusers
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
;    guest ok = no

[homes]
    comment = Home Directories
    path = /home
    valid users = %U
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/lib/samba/profiles
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /var/lib/samba/pdf-documents
    comment = Converted PDF Documents
    admin users = %U
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[share]
    path = /home/ryan/share
    writeable = yes
;    browseable = yes
    guest ok = yes
ryan@LXLE14:~$ 


```

---

### Post by bab1 on 2015-02-05
> **ryan138 said:**
> Here you go. I hope this is correct:

```
ryan@LXLE14:~$ cat /etc/samba/smb.conf

[global]
    netbios name = Samba24
    server string = Samba file and print server
    workgroup = workgroup
    security = user
    hosts allow = 127. 192.168.69.
    interfaces = 127.0.0.1/8 192.168.0.0/24
    bind interfaces only = yes
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = cups
;    load printers = yes
    cups options = raw
;    printing = cups
;    guest account = nobody
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 6
    password level = 6
    encrypt passwords = no
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
;    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
    username map = /etc/samba/smbusers
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
;    guest ok = no

[homes]
    comment = Home Directories
    path = /home
    valid users = %U
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/lib/samba/profiles
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /var/lib/samba/pdf-documents
    comment = Converted PDF Documents
    admin users = %U
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[share]
    path = /home/ryan/share
    writeable = yes
;    browseable = yes
    guest ok = yes
ryan@LXLE14:~$ 


```
Why the modified smb.conf file?  Why are you using winbind?  Is this host a NT4 style PDC?  The default smb.conf file with your shares at the bottom should work.

I would revert to the orignal smb.conf file and add one share to test the configuration.

---

### Post by ryan138 on 2015-02-05
When I opened the samba gui, it said it has to write to the file for some reason.

The winds server is a ClearOS box.

---

### Post by bab1 on 2015-02-05
> **ryan138 said:**
> When I opened the samba gui, it said it has to write to the file for some reason.
What does this mean?  Did you modify the smb.conf file?  Do you have the original smb.conf file?  Are you trying to create a PDC?  > 

The winds server is a ClearOS box.
What is a winds server?

---

### Post by ryan138 on 2015-02-06
sorry WINS server

---

### Post by bab1 on 2015-02-06
> **ryan138 said:**
> sorry WINS server
I assume you have no experience with directly editing the smb.conf file or what the "winbind" references in it are.

Are you running a multi segmented network (vlans or some such)?  WINS is an unnecessary complication in a simple LAN.  Your WINS configuration is  not correct at this point anyway.

Once again, I suggest you revert to the original (default) /etc/samba/smb.conf file for testing purposes.

---

### Post by ryan138 on 2015-02-07
Thank you for your help!
I did a clean install and did not bother adding the samba gui and all is working great now!
Thank you again!
Ryan

---

