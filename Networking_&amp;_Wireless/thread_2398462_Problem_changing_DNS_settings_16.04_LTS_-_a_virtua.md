---
title: "Problem changing DNS settings 16.04 LTS - a virtual bridge seems to be in the middle?"
date: 2018-08-12
forum: Networking &amp; Wireless
---

### Post by bvargo on 2018-08-12
I'm not even sure where to begin here.  I want my primary DNS server to be 1.0.0.1 and the secondary to be 156.154.71.22.

For some reason, enp6s0 is not showing up and I'm on virbr0:

```

$ ifconfig
enp6s0    Link encap:Ethernet  HWaddr 90:2b:34:5a:bc:0d  
          inet addr:192.168.1.2  Bcast:192.168.1.225  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe5a:bc0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28371032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20426509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22946331550 (22.9 GB)  TX bytes:9085309809 (9.0 GB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:50534319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50534319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:26122627110 (26.1 GB)  TX bytes:26122627110 (26.1 GB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:14393949 (14.3 MB)


virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ sudo nmcli connection show 
NAME                UUID                                  TYPE             DEVICE 
tun0                3872b322-d641-45bc-a6bc-7688c6290f7a  tun              tun0   
virbr0              7815a192-cf52-4b69-afb6-254b7f2c0386  bridge           virbr0 
Wi-Fi connection 1  ceb40bc1-a313-495b-9cb4-6a42d8cf8530  802-11-wireless  --     
nicaragua     aff49d90-55f1-4a3d-9a1a-a4a5e194aa49  802-11-wireless  --     

$ sudo nmcli connection show virbr0 
connection.id:                          virbr0
connection.uuid:                        7815a192-cf52-4b69-afb6-254b7f2c0386
connection.interface-name:              virbr0
connection.type:                        bridge
connection.autoconnect:                 no
connection.autoconnect-priority:        0
connection.timestamp:                   1534105714
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
ipv4.method:                            manual
ipv4.dns:                               1.0.0.1
ipv4.dns-search:                        
ipv4.dns-options:                       (default)
ipv4.dns-priority:                      0
ipv4.addresses:                         192.168.122.1/24
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
ipv6.method:                            ignore
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
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
bridge.mac-address:                     --
bridge.stp:                             yes
bridge.priority:                        32768
bridge.forward-delay:                   2
bridge.hello-time:                      2
bridge.max-age:                         20
bridge.ageing-time:                     300
bridge.multicast-snooping:              yes
GENERAL.NAME:                           virbr0
GENERAL.UUID:                           7815a192-cf52-4b69-afb6-254b7f2c0386
GENERAL.DEVICES:                        virbr0
GENERAL.STATE:                          activated
GENERAL.DEFAULT:                        no
GENERAL.DEFAULT6:                       no
GENERAL.VPN:                            no
GENERAL.ZONE:                           --
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/2
GENERAL.SPEC-OBJECT:                    /
GENERAL.MASTER-PATH:                    --
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP4.DNS[1]:                             8.8.8.8
IP6.GATEWAY:                            

```

---

### Post by bvargo on 2018-08-12
I should mention that I do no have any wireless devices on this machine but that I was using a USB 802.11 b/g/n adapter (could never get it working with linux) and that ndiswrapper is on this machine.

I should also mention that I have Oracle VM Virtual Boxes and have used rdp/remmina to access them remotely (i.e. from another computer w/in the network).  The VMs are Windows 10 and Peppermint 9.  

The ISP-supplied primary DNS is 75.75.75.75 (Comcast) and that is not pushing to (at least) this machine.

[B]Question 1:  Why am I on a bridge?

Question 2:  Do I need to be on this bridge?

Question 3:  if yes to 2, how do I modify the DNS setting?

[/B]

---

### Post by bvargo on 2018-08-14
bump...

---

