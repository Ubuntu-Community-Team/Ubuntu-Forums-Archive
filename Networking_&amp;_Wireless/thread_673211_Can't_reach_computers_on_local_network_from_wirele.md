---
title: "Can't reach computers on local network from wireless laptop"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by pumahalen on 2008-01-20
After a straightforward install of 7.10 on Dell Latitude D600, I was happy to find that the internet connection was fine, But then I can not reach any ip-adress on my internal network, can not get a login screen from the routers, even if they provide this very connection I am using right now! Can not ping, or in any way see my two servers from the wireless laptop. From these servers everything connects fine. I have absolutely no clue where to begin here, - I always used to say networking in Linux is easy, because you have full control. :confused:

The internal network i a 192... thing, with a router at address ...254 as the gateway
Some data:

iwconfig:
eth1      IEEE 802.11b  ESSID:"blabla"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:03:2F:0A:08:F7   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality=65/100  Signal level=-61 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

netstat -r

root@dell:/etc/network# netstat -r
Kernel IP routing table
Destination     Gateway         Genmask     Flags   MSS Window irtt Iface
192.168.0.0     *               255.255.255.0    U         0 0          0 eth0
192.168.0.0     *               255.255.255.0    U         0 0          0 eth1
link-local          *               255.255.0.0       U         0 0          0 eth0
default         192.168.0.254   0.0.0.0          UG        0 0          0 eth1
default         192.168.0.254   0.0.0.0          UG        0 0          0 eth0

Yes, checked /etc/hosts for typos and things,

I would really appreciate your help on this!

J

---

### Post by spd106 on 2008-01-20
It looks like you've got two interfaces running on the same network. This can be bad for routing, so perhaps you could try removing one or dropping one of the default routes.

---

### Post by pumahalen on 2008-01-20
So it did not handle both the wired and the wireless interface at the same time. Sounds reasonable, and ifconfig eth0 down did the trick! Why did I newer think of that! Well, if your stuck, you are so occupied with your stuckness that you don't see anything...


Anyway, tanks for helping me out, here.

---

