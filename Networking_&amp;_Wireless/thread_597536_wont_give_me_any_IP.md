---
title: "wont give me any IP"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Flexo82 on 2007-10-30
I have some problems with my wireless network (big surprize). Well, i have one of the dreaded ralink network cards, the RT73 (2573) to be precise and i use gutsy. I have tried several HOWTO's with no luck so far. i have gotten so far that i can connect to open (non-encrypted) networks, but im using a WPA2 encryption at home and whenever i try to connect to that i just hangs at the "obtaining ip" for about 3 minutes and then fails. I currently have ndiswrapper installed with wicd because network manager crashed everytime i connected to a WPA encrypted network.

```
ifconfig wlan0
```
gives me this result
```

wlan0     Link encap:Ethernet  HWaddr 00:10:60:66:28:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:182 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44465 (43.4 KB)  TX bytes:38993 (38.0 KB)

```

I dont know if it is any help, because i am a bit of a noob in linux. But if anybody has any ideas of what might be wrong please don't hesitate with your reply

---

