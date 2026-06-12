---
title: "eth0 grinds to a halt"
date: 2005-09-27
forum: Networking &amp; Wireless
---

### Post by mr_mop on 2005-09-27
On my hoary machine I can download things from the internet without any real problems (an example, I used the machine to install ubuntu :)
The problem is that I am using the machine as a samba server and the ethernet grinds to a halt.  The ping goes sky high and file transfers time out.
Does anyone have any ideas? I've changed the ethernet card and get the same symptoms.

This ping trace was taken when trying to transfer files from the samba server.    

```

ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.90 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.713 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.575 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.619 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.571 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.564 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.641 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.568 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.579 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=0.731 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=0.574 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=0.574 ms
64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=0.702 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=0.658 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=0.572 ms
64 bytes from 192.168.0.1: icmp_seq=16 ttl=64 time=0.687 ms
64 bytes from 192.168.0.1: icmp_seq=17 ttl=64 time=0.663 ms
64 bytes from 192.168.0.1: icmp_seq=18 ttl=64 time=0.563 ms
64 bytes from 192.168.0.1: icmp_seq=19 ttl=64 time=0.629 ms
64 bytes from 192.168.0.1: icmp_seq=20 ttl=64 time=0.663 ms
64 bytes from 192.168.0.1: icmp_seq=21 ttl=64 time=0.569 ms
64 bytes from 192.168.0.1: icmp_seq=22 ttl=64 time=0.570 ms
64 bytes from 192.168.0.1: icmp_seq=23 ttl=64 time=0.580 ms
64 bytes from 192.168.0.1: icmp_seq=24 ttl=64 time=0.673 ms
64 bytes from 192.168.0.1: icmp_seq=25 ttl=64 time=0.580 ms
64 bytes from 192.168.0.1: icmp_seq=26 ttl=64 time=0.568 ms
64 bytes from 192.168.0.1: icmp_seq=27 ttl=64 time=0.570 ms
64 bytes from 192.168.0.1: icmp_seq=28 ttl=64 time=0.560 ms
64 bytes from 192.168.0.1: icmp_seq=29 ttl=64 time=0.575 ms
64 bytes from 192.168.0.1: icmp_seq=30 ttl=64 time=0.582 ms
64 bytes from 192.168.0.1: icmp_seq=31 ttl=64 time=0.680 ms
64 bytes from 192.168.0.1: icmp_seq=32 ttl=64 time=0.646 ms
64 bytes from 192.168.0.1: icmp_seq=33 ttl=64 time=0.584 ms
64 bytes from 192.168.0.1: icmp_seq=34 ttl=64 time=0.559 ms
64 bytes from 192.168.0.1: icmp_seq=35 ttl=64 time=0.580 ms
64 bytes from 192.168.0.1: icmp_seq=36 ttl=64 time=0.631 ms
64 bytes from 192.168.0.1: icmp_seq=37 ttl=64 time=0.579 ms
64 bytes from 192.168.0.1: icmp_seq=38 ttl=64 time=0.695 ms
64 bytes from 192.168.0.1: icmp_seq=39 ttl=64 time=0.613 ms
64 bytes from 192.168.0.1: icmp_seq=40 ttl=64 time=0.561 ms
64 bytes from 192.168.0.1: icmp_seq=41 ttl=64 time=0.641 ms
64 bytes from 192.168.0.1: icmp_seq=42 ttl=64 time=0.580 ms
64 bytes from 192.168.0.1: icmp_seq=43 ttl=64 time=0.575 ms
64 bytes from 192.168.0.1: icmp_seq=44 ttl=64 time=0.569 ms
64 bytes from 192.168.0.1: icmp_seq=45 ttl=64 time=0.708 ms
64 bytes from 192.168.0.1: icmp_seq=46 ttl=64 time=0.676 ms
64 bytes from 192.168.0.1: icmp_seq=47 ttl=64 time=0.601 ms
64 bytes from 192.168.0.1: icmp_seq=49 ttl=64 time=0.633 ms
64 bytes from 192.168.0.1: icmp_seq=48 ttl=64 time=1000 ms
64 bytes from 192.168.0.1: icmp_seq=50 ttl=64 time=201 ms
64 bytes from 192.168.0.1: icmp_seq=58 ttl=64 time=0.575 ms
64 bytes from 192.168.0.1: icmp_seq=51 ttl=64 time=7005 ms
64 bytes from 192.168.0.1: icmp_seq=52 ttl=64 time=6005 ms
64 bytes from 192.168.0.1: icmp_seq=53 ttl=64 time=5004 ms
64 bytes from 192.168.0.1: icmp_seq=54 ttl=64 time=4003 ms
64 bytes from 192.168.0.1: icmp_seq=55 ttl=64 time=3003 ms
64 bytes from 192.168.0.1: icmp_seq=56 ttl=64 time=2002 ms
64 bytes from 192.168.0.1: icmp_seq=57 ttl=64 time=1001 ms
64 bytes from 192.168.0.1: icmp_seq=68 ttl=64 time=0.560 ms
64 bytes from 192.168.0.1: icmp_seq=59 ttl=64 time=9007 ms
64 bytes from 192.168.0.1: icmp_seq=60 ttl=64 time=8007 ms
64 bytes from 192.168.0.1: icmp_seq=61 ttl=64 time=7006 ms
64 bytes from 192.168.0.1: icmp_seq=62 ttl=64 time=6005 ms
64 bytes from 192.168.0.1: icmp_seq=63 ttl=64 time=5004 ms
64 bytes from 192.168.0.1: icmp_seq=64 ttl=64 time=4003 ms
64 bytes from 192.168.0.1: icmp_seq=65 ttl=64 time=3003 ms
64 bytes from 192.168.0.1: icmp_seq=66 ttl=64 time=2002 ms
64 bytes from 192.168.0.1: icmp_seq=67 ttl=64 time=1001 ms
64 bytes from 192.168.0.1: icmp_seq=69 ttl=64 time=12245 ms
64 bytes from 192.168.0.1: icmp_seq=70 ttl=64 time=11245 ms
64 bytes from 192.168.0.1: icmp_seq=71 ttl=64 time=10244 ms
64 bytes from 192.168.0.1: icmp_seq=75 ttl=64 time=6240 ms
64 bytes from 192.168.0.1: icmp_seq=76 ttl=64 time=5240 ms
64 bytes from 192.168.0.1: icmp_seq=77 ttl=64 time=4239 ms
64 bytes from 192.168.0.1: icmp_seq=78 ttl=64 time=3238 ms
64 bytes from 192.168.0.1: icmp_seq=79 ttl=64 time=2237 ms
64 bytes from 192.168.0.1: icmp_seq=80 ttl=64 time=1236 ms
64 bytes from 192.168.0.1: icmp_seq=81 ttl=64 time=235 ms
64 bytes from 192.168.0.1: icmp_seq=92 ttl=64 time=0.575 ms
64 bytes from 192.168.0.1: icmp_seq=82 ttl=64 time=10008 ms
64 bytes from 192.168.0.1: icmp_seq=83 ttl=64 time=9008 ms
64 bytes from 192.168.0.1: icmp_seq=84 ttl=64 time=8007 ms
64 bytes from 192.168.0.1: icmp_seq=85 ttl=64 time=7006 ms
64 bytes from 192.168.0.1: icmp_seq=86 ttl=64 time=6005 ms
64 bytes from 192.168.0.1: icmp_seq=87 ttl=64 time=5004 ms
64 bytes from 192.168.0.1: icmp_seq=88 ttl=64 time=4004 ms
64 bytes from 192.168.0.1: icmp_seq=89 ttl=64 time=3003 ms
64 bytes from 192.168.0.1: icmp_seq=90 ttl=64 time=2002 ms
64 bytes from 192.168.0.1: icmp_seq=91 ttl=64 time=1001 ms
64 bytes from 192.168.0.1: icmp_seq=98 ttl=64 time=0.568 ms
64 bytes from 192.168.0.1: icmp_seq=93 ttl=64 time=5004 ms
64 bytes from 192.168.0.1: icmp_seq=94 ttl=64 time=4003 ms
64 bytes from 192.168.0.1: icmp_seq=95 ttl=64 time=3003 ms
64 bytes from 192.168.0.1: icmp_seq=96 ttl=64 time=2002 ms
64 bytes from 192.168.0.1: icmp_seq=97 ttl=64 time=1001 ms

--- 192.168.0.1 ping statistics ---
105 packets transmitted, 95 received, 9% packet loss, time 104070ms
rtt min/avg/max/mdev = 0.559/2113.422/12245.709/3122.289 ms, pipe 13

``` :confused:

---

### Post by nocturn on 2005-09-27
This seems like some problem between the Samba server and the clients.

The NetBIOS protocol can send a lot of traffic over a network, specially when there is a misconfiguration.

---

### Post by mr_mop on 2005-09-27
Thanks for that. :D

Should I disable NetBIOS on the server and clients?

Where would the misconfiguration likely be? In the samba config file? Or in the the way the network is set up?
I think I am using fixed IP addresses for all of the machines in the network.

---

### Post by nocturn on 2005-09-27
[QUOTE=mr_mop]Thanks for that. :D

Should I disable NetBIOS on the server and clients?

Where would the misconfiguration likely be? In the samba config file? Or in the the way the network is set up?
I think I am using fixed IP addresses for all of the machines in the network.[/QUOTE]

Are you connecting to Samba with Windows clients?  Is so, what version?

You can use a tool like ethereal to sniff network activity, this can help identify the source of the problems.

---

### Post by mr_mop on 2005-09-27
The clients are Windows XP Home boxes that are pretty much 'as installed' by the install CD.  the only change I made is setting the IP address, netmask and DNS entries.  Also I added File and Printer sharing to the Windows Firewall.

The samba server is set to allow read and write access to the home directories of the particular users.

What should I look for in the Ethereal logs? Traffic coming from the Windows boxes 'swamping' other traffic?  Would it be helpful to look at server and client side or only client?

Thanks
MM

---

### Post by mr_mop on 2005-10-07
OK, so I have got an ethereal trace for you to look at. Can anyone see what might be going on.  I was trying to download a directory of files from the ubuntu samba box (192.168.0.7) to an Win XP box.
Then I did some pings to my router at the end to see when the problem had happened. :confused:

I have attached a log file.

---

### Post by mr_mop on 2006-04-13
OK, so I've come back to this same problem.
Anyone else seen this type of thing?

---

