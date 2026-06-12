---
title: "Wireless Network Doesn't Work in Virtual PC with Ubuntu as the machine OS."
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by CompizAddict on 2008-02-19
The os of the virtual machine is UBuntu and the computer os is Vista. When i go on Ubuntu. I don't have connection on the ubuntu os. I have connection outside the virtual machine but not on the ubuntu os. Please Help.:confused:

---

### Post by nixscripter on 2008-02-21
The first thing I think of is: it's probably Windows' fault. Something isn't configured right on the other end. But that's just a little cynicism.

However, looking at the Ubuntu end, please go into a terminal, and post the output of the command:

```
ifconfig
```

---

### Post by CompizAddict on 2008-02-22
K... I upgraded my whole computer to Ubuntu. The internet doesn't work yet...
When i do ifconfig i get:
eth0      Link encap:Ethernet  HWaddr 00:1D:60:F1:FF:3E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4123847 (3.9 MB)  TX bytes:372776 (364.0 KB)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

What should i do?

---

### Post by nixscripter on 2008-02-22
```

eth0    Link encap:Ethernet  HWaddr 00:1D:60:F1:FF:3E  
          [color=blue]inet addr:192.168.1.2[/color]  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4123847 (3.9 MB)  TX bytes:372776 (364.0 KB)
          Interrupt:16 Base address:0xec00

```

Alright, that tells me that the Ubuntu machine is in fact getting an IP from the Windows machine. Let's make sure it's attempting to route the packets out the right place. Please post the output of the command ```
route
```

And also, please use [ CODE ] blocks around it to preserve formatting better.

---

### Post by CompizAddict on 2008-02-23
What about a computer with Ubuntu as the os

---

### Post by nixscripter on 2008-02-23
Sorry, I meant run "route" on the Ubuntu machine.

---

### Post by CompizAddict on 2008-02-25
Kernel IP routing table
Destination    Gateway     Genmask    Flags Metric Ref   Use Iface
What now?

---

### Post by nixscripter on 2008-02-25
That's it? There's nothing there? Do you still have an IP when you do it?

If you do, then that's the problem. Somehow, your routing table got blanked.

Figure out the IP address that your windows machine shows to your Ubuntu box, and try this:

```
sudo route add default gw **win-ip-address** eth0
ping -c 1 **win-ip-address**

```

See if the ping comes back.

---

