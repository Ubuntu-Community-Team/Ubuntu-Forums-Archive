---
title: "Struggling to create NFS in a Solus-lubuntu network"
date: 2021-03-12
forum: Networking &amp; Wireless
---

### Post by jorgeblasio on 2021-03-12
Hi. 

I'm fairly new to linux, specially networking. I come from using MacOS X for the last 20 years.
I'm scratching my head with this issue.
I have a very old tower (2007 Core 2 Duo) that I'm re-purposing to host my music through Plex. In the near future I'll replace it with a more modern build but meanwhile this is what I have.
My network consists of a WiFi 6 TPLink router, a RaspberryPi 3 that captures publicity through pihole, my main computer running Solus GNOME and this tower, running lubuntu 20.10
I have followed the instructions on [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)
My Solus has the nfs-common pkg installed.
The share I want to export is the a couple of directories on a secondary, 1 Tb hard disk mounted to /media/DeepGut. I took ownership of that drive with chown and properly mounts on my lubuntu fstab.
My problem comes when I export the ACL. I get this error:
```
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.0/24:/media/DeepGut".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
```

What am I doing wrong?
I appreciate any input you can give me.

---

### Post by TheFu on 2021-03-12
What are the exact contents of the /etc/exports?

---

### Post by jorgeblasio on 2021-03-12
/media/DeepGut 192.168.0.0/24(rw,all_squash)

---

### Post by TheFu on 2021-03-12
Try:
```
/media/DeepGut 192.168.0.0/24(rw)
```
Be certain to restart the nfs-server process/daemon on the server, then restart the mounts from the clients.

If that works, then we can try to find the squash options.  I always use root_squash for security reasons and put in per-server, not subnet export rules.

And of course, we assume that /media/DeepGut is using an fstab mount on the NFS server and has a Linux native file system.
**df -Th** can prove that.

---

### Post by jorgeblasio on 2021-03-12
Yes, /media/DeepGut is ext4 and is mounted by fstab. I tried changing the host address/name and I restarted the NFS service.
The error is the same:
```
~$ exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.190:/media/DeepGut".
  Assuming default behaviour ('no_subtree_check').                                                                                                                   
  NOTE: this default has changed since nfs-utils version 1.0.x                                                                                                       
                                                                                                                                                                     
exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)                                                                           
exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)                                                                           
exportfs: can't lock /var/lib/nfs/etab for writing

~$ exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "lubuntuDell755:/media/DeepGut".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing

~$ exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.0/24:/media/DeepGut".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
```

---

### Post by TheFu on 2021-03-12
I see the same errors, but nfs is working.

---

### Post by jorgeblasio on 2021-03-13
if I mount manually, I get```
mount.nfs: access denied by server while mounting 192.168.0.190:/media/Deepgut
```

Also if I use network names, my Solus machine complains ```
mount.nfs: Failed to resolve server lubuntuDell755: Name or service not known
```
But ping: ```
ping -c 1 192.168.0.190
PING 192.168.0.190 (192.168.0.190): 56 data bytes
64 bytes from 192.168.0.190: icmp_seq=0 ttl=64 time=0.337 ms
--- 192.168.0.190 ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.337/0.337/0.337/0.000 ms
```

NSF server status:```
&#9679; nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor pr>
    Drop-In: /run/systemd/generator/nfs-server.service.d
             &#9492;&#9472;order-with-mounts.conf
     Active: active (exited) since Sat 2021-03-13 13:02:03 CST; 34min ago
    Process: 3486 ExecStartPre=/usr/sbin/exportfs -r (code=exited, status=0/SUC>
    Process: 3487 ExecStart=/usr/sbin/rpc.nfsd $RPCNFSDARGS (code=exited, statu>
   Main PID: 3487 (code=exited, status=0/SUCCESS)

mar 13 13:02:02 lubuntuDell755 systemd[1]: Starting NFS server and services...
mar 13 13:02:02 lubuntuDell755 exportfs[3486]: exportfs: /etc/exports [1]: Neit>
mar 13 13:02:02 lubuntuDell755 exportfs[3486]:   Assuming default behaviour ('n>
mar 13 13:02:02 lubuntuDell755 exportfs[3486]:   NOTE: this default has changed>
mar 13 13:02:03 lubuntuDell755 systemd[1]: Finished NFS server and services.
```

---

### Post by TheFu on 2021-03-13
That output seems to show the nfs-server is fine. Was something important cut off?
On the NFS server: ```
showmount -e
```
Does that show the mounts as available?

If you don't have name resolution setup, then you can't use hostnames. IPs will be needed.
Any chance of a firewall or tcp-wrappers getting in the way?

I don't remember if ACLs are supported by default, but normal Unix permissions definitely are.
From the client, run
```
sudo mkdir /mnt/DeepGut
sudo mount -t nfs 192.168.0.190:/media/DeepGut /mnt/DeepGut  -o proto=tcp,intr,rw,async
df -Th |grep Deep
```

The only issue I'd expect if there isn't any blocking would be different uids not lining up.  Macs start with uids of 500 and Linux starts with 1000, so that will need to be addressed if there is a Mac involved.  The uid/gid (numbers) need to match for any directories/files on the clients and NFS storage.

---

### Post by jorgeblasio on 2021-03-13
$ showmount -e
```
Export list for lubuntuDell755:
/media/DeepGut 192.168.0.0/24
```

Yes it showed the mount available

No, I don't have a tcp-wrapper, I only have my router's default firewall on.
When I had my Mac, all my shares showed up automagically on Solus, both NFS and samba. That Mac was stolen 2 years ago and now I only have these two machines.

>      Code:
     sudo mkdir /mnt/DeepGut
sudo mount -t nfs 192.168.0.190:/media/DeepGut /mnt/DeepGut  -o proto=tcp,intr,rw,async
df -Th |grep Deep 
The only issue I'd expect if there isn't any blocking would be  different uids not lining up.  Macs start with uids of 500 and Linux  starts with 1000, so that will need to be addressed if there is a Mac  involved.  The uid/gid (numbers) need to match for any directories/files  on the clients and NFS storage.

This worked.

I got this from the last command:
```
192.168.0.190:/media/DeepGut nfs4      916G   77M  870G   1% /mnt/DeepGut
```

---

### Post by TheFu on 2021-03-14
Make the fstab

```
192.168.0.190:/media/DeepGut /mnt/DeepGut  nfs  proto=tcp,intr,rw,async  0   0
```

Run
```
sudo mount -a
```
Use **df** to check the mount. Should be fine. 

All good?

---

### Post by jorgeblasio on 2021-03-15
Nope.
```
sudo mount -a
mount.nfs: Connection timed out
```

---

### Post by TheFu on 2021-03-15
So ... 
sudo **mount -t nfs** .... works
but 
**sudo mount -a** using the fstab above doesn't?

I'd check the client-side log files.  I've never seen this unless the fstab has an error above the line for the nfs mount.  I'd blame systemd-mount.

---

### Post by jorgeblasio on 2021-03-18
That is correct, fstab mount fails, but manually mounting works.

It appears nfs does not log anything by default, journalctl has no mention of nfs.

---

### Post by TheFu on 2021-03-18
I suspect there is an error in the fstab file above where the NFS line(s) are inside it.  systemd-mount isn't as good as the old fstab methods, yet.
Also, it shouldn't hurt to have systemd look at all the files again. Here's the command:
```
sudo systemctl daemon-reload
```
Then you can find the systemd "unit file" created for each NFS mount and use something like:
```
sudo systemctl restart mnt-DeepGut.automount
```
I'm not certain about the service name. It is generated by systemd.
I mount stuff on /S and the service name ended up being "S.automount"

Or perhaps:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

Maybe check the logs for "mount" issues?

How much does Solus differ from Ubuntu?  I've never used it.

---

### Post by jorgeblasio on 2021-03-18
I get this when restaring systemd-mount:
```
Failed to restart mnt-DeepGut.automount: Unit mnt-DeepGut.automount not found.
```

My /etc/systemd does not have any unit files.

Solus is a stable rolling release, non-debian, systemd distro.

---

### Post by TheFu on 2021-03-18
> **jorgeblasio said:**
> I get this when restaring systemd-mount:
```
Failed to restart mnt-DeepGut.automount: Unit mnt-DeepGut.automount not found.
```

My /etc/systemd does not have any unit files.

Solus is a stable rolling release, non-debian, systemd distro.

mnt-DeepGut.automount was a guess, if that wasn't clear. You have to figure out what your system would call it. That's what I meant by 
> I'm not certain about the service name. 
non-debian - well, I'm out. You posted in the Official Flavours sub-forum.  Should that be "Other distros" instead?
Good luck.

---

### Post by jorgeblasio on 2021-03-19
But Lubuntu is the server.

Anyway, yeah, the systemd directory didn't have any .mount files, so I created one according to this blog post [https://rayagainstthemachine.net/linux%20administration/systemd-automount/](https://rayagainstthemachine.net/linux%20administration/systemd-automount/)
Thank you for helping me and for steering me in the right direction. NFS is working using systemd automount.

---

