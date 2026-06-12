---
title: "No Eth0 Connection in 13.10 new install"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by cchat on 2014-01-30
Yesterday I had satellite internet installed and connected to my local wired network.  Also installed a NetGear wireless router between the internet modem and the network.  Both my Windows computers connect as well as my TV.  My two tablets and my phone connect to the wireless.  Since I had been unable to access the network previously I reinstalled Ubuntu 13.10 by deleting the old install and starting fresh.  In the install it would not recognize the Eth0 connection to the network, but would connect with the wireless.  The install went fine with the internet connection through the wireless but still can get no connection through the eth0 connection.  

ifconfig -a gives me the following:
```
chuck@Ubuntu:/etc$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:21:d2:d1:51  
          inet6 addr: fe80::219:21ff:fed2:d151/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:284496 (284.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:183274 (183.2 KB)  TX bytes:183274 (183.2 KB)

wlan0     Link encap:Ethernet  HWaddr 94:44:52:70:68:6c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9644:52ff:fe70:686c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23931 errors:0 dropped:1482 overruns:0 frame:0
          TX packets:13781 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25021721 (25.0 MB)  TX bytes:1750566 (1.7 MB)
```

Clicking on the network-manager icon is less than helpful.  I can communicate with the internet through the wireless, but no connection to my local wired network which includes my primary printer.  
Any suggestions gratefully received.  I am brand new to Ubuntu but experienced in networking.

---

### Post by ian-weisser on 2014-01-30
Look in the kernel boot log (located at /var/log/dmesg) for messages specifically related to eth detection, driver assignment, and interface assignment. Try the following command, and post the results here:
```
grep eth /var/log/dmesg
```

Probe the hardware for ethernet hardware information. Try the following command, and post the ethernet-hardware related info here.
```
sudo lshw
```

---

### Post by Iowan on 2014-01-30
Disable the wireless and try it.

---

### Post by cchat on 2014-01-30
Thanks for the replies.  I have the Ubuntu computer in an upstairs room where the satelite internet modem is located.  The router is downstairs where the other computers are located.  I decided to switch the cable and used the internet modem's cable to reach my local network, and suprisingly it worked.  I then connected the modem back up using the cable I had just taken off the Ubuntu computer and SUPRISE it worked as well!  Apparently the internet modem is happy with either cable but the Ubuntu box is picky and will only work with the one.  I will keep a check on it in case I eventually have to replace the cable that is now on the internet modem to router link.

At any rate I am up and running and can begin loading Samba and other fun things.

Thanks guys.

---

