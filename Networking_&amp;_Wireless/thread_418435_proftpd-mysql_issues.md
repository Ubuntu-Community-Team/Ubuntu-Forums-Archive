---
title: "proftpd-mysql issues"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Temujin_12 on 2007-04-22
I followed the tutorial at [http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting) to setup proftpd-mysql.  Instead of using ftpgroup and ftpuser, I used proftpd for both.  When I try to connect to the FTP server I get this in the log file:
```
Apr 22 08:28:34 rico proftpd[12007] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FTP session closed.
```
...and am unable to connect.

When I run proftpd using the following:
```
sudo proftpd -d 10 -c /etc/proftpd/proftpd.conf
```
...this is what appears in the log file:
```
Apr 22 08:13:34 rico proftpd[11691] localhost: ROOT PRIVS at mod_ctrls.c:1173
Apr 22 08:13:34 rico proftpd[11691] localhost: RELINQUISH PRIVS at mod_ctrls.c:1177
Apr 22 08:13:34 rico proftpd[11691] localhost: FS: using system lstat()
Apr 22 08:13:39 rico proftpd[11691] localhost: FS: using system lstat()
Apr 22 08:13:39 rico proftpd[11692] localhost: RELINQUISH PRIVS at main.c:1180
Apr 22 08:13:39 rico proftpd[11692] localhost: no matching vhost found for ::ffff:192.168.2.102#21, using DefaultServer 'rico'
Apr 22 08:13:39 rico proftpd[11691] localhost: FS: using system lstat()
Apr 22 08:13:39 rico proftpd[11691] localhost: FS: using system lstat()
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): ROOT PRIVS at main.c:1025
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): SETUP PRIVS at main.c:1030
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FTP session requested from unknown class
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): performing module session initializations
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): ROOT PRIVS at mod_quotatab.c:2329
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): RELINQUISH PRIVS at mod_quotatab.c:2336
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): ROOT PRIVS at mod_quotatab.c:2345
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): RELINQUISH PRIVS at mod_quotatab.c:2352
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): dispatching event 'core.exit' to core
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): dispatching event 'core.exit' to mod_delay
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): ROOT PRIVS at mod_delay.c:828
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FS: using system open()
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): RELINQUISH PRIVS at mod_delay.c:830
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): mod_delay/0.5: write-locking DelayTable '/var/run/proftpd/proftpd.delay'
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): mod_delay/0.5: mapping DelayTable '/var/run/proftpd/proftpd.delay' into memory
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): mod_delay/0.5: unmapping DelayTable '/var/run/proftpd/proftpd.delay' from memory
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): mod_delay/0.5: unlocking DelayTable '/var/run/proftpd/proftpd.delay'
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FS: using system write()
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FS: using system close()
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): dispatching event 'core.exit' to mod_ctrls
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): dispatching event 'core.exit' to mod_tls
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): dispatching event 'core.exit' to mod_quotatab
Apr 22 08:13:40 rico proftpd[11692] localhost (::ffff:192.168.2.188[::ffff:192.168.2.188]): FTP session closed.
```

Here's my my proftpd MySQL database:
```
mysql> select * from ftpgroup \G
*************************** 1. row ***************************
groupname: proftpd
      gid: 2001
  members: proftpd
1 row in set (0.00 sec)

mysql> select * from ftpuser \G
*************************** 1. row ***************************
      id: 1
  userid: nicole
  passwd: password
     uid: 2001
     gid: 2001
 homedir: /home/proftpd/nicole
   shell: /usr/sbin/nologin
   count: 0
accessed: 0000-00-00 00:00:00
modified: 0000-00-00 00:00:00
1 row in set (0.00 sec)

mysql> select * from ftpquotalimits \G
*************************** 1. row ***************************
            name: nicole
      quota_type: user
     per_session: true
      limit_type: hard
  bytes_in_avail: 3221225472
 bytes_out_avail: 0
bytes_xfer_avail: 0
  files_in_avail: 0
 files_out_avail: 0
files_xfer_avail: 0
1 row in set (0.00 sec)
mysql> select * from ftpquotatallies \G
Empty set (0.00 sec)

```

Here's the appropriate line in my /etc/passwd file:
```
proftpd:x:2001:2001::/var/run/proftpd:/bin/false
```

Here's the appropriate line in my /etc/group file:
```
proftpd:x:2001:
```

Here's the permissions of /home/proftpd:
```
drwxr-xr-x  2 proftpd proftpd 4096 2007-04-21 23:13 proftpd
```

And lastly, here's my proftpd.conf:
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName                      "rico"
ServerType                      standalone
DeferWelcome                    off

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

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           proftpd

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile                   off

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


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
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

DefaultRoot ~

# The passwords in MySQL are encrypted using CRYPT
SQLAuthTypes            Plaintext Crypt
SQLAuthenticate         users* groups*


# used to connect to the database
# databasename@host database_user user_password
SQLConnectInfo  proftpd@localhost proftpd db_password


# Here we tell ProFTPd the names of the database columns in the "usertable"
# we want it to interact with. Match the names with those in the db
SQLUserInfo     ftpuser userid passwd uid gid homedir shell

# Here we tell ProFTPd the names of the database columns in the "grouptable"
# we want it to interact with. Again the names match with those in the db
SQLGroupInfo    ftpgroup groupname gid members

# set min UID and GID - otherwise these are 999 each
SQLMinID        500

# create a user's home directory on demand if it doesn't exist
SQLHomedirOnDemand on

# Update count every time user logs in
SQLLog PASS updatecount
SQLNamedQuery updatecount UPDATE "count=count+1, accessed=now() WHERE userid='%u'" ftpuser

# Update modified everytime user uploads or deletes a file
SQLLog  STOR,DELE modified
SQLNamedQuery modified UPDATE "modified=now() WHERE userid='%u'" ftpuser

# User quotas
# ===========
QuotaEngine on
QuotaDirectoryTally on
QuotaDisplayUnits Mb
QuotaShowQuotas on

SQLNamedQuery get-quota-limit SELECT "name, quota_type, per_session, limit_type, bytes_in_avail, bytes_out_avail, bytes_xfer_avail, files_in_avail, files_out_avail, files_xfer_avail FROM ftpquotalimits WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery get-quota-tally SELECT "name, quota_type, bytes_in_used, bytes_out_used, bytes_xfer_used, files_in_used, files_out_used, files_xfer_used FROM ftpquotatallies WHERE name = '%{0}' AND quota_type = '%{1}'"

SQLNamedQuery update-quota-tally UPDATE "bytes_in_used = bytes_in_used + %{0}, bytes_out_used = bytes_out_used + %{1}, bytes_xfer_used = bytes_xfer_used + %{2}, files_in_used = files_in_used + %{3}, files_out_used = files_out_used + %{4}, files_xfer_used = files_xfer_used + %{5} WHERE name = '%{6}' AND quota_type = '%{7}'" ftpquotatallies

SQLNamedQuery insert-quota-tally INSERT "%{0}, %{1}, %{2}, %{3}, %{4}, %{5}, %{6}, %{7}" ftpquotatallies

QuotaLimitTable sql:/get-quota-limit
QuotaTallyTable sql:/get-quota-tally/update-quota-tally/insert-quota-tally

RootLogin off
RequireValidShell off
```

And yes, I can connect to the proftpd database using 'mysql -u proftpd -p proftpd'.

I hope this information isn't too overwhelming.  I just want to make sure I provide as much information as I can to minimize any back and forth.

Any help would be greatly appreciated.  Thanks!

EDIT:
Oh yea, and here's the output of 'sudo proftpd -td5':
```
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - parsing '/etc/proftpd/modules.conf' configuration
 - mod_tls/2.1.1: using OpenSSL 0.9.8b 04 May 2006
 - DenyFilter: compiling deny regex '\*.*/'
 - <IfModule>: using 'mod_tls.c' section at line 65
 - <IfModule>: skipping 'mod_quota.c' section at line 69
 - <IfModule>: skipping 'mod_ratio.c' section at line 73
 - <IfModule>: using 'mod_delay.c' section at line 81
 - <IfModule>: using 'mod_ctrls.c' section at line 85
 - mod_ctrls/0.9.4: closing ctrls socket '/var/run/proftpd/proftpd.sock' (3)
 - <IfModule>: skipping 'mod_ctrls_admin.c' section at line 93
 - SQLAuthenticate: use of * in SQLAuthenticate has been deprecated.  Use AuthOrder for setting authoritativeness
 - SQLAuthenticate: use of * in SQLAuthenticate has been deprecated.  Use AuthOrder for setting authoritativeness
 - IPv6 getaddrinfo 'rico' error: Name or service not known
localhost -
localhost - Config for rico:
localhost - DeferWelcome
localhost - DefaultServer
localhost - ShowSymlinks
localhost - TimeoutNoTransfer
localhost - TimeoutStalled
localhost - TimeoutIdle
localhost - DisplayLogin
localhost - DisplayFirstChdir
localhost - ListOptions
localhost - DenyFilter
localhost - UserID
localhost - UserName
localhost - GroupID
localhost - GroupName
localhost - Umask
localhost - DirUmask
localhost - AllowOverwrite
localhost - TransferLog
localhost - TLSEngine
localhost - DelayEngine
localhost - DefaultRoot
localhost - SQLAuthTypes
localhost - SQLAuthenticate
localhost - SQLConnectInfo
localhost - SQLUserTable
localhost - SQLUsernameField
localhost - SQLPasswordField
localhost - SQLUidField
localhost - SQLGidField
localhost - SQLHomedirField
localhost - SQLShellField
localhost - SQLGroupTable
localhost - SQLGroupnameField
localhost - SQLGroupGIDField
localhost - SQLGroupMembersField
localhost - SQLMinID
localhost - SQLHomedirOnDemand
localhost - SQLLog_PASS
localhost - SQLNamedQuery_updatecount
localhost - SQLLog_STOR
localhost - SQLLog_DELE
localhost - SQLNamedQuery_modified
localhost - QuotaEngine
localhost - QuotaDirectoryTally
localhost - QuotaDisplayUnits
localhost - QuotaShowQuotas
localhost - SQLNamedQuery_get-quota-limit
localhost - SQLNamedQuery_get-quota-tally
localhost - SQLNamedQuery_update-quota-tally
localhost - SQLNamedQuery_insert-quota-tally
localhost - QuotaLimitTable
localhost - QuotaTallyTable
localhost - RootLogin
localhost - RequireValidShell
localhost - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
Syntax check complete.
```

---

### Post by Temujin_12 on 2007-04-23
Anyone have an idea what might be going on with this?

---

### Post by Temujin_12 on 2007-04-23
I figured out what the problem was (after reading [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-SQL.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-SQL.html)).  I needed a different value for passwd.  I used the following to generate the passwd to insert into the database:
```
/bin/echo "{sha1}"`/bin/echo -n "password" | openssl dgst -binary -sha1 | openssl enc -base64`
```.

...changed the length of the passwd field to allow for longer hashes:
```
alter table ftpuser change passwd passwd varchar(100) not null;
```

...then inserted it:
```
update ftpuser set passwd = "{sha1}W6ph5Mm5Pz8GgiULbPgzG37mj9g=" where userid = 'nicole';
```

...and changed SQLAuthTypes to the following:
```
SQLAuthTypes            OpenSSL
```

After that, everything works fine.

HOWEVER, now I'm running into the problem where I can access the FTP server just fine from the local network, but cannot from an external network.

After researching this for several hours here are the changes that I've made to proftpd.conf:
```
MasqueradeAddress               mydyndns.homelinux.com
MasqueradeAddress               MY.WAN.IP.ADDRESS
MasqueradeAddress               192.168.2.102

PassivePorts                    60000 60100
```

In my router I've added persistent port forwarding for ports 20-21 and 60000-60100 (on TCP) and pointed all of them to the internal IP address (192.168.2.102).

After doing so, everything works fine internally (no change there), but when I access it from an external network, it stalls when trying to do a directory listing.  I've even gone into the FTP client program (FileZilla) and specified which passive ports to use (60000-60100) and packet traces seem to verify that it is using random ports within that range.

If I try to FTP in using 'ftp' from the command line I can log in, print the current working directory (which is '/'), and change to passive mode.  But as soon as I try 'ls' or 'dir' (before or after entering passive mode) things hang (client-side).

Anyone have any ideas what may be going on?

---

