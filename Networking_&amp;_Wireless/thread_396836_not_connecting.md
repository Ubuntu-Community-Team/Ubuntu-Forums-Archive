---
title: "not connecting"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by blitzwing on 2007-03-29
as much as i hate to do this, ive got to add another "my wireless isnt working thread" sorry.

i finally got my card up and running, and yes its the dreaded bcm4318.... using wicd i get a list of available networks and can get a connection to unsecured networks (ill work on the security thing later) but firefox wont load any web pages. ive searched through what seems like all the related threads and i still cant get it. any ideas?????

---

### Post by chili555 on 2007-03-29
Please *sudo gedit /etc/modprobe.d/blacklist* to add:```
blacklist ipv6
```Save and close gedit. Reboot and tell us if it's better.

If you got bcm4318 working and connected to a network, you are doing extremely well. Good work!

---

### Post by blitzwing on 2007-03-29
it was no easy task gettin this card up and runnin, lots of reading and rebooting.
i tried the blacklist ipv6, no luck

wicd says connected. but the network connection shows eth1 disconnected and 100%
signal. any other ideas???

---

### Post by compwiz18 on 2007-03-30
> **blitzwing said:**
> it was no easy task gettin this card up and runnin, lots of reading and rebooting.
i tried the blacklist ipv6, no luck

wicd says connected. but the network connection shows eth1 disconnected and 100%
signal. any other ideas???

can we see the output of **iwconfig** and **sudo route** and **ifconfig** please?

---

### Post by blitzwing on 2007-03-30
sorry for the delay, had to go to work....
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo route

rob@rob-laptop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:10:A4:A7:0B:36  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2713112 (2.5 MiB)  TX bytes:395614 (386.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:C0:49:FD:05:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:36000000-36002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:780 (780.0 b)  TX bytes:780 (780.0 b)

rob@rob-laptop:~$ 

any help with this would be greatly appreciated

---

### Post by blitzwing on 2007-03-31
bump

---

### Post by blitzwing on 2007-03-31
anybody?????????

---

### Post by chili555 on 2007-03-31
Looks like your wired ethernet is connected and has an IP address. Any improvement if you detach the cable, do *sudo ifdown eth0* and retry the wireless?

---

### Post by blitzwing on 2007-03-31
the wired works fine, i tried without and had no luck. reset wicd to connect to my router i got a connection but cant load any pages....


sudo ifdown

rob@rob-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured

---

### Post by blitzwing on 2007-04-01
i can ping my router, but cant ping any other sites, i tried the ivp6 blacklist and in about:config and still no luck, a dns issue maybe?

---

### Post by blitzwing on 2007-04-01
ready for this one...
i tried to ping [www.google.com](www.google.com), with no luck, so i tried it without thw WWW and it worked, then i tired 2 other generic sites with succes. so it try firefox again and it connects, works and works fine.  then i loose connectiona nd cant reconnect, im running wicd so i tried another local router, not my own and it connects fine. i cant connect to my own router...
ive disabled security on my router. i can ping it and get a great connection but cant load any pages...
any ideas

---

### Post by blitzwing on 2007-04-01
ok my bad, i had to change some settings in wicd for my routers network connection.
btw,                         



                       IT WORKS FINALLY=D>

---

