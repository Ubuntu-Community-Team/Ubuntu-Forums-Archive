---
title: "Installation on remote server -&gt; no eth0 interface"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by jocsch on 2006-07-25
Hi all,
I have a dedicated server which is equipped with SUSE 9.x As this is by no means my favourite distro I decided to install dapper drake on it. As I don't have access to a serial console this was a little adventerous. I had to install the server edition of dapper drake in qemu and had to copy the resulting installation/files out of qemu on a free partition of the server. After grub was modified the system started and according to the log files the boot process went smoothly. Apart from the fact that eth0 is not up and running which means that I can't connect to the server. To modify the configs I always have to start a rescue system. This makes life hard as I can only work with scripts instead of direct input. But back to the problem: First I tried to configure eth0 with dhcp (as this is how SUSE was configured), but I had absolutely no luck in getting this to work so I decided to configure it manually with the needed settings. Unfortunately, something doesn't work either. I still can't ping the server. If I let a script which is placed in rc.local (network should be configured then, or?) do an ifconfig I only see the following output:

```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

and route gives a

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Obviously something went wrong but I can't figure out what. Maybe it's the fact that the network card is different from the one simulated by qemu? But it is recognized correctly as /var/log/syslog shows....

Does somebody has an idea? I am out of ideas what could be wrong. BTW, within qemu the network worked fine. Even dhcp was properly running.

Here some additional configuration files.

/etc/network/interfaces (slightly modified IP adresses ;-))
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 86.216.25.196
netmask 255.255.255.255
gateway 86.216.25.1
broadcast 86.216.25.196

#pre-up sleep 10

```

and the syslog which states that the eth0 interfaces was detected:

```

Jul 25 22:27:33 h689448 kernel: [42949382.220000] eth0: VIA Rhine II at 0x1e400, 00:04:61:73:77:e1, IRQ 177.
Jul 25 22:27:33 h689448 kernel: [42949382.220000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.

```


Thanks for reading,
 Markus

---

### Post by jocsch on 2006-07-26
OK. I solved part of the problem. The MAC address from qemu was still stored and blocked all operations on eth0. 
The following post describes the fix

[http://www.ubuntuforums.org/showthread.php?t=221768](http://www.ubuntuforums.org/showthread.php?t=221768)

Nevertheless. Now dhcp is working and I get an IP adress but the route is not set despite the fact that dhc-script tries to set it.
But I will open up a new thread to not mix it in here.

---

