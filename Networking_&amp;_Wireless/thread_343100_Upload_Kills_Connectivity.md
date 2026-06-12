---
title: "Upload Kills Connectivity"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Darkdelusions on 2007-01-20
I have an issue where uploading anything completely kills my connections I am using a Linksys WRT54G and before that BEFW11SA router. Even uploading a small torrent file to another pc will completely kill the connection. The connection will stay dead until I power cycle the router

Now here is where things get strange. The other pc which is a windows box can upload stuff just fine,

I have flashed the router with the latest firmware from linksys also I dropped another nic and my system. I have even swapped out the network cable. With the windows box able to do everything just fine it (in my head) rules out the router and the connection itself. which only leaves my ubuntu box If anyone could give me any insight that would be great

---

### Post by mssever on 2007-01-21
Hmm...

Can you ping successfully? And you can surf the web just fine?

I also have a WRT54G. It went bad on me, and my Linux laptop was the first to know--other computers/OSes worked fine. Eventually, I got a warranty replacement. So, it's possible that your router is at fault. I can't imagine how your computer could cause the router to act up otherwise.

For the sake of thouroughness--though it probably won't help too much--could you post the output of typing ifconfig?

---

### Post by Darkdelusions on 2007-01-23
I originally thought it was the router so i replaced it.. So this router is not even a month old I got it right after xmas... Now I could have bought a bad one right out of the box that is entirely possible..... I was having the same issue with my old wireless B router as well thou 




```
eth0      Link encap:Ethernet  HWaddr 00:17:31:4C:67:00  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe4c:6700/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:736964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750250 errors:0 dropped:0 overruns:0 carrier:19
          collisions:0 txqueuelen:1000 
          RX bytes:166865301 (159.1 MiB)  TX bytes:66850630 (63.7 MiB)
          Memory:fbec0000-fbf00000
```


Also as far as pinging no... It completely farps all interweb connectivity if i go to console and ping google it hangs for then times out. Also not only does it kill the Net on my machine it kills my windows box as well

---

### Post by Darkdelusions on 2007-01-23
Anyone?

---

### Post by Darkdelusions on 2007-04-19
It appears this was an issue with my router after looking threw the linksys change logs lastnight I noticed the WRT54G had DHCP issues in the previous revisions of the firmware.

---

