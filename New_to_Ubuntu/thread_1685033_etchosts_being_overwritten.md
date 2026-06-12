---
title: "/etc/hosts being overwritten?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by mr_luksom on 2011-02-10
Hi,

I have no idea what I have done to cause this, however my /etc/hosts file is being overwritten on startup.

Any ideas on what I have messed up, and how to get it back?

I used to have a bash that looks like this:
```

glen@mythsrvgk01$

```

Now it looks like this:
```

glen@localhost	127:
[CODE]

/etc/hosts, if I change it, it will still look like this on reboot. The clue seems to be that the bash line looks like the first /etc/hosts line.

[CODE]
10.1.1.4	localhost	127.0.0.1
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	localhost	127.0.0.1
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost6.localdomain6	localhost6
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost.localdomain	localhost
::1	localhost	127.0.0.1
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost6.localdomain6	localhost6
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost.localdomain	localhost
::1	localhost	127.0.0.1
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost6.localdomain6	localhost6
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost.localdomain	localhost
::1	localhost	127.0.0.1
mythsrvgk01	10.1.1.3
mythsrvgk02	10.1.1.4	localhost	127	localhost6.localdomain6	localhost6
mythsrvgk01	10.1.1.3

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

ifconfig output if it helps:
```


eth0      Link encap:Ethernet  HWaddr 00:1a:4d:60:67:d9  
          inet addr:10.1.1.4  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe60:67d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:310799 (310.7 KB)  TX bytes:112903 (112.9 KB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51196 (51.1 KB)  TX bytes:51196 (51.1 KB)

```

---

### Post by mr_luksom on 2011-02-10
It turns out there was something amiss with my hostname file, it basically had /etc/hosts in it, causing network manager to edit the /etc/hosts file to be a little silly.

Lesson to be learnt - /etc/hosts is quite different to /etc/hostname (machine name!).

---

