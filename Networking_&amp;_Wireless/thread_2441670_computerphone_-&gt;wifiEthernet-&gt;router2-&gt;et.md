---
title: "computer/phone -&gt;wifi/Ethernet-&gt;router2-&gt;ethernet-&gt;router1-&gt;Internet"
date: 2020-04-25
forum: Networking &amp; Wireless
---

### Post by thosecars822 on 2020-04-25
Hello

I have a problem with the following topology:

Topology 1: computer with Lubuntu 18.04/phone ->Wifi->router2(192.168.1.2) with Open network authentication->Ethernet->router1(192.168.1.1) with WPA2->Internet

router2's DHCP is disabled
router1's DCHP is enabled in this range: 192.168.1.5-192.168.1.254
computer's IP is static: 192.168.1.10

The content of /etc/netplan/01-netcfg.yaml in the computer is as follows:

> # This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      addresses: [192.168.1.10/24]
      gateway4:  192.168.1.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]

I am trying to get a wireless connection to router2 from a computer or a phone in order to get online but for some strange reason I do not always get connected, only a few random times.

Nonetheless the following topology with the same computer and just replacing the Wifi connection between computer and router2 for the Ethernet connection works always like a charm to let me go online.

Topology 2: computer ->Ethernet->router2->Ethernet->router1->Internet

I guess out of the previous information it can be inferred that the problem might be at the wireless connection between router2 and computer/phone. I would like to be able to get online wirelessly from computer or phone though.

Router2 is AR-5387un COMTREND. I do not know how to set 192.168.1.1 as local gateway IP within router2's administration console. May be I need to fix  that.

Right now one of the phone that I have with me connects without problem but other phones do not connect. Anyway this phone had problems to connect 2 hours ago.

Another interesting thing I saw: one hour ago the computer got connected to router2 wirelessly. Then I disconnected and connnected it to router2 several times as a test and it kept on connecting well. But then I did another test: I connected the computer to router1 wirelessly and then I tried to connected it once again to router2 wirelessly and then the problems came back. Since then the computer did not connect wirelessly to router2 any other time.

> IP addr show displays the following for the computer's wifi interface when the computer does NOT get online:

> 3: wlx0013f7c99c1b: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:13:f7:c9:9c:1b brd ff:ff:ff:ff:ff:ff
    inet6 fe80::36ef:251:4694:81e7/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever



When the computer does not get online
> ping 192.168.1.1 
from the computer displays the following 
> 
connect: La red es inaccesible


I also just checked that the problem gets temporarily solved right away, ONLY for the computer, by restarting router1. But in case I change the wifi connection from router2's wifi interface to the router1's wifi interface and back to router2's wifi interface, then the problem arises again to get online on router2's wifi interface. Restarting router1 does NOT help with phones wifi connection to router2 at least right away like in the case of the computer. But is somehow strange because at some point may be 5 minutes or 10 minutes after getting online in the computer, one of the phones also ends up getting a local WLAN IP address and getting online successfully as well. And once this phone gets connected, I can disconnect it and connect it again to router2's wifi interface wirelessly without a problem unless I connect it in between to router1's wifi interface. Then getting back to router2's wifi interface will bring the problem back again.


I guess all the devices might be struggling to get a local IP address and that is why they have a difficult time getting online wirelessly but I do not know why.


Among other lines > journalctl | grep wpa_supplicant displayed the following, but I do not know what this means:
> <info>  [1587855813.7367] supplicant: wpa_supplicant running....
.... >  wpa_supplicant[876]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed....
.... >  wpa_supplicant[876]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none....
.... >  wpa_supplicant[876]: dbus: Failed to construct signal....
.....>  wpa_supplicant[876]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed

Does anyone have any idea about how I could fix the Wifi connection so that it stops having this random behaviour?

Thanks in advance.

---

### Post by TheFu on 2020-04-25
tl;dr plus i don't do cell phones and avoid wifi for security reasons.

But ....

> router1's DCHP is enabled in this range: 192.168.1.5-192.168.1.254
computer's IP is static: 192.168.1.10
This is a misconfiguration.  No static iPs can be within the DHCP range.

Router2 isn't a router.  it is a switch or a switch + WAP.  Don't use the WAN port on it.

---

### Post by thosecars822 on 2020-04-26
> **TheFu said:**
> tl;dr plus i don't do cell phones and avoid wifi for security reasons.

But ....


This is a misconfiguration.  No static iPs can be within the DHCP range.

Router2 isn't a router.  it is a switch or a switch + WAP.  Don't use the WAN port on it.

Thanks for your answer.

1. With reference to "outer1's DCHP is enabled in this range:  192.168.1.5-192.168.1.254", I noticed that after typing my question in  this forum and I updated changed router's DHCP range  as follows:  192.168.1.20-192.168.1.254.

2. With reference to "Router2 isn't a  router.  it is a switch or a switch + WAP.  Don't use the WAN port on  it.", I forgot to mention that router2 and router2 are connected through  their Ethernet interfaces.

Anyway I will try to improve the  description I already provided of the 2 topologies mentioned in my first  post to make it more friendly-readable:

router1's IP: 192.168.1.1
router2's IP: 192.168.1.2

router1's WIFI is enabled with WPA/WPA2.
router2's WIFI is enabled with Open network  authentication

 computer's SO: Lubuntu 18.04. 
Computer's LAN IP address is static: 192.168.1.10
Computer's WLAN IP address is dynamic.

Topology  1: computer / phone  ->computer's Wifi adapter->router2's WIFI interface->router2's  Ethernet port2->Ethernet cable->router1's Ethernet  port->router1(192.168.1.1)->Router1's WAN port->ONT (Optical  Network Terminal)->Internet

Topology 2: computer               ->computer's Ethernet adapter->Ethernet cable->router2's  Ethernet port1->router2's Ethernet port2->Ethernet  cable->router1's Ethernet  port->router1(192.168.1.1)->Router1's WAN port->ONT (Optical  Network Terminal)->Internet

Topology 3: computer ->Wifi->router1's WLAN interface->Router1's WAN port->ONT (Optical  Network Terminal)->Internet


Computer can get always online through topology2. Therefore topology 2 is NOT a problem

And  as I tried to explain in my first post, the Computer can get online  well  with topology1 after starting router1 ONLY IF I try this topology before  topology2. if I try topology2 at some point, then topology1  will NOT work afterwards until I reboot router1. For some reason the  computer will NOT get a valid WLAN IP in topology1 if I tried topology3  before topology1.


Does anyone have any idea about why this might be happening and about anything I could do to fix it?


Thanks in advance.

---

### Post by TheFu on 2020-04-26
You don't want 2 routers on the same subnet.  

See attachment. See the wifi-AP on the left?  That is just a router that doesn't use the WAN port, so it is a WAP+switch.  The wired ethernet connection to the ISP's router is using one of the LAN ethernet ports.

For a router to route, it needs 2 different subnets connected. The different subnets are critical, so it knows where to send packets. Usually, the WAN interface is hard-coded to have a different subnet than the LAN which is controlled by the router software. Of course, we can disable much of the router software by not enabling the built-in DHCP server, but we still have to NOT use the WAN port.

But if you have a Cisco 2950, then you can probably make the WAN port do whatever you want.  Any normal consumer router, running consumer firmware won't allow that.

Really need to see all the IPs for each interface and routing tables for each device to understand what's happening.

---

### Post by thosecars822 on 2020-04-26
> **TheFu said:**
> You don't want 2 routers on the same subnet.  

See attachment. See the wifi-AP on the left?  That is just a router that  doesn't use the WAN port, so it is a WAP+switch.  The wired ethernet  connection to the ISP's router is using one of the LAN ethernet ports.

For a router to route, it needs 2 different subnets connected. The  different subnets are critical, so it knows where to send packets.  Usually, the WAN interface is hard-coded to have a different subnet than  the LAN which is controlled by the router software. Of course, we can  disable much of the router software by not enabling the built-in DHCP  server, but we still have to NOT use the WAN port.

But if you have a Cisco 2950, then you can probably make the WAN port do  whatever you want.  Any normal consumer router, running consumer  firmware won't allow that.

Really need to see all the IPs for each interface and routing tables for each device to understand what's happening.

May be what I called router2 is only working as an WAP+switch because it's DHCP server is disabled and because it is in the same subnet as the real router, what I called "router1". Therefore I should have said WAP+switch instead of router2.
 
With reference to "we still have to NOT use the WAN port.", I did not use the WAN port in what I called router2.
 
I do not have any Cisco router.
 
WAP+switch is a comtrend AR-5387un and router1 is ZTE ZXHN 367A.
 
With reference to "Really need to see all the IPs for each interface and routing tables for each device to understand what's happening. ", 
```
ip addr show
``` displays the following for the computer's WLAN adapter and as you see there is no IPv4 address in this output:
 
```
3: wlx0013f7c99c1b: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
 link/ether 00:13:f7:c9:9c:1b brd ff:ff:ff:ff:ff:ff
 inet6 fe80::1992:30b1:3d92:5ff4/64 scope link noprefixroute 
valid_lft forever preferred_lft forever
 
```
 


and ```
route -n
``` displays the following empty routing table:
 
```
Tabla de rutas IP del núcleo
 Destino Pasarela Genmask Indic Métric Ref Uso Interfaz
```
 

To further understand what is happening I got the following as the output of the following command launched from the computer. It seems the computer is sending DHCP requests but there is NOT a reply.
 
```
sudo tcpdump -i wlx0013f7c99c1b -pvn port 67 and port 68
```
 
```
17:45:56.026061 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0xdc84ab73, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Request
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:45:59.588629 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0xdc84ab73, secs 3, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Request
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:46:02.469571 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0xdc84ab73, secs 6, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Request
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:46:10.352699 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0x310ac21a, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Discover
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:46:13.051128 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0x310ac21a, secs 3, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Discover
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:46:17.641265 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0x310ac21a, secs 7, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Discover
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
 17:46:24.513844 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:13:f7:c9:9c:1b, length 300, xid 0x310ac21a, secs 14, Flags [none]
 Client-Ethernet-Address 00:13:f7:c9:9c:1b
 Vendor-rfc1048 Extensions
 Magic Cookie 0x63825363
 DHCP-Message Option 53, length 1: Discover
 Requested-IP Option 50, length 4: 192.168.1.33
 Hostname Option 12, length 7: "Fujitsu"
 Parameter-Request Option 55, length 16: 
Subnet-Mask, BR, Time-Zone, Default-Gateway
 Domain-Name, Domain-Name-Server, Option 119, Hostname
 Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
 NTP, Classless-Static-Route-Microsoft, Static-Route, Option 252
```

---

### Post by TheFu on 2020-04-26
Please use "code tags", not "quote tags" when posting terminal output.  Unreadable output makes for misunderstandings and mistakes.

Also, I'd like to see the IPs for **every** interface and routes for each device.  That includes the routers.

The reason I wanted to be absolutely positive the WAN interface wasn't being used on router2, was to eliminate 1 issue.  The request for IPs and routes on each device will eliminate other issues. Computer, cell phone, both "routers." Please clearly label each.  One large code tag group would be good. Show the exact command run with all options.  We seem to use slightly different options, so using the manpage to try and understand them is necessary.

I'd prefer **ifconfig** output over **ip addr** - the **ip** commands make ugly output.  Sorta like how **route -n** and **ip route** - one is readable, the other not readable.

Please and thank you.

With this information, I can sketch a diagram, properly label stuff and see what jumps out as wrong.

---

