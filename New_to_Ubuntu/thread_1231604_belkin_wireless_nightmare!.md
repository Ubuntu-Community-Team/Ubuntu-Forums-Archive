---
title: "belkin wireless nightmare!"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Daverobb on 2009-08-04
Hope someone can help with this - not my laptop and i'm trying to help out a friend but can't get the wireless working after ....

anyway -- it's a Satelellite with copermine processor and 1 g of ram - works fine

belkin wireless g 54g model f5d7010 ver 4000 -- i checked a list (somewhere) and found that it uses the broadcom b43 driver -- couldn't get it working in Intrepid so upgraded to jaunty (which looks good on the laptop, btw)  but:

- wireless networks recognized (usually) when connected but no internet access

- card lights up (both lights) but doesn't seem to be communicating with modem/router

- proprietary driver shows but refuses to activate whenever i push the activate button (message = driver was just disabled but still in use.

what the .... ?

please help

---

### Post by fraser_m on 2009-08-04
Open a Terminal, and run:
```
lspci
```

Post output here.

---

### Post by Daverobb on 2009-08-04
```
lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by fraser_m on 2009-08-04
Is there any available drivers in System > Administration > Hardware Drivers?

---

### Post by Daverobb on 2009-08-04
Yes, 

the Broadcom b43 wireless driver 

software modem  


the broadcom says "the driver was just disabled [which i didn't do] but is still in use" -- the activate button is there but when i try to activate it goes to the download and install screen for a few minutes but doesn't change the driver status

i don't know what the software modem driver is for but i activated it (which worked) but no effect to the wireless

---

### Post by fraser_m on 2009-08-04
Could you open another terminal and do:
```
lsmod | grep b43
```

---

### Post by Daverobb on 2009-08-04
```
lsmod | grep b43
b43                   131484  0 
mac80211              217592  1 b43
led_class              12036  1 b43
ssb                    41220  1 b43
input_polldev          11912  2 b43,toshiba_acpi

```

---

### Post by fraser_m on 2009-08-04
Hm.
```
sudo ifconfig
```

And:
```
sudo iwconfig 
```

---

### Post by Daverobb on 2009-08-04
```
 sudo ifconfig
[sudo] password for flor: 
eth0      Link encap:Ethernet  HWaddr 00:00:39:e0:12:c2  
          inet addr:173.33.235.193  Bcast:173.33.235.255  Mask:255.255.254.0
          inet6 addr: fe80::200:39ff:fee0:12c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30907 errors:1 dropped:0 overruns:0 frame:1
          TX packets:25613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38021457 (38.0 MB)  TX bytes:5580027 (5.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:206248 (206.2 KB)  TX bytes:206248 (206.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:97:47:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:11:50:97:47:d0  
          inet addr:169.254.127.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-97-47-D0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Daverobb on 2009-08-04
```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by fraser_m on 2009-08-04
Are you trying to connect to a network called 'linksys'? If so, it appears to be connected.

---

### Post by CLomax on 2009-08-04
A wild stab in the dark...
Run these one line at a time.
```
ifconfig wlan0 up
iwconfig wlan0 essid linksys
dhcpcd wlan0
```
To check if it's working...
```
ping -c 3 google.com
```
> Are you trying to connect to a network calle 'linksys'? If so, it appears to be connected.
As far as my understanding goes, it isn't actually connected but the device just knows the network is there.

---

### Post by Daverobb on 2009-08-04
Right now I am connected via wired so i can message here.

When i connect the modem to the router and go wireless I can see the networks (linksys is this connection) but I can't access the connection 

I ran the first two commands but the third

```
sudo dhcpcd wlan0
sudo: dhcpcd: command not found

```:

---

### Post by CLomax on 2009-08-04
> **Daverobb said:**
> 
```
sudo dhcpcd wlan0
sudo: dhcpcd: command not found

```:

```
sudo apt-get install dhcpcd
```
?

---

### Post by fraser_m on 2009-08-04
The command should be:
```
sudo dhcpd wlan0
```

---

### Post by lswb on 2009-08-04
> **Daverobb said:**
> Right now I am connected via wired so i can message here.

I ran the first two commands but the third

```
sudo dhcpcd wlan0
sudo: dhcpcd: command not found

```:

Use the command "sudo dhclient wlan0" instead.

---

### Post by Daverobb on 2009-08-04
should i switch to wireless when i run this command?

---

### Post by fraser_m on 2009-08-04
Yes.

---

### Post by Daverobb on 2009-08-04
```
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:97:47:d0
Sending on   LPF/wlan0/00:11:50:97:47:d0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 36575 seconds.
```

---

### Post by CLomax on 2009-08-04
```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 36575 seconds.
```
Looks good to me. Disconnect the wire and see if the wireless works.

---

### Post by Daverobb on 2009-08-04
doesn't work 

```
sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6638
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:97:47:d0
Sending on   LPF/wlan0/00:11:50:97:47:d0
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 34529 seconds.
flor@flor-laptop:~$ ping -c 3 google.com
ping: unknown host google.com

```

big hmmmm

---

### Post by SunnyRabbiera on 2009-08-04
Broadcom really sucks, I would just get a new wireless adapter.
Linksys seems to work for the most part.

---

### Post by Daverobb on 2009-08-04
makes sense -- but still a drag to give up

---

### Post by lswb on 2009-08-04
Your dhclient output:
```
 DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
 DHCPACK of 192.168.1.100 from 192.168.1.1
 bound to 192.168.1.100 -- renewal in 34529 seconds.
```
shows that the adapter is working, it is associated with the AP and has an ip address assigned. A few things to check: 
-What happens when you ping another host on the local net or ping the router itself? i.e. ping 192.168.1.1
-Make sure you haven't inadvertently set up any firewall rules that are blocking connections. 
-Is it possible your router is not letting packets from your system go beyond the local net?

---

