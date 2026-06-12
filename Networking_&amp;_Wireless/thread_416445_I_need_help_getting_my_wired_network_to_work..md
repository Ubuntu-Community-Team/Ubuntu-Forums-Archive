---
title: "I need help getting my wired network to work."
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by trowis on 2007-04-21
My issue is that I can't get Ubuntu to connect to the internet at all, it's as though it has no drivers for my built in network adapter. I am using a PC Chips A13g (V1.0) motherboard with Boardcom AC131 10/100Mbps Fast Ethernet PHY. Any help would be greatly appreciated. I am searching around to find packets/packages/updates/etc.

---

### Post by josephus on 2007-04-21
can you post
```

ifconfig
lshw -C network
```

---

### Post by trowis on 2007-04-21
```

trowis@Schettl:~$ ifconfig
Link encap:Local Loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet6 addr:  1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX Packets:946 errors:0 dropped:0 overruns:0 frame:0
TX Packets:946 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:52164 (50.9 KiB) TX bytes:52164 (50.9 KiB)

trowis@Schettl:~$ lshw -C network
WARNING: you should run this program as super-user.
trowis@Schettl:~$ 

```

This is all typed from one screen to the next, and I even went and made sure everything was in the correct case...Oi vei... I'll retry this on root.

---

### Post by josephus on 2007-04-21
hmm ... it's currently not even detecting your netword card at all

post your complete hardware details:

```
lshw
```

edit: you can try running with sudo but i'm not sure if that will help

---

### Post by trowis on 2007-04-21
Sorry for the delay, but I had to cross-wire an old HP box to my new one for the floppy drive.

The text file is attached. ~5-6 pages worth.

---

### Post by josephus on 2007-04-21
my first guess right now is that this is a problem with the pci bridge (MCP61)

your post is related to :

[http://ubuntuforums.org/showthread.php?t=379756](http://ubuntuforums.org/showthread.php?t=379756)

installing feisty might be a solution (you are using edgy right now, right?)

also can you post the output of 

dmesg

---

### Post by josephus on 2007-04-21
ok.  this is actually the same as another post that i was reading last week, and you shouldn't need install feisty, you'll just need to compile a module:

[http://ubuntuforums.org/showthread.php?t=411540](http://ubuntuforums.org/showthread.php?t=411540)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

---

