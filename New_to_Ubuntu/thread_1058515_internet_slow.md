---
title: "internet slow"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by swampdude on 2009-02-02
i just installed ubuntu 8.10 and it works great but it takes forever to download updates. I have like a 10mb connection. nothing is on the internet right now. Can anyone help?

---

### Post by Crafty Kisses on 2009-02-02
Are you going through a wireless connection, or are you wired?

---

### Post by swampdude on 2009-02-02
wired

---

### Post by Crafty Kisses on 2009-02-02
What are the results of this command?
```
ifconfig
```

---

### Post by tuxxy on 2009-02-02
Hvae you tried a different server

---

### Post by swampdude on 2009-02-02
Well here is the info:
eth0      Link encap:Ethernet  HWaddr 00:13:d3:cd:b5:75  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fecd:b575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166113512 (166.1 MB)  TX bytes:7976855 (7.9 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7172 (7.1 KB)  TX bytes:7172 (7.1 KB)

And secondly, i can change the server i download from?

---

### Post by tuxxy on 2009-02-02
> **swampdude said:**
> 

And secondly, i can change the server i download from?

Yes in your software sources

---

### Post by lisati on 2009-02-02
Possibility: When I updated to 8.10 I noticed that my internet seemed slower, as did some other stuff. The number-one suspect on my *ubuntu laptop is RAM (it has only 222Mb available RAM), but I haven't had a chance to test this theory yet.

---

### Post by swampdude on 2009-02-02
tuxxy could you help me change the server and what to?

---

### Post by spcwingo on 2009-02-02
> **swampdude said:**
> tuxxy could you help me change the server and what to?

I'll give you hand with this.  Just open system>administration>synaptic package manager.  When synaptic opens choose settings>repositories>press the drop-down beside "Download from" and choose "other".  From the new window choose "Select best server".  I hope this helps.

---

