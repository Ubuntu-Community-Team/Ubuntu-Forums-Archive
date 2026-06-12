---
title: "Linksys wmp54g not detecting AP"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by neumeka on 2007-01-07
I am running Xubuntu Edgy and have just installed a Linksys wmp54g wireless network adapter.  I know it installed correctly because it showed up in the networking window as wlan0.  (Actually two entries appeared wlan0 and wmaster0.  As far as I can tell they are both the same)

I checked the enable button.  *ifconfig*  returns the following:

```
eth0      Link encap:Ethernet  HWaddr 00:C0:A8:80:68:F1  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fe80:68f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1549197 (1.4 MiB)  TX bytes:297977 (290.9 KiB)
          Interrupt:201 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5676 (5.5 KiB)  TX bytes:5676 (5.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:14:C6:3C  
          inet6 addr: fe80::218:39ff:fe14:c63c/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:6336 (6.1 KiB)
          Base address:0x7000 

```

*iwconfig produces this:*
```
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"KNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

```

However, *iwlist wlan0 scanning* tells me that there are no scan results.  But I know that there is indeed an available ESSID being broadcast becuase my windows laptop can connect.  Any suggestions?

---

### Post by phossal on 2007-01-07
Have you tried?
[SIZE="1"](where wlan0 is replaced by your wireless interface):[/SIZE]

```
sudo dhclient wlan0
```

---

### Post by neumeka on 2007-01-07
the results for *sudo dhcpclient wlan0*:

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/00:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Don't know if this has anything to do with my problem, but why do wlan0 and wmaster0 both show up under my networking configuring tool?

---

### Post by phossal on 2007-01-08
If you have a wireless dongle/card that is properly recognized, you can connect to a wireless router without configuring any of the *files*. 

For example, I use the wg111, and many tutorials indicate that I should configure *iftab* or */etc/network/interfaces*. It isn't necessary though. A properly recognized wireless interface will connect to a non-wep/wpa enabled router by a combination of the basic commands: iwconfig/dhclient, and sometimes ifup/ifdown.

You might get two wireless interfaces appearing if your files are improperly configured.

---

