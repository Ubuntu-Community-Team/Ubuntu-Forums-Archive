---
title: "Wired Connections don't start on boot"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by yataf on 2008-08-15
I can't seem to figure this one out, but every time I boot up my ubuntu I have to manually start up my wired connection. Anybody know how to fix this?

Thanks.

---

### Post by Crafty Kisses on 2008-08-15
Post these following outputs
```
ifconfig
```
Then the next one
```
lshw -C network
```

---

### Post by Iowan on 2008-08-15
Hope [this one]("http://ubuntuforums.org/showthread.php?t=890531") helps.

---

### Post by yataf on 2008-08-18
Ok, my bad guys for being a little late I was a little busy.

From those 2 commands I got:
```
a@a-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:C6:EB:3D:39  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c6ff:feeb:3d39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:539999 (527.3 KB)  TX bytes:85322 (83.3 KB)
          Interrupt:9 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

a@a-desktop:~$ sudo lshw -C network
[sudo] password for a:
  *-network               
       description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 25
       serial: 00:80:c6:eb:3d:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.147 latency=64 maxlatency=56 mingnt=8 module=tulip multicast=yes

```

Then what I tried was to go edit that interfaces thing and added in auto eth0 but it doesn't seem to be doing it for me.

-Thanks

---

