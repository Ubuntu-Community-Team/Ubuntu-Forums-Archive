---
title: "Unable to set up network"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by steve106 on 2014-04-26
Hi all. Forgive me if I'm asking a question that's already been answered but, I'm not having much luck getting *the right* answers.

I recently installed Ubuntu 12.04 and cannot get to the internet. I've tried so many different things from so many google searches that I might be better off starting again with a fresh install.

First off, it takes forever to even boot up. The message implies that it's a network connection issue. Probably because I've entered bad data into a critical file.

A couple of commands I've tried.

When I type pppoeconf I'm told that, either the device can't be found, or this is no device. I forget the exact wording.

If I type lspci -nnk | grep -i ethernet I get this:
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)

```

Typing lspci -vv | grep Atheros produces this:
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)

```
This is my card so I'm inclined to believe the info is there, I just don't know how to get to it

Another thing that's just started is whenever I type in a sudo command, I am told, unable to resolve host. But my hostname does show up in the error message.

I am a former Unix user from 1981 to about 1995. Our engineering software was running on Sun Workstations. At the time I was considered a power user, although we didn't have access to the web. I've been away so long, and there are enough differences between that system and Ubuntu that it confuses me. Although a lot of the basic commands are still floating around the old gray matter...

Any help you could offer would be tremendously appreciated.
Thanks
Steve

---

### Post by TheFu on 2014-04-26
While based on UNIX, Linux and Ubuntu are NOT UNIX.  Ubuntu desktop should "just work" without needing to open a shell for 95% of the world.
So ... here are the troubleshooting steps, from a high level.
* Verify that the NIC driver is being loaded - if the device is known, then the driver should be there.
* Check **dmesg** for which device the HW and driver are connected with - probably "eth0" for a NIC. If there are multiple ports, try eth1, eth2.  Wireless is different.
* Check whether the automatic network settings have been loaded vie DHCP - **ifconfig**.

So ... if you have an eth0 or eth1, then it is just a configuration issue ... or bad cable, bad switch, bad router ... 

To help with those, we need to know your normal network settings, 
* ifconfig
* route
and if you can ping the local network ... sometimes DNS issues look like network issues to people not that familiar with networking.
[This link]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking") should help determine which part of your setup is failing AFTER the device name and driver is known to be working.

---

### Post by steeldriver on 2014-04-26
No doubt one of the networking driver experts will be along shortly, but I *think* that 12.04 doesn't have the required driver (alx) for that device

There are various solutions (backports/compat, building from source) depending whether you have internet access at all - or you could just install 13.10 or the latest 14.04 which should include the alx driver out of the box

---

### Post by steve106 on 2014-04-26
TheFu...

The output from dmesg was so much that I don't know what to look for, and I tried to attach it but the file was too large.

Here is the output from ifconfig. I tried to re-format it since it changed when I copied it to my windows folder. Hopefully I got it right...
```
lo  Link encap:Local Loopback
    inet addr:127.0.0.1
    Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
    RX packets:292 errors:0 dropped:0 overruns:0 frame:0
    TX packets:292 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
    RX bytes:20484 (20.4 KB)
    TX bytes:20484 (20.4 KB)

```

Here is the output from route:
```
Kernel IP routing tableDestination Gateway Genmask Flags Metric Ref    Use Iface

```

Hopefully this tells you what you need.

---

### Post by TheFu on 2014-04-27
Look for "eth0" inside the log files using 'grep'. If that doesn't exist, then the driver isn't automatically loaded and you'll need to manually handle that "somehow."  At this point, I'd just load 14.04 and hope for the driver, since 12.04 isn't really the best desktop to run now. Stay LTS, but on the newest.  As of last week, that means 14.04.

Until the correct driver is loaded, there isn't anything else to be done. Drivers are NOT my thing, sorry.

---

