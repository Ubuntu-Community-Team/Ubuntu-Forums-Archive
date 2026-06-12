---
title: "ndiswrapper driver stoped working after upgrade from 6.06 to 6.10"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by hansi001 on 2007-01-21
Hi! I really need some help here. i'll explain the situation. :D 

I was running Ubuntu 6.06 and evrything was working perfectly, but i wanted to upgrade to the newer 6.10 witch i shouldn't have done.
Well there is only one thing NOT working right now after the upgrade and that's my wireless network. 
I have a Dell wireless 1450 Wireless USB  adapter. I have installed the driver from the cd (witch worked just fine on 6.06) but it's not working on 6.10.

I also noticed that my wireless is not showing up in ifconfig or the network settings in gnome.

```

hansi@hansi-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:D2:74:76  
          inet addr:10.0.0.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fed2:7476/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2067906 (1.9 MiB)  TX bytes:287014 (280.2 KiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


```

usually my wireless would show up here.

I got the ndiswrapper driver installed
```
hansi@hansi-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
dellnic driver present, hardware present 
```
but I don't think it's loaded or something.

Can anyone help me please or at least give me some tips or hints to where i should look? :)

---

### Post by Metaljaz on 2007-01-21
blacklist any driver that was installed during the upgrade so that only the driver you installed is the one loading.

---

