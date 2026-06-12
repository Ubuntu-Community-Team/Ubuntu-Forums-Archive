---
title: "Networking Disabled"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by thaumielx72 on 2010-06-11
I updated my 10.04 M as usual and now every time it starts up I get that message.  I am using my Kubuntu partition as X Ubuntu's will not access the Internet.   In fact all partitions on my machine access the Internet just fine.  So the hardware is working.

Xubuntu was working great until I let it update recently and that was the end of that.  I know this sounds like some n00b complaining about something  simple but I have been using desktop computers since 1981 and I haven't the foggiest idea what to do here.

My machine is a ZT Intel i7 920 (Sears and Roebuck) 12GB RAM, my old hard drive partitioned to 3 Ubuntu partitions.  It may have been me who zapped my networking but if I did I did so by surfing the web as I have loaded no new programs. 

Everything else appears to be working fine it just won't access the Ethernet.  I could just put the installation CD in and start over (I don't have very much data there to lose) but I figured I'd give you guys a shot at this as it looks to be something simple.

Thanks in advance.

---

### Post by Peter09 on 2010-06-11
O.K
lets just have a sanity check.
1. Is it a wireless or a wired connection
2. If wireless what do you see with network manager
3. Is there a harware switch to turn your wireless /on/off what state is it in?
 
Can you post the output of the terminal commands when only your problem network is connected (i.e if its wireless do not have a wired connection connected)
 
```
 
ifconfig

```
 
and
 
```
lshw -C network
```

---

### Post by thaumielx72 on 2010-06-12
> **Peter09 said:**
> O.K
lets just have a sanity check.
1. Is it a wireless or a wired connection
2. If wireless what do you see with network manager
3. Is there a harware switch to turn your wireless /on/off what state is it in?
 
Can you post the output of the terminal commands when only your problem network is connected (i.e if its wireless do not have a wired connection connected)
 
```
 
ifconfig

```
 
and
 
```
lshw -C network
```

Thanks for the response.

It's a wired DSL connection.  (Verizon)

$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask 255.0.0.0
          inet6 addr:  : :1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX Bytes:240  (240.0 B)


$ lshw _C network
WARNING: you should run this program as super-user
  *-networking disabled
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logic name: eth0
       version: 02
       serial: 40:61:86:00:fa:1b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master_cap_list rom ethernet physical
       configuration:  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 muticast=yes
        resources: irq.31 ioport:d800(size=256) memory:fbdff000-fbdfffff memory:f6ff0000-f6ffffff(prefetchable) memory:fbdc0000-fbddffff(prefetchable)

Thanks in advance for any ideas!

---

### Post by SRST Technologies on 2010-06-12
> **thaumielx72 said:**
> In fact all partitions on my machine access the Internet just fine.
...
I have been using desktop computers since 1981
...
12GB RAM
Is that so?

---

### Post by thaumielx72 on 2010-06-12
> **SRST Technologies said:**
> Is that so?

Yep.

---

### Post by Peter09 on 2010-06-14
What do you see when right clicking on the network manager icon?

---

