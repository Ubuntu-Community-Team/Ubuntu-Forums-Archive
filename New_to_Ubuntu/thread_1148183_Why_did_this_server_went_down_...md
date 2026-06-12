---
title: "Why did this server went down ..?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by byenary on 2009-05-04
I've got a sever wich went down unexpectitly, this is the relevant syslog : It seems to be a normal shutdown bu I can't realy see why he did it... you can ?

May  1 02:04:15 willy-- MARK --
May  1 02:09:54 willy/USR/SBIN/CRON[27924]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May  1 02:17:53 willy/USR/SBIN/CRON[28105]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 02:39:52 willy/USR/SBIN/CRON[28412]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May  1 03:00:48 willy/USR/SBIN/CRON[28670]: (root) CMD (sh /home/elias/scripts/runbackup.sh) 
May  1 03:09:39 willy/USR/SBIN/CRON[28841]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May  1 03:17:26 willy/USR/SBIN/CRON[28973]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 03:22:53 willy init: tty5 main process (4298) killed by TERM signal
May  1 03:22:53 willy init: tty6 main process (4305) killed by TERM signal
May  1 03:22:53 willy init: tty1 main process (32160) killed by TERM signal
May  1 03:22:53 willy init: tty3 main process (4302) killed by TERM signal
May  1 03:22:53 willy init: tty2 main process (4300) killed by TERM signal                
May  1 03:22:53 willy init: tty4 main process (4297) killed by TERM signal                  
May  1 03:23:03 willy avahi-daemon[4483]: Got SIGTERM, quitting.
May  1 03:23:03 willy avahi-daemon[4483]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.123.16.
May  1 03:23:18 willy postfix/master[4826]: terminating on signal 15
May  1 03:23:19 willy mysqld[20146]: 090501  3:23:19 [Note] /usr/sbin/mysqld: Normal shutdown
May  1 03:23:19 willy mysqld[20146]:
May  1 03:23:19 willy mysqld[20146]: 090501  3:23:19  InnoDB: Starting shutdown...
May  1 03:23:22 willy mysqld[20146]: 090501  3:23:22  InnoDB: Shutdown completed; log sequence number 0 2101906915
May  1 03:23:22 willy mysqld[20146]: 090501  3:23:22 [Note] /usr/sbin/mysqld: Shutdown complete
May  1 03:23:22 willy mysqld[20146]:
May  1 03:23:23 willy mysqld_safe[29554]: ended
May  1 03:23:25 willy exiting on signal 15
May  4 10:01:32 willy syslogd 1.4.1#21ubuntu3: restart.
May  4 10:01:32 willy kernel: Inspecting /boot/System.map-2.6.22-14-server
May  4 10:01:32 willy kernel: Loaded 26239 symbols from /boot/System.map-2.6.22-14-server.              
May  4 10:01:32 willy kernel: Symbols match kernel version 2.6.22.
May  4 10:01:32 willy kernel: No module symbols loaded - kernel modules not enabled.

---

### Post by Alterax on 2009-05-04
Looks like it was initiated by a command.  If it weren't, I'd expect it to not crash so cleanly.

Just to be on the safe side, check your crontab entries to see if anyone's added a shutdown sequence.  (I've seen it before, even had to show a guy on here how to add an entry to do it--and to this day can't understand WHY they wanted it.)

Also, does your system log sudoers' activity?  If so, you might want to check those logs to see if anyone manually issued the shutdown, telinit or init commands.  You're looking for an init 6 (reboot) or an init 0(hard shutdown).

---

