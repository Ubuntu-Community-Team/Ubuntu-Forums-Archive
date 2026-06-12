---
title: "Wireless problem .. [wlan0]"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by stfn94 on 2011-01-12
Hello everyone , i have laptop ASUS [dont know what model] with wireless card Atheros Communications Inc. AR9285 Wireless Network Adapter . and i'm running ubuntu 10.10 via VM Player 3.1.3. Ok now , i have problem with wlan0 , i downloaded aircrack , and when i tipe command airodump-ng wlan0 , ubuntu says no such device .. btw i can connect to the internet all works .. Just dont understand, if someone please help me ?




p.s Sorry for bad english .

Thanks ?! 2

---

### Post by amsterdamharu on 2011-01-12
You are running Ubuntu virtually that means the host OS will give the wireless to the guest application (Ubuntu 10.10). I think it will be marked as wired connection.

Try the command ifconfig and see the output.

---

### Post by stfn94 on 2011-01-13
Here's output


```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:5e:65:91  
          inet addr:192.168.86.128  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe5e:6591/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23170 (23.1 KB)  TX bytes:6823 (6.8 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

---

### Post by amsterdamharu on 2011-01-13
Yes, it looks like the host OS won't let you use the wireless directly but gives it to the guest OS as an ethernet card (cable connection).

---

### Post by stfn94 on 2011-01-13
> **amsterdamharu said:**
> Yes, it looks like the host OS won't let you use the wireless directly but gives it to the guest OS as an ethernet card (cable connection).


Any suggestions ?

---

### Post by stfn94 on 2011-01-13
BUMP

I have installed ubuntu (dual boot) but i have new problem . Wireless WORKS fine !



```
stefan@ubuntu:~$  sudo airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.
```

---

