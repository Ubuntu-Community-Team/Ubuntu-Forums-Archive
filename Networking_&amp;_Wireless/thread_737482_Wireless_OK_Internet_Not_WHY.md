---
title: "Wireless OK? Internet Not WHY"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by smallzoo on 2008-03-27
I've read some of the other posts but for my sins I have worked with windows for years so its a bit difficult getting my head around the Xubuntu networking..

I think the wireless card is working but I cannot get an internet connection. If I ping my router from my XP PC  its fine but from the Xbuntu PC I get 

From 169.254.7.5  icmp_seq=1  destination host unreachable.

here are some of the checks I have done..

------------------------------------------------------------------------------------------------------------------------

peter@ubuntu1:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:6c:df:35
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
peter@ubuntu1:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:183296 (179.0 KB)  TX bytes:183296 (179.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:6C:DF:35  
          inet6 addr: fe80::211:95ff:fe6c:df35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:24107 (23.5 KB)
          Interrupt:11 

wlan0:ava Link encap:Ethernet  HWaddr 00:11:95:6C:DF:35  
          inet addr:169.254.7.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 


----------------------------------------------------------------------

Whats up Doc !!

Thanks

peter

---

### Post by creem54 on 2008-03-27
try a 'netstat -rn' and post the results

---

### Post by smallzoo on 2008-03-28
Ok I'll try that and post it..

---

### Post by superprash2003 on 2008-03-28
try this [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html)
 i have a feeling its the ROAMING MODE part.. cause your wlan0 is not getting any ip

---

### Post by smallzoo on 2008-03-28
Roaming is disabled and the router is DHCP enabled../


The command netstat -rn gives


Destination     Gateway    genmask         Flags   MSS Window  irtt  iface
169.254.0.0   0.0.0.0      255.255.0.0      U          0       0         0    wlan0
0.0.0.0           0.0.0.0      0.0.0.0              U          0       0         0    wlan0

Thanks

---

### Post by acirilo on 2008-03-28
to me it was easier to just to put static ip on mine. forget DHCP....

---

### Post by superprash2003 on 2008-03-28
try manually entering the ip.. cause you are getting a 169.x.x.x ip for wlan0 .. which means your router is not giving your computer an ip

---

### Post by Eiríkr on 2008-03-28
Your wireless has an IP address assigned, but the 169.254.xxx.xxx range is reserved for zeroconf -- on Mac, that means Bonjour, and on Linux, that means Avahi.  This strongly suggests that your wireless is not communicating with your router, and the Avahi daemon takes over when DHCP fails.  

Try resetting your network:
```
sudo /etc/init.d/networking restart
```

Post the results of the above command.  Then please post the results of each of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

It'd also make for easier legibility if you could enclose your results in [noparse]```

```[/noparse] tags.  ;)

Cheers,

Eiríkr

---

### Post by smallzoo on 2008-03-28
results of your commands ( I have changed the wireless key etc for obvious reasons..)

```

 * Reconfiguring network interfaces...                        There is already a pid file /var/run/dhclient.wlan0.pid with pid 4567
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:6c:df:35
Sending on   LPF/wlan0/00:11:95:6c:df:35
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:6c:df:35
Sending on   LPF/wlan0/00:11:95:6c:df:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

peter@ubuntu1:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:11:95:6C:DF:35  
          inet6 addr: fe80::211:95ff:fe6c:df35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:27220 (26.5 KB)
          Interrupt:11 

wlan0:ava Link encap:Ethernet  HWaddr 00:11:95:6C:DF:35  
          inet addr:169.254.7.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

```

```

peter@ubuntu1:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"O2wireless039F61"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:D0:F2:D5:4B   
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=46/100  Signal level=24/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

peter@ubuntu1:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface


iface wlan0 inet dhcp
wireless-key s:xxxxxxxxxx
wireless-essid yyyyyyyyyyyy





auto wlan0

```

---

### Post by Eiríkr on 2008-03-28
There might be a bad pid file for your wlan0 interface.  Try the following:
```
sudo ifdown wlan0
sudo ifup --force wlan0
```
... and post the results.

Cheers,

Eiríkr

---

### Post by smallzoo on 2008-03-29
Sorry about the late reply..

here are the results of the commands you said

```

peter@ubuntu1:~$ sudo ifdown wlan0
[sudo] password for peter:
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5293
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:6c:df:35
Sending on   LPF/wlan0/00:11:95:6c:df:35
Sending on   Socket/fallback

```

```

peter@ubuntu1:~$ sudo ifup --force wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:6c:df:35
Sending on   LPF/wlan0/00:11:95:6c:df:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases i



```

---

### Post by Eiríkr on 2008-03-29
This is now past where I can help directly.  I suspect this line is a clue, but I'm not sure how to interpret it:
```
Sending on   Socket/fallback
```

Anyone else able to help?

Cheers,

Eiríkr

---

### Post by smallzoo on 2008-03-31
Thanks for your help.. I guess I will have to post again as I am getting no other responses..

Thanks again

Peter

---

### Post by smallzoo on 2008-04-02
Thanks for the replies.. but guess what I solved it more by good luck than good management. I read on one website that when you set up a wireless card and decide to put in the wep key as text you MUST put quotes around the key// guess what I hadnt !.. so I changed it to hexadecimal and put the same SSID key in and it worked !!!

Well worth noting !

Thanks again

---

### Post by VJ42 on 2008-04-02
> **smallzoo said:**
> Thanks for the replies.. but guess what I solved it more by good luck than good management. I read on one website that when you set up a wireless card and decide to put in the wep key as text you MUST put quotes around the key// guess what I hadnt !.. so I changed it to hexadecimal and put the same SSID key in and it worked !!!

Well worth noting !

Thanks againI'm having similar problems to you, which website was this?

---

