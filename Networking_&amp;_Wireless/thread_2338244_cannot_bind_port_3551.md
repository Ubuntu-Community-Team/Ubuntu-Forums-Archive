---
title: "cannot bind port 3551"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by zkab on 2016-09-26
After upgrading to 16.04.1 LTS apcupsd stopped working.

$ sudo service apcupsd status
&#9679; apcupsd.service - LSB: Starts apcupsd daemon
   Loaded: loaded (/etc/init.d/apcupsd; bad; vendor preset: enabled)
   Active: active (running) since sön 2016-09-25 21:09:09 CEST; 14h ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1133 ExecStart=/etc/init.d/apcupsd start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/apcupsd.service
           &#9492;&#9472;1169 /sbin/apcupsd

sep 25 21:09:09 zkab systemd[1]: Starting LSB: Starts apcupsd daemon...
sep 25 21:09:09 zkab apcupsd[1133]: Starting UPS power management: apcupsd.
sep 25 21:09:09 zkab apcupsd[1169]: apcupsd 3.14.12 (29 March 2014) debian startup succeeded
sep 25 21:09:09 zkab apcupsd[1169]: [COLOR="#FF0000"]apcserver: cannot bind port 3551. ERR=Cannot assign requested address[/COLOR]
sep 25 21:09:09 zkab systemd[1]: Started LSB: Starts apcupsd daemon.
sep 25 21:15:27 zkab apcupsd[1169]: NIS server startup succeeded

How can this be fixed ?

---

