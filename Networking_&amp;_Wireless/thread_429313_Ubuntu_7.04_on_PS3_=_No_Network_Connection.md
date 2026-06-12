---
title: "Ubuntu 7.04 on PS3 = No Network Connection"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by Tridion2000 on 2007-05-01
I am running the LiveCD of Ubuntu 7.04 on my PS3 but after it loads up there is no network connection. I don't want to install it until I can at least get on the internet with it. I am using a wired connection which works fine on my PS3 normally.

Any ideas why Ubuntu won't connect to it?

---

### Post by ditsch on 2007-05-01
Despite the NetworkManager Applet claims there is no connection, the network works. It can be configured with /etc/network/interfaces. I use DHCP because it is the easiest way.

If it doesn't work for you, could you show the output of ```
ifconfig
``` and ```
cat /etc/network/interfaces
```

---

### Post by R!nGo on 2007-09-29
hey there,
i know this is an old topic but i got the same problem except that i'm running from an actual system not live CD

i use ehternet cable to connect to Win Xp where the shared connection was working just fine before installing Ubuntu 7.04 on my PS3

i fed up trying to set up connection with no results !

i did what has been asked, and after typing in terminal that's the out put:
```

ps3@ps3-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:C5:9E:A9:03  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::219:c5ff:fe9e:a903/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:101490 (99.1 KiB)  TX bytes:44788 (43.7 KiB) 
          Interrupt:59 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:798 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:798 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:63470 (61.9 KiB)  TX bytes:63470 (61.9 KiB) 


```

```
ps3@ps3-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet static 
address 192.168.0.1 
netmask 255.255.255.0 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 

ps3@ps3-desktop:~$ 
```


can anybody offer me the precious HELP !!!!
cuz i dn't know what the hell  those outputs mean !!!! :lolflag:

waiting for ur replys :)

thank u n advance :)

---

### Post by R!nGo on 2007-09-30
please help me :(

---

### Post by ditsch on 2007-10-01
Am I right you use a Windows XP shared Internet connection to connect your PS3 to the internet? Then you have an IP address conflict at the moment. You could simply use DHCP to receive an IP address. Your /etc/network/interfaces would look like this then:
```
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp
```

---

