---
title: "NFS mount does not work"
date: 2017-01-14
forum: Networking &amp; Wireless
---

### Post by Kjeldgaard on 2017-01-14
Hi all,

I am trying to mount a NFS share on a client machine, but the mount command times out.

**Server info:**
OS: Raspbian GNU/Linux 8.0 (jessie)
```
cat /etc/exports# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/MediaHdd 192.168.87.0/24(rw,sync,no_subtree_check)

```
Local IP address: 192.168.87.113
Hostname: raspberrypi

[B]Client info:
[/B]OS: Ubuntu 16.04 LTS
Local IP address: 192.168.87.112

I have tried the following mount commands on the client:
```
sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.87.113:/media/MediaHdd /media/RaspberryHdd/
```
returns
```
mount.nfs4: Connection timed out
```

```
sudo mount -t nfs4 -o proto=tcp,port=2049 //192.168.87.113:/media/MediaHdd /media/RaspberryHdd/
```
returns
```
mount.nfs4: Failed to resolve server //192.168.87.113: Name or service not known
```

```
 sudo mount -t nfs4 -o proto=tcp,port=2049 raspberrypi:/media/MediaHdd /media/RaspberryHdd/
```
returns
```
mount.nfs4: Failed to resolve server raspberrypi: Name or service not known
```

```
sudo mount 192.168.87.113:/media/MediaHdd /media/RaspberryHdd/
```
returns
```
mount.nfs: Connection timed out
```

BTW, ping works fine
```
ping 192.168.87.113PING 192.168.87.113 (192.168.87.113) 56(84) bytes of data.
64 bytes from 192.168.87.113: icmp_seq=1 ttl=64 time=0.240 ms
64 bytes from 192.168.87.113: icmp_seq=2 ttl=64 time=0.337 ms
64 bytes from 192.168.87.113: icmp_seq=3 ttl=64 time=0.349 ms
64 bytes from 192.168.87.113: icmp_seq=4 ttl=64 time=0.321 ms
64 bytes from 192.168.87.113: icmp_seq=5 ttl=64 time=0.335 ms
^C
--- 192.168.87.113 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.240/0.316/0.349/0.042 ms
```
and so does ssh.

```
 ssh pi@192.168.87.113pi@192.168.87.113's password:


The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat Jan 14 11:19:46 2017 from 192.168.87.190
```

So why does NFS not work? What am I missing?

I have already searched for the answer here with out any luck:
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)
[https://ubuntuforums.org/showthread.php?t=249889](https://ubuntuforums.org/showthread.php?t=249889)
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

BR,
Kjeldgaard

---

### Post by Kjeldgaard on 2017-01-14
Ok, I have found the solution here:
[https://www.raspberrypi.org/forums/viewtopic.php?f=36&t=14500&sid=ba54e4571a9ca0be8fb8a0980fd62333&start=25](https://www.raspberrypi.org/forums/viewtopic.php?f=36&t=14500&sid=ba54e4571a9ca0be8fb8a0980fd62333&start=25)

I have to run
```
$sudo service rpcbind restart
$sudo service nfs-kernel-server restart
```
after each reboot.

---

