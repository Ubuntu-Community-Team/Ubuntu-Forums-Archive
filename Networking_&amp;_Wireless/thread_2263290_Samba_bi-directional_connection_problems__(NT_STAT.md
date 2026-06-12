---
title: "Samba bi-directional connection problems  (NT_STATUS_ACCESS_DENIED)"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by cjsmall on 2015-01-30
Ubuntu 14.10 server with Xfce4 desktop additions, the Nemo file manager and the current samba 2.4.1.11

There are many other posts here and across the internet that describe similar samba problems.  However, I have not found any helpful information there that addressed my particular issues.

I have attempted to configure samba on this system with little success.  My little network consists of:

  * This Ubuntu server  (**UB**)
  * A Sun Server running Solaris 10 and samba 3.6.5  (**SUN**)
  * A Windows XP machine  (**XP**)
  * A Windows 7 machine  (**W7**)

The **XP** and **W7** machines can access shares on each other and both can access the samba shares on the SUN.

After configuring samba on this **UB** sysem, I can access shares on the **SUN** and **XP** , but when attempting to connect to **W7** the logon dialog is displayed.  The username, Domain (WORKGROUP) and Password are entered and the Connect button pressed.  Moments later this dialog is redisplayed.  It will not connect.  Attempts to connect to **UB** itself result in an error: [I]"Unable to mount location; Failed to retreive share list from server.  Connection timed out."
[/I]
Attempts to access **UB** from **W7** result in error: *"Windows cannot access \\UB"*
Attempts to access **UB** from **XP** result in error: *"\\UB is not accessible"*

smbpasswd has been used to set passwords which match the login on all systems.

Now the details:

```
# smbstatus

Samba version 4.1.11-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED

Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

No locked files
```

```
# smbclient -L localhost
Enter jeff's password: 
session setup failed: NT_STATUS_UNSUCCESSFUL
```

```
Excerpts from /var/log/samba/log.samba

  STATUS=daemon 'nmbd' finished starting up and ready to serve connectionsGot SIGTERM: going down...
  STATUS=daemon 'winbindd' finished starting up and ready to serve connectionsGot sig[15] terminate (is_parent=1)
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsFailed to delete pidfile /var/run/samba/smbd.pid. Error was No such file or directory
[2015/01/30 13:38:32.067923,  0] ../source3/smbd/server.c:1289(main)
  standard input is not a socket, assuming -D option
[2015/01/30 13:38:32.082167,  0] ../lib/util/become_daemon.c:136(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsUnable to connect to CUPS server localhost:631 - Bad file descriptor
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsfailed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2015/01/30 13:38:32.108730,  0] ../lib/util/become_daemon.c:136(daemon_ready)
[2015/01/30 13:38:32.108796,  0] ../source3/winbindd/winbindd_cache.c:3196(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 2
[2015/01/30 13:38:32.145121,  0] ../lib/util/become_daemon.c:136(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsDenied connection from 204.107.91.2 (204.107.91.2)
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsDenied connection from 204.107.91.2 (204.107.91.2)
  STATUS=daemon 'smbd' finished starting up and ready to serve connectionsDenied connection from 204.107.91.2 (204.107.91.2)
  [....]
```

```
# ps -ef | grep mbd
root     32508     1  0 16:26 ?        00:00:00 nmbd -D
root     32518     1  0 16:26 ?        00:00:00 smbd -F
root     32534 32518  0 16:26 ?        00:00:00 smbd -F
```

Note that **smbd** is being started in foreground rather than background.  I'm puzzled by this.  All nmbd and smbd processes are started as daemons (**-D**) on the **SUN** system.

Here is the content of the /etc/samba/smb.conf file.  I have eliminated a few shares since they are all similar.

```
###############################################################################
# FILE:         smb.conf
#
# DESCRIPTION:  Samba configuration file for dymaxion
#
# REVISION:     Original coding  01-21-15  jeff@cjsa.com
#               Latest revision  01-30-15  jeff@cjsa.com
#
# NOTES:        * See the manual page: smb.conf(5)
#
#               * Lines beginning with '#' or ';' are ignored.
#
#               * After modifications, use testparm to check file syntax.
#
#               * The "use client driver = yes" line in the printers section
#                 resolves the "access denied" message you see in the printer
#                 queue, which makes it impossible to manage jobs from the
#                 Windows XP system.
#
#               * After modifying this file, as root issue the following cmd:
#
#                       service samba restart
#
###############################################################################

[global]
    netbios name                = dymmaxion
    workgroup                   = WORKGROUP

    client lanman auth          = no
    client NTLMv2 auth          = yes
    client plaintext auth       = no
    lanman auth                 = no
    ntlm auth                   = yes

    allow trusted domains       = no
    bind interfaces only        = yes
    client schannel             = no
    client signing              = no
    client use spnego           = no
    cups options                = raw
    disable netbios             = no
    dns proxy                   = no
    domain logons               = no
    domain master               = no
    encrypt passwords           = yes
    follow symlinks             = yes
    guest account               = smbguest
    guest ok                    = no
    hostname lookups            = no
    hosts allow                 = localhost, belvedere, dymaxion, dymaxion2, \
                                  ionic, organic, usonian, streamium, \
                                  receiver1, television1, bluray1, bluray2
    interfaces                  = 204.107.91.0/24  127.0.0.1/8  192.168.0.0/24
    load printers               = yes
    local master                = no
    lock directory              = /var/lock/samba
    log file                    = /var/log/samba/log.samba
    log level                   = 0
    machine password timeout    = 120
    map to guest                = bad user
    max connections             = 10
    max log size                = 1000
    message command             = sh -c 'xedit %s; rm -f %s' &
    name resolve order          = hosts lmhosts wins bcast
    nt pipe support             = yes
    nt status support           = yes
    obey pam restrictions       = yes
    pam password change         = no
    panic action                = /usr/share/samba/panic-action %d
    passdb backend              = tdbsam:/etc/samba/private/passdb.tdb
    passwd chat timeout         = 120
    preferred master            = no
    preserve case               = yes
    print command               = lp -s -c -d%p %s; rm %s
    printcap name               = cups
    printing                    = cups
    security                    = user
    #server role                        = auto
    server role                 = standalone server
    server schannel             = no
    server signing              = no
    server string               = Dymaxion Samba Server
    short preserve case         = yes
    socket options              = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    syslog                      = 0
    time server                 = no
    unix password sync          = no
    username level              = 0
    username map                = /etc/samba/smbusers
    wins proxy                  = no
    wins support                = no
    valid users                 = jeff, sherril
    #valid users                        = %S

[netlogon]
    available                   = yes
    browseable                  = yes
    comment                     = Network Logon Service
    guest ok                    = no
    locking                     = no
    path                        = /var/lib/samba/netlogon
    printable                   = no
    public                      = no
    read only                   = no
    strict locking              = no
    writable                    = no

[printers]
    browseable                  = no
    comment                     = All Printers
    create mask                 = 0700
    guest ok                    = no
    locking                     = no
    path                        = /var/spool/samba
    public                      = no
    printable                   = yes
    writeable                   = no

[root]
    browseable                  = yes
    comment                     = Root Directory
    dont descend                = /proc
    locking                     = no
    path                        = /
    public                      = no
    writeable                   = yes

[tmp]
    browseable                  = yes
    comment                     = Temporary File Space
    locking                     = no
    path                        = /tmp
    public                      = yes
    writeable                   = yes

[html]
    browseable                  = yes
    comment                     = Local WEB Pages
    create mask                 = 0755
    force user                  = jeff
    force group                 = cjs
    locking                     = no
    path                        = /var/www/html
    printable                   = no
    public                      = no
    write list                  = jeff, sherril
    writable                    = yes

[images]
    browseable                  = yes
    comment                     = Jeff's Pictures Directory
    create mask                 = 0755
    force user                  = jeff
    force group                 = cjs
    locking                     = no
    path                        = /u/jeff/Pictures
    printable                   = no
    public                      = no
    write list                  = jeff, sherril
    writable                    = yes

[jeff]
    browseable                  = yes
    comment                     = Jeff's Home Directory
    create mask                 = 0755
    force user                  = jeff
    force group                 = cjs
    locking                     = no
    path                        = /u/jeff
    printable                   = no
    public                      = no
    write list                  = jeff, sherril
    writable                    = yes

[lib]
    browseable                  = yes
    comment                     = Jeff's Library Directory
    create mask                 = 0755
    force user                  = jeff
    force group                 = cjs
    locking                     = no
    path                        = /u/jeff/lib
    printable                   = no
    public                      = no
    write list                  = jeff, sherril
    writable                    = yes

[proj]
    browseable                  = yes
    comment                     = Jeff's Projects Directory
    create mask                 = 0755
    force user                  = jeff
    force group                 = cjs
    locking                     = no
    path                        = /u/jeff/lib/proj
    printable                   = no
    public                      = no
    write list                  = jeff, sherril
    writable                    = yes
```

Any suggestions are greatly appreciated.

---

### Post by SeijiSensei on 2015-01-30
Did you create a Samba account for jeff using smbpasswd?

---

### Post by cjsmall on 2015-01-31
Yes.  There are only two active users on this LAN and I have created both users and reset the passwords with smbpasswd multiple times just to make sure that there wasn't an error there. 

One other thing that I should add for completeness is that when booting, there were two attempts to start SMB/CIFS, with the second failing:

```
Starting SMB/CIFS File and Active Directory Server[ OK ]
...
Starting SMB/CIFS File and Active Directory Server[fail]
```

Based upon this article: [http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04](http://askubuntu.com/questions/455418/samba-started-twice-on-boot-up-after-upgrade-to-14-04), I created the recommended **/etc/init/samba-ad-dc.override** file with "manual" as the content, which stops this system from acting as a directory and domain controller server.  This solved the boot message problem and has had no apparent effect, either pro or con, on the remainder of my issues. 

I'm also aware that I have a CUPS  problem, but I believe that that is related to CUPS configuration and has nothing to do with samba,

---

