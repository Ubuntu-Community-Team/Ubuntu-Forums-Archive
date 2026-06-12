---
title: "Cannot connect to wireless or ethernet anymore"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by AnotherN00b on 2011-06-11
Hey guys,

So I'm still new to Linux and recently installed Ubuntu 11.04 on my notebook.  At first was seeing wireless networks fine and could connect to all of the unless they have WPA2 encryption on them.  Recently the wireless hasn't been working.  But I could connect via ethernet LAN (sometimes having to use the sudo dhclient eth0 command).

But just yesterday that quit working too!  I have been searching all morning and can't find the solution.  I don't know what to do next please help.  Here's my ifconfig:

caleb@pax:/etc/init.d$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:a5:f9:ce 
          inet6 addr: fe80::21b:24ff:fea5:f9ce/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:393735 (393.7 KB)  TX bytes:60587 (60.5 KB)
          Interrupt:18

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2296 (2.2 KB)  TX bytes:2296 (2.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:11:3e:48 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:80400000-80410000

---

### Post by Swagman on 2011-06-11
Before we go any further.... Who's your ISP ?

(I wish people would add their location to their profile so we don't have to ask this question)

If your ISP is BT and you are using their homehub then join the queue

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

Fix/es are from page 9

---

### Post by AnotherN00b on 2011-06-11
Yeah sorry about that.  My ISP is actually CenturyLink I live in Tallahassee FL.

But I'm having the same issues regardless of where I am.  At work, home, or a friends house.  I'm pretty sure my that one of those ISP's is Comcast.

---

### Post by MasterGamerJK on 2011-06-11
The IPS has NOTHING to do with it. I guarantee it.

---

