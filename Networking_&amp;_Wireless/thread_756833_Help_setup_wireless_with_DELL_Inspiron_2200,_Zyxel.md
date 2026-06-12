---
title: "Help setup wireless with DELL Inspiron 2200, Zyxel Wireless Cable Router &amp; USB"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by sid.kris on 2008-04-16
Hi,

I am new to Linux. Have always used Windows but decided to try Ubuntu because my system was very slow with XP & Anti-Virus software etc. I now have a vastly performant laptop et al. However the thing I need most doesnt work...Wireless. I got ZyDAS ZyXEL Wireless Cable Router & USB Adaptor as it said on the box that it was compatible with Linux. I checked my laptop specification and found it has a Wireless Mini PCI Card. I am unable to get Wireless working. I went through many documents on the internet but I am completely confused & puzzled by all this technical stuff. Here is my hardware details:

[LIST=1]
[*]DELL Inspiron 2200
[*]DELL Wireless 1370 802.11b/g Mini PCI Card
[*]ZyDAS ZyXEL (Model: NBG334W) - USB Wireless Adaptor & Wireless Cable Router ([http://www.zyxel.co.uk/web/product_family_detail.php?PC1indexflag=20040520161313&CategoryGroupNo=D6E54FEE-BE55-46BB-B3DB-29E3361862EE](http://www.zyxel.co.uk/web/product_family_detail.php?PC1indexflag=20040520161313&CategoryGroupNo=D6E54FEE-BE55-46BB-B3DB-29E3361862EE))
[/LIST]

I have installed Ubuntu 8.04 beta. The ZyXEL manuals say that I have to access 192.168.1.1 using a browser and setup Wireless. I am unable to connect to 192.168.1.1. The manuals also mention a password "1234". I can see my wireless router in the Network Monitor and when I select it, I am able to connect (it says connected and 100%). However I am unable to connect to the Internet and access any websites. I would be happy if I can get it working with any one wireless.

Please bear with my stupidity. Can someone pls guide me with the step by step instructions. Any help would be very much appreciated.

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-16
They probably mean [http://192.168.1.1](http://192.168.1.1). Did you try that? Also, can you hook up to the router with a wire and get an IP address? Then open Firefox and put in [http://192.168.1.1](http://192.168.1.1) and configure the wireless. Post back and give us the good news!

---

### Post by sid.kris on 2008-04-17
Hello,

Thanks for the quick response. I tried accessing [http://192.168.1.1](http://192.168.1.1) from the browser but failed. I connected my laptop directly to the router (one document on the internet said I have to connect to the WAN port) but still couldnt access [http://192.168.1.1](http://192.168.1.1). How do I get an IP address...Can you please advice?

Thanks once again for taking interest in my query.

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-17
In every router I am familiar with, the cable modem or DSL modem connects to the WAN port and all the computers connect to the LAN ports or wirelessly. I suggest connecting this way:

Modem--->WAN port on router   LAN port---> computer

Then power off (unplug) the modem and the router for 15 seconds. Power up the modem and let all the lights light and blink and settle. Power up the router. Open a terminal on the computer and do:```
sudo dhclient eth0
```Did you get an IP address? Can you now do [http://192.168.1.1](http://192.168.1.1) and configure the wireless in the router?

---

### Post by sid.kris on 2008-04-18
Hello,

I tried what you advised and I couldnt access [http://192.168.1.1](http://192.168.1.1) still. Though this is frustrating, it is a good learning experience for a non-IT person like me. I dont want to give up just yet :). I have the result of many commands I have found in my search for the solution:

[LIST=1]
[*]sudo dhclient eth0
[*]ip address show
[*]ifconfig
[*]iwconfig
[*]lsusb
[*]cat /etc/network/interfaces
[*]cat /etc/resolv.conf
[/LIST]

The output of these commands is shown below:

```
sid@sid-laptop:~$ sudo dhclient eth0
[sudo] password for sid: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:12:3f:f7:9b:cf
Sending on   LPF/eth0/00:12:3f:f7:9b:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```



```
sid@sid-laptop:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:12:3f:f7:9b:cf brd ff:ff:ff:ff:ff:ff
    inet 169.254.9.237/16 brd 169.254.255.255 scope link eth0:avahi
    inet6 fe80::212:3fff:fef7:9bcf/64 scope link 
       valid_lft forever preferred_lft forever
3: wmaster0: <BROADCAST,MULTICAST> mtu 1500 qdisc ieee80211 qlen 1000
    link/ieee802.11 00:14:a5:3c:22:9d brd ff:ff:ff:ff:ff:ff
4: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:14:a5:3c:22:9d brd ff:ff:ff:ff:ff:ff
5: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:19:cb:03:62:33 brd ff:ff:ff:ff:ff:ff
```



```
sid@sid-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:f7:9b:cf  
          inet6 addr: fe80::212:3fff:fef7:9bcf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:123137 (120.2 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:12:3f:f7:9b:cf  
          inet addr:169.254.9.237  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:410825 (401.1 KB)  TX bytes:410825 (401.1 KB)
```



```
sid@sid-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b/g  ESSID:"ZyXEL"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:3C:09:60   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



```
sid@sid-laptop:~$ lsusb
Bus 005 Device 002: ID 0586:3410 ZyXEL Communications Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```


```
sid@sid-laptop:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0
```


```
sid@sid-laptop:~$ cat /etc/resolv.conf
nameserver 62.30.112.39
nameserver 194.117.134.19
nameserver 62.30.0.39
```

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-18
Sid-
We are no where near giving up! We are so close, I can feel it!

Just until we can get the router set up, detach and set aside the little ZyDAS and hook up the wire. I know it's probably a pain, in my house, the DSL modem, router, etc. are in a cabinet in the laundry room; my desktop, when I am hard-wired, is the ironing board!

Reboot your machine and then please let me see, in order:```
ifconfig
sudo ifconfig eth0 up
sudo dhclient eth0
sudo ethtool eth0
```We'll get it.

You have been connected at some time, otherwise *resolv.conf* would not be filled in; unless you filled it in yourself.

---

### Post by sid.kris on 2008-04-23
Hello,

I executed the commands you advised in the exact order. Please find the results below:

```
sid@sid-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:f7:9b:cf  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:56766 (55.4 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:12:3f:f7:9b:cf  
          inet addr:169.254.9.237  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:249770 (243.9 KB)  TX bytes:249770 (243.9 KB)
```

```
sid@sid-laptop:~$ sudo ifconfig eth0 up
```

```
sid@sid-laptop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 7466
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:12:3f:f7:9b:cf
Sending on   LPF/eth0/00:12:3f:f7:9b:cf
Sending on   Socket/fallback
DHCPREQUEST of 82.45.73.225 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 82.45.73.225 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 82.45.73.225
PING 82.45.72.1 (82.45.72.1) 56(84) bytes of data.

--- 82.45.72.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

```
sid@sid-laptop:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
```

Also I have the output of a few other commands:

```
sid@sid-laptop:~$ cat /etc/networks
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0
```

```
sid@sid-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 sid-laptop

# The following lines are desirable for IPv6 capable hosts
```

```
sid@sid-laptop:~$ cat /etc/hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
```

```
sid@sid-laptop:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
```

```
sid@sid-laptop:~$ cat /etc/host.conf
# The "order" line is only used by old versions of the C library.
multi off
```

If I click the Network icon I get a prompt to connect to a wired network. I have attached the screenshot. Please advice me as to what values I should enter to connect. Also the values to choose for EAP and Phase2 Type in the dropdown are:

EAP - PEAP, TLS, TTLS
Phase2 Type -  None, PAP, MSCHAP, MSCHAPV2, GTC

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-23
It would shock me if your *wired* network were 802.1x encrypted. However, NetworkManager at least thinks there is something out there to connect to! I would first try Manual Settings and the following:```
IP address 192.168.1.2
Netmask 255.255.255.0
Network 192.168.1.1
```Save, close and see if you connect with:```
ping -c3 192.168.1.1
ping -c3 www.google.com
```Then see if you can get to the admin page of the router: [http://192.168.1.1](http://192.168.1.1)

I notice you need to disable your popup blocker to get this to work. Go to Firefox -> Edit -> Preferences and set an exception for popups for 192.168.1.1.

Let us know.

---

### Post by sid.kris on 2008-04-23
Hello,

I will try that out. I assume that I need to go to Network Manager and set the details for eth0 (IP Address, Netmask, Gateway). Actually I setup wireless with WPA when I had Windows XP. Would that have been the cause of the problems. The manuals say that if I power-off the router and power-on everything would be reset. I have even done that. Anyways I will try what you advised today and let you know the results. Thanks a lot.

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-23
> I assume that I need to go to Network Manager and set the details for eth0 (IP Address, Netmask, Gateway).Yes, exactly.> Actually I setup wireless with WPA when I had Windows XP. Would that have been the cause of the problemsThat would only explain why you might have a bit of difficulty connecting wirelessly, not wired.> I will try what you advised today and let you know the results.Looking forward to it.

---

### Post by sid.kris on 2008-04-24
Hello,

Your advice worked! I was able to access [http://192.168.1.1](http://192.168.1.1) and setup wireless. I am still unable to use the wireless. I find eth1 and wlan0. Tried disabling eth1 but it didnt work. Please advice me. Thanks a lot for your patience. Here are my wireless details after setup:

```
System Name: ZyXEL
      Firmware Version: V3.60(AMS.0) | 05/18/2007
      WAN Information     
          - MAC Address: 00:19:cb:3c:09:61
          - IP Address: 82.34.247.201
          - IP Subnet Mask: 255.255.255.0
          - DHCP: Client
      LAN Information:     
          - MAC Address: 00:19:cb:3c:09:60
          - IP Address: 192.168.1.1
          - IP Subnet Mask: 255.255.255.0
          - DHCP: None
      WLAN Information:     
          - MAC Address: 00:19:cb:3c:09:60
          - Name(SSID): ZyXEL   
          - Channel: 6
          - Operating Channel: 6
          - Security Mode: WPA2-PSK
          - 802.11 Mode: 802.11b/g
```

Can you pls advice me as to what steps I should be following next to setup wireless, now that i have configured the wireless router.

Kind Regards,
Sid

---

### Post by chili555 on 2008-04-24
> - Security Mode: WPA2-PSKI know very little about WPA. Generally the process is to install *wpa-supplicant* from Synaptic, and then you should be able to click the Network Manager icon at the upper right and fill in your WPA details and connect. If it doesn't work quite that smoothly, I would start a new thread, "Please help me set up WPA" or some such.

Sorry, I have run out of talent. Now, if you want to try without encryption or with WEP, Network Mangler should do fine. The manual way is to open a terminal and do:```
sudo iwconfig
```See which wireless interface is actually alive. Let's use eth1 for now, but substitute wlan0 if that turns out to be yours.```
sudo iwconfig eth1 essid ZyXEL
sudo iwconfig eth1 key urWEPkeyHERE
sudo dhclient eth1
```Leave out the WEP key if you are not using WEP, of course.

Network Manager will not allow connection of wireless if you are connected wired, so before you start all this, disconnect the wire and do:```
sudo ifdown eth0
```Good luck!

---

### Post by sid.kris on 2008-05-07
Hello,

I re-configured the wifi from WPA2 to WEP and tried the steps you advised. I tried with both eth1 and wlan0. Found out that wlan0 is the laptop's built in wireless and eth1 is the Zyxel USB adaptor. Even tried with wlan0 after removing the USB adaptor. Even tried manually specifying the IP address, Subnet Mask and Gateway in the NetworkManager. All the efforts failed.

When I tried step 2 it threw an error. I googled and found out that I have to prepend a "s:" to the password.

```
sidsid@sid-laptop:~$ sudo iwconfig wlan0 key "sidkriswifipassword"
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "sidkriswifipassword".
```

I tried all the steps with the passphrase and hex key too. Here are the results after prepending step 2 with "s:". The results were the same with eth1 too:

```
sid@sid-laptop:~$ sudo iwconfig wlan0 essid "ZyXEL"
```

```
sid@sid-laptop:~$ sudo iwconfig wlan0 key "s:sidkriswifipassword"
```

```
sid@sid-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7576
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:3c:22:9d
Sending on   LPF/wlan0/00:14:a5:3c:22:9d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
sid@sid-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

Looks like Linux is not for an average user like me ](*,). Guess I have no choice but to go back to my Win XP :(.

Kind Regards,
Sid

---

