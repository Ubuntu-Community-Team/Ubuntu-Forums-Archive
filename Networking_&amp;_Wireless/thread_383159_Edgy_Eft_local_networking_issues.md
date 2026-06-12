---
title: "Edgy Eft local networking issues"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by LearnedHand on 2007-03-12
I'm having difficulty getting my Ubuntu 6.10 Edgy Eft machine to be able to see other machines on my local network (i.e. cannot ping other machines, cannot ssh, etc.). Also, other machines on the same network cannot see the Ubuntu machine.

My network comprises a linksys wireless router to which 2 apple laptops, 1 windows vista laptop, and a printer are connected. I have allocated static IPs to each of these machines. All of the machines, except for the ubuntu machine, are able to ping each other and use any network services hosted on any of the other machines. All of the machines, including the ubuntu machine, are able to connect to the internet.

The linksys router (192.168.1.1) connects to the internet via a SpeedStream DSL modem (192.168.0.1) provided to me by my ISP. Each of the machines has an IP address of the form 192.168.1.x. Each of the machines uses 192.168.1.1 as it's gateway address and all, except ubuntu, connect to the internet properly when using 192.168.1.1 as the  DNS server.  Ubuntu only connects to the internet if 192.168.0.1 is used as the DNS server and is not able to see or be seen by any of the other machines. Strangely enough, ubuntu can't even ping the router it's using to connect to the internet? Anybody know what the problem is?

I've connected machines to this network using a ton of different OSs, but I've never seen this behavior on anything else, which is why I'm thinking it's an OS issue. It might also be useful to know that I have a netgear wg311v3 wireless network card, and used ndiswrapper to make it work under Edgy Eft. 

Any help would be much appreciated.

---

### Post by siciliancasanova on 2007-03-12
Go to **System > Administration > Shared Folders**

Click on **General Properties** and change your workgroup

You can view other networks and so forth at **Places > Network Servers**

Also go to **System > Administration > Networking**

And click on the **General** tab and check the **Automatic Service Discovery** box

---

### Post by LearnedHand on 2007-03-12
Thanks for the help. Unfortunately, this doesn't seem to help. I still cannot ping the ubuntu box or login using ssh from the ubuntu machine to any of the macs or from any of the macs to the ubuntu machine (my main goal). I don't really have a "Workgroup" for these machines, they're all just connected to the same router and, usually, I'm able to use ssh to log into the different machines using the IP addressed that I assigned to it. In this case, ubuntu can't see anything, even the router it uses to connect to the internet! I think this is a configuration issue.

---

### Post by siciliancasanova on 2007-03-12
So for your output for:
```
iwconfig
```

It's showing nothing for the **Access Point** section of the output?

---

### Post by siciliancasanova on 2007-03-12
Also when you run ```
netstat
``` are there any flags showing up?

---

### Post by LearnedHand on 2007-03-12
iwconfig output
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:B0:DB:90   
          Bit Rate:11 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-78 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

netstat output
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.1.4:2402        ohiggins.ubuntu.com:www TIME_WAIT  
tcp        0      0 192.168.1.4:2845        py-in-f104.google.c:www ESTABLISHED
tcp        0      0 192.168.1.4:4776        ar-in-f99.google.co:www ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    4227     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    4411     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    9089     @/org/freedesktop/hal/udev_event
unix  9      [ ]         DGRAM                    8690     /dev/log
unix  3      [ ]         STREAM     CONNECTED     12321    
unix  3      [ ]         STREAM     CONNECTED     12320    
unix  3      [ ]         STREAM     CONNECTED     12318    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     12317    
unix  3      [ ]         STREAM     CONNECTED     12314    /tmp/orbit-jonathan/linc-124b-0-3514f92bb2a85
unix  3      [ ]         STREAM     CONNECTED     12313    
unix  3      [ ]         STREAM     CONNECTED     12312    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     12311    
unix  3      [ ]         STREAM     CONNECTED     12310    /tmp/orbit-jonathan/linc-124b-0-3514f92bb2a85
unix  3      [ ]         STREAM     CONNECTED     12309    
unix  3      [ ]         STREAM     CONNECTED     12306    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     12305    
unix  3      [ ]         STREAM     CONNECTED     12303    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     12302    
unix  3      [ ]         STREAM     CONNECTED     12298    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12297    
unix  3      [ ]         STREAM     CONNECTED     11973    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11972    
unix  3      [ ]         STREAM     CONNECTED     11971    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11970    
unix  3      [ ]         STREAM     CONNECTED     11969    /tmp/orbit-jonathan/linc-11f4-0-1bde891546783
unix  3      [ ]         STREAM     CONNECTED     11968    
unix  3      [ ]         STREAM     CONNECTED     11965    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11964    
unix  3      [ ]         STREAM     CONNECTED     11959    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11958    
unix  3      [ ]         STREAM     CONNECTED     11938    /tmp/orbit-jonathan/linc-11e5-0-1dbdc796bcca8
unix  3      [ ]         STREAM     CONNECTED     11937    
unix  3      [ ]         STREAM     CONNECTED     11934    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11933    
unix  3      [ ]         STREAM     CONNECTED     11921    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11920    
unix  3      [ ]         STREAM     CONNECTED     11911    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11910    
unix  3      [ ]         STREAM     CONNECTED     11909    /tmp/orbit-jonathan/linc-11e2-0-733b68a393d74
unix  3      [ ]         STREAM     CONNECTED     11908    
unix  3      [ ]         STREAM     CONNECTED     11905    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11904    
unix  3      [ ]         STREAM     CONNECTED     11900    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11899    
unix  3      [ ]         STREAM     CONNECTED     11889    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11888    
unix  3      [ ]         STREAM     CONNECTED     11885    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11884    
unix  3      [ ]         STREAM     CONNECTED     11879    /tmp/orbit-jonathan/linc-117b-0-47c01cd38fe6e
unix  3      [ ]         STREAM     CONNECTED     11878    
unix  3      [ ]         STREAM     CONNECTED     11877    /tmp/orbit-jonathan/linc-11c9-0-6c592582f77c
unix  3      [ ]         STREAM     CONNECTED     11876    
unix  3      [ ]         STREAM     CONNECTED     11867    /tmp/orbit-jonathan/linc-1192-0-4e8920ad17671
unix  3      [ ]         STREAM     CONNECTED     11866    
unix  3      [ ]         STREAM     CONNECTED     11865    /tmp/orbit-jonathan/linc-11bd-0-22271b324548e
unix  3      [ ]         STREAM     CONNECTED     11864    
unix  3      [ ]         STREAM     CONNECTED     11857    /tmp/orbit-jonathan/linc-11c2-0-10d220edb6bd3
unix  3      [ ]         STREAM     CONNECTED     11856    
unix  3      [ ]         STREAM     CONNECTED     11855    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11854    
unix  3      [ ]         STREAM     CONNECTED     11852    /tmp/orbit-jonathan/linc-11c9-0-6c592582f77c
unix  3      [ ]         STREAM     CONNECTED     11851    
unix  3      [ ]         STREAM     CONNECTED     11850    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11849    
unix  3      [ ]         STREAM     CONNECTED     11848    /tmp/orbit-jonathan/linc-11c9-0-6c592582f77c
unix  3      [ ]         STREAM     CONNECTED     11847    
unix  3      [ ]         STREAM     CONNECTED     11844    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11843    
unix  3      [ ]         STREAM     CONNECTED     11839    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11838    
unix  3      [ ]         STREAM     CONNECTED     11825    /tmp/orbit-jonathan/linc-11c2-0-10d220edb6bd3
unix  3      [ ]         STREAM     CONNECTED     11824    
unix  3      [ ]         STREAM     CONNECTED     11821    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11820    
unix  3      [ ]         STREAM     CONNECTED     11818    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11817    
unix  3      [ ]         STREAM     CONNECTED     11811    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11810    
unix  3      [ ]         STREAM     CONNECTED     11812    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11809    
unix  3      [ ]         STREAM     CONNECTED     11796    /tmp/orbit-jonathan/linc-11bd-0-22271b324548e
unix  3      [ ]         STREAM     CONNECTED     11795    
unix  3      [ ]         STREAM     CONNECTED     11794    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11793    
unix  3      [ ]         STREAM     CONNECTED     11790    /tmp/orbit-jonathan/linc-11bd-0-22271b324548e
unix  3      [ ]         STREAM     CONNECTED     11789    
unix  3      [ ]         STREAM     CONNECTED     11786    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11785    
unix  3      [ ]         STREAM     CONNECTED     11773    /tmp/orbit-jonathan/linc-1192-0-4e8920ad17671
unix  3      [ ]         STREAM     CONNECTED     11772    
unix  3      [ ]         STREAM     CONNECTED     11771    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11770    
unix  3      [ ]         STREAM     CONNECTED     11768    /tmp/mapping-jonathan
unix  3      [ ]         STREAM     CONNECTED     11761    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11760    
unix  3      [ ]         STREAM     CONNECTED     11756    
unix  3      [ ]         STREAM     CONNECTED     11752    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     11751    
unix  3      [ ]         STREAM     CONNECTED     11750    /tmp/orbit-jonathan/linc-119a-0-3ffc00e8a7756
unix  3      [ ]         STREAM     CONNECTED     11749    
unix  3      [ ]         STREAM     CONNECTED     11748    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11747    
unix  3      [ ]         STREAM     CONNECTED     11746    /tmp/orbit-jonathan/linc-119a-0-3ffc00e8a7756
unix  3      [ ]         STREAM     CONNECTED     11745    
unix  3      [ ]         STREAM     CONNECTED     11742    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11741    
unix  3      [ ]         STREAM     CONNECTED     11739    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11738    
unix  3      [ ]         STREAM     CONNECTED     11734    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11733    
unix  3      [ ]         STREAM     CONNECTED     11726    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11719    
unix  3      [ ]         STREAM     CONNECTED     11718    /tmp/orbit-jonathan/linc-117b-0-47c01cd38fe6e
unix  3      [ ]         STREAM     CONNECTED     11717    
unix  3      [ ]         STREAM     CONNECTED     11716    /tmp/orbit-jonathan/linc-11a9-0-3ffc00e82a426
unix  3      [ ]         STREAM     CONNECTED     11715    
unix  3      [ ]         STREAM     CONNECTED     11707    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11706    
unix  3      [ ]         STREAM     CONNECTED     11705    /tmp/orbit-jonathan/linc-11a9-0-3ffc00e82a426
unix  3      [ ]         STREAM     CONNECTED     11704    
unix  3      [ ]         STREAM     CONNECTED     11703    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11702    
unix  3      [ ]         STREAM     CONNECTED     11701    /tmp/orbit-jonathan/linc-11a9-0-3ffc00e82a426
unix  3      [ ]         STREAM     CONNECTED     11700    
unix  3      [ ]         STREAM     CONNECTED     11697    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11696    
unix  3      [ ]         STREAM     CONNECTED     11692    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11691    
unix  3      [ ]         STREAM     CONNECTED     11686    /tmp/orbit-jonathan/linc-1192-0-4e8920ad17671
unix  3      [ ]         STREAM     CONNECTED     11685    
unix  3      [ ]         STREAM     CONNECTED     11682    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11681    
unix  3      [ ]         STREAM     CONNECTED     11679    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11678    
unix  3      [ ]         STREAM     CONNECTED     11674    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11673    
unix  3      [ ]         STREAM     CONNECTED     11664    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11663    
unix  3      [ ]         STREAM     CONNECTED     11660    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11659    
unix  3      [ ]         STREAM     CONNECTED     11657    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11656    
unix  3      [ ]         STREAM     CONNECTED     11654    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11653    
unix  3      [ ]         STREAM     CONNECTED     11649    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11648    
unix  3      [ ]         STREAM     CONNECTED     11647    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11646    
unix  2      [ ]         DGRAM                    11645    
unix  3      [ ]         STREAM     CONNECTED     11644    /tmp/orbit-jonathan/linc-1194-0-183a40da4ec70
unix  3      [ ]         STREAM     CONNECTED     11643    
unix  3      [ ]         STREAM     CONNECTED     11640    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11639    
unix  3      [ ]         STREAM     CONNECTED     11636    /tmp/orbit-jonathan/linc-117d-0-47c01cd3aa4dc
unix  3      [ ]         STREAM     CONNECTED     11635    
unix  3      [ ]         STREAM     CONNECTED     11634    /tmp/orbit-jonathan/linc-117b-0-47c01cd38fe6e
unix  3      [ ]         STREAM     CONNECTED     11633    
unix  3      [ ]         STREAM     CONNECTED     11632    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11630    
unix  3      [ ]         STREAM     CONNECTED     11631    /tmp/orbit-jonathan/linc-1181-0-14db520a2f698
unix  3      [ ]         STREAM     CONNECTED     11629    
unix  3      [ ]         STREAM     CONNECTED     11637    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11623    
unix  3      [ ]         STREAM     CONNECTED     11619    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11618    
unix  3      [ ]         STREAM     CONNECTED     11613    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11612    
unix  3      [ ]         STREAM     CONNECTED     11609    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11608    
unix  3      [ ]         STREAM     CONNECTED     11607    /tmp/orbit-jonathan/linc-1190-0-3588a1f91dcd
unix  3      [ ]         STREAM     CONNECTED     11606    
unix  3      [ ]         STREAM     CONNECTED     11603    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11602    
unix  3      [ ]         STREAM     CONNECTED     11600    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11595    
unix  3      [ ]         STREAM     CONNECTED     11589    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11588    
unix  3      [ ]         STREAM     CONNECTED     11579    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11578    
unix  3      [ ]         STREAM     CONNECTED     11574    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11573    
unix  3      [ ]         STREAM     CONNECTED     11572    /tmp/orbit-jonathan/linc-117f-0-3588a1f82aca0
unix  3      [ ]         STREAM     CONNECTED     11571    
unix  3      [ ]         STREAM     CONNECTED     11568    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11567    
unix  3      [ ]         STREAM     CONNECTED     11565    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11564    
unix  3      [ ]         STREAM     CONNECTED     11560    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11559    
unix  3      [ ]         STREAM     CONNECTED     11553    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11552    
unix  3      [ ]         STREAM     CONNECTED     11551    /tmp/orbit-jonathan/linc-1185-0-6a530cfaf1382
unix  3      [ ]         STREAM     CONNECTED     11550    
unix  3      [ ]         STREAM     CONNECTED     11547    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11546    
unix  3      [ ]         STREAM     CONNECTED     11543    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11542    
unix  3      [ ]         STREAM     CONNECTED     11532    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11531    
unix  3      [ ]         STREAM     CONNECTED     11523    /tmp/orbit-jonathan/linc-117d-0-47c01cd3aa4dc
unix  3      [ ]         STREAM     CONNECTED     11522    
unix  3      [ ]         STREAM     CONNECTED     11519    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11518    
unix  3      [ ]         STREAM     CONNECTED     11516    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11515    
unix  3      [ ]         STREAM     CONNECTED     11506    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11505    
unix  3      [ ]         STREAM     CONNECTED     11502    /tmp/orbit-jonathan/linc-117b-0-47c01cd38fe6e
unix  3      [ ]         STREAM     CONNECTED     11501    
unix  3      [ ]         STREAM     CONNECTED     11498    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11497    
unix  3      [ ]         STREAM     CONNECTED     11495    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11490    
unix  3      [ ]         STREAM     CONNECTED     11484    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11483    
unix  3      [ ]         STREAM     CONNECTED     11473    /tmp/.ICE-unix/4402
unix  3      [ ]         STREAM     CONNECTED     11472    
unix  3      [ ]         STREAM     CONNECTED     11471    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11470    
unix  3      [ ]         STREAM     CONNECTED     11469    /tmp/orbit-jonathan/linc-1176-0-3ac8e831e7a49
unix  3      [ ]         STREAM     CONNECTED     11468    
unix  3      [ ]         STREAM     CONNECTED     11465    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11464    
unix  3      [ ]         STREAM     CONNECTED     11448    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11447    
unix  3      [ ]         STREAM     CONNECTED     11445    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     11444    
unix  2      [ ]         STREAM                   11441    
unix  3      [ ]         STREAM     CONNECTED     11408    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11407    
unix  3      [ ]         STREAM     CONNECTED     11400    /tmp/orbit-jonathan/linc-1161-0-23c867fc4853d
unix  3      [ ]         STREAM     CONNECTED     11399    
unix  3      [ ]         STREAM     CONNECTED     11396    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11395    
unix  3      [ ]         STREAM     CONNECTED     11391    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11390    
unix  3      [ ]         STREAM     CONNECTED     11377    @/tmp/dbus-NFX75ITu4n
unix  3      [ ]         STREAM     CONNECTED     11376    
unix  3      [ ]         STREAM     CONNECTED     11348    /tmp/orbit-jonathan/linc-1132-0-62c3f896461ee
unix  3      [ ]         STREAM     CONNECTED     11347    
unix  3      [ ]         STREAM     CONNECTED     11346    /tmp/orbit-jonathan/linc-115b-0-13b114042de7a
unix  3      [ ]         STREAM     CONNECTED     11161    
unix  2      [ ]         DGRAM                    11147    
unix  3      [ ]         STREAM     CONNECTED     11141    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11140    
unix  3      [ ]         STREAM     CONNECTED     11137    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11136    
unix  3      [ ]         STREAM     CONNECTED     11135    
unix  3      [ ]         STREAM     CONNECTED     11134    
unix  2      [ ]         DGRAM                    10891    
unix  3      [ ]         STREAM     CONNECTED     10890    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10889    
unix  2      [ ]         DGRAM                    10872    
unix  2      [ ]         DGRAM                    10843    
unix  3      [ ]         STREAM     CONNECTED     10597    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10596    
unix  3      [ ]         STREAM     CONNECTED     10589    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10588    
unix  3      [ ]         STREAM     CONNECTED     10568    @/tmp/hald-local/dbus-3vcNEOIjaX
unix  3      [ ]         STREAM     CONNECTED     10564    
unix  3      [ ]         STREAM     CONNECTED     10557    @/tmp/hald-local/dbus-3vcNEOIjaX
unix  3      [ ]         STREAM     CONNECTED     10553    
unix  3      [ ]         STREAM     CONNECTED     10506    @/tmp/hald-local/dbus-3vcNEOIjaX
unix  3      [ ]         STREAM     CONNECTED     10498    
unix  3      [ ]         STREAM     CONNECTED     10491    @/tmp/hald-local/dbus-3vcNEOIjaX
unix  3      [ ]         STREAM     CONNECTED     10483    
unix  3      [ ]         STREAM     CONNECTED     10444    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     10443    
unix  3      [ ]         STREAM     CONNECTED     10447    @/tmp/hald-local/dbus-3vcNEOIjaX
unix  3      [ ]         STREAM     CONNECTED     10438    
unix  3      [ ]         STREAM     CONNECTED     9084     @/tmp/hald-runner/dbus-eZvPnEZhtG
unix  3      [ ]         STREAM     CONNECTED     9083     
unix  3      [ ]         STREAM     CONNECTED     9065     
unix  3      [ ]         STREAM     CONNECTED     9064     
unix  2      [ ]         DGRAM                    8973     
unix  3      [ ]         STREAM     CONNECTED     8919     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     8918     
unix  5      [ ]         STREAM     CONNECTED     10452    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8904     
unix  2      [ ]         DGRAM                    8734     

```

Looks like no flags

Any ideas?

---

### Post by siciliancasanova on 2007-03-13
Well the netstat is showing that you have established pings with outside networks.  Also the iwconfig shows that your card is reading the correct access point, if it wasn't you wouldn't have wireless working at all.

Do you happen to have a firewall set up at all?  Like firestarter?  I know there is a setting in there that disables your machine from being seen on any networks.

---

### Post by LearnedHand on 2007-03-13
Other than using ndiswrapper to make the wireless NIC work, a few tinkerings to make my NVidia card work, and the installation of Blender, this is a plaint, default Ubuntu 6.10 Edgy Eft installation. I just installed this yesterday, so most everything is how it comes off the install.

Unless ubuntu has some default firewall installed and turned on, I don't have a software firewall on this.

---

### Post by siciliancasanova on 2007-03-13
Can you do anything in **System > Administration > Network Tools** ?  Does it even output anything in any of the tabs?  Including a traceroute of your router 198.162.0.1 ?  Basically it's not the information that's important, is it displaying any information?

---

### Post by LearnedHand on 2007-03-13
Devices:
lists stuff under IPv4 and IPV6

Ping:
I can ping 192.168.0.1 (the DSL modem)
I cannot ping 192.168.1.1 (the router)
This is very strange because the ubuntu machine is using ONLY a wireless connection. The only possible way it can get to the DSL modem is through that router, but it won't return pings. It says Destination Unreachable, even though the router responds to pings from the other machine
I can also ping internet sites (ubuntu.com google.com, etc.)

Netstat:
lists a bunch of info

Traceroute:
the path to 192.168.0.1 (the DSL) modem. It just lists the ubuntu machine's IP (192.168.1.4) and then the DSL modem (192.168.0.1). It also does the same when tracerouting to an outside address. It seems like it somehow goes directly to the DSL modem even though the DSL modem is physically connected only to the router.

Port Scan:
I can scan ports of the DSL modem, but nothing else

---

### Post by r.stiltskin on 2007-03-13
What output do you get from:
netstat -nr
arp
ifconfig

---

### Post by LearnedHand on 2007-03-13
netstat -nr

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.240 U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.240 U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

arp
```

Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.7                      (incomplete)                              eth0
192.168.1.1                      (incomplete)                              eth0
192.168.1.1              ether   00:0C:41:B0:DB:90   C                     wlan0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:11:95:1D:B4:1E  
          inet addr:192.168.1.4  Bcast:192.168.1.15  Mask:255.255.255.240
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84486 (82.5 KiB)  TX bytes:84486 (82.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:84:EB:A4  
          inet addr:192.168.1.4  Bcast:192.168.1.15  Mask:255.255.255.240
          inet6 addr: fe80::214:6cff:fe84:eba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8051473 (7.6 MiB)  TX bytes:1697008 (1.6 MiB)
          Interrupt:177 Memory:e8000000-e8010000 

```

Thanks so much for your help, i'm completely baffled by this problem

---

### Post by siciliancasanova on 2007-03-13
Well I hate to say that it's like your original post in that it might have had a bad installation but I wanted to run all this other stuff to make sure that it's all working.  I will admit that I have only been using linux for a week but I have a wireless desktop and had to go through all the steps to network with other computers to share files and set up remotely which I all did fine with wireless with ndiswrapper so we are looking at almost identical set ups in terms of the wireless to router connection and operating system.  The only network settings I changed were the ones I had listed for you to change above.  

As of now we can only hope that a guru gets on here and has seen this situation before or knows a link to someone who has.

---

### Post by LearnedHand on 2007-03-13
Thanks for your help, hopefully somebody will know what to do with this. The main reason I want to use ubuntu on this desktop machine is because i have all of these laptops with small hard drives and i want to be able to host files and such on it that I can get using simple unix tools. I feel like i'm really close, but I can't quite get a handle on this issue. At any rate, hopefully someone will come along with more info. Thanks!

---

### Post by r.stiltskin on 2007-03-13
You have your wireless card (wlan0) and your ethernet adapter (eth0) both configured statically with the same internet address 192.168.1.4.

I'm not positive, but I think that's a problem.  Give the ethernet adapter a different address (edit /etc/network/interfaces) and then restart networking (sudo /etc/init.d/networking restart) or reboot.

---

### Post by LearnedHand on 2007-03-13
yep, changing the wired NIC to a different IP made it all work right. Thanks!

---

### Post by siciliancasanova on 2007-03-13
Lol, I feel so non-helpful, but that's good information.  Thanks r.stiltskin.

---

### Post by r.stiltskin on 2007-03-13
It's nice to be able to help occasionally.    :)

---

