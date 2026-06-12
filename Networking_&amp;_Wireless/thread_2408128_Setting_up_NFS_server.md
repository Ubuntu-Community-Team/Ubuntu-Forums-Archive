---
title: "Setting up NFS server"
date: 2018-12-14
forum: Networking &amp; Wireless
---

### Post by dworan on 2018-12-14
Still new to ubuntu, but have so far managed to get by using guides and existing forum posts. This time I'm stuck....

ran [COLOR=#ff0000][FONT=monospace]sudo apt-get install nfs-k[/FONT][FONT=monospace]ernel-ser[/FONT][FONT=monospace]ver[/FONT][/COLOR][COLOR=#3A3A3A][FONT=monospace]
[/FONT][/COLOR]
Edited /etc/exports to:
[COLOR=#ff0000]# /etc/exports: the access control list for filesystems which may be exported[/COLOR]
[COLOR=#ff0000]#        to NFS clients.  See exports(5).[/COLOR]
[COLOR=#ff0000]# /tank/Movies 192.168.1.143(rw,sync,no_subtree_check,no_root_squash)[/COLOR]
[COLOR=#ff0000]# /tank/TVSeries 192.168.1.143(rw,sync,no_subtree_check,no_root_squash)[/COLOR]
[COLOR=#ff0000]# /home 192.168.1.143(rw,sync,no_subtree_check,no_root_squash)[/COLOR]

Got an the following error when saving:
[COLOR=#ff0000]** (gedit:19160): Warning **: 10:26:08:958: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported[/COLOR]

Read in another forum post that this error could just be ignored??

Ran [COLOR=#ff0000]sudo systemctl restart nfs-kernel-server
[/COLOR]
Couldn't find anything on the client (Vero 4k+), si I tried running [COLOR=#ff0000]sudo exportfs -a [/COLOR]on the server, but didn't get any output... 

Tried [COLOR=#ff0000]/etc/init.d/nfs-kernel-server [/COLOR]and received:
&#9679; nfs-server.service - NFS server and services
   Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor preset: enabled)
   Active: active (exited) since Fri 2018-12-14 10:18:44 CET; 4min 14s ago
  Process: 17821 ExecStopPost=/usr/sbin/exportfs -f (code=exited, status=0/SUCCESS)
  Process: 17820 ExecStopPost=/usr/sbin/exportfs -au (code=exited, status=0/SUCCESS)
  Process: 17819 ExecStop=/usr/sbin/rpc.nfsd 0 (code=exited, status=0/SUCCESS)
  Process: 17830 ExecStart=/usr/sbin/rpc.nfsd $RPCNFSDARGS (code=exited, status=0/SUCCESS)
  Process: 17829 ExecStartPre=/usr/sbin/exportfs -r (code=exited, status=0/SUCCESS)
 Main PID: 17830 (code=exited, status=0/SUCCESS)


des. 14 10:18:44 Server systemd[1]: Starting NFS server and services...
des. 14 10:18:44 Server systemd[1]: Started NFS server and services.

So as far as I can see, NFS should be running... Don't get why it doesn't seem to be exporting anything... Something wrong with the /etc/exports file possibly?

---

### Post by dworan on 2018-12-14
Newer than I thought I guess... Removed the hashtags that obviously don't belong in /etc/exports... Seems to be working after all :P

---

