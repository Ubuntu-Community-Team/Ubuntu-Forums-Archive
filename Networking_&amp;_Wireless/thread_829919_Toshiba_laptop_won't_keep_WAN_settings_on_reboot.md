---
title: "Toshiba laptop won't keep WAN settings on reboot"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by EmperorMoo on 2008-06-15
I'm running Hardy upgraded from Gutsy on an old Toshiba Satellite laptop, and it's running on a WEP WAN network [DHCP].

My problem is that on reboot, all WAN settings are lost, and they have to be recovered by entering the following:

```

   54  sudo ifconfig eth0 down
   55  sudo ifconfig eth1 down
   56  sudo dhclient -r eth1
   57  sudo ifconfig eth1 up
   58  sudo iwconfig eth1 essid "ESSID"
   59  sudo iwconfig eth1 key HEX_KEY
   60  sudo iwconfig eth1 mode Managed
   61  sudo dhclient eth1

```

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"ESSID"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:5B:00:C6:6F   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:

```

eth1      Link encap:Ethernet  HWaddr 00:04:23:60:4a:6e  
          inet addr:192.168.0.144  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe60:4a6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:996 errors:32 dropped:32 overruns:0 frame:0
          TX packets:1492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:777145 (758.9 KB)  TX bytes:182950 (178.6 KB)
          Interrupt:11 Memory:fcefe000-fcefefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95564 (93.3 KB)  TX bytes:95564 (93.3 KB)

```

I have noticed that the (unused) ethernet port - this machine used to be on a wired LAN - is coming up as eth1.

Any ideas appreciated.  I don't really want to have to do a clean install of Hardy if possible as I can't get the laptop to boot from a CD.

---

### Post by Ho.Simps on 2008-06-22
I had the same problem.

Instead many command (ifconfig ..) you can use ```
/etc/init.d/networking restart
```

My solution:
1) add networking script to starting scripts
```
sudo ln -s /etc/init.d/networking /etc/rc3.d/S88networking
```
2) replace **start** parameter to **restart** in /etc/init.d/networking script
 - replace ```
start)
``` to ```
start1)
```
 - replace ```
force-reload|restart)
``` to ```
force-reload|restart|start)
```

and after reboot WAN must work

---

