---
title: "[SOLVED] Hardy 8.04 NFS stopped working after update"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Chachee on 2008-09-25
Greetings all,
  Been lurking and reading through threads, but didn't really see anything that helped me.  So I'm posting my own.

  I have a FreeNAS server (based on FreeBSD) sharing NFS and CIFS/SMB on my home network.  Up until last week when I did a rather large update after a week vacation everything was great and my NFS shares would load on login.  After that update though, I get this - 

```
 sudo mount -a
mount.nfs: internal error

```

  I can still see the CIFS shares, though I'd rather use NFS on my Linux systems since it's much easier and robust than the CIFS.  And besides gaming I'm trying to do everything in an Open Source sorta way.

  Here's what I've got running and various helpful commands I've seen in other threads:

```
IP Addy's:
Server - 192.168.1.3 /24
jeremy-desktop - DHCP from router, currently 192.168.1.104 /24
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ff843bc4-e0db-40e6-8e3b-5d1b74dd10d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a85c0234-cec7-4474-a473-e397688b3918 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
192.168.1.3:/mnt/Backup /home/jeremy/Backup nfs defaults 0 0 
192.168.1.3:/mnt/Videos /home/jeremy/Videos nfs defaults 0 0
192.168.1.3:/mnt/Music /home/jeremy/Music nfs defaults 0 0
```

```
 rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp  45875  status
    100024    1   tcp  37390  status
    100000    2   udp    111  portmapper

```

```
 ps ax | grep portmap
 6957 ?        Ss     0:00 /sbin/portmap
 6989 pts/0    R+     0:00 grep portmap

```

```

[COLOR="Red"]NFS service off on server-[/COLOR]
nc -zv 192.168.1.3 1-10000
server.local [192.168.1.3] 873 (rsync) open
server.local [192.168.1.3] 445 (microsoft-ds) open
server.local [192.168.1.3] 139 (netbios-ssn) open
server.local [192.168.1.3] 80 (www) open
server.local [192.168.1.3] 22 (ssh) open
server.local [192.168.1.3] 21 (ftp) open

[COLOR="Red"]NFS Service on -[/COLOR]
jeremy@jeremy-desktop:/$ nc -zv 192.168.1.3 1-10000
server.local [192.168.1.3] 2049 (nfs) open
server.local [192.168.1.3] 936 (?) open
server.local [192.168.1.3] 873 (rsync) open
server.local [192.168.1.3] 692 (?) open
server.local [192.168.1.3] 605 (?) open
server.local [192.168.1.3] 445 (microsoft-ds) open
server.local [192.168.1.3] 139 (netbios-ssn) open
server.local [192.168.1.3] 111 (sunrpc) open
server.local [192.168.1.3] 80 (www) open
server.local [192.168.1.3] 22 (ssh) open
server.local [192.168.1.3] 21 (ftp) open

```

```
jeremy@jeremy-desktop:/$ showmount -d 192.168.1.3
rpc mount dump: RPC: Timed out

```

```
Server Processes:
last pid:  2533;  load averages:  0.00,  0.00,  0.00  up 0+01:18:48    13:56:03
28 processes:  1 running, 27 sleeping

Mem: 12M Active, 11M Inact, 19M Wired, 12K Cache, 11M Buf, 890M Free
Swap:


  PID USERNAME  THR PRI NICE   SIZE    RES STATE    TIME   WCPU COMMAND
 1031 root        1   4    0  3400K  2480K kqread   0:00  0.00% lighttpd
 2531 root        1  -8    0 10416K  8084K piperd   0:00  0.00% php
  876 root        1  76    0  5492K  3316K select   0:00  0.00% nmbd
 2413 root        1  76    0  1396K  1132K select   0:00  0.00% nfsd
  880 root        1  76    0  8028K  4776K select   0:00  0.00% smbd
  804 root        1  76    0  1400K  1000K select   0:00  0.00% syslogd
 2502 root        1  76    0  1484K  1100K select   0:00  0.00% mDNSResponderPosix
 2275 root        1  76    0  1504K  1220K select   0:00  0.00% rpcbind
 2365 root        1  76    0  1556K  1312K select   0:00  0.00% mountd
 1154 root        1   8    0  1732K  1436K wait     0:00  0.00% login
 1156 root        1  20    0  2836K  1748K pause    0:00  0.00% csh
 1162 root        1   5    0  1840K  1396K ttyin    0:00  0.00% sh
 1090 root        1   8    0  1372K  1016K nanslp   0:00  0.00% cron
 1375 root        1  76    0  1668K  1440K select   0:00  0.00% rpc.lockd
  943 root        1  76    0  3640K  1912K select   0:00  0.00% pure-ftpd
  897 root        1   8    0  2512K  1736K nanslp   0:00  0.00% smartd
 2455 root        1  76    0   257M  1172K select   0:00  0.00% rpc.statd
  854 root        1  76    0  2856K  2336K select   0:00  0.00% sshd

```

  I've tried to supply as much info as possible.  I have restarted everything multiple times.  I've reinstalled nfs-common multiple times.

  I tried the patch here: [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444/comments/23](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/213444/comments/23) to no avail.

  However this bug: [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/251923]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/251923") makes me think that it might be related to different versions of NFS used by the server and the box.

  Not really sure where to go, though I'm looking to learn and any pointers are very helpful.  If more info is required please let me know.

JT

---

### Post by Chachee on 2008-09-25
Had a brand new computer with 8.04 installed and it doesn't work on there either.

Trying to round up the info from the server to.  SSH'd to it and got - 

```
server:/etc# cat exports
/mnt/Videos/ -alldirs -mapall=root -network 192.168.1.0 -mask 255.255.255.0

/mnt/Music/ -alldirs -mapall=root -network 192.168.1.0 -mask 255.255.255.0

/mnt/Backup/ -alldirs -mapall=root -network 192.168.1.0 -mask 255.255.255.0

```

Thanks.

JT

---

### Post by alaya.zied on 2008-09-25
I have the same problem.
I followed this toto: [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
and all works good the first time.
few days later, after an update, I got 'nfs internal error' each time !!!

I tried to re-follow the same tot, restart all services, but nothink !

it's very important to me, I have multiple Go of data and it's not easy.

please help.

---

### Post by Chachee on 2008-09-26
Still having issue.

---

### Post by Chachee on 2008-09-28
Still nothing?

---

### Post by alaya.zied on 2008-10-02
some idea to try fix this please ?

---

### Post by pinkunicorn on 2008-10-15
I get the same error on a freshly installed 8.04 machine. I've tried reinstalling nfs-common to no avail. This machine was installed with Gutsy today (since that's the boot disk I happened to have handy) and immediately upgraded to Hardy.

My previous work station mounted the same share flawlessly from Hardy, so one would expect this to be solvable.

---

### Post by Chachee on 2008-10-16
And yet still nothing.  This makes my ubuntu partition useless since I can't get to my movies/music with Amarok.

How lame...

JT

---

### Post by Chachee on 2008-10-30
Does anyone know if the new update is going to fix this problem?

---

### Post by dmizer on 2008-10-30
My NFS shares work with no problem in 8.04. Try the howto located in the forth link in my sig.

---

### Post by Chachee on 2008-11-01
I'll give it a shot again and let you know.

---

### Post by Chachee on 2008-11-29
Upgraded to 8.10 and now it works.  Very lame, to be honest.  I expect more out of my brew!

Like Ibex though.. just wish it wouldn't lock up all the time.

JT

---

