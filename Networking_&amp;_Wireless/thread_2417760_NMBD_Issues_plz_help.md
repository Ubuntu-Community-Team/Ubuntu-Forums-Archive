---
title: "NMBD Issues plz help"
date: 2019-04-26
forum: Networking &amp; Wireless
---

### Post by wolfzrat on 2019-04-26
So out of no where this happen

nmbd.service - Samba NMB Daemon
   Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: ena
   Active: failed (Result: timeout) since Fri 2019-04-26 20:55:37 EDT; 2min 3s a
     Docs: man:nmbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 5425 ExecStart=/usr/sbin/nmbd --foreground --no-process-group $NMBDOP
 Main PID: 5425 (code=killed, signal=TERM)
   Status: "nmbd: No local IPv4 non-loopback interfaces available, waiting for i

Apr 26 20:54:07 gameserver systemd[1]: Starting Samba NMB Daemon...
Apr 26 20:55:37 gameserver systemd[1]: nmbd.service: Start operation timed out. 
Apr 26 20:55:37 gameserver systemd[1]: nmbd.service: Failed with result 'timeout
Apr 26 20:55:37 gameserver systemd[1]: Failed to start Samba NMB Daemon.


could someone please assist me as i am new to Ubuntu Server

Thanks

---

### Post by wildmanne39 on 2019-04-29
Thread closed. Please do not post duplicates, it dilutes community effort.

---

