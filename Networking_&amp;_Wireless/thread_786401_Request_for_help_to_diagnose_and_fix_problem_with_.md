---
title: "Request for help to diagnose and fix problem with dsl modem (pppoe)"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by d.rey on 2008-05-08
_0. Problem summary._
I have spent countless hours trying to connect to the Internet through an ADSL modem from a desktop using pppoe (Ubuntu 7.10 --Gutsy Gibbon). The summary is that after I issue the command pon dsl-provider, I cannot connect to the Internet; I see the following in /var/log/syslog:

```
May  7 19:08:08 fiesta pppd[11535]: Timeout waiting for PADS packets
May  7 19:08:08 fiesta pppd[11535]: Unable to complete PPPoE Discovery
```

Any guidance would be immensely appreciated. See details below.

_1. Hardware setup._
I am an Earthlink DSL subscriber, using the ZyXel Prestige 645 ADSL modem. I have a very old 10Mps hub (Compex  Microhub/8) connected to the modem and three things connected to the hub. First, an Apple desktop which can access the Internet fine (using pppoe in Apple's OS). Second, and Apple airport (to which Apple and Microsoft laptops connect and access the Internet fine). And third, a desktop running Ubuntu 7.10 (Gutsy Gibbon) --which I am struggling to get connected to the Internet and is the reason of my request of help.

_2. Sofware setup._
I am using Ubuntu 7.10 (Gutsy Gibbon) installed from CD's, and since I haven't been able to connect to the Internet, I haven't run any updates. Versions for some packages: ppp-2.4.4rel-9ubuntu2, pppconfig-2.3.17ubuntu1, pppoeconf-1.16ubuntu1.

_3. Problem description._
I assume that there's no problem with the wiring: the network card has two lights: the first one ("link/act") is on and flickering; the second one ("100") is off (the hub is 10Mbps).

I have three ethernet connectors on my computer: Two of them integrated on the motherboad (although, I believe I disabled one of these in the bios). The third one from a network card --which is the only one to which I have something connected.

ifconfig gives the following output:

```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:11:FE:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:04:5A:56:3F:EC  
          inet6 addr: fe80::204:5aff:fe56:3fec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2085 errors:2 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:1464 (1.4 KB)  TX bytes:634887 (620.0 KB)
          Interrupt:19 Base address:0x9000 

eth0:avah Link encap:Ethernet  HWaddr 00:0C:6E:11:FE:CB  
          inet addr:169.254.9.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:04:5A:56:3F:EC  
          inet addr:169.254.7.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112848 (110.2 KB)  TX bytes:112848 (110.2 KB)
```

I don't know why I have the eth0:avah and eth1:avah entries, but I assume there's nothing wrong with that.
Also, I don't know which is the network interface that pppoe should be using, but I assume is eth1 because it reads "RUNNING" in the ifconfig output.

I have used pppoeconf (with all the default options) and get the following /etc/ppp/peers/dsl-provider file:

```
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth1
usepeerdns
user "my_user_name@earthlink.net"
```
pppoeconf also created files /etc/ppp/chap-secrets and /etc/ppp/pap-secrets, which I am omitting.
I assume that the user name and password that I am providing are correct, but have not way knowing certainly, and I wonder how I could determine if the username/password combination is the the source of my problems.
Note that I have only used pppoeconf, not pppconfig.

When I do pon dsl-provider, I cannot access the Internet (I enter [http://74.125.19.99/](http://74.125.19.99/) in Firefox's and it says that connection with the server can't be established). I see the following in /var/log/syslog:
```
May  7 23:35:32 fiesta pppd[12340]: Plugin rp-pppoe.so loaded.
May  7 23:35:32 fiesta pppd[12342]: pppd 2.4.4 started by root, uid 0
May  7 23:35:37 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
May  7 23:35:41 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
May  7 23:35:52 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
May  7 23:36:07 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:36:07 fiesta pppd[12342]: Unable to complete PPPoE Discovery
May  7 23:36:08 fiesta dhclient: No DHCPOFFERS received.
May  7 23:36:08 fiesta dhclient: No working leases in persistent database - sleeping.
May  7 23:37:12 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:37:12 fiesta pppd[12342]: Unable to complete PPPoE Discovery
May  7 23:38:17 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:38:17 fiesta pppd[12342]: Unable to complete PPPoE Discovery
May  7 23:38:26 fiesta dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  7 23:38:33 fiesta dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May  7 23:38:41 fiesta dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May  7 23:38:53 fiesta dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May  7 23:38:57 fiesta dhclient: No DHCPOFFERS received.
May  7 23:38:57 fiesta dhclient: No working leases in persistent database - sleeping.
May  7 23:39:22 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:39:22 fiesta pppd[12342]: Unable to complete PPPoE Discovery
May  7 23:39:41 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
May  7 23:39:48 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
May  7 23:39:55 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
May  7 23:40:05 fiesta dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
May  7 23:40:12 fiesta dhclient: No DHCPOFFERS received.
May  7 23:40:12 fiesta dhclient: No working leases in persistent database - sleeping.
May  7 23:40:27 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:40:27 fiesta pppd[12342]: Unable to complete PPPoE Discovery
May  7 23:41:32 fiesta pppd[12342]: Timeout waiting for PADS packets
May  7 23:41:32 fiesta pppd[12342]: Unable to complete PPPoE Discovery
```
I don't know why this log has refereces to DHCPDISCOVER, I wonder if that points to any problem.
Note that I have no /etc/resolv.conf file; but I believe this is not the problem (or the first one, anyway), since I wasn't able to access [http://74.125.19.99/](http://74.125.19.99/) (Google's page).

Also note that if I first execute "pon dsl-provider" followed by "ifconfig ppp0", I get:

```
ppp0: error fetching interface information: Device not found
```
Any guidance would be greatly appreciated. Please, let me know if there's more information that would be helpful.

---

### Post by superprash2003 on 2008-05-08
is DHCP enabled in your router? your ifconfig tells that you arent getting an ip.. go to system->administration->network and choose your network card and set it to DHCP

---

### Post by d.rey on 2008-05-08
Thanks for the guidelines but that didn't work (see below).

> is DHCP enabled in your router?

While I am not sure, I believe that the ZyXel that I am using is not a router but a modem. I also believe that it does not incorporate DCHP capabilities.

> your ifconfig tells that you arent getting an ip.. go to system->administration->network and choose your network card and set it to DHCP 

I went to System->Administration->Nework, and in the "Connections" tab, I selected the properties for "Wired connection (eth1)" and for "Wired connection (eth0)". Both of them showed a tick for "Enable roaming connections". I removed these ticks, which ungreyed the section "Configuration settings" for each interface. This allowed me to select (for both interfaces) "DHCP".

Note that there's a third interface in System->Administration->Nework->Connections labelled "Modem connection", which is not enabled. I think doing so requires that I provide ISP phone number and some other modem settings that I believe are only for dialup.

---

### Post by superprash2003 on 2008-05-08
if DHCP isnt enabled in your modem... then instead of selecting DHCP select Static Ip address and enter ip address manually and then try

---

### Post by d.rey on 2008-05-09
Thanks Superprash2003

Do I need to get the ip address from my ISP?

If I recall correctly, the Apple computer that is using that same connection is using pppoe but it was not necessary to manually enter an IP address. Is it possible that my modem does not support DHCP, yet manually entering the IP address is unnecessary?

Daniel.

---

### Post by superprash2003 on 2008-05-09
most modems do support DHCP.. incase you have resetted it by any chance.. then it maybe turned off.. try this.. go to system->administration->network choose your network card( if you are not sure do it for both eth0 and eth1).. select Static ip address instead of DHCP.. and enter ip as 192.168.1.10 .. i am presuming that your router's ip address is 192.168.1.1 .. if not, you have to change it accordingly..Enter different ip's for eth0 and eth1.. like 192.168.1.10 for eth0 and 192.168.1.11 for eth1(since your not sure which is connected to the router).. now try to ping your router.. ping 192.168.1.1 replace 192.168.1.1 with your router's ip.. and also post output of ifconfig

---

