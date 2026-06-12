---
title: "I can't ping from ubuntu host to xp guest!!"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-23
I've ubuntu installed on my machine as a host, xp on the other hand is installed under vbox 3.2 as a guest.
when i'm trying to ping from xp to ubuntu it works fine but doesn't successful when pinging from ubutnu to xp.

$ ifconfig:

[PHP]eth0      Link encap:Ethernet  HWaddr 00:1f:d0:13:a9:9f  
          inet6 addr: fe80::21f:d0ff:fe13:a99f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:122140759 (122.1 MB)  TX bytes:18873699 (18.8 MB)
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109729 (109.7 KB)  TX bytes:109729 (109.7 KB)

[/PHP]
 

ipconfig:

[PHP] Connection-specific DNS Suffix  . :   
        IP Address. . . . . . . . . . . . : 10.0.2.15 
        Subnet Mask . . . . . . . . . . . : 255.255.255.0 
        Default Gateway . . . . . . . . . : 10.0.2.2 
[/PHP]

also firewall is disabled on xp 

any help

---

### Post by bodhi.zazen on 2010-07-24
It appears you are using "NAT" or the default networking. You can not easily ping or connect to servers running on the guest with nat.

Shut window down and try bridged networking.

See : [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by MBG1987 on 2010-07-24
> **bodhi.zazen said:**
> It appears you are using "NAT" or the default networking. You can not easily ping or connect to servers running on the guest with nat.


Thank you, but if i gave xp a static ip will it work?

---

### Post by bodhi.zazen on 2010-07-24
> **MBG1987 said:**
> Thank you, but if i gave xp a static ip will it work?

 ping does not work with the NAT networking option.

If you use bridged networking it does not matter if you use a static ip or dhcp, ping should work.

What are you trying to do ?

You should be able to ping from windows to the internet w/o any problem.

---

### Post by CharlesA on 2010-07-24
If you use the NAT network option, it works just like the guest is behind a router, it can ping addresses on the host's network and connect to them, but you cannot access the guest from the host's network.

It's complicated, but it works.

---

### Post by MBG1987 on 2010-07-25
finally, it works ,i changed the network from NAT to bridge,although i don't know what happen!

---

