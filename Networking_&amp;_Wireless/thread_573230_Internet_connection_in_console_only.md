---
title: "Internet connection in console only"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by mtaschuk on 2007-10-11
So. I have a wired connection with NetworkManager 0.6.4 on Fiesty 7.04. NetworkManager says that I'm connected to the wired internet, but there is no internet access via Firefox, gaim, or Skype. I also cannot ping any destination external to the local server - however, the text-based browser w3m connects to the internet quite happily. I ran a search on google through w3m. Yet, nothing else has internet! Any help would be appreciated! ](*,)

---

### Post by jfinkels on 2007-10-11
What is the output of this command:```
ifconfig -a
```

---

### Post by mtaschuk on 2007-10-11
The output for ifconfig -a is:

```
ath0      Link encap:Ethernet  HWaddr 00:13:46:D8:05:A9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:874 (874.0 b)  TX bytes:6641 (6.4 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:1D:DD:D0  
          inet addr:192.168.4.138  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe1d:ddd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:512323857 (488.5 MiB)  TX bytes:116932845 (111.5 MiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9159 (8.9 KiB)  TX bytes:9159 (8.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-D8-05-A9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:501551 errors:0 dropped:0 overruns:0 frame:80526
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:86837770 (82.8 MiB)  TX bytes:60063 (58.6 KiB)
          Interrupt:10 
```

---

### Post by jfinkels on 2007-10-11
Hmm...have you checked settings on your router to see if anything is blocked or forwarded in some odd way? Go to [http://192.168.4.1/](http://192.168.4.1/) (probably) to see your router's configuration page.

---

