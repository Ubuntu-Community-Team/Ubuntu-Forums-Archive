---
title: "I Have Two IP's?"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2007-10-02
OK - I am running 7.04 on my Dell laptop and it works fine. I am posting from it right now however I have my Intel wireless card enabled as well as I have a Cat5e cable jacked into my NIC. So I want to make sure that I am connected to my wired connection and not a neighbors wireless AP. Ubuntu auto connects to the most available open AP which at home is not mine and while I can disable the internal wireless card in the browser, I prefer not to and would like to know how I can determine which connection is active. Here is what I see...

```
cwilliams@swordfish:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe6a:d1b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19837 (19.3 KiB)  TX bytes:40193 (39.2 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe54:c29a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2665468 (2.5 MiB)  TX bytes:674744 (658.9 KiB)
          Interrupt:19 Base address:0x6000 Memory:dfcff000-dfcfffff 
```

---

### Post by noob12 on 2007-10-02
Yes, probably both.

See what your routing table shows **route -n**.  It will tell you the interface being used for each route in the right hand column.

NetworkManager won't normally put you in this situation but you can end up in this situation if you are starting/configuring the interfaces manually.  If you want it to manage them both, edit your /etc/network/interfaces file and take out all stanzas except the first lo (loopback) one.

---

### Post by CarlosinFL on 2007-10-03
Thanks - I will give that a shot!

---

