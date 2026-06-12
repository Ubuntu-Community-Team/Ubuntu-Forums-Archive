---
title: "Turn off eth1"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by nbakewell on 2008-10-06
Hello,

I can turn off my eth1 card temporarily (until next reboot) by using the command sudo ifconfig eth1 down - but the next time it restarts, eth1 is up again.  I'm looking for a command that will bring eth1 down and have it stay off, even after rebooting, until I specify to bring it online again.  Is there a command to do this?  Or do I have to perform a file edit?

Thanks!

---

### Post by willca on 2008-10-07
Look at the file /etc/network/interfaces

Look for the line auth eth1 and delete that. 
Then reload network
sudo /etc/init.d/networking restart

---

### Post by nbakewell on 2008-10-07
Ok, so if I do that and I don't restart the network, eth1 will stay active until I restart, correct?  Are there no bash commands that will accomplish this?

---

### Post by emarcellus on 2008-10-07
I need to turn off eth0 and my wireless card as well.
etc/network/interfaces  only has 2 lines

auto lo
iface lo inet loopback

I am running 8.04 x86_64

Thanks
Ed

---

### Post by superprash2003 on 2008-10-07
has ubuntu actually recognized eth0 and your wifi card, if so it should be in the interfaces file

---

### Post by emarcellus on 2008-10-07
I knew someone was going to ask that. I should have posted that.
my interfaces file is as I showed above.
Yes, If you do a ifconfig you see all network cards available.

```
ed@4Horsemen:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:4f:89:8f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68275 (66.6 KB)  TX bytes:11498 (11.2 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:1d:60:4f:83:01  
          inet addr:192.168.1.96  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:809058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1197284568 (1.1 GB)  TX bytes:30346192 (28.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7050 (6.8 KB)  TX bytes:7050 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:28:e9:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-28-E9-D3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

To get Firefox to work I issue 
```

sudo ifconfig eth0 down
```

Then I restart Firefox and it works.
I have everything set for DHCP.

Normally when I install (and this is a fresh install btw) I use the ALT disk. I could not find it so I used the 8.04 i86_64 bit Live CD and installed from there.

Thanks for looking....
:)

---

