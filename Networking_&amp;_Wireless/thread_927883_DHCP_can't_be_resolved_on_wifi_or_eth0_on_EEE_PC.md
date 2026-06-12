---
title: "DHCP can't be resolved on wifi or eth0 on EEE PC"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by tehschulman on 2008-09-23
I'm back at home visiting for a few days and I've been able to use my parent's network without a problem, until last night. Whenever I attempt to connect via ethernet or wireless I find that the network doesn't give me a DHCP address. This is very frustruating, especially considering I've made almost no changes to my machine since yesterday afternoon and yesterday evening. I did install some packages to get my GPS unit working under Linux, but otherwise no major systemwide changes that would effect the network.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: RaLink Unknown device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)


```

syslog
```

Sep 23 12:25:07 lilblackbox NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ra0 / linksys 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Deactivating device ra0. 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Device ra0 activation scheduled... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) started... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Sep 23 12:25:07 lilblackbox NetworkManager: <info>  Activation (ra0/wireless): access point 'linksys' is unencrypted, no key needed. 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ra0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was 'OK' 
Sep 23 12:25:08 lilblackbox kernel: [  360.887760] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 442
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was 'OK' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was '0' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was 'OK' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was 'OK' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  SUP: response was 'OK' 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  Supplicant state changed: 0 
Sep 23 12:25:08 lilblackbox NetworkManager: <info>  Supplicant state changed: 0 
Sep 23 12:25:09 lilblackbox kernel: [  361.109517] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
Sep 23 12:25:09 lilblackbox NetworkManager: <info>  Supplicant state changed: 1 
Sep 23 12:25:09 lilblackbox NetworkManager: <info>  Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys'. 
Sep 23 12:25:09 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 23 12:25:09 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) started... 
Sep 23 12:25:10 lilblackbox NetworkManager: <info>  Activation (ra0) Beginning DHCP transaction. 
Sep 23 12:25:10 lilblackbox dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 134519072
Sep 23 12:25:10 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 23 12:25:10 lilblackbox NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ra0 
Sep 23 12:25:10 lilblackbox avahi-daemon[4845]: Registering new address record for fe80::215:afff:fee5:a453 on ra0.*.
Sep 23 12:25:11 lilblackbox kernel: [  364.044537] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Sep 23 12:25:11 lilblackbox kernel: [  364.048011] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Sep 23 12:25:11 lilblackbox NetworkManager: <info>  Supplicant state changed: 0 
Sep 23 12:25:11 lilblackbox NetworkManager: <info>  Supplicant state changed: 1 
Sep 23 12:25:12 lilblackbox dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Sep 23 12:25:12 lilblackbox NetworkManager: <info>  Supplicant state changed: 0 
Sep 23 12:25:12 lilblackbox NetworkManager: <info>  Supplicant state changed: 0 
Sep 23 12:25:15 lilblackbox kernel: [  367.169406] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 249
Sep 23 12:25:15 lilblackbox kernel: [  367.169728] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Sep 23 12:25:15 lilblackbox NetworkManager: <info>  Supplicant state changed: 1 
Sep 23 12:25:16 lilblackbox dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
Sep 23 12:25:16 lilblackbox dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Sep 23 12:25:16 lilblackbox dhclient: DHCPREQUEST of 192.168.1.103 on ra0 to 255.255.255.255 port 67
Sep 23 12:25:16 lilblackbox dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Sep 23 12:25:16 lilblackbox dhclient: bound to 192.168.1.103 -- renewal in 41952 seconds.
Sep 23 12:25:19 lilblackbox kernel: [  371.880626] ra0: no IPv6 routers present
Sep 23 12:26:49 lilblackbox NetworkManager: <info>  Device 'ra0' DHCP transaction took too long (>99s), stopping it. 
Sep 23 12:26:49 lilblackbox dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 6738
Sep 23 12:26:49 lilblackbox dhclient: killed old client process, removed PID file
Sep 23 12:26:49 lilblackbox dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67
Sep 23 12:26:49 lilblackbox dhclient: send_packet: Network is unreachable
Sep 23 12:26:49 lilblackbox dhclient: send_packet: please consult README file regarding broadcast address.
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ra0 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ra0 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) failure scheduled... 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) failed for access point (linksys) 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Activation (ra0) failed. 
Sep 23 12:26:50 lilblackbox NetworkManager: <info>  Deactivating device ra0. 
Sep 23 12:26:50 lilblackbox avahi-daemon[4845]: Withdrawing address record for fe80::215:afff:fee5:a453 on ra0.
Sep 23 12:27:06 lilblackbox kernel: [  478.150521] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 245
Sep 23 12:27:36 lilblackbox kernel: [  508.520227] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 418
Sep 23 12:28:06 lilblackbox kernel: [  538.511206] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 276
Sep 23 12:28:36 lilblackbox kernel: [  568.508216] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 330
Sep 23 12:28:53 lilblackbox kernel: [  585.565329] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep 23 12:28:53 lilblackbox kernel: [  585.568525] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep 23 12:28:53 lilblackbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Will activate connection 'eth0'. 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Device eth0 activation scheduled... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) started... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 23 12:28:53 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 23 12:28:54 lilblackbox NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep 23 12:28:54 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 23 12:28:54 lilblackbox NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 23 12:28:55 lilblackbox avahi-daemon[4845]: Registering new address record for fe80::222:15ff:fe61:a3fa on eth0.*.
Sep 23 12:28:58 lilblackbox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep 23 12:28:58 lilblackbox dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Sep 23 12:28:58 lilblackbox dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
Sep 23 12:28:58 lilblackbox dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Sep 23 12:28:58 lilblackbox dhclient: bound to 192.168.1.100 -- renewal in 41939 seconds.
Sep 23 12:29:04 lilblackbox kernel: [  596.256355] eth0: no IPv6 routers present
Sep 23 12:29:06 lilblackbox kernel: [  598.502244] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 249
Sep 23 12:29:06 lilblackbox NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Sep 23 12:29:36 lilblackbox NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Sep 23 12:29:36 lilblackbox kernel: [  628.496279] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 164
Sep 23 12:30:33 lilblackbox NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>99s), stopping it. 
Sep 23 12:30:33 lilblackbox dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7334
Sep 23 12:30:33 lilblackbox dhclient: killed old client process, removed PID file
Sep 23 12:30:33 lilblackbox dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Sep 23 12:30:33 lilblackbox dhclient: send_packet: Network is unreachable
Sep 23 12:30:33 lilblackbox dhclient: send_packet: please consult README file regarding broadcast address.
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  Activation (eth0) failure scheduled... 
Sep 23 12:30:34 lilblackbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 23 12:30:35 lilblackbox NetworkManager: <info>  Activation (eth0) failed. 
Sep 23 12:30:35 lilblackbox NetworkManager: <info>  Deactivating device eth0. 
Sep 23 12:30:35 lilblackbox avahi-daemon[4845]: Withdrawing address record for fe80::222:15ff:fe61:a3fa on eth0.
Sep 23 12:30:35 lilblackbox NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 


```

Router is a linksys which I've had no problems connecting to before. I can't even access the router information when I'm plugged in via ethernet. ra0 is the wireless adapter. HELP!

---

### Post by tehschulman on 2008-09-23
I'm able to run dhclient on my adapters and it appears to bind an address, this is verified by my router status page, but I still can't seem to access the internet. Network Manager fails to connect anything.

Really scratching my head on this...

---

### Post by tehschulman on 2008-09-23
Ok, a further update. I'm now online with manually entered IP information. Looks like it isn't my hardware that's screwy after all. I'm left with the question though, **why can't my computer connect to the internet even after I've been assigned a DHCP address on my router?**

---

### Post by Iowan on 2008-09-23
Glad you got online.  If you'd like to pursue it, post results of **ifconfig** and contents of **/etc/network/interfaces**.

---

### Post by tehschulman on 2008-09-25
Ok, so I'm back home now and can successfully connect to my wireless. However, I have to manually start dhcp in order to resolve an address on the network. dhclient and dhcpbd, which I'm assuming were installed by default, do not seem to find an address, so I've installed dhcpcd and have been using that to get online. 
 
More annoyingly though, my router has been asking me for my wifi password every five minutes in order to stay connected. Really not cool, D-link.

ifconfig (ra0 is online)
```

eth0      Link encap:Ethernet  HWaddr 00:22:15:61:a3:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:11
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1719471 (1.6 MB)  TX bytes:1719471 (1.6 MB)

ra0       Link encap:Ethernet  HWaddr 00:15:af:e5:a4:53  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fee5:a453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329830 errors:169 dropped:0 overruns:0 frame:0
          TX packets:64189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61289262 (58.4 MB)  TX bytes:26835174 (25.5 MB)
          Interrupt:18 

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.180.1  Bcast:172.16.180.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.199.1  Bcast:192.168.199.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

/etc/network/interfaces                                        
```

auto lo
iface lo inet loopback

```

---

### Post by willca on 2008-09-25
What is your wireless security setup on that router?

If it asks for a password, then its likely doing some WEP in there.

---

### Post by mlnsharma on 2008-09-25
Hi Guys, I am a new user...iHave Ubuntu 8.04 installed in my pc now.. I use an ethernet card for accessing Internet in a LAN..When i use in xp it automatically detected the ethernet card..But in ubuntu it didnt...And even after manually configuring it is not detecting the card...Can any one help me with this issue...Pls do reply !!

---

### Post by tehschulman on 2008-09-25
> **willca said:**
> What is your wireless security setup on that router?

If it asks for a password, then its likely doing some WEP in there.

Yes it's set up to do 64bit WEP, but it shouldn't require me to keep entering the password. I've connected to this network before and have only had to identify myself once. Now I'm being asked to do it every few minutes and it's quite annoying. I think it has something to do with dhcpcd, since I'm running it manually.

> **mlnsharma said:**
> Hi Guys, I am a new user...iHave Ubuntu 8.04 installed in my pc now.. I use an ethernet card for accessing Internet in a LAN..When i use in xp it automatically detected the ethernet card..But in ubuntu it didnt...And even after manually configuring it is not detecting the card...Can any one help me with this issue...Pls do reply !!

You should probably start your own thread for this, but it sounds like kernel issue. Make sure you have the right network card drivers installed in your kernel for your hardware.

---

### Post by tehschulman on 2008-09-25
Currently using Wireshark to see what's causing the disconnecting. It looks like my DHCP address just keeps releasing every few minutes for no particular reason. Would really appreciate some help with this.

---

### Post by willca on 2008-09-26
then try this out and see if it stops bugging you about password...

Edit /etc/network/interfaces

auto wlan0
iface inet wlan0 dhcp
wireless-essid whateveryouressidisputithere
wireless-key whateveryourwirelesskeyputithere

Save and do
sudo /etc/init.d/networking restart

---

### Post by tehschulman on 2008-09-26
Still getting asked for my password. Here's what it outputted when I restarted /etc/init.d/networking

```

dmschulman@lilblackbox:~$ sudo /etc/init.d/networking restart
sudo: unable to resolve host lilblackbox
 * Reconfiguring network interfaces...                                There is already a pid file /var/run/dhclient.ra0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

ifmetric not found
Listening on LPF/ra0/00:15:af:e5:a4:53
Sending on   LPF/ra0/00:15:af:e5:a4:53
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ifmetric not found
                                                               [ OK ]

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wireless-essid ProjectIthaca
wireless-key babeedadee

```

Setting those variables forces the Network Manager into manual mode which does not seem to work for me at all right now, so I've removed those entries. I have to be in roaming mode and connect to the AP that way for anything to work. Once it connects I run dhcpcd manually and only then can I get online.

---

### Post by tehschulman on 2008-09-26
SOLVED

There were some stray scripts in my /etc/dhcp3 folder, from some package I installed way back when I'm assuming, that were forcing the DHCP release and generally screwed things up. Deleted them as sudo and now I'm back online!

---

