---
title: "One of two point-to-point interfaces in Ubuntu 16.04 on Jetson TX2 fails"
date: 2019-02-12
forum: Networking &amp; Wireless
---

### Post by mhoejgaard-lorenz on 2019-02-12
The setup consists of a NVIDIA Jetson TX2 and 2 SIM7100 modems, and the idea is to use both modems for different applications under normal use, and the working one for all communications should the other one fail. My issue is that the second ppp interface always fails. The issue occurs no matter in which order the modems are enabled. Additionally, if the first modem is disabled a general ping and a ping on ppp0 still succeeds indicating that modem2 is being used as a failover on ppp0 instead of using its own (at least I assume so) ppp1.

The modems are handled by ModemManager which recognizes them correctly:

```
nvidia@tegra-ubuntu:~$ mmcli -L


Found 2 modems:
    /org/freedesktop/ModemManager1/Modem/1 [SIMCOM INCORPORATED] SIMCOM_SIM7100E
    /org/freedesktop/ModemManager1/Modem/0 [SIMCOM INCORPORATED] SIMCOM_SIM7100E



```

```

nvidia@tegra-ubuntu:~$ mmcli -m 0

/org/freedesktop/ModemManager1/Modem/0 (device id '5e5e761b29adececc71ffd2a70550b534171a43d')
  -------------------------
  Hardware |   manufacturer: 'SIMCOM INCORPORATED'
           |          model: 'SIMCOM_SIM7100E'
           |       revision: '4534B06SIM7100E'
           |      supported: 'gsm-umts, lte'
           |        current: 'gsm-umts, lte'
           |   equipment id: '866802021319118'
  -------------------------
  System   |         device: '/sys/devices/3530000.xhci/usb1/1-3/1-3.2'
           |        drivers: 'option1'
           |         plugin: 'SimTech'
           |   primary port: 'ttyUSB7'
           |          ports: 'ttyUSB7 (at), ttyUSB4 (qcdm), ttyUSB6 (at)'
  -------------------------
  Numbers  |           own : 'unknown'
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'unknown'
           |          state: 'connected'
           |    power state: 'on'
           |    access tech: 'unknown'
           | signal quality: '58' (recent)
  -------------------------
  Modes    |      supported: 'allowed: 2g; preferred: none
           |                  allowed: 3g; preferred: none
           |                  allowed: 2g, 3g; preferred: none
           |                  allowed: 2g, 3g; preferred: 2g
           |                  allowed: 2g, 3g; preferred: 3g
           |                  allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  3GPP     |           imei: '866802021319118'
           |  enabled locks: 'none'
           |    operator id: '23801'
           |  operator name: 'TDC TDC'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'


  -------------------------

  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/0'

```

```

nvidia@tegra-ubuntu:~$ mmcli -m 1


/org/freedesktop/ModemManager1/Modem/1 (device id 'eb9bfab9555fa4f7bbbe4ceff48b1b50555f7dfe')
  -------------------------
  Hardware |   manufacturer: 'SIMCOM INCORPORATED'
           |          model: 'SIMCOM_SIM7100E'
           |       revision: '4534B06SIM7100E'
           |      supported: 'gsm-umts, lte'
           |        current: 'gsm-umts, lte'
           |   equipment id: '866802021319027'
  -------------------------
  System   |         device: '/sys/devices/3530000.xhci/usb1/1-3/1-3.1'
           |        drivers: 'option1'
           |         plugin: 'SimTech'
           |   primary port: 'ttyUSB11'
           |          ports: 'ttyUSB11 (at), ttyUSB9 (qcdm), ttyUSB12 (at)'
  -------------------------
  Numbers  |           own : 'unknown'
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'unknown'
           |          state: 'connected'
           |    power state: 'on'
           |    access tech: 'unknown'
           | signal quality: '64' (recent)
  -------------------------
  Modes    |      supported: 'allowed: 2g; preferred: none
           |                  allowed: 3g; preferred: none
           |                  allowed: 2g, 3g; preferred: none
           |                  allowed: 2g, 3g; preferred: 2g
           |                  allowed: 2g, 3g; preferred: 3g
           |                  allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  3GPP     |           imei: '866802021319027'
           |  enabled locks: 'none'
           |    operator id: '23801'
           |  operator name: 'TDC TDC'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/1'


  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/1'


```

The connections are setup up with NetworkManager:

```

nvidia@tegra-ubuntu:~$ nmcli con show 4G1 
[connection.id]("http://connection.id"):                          4G1
connection.uuid:                        3014fcaa-5dff-4966-a900-ebfef6f8f9b9
connection.interface-name:              --
connection.type:                        gsm
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.timestamp:                   1549959479
connection.read-only:                   no
connection.permissions:                 
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
ipv4.method:                            auto
ipv4.dns:                               
ipv4.dns-search:                        
ipv4.dns-options:                       (default)
ipv4.dns-priority:                      0
ipv4.addresses:                         
ipv4.gateway:                           --
ipv4.routes:                            
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
ipv6.method:                            auto
ipv6.dns:                               
ipv6.dns-search:                        
ipv6.dns-options:                       (default)
ipv6.dns-priority:                      0
ipv6.addresses:                         
ipv6.gateway:                           --
ipv6.routes:                            
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       -1 (unknown)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
gsm.number:                             *99#
gsm.username:                           --
gsm.password:                           <hidden>
gsm.password-flags:                     0 (none)
gsm.apn:                                internet
gsm.network-id:                         --
gsm.pin:                                <hidden>
gsm.pin-flags:                          0 (none)
gsm.home-only:                          no
gsm.device-id:                          5e5e761b29adececc71ffd2a70550b534171a43d
gsm.sim-id:                             --
gsm.sim-operator-id:                    --
[GENERAL.NAME]("http://GENERAL.NAME"):                           4G1
GENERAL.UUID:                           3014fcaa-5dff-4966-a900-ebfef6f8f9b9
GENERAL.DEVICES:                        ttyUSB7
GENERAL.STATE:                          activated
GENERAL.DEFAULT:                        yes
GENERAL.DEFAULT6:                       no
GENERAL.VPN:                            no
GENERAL.ZONE:                           --
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/1
GENERAL.SPEC-OBJECT:                    /
GENERAL.MASTER-PATH:                    --
IP4.ADDRESS[1]:                         [10.7.38.222/32]("http://10.7.38.222/32")
IP4.GATEWAY:                            0.0.0.0
IP4.ROUTE[1]:                           dst = [169.254.0.0/16]("http://169.254.0.0/16"), nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             194.239.134.83
IP4.DNS[2]:                             193.162.153.164


```

```

nvidia@tegra-ubuntu:~$ nmcli con show 4G2
[connection.id]("http://connection.id"):                          4G2
connection.uuid:                        c62f2714-4d6a-4425-a51b-8b54c70901fc
connection.interface-name:              --
connection.type:                        gsm
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.timestamp:                   1549959742
connection.read-only:                   no
connection.permissions:                 
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:                 
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
ipv4.method:                            auto
ipv4.dns:                               
ipv4.dns-search:                        
ipv4.dns-options:                       (default)
ipv4.dns-priority:                      0
ipv4.addresses:                         
ipv4.gateway:                           --
ipv4.routes:                            
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
ipv6.method:                            auto
ipv6.dns:                               
ipv6.dns-search:                        
ipv6.dns-options:                       (default)
ipv6.dns-priority:                      0
ipv6.addresses:                         
ipv6.gateway:                           --
ipv6.routes:                            
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       -1 (unknown)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
gsm.number:                             *99#
gsm.username:                           --
gsm.password:                           <hidden>
gsm.password-flags:                     0 (none)
gsm.apn:                                internet
gsm.network-id:                         --
gsm.pin:                                <hidden>
gsm.pin-flags:                          0 (none)
gsm.home-only:                          no
gsm.device-id:                          eb9bfab9555fa4f7bbbe4ceff48b1b50555f7dfe
gsm.sim-id:                             --
gsm.sim-operator-id:                    --
[GENERAL.NAME]("http://GENERAL.NAME"):                           4G2
GENERAL.UUID:                           c62f2714-4d6a-4425-a51b-8b54c70901fc
GENERAL.DEVICES:                        ttyUSB11
GENERAL.STATE:                          activated
GENERAL.DEFAULT:                        no
GENERAL.DEFAULT6:                       no
GENERAL.VPN:                            no
GENERAL.ZONE:                           --
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/0
GENERAL.SPEC-OBJECT:                    /
GENERAL.MASTER-PATH:                    --
IP4.ADDRESS[1]:                         [10.37.221.119/32]("http://10.37.221.119/32")
IP4.GATEWAY:                            0.0.0.0
IP4.DNS[1]:                             194.239.134.83
IP4.DNS[2]:                             193.162.153.164


```

When the modems are enabled by a pulse on their power pin, they boot in 20 seconds or so, are recognized by ModemManager, and the interfaces ppp0 and ppp1 appears (or are brought up).

A general ping of google.com shows network connection:

```

nvidia@tegra-ubuntu:~$ ping -c 5 [google.com]("http://google.com")
PING [google.com]("http://google.com") (172.217.20.46) 56(84) bytes of data.
64 bytes from [arn11s01-in-f14.1e100.net]("http://arn11s01-in-f14.1e100.net") (172.217.20.46): icmp_seq=1 ttl=55 time=29.8 ms
64 bytes from [arn11s01-in-f14.1e100.net]("http://arn11s01-in-f14.1e100.net") (172.217.20.46): icmp_seq=2 ttl=55 time=79.0 ms
64 bytes from [arn11s01-in-f14.1e100.net]("http://arn11s01-in-f14.1e100.net") (172.217.20.46): icmp_seq=3 ttl=55 time=72.9 ms
64 bytes from [arn11s01-in-f14.1e100.net]("http://arn11s01-in-f14.1e100.net") (172.217.20.46): icmp_seq=4 ttl=55 time=78.4 ms
64 bytes from [arn11s01-in-f14.1e100.net]("http://arn11s01-in-f14.1e100.net") (172.217.20.46): icmp_seq=5 ttl=55 time=68.9 ms


--- [google.com]("http://google.com") ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 29.879/65.850/79.048/18.364 ms



```

A ping on ppp0 shows network connection as well:

```

nvidia@tegra-ubuntu:~$ ping -c 5 -I ppp0 [google.com]("http://google.com")
PING [google.com]("http://google.com") (172.217.20.46) from 10.7.38.222 ppp0: 56(84) bytes of data.
64 bytes from [par10s09-in-f46.1e100.net]("http://par10s09-in-f46.1e100.net") (172.217.20.46): icmp_seq=1 ttl=55 time=28.5 ms
64 bytes from [par10s09-in-f46.1e100.net]("http://par10s09-in-f46.1e100.net") (172.217.20.46): icmp_seq=2 ttl=55 time=82.0 ms
64 bytes from [par10s09-in-f46.1e100.net]("http://par10s09-in-f46.1e100.net") (172.217.20.46): icmp_seq=3 ttl=55 time=81.8 ms
64 bytes from [par10s09-in-f46.1e100.net]("http://par10s09-in-f46.1e100.net") (172.217.20.46): icmp_seq=4 ttl=55 time=104 ms
64 bytes from [par10s09-in-f46.1e100.net]("http://par10s09-in-f46.1e100.net") (172.217.20.46): icmp_seq=5 ttl=55 time=78.1 ms


--- [google.com]("http://google.com") ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 28.584/75.048/104.623/25.054 ms


```

Pinging on ppp1 fails:

```

ping -c 5 -I ppp1 [google.com]("http://google.com")
PING [google.com]("http://google.com") (172.217.20.46) from 10.37.221.119 ppp1: 56(84) bytes of data.


--- [google.com]("http://google.com") ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```

Inspecting the interfaces reveals that both have IPs but also that they have p-t-p 0.0.0.0:

```

nvidia@tegra-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4b:c6:14:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:347675 (347.6 KB)  TX bytes:347675 (347.6 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.7.38.222  P-t-P:0.0.0.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:12567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14646953 (14.6 MB)  TX bytes:1006843 (1.0 MB)


ppp1      Link encap:Point-to-Point Protocol  
          inet addr:10.37.221.119  P-t-P:0.0.0.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4452 (4.4 KB)  TX bytes:5137 (5.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:04:4b:c6:14:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

I assume that the routing table could be of interest:

```

nvidia@tegra-ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     700    0        0 ppp0
default         *               0.0.0.0         U     701    0        0 ppp1
link-local      *               255.255.0.0     U     1000   0        0 ppp0


```

Any help or pointers to solutions or resources to resolve the matter of getting ppp1 to work as expected are highly appreciated.

---

