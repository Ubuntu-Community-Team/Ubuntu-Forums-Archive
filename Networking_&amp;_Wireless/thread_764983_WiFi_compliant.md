---
title: "WiFi compliant"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by billbog on 2008-04-24
Hello -Rather a basic question : I have an Acer Aspire 3003 LM. which might or might not be wifi compliant (it depends on specification). How do I find out if I have it? Firefox not working.

---

### Post by superprash2003 on 2008-04-24
go to terminal and type ifconfig and post results here

---

### Post by billbog on 2008-04-24
Heres what came back :
Link encap:Ethernet  HWaddr 00:0B:6A:B6:5D:0D  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:feb6:5d0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:434035 (423.8 KB)  TX bytes:63642 (62.1 KB)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX byt

---

### Post by superprash2003 on 2008-04-24
have you connected a LAN cable to your acer?

---

### Post by MikeonTV on 2008-04-24
I'm having the exact same problem with an acer aspire 3680

my ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:4e:76:40  
          inet addr:192.168.10.6  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe4e:7640/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16534043 (15.7 MB)  TX bytes:846450 (826.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82300 (80.3 KB)  TX bytes:82300 (80.3 KB)

---

### Post by superprash2003 on 2008-04-25
so are you connecting your acer via a wired connection right now?

---

### Post by chili555 on 2008-04-25
In the case of both posters, it appears yes. This causes NetworkManager to not allow activation of the wireless. Why would it? You are connected to the world and you have a valid, working IP address. However, check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)  especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themSo, in order to see your wireless, you will need to disconnect the wire and then do:```
sudo ifdown eth0
iwconfig
```Let us know.

---

