---
title: "This interface does not exist - part two"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by SilentTim on 2008-05-30
Hi all,

I'm getting the same error as in this thread:
[http://ubuntuforums.org/showthread.php?t=512770](http://ubuntuforums.org/showthread.php?t=512770)

I'm running Hardy by the way.

I can't connect to my wireless network, then when I press 'configure' on my network devices, it gives me the "The interface does not exist..." message.

I've followed all the advice in that thread, but so far to no avail. I've switched off the security on my router to test if I can connect without it, so here a few screen dumps from that effort (NB, I'm connected through a wire at the moment, hence why eth0 shows up as connected):


ndiswrapper is correctly installed:
```

tim@thinktank:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 
tim@thinktank:~$ 

```


I have the correct wireless drivers and hardware:
```

tim@thinktank:~$ ndiswrapper -l
mrv8335x : driver installed
	device (11AB:1FAA) present
tim@thinktank:~$ 

```

Then my current connections:
```

tim@thinktank:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:8a:35:f3:bb  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2984466 (2.8 MB)  TX bytes:492400 (480.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94132 (91.9 KB)  TX bytes:94132 (91.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:a9:54:d0:f9  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:a9ff:fe54:d0f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19990 (19.5 KB)  TX bytes:2018 (1.9 KB)
          Interrupt:11 Memory:c4010000-c4020000 

```

Now, as I said, I've disabled the security on my router. This actually allowed me to connect to the router and gain an IP Address etc, so I'm now thinking its something to do with security settings. I might try reinstalling wpa_supplicant. However, when I press 'configure' on wlan0, it still gives me the 'The interface does not exist...' message.

Can anyone shed any light please?

---

### Post by hal10000 on 2008-05-30
It seems as if your card has got a connection after turning off security, so you might be right that it has something to do with wpa/wep.

But with security turned off, can you ping your router (perhaps [COLOR="Red"]ping 192.168.0.1[/COLOR]) or can you ping an adress in the internet? (e.g. [COLOR="Red"]ping [www.nasa.gov](www.nasa.gov)[/COLOR])
If so, then you can be sure that it has something to do with your security settings.

btw., are you sure you have to use ndiswrapper for your card? If there is a native linux driver instead of ndiswrapper i would prefer this one, because with ndiswrapper you sometimes don't get the full fuctionality for your card

---

