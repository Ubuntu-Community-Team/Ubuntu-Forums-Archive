---
title: "Is my wireless card broken or something?"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by Comrade42 on 2007-04-09
(I'm on Edgy 6.10)

For the past few days I have not been able to connect to any wireless signal at all. One week ago it worked perfectly but now it isn't working. My wireless connection icon has a (!) triangle on it, and out of the four possible bars filled, I get one yellow bar. When I doubleclick on it I get into Connection Properties and it says that connection "eth1" (my wireless) is "Disconnected". I go to "Configure" and go to the drop-down menu that used to show names of nearby networks, and it doesn't give me anything, even though I see a functioning wireless router in front of me. (I have tried this at two different places, different routers.) Even if I type in the correct name of the router (Network name/ESSID), it doesn't connect, and when I exit out of "Configure", it still gives me "Disconnected". I have no idea what's going on. Any help?

---

### Post by josephus on 2007-04-09
Sounds like the wireless connection is disabled.

Go into System->Administration->Networking and see if eth1 is checked or not.  If not check it.

You could also try from terminal

```
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by skip27 on 2007-04-09
try 'sudo ifconfig <interface> up'

---

### Post by Comrade42 on 2007-04-09
Re: josephus

I went into the administration window and yes, the box is checked.
I tried the commands you gave me and this is what I got:
```

tom@tom-laptop:~$ sudo ifdown eth1
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 4620
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:3f:de:f5
Sending on   LPF/eth1/00:12:f0:3f:de:f5
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```

```

tom@tom-laptop:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:3f:de:f5
Sending on   LPF/eth1/00:12:f0:3f:de:f5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Does this mean anything?


Re: skip27

I entered the command exactly as you gave it and nothing happened, as far as I can tell.


I also followed advice from another forum and it didn't help. Here's what I tried:

```
tom@tom-laptop:~$ sudo iwconfig eth1 ap any

```
Nothing happened.

```
tom@tom-laptop:~$ iwlist eth1 scan
eth1      No scan results
```

---

### Post by josephus on 2007-04-09
can you post some more information about your card

```
lspci | grep Eth
or 
lshw -class Network
```


and check dmesg to see if there are any error messages that might be related.  post them here if you see anything noteworthy.

---

### Post by Comrade42 on 2007-04-09
```
tom@tom-laptop:~$ lspci | grep Eth
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

```
tom@tom-laptop:~$ lshw -class Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:57:54:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 ip=192.168.0.102 multicast=yes
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:3f:de:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=radio off
       resources: iomemory:faffd000-faffdfff irq:5

```

Same thing as above, but with sudo:

```
tom@tom-laptop:~$ sudo lshw -class Network
Password:
 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:57:54:dc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.0.102 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:3f:de:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=radio off
       resources: iomemory:faffd000-faffdfff irq:5

```

The "configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=radio off" makes me suspicious...

---

### Post by josephus on 2007-04-09
is there a on/off switch for your wireless card.  on my laptop for instance i can use the combination fn+f5 to turn off the card .

---

### Post by Comrade42 on 2007-04-10
Er... oh my god. I can't believe I could've overlooked that. I didn't even know it was there... Uh, sorry about all this. Problem's fixed now.

---

### Post by josephus on 2007-04-10
well glad it's working now.

---

### Post by achill3z on 2007-04-15
I have a similar issue as Comrade42...So, here's a little background...
I installed the drivers for my Dell E1705 Inspiron with the 802.11 Draft n mini wireless card using ndiswrapper. The drivers installed fine, and Edgy recognizes my hardware. I went to System>Administration>Networking and enabled my wireless connection wlan0 and configured it to use DHCP. I have my router, which is a Linksys WRT54GS, set up with WPA-TKIP encryption and my passphrase is one similar to this(Plain ASCII)(...and no, this is not my passphrase, just an example showing that it is alphanumeric with symbols and such) [HTML]JhhU(?NUna|3KpMv~jHa"^s8C|Q?#2G^0<RlPR9>nN4#do`W_Ut@=JKTlAxTls5[/HTML] which I got off of [www.grc.com/passwords](www.grc.com/passwords) .  I configured wlan0 with this passphrase and I entered the correct ESSID .  My wifi light on my laptop is lit and if I do a Fn+F2 combination, it turns my wifi light on and off. However, when I go into the wlan0 properties, it shows that the interface is disconnected.  Here are the results of several commands that you might find helpful to help me troubleshoot this. One side note/question...do I have to do anything different to enable Edgy to use WPA-TKIP encryption? Or, does it do this natively? One more thing, I have my router set to NOT broadcast my ESSID AND I have MAC address filtering enabled, but, the router lets it on while using Vista, so that shouldn't matter....just want you to know my whole setup.
[HTML]laptop@laptop-laptop:~$ sudo lshw -class Network
Password:
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:a8:ab:47
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.41 firmware=Broadcom,10/12/2006, 4.100.15.5 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ecffc000-ecffffff iomemory:e0000000-e00fffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:5c:0e:ef
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.100 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ecbfe000-ecbfffff irq:177
  *-network
       description: IEEE1394 interface
       physical id: 2
       logical name: eth1
       serial: 34:4f:c0:00:30:53
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes
[/HTML]
[HTML]laptop@laptop-laptop:~$ lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
[/HTML]
[HTML]laptop@laptop-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]
[HTML]laptop@laptop-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:CF:A8:AB:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:ecffc000-ed000000 
[/HTML]
[HTML]laptop@laptop-laptop:~$ sudo ifup wlan0
eval: 1: Syntax error: Unterminated quoted string
run-parts: /etc/network/if-pre-up.d/wireless-tools exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/HTML]
[HTML]laptop@laptop-laptop:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6434
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback
[/HTML]

Please Help!

---

### Post by achill3z on 2007-04-15
Anyone?

---

### Post by josephus on 2007-04-15
Well the interesting is here:

```
eval: 1: Syntax error: Unterminated quoted string
run-parts: /etc/network/if-pre-up.d/wireless-tools exited with return code 2
```

I'm not sure what this refers to - maybe a malformed passphrase?  Are there quotes in your passphrase (sorry I don't use WPA, so I don't know if they are even allowed).

Anyways have you tried with an unsecured network to see if it is related to the encryption?

---

### Post by achill3z on 2007-04-15
To answer your question, yes there were quotes in my old passphrase. Ok, so I tried another WPA passphrase...this one was just alphanumeric and this is what I get with ifup wlan0
[HTML]laptop@laptop-laptop:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/HTML]
I don't really know how to use wpa_supplicant, but I downloaded wpa_gui and these are the results of it:
[HTML]laptop@laptop-laptop:~$ wpa_gui
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
[/HTML]
Here are the results when I totally disable my security on my router and I have it set to broadcast my SSID:
[HTML]laptop@laptop-laptop:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/HTML]

---

### Post by josephus on 2007-04-15
The last error message i think is related to the encryption key.  I think somewhere in one of the network configuration utilities you still have encryption set on.

i'm not sure what the correct sequence of events is from the command line but give this a try:

```

sudo ifdown ath0
sudo iwconfig wlan0 enc off
sudo iwconfig wlan0 key off
sudo iwconfig wlan0 essid any 
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

---

### Post by achill3z on 2007-04-15
entered wrong info here....see next post.

---

### Post by achill3z on 2007-04-15
I didn't complete the commands b/c I got the following from the first command: btw, thanks for all the help thus far.
[HTML]britt@britt-laptop:~$ sudo ifdown ath0
ifdown: interface ath0 not configured
[/HTML]

---

### Post by josephus on 2007-04-15
sorry.  the first line is my mistake

wlan0 is the name of your wireless interface, mine happens to be ath0.

```
sudo ifdown wlan0
```

---

