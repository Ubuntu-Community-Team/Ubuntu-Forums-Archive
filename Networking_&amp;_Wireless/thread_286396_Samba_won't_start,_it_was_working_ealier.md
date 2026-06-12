---
title: "Samba won't start, it was working ealier"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Schammy on 2006-10-27
I've been tinkering with Samba via the SWAT web-based confi tool and all of the sudden, smbd won't start.  I use the SWAT conole to stop/start/restart and nothing works.

I tried terminal commands too and get this resposne:

steve@steve-ubuntu:~$ /etc/init.d/samba start
 * Starting Samba daemons... install: cannot change owner and/or group of `/var/run/samba': Operation not per mitted
/etc/init.d/samba: line 25:  5508 Aborted                 start-stop-daemon --st art --quiet --oknodo --exec /usr/sbin/smbd -- -D
                                                                         [fail]

Can anyone help?  Is my Samba broken?  Please tell me it ain't so.

---

### Post by Schammy on 2006-10-27
I also tried reinstalling and got this error...
steve@steve-ubuntu:~$ sudo aptitude reinstall samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  samba
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                                                                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
steve@steve-ubuntu:~$

---

