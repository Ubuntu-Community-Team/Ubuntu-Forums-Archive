---
title: "ProFTPD-MySQL Internal/External Network Question"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Temujin_12 on 2007-04-24
First off, I installed proftpd following these how to's:
[http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html)

I'm running into the problem where I can access the FTP server just fine from the local network, but cannot from an external network.

Here's my proftpd.conf:
```
Include /etc/proftpd/modules.conf
ServerName                      "rico"
ServerType                      standalone
DeferWelcome                    off
UseReverseDNS                   off
IdentLookups                    off
MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on
TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200
DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"
DenyFilter                      \*.*/
Port                            21
MasqueradeAddress               dyndnsaddress.homelinux.com
PassivePorts                    60000 60100
MaxInstances                    30
User                            proftpd
Group                           proftpd
Umask                           002  002
AllowOverwrite                  on
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
  TLSEngine off
</IfModule>

<IfModule mod_quota.c>
  QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
  Ratios on
</IfModule>

<IfModule mod_delay.c>
  DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
  ControlsEngine        on
  ControlsMaxClients    2
  ControlsLog           /var/log/proftpd/controls.log
  ControlsInterval      5
  ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
  AdminControlsEngine on
</IfModule>

RootLogin off
RequireValidShell off

# mysql config below here, as per http://www.howtoforge.com/proftpd_mysql_virtual_hosting ...

```

In my router I've added persistent port forwarding for ports 20-21 and 60000-60100 (on TCP) and pointed all of them to the internal IP address (192.168.2.102).

I can log in from the internal network and do a directory listing, but only BEFORE entering passive mode. When I access it from an external network, it stalls when trying to do a directory listing (before or after entering passive mode). I've even gone into the FTP client program (FileZilla) and specified which passive ports to use (60000-60100) and packet traces seem to verify that it is using random ports within that range.

If I try to FTP in from an external network using 'ftp' from the command line I can log in, print the current working directory (which is '/'), and change to passive mode. But as soon as I try 'ls' or 'dir' (before or after entering passive mode) things hang (client-side).

Here's the FileZilla log:
```
Status:	Connected
Trace:	FtpControlSocket.cpp(3986): ResetOperation(1)  OpMode=1 OpState=-13   caller=0x003ead04
Trace:	FtpControlSocket.cpp(1213): List(FALSE,0,"","",1)  OpMode=0 OpState=-1   caller=0x003ead04
Status:	Retrieving directory listing...
Command:	PWD
Trace:	FtpControlSocket.cpp(823): OnReceive(0)  OpMode=4 OpState=0   caller=0x003ead04
Response:	257 "/" is current directory.
Trace:	FtpControlSocket.cpp(1213): List(FALSE,0,"","",0)  OpMode=4 OpState=0   caller=0x003ead04
Command:	TYPE A
Trace:	FtpControlSocket.cpp(823): OnReceive(0)  OpMode=4 OpState=8   caller=0x003ead04
Response:	200 Type set to A
Trace:	FtpControlSocket.cpp(1213): List(FALSE,0,"","",0)  OpMode=4 OpState=8   caller=0x003ead04
Command:	PASV
```

It never progresses beyond 'Command: PASV'

On the server-side, when I'm running proftpd using 'proftpd -d 10 -c /etc/proftpd/proftpd.conf', this is the relevant output:
```
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching CMD command 'PWD' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): in dir_check_full(): path = '/', fullpath = '/home/proftpd/userdir/'.
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): FS: using system stat()
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): FS: using system stat()
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching POST_CMD command 'PWD' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'PWD' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'PWD' to mod_log
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'TYPE A' to mod_rewrite
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'TYPE A' to mod_tls
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'TYPE A' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'TYPE A' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching CMD command 'TYPE A' to mod_xfer
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching POST_CMD command 'TYPE A' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'TYPE A' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'TYPE A' to mod_log
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'PASV' to mod_rewrite
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'PASV' to mod_tls
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'PASV' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching PRE_CMD command 'PASV' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching CMD command 'PASV' to mod_core
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): in dir_check_full(): path = '/', fullpath = '/home/proftpd/userdir/'.
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): FS: using system stat()
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): FS: using system stat()
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): error setting IPV6_V6ONLY: Protocol not available
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): Entering Passive Mode (WAN,ID,ADD,RES,234,114).
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching POST_CMD command 'PASV' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'PASV' to mod_sql
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): dispatching LOG_CMD command 'PASV' to mod_log
Apr 24 08:56:33 rico proftpd[6535] localhost: FS: using system lstat()
Apr 24 08:56:38 rico proftpd[6535] localhost: FS: using system lstat()

```

After this, 'localhost: FS: using system lstat()' will continue to repeat with no further communication between client-server.

Note that the following from the server log:
```
Apr 24 07:56:30 rico proftpd[6554] localhost (::ffff:CLI.ENT.IP.ADDR[::ffff:CLI.ENT.IP.ADDR]): Entering Passive Mode (WAN,ID,ADD,RES,234,114).
```
...seems to indicate that it is respecting the PassivePorts directive as 234 * 256 + 114 = 60018 (which is within the specified 60000-60100 range).

I tried adding VirtualHost directives to respond to the internal IP (192.168.2.102), as per  the last question-answer at [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html), by adding the following:
```
# Note that your LAN address should be used here
<VirtualHost 192.168.2.102>
  ServerName "Some Other Server Name"

  # Note that there is no MasqueradeAddress directive
  # used in this section!
</VirtualHost>
```
...but this causes login errors (passwords are rejected).  If adding this VirtualHost directive is the answer, what other config options do I need to add INSIDE the directive?

Any help is greatly appreciated.

---

