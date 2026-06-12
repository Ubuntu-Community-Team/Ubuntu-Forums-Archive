---
title: "Network manager won't automatically switch to ethernet"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by temporos on 2013-12-29
If I boot up with the ethernet cable plugged-in, then the Network Manager will recognize both the ethernet and wireless connections, and it will prefer the ethernet. That's good. When I suspend and unplug, the Network Manager automatically switches to the wireless connection. This is good, too. But when I suspend and plug the ethernet cable back in, the Network Manager still uses the wireless connection and won't recognize that the ethernet connection exists. I'm assuming this is a Network Manager problem, but I don't know, really.

How can I configure Lubuntu to automatically detect and prefer the ethernet connection after it's been plugged-in again?

---

### Post by papampi on 2013-12-30
I think usually it wont switch to Ethernet as long as wireless is connected,
but it should switch to Ethernet when you turn off the wireless.

logic is that network stay connected to any device until that device is unavailable then it will look to find an alternative,
but you can write a loop script to check for lan connections and turn off wireless when its available

---

### Post by temporos on 2013-12-30
Thanks for the response, papampi. Let me clarify a bit.

> **papampi said:**
> I think usually it wont switch to Ethernet as long as wireless is connected, but it should switch to Ethernet when you turn off the wireless.
Yes. In the case where I simply plug the ethernet cable back into the machine, I'd expect wireless to remain connected and preferred, since it never disconnected.

The situation I'm asking about is when I suspend the machine while on wireless, physically move to another location and plug the ethernet cable back into the machine while still suspended, and then bring the machine back up. Instead of connecting to the ethernet, Lubuntu will search for and connect to the new wireless network and refuse to detect any ethernet connection. The only time Lubuntu will detect an ethernet connection is when one is available at boot. Even logging out and back in does not force a network reset.

---

### Post by Iowan on 2013-12-30
I wonder if it's hanging onto the old IP address. **man dhclient** reports:
>  ...The client normally  doesn't release  the  current  lease as this is not required by the DHCP protocol but some cable ISPs require their clients to notify the server if they wish to release an assigned IP address. You might try releasing the lease.

---

### Post by temporos on 2013-12-31
> **Iowan said:**
> I wonder if it's hanging onto the old IP address.
That shouldn't be an issue, since when I move to another location, the wireless connects to a completely different network. Different IP address, gateway, and even security protocol. The prior wireless network is disconnected, but it still searches for and connects to another wireless network instead of detecting the ethernet. If I reboot, it will connect to the ethernet just fine, but I'd rather not have to reboot every time.

---

### Post by temporos on 2014-01-05
Here is some new information, since I still can't figure this out. Disconnecting the wireless network caused me to lose connectivity entirely; the ethernet was not detected even though wireless was disabled. I tried to manually restart the ethernet connection, and I got this.

```
$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

Not configured? :confused: That's funny, since I was using ethernet this morning before I unplugged and used wifi down the street. Okay, let's see what's up.

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:f4:08:2a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3925679 errors:4294966852 dropped:4294967148 overruns:4294967222 frame:4294967295
          TX packets:2177973 errors:4294967000 dropped:0 overruns:4294967222 carrier:4294967295
          collisions:4294966926 txqueuelen:1000 
          RX bytes:1149491050 (1.1 GB)  TX bytes:326873443 (326.8 MB)
```

Well. Those tonnes of errors might have something to do with it. :shock: It's still *configured*, though. What's going on?

---

