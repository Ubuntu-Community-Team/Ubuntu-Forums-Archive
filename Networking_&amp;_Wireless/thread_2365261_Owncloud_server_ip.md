---
title: "Owncloud server ip"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by Karolina.K on 2017-07-04
Hello, 

I used my old computer to make a owncloud server with, i made it, in the adress field i just wrote localhost/owncloud but now when i want to connect using mobile, i need to put server adress, how can i find this?  also im suspecting there is some problem since its connected to router?

thanks in advance

---

### Post by ajgreeny on 2017-07-04
Command **ifconfig** should show you the IP of the owncloud server.

This assumes you are using Ubuntu, or at least another Linux distro.
The output should be similar to this with the local IP shown in red
```
user@XubuntuXenial:~$ ifconfig
enp4s0    Link encap:Ethernet  HWaddr 08:60:6e:e5:cc:77  
         [COLOR="#FF0000"] inet addr:192.168.1.40[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae0f:877e:f0d5:b35a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171289 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168437376 (168.4 MB)  TX bytes:152761352 (152.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:7054134 (7.0 MB)  TX bytes:7054134 (7.0 MB)
```
If you need the public IP use command ```
curl  ipinfo.io/ip
```

---

