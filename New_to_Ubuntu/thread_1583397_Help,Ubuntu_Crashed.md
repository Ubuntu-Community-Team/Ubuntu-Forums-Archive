---
title: "Help,Ubuntu Crashed"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by usualwyy on 2010-09-27
Ubuntu Crashed several times for unknow reasons :confused::confused::confused:

Condition:
when  or after operating(copy or move or backup) [COLOR=#000000]Large files

I think it must be kernel crashed, because Ctrl+SysRq+reisub didn't work anymore

[/COLOR]Hardware environment:
I5 450M + ATI HD5430(with official driver) + 320G ATA TOSHIBA + HM55 chipset

Software environment:
Ubuntu X86 X64

Waiting for kindly advice

thanks...

---

### Post by NightwishFan on 2010-09-27
Do a small thing for me:

Decribe what you are doing at the time of the crash, and things you noticed. Also upload /var/log/syslog here for us to peruse.

Hopefully we can help! :)

---

### Post by tedygram311 on 2010-09-27
Try booting from the disk.  See if you are able to move things there.  Then you could wipe your hard drive and attempt to go from there.  I would not do that immediately but that is an option.

---

### Post by jtarin on 2010-09-27
I use this for such things.It allows you to watch kernel messages> A nice trick is to pipe dmesg to tail to watch any message that comes to dmesg. To do this, issue the command dmesg | tail -f and the last few lines of dmesg will remain in your terminal. Every time a new entry arrives it will be at the bottom of the &#8220;tail.&#8221; Keep this window open when doing heavy duty system administration or debugging a system.

---

### Post by usualwyy on 2010-09-27
NightwishFan & tedygram311

Thank you two kindly guys really

I'm a newbie for Ubuntu

since I used Ubuntu last week,I got system crashed many times a day, even during I used live CD bakup

First time the Ubuntu crashed,I was browsing the web&#12290;I drew lesson from this,and after the first time crashed,I didn't do anything during file operating at all, but it still crashed,and I found when I operating large files,it happens 100% and never missed

The files I operated is about  1G to 3G
I mounted the / and /home as EXT4

to NightwishFan:
Before the last time it crashed I noticed that the 3rd CPU runs in 100% and others only 5%,and 1 second later,it crashed

to tedygram311:
I'm very sure that my hard disk is healthy and strong,but I'm not sure what about the drivers
I won't wipe my hard disk anymore,for I had wiped it at least 10 times.

I almost lost confidence with my Ubuntu

I hope you can recognize what I wrote in my bad English
Thanks again for help

---

### Post by usualwyy on 2010-09-27
> **jtarin said:**
> I use this for such things.It allows you to watch kernel messages

you mean I have to keep this terminal and watch my system  break down again?

my goodness

It may be the worst idea [COLOR=#000000]I've ever heard

system crash almost drive me crazy&#12290;[/COLOR]

---

### Post by usualwyy on 2010-09-27
the log is in attachment

Please help me :cry:

---

### Post by NightwishFan on 2010-09-27
Only parts of the log I saw that may have been an issue were:
```
Sep 28 06:33:42 bigchan-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 28 06:33:42 bigchan-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="4016" x-info="http://www.rsyslog.com"] (re)start
Sep 28 06:33:42 bigchan-laptop rsyslogd: rsyslogd's groupid changed to 103
Sep 28 06:33:42 bigchan-laptop rsyslogd: rsyslogd's userid changed to 101
Sep 28 06:33:42 bigchan-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep 28 06:33:42 bigchan-laptop acpid: 38 rules loaded
Sep 28 06:33:42 bigchan-laptop acpid: waiting for events: event logging is off
Sep 28 06:33:42 bigchan-laptop kernel: [  805.489070] type=1505 audit(1285626822.951:18):  operation="profile_replace" pid=4020 name="/usr/sbin/mysqld"
Sep 28 06:33:43 bigchan-laptop init: udev main process (3803) killed by KILL signal
Sep 28 06:33:43 bigchan-laptop init: udev main process ended, respawning
Sep 28 06:33:43 bigchan-laptop init: dbus main process (3869) killed by KILL signal
Sep 28 06:33:43 bigchan-laptop init: dbus main process ended, respawning
Sep 28 06:33:43 bigchan-laptop init: Disconnected from system bus
Sep 28 06:33:43 bigchan-laptop init: dbus main process (4038) terminated with status 1
Sep 28 06:33:43 bigchan-laptop init: dbus main process ended, respawning
Sep 28 06:33:43 bigchan-laptop init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Sep 28 06:33:43 bigchan-laptop kernel: [  805.565872] udev: starting version 151
Sep 28 06:33:43 bigchan-laptop /etc/mysql/debian-start[4049]: Upgrading MySQL tables if necessary.
Sep 28 06:33:43 bigchan-laptop kernel: [  806.507339] SysRq : Emergency Sync
Sep 28 06:33:43 bigchan-laptop kernel: [  806.517628] Emergency Sync complete
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4052]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4052]: Looking for 'mysql' as: /usr/bin/mysql
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4052]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4052]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4059]: Checking for insecure root accounts.
Sep 28 06:33:44 bigchan-laptop /etc/mysql/debian-start[4063]: Triggering myisam-recover for all MyISAM tables
Sep 28 06:33:45 bigchan-laptop kernel: [  807.617602] SysRq : Emergency Remount R/O
```

I cant make heads or tail of it. >_>

---

