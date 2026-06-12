---
title: "Network History shows SENT package spike every 2 seconds!!??"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by paulvbrown on 2007-09-04
Alright, I'm stumped.  (Not that that's saying much - pretty much a Linux noob, still, sadly.)

I've got Ubuntu (Dapper) installed (with latest updates) on my daughter's IBM Thinkpad T21, and was just poking around, and in the System Monitor, the Network History shows a spike of sent data (about 250bytes each time) like every other second!  Any idea what that could be about?  

Feisty, installed on my more modern HP dv6205us, displayed SOMEWHAT similar behavior, but the sent packages were only occuring like every 20 secs, and now when I went verify that, I see that the spikes are not there any more on my PC.  I've got several apps open, whereas right now on her laptop the only "application" that's open is the System Monitor.  I don't SEE anything immediately that just screams at me, "Hey, I'm probably gonna send info across the internet to somewhere!"

My plan is to try and switch her to a more fresh version of Ubuntu, or possibly change to another distro anyway, but I'm one of those people that like to find the REASONS behind things....

Oh, right now her laptop's plugged directly into the LAN, and doesn't have a wireless card or anything, so don't think it should be anything related to wireless, though it does reek of some sort of "keep alive" messaging or something...

any help?

Thanks in advance!

---

### Post by noob12 on 2007-09-04
For clues you might look at /var/log/syslog and /var/log/kern.log.
 
You can also use tcpdump to see any traffic going out of the box.  For eth0 this would tell you where the traffic is going at least and may provide a clue. This dumps some of the contents of the packets as well.  You can get more with additional options to tcpdump
```

sudo tcpdump -i eth0 -X host *replace.this.with.the.hosts.own.ip.address*

```

---

### Post by eluzi on 2007-09-04
Yeah, try to use tcpdump to check what's it about...it could be only the maintenance of your ip through dhcp ack's...

---

### Post by paulvbrown on 2007-09-04
Ok, now that's just weird.

Both logs show something along the lines of : 
```
device eth0 entered promiscuous mode
device eth0 left promiscuous mode
```

Hmmm - and then after the last one of those I see:
```
localhost /USR/SBIN/CRON[15700]: (root) CMD (   run-parts --report /etc/cron.hourly)
```

after which, or at about the same time -- spikes stopped finally.

But that's not the weird part -- the weird part was that tcpdump didn't show any activity at all.  I must have got the command wrong somehow...?

ifconfig shows: 
```

eth0      Link encap:Ethernet  HWaddr 00:03:47:BB:99:FB
          inet addr:192.168.255.4  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:febb:99fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17765994 (16.9 MiB)  TX bytes:895953 (874.9 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:1 dropped:1 overruns:0 frame:0
          TX packets:58849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:1933610 (1.8 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)
```

so my tcpdump command looked like this:
```
sudo tcpdump -i eth0 -X host 192.168.255.4
```

And it seemed to do nothing, meanwhile I was looking at the NetworkMonitor and there were the spikes, just about as regular as clockwork...

---

### Post by guardsman85 on 2007-09-04
> **paulvbrown said:**
> I must have got the command wrong somehow...?
p command looked like this:
...
```
sudo tcpdump -i eth0 -X host 192.168.255.4
```And it seemed to do nothing, meanwhile I was looking at the NetworkMonitor and there were the spikes, just about as regular as clockwork...

Your command looks alright.

Can you tell if the spikes you're getting are send or receive spikes?

---

### Post by noob12 on 2007-09-04
> **paulvbrown said:**
> Ok, now that's just weird.

Both logs show something along the lines of : 
```
device eth0 entered promiscuous mode
device eth0 left promiscuous mode
```


This happens when you run tcpdump.  It puts the device in promiscuous mode which allows it to listen to traffic that's not just to/from your host.

> 
Hmmm - and then after the last one of those I see:
```
localhost /USR/SBIN/CRON[15700]: (root) CMD (   run-parts --report /etc/cron.hourly)
```
after which, or at about the same time -- spikes stopped finally.


That's your hourly cron jobs; probably not related.


> 
But that's not the weird part -- the weird part was that tcpdump didn't show any activity at all.  I must have got the command wrong somehow...?

ifconfig shows: 
```

eth0      Link encap:Ethernet  HWaddr 00:03:47:BB:99:FB
          inet addr:192.168.255.4  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:febb:99fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17765994 (16.9 MiB)  TX bytes:895953 (874.9 KiB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:1 dropped:1 overruns:0 frame:0
          TX packets:58849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:1933610 (1.8 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)
```

so my tcpdump command looked like this:
```
sudo tcpdump -i eth0 -X host 192.168.255.4
```

And it seemed to do nothing, meanwhile I was looking at the NetworkMonitor and there were the spikes, just about as regular as clockwork...


That's the right command.

I actually do not know what NetworkMonitor is.  Do you know if it includes monitoring the loopback interface?

---

### Post by paulvbrown on 2007-09-04
Don't know if it includes loopback interface monitoring, but tried to tcpdump that as well, and got the same (none) results.  It is definitely SENT activity I'm seeing.  Just weird -- at this point, though, I'm just planning on upgrading to Feisty and/or trying another distro, and letting it go.  It's just like one of those annoying Windows problems I'd always run into, though -- where all of a sudden my hard drive starts driving me crazy with all the work it's doing, and NOTHING should be going on at the time (to my knowledge).  So hate to see that kind of thing happening to my Linux machines...

---

### Post by guardsman85 on 2007-09-05
I notice that your ifconfig shows irda0.  It could be that it is sending out beacons.  If your network monitor considers this a network interface the spikes you're seeing could be beacons from the infrared port (irda0).  I don't think the beacons would show up in a tcp dump, because I don't think the interface uses the TCP stack.  You could try disabling the irda0 interface (if you don't need it) and seeing if the problem goes away.
```
sudo ifconfig irda0 down
```

---

