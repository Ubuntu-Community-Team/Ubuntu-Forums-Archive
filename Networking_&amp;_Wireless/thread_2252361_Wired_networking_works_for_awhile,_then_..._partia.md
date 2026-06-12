---
title: "Wired networking works for awhile, then ... partially"
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by Brian_Binder on 2014-11-11
Hi there everyone - working on Ubuntu 14.04.1 LTS and I'm running in to a problem that I'm curious if others have run into before.  The main issue is that the machine will stop communicating with other devices, randomly.  In the example below, you'll see that it can't ping its own default gateway, but it can ping Google's DNS with no problem.

```
support@monitor:~$ ping 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=48 time=18.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=48 time=20.0 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 18.706/19.357/20.009/0.666 ms
support@monitor:~$ ping 172.20.8.1
PING 172.20.8.1 (172.20.8.1) 56(84) bytes of data.
^C
--- 172.20.8.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4998ms


support@monitor:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=48 time=18.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=48 time=19.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=48 time=18.7 ms
^C
--- 172.20.9.10 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 0.170/0.239/0.315/0.048 ms
support@monitor:~$ ping 172.20.1.10
PING 172.20.1.10 (172.20.1.10) 56(84) bytes of data.
64 bytes from 172.20.1.10: icmp_seq=1 ttl=126 time=0.722 ms
64 bytes from 172.20.1.10: icmp_seq=2 ttl=126 time=0.724 ms
64 bytes from 172.20.1.10: icmp_seq=3 ttl=126 time=0.863 ms
64 bytes from 172.20.1.10: icmp_seq=4 ttl=126 time=1.00 ms
64 bytes from 172.20.1.10: icmp_seq=5 ttl=126 time=0.743 ms
64 bytes from 172.20.1.10: icmp_seq=6 ttl=126 time=0.731 ms
64 bytes from 172.20.1.10: icmp_seq=7 ttl=126 time=0.758 ms
^C
--- 172.20.1.10 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5998ms
rtt min/avg/max/mdev = 0.722/0.792/1.003/0.097 ms
```

I have running notes, as well as some of the commonly requested items that people ask for, including in this link here:
[https://www.evernote.com/l/AAHFME1oNWlLm4SRtrE9rZeuS1-JssNLuWQ](https://www.evernote.com/l/AAHFME1oNWlLm4SRtrE9rZeuS1-JssNLuWQ)

So the system can ping other machines in other VLANs, but not the default gateway, yet the default gateway can ping the machine just fine.  Downing the NIC and bringing it back up makes everything right again, but only for a limited time ... which is random.  Could be great for 1 hour or 8 hours.  172.20.8.1 is a router and no ACL's are blocking anything for this device whatsoever.  I can take this machine offline, and replace it with a Windows machine with all of the same settings and ping the address(es) all day long.  So I'm thinking there's something specific to the install (NIC or driver possibly) itself and configuration but haven't found it yet.

Any thoughts?
Thanks,
Brian

---

