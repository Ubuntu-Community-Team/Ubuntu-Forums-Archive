---
title: "Update killed interweb! (UbuntuMATE 16.04.4)"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by d0006 on 2018-05-04
Did an update with Synaptic yesterday (4 May 2018) and today I have no internet connectivity! No nm-applet, no NetworkManager, no nothin'!

After much searching and much pain (and more pain) (I am strictly an intermediate Linux user and I have much problems when things break).
```
foo@bar:~$ nm-applet
(nm-applet:3044): nm-applet-WARNING **: NetworkManager is not running
```
```
foo@bar:~$ sudo service network-manager restart
Job for NetworkManager.service failed because the control process exited with error code. See "systemctl status NetworkManager.service" and "journalctl -xe" for details.

```
So:
```
foo@bar:~$ systemctl status NetworkManager.service
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since Fri 2018-05-04 21:10:56 MDT; 38s ago
     Docs: man:NetworkManager(8)
  Process: 3085 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, status=1/FAILURE)
 Main PID: 3085 (code=exited, status=1/FAILURE)

May 04 21:10:56 bar systemd[1]: Failed to start Network Manager.
May 04 21:10:56 bar systemd[1]: NetworkManager.service: Unit entered failed state.
May 04 21:10:56 bar systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
May 04 21:10:56 bar systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
May 04 21:10:56 bar systemd[1]: Stopped Network Manager.
May 04 21:10:56 bar systemd[1]: NetworkManager.service: Start request repeated too quickly.
May 04 21:10:56 bar systemd[1]: Failed to start Network Manager.
```
No help.
So:
```
foo@bar:~$ journalctl -xe
-- 
-- Unit NetworkManager.service has finished shutting down.
May 04 21:14:24 bar systemd[1]: Starting Network Manager...
-- Subject: Unit NetworkManager.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit NetworkManager.service has begun starting up.
May 04 21:14:24 bar NetworkManager[3992]: Failed to read configuration: /etc/NetworkManager/conf.d/MACChanger-Persistant.conf: Key file does not start
May 04 21:14:24 bar systemd[1]: NetworkManager.service: Main process exited, code=exited, status=1/FAILURE
May 04 21:14:24 bar systemd[1]: Failed to start Network Manager.
-- Subject: Unit NetworkManager.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit NetworkManager.service has failed.
-- 
-- The result is failed.
May 04 21:14:24 bar systemd[1]: NetworkManager.service: Unit entered failed state.
May 04 21:14:24 bar systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
May 04 21:14:24 bar systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
May 04 21:14:24 bar systemd[1]: Stopped Network Manager.
-- Subject: Unit NetworkManager.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit NetworkManager.service has finished shutting down.
May 04 21:14:24 bar systemd[1]: NetworkManager.service: Start request repeated too quickly.
May 04 21:14:24 bar systemd[1]: Failed to start Network Manager.
-- Subject: Unit NetworkManager.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit NetworkManager.service has failed.
-- 
-- The result is failed.
May 04 21:14:28 bar ntpd[1583]: error resolving pool 0.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
May 04 21:14:30 bar ntpd[1583]: error resolving pool 2.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
May 04 21:14:35 bar ntpd[1583]: error resolving pool 1.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
May 04 21:14:36 bar ntpd[1583]: error resolving pool ntp.ubuntu.com: Temporary failure in name resolution (-3)
May 04 21:14:39 bar ntpd[1583]: error resolving pool 3.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
lines 2774-2814/2814 (END)
```
Eureka!

Previously I installed Macchanger, which did not work with NetworkManager v1.2.6.  It is not possible to use a later version of NetworkManager with Ubuntu 16.04.  A suggestion I found online was to add a configuration file to etc/NetworkManager/conf.d (which did not work). 
I deleted Macchanger and the extra configuration file and now I have teh interweb! Yay!

---

