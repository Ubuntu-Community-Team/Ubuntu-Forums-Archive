---
title: "My wired network doesn't work anymore"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by ogwilson on 2007-12-08
After installing WICD, my wired network doesn't work anymore. Can anyone help me to get it working again?

---

### Post by ogwilson on 2007-12-09
Bump

---

### Post by gombadi on 2007-12-09
Sure we can help but you are going to have to tell us a bit more about your problem.

When you say your wired network is not working anymore - in what way? What problems are you having?

In a terminal window type these commands and post the results -

```

ifconfig -a
cat /etc/network/interface

```

These commands will show how your system is currently configured and we may even see what WICD has done when it was installed.

Have you asked on the WICD forum to see if they know what may be wrong?

---

### Post by ogwilson on 2007-12-12
Here's what I get from the first line, ifconfig
 
```

[SIZE=3][COLOR=#000000][FONT=Times]eth0      Link encap:Ethernet  HWaddr 00:1C:23:8E:37:90  [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          collisions:0 txqueuelen:1000 [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          Interrupt:17 [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]eth1      Link encap:Ethernet  HWaddr 00:1B:FC:DB:F2:F3  [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          collisions:0 txqueuelen:1000 [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          Interrupt:17 [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]lo        Link encap:Local Loopback  [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          collisions:0 txqueuelen:0 [/FONT][/COLOR][/SIZE]
[FONT=Times][SIZE=3][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times]          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT][/COLOR][/SIZE]


```
 
and here's what i got from the second line
 
```
cat: /etc/network/interface: No such file or directory
```

---

### Post by ogwilson on 2007-12-12
Bump please. And remember, I can't download anything directly to the linux system as it refuses to connect to any network.

---

### Post by gombadi on 2007-12-13
Sorry the file is /etc/network/interfaces - an 's' on the end.

It holds the information about your network interfaces but WICD may have changed it.

It looks like your system has no configured IP address. Note the lines starting "inet addr:" 
My ifconfig has 
```

eth0      Link encap:Ethernet  HWaddr 00:19:D1:70:FA:F4  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe70:faf4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:15955195 (15.2 MB)  TX bytes:3005064 (2.8 MB)
          Base address:0x20c0 Memory:90300000-90320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:705043 (688.5 KB)  TX bytes:705043 (688.5 KB)


```

A quick fix may be to manually set an ip address while you try and figure out what is happening. You can do this by -
```

sudo ifconfig eth0 a.b.c.d
Change a.b.c.d to the ip address for your system such as 192.168.100.100

May also need
sudo route add default gw e.f.g.h
where e.f.g.h is your default router

```

Note - This ip address will only last until you reboot. You will have to enter this each time you boot the machine until you find a permanent fix. Of course the backout method if you have any problems is to reboot your system.

Note 2 - I do not use WICD and am not sure what it has done to your system so you may break things if you poke around and change files/options without knowing what they are for. Be careful and always have backups :-)


When you get online it may pay to ask in the WICD forum to see if they can suggest a solution.

---

### Post by ogwilson on 2007-12-14
All of that didn't work for me, so I went ahead annd reinstalled Ubuntu. I then downloaded my drivers and suddenly the wireless just started "working" I guess it's weird. It'll either just work or just won't. Thanks for all the help.

---

