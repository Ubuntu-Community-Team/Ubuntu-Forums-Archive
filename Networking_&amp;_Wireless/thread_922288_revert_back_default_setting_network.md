---
title: "revert back default setting network"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by donjo on 2008-09-17
hi,i need to revert my default setting network for ubuntu.
using wired connection..
after some upgrade of network, it was crashed,and i unable to use wired connection at all
now using my friends laptop..

how to set back network configuration to original setting ha?
please

---

### Post by Iowan on 2008-09-17
Dunno about reloading defaults, but you should be able to fix what broke... Drivers might be difficult, but basic network settings might solve the problem.  **/etc/network/interfaces** file should have a section similar to:```
auto eth0
iface eth0 inet dhcp
```

---

### Post by donjo on 2008-09-17
> **Iowan said:**
> Dunno about reloading defaults, but you should be able to fix what broke... Drivers might be difficult, but basic network settings might solve the problem.  **/etc/network/interfaces** file should have a section similar to:```
auto eth0
iface eth0 inet dhcp
```

i have done that, but still unable to use my network,
please help me..
i just need to redo what i have done before,
what the step??

---

### Post by Iowan on 2008-09-17
Post results of **ifconfig**.  Do you have a firewall running?

---

### Post by donjo on 2008-09-17
> **Iowan said:**
> Post results of **ifconfig**.  Do you have a firewall running?

not have firewall,
it happen just after some upgrading that made crash,
so that the problem,
crash happen,and i can't use my network manager anymore,
it said no network connection

for ifconfig,i can't show here, becoz now i'm using another laptop,
but it show that there is no ip address found,

---

### Post by donjo on 2008-09-17
ok this is my ifconfig :```


root@scorps-laptop:/media/f/NetworkManager-0.6.5# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:fc:0d:5e  
          inet6 addr: fe80::216:d3ff:fefc:d5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91189 (91.1 KB)  TX bytes:7411 (7.4 KB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3958 (3.9 KB)  TX bytes:3958 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:1a:73:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-00-00-1A-73-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```



# sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main

```

this problem happen after i do this update,
i add the last two line, and i think that made error..

so i hope to revert back, 

and how can i install back gnome network manager??
i already download NetworkManager-0.6.5.tar.gz file,extract it,
but don't know how to install it

when i type make install isaid error on sometihng,
./configure also same..
:confused:
so what should i do??
please...:(

---

### Post by donjo on 2008-09-18
anyone can help me please ????
please :(

---

### Post by donjo on 2008-09-18
err.. why ?
why there is no one can solve my problem??
my ubuntu still can't get connection...
what should i do ??
owh please friends

---

### Post by donjo on 2008-09-21
and why every time i want to online,
i need to do this


```
sudo etc/init.d/networking restart
```


if i dont do this , i can't get ip address from server and i can't onlinee

but after do this ,
i can online without problem..

how to permanent it?

---

### Post by tm222 on 2009-04-19
You need to put it in some startup configuration, not sure how to do it in 8.04 and 8.10, because that changed it Jaunty Beta (I'm using it) ;)

You can look it up, many changing in to Mac theme things use this

---

