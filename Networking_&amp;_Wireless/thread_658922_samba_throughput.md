---
title: "samba throughput"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by detectiveinspekta on 2008-01-05
I am using linux on my main desktop and get around 4MB/s downloading a 700MB video from another linux server. I tested it by using:
```

time cp /media/share/videos/vid1.avi ~/

```
This downloaded in about 2 min 30s.
I downloaded the same file using apache this time it downloaded in about 1 min 30s.

So somehow I can download files faster in apache, however I want the ability to share files under samba (with windows clients) at similar speeds.

Just as a test I booted to windowsxp and tested the same file (downloaded and uploaded in around 1min 30s.


So I'm guessing there is something wrong with my drivers (but apache works) or my smb client. I have limited knowleage i

```

jonathan@jonathan-desktop:~$ dmesg | grep eth0
[   50.695170] eth0: forcedeth.c: subsystem: 010de:0c11 bound to 0000:00:04.0
[   78.127467] eth0: no IPv6 routers present

```

```

...
...
[files]
path = /media/files
comment = movies series
public = yes
browsable = yes
public = yes
writable = no
create mask = 0777
directory mask = nobody
force group = nogroup

```
using share security btw

---

### Post by detectiveinspekta on 2008-01-05
```

jonathan@jonathan-desktop:~$ sudo mii-toolSIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found

```

```

eth0      Link encap:Ethernet  HWaddr 10:00:00:00:00:00  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2054920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2019034131 (1.8 GiB)  TX bytes:915713769 (873.2 MiB)
          Interrupt:18 

```

---

### Post by Orfintain on 2008-01-05
Looks like you don't have IPV6 enabled you can turn that on again, Genenerally you want it on less you are using something that dosn't work with it (like VM ware)

---

### Post by detectiveinspekta on 2008-01-05
I think that log message is saying it cant find any ipv6 routers on the network. Which I don't, I doubt this is the problem.

---

### Post by detectiveinspekta on 2008-01-05
```

smbclient //mycomp/share/

->get vid.avi


```

surprisingly this downloaded pretty fast 1min 30s. So it must be Nautilus or Gnomes problem.

---

