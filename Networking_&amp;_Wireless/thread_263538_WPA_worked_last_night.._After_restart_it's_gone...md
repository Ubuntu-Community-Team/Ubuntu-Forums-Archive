---
title: "WPA worked last night.. After restart it's gone.."
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by CarbineMonoxide on 2006-09-23
Well, I installed knetorkmanager last night. When I installed it, it automatically worked. After I restarted, I run knetworkmanager and it seems to not work anymore. No networks are detected in it.

```
root@carbine-laptop:/home/carbine# knetworkmanager
Creating link /root/.kde/socket-carbine-laptop.
Created link from "/root/.kde/socket-carbine-laptop" to "/tmp/ksocket-root"
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
Creating link /root/socket-carbine-laptop.
Created link from "/root/socket-carbine-laptop" to "/tmp/ksocket-root"
Creating link /root/.kde/tmp-carbine-laptop.
Created link from "/root/.kde/tmp-carbine-laptop" to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Creating link /root/cache-carbine-laptop.
Created link from "/root/cache-carbine-laptop" to "/var/tmp/kdecache-root"
Creating link /root/tmp-carbine-laptop.
Created link from "/root/tmp-carbine-laptop" to "/tmp/kde-root"
Link points to "/var/tmp/kdecache-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdeinit: Shutting down running client.
org.freedesktop.NetworkManagerInfo already owned.
root@carbine-laptop:/home/carbine# ---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_carbine-laptop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.

```

I am using an MSI CB54G and an internal Broadcom 4318.. I know for a fact that I was connected via WPA last night. By the way, I'm a complete linux n00b, so I might need some walkthroughs. =P

---

### Post by happy-and-lost on 2006-09-23
Urrghh... KDE.
Are you using Ubuntu or Kubuntu?

Either way, ```
sudo apt-get install wifi-radar
``` will install a very useful GUI wifi management tool, which should solve your problem.

---

### Post by CarbineMonoxide on 2006-09-25
Okay.. I've installed Wifi-Radar. It works fine for connecting to a non-secured network, but it's asking for a WPA driver? That and my wireless G networks are showing up as B...

---

### Post by joshlfisher on 2006-09-25
I just installed Kubuntu Dapper, and I don't seem to have WPA support. I have an intel Centrino chipset. How do I enable WPA?
(I am a Kubuntu and Lunix n00b)

---

### Post by CarbineMonoxide on 2006-09-26
Well.. I set the WPA driver to ndiswrapper and it connected fine.. The only problem I'm having now is it shows my G network as a B network..

---

