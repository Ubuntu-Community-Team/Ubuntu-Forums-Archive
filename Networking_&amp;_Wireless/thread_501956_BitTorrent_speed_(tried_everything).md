---
title: "BitTorrent speed (tried everything)"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by plenque on 2007-07-16
Hi all...

I've tried everything and I can't get torrent downloads to go faster. I've tried Azureus, uTorrent under wine, Deluge, standard bt-download, etc etc etc.

Ports are correctly forwarded on my router (VNC and Windows Torrents work in the same way), I've disabled IPv6, disabled uPNP in my router, tweaked connection parameters, restarted my router a million times, and I just don't know what else to try.

**iptables -L** shows:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

**netstat -lp --protocol=inet** shows (with uTorrent), so the port is correctly binded:
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:50000                 *:*                     LISTEN     10747/wineserver
udp        0      0 *:50000                 *:*                                10747/wineserver
```

**lsmod | grep ipv6** doesn't show anything.

Seems uploads are not working, but everything is correctly configured.

Any help will be greatly appreciated.
Regards,
Mauro.

---

### Post by PointSource on 2007-07-16
> **plenque said:**
> Hi all...

I've tried everything and I can't get torrent downloads to go faster
....
Seems uploads are not working, but everything is correctly configured.
...


Is it not working at all, or is it just slow?

My only suggestion is perhaps you have reached your bandwidth limit already, and there IS no solution.

---

### Post by avik on 2007-07-16
And remember, torrents download faster with more people, so if you're downloading something relatively obscure, you're not going to get high speeds.

---

### Post by kelvin spratt on 2007-07-16
your ISP might be capping you go to [http://portforward.com/routers.htm](http://portforward.com/routers.htm) it tells you how to set your ports correctly also enable DHT you seem to have it disabled a lot of torrents run on DHT choose a good listening port like 61401 don't set you uploads to high as this slows down your system and your downloads, i find this works for me on any application  that i use, i often max out and also remember check the amount of seeders v leechers 1 seeder 300 leechers don't bother,

---

### Post by AKA3Toes on 2007-07-16
[FONT="Times New Roman"][SIZE="3"][I]---Don't know what mobo you have or if there is an integrated firewall, nor do I know if that firewall can be installed on Linux. When I was running XP, I found that the nVidia firewall for my mobo did not support P2P. Make sure your hardware does support it and/or that your firewall is allowing the connection. I probably don't have to remind you to set up your router if you haven't already done so... for port forwarding.

---FWIW, I had to uninstall BitTorrent and fly with eMule. Sucked not getting torrents, always seemed to be a more mature sharing format to me... compared to limiewre's users who rename everything incorrectly.[/I][/SIZE][/FONT]

---

### Post by plenque on 2007-08-01
Thank you all for answering...

Quick replies:

- Upload are only slow (and most of the time Deluge is not uploading).
- I don't have a motherboard firewall (thank god, didn't know that existed).
- I'm using encrypted traffic on a very high port number... So I guess my ISP can't limit my transfers.
- I'm trying with very popular torrents.

Any other suggestion? I guess I'm out of luck.

Regards,
Mauro.

---

### Post by Hallvor on 2007-08-03
What is your bandwidth, and what is the average upload rate? Didn`t catch if you have a router. But some routers are horrible for filesharing because they can`t handle a high number of connections.

---

