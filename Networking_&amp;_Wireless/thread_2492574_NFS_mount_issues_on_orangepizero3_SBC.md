---
title: "NFS mount issues on orangepizero3 SBC"
date: 2023-11-15
forum: Networking &amp; Wireless
---

### Post by machs on 2023-11-15
I have a NFS server running with a valid export.conf, 3 of 4 clients on the network are able to connect to this server without issue and can read / write. 

the forth client (orangepizero3) is the problem.  When i try to mount the NFS directory i get the follow error
```

machs@orangepizero3:~$ sudo mount -t nfs  192.168.0.131:/media/smilingBuddha /media/smilingBuddha -vvv
mount.nfs: timeout set for Wed Nov 15 13:35:23 2023
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.0.131,clientaddr=192.168.0.246'
mount.nfs: mount(2): Protocol error
mount.nfs: Protocol error

```

I've tried a few different incantations of the mount command specifying various NFS options, which ultimately fails after timing out. 

```
machs@orangepizero3:~$ sudo mount -t nfs -o mountvers=3 electricsheep:/media/smilingBuddha /media/smilingBuddha -vvv
mount.nfs: timeout set for Wed Nov 15 13:43:12 2023
mount.nfs: trying text-based options 'mountvers=3,addr=192.168.0.131'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.0.131 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.0.131 prog 100005 vers 3 prot UDP port 50411
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed



```

Futher confusing things is that I can mount a NFS share from a older NAS box on orangepizero3 without issues :() 

```
machs@orangepizero3:~$ sudo mount /media/pillarOfAutumn -vvv
mount.nfs: timeout set for Wed Nov 15 13:36:56 2023
mount.nfs: trying text-based options 'hard,intr,vers=4.2,addr=192.168.0.77,clientaddr=192.168.0.246'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'hard,intr,vers=4,minorversion=1,addr=192.168.0.77,clientaddr=192.168.0.246'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'hard,intr,vers=4,addr=192.168.0.77,clientaddr=192.168.0.246'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'hard,intr,addr=192.168.0.77'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.0.77 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.0.77 prog 100005 vers 3 prot UDP port 46905

```

This succeeds and I can access that NFS directory!

The only thing i can think of is that orangepizero3 is running an old-ish kernel, which is nessecary since it the 6.x kernel did not work with the onboard wifi. 

client
```


machs@orangepizero3:~$ showmount -e electricsheep
Export list for electricsheep:
/media/smilingBuddha 192.168.0.0/24


machs@orangepizero3:~$ rpcinfo -p electricsheep | grep nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs

machs@orangepizero3:~$ uname -a
Linux orangepizero3 5.4.125 #1.0.0 SMP Fri Jun 30 11:59:12 CST 2023 aarch64 aarch64 aarch64 GNU/Linux

```

server

```
machs@electricSheep:~$ uname -a
Linux electricSheep 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  9 15:34:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

machs@electricSheep:~$ cat /etc/exports 
/media/smilingBuddha  192.168.0.0/24(rw,sync,no_root_squash,no_subtree_check)

```

I haven't been able to resolve with  the normal method of googling the hell out of the error codes.  Any help would be appreciated! Thank you

---

### Post by TheFu on 2023-11-18
Which version of Ubuntu is being used?

---

### Post by machs on 2023-11-19
The server is on Ubuntu 22.04 and the client is on "Orange Pi 1.0.0 Jammy with Linux 5.4.125" which is a debian based distro with build in support for this single board computre hardware.

---

### Post by TheFu on 2023-11-20
Timeouts mean some part of the connection isn't working.  

Does ping from the client to the server work using the name or IP from the mount command?
Does the exports file on the server "know" the IP/name from the client and allow it?
Are all the specific ports needed opened between the systems?  I think there are 3 ports in v4 of NFS. One of them changes with each connection unless you force it to a specific value.  I'm using these for the NFS server:
```
$ sudo ufw status 
Status: active

To                         Action      From
--                         ------      ----
111                        ALLOW       172.22.22.0/24            
2049                       ALLOW       172.22.22.0/24            
13025                      ALLOW       172.22.22.0/24
```

/etc/default/nfs-kernel-server:
```
RPCMOUNTDOPTS="--manage-gids -p 13025"
```

I know nothing about OrangePi, but NFS works fine on my Raspberry Pi systems (2, 3, 4) running a customized Raspbian/Debian.

---

### Post by machs on 2023-11-21
Hi TheFu, thanks for getting back to me. 

Ping > connectivity from the client to the server works using the hostname. 
Exports >  on the server I am exporting 192.168.0.0/24 which should allow the client with address 192.168.0.246.  I also tried adding the client address to exports, no change in behaviour. 
Firewall > neither the client or the server are running ufw at this time
MountOpts > i don't have a port specified, only manage gids.  I tried adding a port and no change. 

I'm restarting the nfs-kernel-server with systemctl between config changes on the server.

from the server dmesg output
```

[477806.975229] nfsd: last server has exited, flushing export cache
[477807.149638] NFSD: Using nfsdcld client tracking operations.
[477807.149641] NFSD: starting 90-second grace period (net f0000000)
[477866.987975] NFSD: all clients done reclaiming, ending NFSv4 grace period (net f0000000)
```

not really sure what to make of that.

---

### Post by TheFu on 2023-11-21
Is /media/smilingBuddha always mounted, as in through the fstab?  Using a real mount, not gio or gvfs?

---

### Post by machs on 2023-11-21
yes, on the server smilingBuddha is statically mounted using fstab

```

machs@electricSheep:~$ cat /etc/fstab 
*snip*
UUID=38d81037-69c2-444c-8951-ba190423fdc6 /media/smilingBuddha auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

I've noticed that all of my clients are using a different nfs-common version.  orangepizero3 seems to be the latest version, 2.6.1 and the other clients (which work fine) are running 1.x.  I think I'll try to update nfs-common from source to the latest 2.6.4

---

### Post by machs on 2023-11-21
Humph. I built nfs-utils from source off git hub at version 2.6.3 (2.6.4 doesn't want to compile). installed. No change.

---

### Post by TheFu on 2023-11-21
I don't have any clues.

None of my systems run a 6.x kernel. 5.15 is the latest.  I avoid bleeding edge stuff.

I don't use any g-xxxxx stuff in the fstab, never mount storage under /media/ and always have fsck checks allowed through the fstab entry. Also, my exports file lists specific clients, never squashes root, doesn't hav a subnet, but I have used subnets there before.  With more than 3 mounts, I have needed to add an "fsid=" option to the exports.
I've used single system exports lines and used the line wrapping to have many systems listed. Both work, provided I didn't have any typos.

All my NFS shares use ext4 file system as the real storage.

and I don't specify NFS versions, let the systems negotiate the version for themselves.  I think you tried that already.

---

### Post by machs on 2023-11-23
a few other things I've tried with out any luck. 
- downgrading nfs-common on the client to version 1.3.4 using the debian buster deb
- using a docker image of an nfs-client
- spinning up a docker image of another nfs-server sharing a different directory

same results for each, if i leave off the version option it defaults to nfs 4.2 and throws a protocol erorr
if i specify vers=3 then it tries to connect then times out.

---

