---
title: "[SOLVED] NFS problem with IP addresses in /etc/exports"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by icheyne on 2007-12-25
How come when I specify an IP address in /etc/exports it's ignored and I get "permisson denied" at the NFS client but when I specify * instead of an IP address it works?. All the guides say I should use a range like 192.168.0.0/24 but that doesn't work.

i.e.
These do not work:
```
/home/iain/multimedia_backup/vids/ http://192.168.11.0/24(rw,sync,no_subtree_check)
``````
/home/iain/multimedia_backup/vids/ http://192.168.11.31(rw,sync,no_subtree_check)
```but this does:
```
/home/iain/multimedia_backup/vids/ *(rw,sync,no_subtree_check)
```

---

### Post by dnvikram on 2007-12-26
a) Do an ,"ls -l" on this location ,"/home/iain/multimedia_backup/vids/" and paste the output.Who owns this directory?

b)The * in the line below indicates that you almost everyone is allowed to mount that location over the nfs.Its something like you are sharing it to ALL the machines on the network.

c)Why do you have the **http://** infront of the ip address of the machine(s) to which you want to share? 

d)Try removing those http:// from that line,restart your nfs service and then try mounting the nfs share on the client machine.

---

### Post by icheyne on 2007-12-26
You are absolutely right. It was the http's that were messing it up.

Thanks for fixing my problem. :)

---

