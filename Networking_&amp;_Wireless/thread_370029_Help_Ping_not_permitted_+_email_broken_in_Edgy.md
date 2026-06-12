---
title: "Help: Ping not permitted + email broken in Edgy"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by joneall on 2007-02-25
I'm not sure what happened, I just did a mod to fix a previously incomplete java installation (by Adept). Since, I can't send or receive any email (Thunderbird), but web access via Firefox works fine.  Also nslookup works, but not ping.

jon@kubuntu-jon:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.048 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.048 ms

jon@kubuntu-jon:~$ nslookup smtp.nerim.net
Server:         192.168.1.254
Address:        192.168.1.254#53

Name:   smtp.nerim.net
Address: 62.4.16.95
Name:   smtp.nerim.net
Address: 62.4.17.82

jon@kubuntu-jon:~$ ping 62.4.16.95
PING 62.4.16.95 (62.4.16.95) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

Here's my ifconfig

jon@kubuntu-jon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:17:5C:34
          inet addr:192.168.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5765867 (5.4 MiB)  TX bytes:730070 (712.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1604 (1.5 KiB)  TX bytes:1604 (1.5 KiB)

As far as I know, I'm not running a firewall.  I don't see anything firewall-like is "ps -edf". And the /etc/hosts.{allow|deny} files contain only commented lines.

What could be wrong here?  I'd really like to be able to use my email again!  :(

---

### Post by joneall on 2007-02-25
I just rebooted the machine and now Thunderbird works.  (Thank goo'ness!)  But I still can't ping.anything but localhost.  Is this normal?

---

### Post by sadjack on 2007-02-25
If you can ping localhost this suggests that ping is working. The fact that you cannot get out from your computer suggests to me that your network settings are not correct. 

Are you using DHCP to allocate IP addresses? Are your DNS settings correct?

---

