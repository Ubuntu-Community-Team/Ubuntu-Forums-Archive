---
title: "Network just not working"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by calnane on 2008-02-22
Hi, sorry if my spelling is bad i'm writing this from an eeepc.

I'm using ubuntu server as a file server for my house with 2 ethernet 10/100 cards. It was working perfectly untill a few days ago. The ethernet cards are working beacause the lights are flashing both ends of the cable. But I cannot connect from any computer in my house and my router cannot see it. Whenever I try to ping from the machine i get the message:

```
connect: Network is unreachable
```

Both cards are showing up when I run "lspci".

Please remember i'm a n00b,

Thanks

---

### Post by nixscripter on 2008-02-22
"Network is unreachable" means that the computer doesn't know where to route the packets in order to get to where they have to go. Please open a terminal, and post the output of two commands: ```
ifconfig -a
``` and ```
route
```.

Also, please put them in [CODE] blocks so that the formatting will be intact and readable.

---

### Post by calnane on 2008-02-23
> **nixscripter said:**
> "Network is unreachable" means that the computer doesn't know where to route the packets in order to get to where they have to go. Please open a terminal, and post the output of two commands: ```
ifconfig -a
``` and ```
route
```.

Also, please put them in ```
 blocks so that the formatting will be intact and readable.


All right.

**ifconfig -a**
[CODE]
eth0    Link encap:Ethernet HWaddr 00:00:1C:D8:6B:C8
          inet addr:86.41.77.124 Bcast:255.255.255.255 Mask 255.255.0.0
          inet6 addr: fe80::200:1cff:fed8:6bc8/64 Scope:link
          UP BROADCAST RUNNING MULTICAST: MTU:1500 Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24192 (13.6 KB) TX bytes:4873 (4.7 KB)
          Interrupt:5 Base address:0xe000

lo       Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b) TX bytes:0 (0.0b)

```

**route**
```

Kernel IP routing table
Destination     Gateway     Genmask       Flags  Metric  Ref     Use Iface
84.41.0.0        *               255.255.0.0    U       0         0           0 eth0

```

---

### Post by calnane on 2008-02-23
**anyone???**:(

---

### Post by nixscripter on 2008-02-23
```

eth0    Link encap:Ethernet HWaddr 00:00:1C:D8:6B:C8
          inet addr:[color=blue]86.41.77.124[/color] Bcast:255.255.255.255 Mask 255.255.0.0
          inet6 addr: fe80::200:1cff:fed8:6bc8/64 Scope:link
          UP BROADCAST RUNNING MULTICAST: MTU:1500 Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24192 (13.6 KB) TX bytes:4873 (4.7 KB)
          Interrupt:5 Base address:0xe000

```

Okay, you have an IP. That's the first good thing.

```

Kernel IP routing table
Destination     Gateway     Genmask       Flags  Metric  Ref     Use Iface
84.41.0.0        *               255.255.0.0    U       0         0           0 eth0

```

What I don't see is a default route. The kernel doesn't know where to send packets to anywhere other than address on the 84.41.0.0 network.

This will establish a default route, i.e. where to send the packets when the kernel doesn't know what else to do with them: ```
sudo route add default eth0
```

If it doesn't print an error, try connecting again.

---

### Post by calnane on 2008-02-24
> **nixscripter said:**
> ```

eth0    Link encap:Ethernet HWaddr 00:00:1C:D8:6B:C8
          inet addr:[color=blue]86.41.77.124[/color] Bcast:255.255.255.255 Mask 255.255.0.0
          inet6 addr: fe80::200:1cff:fed8:6bc8/64 Scope:link
          UP BROADCAST RUNNING MULTICAST: MTU:1500 Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24192 (13.6 KB) TX bytes:4873 (4.7 KB)
          Interrupt:5 Base address:0xe000

```

Okay, you have an IP. That's the first good thing.

```

Kernel IP routing table
Destination     Gateway     Genmask       Flags  Metric  Ref     Use Iface
84.41.0.0        *               255.255.0.0    U       0         0           0 eth0

```

What I don't see is a default route. The kernel doesn't know where to send packets to anywhere other than address on the 84.41.0.0 network.

This will establish a default route, i.e. where to send the packets when the kernel doesn't know what else to do with them: ```
sudo route add default eth0
```

If it doesn't print an error, try connecting again.


Thanks I'll try this later if it doesn't work ill be back

---

### Post by Iowan on 2008-02-24
> **calnane said:**
> I'm using ubuntu server as a file server for my house with 2 ethernet 10/100 cards. **ifconfig** isn't showing the 2nd card - to what does it connect?

---

