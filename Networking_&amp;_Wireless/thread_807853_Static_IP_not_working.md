---
title: "Static IP not working"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by gammyhand on 2008-05-26
I want to put my desktop onto a static IP and the settings that *should* be fine are not working. Can anyone advise where I am going wrong please?

Results of ifconfig -a are:

eth0      Link encap:Ethernet  HWaddr 00:30:1b:b0:f4:1e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb0:f41e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24596200 (23.4 MB)  TX bytes:4681426 (4.4 MB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92900 (90.7 KB)  TX bytes:92900 (90.7 KB)

and the details I am putting into manual network configuration are:

connection type: use static ip
ip address:192.168.1.10
subnet mask: 255.255.255.0
gateway: 192.168.1.1

Thanks.

---

### Post by Iowan on 2008-05-26
What isn't working? (Should the static address be 192.168.1.2 or 192.168.1.10?) If you changed from one to the other, did you restart networking (**/etc/init.d/networking restart**)? Check or post the **/etc/network/interfaces** file. It should contain the manual networking information.

---

### Post by OoooMatron on 2008-05-26
I also had this problem with Hardy and resorted to roaming mode and fixed the ip in the router otherwise I couldn't connect to the internet.

Very annoying!

---

### Post by carious on 2008-05-26
I have this problem as well.  But my router does not allow fixed static IP addressing..  Haven't found a way around it yet.  Pre-Hardy it was functional..  Post-Hardy it is not.

---

### Post by fwre01 on 2008-05-27
> **gammyhand said:**
> I want to put my desktop onto a static IP and the settings that *should* be fine are not working. Can anyone advise where I am going wrong please?

Results of ifconfig -a are:

eth0      Link encap:Ethernet  HWaddr 00:30:1b:b0:f4:1e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb0:f41e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24596200 (23.4 MB)  TX bytes:4681426 (4.4 MB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92900 (90.7 KB)  TX bytes:92900 (90.7 KB)

and the details I am putting into manual network configuration are:

connection type: use static ip
ip address:192.168.1.10
subnet mask: 255.255.255.0
gateway: 192.168.1.1

Thanks.

gammyhand, it may be that the syntax is wrong, this is what it should look like, i didnt include the auto eth0 part in mine and it didnt work for ages.

```

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
```

---

