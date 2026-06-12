---
title: "Strange &quot;No route to host&quot;-behavior - arp sometimes incomplete?"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by tobnels on 2015-03-23
Hi all,

my laptop (Ubuntu 14.04) is (directly) connected to my Raspberry Pi via an ethernet cabel.

I gave both of them a static IP, installed SSH and *most of the time* I can connet via SSH from my  laptop to the Raspberry Pi just fine.

However, sometimes (seems to be randomly?) I get 
```

$ ssh pi@192.168.100.20
ssh: connect to host 192.168.100.20 port 22: No route to host

```

Although the *route* output is correct, and the ssh server is running on the Rasberry Pi (I checked it).

But I noticed that if I get the error the ARP entry is incorrect (see the first linle):
```

$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.100.20                   (incomplete)                              eth0
X                         ether   Y                  C                     wlan0

```

I tried adding a static arp entry (with a value for HWwaddress taken from a session where connecting to the Rasberry Pi worked), but I still couldn't connect (same error).

Sometimes it then helps to restart my laptop (sometimes it doesn't).
Sometimes it then helps to restart the Rasberry Pi (sometime it doesn't).

This appears to be random and I cannot find a pattern what is wrong... do you have any idea?

Best regards

---

### Post by SeijiSensei on 2015-03-23
I've seen that error when the routing is correct, but the SSH server is down.  In these cases I can ping the server so I know there is not a routing problem.  It seems to be a bogus error diagnosis from the SSH client.

---

### Post by tobnels on 2015-03-24
In my case if this problem occurs,

- I cannot ping:
> 
$ ping 192.168.100.20
PING 192.168.100.20 (192.168.100.20) 56(84) bytes of data.
From 192.168.100.78 icmp_seq=1 Destination Host Unreachable
From 192.168.100.78 icmp_seq=2 Destination Host Unreachable
From 192.168.100.78 icmp_seq=3 Destination Host Unreachable
From 192.168.100.78 icmp_seq=4 Destination Host Unreachable

- the SSH server is running fine (I checked that it is up and listening on port 22)

---

