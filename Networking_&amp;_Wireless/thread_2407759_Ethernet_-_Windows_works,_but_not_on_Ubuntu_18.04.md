---
title: "Ethernet - Windows works, but not on Ubuntu 18.04"
date: 2018-12-08
forum: Networking &amp; Wireless
---

### Post by durai23 on 2018-12-08
Hello,


On my Ubuntu 18.04 laptop the ethernet doesn't work at **my home network** (also wifi, hotspot, and usb tethering also don't work). But my **Windows laptop works** at my home network. **Also the Ethernet works on my Ubuntu 18.04 laptop when I have it at my work network.**


On my router's admin portal it says that my Ubuntu 18.04 laptop is connected successfully (through Ethernet or wifi). When I try to load a page on the browser it doesn't load immediately and loads after 5-10 minutes but extremely slowly. Sometimes it times out.


The Ethernet icon at top right appears normal. These are the Ethernet settings -


Ipv4 Address : <hidden>
Ipv6 Address : <hidden>
Hardware Address : <hidden>
Defualt route: 192.168.2.1
DNS :           192.168.2.1


MTU : automatic


IPv4 : all settings automatic
IPv6 : all settings automatic


Following are ouputs from common diagnostic commands.


```
lspci
#########################################
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics P530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.1 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #13 (rev f1)
00:1d.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
04:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0115 (rev 01)
06:00.0 PCI bridge: Intel Corporation DSL6340 Thunderbolt 3 Bridge [Alpine Ridge 2C 2015]
07:00.0 PCI bridge: Intel Corporation DSL6340 Thunderbolt 3 Bridge [Alpine Ridge 2C 2015]
07:01.0 PCI bridge: Intel Corporation DSL6340 Thunderbolt 3 Bridge [Alpine Ridge 2C 2015]
07:02.0 PCI bridge: Intel Corporation DSL6340 Thunderbolt 3 Bridge [Alpine Ridge 2C 2015]
3e:00.0 USB controller: Intel Corporation DSL6340 USB 3.1 Controller [Alpine Ridge]


rfkill
#############################################
ID TYPE      DEVICE            SOFT      HARD
 1 wlan      dell-wifi      blocked unblocked
 2 bluetooth dell-bluetooth blocked unblocked
 3 wlan      phy0           blocked unblocked


cat /etc/network/interfaces
#########################################
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


ifconfig
########################################
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:4b:96:1e:b5  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enxd481d72f6de3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.106  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 2003:e3:bf1:fe3f:c4d0:c2ce:83de:6cff  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::6c7b:cb8d:a686:813b  prefixlen 64  scopeid 0x20<link>
        inet6 2003:e3:bf1:fe3f:3cf5:137d:588e:7f14  prefixlen 64  scopeid 0x0<global>
        ether d4:81:d7:2f:6d:e3  txqueuelen 1000  (Ethernet)
        RX packets 24381  bytes 25698606 (25.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11939  bytes 1708630 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6442  bytes 414119 (414.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6442  bytes 414119 (414.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


iwconfig
#########################################
wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


cat /etc/resolv.conf 
(this is a symlinked file to /run/systemd/resolve/stub-resolv.conf)
########################################
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
search speedport.ip


nmcli device show
###################################          
GENERAL.DEVICE:                         enxd481d72f6de3
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         D4:81:D7:2F:6D:E3
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     wired_sandkaulbach
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.2.106/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.2.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.2.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
IP4.DOMAIN[1]:                          speedport.ip
IP6.ADDRESS[1]:                         2003:e3:bf1:fe3f:c4d0:c2ce:83de:6cff/64
IP6.ADDRESS[2]:                         2003:e3:bf1:fe3f:3cf5:137d:588e:7f14/64
IP6.ADDRESS[3]:                         fe80::6c7b:cb8d:a686:813b/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = 2003:e3:bf1:fe3f::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::1, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.HWADDR:                         02:42:4B:96:1E:B5
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     docker0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.17.0.0/16, nh = 0.0.0.0, mt = 0
IP6.GATEWAY:                            --


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.HWADDR:                         14:AB:C5:D0:E8:E1
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --


GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            --


iptables
############################################
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy DROP)
target     prot opt source               destination         
DOCKER-USER  all  --  anywhere             anywhere            
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain DOCKER (1 references)
target     prot opt source               destination         


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination         
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            


Chain DOCKER-ISOLATION-STAGE-2 (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            


Chain DOCKER-USER (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


nslookup www.google.com
############################################
Server:        127.0.0.53
Address:    127.0.0.53#53


Non-authoritative answer:
Name:    www.google.com
Address: 216.58.212.228
Name:    www.google.com
Address: 2a00:1450:400e:803::2004


ping www.google.com
#########################################


ping www.google.com
PING www.google.com(ams16s29-in-x04.1e100.net (2a00:1450:400e:804::2004)) 56 data bytes
64 bytes from ams16s29-in-x04.1e100.net (2a00:1450:400e:804::2004): icmp_seq=1 ttl=57 time=17.0 ms
64 bytes from ams16s29-in-x04.1e100.net (2a00:1450:400e:804::2004): icmp_seq=2 ttl=57 time=17.7 ms
64 bytes from ams16s29-in-x04.1e100.net (2a00:1450:400e:804::2004): icmp_seq=3 ttl=57 time=17.8 ms
64 bytes from ams16s29-in-x04.1e100.net (2a00:1450:400e:804::2004): icmp_seq=4 ttl=57 time=16.9 ms
ping gooogle dns#######################################
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=124 time=10.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=124 time=10.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=124 time=9.73 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=124 time=9.85 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=124 time=10.1 ms
wget google#######################################
--2018-12-09 01:39:17--  http://www.google.com/
Resolving www.google.com (www.google.com)... 2a00:1450:400e:804::2004, 172.217.17.36
Connecting to www.google.com (www.google.com)|2a00:1450:400e:804::2004|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;index.html.3&#8217;


index.html.3                                           [ <=>                                                                                                             ]  10,84K  --.-KB/s    in 0,003s  


2018-12-09 01:39:17 (3,20 MB/s) - &#8216;index.html.3&#8217; saved [11097]


dig www.google.com
#########################################




; <<>> DiG 9.11.3-1ubuntu1.2-Ubuntu <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23981
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.google.com.            IN    A


;; ANSWER SECTION:
www.google.com.        0    IN    A    216.58.212.228


;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Sun Dec 09 01:40:40 CET 2018
;; MSG SIZE  rcvd: 59


netstat -nr
#############################################
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 enxd481d72f6de3
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 enxd481d72f6de3
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 enxd481d72f6de3


route -n
#################################################
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 enxd481d72f6de3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxd481d72f6de3
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enxd481d72f6de3


sudo tracepath www.google.com
(FAILED - stopped wtih Ctrl-C)
#####################################
 1?: [LOCALHOST]                        0.036ms pmtu 1492
 1:  p200300E30BF1FE3FBE30D9FFFE857D72.dip0.t-ipconnect.de   1.101ms 
 1:  p200300E30BF1FE3FBE30D9FFFE857D72.dip0.t-ipconnect.de   1.027ms 
 2:  ^C

``` 


Please let me know if you need more information.

---

### Post by him610 on 2018-12-08
This is just a guess, but you are showing:
```
IP4.DNS[1]:     192.168.2.1
```
That's the same address as your ```
IP4.GATEWAY:      192.168.2.1
```
Not saying that is wrong, but I think most folks use an external DNS, for instance 8.8.8.8

---

### Post by an3as on 2018-12-09
in my case (18.04) I have resolved with this video instructions

[https://www.youtube.com/watch?v=wjS4eBnR3q0](https://www.youtube.com/watch?v=wjS4eBnR3q0)

[COLOR=#000080][SIZE=2][FONT=arial]cd /etc[/FONT][/SIZE][/COLOR]
[COLOR=#000080][SIZE=2][FONT=arial]ls[/FONT][/SIZE][/COLOR]
[COLOR=#000080][SIZE=2][FONT=arial]sudo nanoresolv.conf[/FONT][/SIZE][/COLOR]
[COLOR=#000080][SIZE=2][FONT=arial]--------rootpassword[/FONT][/SIZE][/COLOR]

[COLOR=#000080][SIZE=2][FONT=arial]nameserver 8.8.8.8  [/FONT][/SIZE][/COLOR]
[COLOR=#000080][SIZE=2][FONT=arial]nameserver 8.8.4.4[/FONT][/SIZE][/COLOR]

[COLOR=#000080][SIZE=2][FONT=arial]---------ctl+x[/FONT][/SIZE][/COLOR]

but unfortunately every time that I make a reboot , I have to repeat all.
any suggestion to do this solution permanently?

---

### Post by The Cog on 2018-12-09
I assume you actually edited /etc/resolv.conf. Notice that /etc/resolv.conf is a symbolic link to the file that gets re-written on every boot:
```
ls -l /etc/resolv.conf
```
You could delete that symlink and replace it with your own text file:
```
sudo mv /etc/resolv.conf /etc/resolv.conf.original
sudo nano /etc/resolv.conf
```

---

