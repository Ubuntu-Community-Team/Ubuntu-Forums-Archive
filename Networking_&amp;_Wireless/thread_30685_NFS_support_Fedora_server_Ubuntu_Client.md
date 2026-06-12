---
title: "NFS support Fedora server Ubuntu Client"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by ryan on 2005-04-29
I can mount a NFS export from my Fedora box on my unbuntu laptop. But the export is read only. 

From etc/exports

/home/ryan/Ongoing      ryan-lap.localdomain (rw)

from fstab on the Unbuntu laptop

ryan.localdomain:/home/ryan/Ongoing /home/ryan/Fedora nfs defaults 0 0

Everything mounts fine and I can see everything in my export and copy it to my Unbuntu laptop, but can't write to it.

From the Fedora box

[ryan@ryan ~]$ id
uid=500(ryan) gid=500(ryan) groups=500(ryan)

From the Unbuntu


ryan@ryan-lap:~$ id
uid=1000(ryan) gid=1000(ryan)
groups=4(adm),20(dialout),24(cdrom),25(floppy),29(
audio),30(dip),44(video),46(plugdev),107(lpadmin),108(scanner),109(admin),1000(r
yan)

seems to be a permissions deal anyone have any ideas about how change it.

tks

---

### Post by ryan on 2005-04-30
In addition to the initial R/W issue, it seems that since I work on a WAN, I have found that I can't access the NFS export if I am on a different subnet on the same network. Windows domain with 3 subnets. Any ideas ? tks

---

### Post by ryan on 2005-05-01
Someone suggested that I check var/log/messages and here was some portions that might have some relevance.
This is part of the log from yesterday when I first did the NFS export: Says something about the 'sync' or 'async' option plus ' failed to contact portmap (errno -5).' as well 'ryan-lap.domain.local has non-inet addr' perhaps I will try using an IP number and not a host name and see if that makes a difference.


Apr 29 15:14:50 ryan rpc.mountd: Caught signal 15, un-registering and exiting.
Apr 29 15:14:50 ryan nfs: rpc.mountd shutdown succeeded
Apr 29 15:14:54 ryan kernel: nfsd: last server has exited
Apr 29 15:14:54 ryan kernel: nfsd: unexporting all filesystems
Apr 29 15:14:54 ryan kernel: RPC: failed to contact portmap (errno -5).
Apr 29 15:14:54 ryan nfs: nfsd shutdown succeeded
Apr 29 15:14:54 ryan nfs: rpc.rquotad shutdown succeeded
Apr 29 15:14:54 ryan nfs: Shutting down NFS services: succeeded
Apr 29 15:14:54 ryan exportfs[26033]: ryan-lap.domain.local has non-inet addr
Apr 29 15:14:54 ryan exportfs: exportfs: ryan-lap.domain.local has non-inet addr
Apr 29 15:14:54 ryan exportfs[26033]: ryan-lap.domain.local has non-inet addr
Apr 29 15:14:54 ryan exportfs: exportfs: ryan-lap.domain.local has non-inet addr
Apr 29 15:14:54 ryan nfs: Starting NFS services: succeeded
Apr 29 15:14:54 ryan nfs: rpc.rquotad startup succeeded
Apr 29 15:14:54 ryan nfs: rpc.nfsd startup succeeded
Apr 29 15:14:54 ryan nfs: rpc.mountd startup succeeded
Apr 29 15:14:54 ryan rpcidmapd: rpc.idmapd -SIGHUP succeeded
Apr 29 15:15:41 ryan rpc.mountd: mount request from unknown host 192.168.2.41 for /home/ryan/Ongoing (/home/ryan/Ongoing)
Apr 29 15:16:46 ryan rpc.mountd: mount request from unknown host 192.168.2.41 for /home/ryan/Ongoing (/home/ryan/Ongoing)
Apr 29 15:17:24 ryan rpc.mountd: Caught signal 15, un-registering and exiting.
Apr 29 15:17:24 ryan nfs: rpc.mountd shutdown succeeded
Apr 29 15:17:28 ryan kernel: nfsd: last server has exited
Apr 29 15:17:28 ryan kernel: nfsd: unexporting all filesystems
Apr 29 15:17:28 ryan kernel: RPC: failed to contact portmap (errno -5).
Apr 29 15:17:28 ryan nfs: nfsd shutdown succeeded
Apr 29 15:17:28 ryan nfs: rpc.rquotad shutdown succeeded
Apr 29 15:17:28 ryan nfs: Shutting down NFS services: succeeded
Apr 29 15:17:28 ryan exportfs[26141]: /etc/exports [5]: No 'sync' or 'async' option specified for export "ryan-lap.domain.local:/home/ryan/Ongoing". Assuming default behaviour ('sync'). NOTE: this default has changed from previous versions
Apr 29 15:17:28 ryan exportfs: exportfs: /etc/exports [5]: No 'sync' or 'async' option specified for export "ryan-lap.domain.local:/home/ryan/Ongoing".


This iis from today
Says something about the 'sync' or 'async' option again


Apr 30 21:02:18 ryan exportfs[31763]: /etc/exports [5]: No 'sync' or 'async' option specified for export "ryan-lap.domain.local:/home/ryan/Ongoing". Assuming default behaviour ('sync'). NOTE: this default has changed from previous versions
Apr 30 21:02:18 ryan exportfs: exportfs: /etc/exports [5]: No 'sync' or 'async' option specified for export "ryan-lap.domain.local:/home/ryan/Ongoing".
Apr 30 21:02:18 ryan exportfs: Assuming default behaviour ('sync').
Apr 30 21:02:18 ryan exportfs: NOTE: this default has changed from previous versions
Apr 30 21:02:18 ryan nfs: Starting NFS services: succeeded
Apr 30 21:02:18 ryan nfs: rpc.rquotad startup succeeded
Apr 30 21:02:18 ryan nfs: rpc.nfsd startup succeeded
Apr 30 21:02:18 ryan nfs: rpc.mountd startup succeeded
Apr 30 21:02:18 ryan rpcidmapd: rpc.idmapd -SIGHUP succeeded
Apr 30 21:06:28 ryan rpc.mountd: authenticated unmount request from ryan-lap.domain.local:683 for /home/ryan/Ongoing (/home/ryan/Ongoing)

---

