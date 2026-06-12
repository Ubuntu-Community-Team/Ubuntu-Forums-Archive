---
title: "Cannot mount NFS (Connection timed out) yet can browse network to and mount folder"
date: 2015-10-29
forum: Networking &amp; Wireless
---

### Post by Chowarmaan on 2015-10-29
Using Ubuntu 15.04 on a notebook, I cannot mount a NFS share from my FreeNAS 9.3.1.  When I attempt to mount the share, it takes a long time then issues a mount.nfs: Connection timed out.  I can however using the file folders, browse the network, and see and mount the shares that way.  nfs-common appears to be up to date and rpcinfo -p returns:
program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper

I am a basic user on Linux and not sure what to try next.

---

### Post by TheFu on 2015-10-29
Please post the specific line in the client-side /etc/fstab where the mount is being attempted.
The /etc/exports file from the NFS server would be helpful too.

---

### Post by Chowarmaan on 2015-10-29
From the command line:  
sudo mount -t nfs 192.168.0.104:/mnt/NAS /mnt/FreeNAS
sudo mount -t nfs -o proto=tcp 192.168.0.104:/mnt/NAS /mnt/FreeNAS

/etc/fstab
[FONT=Roboto Slab]192.168.0.104:/mnt/NAS /mnt/FreeNAS nfs async,auto,dev,exec,rw,nouser 0 0[/FONT][/COLOR]

FreeNAS /etc/exports
[COLOR=#FFFFFF]/mnt/NAS  -alldirs -mapall=mediactr:wheel AMD6Core    

[/COLOR]

---

### Post by SeijiSensei on 2015-10-29
Try adding "vers=3" to the options in fstab and see if that helps.

Are you trying to mount the share as root (usually the case if it's mounting in /etc/fstab).  If so you'll need to add "no_root_squash" to the options in /etc/exports.  With that, and "defaults,async" in /etc/fstab, my shares mount without a problem.  (Oh, you have a NAS?  Can you enable no_root_squash on that?)

---

### Post by Chowarmaan on 2015-10-29
I get the following error with vers=3 in the fstab
mount.nfs: requested NFS version or transport protocol is not supported

[COLOR=#000000][FONT=Roboto Slab]192.168.0.104:/mnt/NAS /mnt/FreeNAS nfs async,auto,dev,exec,rw,nouser,vers=3 0 0[/FONT][/COLOR]

I did add the no_root_squash at the end of the line in the /etc/exports for FreeNAS, but it is not preserved.  Using my username and group in the -mapall is suppose to do the same thing as the no_root_squash.

---

### Post by Chowarmaan on 2015-11-01
I just applied the latest Ubuntu 15.10, and I am still getting the same error, This is preventing the NAS from being used by other systems.

---

### Post by Chowarmaan on 2015-11-03
[COLOR=#141414][FONT=Trebuchet MS][INDENT]I have the dump from the Ubuntu 15.10 which appears to be a routing problem, but ping works.

~$ ping 192.168.0.104
PING 192.168.0.104 (192.168.0.104) 56(84) bytes of data.
64 bytes from 192.168.0.104: icmp_seq=1 ttl=64 time=0.214 ms
64 bytes from 192.168.0.104: icmp_seq=2 ttl=64 time=0.257 ms
64 bytes from 192.168.0.104: icmp_seq=3 ttl=64 time=0.252 ms
^C
--- 192.168.0.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.214/0.241/0.257/0.019 ms

~$ sudo mount -t nfs -o nfsvers=3 192.168.0.104:/mnt/NAS /mnt/test 
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: portmap query failed: RPC: Remote system error - No route to host
mount.nfs: Connection timed out
mount.nfs: timeout set for Tue Nov 3 08:17:51 2015
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying text-based options 'nfsvers=3,addr=192.168.0.4'
mount.nfs: prog 100003, trying vers=3, prot=6

This dump is from the Ubuntu attempting to mount the FreeNAS volume.

FreeNAS attempting to mount the same thing, gives an RPC routing error, then permission denied. I am using the shell option on FreeNAS to try to run the commands. The shell starts with a ~#, but maybe I need the sudo there as well? 
[/INDENT][/FONT][/COLOR]
[COLOR=#141414][FONT=Trebuchet MS]
[/FONT][/COLOR]

---

### Post by Chowarmaan on 2015-11-05
[COLOR=#141414][FONT=Georgia]I posted further information on errors in verbose mode. I have updated to Ubuntu 15.10 without any change either. I can however, browse through the File GUI and see the folder (Browse Network, FreeNAS, ...) and can access the files that way, just not with nfs.[/FONT][/COLOR]

---

### Post by gordintoronto on 2015-11-06
This is probably a dumb question: are you sure it's not a Samba share?

---

### Post by Chowarmaan on 2015-11-08
> **gordintoronto said:**
> This is probably a dumb question: are you sure it's not a Samba share?

I am trying and failing the NFS share  I believe the GUI though is loading the Samba share, which I also have set up for Windows computers.  So I think the browsing on the network through the GUI in Linux is using the Samba, but it does show I can get to and access the computer.

---

