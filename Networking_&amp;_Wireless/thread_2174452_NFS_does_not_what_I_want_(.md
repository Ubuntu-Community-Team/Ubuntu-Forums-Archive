---
title: "NFS does not what I want :("
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by wimduk on 2013-09-14
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#0000ff][FONT=Ubuntu]**Problem SOLVED!**[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]

Dear Reader,[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]I want to share with NFS my[/FONT][/COLOR]** /home **[COLOR=#333333][FONT=Ubuntu]directory  from server [/FONT][/COLOR]**192.168.2.92**[COLOR=#333333][FONT=Ubuntu] with client [/FONT][/COLOR]**192.168.2.93**[COLOR=#333333][FONT=Ubuntu] via mountpoint [/FONT][/COLOR]**/media/share**[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]But it does not work ;(.[/FONT][/COLOR]

**Server actions.**
[COLOR=#333333][FONT=Ubuntu]1. apt-get install nfs-server-kernel[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]2. update /etc/exports[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   # Example for NFSv4:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   # /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   # /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   #[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]   /home  192.168.2.93(rw,sync,no_subtree_check)[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]3. command ps -ef | grep nfs output[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17766     2  0 13:09 ?        00:00:00 [nfsiod][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17990     2  0 13:09 ?        00:00:00 [nfsd4][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17991     2  0 13:09 ?        00:00:00 [nfsd4_callbacks][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17992     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17993     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17994     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17995     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17996     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17997     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17998     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root     17999     2  0 13:09 ?        00:00:00 [nfsd][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   wim      18360 18331  1 16:09 ?        00:00:03 /usr/bin/leafpad /home/wim/Dropbox/Netwerken/Share a remote harddrive/nfs_problem.txt[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   wim      18366 16902  0 16:13 pts/1    00:00:00 grep --color=auto nfs[/FONT][/COLOR]


**Client actions**
[COLOR=#333333][FONT=Ubuntu]1. apt-get install nfs-common (succesvol)[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]2. update /etc/fstab[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   # Koppelen 192.168.2.92:/home aan /media/share[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   192.168.2.92:/home /media/share   nfs  rw,hard,intr 0 0[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]3. make mountpoint /media/share[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   drwxrwxrwx 2 root root 4096 sep 14 13:40 share[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]4. client "sees" server (ping)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   PING 192.168.2.92 (192.168.2.92) 56(84) bytes of data.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   64 bytes from 192.168.2.92: icmp_req=1 ttl=64 time=3.53 ms[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   64 bytes from 192.168.2.92: icmp_req=2 ttl=64 time=4.33 ms[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]5. command ps -ef | grep nfs output[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root       962   315  0 14:51 ?        00:00:00 mount -t nfs -o rw,hard,intr 192.168.2.92:/home /media/share[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root       963   962  0 14:51 ?        00:00:00 /sbin/mount.nfs 192.168.2.92:/home /media/share -o rw,hard,intr[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   root      1085     2  0 14:51 ?        00:00:00 [nfsiod][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]   wim       2661  2527  0 14:56 pts/0    00:00:00 grep --color=auto nfs[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]Every suggestion is welcome[/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu]Many thanks in advancee,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]wimduk[/FONT][/COLOR]

---

### Post by Merrattic on 2013-09-14
A few things:

```
sudo apt-get install nfs-kernel-server
``` (not nfs-server-kernel)
Did you start the server?
```
 sudo service nfs-kernel-server start
```
Did you install rpcbind on the client (used to be portmap)
```
sudo apt-get install rpdbind
```

my favourite how to here [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by wimduk on 2013-09-14
Hello [COLOR=#000000]Merrattic,

Many thanks for your fast reply, great!
nfs-server-kernel is a typo, sorry for that (Newbie he) [/COLOR]:oops:[COLOR=#000000]
nfs is up and running, as far as I can see.

On the client rpcbind is NOT installed. I have some questions about this package;
1. what is the function?
2. If this is important, why is this not mentioned in the doscumentation I read so  far? ([/COLOR][COLOR=#000000]I have seen, and read, a lot of nfs stuff but I did not found a complete "step by step" manual for the first time user (whatI am))[/COLOR][COLOR=#000000]
3. what command can I execute to check the correct working of rpcbind?

[/COLOR][COLOR=#000000]Again, many thanks and with kind regards,[/COLOR][COLOR=#000000]
wimduk[/COLOR]

---

### Post by wimduk on 2013-09-15
[COLOR=#000000]Hello [/COLOR][COLOR=#000000][COLOR=#000000]Merrattic,

rpcbind installed, but no succes.
command mount -av gives "no route to host", but ping works (both sides)
Any idea?

kind regards,
wimduk

[/COLOR][/COLOR]

---

### Post by SeijiSensei on 2013-09-15
Are you trying to mount the share as the client's root user?  If so, the exported share must have the "no_root_squash" parameter included in /etc/exports.  See "[man exports](http://linux.die.net/man/5/exports) for details.

---

### Post by wimduk on 2013-09-15
Hello SeijSensei,
 
Thanks for your reply. I just want to logon as a normal user.
[SIZE=1][COLOR=#000000][SIZE=2]
I processed also the Rcpinfo -p command and these are the results[/SIZE]

[/COLOR][/SIZE]Server: rcpinfo -p localhost output
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  35230  status
    100024    1   tcp  51043  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  37420  nlockmgr
    100021    3   udp  37420  nlockmgr
    100021    4   udp  37420  nlockmgr
    100021    1   tcp  52075  nlockmgr
    100021    3   tcp  52075  nlockmgr
    100021    4   tcp  52075  nlockmgr
    100005    1   udp  43314  mountd
    100005    1   tcp  56998  mountd
    100005    2   udp  37317  mountd
    100005    2   tcp  59040  mountd
    100005    3   udp  34373  mountd
    100005    3   tcp  49717  mountd


Client: rcpinfo -p 192.168.2.92 output (from client to server)
[COLOR=#ff0000]_*** no output, mothing happens***_[/COLOR]

 Any idea?

With kind regards,
wimduk

---

### Post by wimduk on 2013-09-16
Dear all,

Problem SOLVED ;) A firewall was running on the server.

Many thanks for your support!

With kind regards, wimduk

---

