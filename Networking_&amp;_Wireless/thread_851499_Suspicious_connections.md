---
title: "Suspicious connections"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by HyperHacker on 2008-07-06
I just noticed about 30 outbound connections to 204.2.228.51 on port 80 listed for a moment in Conky. There doesn't seem to be an actual site at that address ("URL / is invalid"), and it doesn't appear to match any of the sites I've visited today.

Out of curiosity I checked netstat and got some suspicious results:```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 mercury:41383           home:www                ESTABLISHED
tcp        0      0 mercury:45098           205.188.10.185:aol      ESTABLISHED
tcp        0      0 mercury:59236           63-217-20-68.sdsl.c:www ESTABLISHED
tcp        0      0 mercury:42373           205.188.13.60:aol       ESTABLISHED
tcp        0      0 mercury:41382           home:www                ESTABLISHED
tcp        0      0 mercury:49801           caim-d03b.blue.aol.:aol ESTABLISHED
tcp        0      0 mercury:38069           by1msg4246206.gate:msnp ESTABLISHED
tcp        0      0 mercury:51726           oam-m02a.blue.aol.c:aol ESTABLISHED
tcp        0      0 mercury:59239           63-217-20-68.sdsl.c:www ESTABLISHED
tcp        0      0 mercury:59235           63-217-20-68.sdsl.c:www ESTABLISHED
tcp        0      0 mercury:34087           h-207-148-159-24.ge:www ESTABLISHED
tcp        0      0 mercury:59237           63-217-20-68.sdsl.c:www ESTABLISHED
tcp        0      0 mercury:37720           admin-d03a.blue.aol:aol ESTABLISHED
tcp        0      0 mercury:59238           63-217-20-68.sdsl.c:www ESTABLISHED
tcp        0      0 mercury:41381           home:www                ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  14     [ ]         DGRAM                    14900    /dev/log
unix  2      [ ]         DGRAM                    6254     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    6388     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    15794    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     206962   /var/run/avahi-daemon/socket
unix  3      [ ]         STREAM     CONNECTED     206961   
unix  3      [ ]         STREAM     CONNECTED     141401   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     141400   
unix  3      [ ]         STREAM     CONNECTED     78939    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     78938    
unix  3      [ ]         STREAM     CONNECTED     69050    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     69049    
unix  3      [ ]         STREAM     CONNECTED     69046    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     69045    
unix  3      [ ]         STREAM     CONNECTED     69041    /tmp/.ICE-unix/dcop7254-1215301495
unix  3      [ ]         STREAM     CONNECTED     69040    
unix  3      [ ]         STREAM     CONNECTED     69033    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     69032    
unix  3      [ ]         STREAM     CONNECTED     68129    /tmp/ksocket-hyperhacker/klauncherIGKv4b.slave-socket
unix  3      [ ]         STREAM     CONNECTED     68128    
unix  3      [ ]         STREAM     CONNECTED     57348    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     57347    
unix  3      [ ]         STREAM     CONNECTED     57346    
unix  3      [ ]         STREAM     CONNECTED     57345    
unix  3      [ ]         STREAM     CONNECTED     57332    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     57331    
unix  3      [ ]         STREAM     CONNECTED     42504    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     42503    
unix  3      [ ]         STREAM     CONNECTED     42456    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     42455    
unix  3      [ ]         STREAM     CONNECTED     34519    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     34518    
unix  3      [ ]         STREAM     CONNECTED     34500    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     34499    
unix  3      [ ]         STREAM     CONNECTED     33090    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     33089    
unix  3      [ ]         STREAM     CONNECTED     23266    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     23265    
unix  3      [ ]         STREAM     CONNECTED     23264    /tmp/orbit-hyperhacker/linc-1cc2-0-228a04ee55ffa
unix  3      [ ]         STREAM     CONNECTED     23263    
unix  3      [ ]         STREAM     CONNECTED     23260    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     23259    
unix  3      [ ]         STREAM     CONNECTED     23255    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     23254    
unix  3      [ ]         STREAM     CONNECTED     22317    
unix  3      [ ]         STREAM     CONNECTED     22316    
unix  3      [ ]         STREAM     CONNECTED     22315    
unix  3      [ ]         STREAM     CONNECTED     22314    
unix  3      [ ]         STREAM     CONNECTED     22313    
unix  3      [ ]         STREAM     CONNECTED     22312    
unix  2      [ ]         STREAM     CONNECTED     22274    
unix  2      [ ]         DGRAM                    22260    
unix  2      [ ]         STREAM     CONNECTED     22246    
unix  3      [ ]         STREAM     CONNECTED     22237    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     22236    
unix  3      [ ]         STREAM     CONNECTED     22235    /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     22234    
unix  3      [ ]         STREAM     CONNECTED     22225    /tmp/.ICE-unix/dcop7254-1215301495
unix  3      [ ]         STREAM     CONNECTED     22224    
unix  3      [ ]         STREAM     CONNECTED     22199    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22198    
unix  3      [ ]         STREAM     CONNECTED     22196    /tmp/.ICE-unix/dcop7254-1215301495
unix  3      [ ]         STREAM     CONNECTED     22195    
unix  3      [ ]         STREAM     CONNECTED     22186    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22185    
unix  3      [ ]         STREAM     CONNECTED     22176    /tmp/.ICE-unix/dcop7254-1215301495
unix  3      [ ]         STREAM     CONNECTED     22175    
unix  3      [ ]         STREAM     CONNECTED     22173    
unix  3      [ ]         STREAM     CONNECTED     22172    
unix  3      [ ]         STREAM     CONNECTED     22113    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     22112    
unix  3      [ ]         STREAM     CONNECTED     22111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22110    
unix  2      [ ]         STREAM     CONNECTED     22105    
unix  3      [ ]         STREAM     CONNECTED     22089    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22088    
unix  3      [ ]         STREAM     CONNECTED     21498    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     21497    
unix  3      [ ]         STREAM     CONNECTED     21489    /tmp/orbit-hyperhacker/linc-1c18-0-6c55aa855a2d
unix  3      [ ]         STREAM     CONNECTED     21488    
unix  3      [ ]         STREAM     CONNECTED     21485    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     21484    
unix  3      [ ]         STREAM     CONNECTED     21481    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     21480    
unix  3      [ ]         STREAM     CONNECTED     21476    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21475    
unix  3      [ ]         STREAM     CONNECTED     21351    /tmp/orbit-hyperhacker/linc-1c10-0-1638eb81399f5
unix  3      [ ]         STREAM     CONNECTED     21350    
unix  3      [ ]         STREAM     CONNECTED     21347    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     21346    
unix  3      [ ]         STREAM     CONNECTED     21342    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     21341    
unix  3      [ ]         STREAM     CONNECTED     20779    
unix  3      [ ]         STREAM     CONNECTED     20778    
unix  3      [ ]         STREAM     CONNECTED     20772    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20771    
unix  3      [ ]         STREAM     CONNECTED     20768    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     20767    
unix  3      [ ]         STREAM     CONNECTED     20680    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     20679    
unix  3      [ ]         STREAM     CONNECTED     20650    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20649    
unix  3      [ ]         STREAM     CONNECTED     20271    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20270    
unix  3      [ ]         STREAM     CONNECTED     20233    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20232    
unix  3      [ ]         STREAM     CONNECTED     20115    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20114    
unix  3      [ ]         STREAM     CONNECTED     20111    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     20110    
unix  3      [ ]         STREAM     CONNECTED     20041    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     20040    
unix  3      [ ]         STREAM     CONNECTED     20038    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20037    
unix  3      [ ]         STREAM     CONNECTED     19941    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19940    
unix  3      [ ]         STREAM     CONNECTED     19933    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19932    
unix  3      [ ]         STREAM     CONNECTED     19922    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19921    
unix  3      [ ]         STREAM     CONNECTED     19918    /tmp/orbit-hyperhacker/linc-1b35-0-55aa5008985ec
unix  3      [ ]         STREAM     CONNECTED     19917    
unix  3      [ ]         STREAM     CONNECTED     19914    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     19913    
unix  3      [ ]         STREAM     CONNECTED     19905    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19904    
unix  3      [ ]         STREAM     CONNECTED     19903    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19902    
unix  3      [ ]         STREAM     CONNECTED     19895    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19894    
unix  3      [ ]         STREAM     CONNECTED     19887    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19886    
unix  3      [ ]         STREAM     CONNECTED     19845    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19844    
unix  3      [ ]         STREAM     CONNECTED     19837    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19834    
unix  3      [ ]         STREAM     CONNECTED     19823    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19822    
unix  3      [ ]         STREAM     CONNECTED     19807    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19806    
unix  3      [ ]         STREAM     CONNECTED     19799    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19798    
unix  2      [ ]         DGRAM                    19797    
unix  3      [ ]         STREAM     CONNECTED     19781    /tmp/orbit-hyperhacker/linc-1b27-0-6abce6c1ace51
unix  3      [ ]         STREAM     CONNECTED     19780    
unix  3      [ ]         STREAM     CONNECTED     19777    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     19776    
unix  3      [ ]         STREAM     CONNECTED     19753    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19752    
unix  3      [ ]         STREAM     CONNECTED     19761    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19736    
unix  3      [ ]         STREAM     CONNECTED     19731    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19726    
unix  3      [ ]         STREAM     CONNECTED     19730    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19722    
unix  3      [ ]         STREAM     CONNECTED     19653    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19652    
unix  3      [ ]         STREAM     CONNECTED     19610    /tmp/orbit-hyperhacker/linc-1b0c-0-7ccb673729faf
unix  3      [ ]         STREAM     CONNECTED     19609    
unix  3      [ ]         STREAM     CONNECTED     19608    /tmp/orbit-hyperhacker/linc-1b12-0-60fa2bc8c84ed
unix  3      [ ]         STREAM     CONNECTED     19607    
unix  3      [ ]         STREAM     CONNECTED     19575    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19574    
unix  3      [ ]         STREAM     CONNECTED     19451    /tmp/orbit-hyperhacker/linc-1b0c-0-7ccb673729faf
unix  3      [ ]         STREAM     CONNECTED     19450    
unix  3      [ ]         STREAM     CONNECTED     19447    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     19446    
unix  3      [ ]         STREAM     CONNECTED     19442    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19441    
unix  3      [ ]         STREAM     CONNECTED     19377    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19376    
unix  3      [ ]         STREAM     CONNECTED     19373    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19372    
unix  3      [ ]         STREAM     CONNECTED     19365    /tmp/orbit-hyperhacker/linc-1b04-0-f523658bafce
unix  3      [ ]         STREAM     CONNECTED     19364    
unix  3      [ ]         STREAM     CONNECTED     19361    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     19360    
unix  3      [ ]         STREAM     CONNECTED     19329    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19328    
unix  3      [ ]         STREAM     CONNECTED     19322    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19321    
unix  3      [ ]         STREAM     CONNECTED     19318    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19317    
unix  3      [ ]         STREAM     CONNECTED     19303    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19302    
unix  3      [ ]         STREAM     CONNECTED     19300    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19299    
unix  3      [ ]         STREAM     CONNECTED     19293    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19292    
unix  3      [ ]         STREAM     CONNECTED     19290    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19289    
unix  3      [ ]         STREAM     CONNECTED     19281    @/tmp/fam-hyperhacker-
unix  3      [ ]         STREAM     CONNECTED     19280    
unix  3      [ ]         STREAM     CONNECTED     19279    @/tmp/dbus-BrEAkdkEMR
unix  3      [ ]         STREAM     CONNECTED     19278    
unix  3      [ ]         STREAM     CONNECTED     19277    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19276    
unix  3      [ ]         STREAM     CONNECTED     19274    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19273    
unix  3      [ ]         STREAM     CONNECTED     19268    
unix  3      [ ]         STREAM     CONNECTED     19267    
unix  3      [ ]         STREAM     CONNECTED     19254    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19253    
unix  3      [ ]         STREAM     CONNECTED     19250    /tmp/.ICE-unix/6703
unix  3      [ ]         STREAM     CONNECTED     19249    
unix  3      [ ]         STREAM     CONNECTED     19246    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19245    
unix  3      [ ]         STREAM     CONNECTED     19243    @/tmp/fam-hyperhacker-
unix  3      [ ]         STREAM     CONNECTED     19242    
unix  3      [ ]         STREAM     CONNECTED     19232    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19231    
unix  3      [ ]         STREAM     CONNECTED     19215    /tmp/orbit-hyperhacker/linc-1a2f-0-2e97a5a38ebc8
unix  3      [ ]         STREAM     CONNECTED     19214    
unix  3      [ ]         STREAM     CONNECTED     19211    /tmp/orbit-hyperhacker/linc-1aed-0-18607223f011e
unix  3      [ ]         STREAM     CONNECTED     19210    
unix  3      [ ]         STREAM     CONNECTED     19090    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19089    
unix  3      [ ]         STREAM     CONNECTED     19087    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19086    
unix  3      [ ]         STREAM     CONNECTED     19063    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19062    
unix  3      [ ]         STREAM     CONNECTED     19053    /tmp/scim-panel-socket:0-hyperhacker
unix  3      [ ]         STREAM     CONNECTED     19052    
unix  3      [ ]         STREAM     CONNECTED     19049    /tmp/scim-helper-manager-socket-hyperhacker
unix  3      [ ]         STREAM     CONNECTED     19048    
unix  3      [ ]         STREAM     CONNECTED     19039    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19038    
unix  3      [ ]         STREAM     CONNECTED     19037    /tmp/scim-socket-frontend-hyperhacker
unix  3      [ ]         STREAM     CONNECTED     19036    
unix  3      [ ]         STREAM     CONNECTED     19030    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19029    
unix  3      [ ]         STREAM     CONNECTED     19028    /tmp/scim-socket-frontend-hyperhacker
unix  3      [ ]         STREAM     CONNECTED     19027    
unix  3      [ ]         STREAM     CONNECTED     19026    /tmp/scim-socket-frontend-hyperhacker
unix  3      [ ]         STREAM     CONNECTED     19025    
unix  3      [ ]         STREAM     CONNECTED     18001    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18000    
unix  2      [ ]         DGRAM                    17855    
unix  3      [ ]         STREAM     CONNECTED     17631    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17630    
unix  3      [ ]         STREAM     CONNECTED     17261    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     17260    
unix  2      [ ]         DGRAM                    17149    
unix  3      [ ]         STREAM     CONNECTED     17132    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     17131    
unix  5      [ ]         STREAM     CONNECTED     17632    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17123    
unix  3      [ ]         STREAM     CONNECTED     16916    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16915    
unix  2      [ ]         DGRAM                    16914    
unix  3      [ ]         STREAM     CONNECTED     16883    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16882    
unix  2      [ ]         DGRAM                    16881    
unix  3      [ ]         STREAM     CONNECTED     16836    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16835    
unix  2      [ ]         DGRAM                    16831    
unix  3      [ ]         STREAM     CONNECTED     16748    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16734    
unix  3      [ ]         STREAM     CONNECTED     16733    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16732    
unix  3      [ ]         STREAM     CONNECTED     16707    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16693    
unix  3      [ ]         STREAM     CONNECTED     16692    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16691    
unix  3      [ ]         STREAM     CONNECTED     16679    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16665    
unix  3      [ ]         STREAM     CONNECTED     16664    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16663    
unix  3      [ ]         STREAM     CONNECTED     16651    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16637    
unix  3      [ ]         STREAM     CONNECTED     16636    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16635    
unix  3      [ ]         STREAM     CONNECTED     16623    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16609    
unix  3      [ ]         STREAM     CONNECTED     16608    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16607    
unix  3      [ ]         STREAM     CONNECTED     16357    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     16345    
unix  3      [ ]         STREAM     CONNECTED     16035    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     16034    
unix  3      [ ]         STREAM     CONNECTED     15990    @/var/run/hald/dbus-EV5XsG6Uwn
unix  3      [ ]         STREAM     CONNECTED     15989    
unix  3      [ ]         STREAM     CONNECTED     15785    @/var/run/hald/dbus-c0Ra16PE3r
unix  3      [ ]         STREAM     CONNECTED     15784    
unix  3      [ ]         STREAM     CONNECTED     15765    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15764    
unix  3      [ ]         STREAM     CONNECTED     15744    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15743    
unix  3      [ ]         STREAM     CONNECTED     15718    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15717    
unix  2      [ ]         DGRAM                    15716    
unix  2      [ ]         DGRAM                    15308    
unix  3      [ ]         STREAM     CONNECTED     15167    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15166    
unix  3      [ ]         STREAM     CONNECTED     15161    
unix  3      [ ]         STREAM     CONNECTED     15160    
unix  2      [ ]         DGRAM                    15158    
unix  3      [ ]         STREAM     CONNECTED     15066    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15065    
unix  3      [ ]         STREAM     CONNECTED     15057    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15056    
unix  3      [ ]         STREAM     CONNECTED     15027    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15026    
unix  2      [ ]         DGRAM                    15022    
unix  3      [ ]         STREAM     CONNECTED     15001    
unix  3      [ ]         STREAM     CONNECTED     15000    
unix  2      [ ]         DGRAM                    14977    
```What is "BrEAkdkEMR"? It doesn't show up on Google and there's no such file in /tmp.

---

