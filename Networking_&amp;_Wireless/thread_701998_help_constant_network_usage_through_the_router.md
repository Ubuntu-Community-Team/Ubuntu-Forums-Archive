---
title: "help: constant network usage through the router"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by chene on 2008-02-19
greetings,

I think I may have a security breach on my ubuntu (AMD_74, 7.10) system.  Since last week, I have noticed a constant network on my computer, even when the computer is just booted.  I'm not running any IM (e.g. pidgin) nor any P2P programs (e.g. torrent), but there is always a constant network usage of >20% (according to network applet). 

I've then double-checked my router:  indeed, these network activities went through the router as the light indicators of both the LAN (connected to PC) and WAN (DSL modem) are flashing synchronized. 


a clip of "netstat -ac" gives output of the following.  I would appreciate if anyone can take a look and tell me if anything looks suspicious:  (thank you)

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      1 192.168.1.217:33708     12.120.1.254:www        FIN_WAIT1  
tcp6       0      0 *:ssh                   *:*                     LISTEN     
udp        0      0 *:32769                 *:*                                
udp        0      0 192.168.1.21:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.2:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 192.168.1.217:ntp       *:*                                
udp        0      0 localhost:ntp           *:*                                
udp        0      0 *:ntp                   *:*                                
udp6       0      0 fe80::217:31ff:fe56:ntp *:*                                
udp6       0      0 ip6-localhost:ntp       *:*                                
udp6       0      0 *:ntp                   *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     19068    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16898    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     19464    /tmp/keyring-YUziU2/socket
unix  2      [ ACC ]     STREAM     LISTENING     17158    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     19546    /tmp/ssh-tXuQwp6345/agent.6345
unix  2      [ ACC ]     STREAM     LISTENING     19562    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  2      [ ACC ]     STREAM     LISTENING     21734    /tmp/mapping-chene
unix  2      [ ACC ]     STREAM     LISTENING     19572    /tmp/orbit-chene/linc-18c9-0-45e967f730b88
unix  2      [ ACC ]     STREAM     LISTENING     19848    /tmp/.ICE-unix/6345
unix  2      [ ACC ]     STREAM     LISTENING     19882    /tmp/orbit-chene/linc-18f6-0-41a7df77968b7
unix  2      [ ACC ]     STREAM     LISTENING     19994    /tmp/orbit-chene/linc-1901-0-3419be593d893
unix  2      [ ACC ]     STREAM     LISTENING     20017    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  2      [ ACC ]     STREAM     LISTENING     20047    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  2      [ ACC ]     STREAM     LISTENING     20061    /tmp/orbit-chene/linc-18fc-0-64e94a3ee2636
unix  2      [ ACC ]     STREAM     LISTENING     20083    /tmp/orbit-chene/linc-190c-0-7899827047b65
unix  2      [ ACC ]     STREAM     LISTENING     20123    /tmp/orbit-chene/linc-190e-0-17a29b62b232d
unix  2      [ ACC ]     STREAM     LISTENING     20235    /tmp/orbit-chene/linc-191f-0-48ca4364e8378
unix  2      [ ACC ]     STREAM     LISTENING     18975    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     20246    /tmp/orbit-chene/linc-190d-0-6642496978091
unix  2      [ ACC ]     STREAM     LISTENING     20253    /tmp/orbit-chene/linc-1914-0-664249697baac
unix  2      [ ACC ]     STREAM     LISTENING     20273    /tmp/orbit-chene/linc-191a-0-39cf5527cbbae
unix  2      [ ACC ]     STREAM     LISTENING     20311    /tmp/orbit-chene/linc-192b-0-3f8815f259311
unix  2      [ ACC ]     STREAM     LISTENING     20469    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  2      [ ACC ]     STREAM     LISTENING     17235    @/var/run/hald/dbus-nMDK0pHEFF
unix  2      [ ACC ]     STREAM     LISTENING     20473    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  2      [ ACC ]     STREAM     LISTENING     20537    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  2      [ ACC ]     STREAM     LISTENING     21724    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  2      [ ACC ]     STREAM     LISTENING     21750    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  2      [ ACC ]     STREAM     LISTENING     21847    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  2      [ ACC ]     STREAM     LISTENING     21866    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  2      [ ACC ]     STREAM     LISTENING     21889    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  2      [ ACC ]     STREAM     LISTENING     21919    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  2      [ ACC ]     STREAM     LISTENING     21959    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  2      [ ACC ]     STREAM     LISTENING     22020    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  2      [ ACC ]     STREAM     LISTENING     22086    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  2      [ ACC ]     STREAM     LISTENING     22572    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  2      [ ACC ]     STREAM     LISTENING     489059   /tmp/orbit-chene/linc-1df2-0-61dbe97f8d91c
unix  2      [ ]         DGRAM                    8894     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     487489   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     18755    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     18840    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17218    @/tmp/dbus-c9nZcOmt9x
unix  2      [ ]         DGRAM                    9114     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     18828    @/var/run/dbus-35xWvYdQXg
unix  2      [ ACC ]     STREAM     LISTENING     18826    /var/run/sdp
unix  2      [ ]         DGRAM                    17246    @/org/freedesktop/hal/udev_event
unix  11     [ ]         DGRAM                    17065    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     19862    @/tmp/dbus-gSfQ2MLoyZ
unix  2      [ ACC ]     STREAM     LISTENING     17238    @/var/run/hald/dbus-dltQLXAU2W
unix  3      [ ]         STREAM     CONNECTED     489064   @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     489063   
unix  3      [ ]         STREAM     CONNECTED     489062   /tmp/orbit-chene/linc-1df2-0-61dbe97f8d91c
unix  3      [ ]         STREAM     CONNECTED     489061   
unix  3      [ ]         STREAM     CONNECTED     489058   /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     489057   
unix  3      [ ]         STREAM     CONNECTED     489049   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     489048   
unix  3      [ ]         STREAM     CONNECTED     487480   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     487479   
unix  3      [ ]         STREAM     CONNECTED     22594    
unix  3      [ ]         STREAM     CONNECTED     22593    
unix  3      [ ]         STREAM     CONNECTED     22579    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  3      [ ]         STREAM     CONNECTED     22578    
unix  3      [ ]         STREAM     CONNECTED     22577    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22576    
unix  3      [ ]         STREAM     CONNECTED     22575    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  3      [ ]         STREAM     CONNECTED     22574    
unix  3      [ ]         STREAM     CONNECTED     22571    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22570    
unix  3      [ ]         STREAM     CONNECTED     22568    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22567    
unix  3      [ ]         STREAM     CONNECTED     22563    /tmp/.X11-unix/X0
unix  4      [ ]         STREAM     CONNECTED     22562    
unix  3      [ ]         STREAM     CONNECTED     22132    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     22131    
unix  3      [ ]         STREAM     CONNECTED     22121    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     22120    
unix  3      [ ]         STREAM     CONNECTED     22115    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22114    
unix  3      [ ]         STREAM     CONNECTED     22105    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22104    
unix  3      [ ]         STREAM     CONNECTED     22103    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22102    
unix  3      [ ]         STREAM     CONNECTED     22101    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22100    
unix  3      [ ]         STREAM     CONNECTED     22093    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22092    
unix  3      [ ]         STREAM     CONNECTED     22091    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22090    
unix  3      [ ]         STREAM     CONNECTED     22089    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22088    
unix  3      [ ]         STREAM     CONNECTED     22085    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22084    
unix  3      [ ]         STREAM     CONNECTED     22080    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22079    
unix  3      [ ]         STREAM     CONNECTED     22060    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22059    
unix  3      [ ]         STREAM     CONNECTED     22058    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     22057    
unix  3      [ ]         STREAM     CONNECTED     22044    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22043    
unix  3      [ ]         STREAM     CONNECTED     22042    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22041    
unix  3      [ ]         STREAM     CONNECTED     22034    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22033    
unix  3      [ ]         STREAM     CONNECTED     22032    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22031    
unix  3      [ ]         STREAM     CONNECTED     22029    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22028    
unix  3      [ ]         STREAM     CONNECTED     22023    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22022    
unix  3      [ ]         STREAM     CONNECTED     22019    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22018    
unix  3      [ ]         STREAM     CONNECTED     21976    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21975    
unix  3      [ ]         STREAM     CONNECTED     21974    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21973    
unix  3      [ ]         STREAM     CONNECTED     21966    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21965    
unix  3      [ ]         STREAM     CONNECTED     21964    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21963    
unix  3      [ ]         STREAM     CONNECTED     21962    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21961    
unix  3      [ ]         STREAM     CONNECTED     21958    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21957    
unix  3      [ ]         STREAM     CONNECTED     21953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21952    
unix  3      [ ]         STREAM     CONNECTED     21949    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21948    
unix  3      [ ]         STREAM     CONNECTED     21947    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21946    
unix  3      [ ]         STREAM     CONNECTED     21938    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21937    
unix  3      [ ]         STREAM     CONNECTED     21936    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21935    
unix  3      [ ]         STREAM     CONNECTED     21926    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21925    
unix  3      [ ]         STREAM     CONNECTED     21924    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21923    
unix  3      [ ]         STREAM     CONNECTED     21922    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21921    
unix  3      [ ]         STREAM     CONNECTED     21918    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21917    
unix  3      [ ]         STREAM     CONNECTED     21913    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21912    
unix  3      [ ]         STREAM     CONNECTED     21907    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     21906    
unix  3      [ ]         STREAM     CONNECTED     21905    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21904    
unix  3      [ ]         STREAM     CONNECTED     21903    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21902    
unix  3      [ ]         STREAM     CONNECTED     21901    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21900    
unix  3      [ ]         STREAM     CONNECTED     21897    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     21896    
unix  3      [ ]         STREAM     CONNECTED     21888    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21887    
unix  3      [ ]         STREAM     CONNECTED     21883    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21882    
unix  3      [ ]         STREAM     CONNECTED     21873    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21872    
unix  3      [ ]         STREAM     CONNECTED     21871    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21870    
unix  3      [ ]         STREAM     CONNECTED     21869    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21868    
unix  3      [ ]         STREAM     CONNECTED     21865    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21864    
unix  3      [ ]         STREAM     CONNECTED     21860    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21859    
unix  3      [ ]         STREAM     CONNECTED     21854    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21853    
unix  3      [ ]         STREAM     CONNECTED     21852    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21851    
unix  3      [ ]         STREAM     CONNECTED     21850    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21849    
unix  3      [ ]         STREAM     CONNECTED     21846    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21845    
unix  3      [ ]         STREAM     CONNECTED     21844    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21843    
unix  3      [ ]         STREAM     CONNECTED     21837    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21836    
unix  3      [ ]         STREAM     CONNECTED     21785    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21784    
unix  3      [ ]         STREAM     CONNECTED     21783    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     21782    
unix  3      [ ]         STREAM     CONNECTED     21774    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     21773    
unix  3      [ ]         STREAM     CONNECTED     21772    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21771    
unix  3      [ ]         STREAM     CONNECTED     21770    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     21769    
unix  3      [ ]         STREAM     CONNECTED     21768    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21767    
unix  3      [ ]         STREAM     CONNECTED     21766    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21765    
unix  3      [ ]         STREAM     CONNECTED     21762    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21761    
unix  3      [ ]         STREAM     CONNECTED     21760    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21759    
unix  3      [ ]         STREAM     CONNECTED     21753    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21752    
unix  3      [ ]         STREAM     CONNECTED     21749    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21747    
unix  3      [ ]         STREAM     CONNECTED     21738    /tmp/mapping-chene
unix  3      [ ]         STREAM     CONNECTED     21733    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     21732    
unix  3      [ ]         STREAM     CONNECTED     21731    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21730    
unix  3      [ ]         STREAM     CONNECTED     21729    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21728    
unix  3      [ ]         STREAM     CONNECTED     21727    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21726    
unix  3      [ ]         STREAM     CONNECTED     21723    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21722    
unix  3      [ ]         STREAM     CONNECTED     21718    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21717    
unix  3      [ ]         STREAM     CONNECTED     21705    
unix  3      [ ]         STREAM     CONNECTED     21503    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     21500    
unix  3      [ ]         STREAM     CONNECTED     21499    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21498    
unix  3      [ ]         STREAM     CONNECTED     20540    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     20539    
unix  3      [ ]         STREAM     CONNECTED     20536    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20535    
unix  3      [ ]         STREAM     CONNECTED     20533    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20532    
unix  3      [ ]         STREAM     CONNECTED     20528    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20527    
unix  3      [ ]         STREAM     CONNECTED     20518    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     20517    
unix  3      [ ]         STREAM     CONNECTED     20516    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20515    
unix  3      [ ]         STREAM     CONNECTED     20514    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20513    
unix  3      [ ]         STREAM     CONNECTED     20504    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20503    
unix  3      [ ]         STREAM     CONNECTED     20502    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20501    
unix  3      [ ]         STREAM     CONNECTED     20500    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20499    
unix  3      [ ]         STREAM     CONNECTED     20494    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20493    
unix  3      [ ]         STREAM     CONNECTED     20485    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20484    
unix  3      [ ]         STREAM     CONNECTED     20483    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     20482    
unix  3      [ ]         STREAM     CONNECTED     20481    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  3      [ ]         STREAM     CONNECTED     20480    
unix  3      [ ]         STREAM     CONNECTED     20479    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20477    
unix  3      [ ]         STREAM     CONNECTED     20478    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20476    
unix  3      [ ]         STREAM     CONNECTED     20472    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     20471    
unix  3      [ ]         STREAM     CONNECTED     20468    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20467    
unix  3      [ ]         STREAM     CONNECTED     20465    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20464    
unix  3      [ ]         STREAM     CONNECTED     20460    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20459    
unix  3      [ ]         STREAM     CONNECTED     20453    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20452    
unix  3      [ ]         STREAM     CONNECTED     20318    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20317    
unix  3      [ ]         STREAM     CONNECTED     20316    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20315    
unix  3      [ ]         STREAM     CONNECTED     20314    /tmp/orbit-chene/linc-192b-0-3f8815f259311
unix  3      [ ]         STREAM     CONNECTED     20313    
unix  3      [ ]         STREAM     CONNECTED     20310    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20309    
unix  3      [ ]         STREAM     CONNECTED     20305    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20304    
unix  3      [ ]         STREAM     CONNECTED     20290    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20289    
unix  3      [ ]         STREAM     CONNECTED     20286    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20285    
unix  3      [ ]         STREAM     CONNECTED     20283    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20282    
unix  2      [ ]         DGRAM                    20281    
unix  3      [ ]         STREAM     CONNECTED     20276    /tmp/orbit-chene/linc-191a-0-39cf5527cbbae
unix  3      [ ]         STREAM     CONNECTED     20275    
unix  3      [ ]         STREAM     CONNECTED     20272    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20271    
unix  3      [ ]         STREAM     CONNECTED     20269    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20268    
unix  3      [ ]         STREAM     CONNECTED     20264    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20263    
unix  3      [ ]         STREAM     CONNECTED     20258    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20257    
unix  3      [ ]         STREAM     CONNECTED     20256    /tmp/orbit-chene/linc-1914-0-664249697baac
unix  3      [ ]         STREAM     CONNECTED     20255    
unix  3      [ ]         STREAM     CONNECTED     20252    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20251    
unix  3      [ ]         STREAM     CONNECTED     20249    /tmp/orbit-chene/linc-190d-0-6642496978091
unix  3      [ ]         STREAM     CONNECTED     20248    
unix  3      [ ]         STREAM     CONNECTED     20244    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20243    
unix  3      [ ]         STREAM     CONNECTED     20238    /tmp/orbit-chene/linc-191f-0-48ca4364e8378
unix  3      [ ]         STREAM     CONNECTED     20237    
unix  3      [ ]         STREAM     CONNECTED     20234    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20233    
unix  3      [ ]         STREAM     CONNECTED     20229    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20228    
unix  3      [ ]         STREAM     CONNECTED     20241    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20187    
unix  3      [ ]         STREAM     CONNECTED     20183    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20182    
unix  3      [ ]         STREAM     CONNECTED     20128    /tmp/orbit-chene/linc-190e-0-17a29b62b232d
unix  3      [ ]         STREAM     CONNECTED     20125    
unix  3      [ ]         STREAM     CONNECTED     20121    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20120    
unix  3      [ ]         STREAM     CONNECTED     20116    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20115    
unix  3      [ ]         STREAM     CONNECTED     20114    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20113    
unix  3      [ ]         STREAM     CONNECTED     20111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20110    
unix  3      [ ]         STREAM     CONNECTED     20240    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20106    
unix  3      [ ]         STREAM     CONNECTED     20100    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20099    
unix  3      [ ]         STREAM     CONNECTED     20090    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20089    
unix  3      [ ]         STREAM     CONNECTED     20088    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20087    
unix  3      [ ]         STREAM     CONNECTED     20086    /tmp/orbit-chene/linc-190c-0-7899827047b65
unix  3      [ ]         STREAM     CONNECTED     20085    
unix  3      [ ]         STREAM     CONNECTED     20082    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20081    
unix  3      [ ]         STREAM     CONNECTED     20078    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20077    
unix  3      [ ]         STREAM     CONNECTED     20067    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20066    
unix  3      [ ]         STREAM     CONNECTED     20064    /tmp/orbit-chene/linc-18fc-0-64e94a3ee2636
unix  3      [ ]         STREAM     CONNECTED     20063    
unix  3      [ ]         STREAM     CONNECTED     20060    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20059    
unix  3      [ ]         STREAM     CONNECTED     20054    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20053    
unix  3      [ ]         STREAM     CONNECTED     20050    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  3      [ ]         STREAM     CONNECTED     20049    
unix  3      [ ]         STREAM     CONNECTED     20046    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20045    
unix  3      [ ]         STREAM     CONNECTED     20043    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20042    
unix  3      [ ]         STREAM     CONNECTED     20038    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20037    
unix  3      [ ]         STREAM     CONNECTED     20020    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     20019    
unix  3      [ ]         STREAM     CONNECTED     20016    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20015    
unix  3      [ ]         STREAM     CONNECTED     20013    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20012    
unix  3      [ ]         STREAM     CONNECTED     20008    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20007    
unix  3      [ ]         STREAM     CONNECTED     20002    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20001    
unix  3      [ ]         STREAM     CONNECTED     19999    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19998    
unix  3      [ ]         STREAM     CONNECTED     19997    /tmp/orbit-chene/linc-1901-0-3419be593d893
unix  3      [ ]         STREAM     CONNECTED     19996    
unix  3      [ ]         STREAM     CONNECTED     19993    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19992    
unix  3      [ ]         STREAM     CONNECTED     19988    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     19987    
unix  4      [ ]         STREAM     CONNECTED     19986    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19985    
unix  3      [ ]         STREAM     CONNECTED     19979    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19978    
unix  3      [ ]         STREAM     CONNECTED     19887    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     19886    
unix  3      [ ]         STREAM     CONNECTED     19885    /tmp/orbit-chene/linc-18f6-0-41a7df77968b7
unix  3      [ ]         STREAM     CONNECTED     19884    
unix  3      [ ]         STREAM     CONNECTED     19881    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19880    
unix  3      [ ]         STREAM     CONNECTED     19876    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19875    
unix  3      [ ]         STREAM     CONNECTED     19866    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     19865    
unix  3      [ ]         STREAM     CONNECTED     19864    
unix  3      [ ]         STREAM     CONNECTED     19863    
unix  3      [ ]         STREAM     CONNECTED     19832    /tmp/orbit-chene/linc-18c9-0-45e967f730b88
unix  3      [ ]         STREAM     CONNECTED     19831    
unix  3      [ ]         STREAM     CONNECTED     19830    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19571    
unix  3      [ ]         STREAM     CONNECTED     19552    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19551    
unix  3      [ ]         STREAM     CONNECTED     19481    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19480    
unix  3      [ ]         STREAM     CONNECTED     19473    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19472    
unix  3      [ ]         STREAM     CONNECTED     19322    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     19321    
unix  3      [ ]         STREAM     CONNECTED     19082    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     19081    
unix  5      [ ]         STREAM     CONNECTED     19391    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19077    
unix  3      [ ]         STREAM     CONNECTED     18839    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18838    
unix  2      [ ]         DGRAM                    18837    
unix  3      [ ]         STREAM     CONNECTED     18834    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18833    
unix  2      [ ]         DGRAM                    18832    
unix  3      [ ]         STREAM     CONNECTED     18816    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18815    
unix  2      [ ]         DGRAM                    18799    
unix  3      [ ]         STREAM     CONNECTED     18767    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18766    
unix  2      [ ]         DGRAM                    18765    
unix  3      [ ]         STREAM     CONNECTED     18758    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18757    
unix  3      [ ]         STREAM     CONNECTED     18752    
unix  3      [ ]         STREAM     CONNECTED     18751    
unix  2      [ ]         DGRAM                    18749    
unix  2      [ ]         DGRAM                    18696    
unix  3      [ ]         STREAM     CONNECTED     18685    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18684    
unix  3      [ ]         STREAM     CONNECTED     18517    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18516    
unix  3      [ ]         STREAM     CONNECTED     18513    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18512    
unix  3      [ ]         STREAM     CONNECTED     18183    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18182    
unix  3      [ ]         STREAM     CONNECTED     18174    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18173    
unix  3      [ ]         STREAM     CONNECTED     18160    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18153    
unix  3      [ ]         STREAM     CONNECTED     18159    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18141    
unix  3      [ ]         STREAM     CONNECTED     18158    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17740    
unix  3      [ ]         STREAM     CONNECTED     18154    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17733    
unix  3      [ ]         STREAM     CONNECTED     18136    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17717    
unix  3      [ ]         STREAM     CONNECTED     17241    @/var/run/hald/dbus-dltQLXAU2W
unix  3      [ ]         STREAM     CONNECTED     17240    
unix  3      [ ]         STREAM     CONNECTED     17237    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17236    
unix  3      [ ]         STREAM     CONNECTED     17224    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17223    
unix  3      [ ]         STREAM     CONNECTED     17221    
unix  3      [ ]         STREAM     CONNECTED     17220    
unix  3      [ ]         STREAM     CONNECTED     17222    @/tmp/dbus-c9nZcOmt9x
unix  3      [ ]         STREAM     CONNECTED     17219    
unix  3      [ ]         STREAM     CONNECTED     17192    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17191    
unix  3      [ ]         STREAM     CONNECTED     17181    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17180    
unix  2      [ ]         DGRAM                    17176    
unix  3      [ ]         STREAM     CONNECTED     17161    
unix  3      [ ]         STREAM     CONNECTED     17160    
unix  2      [ ]         DGRAM                    17147    
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      1 192.168.1.217:33708     12.120.1.254:www        FIN_WAIT1  
tcp6       0      0 *:ssh                   *:*                     LISTEN     
udp        0      0 *:32769                 *:*                                
udp        0      0 192.168.1.21:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 192.168.1.2:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 192.168.1.217:ntp       *:*                                
udp        0      0 localhost:ntp           *:*                                
udp        0      0 *:ntp                   *:*                                
udp6       0      0 fe80::217:31ff:fe56:ntp *:*                                
udp6       0      0 ip6-localhost:ntp       *:*                                
udp6       0      0 *:ntp                   *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     19068    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16898    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     19464    /tmp/keyring-YUziU2/socket
unix  2      [ ACC ]     STREAM     LISTENING     17158    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     19546    /tmp/ssh-tXuQwp6345/agent.6345
unix  2      [ ACC ]     STREAM     LISTENING     19562    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  2      [ ACC ]     STREAM     LISTENING     21734    /tmp/mapping-chene
unix  2      [ ACC ]     STREAM     LISTENING     19572    /tmp/orbit-chene/linc-18c9-0-45e967f730b88
unix  2      [ ACC ]     STREAM     LISTENING     19848    /tmp/.ICE-unix/6345
unix  2      [ ACC ]     STREAM     LISTENING     19882    /tmp/orbit-chene/linc-18f6-0-41a7df77968b7
unix  2      [ ACC ]     STREAM     LISTENING     19994    /tmp/orbit-chene/linc-1901-0-3419be593d893
unix  2      [ ACC ]     STREAM     LISTENING     20017    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  2      [ ACC ]     STREAM     LISTENING     20047    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  2      [ ACC ]     STREAM     LISTENING     20061    /tmp/orbit-chene/linc-18fc-0-64e94a3ee2636
unix  2      [ ACC ]     STREAM     LISTENING     20083    /tmp/orbit-chene/linc-190c-0-7899827047b65
unix  2      [ ACC ]     STREAM     LISTENING     20123    /tmp/orbit-chene/linc-190e-0-17a29b62b232d
unix  2      [ ACC ]     STREAM     LISTENING     20235    /tmp/orbit-chene/linc-191f-0-48ca4364e8378
unix  2      [ ACC ]     STREAM     LISTENING     18975    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     20246    /tmp/orbit-chene/linc-190d-0-6642496978091
unix  2      [ ACC ]     STREAM     LISTENING     20253    /tmp/orbit-chene/linc-1914-0-664249697baac
unix  2      [ ACC ]     STREAM     LISTENING     20273    /tmp/orbit-chene/linc-191a-0-39cf5527cbbae
unix  2      [ ACC ]     STREAM     LISTENING     20311    /tmp/orbit-chene/linc-192b-0-3f8815f259311
unix  2      [ ACC ]     STREAM     LISTENING     20469    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  2      [ ACC ]     STREAM     LISTENING     17235    @/var/run/hald/dbus-nMDK0pHEFF
unix  2      [ ACC ]     STREAM     LISTENING     20473    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  2      [ ACC ]     STREAM     LISTENING     20537    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  2      [ ACC ]     STREAM     LISTENING     21724    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  2      [ ACC ]     STREAM     LISTENING     21750    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  2      [ ACC ]     STREAM     LISTENING     21847    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  2      [ ACC ]     STREAM     LISTENING     21866    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  2      [ ACC ]     STREAM     LISTENING     21889    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  2      [ ACC ]     STREAM     LISTENING     21919    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  2      [ ACC ]     STREAM     LISTENING     21959    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  2      [ ACC ]     STREAM     LISTENING     22020    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  2      [ ACC ]     STREAM     LISTENING     22086    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  2      [ ACC ]     STREAM     LISTENING     22572    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  2      [ ACC ]     STREAM     LISTENING     489059   /tmp/orbit-chene/linc-1df2-0-61dbe97f8d91c
unix  2      [ ]         DGRAM                    8894     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     487489   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     18755    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     18840    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17218    @/tmp/dbus-c9nZcOmt9x
unix  2      [ ]         DGRAM                    9114     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     18828    @/var/run/dbus-35xWvYdQXg
unix  2      [ ACC ]     STREAM     LISTENING     18826    /var/run/sdp
unix  2      [ ]         DGRAM                    17246    @/org/freedesktop/hal/udev_event
unix  11     [ ]         DGRAM                    17065    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     19862    @/tmp/dbus-gSfQ2MLoyZ
unix  2      [ ACC ]     STREAM     LISTENING     17238    @/var/run/hald/dbus-dltQLXAU2W
unix  3      [ ]         STREAM     CONNECTED     489064   @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     489063   
unix  3      [ ]         STREAM     CONNECTED     489062   /tmp/orbit-chene/linc-1df2-0-61dbe97f8d91c
unix  3      [ ]         STREAM     CONNECTED     489061   
unix  3      [ ]         STREAM     CONNECTED     489058   /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     489057   
unix  3      [ ]         STREAM     CONNECTED     489049   /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     489048   
unix  3      [ ]         STREAM     CONNECTED     487480   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     487479   
unix  3      [ ]         STREAM     CONNECTED     22594    
unix  3      [ ]         STREAM     CONNECTED     22593    
unix  3      [ ]         STREAM     CONNECTED     22579    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  3      [ ]         STREAM     CONNECTED     22578    
unix  3      [ ]         STREAM     CONNECTED     22577    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22576    
unix  3      [ ]         STREAM     CONNECTED     22575    /tmp/orbit-chene/linc-1994-0-105231d76e127
unix  3      [ ]         STREAM     CONNECTED     22574    
unix  3      [ ]         STREAM     CONNECTED     22571    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22570    
unix  3      [ ]         STREAM     CONNECTED     22568    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22567    
unix  3      [ ]         STREAM     CONNECTED     22563    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22562    
unix  3      [ ]         STREAM     CONNECTED     22132    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     22131    
unix  3      [ ]         STREAM     CONNECTED     22121    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     22120    
unix  3      [ ]         STREAM     CONNECTED     22115    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22114    
unix  3      [ ]         STREAM     CONNECTED     22105    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22104    
unix  3      [ ]         STREAM     CONNECTED     22103    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22102    
unix  3      [ ]         STREAM     CONNECTED     22101    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22100    
unix  3      [ ]         STREAM     CONNECTED     22093    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22092    
unix  3      [ ]         STREAM     CONNECTED     22091    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22090    
unix  3      [ ]         STREAM     CONNECTED     22089    /tmp/orbit-chene/linc-198b-0-5c04e34ca25f5
unix  3      [ ]         STREAM     CONNECTED     22088    
unix  3      [ ]         STREAM     CONNECTED     22085    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22084    
unix  3      [ ]         STREAM     CONNECTED     22080    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22079    
unix  3      [ ]         STREAM     CONNECTED     22060    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22059    
unix  3      [ ]         STREAM     CONNECTED     22058    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     22057    
unix  3      [ ]         STREAM     CONNECTED     22044    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     22043    
unix  3      [ ]         STREAM     CONNECTED     22042    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22041    
unix  3      [ ]         STREAM     CONNECTED     22034    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22033    
unix  3      [ ]         STREAM     CONNECTED     22032    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     22031    
unix  3      [ ]         STREAM     CONNECTED     22029    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     22028    
unix  3      [ ]         STREAM     CONNECTED     22023    /tmp/orbit-chene/linc-197c-0-2ca1350570740
unix  3      [ ]         STREAM     CONNECTED     22022    
unix  3      [ ]         STREAM     CONNECTED     22019    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     22018    
unix  3      [ ]         STREAM     CONNECTED     21976    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21975    
unix  3      [ ]         STREAM     CONNECTED     21974    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21973    
unix  3      [ ]         STREAM     CONNECTED     21966    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21965    
unix  3      [ ]         STREAM     CONNECTED     21964    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21963    
unix  3      [ ]         STREAM     CONNECTED     21962    /tmp/orbit-chene/linc-197e-0-47af9a76bb625
unix  3      [ ]         STREAM     CONNECTED     21961    
unix  3      [ ]         STREAM     CONNECTED     21958    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21957    
unix  3      [ ]         STREAM     CONNECTED     21953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21952    
unix  3      [ ]         STREAM     CONNECTED     21949    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21948    
unix  3      [ ]         STREAM     CONNECTED     21947    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21946    
unix  3      [ ]         STREAM     CONNECTED     21938    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21937    
unix  3      [ ]         STREAM     CONNECTED     21936    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21935    
unix  3      [ ]         STREAM     CONNECTED     21926    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21925    
unix  3      [ ]         STREAM     CONNECTED     21924    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21923    
unix  3      [ ]         STREAM     CONNECTED     21922    /tmp/orbit-chene/linc-1982-0-15d0e23bc3cc7
unix  3      [ ]         STREAM     CONNECTED     21921    
unix  3      [ ]         STREAM     CONNECTED     21918    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21917    
unix  3      [ ]         STREAM     CONNECTED     21913    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21912    
unix  3      [ ]         STREAM     CONNECTED     21907    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     21906    
unix  3      [ ]         STREAM     CONNECTED     21905    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21904    
unix  3      [ ]         STREAM     CONNECTED     21903    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21902    
unix  3      [ ]         STREAM     CONNECTED     21901    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21900    
unix  3      [ ]         STREAM     CONNECTED     21897    /tmp/orbit-chene/linc-197a-0-15d0e23b327d2
unix  3      [ ]         STREAM     CONNECTED     21896    
unix  3      [ ]         STREAM     CONNECTED     21888    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21887    
unix  3      [ ]         STREAM     CONNECTED     21883    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21882    
unix  3      [ ]         STREAM     CONNECTED     21873    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21872    
unix  3      [ ]         STREAM     CONNECTED     21871    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21870    
unix  3      [ ]         STREAM     CONNECTED     21869    /tmp/orbit-chene/linc-1984-0-15d0e23b2611f
unix  3      [ ]         STREAM     CONNECTED     21868    
unix  3      [ ]         STREAM     CONNECTED     21865    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21864    
unix  3      [ ]         STREAM     CONNECTED     21860    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21859    
unix  3      [ ]         STREAM     CONNECTED     21854    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21853    
unix  3      [ ]         STREAM     CONNECTED     21852    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21851    
unix  3      [ ]         STREAM     CONNECTED     21850    /tmp/orbit-chene/linc-1980-0-15d0e23b1062e
unix  3      [ ]         STREAM     CONNECTED     21849    
unix  3      [ ]         STREAM     CONNECTED     21846    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21845    
unix  3      [ ]         STREAM     CONNECTED     21844    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21843    
unix  3      [ ]         STREAM     CONNECTED     21837    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21836    
unix  3      [ ]         STREAM     CONNECTED     21785    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21784    
unix  3      [ ]         STREAM     CONNECTED     21783    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     21782    
unix  3      [ ]         STREAM     CONNECTED     21774    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     21773    
unix  3      [ ]         STREAM     CONNECTED     21772    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21771    
unix  3      [ ]         STREAM     CONNECTED     21770    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     21769    
unix  3      [ ]         STREAM     CONNECTED     21768    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21767    
unix  3      [ ]         STREAM     CONNECTED     21766    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21765    
unix  3      [ ]         STREAM     CONNECTED     21762    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     21761    
unix  3      [ ]         STREAM     CONNECTED     21760    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21759    
unix  3      [ ]         STREAM     CONNECTED     21753    /tmp/orbit-chene/linc-194e-0-f91bb6faa4a3
unix  3      [ ]         STREAM     CONNECTED     21752    
unix  3      [ ]         STREAM     CONNECTED     21749    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21747    
unix  3      [ ]         STREAM     CONNECTED     21738    /tmp/mapping-chene
unix  3      [ ]         STREAM     CONNECTED     21733    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     21732    
unix  3      [ ]         STREAM     CONNECTED     21731    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21730    
unix  3      [ ]         STREAM     CONNECTED     21729    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21728    
unix  3      [ ]         STREAM     CONNECTED     21727    /tmp/orbit-chene/linc-194a-0-f91bb6f76e23
unix  3      [ ]         STREAM     CONNECTED     21726    
unix  3      [ ]         STREAM     CONNECTED     21723    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     21722    
unix  3      [ ]         STREAM     CONNECTED     21718    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21717    
unix  3      [ ]         STREAM     CONNECTED     21705    
unix  3      [ ]         STREAM     CONNECTED     21503    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     21500    
unix  3      [ ]         STREAM     CONNECTED     21499    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     21498    
unix  3      [ ]         STREAM     CONNECTED     20540    /tmp/orbit-chene/linc-1941-0-1dd09324f2b98
unix  3      [ ]         STREAM     CONNECTED     20539    
unix  3      [ ]         STREAM     CONNECTED     20536    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20535    
unix  3      [ ]         STREAM     CONNECTED     20533    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20532    
unix  3      [ ]         STREAM     CONNECTED     20528    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20527    
unix  3      [ ]         STREAM     CONNECTED     20518    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     20517    
unix  3      [ ]         STREAM     CONNECTED     20516    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20515    
unix  3      [ ]         STREAM     CONNECTED     20514    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20513    
unix  3      [ ]         STREAM     CONNECTED     20504    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20503    
unix  3      [ ]         STREAM     CONNECTED     20502    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20501    
unix  3      [ ]         STREAM     CONNECTED     20500    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20499    
unix  3      [ ]         STREAM     CONNECTED     20494    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20493    
unix  3      [ ]         STREAM     CONNECTED     20485    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20484    
unix  3      [ ]         STREAM     CONNECTED     20483    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     20482    
unix  3      [ ]         STREAM     CONNECTED     20481    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  3      [ ]         STREAM     CONNECTED     20480    
unix  3      [ ]         STREAM     CONNECTED     20479    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20477    
unix  3      [ ]         STREAM     CONNECTED     20478    /tmp/orbit-chene/linc-1909-0-54f0090c8c7b8
unix  3      [ ]         STREAM     CONNECTED     20476    
unix  3      [ ]         STREAM     CONNECTED     20472    /tmp/orbit-chene/linc-1918-0-32578e5374958
unix  3      [ ]         STREAM     CONNECTED     20471    
unix  3      [ ]         STREAM     CONNECTED     20468    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20467    
unix  3      [ ]         STREAM     CONNECTED     20465    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20464    
unix  3      [ ]         STREAM     CONNECTED     20460    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20459    
unix  3      [ ]         STREAM     CONNECTED     20453    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20452    
unix  3      [ ]         STREAM     CONNECTED     20318    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20317    
unix  3      [ ]         STREAM     CONNECTED     20316    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20315    
unix  3      [ ]         STREAM     CONNECTED     20314    /tmp/orbit-chene/linc-192b-0-3f8815f259311
unix  3      [ ]         STREAM     CONNECTED     20313    
unix  3      [ ]         STREAM     CONNECTED     20310    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20309    
unix  3      [ ]         STREAM     CONNECTED     20305    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20304    
unix  3      [ ]         STREAM     CONNECTED     20290    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20289    
unix  3      [ ]         STREAM     CONNECTED     20286    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20285    
unix  3      [ ]         STREAM     CONNECTED     20283    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20282    
unix  2      [ ]         DGRAM                    20281    
unix  3      [ ]         STREAM     CONNECTED     20276    /tmp/orbit-chene/linc-191a-0-39cf5527cbbae
unix  3      [ ]         STREAM     CONNECTED     20275    
unix  3      [ ]         STREAM     CONNECTED     20272    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20271    
unix  3      [ ]         STREAM     CONNECTED     20269    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20268    
unix  3      [ ]         STREAM     CONNECTED     20264    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20263    
unix  3      [ ]         STREAM     CONNECTED     20258    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20257    
unix  3      [ ]         STREAM     CONNECTED     20256    /tmp/orbit-chene/linc-1914-0-664249697baac
unix  3      [ ]         STREAM     CONNECTED     20255    
unix  3      [ ]         STREAM     CONNECTED     20252    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20251    
unix  3      [ ]         STREAM     CONNECTED     20249    /tmp/orbit-chene/linc-190d-0-6642496978091
unix  3      [ ]         STREAM     CONNECTED     20248    
unix  3      [ ]         STREAM     CONNECTED     20244    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20243    
unix  3      [ ]         STREAM     CONNECTED     20238    /tmp/orbit-chene/linc-191f-0-48ca4364e8378
unix  3      [ ]         STREAM     CONNECTED     20237    
unix  3      [ ]         STREAM     CONNECTED     20234    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20233    
unix  3      [ ]         STREAM     CONNECTED     20229    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20228    
unix  3      [ ]         STREAM     CONNECTED     20241    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20187    
unix  3      [ ]         STREAM     CONNECTED     20183    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20182    
unix  3      [ ]         STREAM     CONNECTED     20128    /tmp/orbit-chene/linc-190e-0-17a29b62b232d
unix  3      [ ]         STREAM     CONNECTED     20125    
unix  3      [ ]         STREAM     CONNECTED     20121    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20120    
unix  3      [ ]         STREAM     CONNECTED     20116    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20115    
unix  3      [ ]         STREAM     CONNECTED     20114    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20113    
unix  3      [ ]         STREAM     CONNECTED     20111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20110    
unix  3      [ ]         STREAM     CONNECTED     20240    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20106    
unix  3      [ ]         STREAM     CONNECTED     20100    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20099    
unix  3      [ ]         STREAM     CONNECTED     20090    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20089    
unix  3      [ ]         STREAM     CONNECTED     20088    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20087    
unix  3      [ ]         STREAM     CONNECTED     20086    /tmp/orbit-chene/linc-190c-0-7899827047b65
unix  3      [ ]         STREAM     CONNECTED     20085    
unix  3      [ ]         STREAM     CONNECTED     20082    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20081    
unix  3      [ ]         STREAM     CONNECTED     20078    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20077    
unix  3      [ ]         STREAM     CONNECTED     20067    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20066    
unix  3      [ ]         STREAM     CONNECTED     20064    /tmp/orbit-chene/linc-18fc-0-64e94a3ee2636
unix  3      [ ]         STREAM     CONNECTED     20063    
unix  3      [ ]         STREAM     CONNECTED     20060    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20059    
unix  3      [ ]         STREAM     CONNECTED     20054    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20053    
unix  3      [ ]         STREAM     CONNECTED     20050    /tmp/orbit-chene/linc-1900-0-3419be59c39f4
unix  3      [ ]         STREAM     CONNECTED     20049    
unix  3      [ ]         STREAM     CONNECTED     20046    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20045    
unix  3      [ ]         STREAM     CONNECTED     20043    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20042    
unix  3      [ ]         STREAM     CONNECTED     20038    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20037    
unix  3      [ ]         STREAM     CONNECTED     20020    /tmp/orbit-chene/linc-18ff-0-3419be595546b
unix  3      [ ]         STREAM     CONNECTED     20019    
unix  3      [ ]         STREAM     CONNECTED     20016    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     20015    
unix  3      [ ]         STREAM     CONNECTED     20013    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     20012    
unix  3      [ ]         STREAM     CONNECTED     20008    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20007    
unix  3      [ ]         STREAM     CONNECTED     20002    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     20001    
unix  3      [ ]         STREAM     CONNECTED     19999    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19998    
unix  3      [ ]         STREAM     CONNECTED     19997    /tmp/orbit-chene/linc-1901-0-3419be593d893
unix  3      [ ]         STREAM     CONNECTED     19996    
unix  3      [ ]         STREAM     CONNECTED     19993    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19992    
unix  3      [ ]         STREAM     CONNECTED     19988    /tmp/.ICE-unix/6345
unix  3      [ ]         STREAM     CONNECTED     19987    
unix  4      [ ]         STREAM     CONNECTED     19986    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19985    
unix  3      [ ]         STREAM     CONNECTED     19979    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19978    
unix  3      [ ]         STREAM     CONNECTED     19887    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     19886    
unix  3      [ ]         STREAM     CONNECTED     19885    /tmp/orbit-chene/linc-18f6-0-41a7df77968b7
unix  3      [ ]         STREAM     CONNECTED     19884    
unix  3      [ ]         STREAM     CONNECTED     19881    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19880    
unix  3      [ ]         STREAM     CONNECTED     19876    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19875    
unix  3      [ ]         STREAM     CONNECTED     19866    @/tmp/dbus-gSfQ2MLoyZ
unix  3      [ ]         STREAM     CONNECTED     19865    
unix  3      [ ]         STREAM     CONNECTED     19864    
unix  3      [ ]         STREAM     CONNECTED     19863    
unix  3      [ ]         STREAM     CONNECTED     19832    /tmp/orbit-chene/linc-18c9-0-45e967f730b88
unix  3      [ ]         STREAM     CONNECTED     19831    
unix  3      [ ]         STREAM     CONNECTED     19830    /tmp/orbit-chene/linc-18f0-0-77e30f4f1ca5a
unix  3      [ ]         STREAM     CONNECTED     19571    
unix  3      [ ]         STREAM     CONNECTED     19552    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19551    
unix  3      [ ]         STREAM     CONNECTED     19481    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19480    
unix  3      [ ]         STREAM     CONNECTED     19473    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19472    
unix  3      [ ]         STREAM     CONNECTED     19322    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     19321    
unix  3      [ ]         STREAM     CONNECTED     19082    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     19081    
unix  5      [ ]         STREAM     CONNECTED     19391    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19077    
unix  3      [ ]         STREAM     CONNECTED     18839    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18838    
unix  2      [ ]         DGRAM                    18837    
unix  3      [ ]         STREAM     CONNECTED     18834    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18833    
unix  2      [ ]         DGRAM                    18832    
unix  3      [ ]         STREAM     CONNECTED     18816    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18815    
unix  2      [ ]         DGRAM                    18799    
unix  3      [ ]         STREAM     CONNECTED     18767    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18766    
unix  2      [ ]         DGRAM                    18765    
unix  3      [ ]         STREAM     CONNECTED     18758    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18757    
unix  3      [ ]         STREAM     CONNECTED     18752    
unix  3      [ ]         STREAM     CONNECTED     18751    
unix  2      [ ]         DGRAM                    18749    
unix  2      [ ]         DGRAM                    18696    
unix  3      [ ]         STREAM     CONNECTED     18685    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18684    
unix  3      [ ]         STREAM     CONNECTED     18517    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18516    
unix  3      [ ]         STREAM     CONNECTED     18513    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18512    
unix  3      [ ]         STREAM     CONNECTED     18183    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18182    
unix  3      [ ]         STREAM     CONNECTED     18174    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     18173    
unix  3      [ ]         STREAM     CONNECTED     18160    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18153    
unix  3      [ ]         STREAM     CONNECTED     18159    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     18141    
unix  3      [ ]         STREAM     CONNECTED     18158    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17740    
unix  3      [ ]         STREAM     CONNECTED     18154    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17733    
unix  3      [ ]         STREAM     CONNECTED     18136    @/var/run/hald/dbus-nMDK0pHEFF
unix  3      [ ]         STREAM     CONNECTED     17717    
unix  3      [ ]         STREAM     CONNECTED     17241    @/var/run/hald/dbus-dltQLXAU2W
unix  3      [ ]         STREAM     CONNECTED     17240    
unix  3      [ ]         STREAM     CONNECTED     17237    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17236    
unix  3      [ ]         STREAM     CONNECTED     17224    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17223    
unix  3      [ ]         STREAM     CONNECTED     17221    
unix  3      [ ]         STREAM     CONNECTED     17220    
unix  3      [ ]         STREAM     CONNECTED     17222    @/tmp/dbus-c9nZcOmt9x
unix  3      [ ]         STREAM     CONNECTED     17219    
unix  3      [ ]         STREAM     CONNECTED     17192    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17191    
unix  3      [ ]         STREAM     CONNECTED     17181    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17180    
unix  2      [ ]         DGRAM                    17176    
unix  3      [ ]         STREAM     CONNECTED     17161    
unix  3      [ ]         STREAM     CONNECTED     17160    
unix  2      [ ]         DGRAM                    17147

---

### Post by SpaceTeddy on 2008-02-20
netstat does not really help in this situation. What you want is to look at tcpdump (see what pakets are flying around) or wireshard (same, just with graphical stuff) and figure out from there what the problem is.

also, you might want to try to block your network card (not disable) and see if that stops the problem. if it does not, you have a severe problem.

try to block all network traffic with
> sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP

to reenable your network you can use
> sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT

if these commands stop your flow, do a small dump of your networktraffic (with either iptraf or wireshark), [SIZE="4"]**ZIP IT**[/SIZE], and append it here in your post. i would be willing to look through it and try to find the underlaying cause...

---

### Post by chene on 2008-03-15
> **SpaceTeddy said:**
> netstat does not really help in this situation. What you want is to look at tcpdump (see what pakets are flying around) or wireshard (same, just with graphical stuff) and figure out from there what the problem is.

also, you might want to try to block your network card (not disable) and see if that stops the problem. if it does not, you have a severe problem.

try to block all network traffic with


to reenable your network you can use


if these commands stop your flow, do a small dump of your networktraffic (with either iptraf or wireshark), [SIZE="4"]**ZIP IT**[/SIZE], and append it here in your post. i would be willing to look through it and try to find the underlaying cause...

hi there,

sorry for the late reply.  I have been busy with my job and had no time to looking into my home network problem.  As per your suggestion, I think my computer may be compromised.  The two commends you suggested to block the traffic did NOT stop anything, and I'm attaching the captured report from wireshark below.

Note the capture was done when the machine is just booted, i.e. no program was started (no pidgin, deluge, browser, etc).

Port 29874 is my torrent port used by deluge.  I'm going to change it to a different port to see if it helps.  It is surprising that it is been used even though deluge is not running, an indication that my computer is being compromised.

I'm also using arno-iptables-firewall with the following ports open:

DC_OPEN_TCP="21 22 135 139 445 631 990 5678 5679 29874 32989"
DC_OPEN_UDP="137 138 29874 32989"

this was meant for my ssh/ftp/samba/cupd.  any help is very much appreciated,

---

