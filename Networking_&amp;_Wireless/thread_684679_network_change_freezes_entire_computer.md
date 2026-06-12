---
title: "network change freezes entire computer"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by unfair on 2008-02-01
I am using the standard nm-applet that comes packaged with gutsy.

I use static IP addresses at home and work - so I set up two locations under "manual configuration".  When I switch from my home location to my work location it has a tendency to freeze the whole OS.  It hasn't happened *every* time - but more than 50% of the few times I've done it so far.

Also note that it does not freeze instantly - it takes a few seconds after I click the green check mark to apply the settings and close the manual configuration window.  

Does anyone have insight on why this might be happening, or have a workaround?  

Work ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:DC:17:A6  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fedc:17a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2496584 (2.3 MB)  TX bytes:282779 (276.1 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:20:C8:7D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27524 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:288 (288.0 b)  TX bytes:288 (288.0 b)

```

Home ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:DC:17:A6  
          inet addr:192.168.90.67  Bcast:192.168.90.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fedc:17a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2511300 (2.3 MB)  TX bytes:282779 (276.1 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:20:C8:7D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27908 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 b)  TX bytes:376 (376.0 b)

```

---

### Post by unfair on 2008-02-02
Anyone have suggestions or need more information?  I would really like to fix this annoying issue.

---

### Post by unfair on 2008-02-09
Another note - this happens when I change to a wireless network as well.  It freezes the keyboard/mouse/any input device (caps lock does not light up when you press it, etc) - but if you have music playing or an animation on the screen they will continue to run.

It must have something to do with nm-applet, based on some other threads I've seen - but the only useful suggestion I've seen is to switch to wicd instead of nm-applet, and this package isn't in ubuntu synaptic by default - so this is a major problem for novice users.

---

### Post by fbarcenas on 2008-04-15
Yeah, I get the same problem.. I still don't know what it is.
Maybe the right hardware combination will cause it.

I'm using an HP dv5000 series laptop.

And you?

---

