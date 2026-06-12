---
title: "brand new install and no internet"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Vschiffy on 2010-05-14
Hello everyone, this is my first post ever :)

I'm brand new to Linux, got Ubuntu on my laptop yesterday and I just finished putting Ubuntu on my desktop.

My laptop is able to wirelessly connect to my network just fine, but my wired desktop fails to provide an internet connection...

Any advice would be greatly appreciated!

Here is the output of 'ifconfig' :

eth0      Link encap:Ethernet  HWaddr 00:1b:b9:64:5c:ff  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fe64:5cff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:249 errors:320 dropped:0 overruns:0 frame:320
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42154 (42.1 KB)  TX bytes:33815 (33.8 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by devilized on 2010-05-14
That's an awful lot of errors received - try a new cable

---

### Post by Vschiffy on 2010-05-14
Okay, I replaced the ethernet cable with a brand new one I had in storage, no dice.

Might I add that when I boot my desktop into Windows 7 I am able to access the internet just fine...

---

### Post by Sealbhach on 2010-05-14
Hi,
please show us

```
lshw -C network
```

.

---

### Post by Vschiffy on 2010-05-14
> **Sealbhach said:**
> Hi,
please show us

```
lshw -C network
```.


Here you go!

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1b:b9:64:5c:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.3 ip=192.168.1.105 latency=0 multicast=yes
       resources: irq:19 memory:f9ffcc00-f9ffcc7f ioport:dc00(size=128)

---

### Post by Sealbhach on 2010-05-14
Not good news about this particular ethernet adapter that you have. There's been problems with it for years, though it had been fixed in recent kernels, but the problem seems to have come back.

There's a bug report here about it:

[https://bugs.launchpad.net/ubuntu/+bug/345374](https://bugs.launchpad.net/ubuntu/+bug/345374)

A workaround that some people report to have worked is to change the MTU to 1492.

You can try this by right-clicking on the network icon, select Edit Connections, choose Wired, click on eth0, click on Edit, change MTU from Automatic to 1492 and click Apply.

Give it a try and see what happens.

.

---

### Post by Skrynesaver on 2010-05-14
> **Vschiffy said:**
> 

My laptop is able to wirelessly connect to my network just fine, but my wired desktop fails to provide an internet connection...


How did you set up the network on your wired system. (ie. is external access specific to the computer name of the laptop under Win7)

---

### Post by Vschiffy on 2010-05-14
> **Sealbhach said:**
> Not good news about this particular ethernet adapter that you have. There's been problems with it for years, though it had been fixed in recent kernels, but the problem seems to have come back.

There's a bug report here about it:

[https://bugs.launchpad.net/ubuntu/+bug/345374](https://bugs.launchpad.net/ubuntu/+bug/345374)

A workaround that some people report to have worked is to change the MTU to 1492.

You can try this by right-clicking on the network icon, select Edit Connections, choose Wired, click on eth0, click on Edit, change MTU from Automatic to 1492 and click Apply.

Give it a try and see what happens.

.
YES! Epic win!

That worked perfectly! Thanks a lot!

---

### Post by Sealbhach on 2010-05-14
> **Vschiffy said:**
> YES! Epic win!

That worked perfectly! Thanks a lot!

That's great! For the record, can you do 

```
uname -a
```

in a terminal so we know which kernel you're using?

.

---

### Post by Vschiffy on 2010-05-14
> **Sealbhach said:**
> That's great! For the record, can you do 

```
uname -a
```

in a terminal so we know which kernel you're using?

.
Sorry for the slow reply, was having way too much fun on my desktop :)

Here is what you requested:
Linux vittorio-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

