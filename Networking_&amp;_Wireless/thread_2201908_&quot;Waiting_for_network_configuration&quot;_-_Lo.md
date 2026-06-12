---
title: "&quot;Waiting for network configuration&quot; - Long Boot Times"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2014-01-26
This is an issue that has been plaguing me for a long time now.  I just finished a fresh install on my server, and this is still a problem.  I'm not sure if I've got something messed up in a configuration somewhere, or if there's a bug/problem here.

_*A little background:*_

This machine acts as my home router/firewall and overall server.  This is achieved through a 4-port PCI ethernet card and the motherboard's onboard ethernet.  Software-wise, the system runs DHCP, Bind9, and Shorewall to tie it all together.  In addition to being my router/firewall, this box also hosts a number of LXC Containers, each with their own specific duties.  For example, one of them runs as a web server, one of them as a database server, and so on.  These containers are assigned a static IP address, and connect to the rest of the network using a bridge.

There are two bridges, br0 and br1, which are defined as follows in /etc/network/interfaces:

```
#bridge for LXC (dmz)
iface br0 inet static
        address 192.168.80.1
        netmask 255.255.255.0
        broadcast 192.168.80.255
        network 192.168.80.0
        bridge_maxwait 15
        pre-up brctl addbr br0
        post-down ip link set br0 down
        post-down brctl delbr br0

#bridge for LXC (internal)
iface br1 inet static
        address 192.168.90.1
        netmask 255.255.255.0
        broadcast 192.168.80.255
        network 192.168.80.0
        bridge_maxwait 15
        pre-up brctl addbr br1
        post-down ip link set br1 down
        post-down brctl delbr br1

```

_*The problem:*_

When I boot the system, it hangs at "Waiting for network configuration."  It will sit and wait for some time, and eventually says that it will wait an additional 60 seconds before continuing to boot.  When the system does finally finish booting, ifconfig reveals the following:

```
br0       Link encap:Ethernet  HWaddr fe:f8:21:bb:77:98  
          inet addr:192.168.80.1  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::fcf8:21ff:febb:7798/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:648 (648.0 B)

br1       Link encap:Ethernet  HWaddr 3a:24:fa:16:aa:73  
          inet addr:192.168.90.1  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::3824:faff:fe16:aa73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:648 (648.0 B)

```

So, to me, it looks like the bridges are both up and running when booting is complete.  What is the system waiting for at boot time?  If I can't fix whatever is causing this (google has resulted in a few hits, but nothing has helped), is there a way to force the system to *not* wait?

---

### Post by ajgreeny on 2014-01-26
Interesting!

I have been having a similar sounding problem when trying to boot the Trusty daily live system (14.04, so problems expected) about which I started a thread at [http://ubuntuforums.org/showthread.php?t=2200517](http://ubuntuforums.org/showthread.php?t=2200517).  I have detailed my hardware there and it would be interesting to know if your eth0 card is the same as mine, a Realtek RTL-8139 which has always worked fine before.  The problem must be hardware related as the same ISO live image boots fine on two other computers I have, and finds the network with no problem at all on those, one wired the other wireless.

---

### Post by svtguy88 on 2014-01-26
My 4-port ethernet card has two Intel 82546EB chips, and the onboard ethernet is an Intel 82541GI...

---

### Post by svtguy88 on 2014-01-29
Bump...

Anyone?  I'd really like to cut my boot time down by skipping the 'waiting for network configuration' stage.  Between the server taking its dear sweet time to get through POST (~3 minutes) and this boot delay (~3 minutes), it's a painful experience to wait for it to reboot.

---

