---
title: "problem conecting to my router ..."
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by spinctz on 2008-03-10
i was finally able to install my drivers for lan and wifi on my Fujitsu-Siemens Esprimo v5515... via wifi i can connect to the internet  but via lan through a corega router that is impossible for me ... if anyone can help ... i would apreciate ... i tried dhcp and static ip but nothing ...

---

### Post by TheWizzard on 2008-03-10
please post the output of:
cat /etc/network/interfaces
iwconfig
ifconfig

what is tour router's IP?

---

### Post by spinctz on 2008-03-10
spinctz@spinctz-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



spinctz@spinctz-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"B"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:B8:1A:61   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


spinctz@spinctz-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2990 (2.9 KB)  TX bytes:2990 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:A0:D1:CA:B9:AF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:59561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3594617 (3.4 MB)  TX bytes:54456 (53.1 KB)
          Interrupt:22 Memory:d4407000-d4407080 

wlan1     Link encap:Ethernet  HWaddr 00:C0:A8:FE:81:38  
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fefe:8138/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34926387 (33.3 MB)  TX bytes:1930174 (1.8 MB)
          Interrupt:16 Memory:d4100000-d4110000 

wlan0 is the wired network device and wlan1 is the wifi device ... when i plug the cable it switch from wireless to wire ... gets the ip from the router but the internet is not working ...i accesed the router page from another computer with windows os and the router sees the laptop ...when i ping the router address ... it responds ...but when i ping the other computer i doesn't respond ...10x for answering ...

---

### Post by spinctz on 2008-03-10
in the above post there was a mistake in ifconfig command because i was running on the wireless ... this is the corect one ...

spinctz@spinctz-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2964 (2.8 KB)  TX bytes:2964 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:A0:D1:CA:B9:AF  
          inet addr:192.168.1.168  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:feca:b9af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48144 (47.0 KB)  TX bytes:91442 (89.2 KB)
          Interrupt:22 Memory:d4407000-d4407080

---

### Post by TheWizzard on 2008-03-12
it sounds like a problem with your router or your firewall. did you install firestarter?

---

