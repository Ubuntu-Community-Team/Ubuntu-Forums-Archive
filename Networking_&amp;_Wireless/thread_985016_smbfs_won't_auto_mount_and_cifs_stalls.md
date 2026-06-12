---
title: "smbfs won't auto mount and cifs stalls"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by ukdoc on 2008-11-17
Hi

I've got a desktop running kubuntu gutsy. I also have a network drive with a fixed ip address.

I can mount the network drive without any problems.

```
sudo mount -t smbfs //192.168.2.220/netdrive /media/nwd -o credentials=/home/user_name/.smbpassword,uid=1000
```

I tried to add the following line to /etc/fstab

```
//192.168.2.220/netdrive /media/nwd smbfs credentials=/home/user_name/.smbpassword,uid=1000 0 0
```

Unfortunately after rebooting it doesn't seem to have mounted.

I can mount with cifs but whenever I try to copy a decent size file it whizzes along at first then the copy dialog box shows that the copy has stalled - if I leave it long enough it completes the copy.

Here's some output from networking commands.

```
eth0      Link encap:Ethernet  HWaddr 00:04:75:B4:01:42
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24501174 (23.3 MB)  TX bytes:516899688 (492.9 MB)
          Interrupt:11 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:596981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:310115020 (295.7 MB)  TX bytes:310115020 (295.7 MB)

```

```
 *-network
       description: Ethernet interface
       product: 3CSOHO100B-TX 910-A01 [tulip]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth0
       version: 31
       serial: 00:04:75:b4:01:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.2.101 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes

```

Can anyone give any suggestions as to where to go from here. I'd like to be able to automount my drive, and would preferably like to get cifs working as transfer speeds seem a lot faster, and I would eventually like to upgrade to hardy and intrepid - am I right in thinking there is no longer smbfs support? I'm a relative linux newbie so any replies will have to assume I have minimal technical knowledge.

---

### Post by mccartyj on 2008-11-19
[http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")

I had similar problems and this thread really helped. Maybe it's got what you need?

Good Luck!

---

