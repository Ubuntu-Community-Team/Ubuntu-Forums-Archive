---
title: "IPV6 Routing Error Wifi Connected but No Internet"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by kendrick on 2017-02-11
I can't figure out how to get wifi working again after a slightly botched upgrade from 14.04 to 16.04. Wifi is connecting but I cannot connect to the internet. It seems I have no default route set up but am not sure what to do next. Pretty sure our router is using ipv6. Thanks for the help can't wait to get my system going again.

wireless-info output:
[http://pastebin.ubuntu.com/23976681/](http://pastebin.ubuntu.com/23976681/)

---

### Post by The Cog on 2017-02-11
Can you please post the output from these three commands:
```
ifconfig
route
route -6
```

---

### Post by kendrick on 2017-02-11
```
ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1940907 (1.9 MB)  TX bytes:1940907 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 94:65:9c:fd:16:dc  
          inet6 addr: 2600:8804:5400:3300:9665:9cff:fefd:16dc/64 Scope:Global
          inet6 addr: fe80::9665:9cff:fefd:16dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2802648 (2.8 MB)  TX bytes:1801779 (1.8 MB)

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

route -6

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2600:8804:5400:3300:9665:9cff:fefd:16dc/128 ::                         Ue   256 0     0 wlan0
2600:8804:5400:3300::/64       ::                         U    600 0     0 wlan0
2600:8804:5400:3300::/56       fe80::6eb0:ceff:fecf:89f3  UG   600 0     0 wlan0
fe80::/64                      ::                         U    256 0     0 wlan0
::/0                           fe80::6eb0:ceff:fecf:89f3  UG   600 4   117 wlan0
::/0                           ::                         !n   -1  1 16654 lo
::1/128                        ::                         Un   0   4     8 lo
2600:8804:5400:3300:9665:9cff:fefd:16dc/128 ::                         Un   0   2    18 lo
fe80::9665:9cff:fefd:16dc/128  ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 4    77 wlan0
::/0                           ::                         !n   -1  1 16654 lo

```

---

### Post by The Cog on 2017-02-11
OK, you have no IPv4, but I think your IPv6 looks OK. 
Can you try these commands and post the results:
```
ping6 fe80::6eb0:ceff:fecf:89f3
ping6 2a00:1450:4009:801::200e
ping6 google.com
```

---

### Post by kendrick on 2017-02-11
```
ping6 fe80::6eb0:ceff:fecf:89f3
connect: Invalid argument

ping6 2a00:1450:4009:801::200e
PING 2a00:1450:4009:801::200e(2a00:1450:4009:801::200e) 56 data bytes

From 2600:8804:5400:3300:9665:9cff:fefd:16dc icmp_seq=1 Destination unreachable: Address unreachable
... continues like this until I put an end to it after 200 tries

ping6 google.com
unknown host

```

---

### Post by The Cog on 2017-02-11
I don't understand the problem with that first command. Can you try it again and then this command?
```
ip neighbor list
```

---

### Post by chili555 on 2017-02-11
When you click the Network Manager icon, select 'Edit Connections', then edit your connection DB590A, under IPv4 settings, what is the Method? DHCP, we hope??

If not, change it, reboot and show us again:```
ifconfig
```

This is very, very interesting:> WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b24cd416-6e7e-4303-9521-d5b133e10c7f | DB590A
IP6.ADDRESS[1]:                         2600:8804:5400:3300:<IP6 'wlan0' [IF1]>/64
IP6.ADDRESS[2]:                         fe80::<IP6 'wlan0' [IF1]>/64
IP6.GATEWAY:                            fe80::6eb0:ceff:fecf:89f3
IP6.ROUTE[1]:                           dst = 2600:8804:5400:3300::/56, nh = fe80::6eb0:ceff:fecf:89f3, mt = 600
IP6.ROUTE[2]:                           dst = 2600:8804:5400:3300::/64, nh = ::, mt = 600
IP6.DNS[1]:                             2001:578:3f::30
IP6.DNS[2]:                             2001:578:3f:1::30Notice that IPv4 is not mentioned. A more normal wireless_script reads more like this:> IP4.ADDRESS[1]:                         192.168.1.104/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
<snip>
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::abb4:3c6:d569:5c96/64
IP6.GATEWAY:                            I would also check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Your driver and old Chili hate hate hate TKIP.

---

### Post by kendrick on 2017-02-12
I'm not sure what the issue is with that ping command. I'm guessing ping doesn't like the :: format which I guess is short for :0000: if I try putting zeros in it says unknown host as well. I tried changing the router settings too to no avail. I'm not sure that that is the issue though because this same network was working in 14.04. I was able to manually set an IP for my device using the mac address in the DHCP settings. This solves my problem for now but I hope I don't have to connect to any IPV6 routers where I don't have access to the router settings. my wireless info script outputs this now. [https://paste.ubuntu.com/23985033/](https://paste.ubuntu.com/23985033/)

---

### Post by The Cog on 2017-02-12
The :: is short for one **or more** :0000: segments - enough to make up the correct length address. 
I tried that ping6 command on my laptp and got this result:
```
steve@StevesLappy:~$ ping6 fe80::6eb0:ceff:fecf:89f3
PING fe80::6eb0:ceff:fecf:89f3(fe80::6eb0:ceff:fecf:89f3) 56 data bytes
From fe80::5635:30ff:feb5:3479%wlo1 icmp_seq=1 Destination unreachable: Address unreachable

```
Address is of course unreachable because that device isn't on my network.
So I still don't understand the "connect" bit of the error message. Oh well.

---

### Post by chili555 on 2017-02-12
> I'm guessing ping doesn't like the :: format which I guess is short for :0000:It works just fine if the address is a valid reachable address that is set to return pings. For example:```
chili@T440p:~$ ping -c3 2620:0:861:ed1a::1
PING 2620:0:861:ed1a::1(2620:0:861:ed1a::1) 56 data bytes
64 bytes from 2620:0:861:ed1a::1: icmp_seq=1 ttl=51 time=29.8 ms
64 bytes from 2620:0:861:ed1a::1: icmp_seq=2 ttl=51 time=29.7 ms
64 bytes from 2620:0:861:ed1a::1: icmp_seq=3 ttl=51 time=30.1 ms

--- 2620:0:861:ed1a::1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 29.730/29.907/30.171/0.190 ms

```

---

