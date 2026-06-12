---
title: "wireless connection 0%"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by ikedaman on 2008-07-23
I recently upgraded to Hardy Heron.  I need to connect to my network wirelessly, which I have never done in ubuntu before.  I have a Linksys WMP54G wireless pci adapter.  It works fine in Windows and connecting to this household's wireless network from windows.  

When I click on the network icon in the upper right, I can see the network that I want to connect to and a bar that I assume is the broadcast signal strength.  I click on it and it prompts me for the WEP hex.  I enter it and it says "Wireless connection to '[my network's name]' 0%" when I hover over the bar signal icon which looks empty.  It acts the same if I enter a bunch of random letters and numbers in the WEP hex field.  Point is, I can't get any signal from this network.  I'm not even sure if it is even trying to connect.  In the drop down under the network icon, it shows my wired connection and the wireless connection with the little select bubble filled in indicating that it is connected.  Still, when I unplug my ethernet, no internet.

In other threads, people have posted some helpful ish for the linux gurus, so here is some of that information:

```
ikedaman@ikedaman-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B3:84:A0:93   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
ikedaman@ikedaman-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:e0:d9:06  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fee0:d906/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:84158526 (80.2 MB)  TX bytes:2888255 (2.7 MB)
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166800 (162.8 KB)  TX bytes:166800 (162.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:6d:e3:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-6D-E3-FA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Let me know what you think or if you need anything else.

Thanks in advance.

Ike

---

