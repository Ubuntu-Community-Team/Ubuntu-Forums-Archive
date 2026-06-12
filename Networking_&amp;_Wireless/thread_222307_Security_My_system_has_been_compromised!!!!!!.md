---
title: "Security: My system has been compromised!!!!!!"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2006-07-24
Guys... seriously, i think someone logs in my PC. I installed linux a couple of days ago and i have not put anything apart from the latest repositories from ubuntuguide.org and :
mplayer
beep media player
webmin
acrobat
amsn
azureus
downloader
amule
gftp 
VNCserver (not installed yet)

Everytime i log in, or i enable my network connection my mouse is moving left and right, it closes windows, and behaves like there is someone on my system!!!!! 
I am really scared as i don't know how to confirm that someone is in. 

If i was under windows i would run a netstat to see what ports i have open but in linux i don't get all these services:

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:44543         localhost:39596         ESTABLISHED
tcp        0      0 192.168.0.2:34288       by2m6-cs12.msgr.ho:1863 ESTABLISHED
tcp        0      0 192.168.0.111:59890     by1msg5082517.phx.:1863 ESTABLISHED
tcp        0      0 192.168.0.2:40466       66.249.91.99:www        ESTABLISHED
tcp        0      0 localhost:39596         localhost:44543         ESTABLISHED
tcp        0      0 192.168.0.2:34439       by2msg1231714.phx.:1863 ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    5196     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    11556    @/org/freedesktop/hal/udev_event
unix  11     [ ]         DGRAM                    10393    /dev/log
unix  3      [ ]         STREAM     CONNECTED     40880
unix  3      [ ]         STREAM     CONNECTED     40879
unix  3      [ ]         STREAM     CONNECTED     40877    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     40876
unix  3      [ ]         STREAM     CONNECTED     40874    /tmp/orbit-genesis/linc-37dd-0-3bea3e7030bbe
unix  3      [ ]         STREAM     CONNECTED     40873
unix  3      [ ]         STREAM     CONNECTED     40872    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     40871
unix  3      [ ]         STREAM     CONNECTED     40870    /tmp/orbit-genesis/linc-37dd-0-3bea3e7030bbe
unix  3      [ ]         STREAM     CONNECTED     40869
unix  3      [ ]         STREAM     CONNECTED     40866    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     40865
unix  3      [ ]         STREAM     CONNECTED     40862    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     40861
unix  3      [ ]         STREAM     CONNECTED     40857    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     40856
unix  3      [ ]         STREAM     CONNECTED     39564    /tmp/orbit-genesis/linc-36e0-0-32a2d86693444
unix  3      [ ]         STREAM     CONNECTED     39563
unix  3      [ ]         STREAM     CONNECTED     39562    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     39561
unix  3      [ ]         STREAM     CONNECTED     39559    /tmp/orbit-genesis/linc-36e0-0-32a2d86693444
unix  3      [ ]         STREAM     CONNECTED     39558
unix  3      [ ]         STREAM     CONNECTED     39555    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     39554
unix  3      [ ]         STREAM     CONNECTED     39551    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     39550
unix  3      [ ]         STREAM     CONNECTED     39546    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     39545
unix  3      [ ]         STREAM     CONNECTED     35303    /tmp/orbit-genesis/linc-2e13-0-6c74a043c83f2
unix  3      [ ]         STREAM     CONNECTED     35302
unix  3      [ ]         STREAM     CONNECTED     35301    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     35300
unix  3      [ ]         STREAM     CONNECTED     35298    /tmp/orbit-genesis/linc-2e13-0-6c74a043c83f2
unix  3      [ ]         STREAM     CONNECTED     35297
unix  3      [ ]         STREAM     CONNECTED     35296    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     35293
unix  3      [ ]         STREAM     CONNECTED     33486    /tmp/orbit-genesis/linc-3149-0-c5d6169aa55e
unix  3      [ ]         STREAM     CONNECTED     33485
unix  3      [ ]         STREAM     CONNECTED     33482    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     33481
unix  3      [ ]         STREAM     CONNECTED     33479    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     33478
unix  3      [ ]         STREAM     CONNECTED     33038    /tmp/orbit-genesis/linc-30d9-0-bd4eaeee33eb
unix  3      [ ]         STREAM     CONNECTED     33037
unix  3      [ ]         STREAM     CONNECTED     33034    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     33033
unix  3      [ ]         STREAM     CONNECTED     33021    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     33020
unix  3      [ ]         STREAM     CONNECTED     30394    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     30393
unix  3      [ ]         STREAM     CONNECTED     15012    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15011
unix  3      [ ]         STREAM     CONNECTED     13710    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13709
unix  3      [ ]         STREAM     CONNECTED     13708    @/tmp/dbus-b5axr9Ksmpunix  3      [ ]         STREAM     CONNECTED     13707
unix  3      [ ]         STREAM     CONNECTED     13706    /tmp/orbit-genesis/linc-13f2-0-5cea10225b358
unix  3      [ ]         STREAM     CONNECTED     13705
unix  3      [ ]         STREAM     CONNECTED     13702    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13701
unix  3      [ ]         STREAM     CONNECTED     13697    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13696
unix  3      [ ]         STREAM     CONNECTED     13651    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13650
unix  3      [ ]         STREAM     CONNECTED     13649    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13648
unix  3      [ ]         STREAM     CONNECTED     13647    /tmp/orbit-genesis/linc-13e7-0-3a18fe0522b10
unix  3      [ ]         STREAM     CONNECTED     13646
unix  3      [ ]         STREAM     CONNECTED     13641    /tmp/orbit-genesis/linc-13e7-0-3a18fe0522b10
unix  3      [ ]         STREAM     CONNECTED     13640
unix  3      [ ]         STREAM     CONNECTED     13639    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13638
unix  3      [ ]         STREAM     CONNECTED     13637    /tmp/orbit-genesis/linc-13e7-0-3a18fe0522b10
unix  3      [ ]         STREAM     CONNECTED     13636
unix  3      [ ]         STREAM     CONNECTED     13633    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13632
unix  3      [ ]         STREAM     CONNECTED     13628    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13627
unix  3      [ ]         STREAM     CONNECTED     13618    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13617
unix  3      [ ]         STREAM     CONNECTED     13616    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13615
unix  3      [ ]         STREAM     CONNECTED     13614    /tmp/orbit-genesis/linc-13e5-0-14380b69855f9
unix  3      [ ]         STREAM     CONNECTED     13613
unix  3      [ ]         STREAM     CONNECTED     13606    /tmp/orbit-genesis/linc-13e5-0-14380b69855f9
unix  3      [ ]         STREAM     CONNECTED     13605
unix  3      [ ]         STREAM     CONNECTED     13604    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13603
unix  3      [ ]         STREAM     CONNECTED     13602    /tmp/orbit-genesis/linc-13e5-0-14380b69855f9
unix  3      [ ]         STREAM     CONNECTED     13601
unix  3      [ ]         STREAM     CONNECTED     13598    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13597
unix  3      [ ]         STREAM     CONNECTED     13593    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13592
unix  3      [ ]         STREAM     CONNECTED     13583    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13582
unix  3      [ ]         STREAM     CONNECTED     13574    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13573
unix  3      [ ]         STREAM     CONNECTED     13572    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     13571
unix  3      [ ]         STREAM     CONNECTED     13566    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13565
unix  3      [ ]         STREAM     CONNECTED     13564    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13563
unix  3      [ ]         STREAM     CONNECTED     13562    /tmp/orbit-genesis/linc-13d3-0-7a5e031d7f7e4
unix  3      [ ]         STREAM     CONNECTED     13561
unix  3      [ ]         STREAM     CONNECTED     13553    /tmp/mapping-genesis
unix  3      [ ]         STREAM     CONNECTED     13545
unix  3      [ ]         STREAM     CONNECTED     13543    /tmp/orbit-genesis/linc-13d3-0-7a5e031d7f7e4
unix  3      [ ]         STREAM     CONNECTED     13542
unix  3      [ ]         STREAM     CONNECTED     13541    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     13540
unix  3      [ ]         STREAM     CONNECTED     13537    /tmp/orbit-genesis/linc-13d3-0-7a5e031d7f7e4
unix  3      [ ]         STREAM     CONNECTED     13536
unix  3      [ ]         STREAM     CONNECTED     13535    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13534
unix  3      [ ]         STREAM     CONNECTED     13533    /tmp/orbit-genesis/linc-13d3-0-7a5e031d7f7e4
unix  3      [ ]         STREAM     CONNECTED     13532
unix  3      [ ]         STREAM     CONNECTED     13529    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13528
unix  3      [ ]         STREAM     CONNECTED     13524    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13523
unix  3      [ ]         STREAM     CONNECTED     13514    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13512
unix  3      [ ]         STREAM     CONNECTED     13471    /tmp/orbit-genesis/linc-13a3-0-43923d42e7662
unix  3      [ ]         STREAM     CONNECTED     13470
unix  3      [ ]         STREAM     CONNECTED     13477    /tmp/orbit-genesis/linc-1393-0-1c32a6fa7432e
unix  3      [ ]         STREAM     CONNECTED     13461
unix  3      [ ]         STREAM     CONNECTED     13469    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     13460
unix  3      [ ]         STREAM     CONNECTED     13457    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     13456
unix  3      [ ]         STREAM     CONNECTED     13455    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13454
unix  3      [ ]         STREAM     CONNECTED     13453    /tmp/orbit-genesis/linc-1393-0-1c32a6fa7432e
unix  3      [ ]         STREAM     CONNECTED     13452
unix  3      [ ]         STREAM     CONNECTED     13451    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13450
unix  3      [ ]         STREAM     CONNECTED     13442    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13441
unix  3      [ ]         STREAM     CONNECTED     13440    /tmp/orbit-genesis/linc-13be-0-2d5cf0733aaa0
unix  3      [ ]         STREAM     CONNECTED     13439
unix  3      [ ]         STREAM     CONNECTED     13436    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13435
unix  3      [ ]         STREAM     CONNECTED     13429    /tmp/orbit-genesis/linc-13b6-0-26434f3f32458
unix  3      [ ]         STREAM     CONNECTED     13428
unix  3      [ ]         STREAM     CONNECTED     13427    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13426
unix  3      [ ]         STREAM     CONNECTED     13425    /tmp/orbit-genesis/linc-13b6-0-26434f3f32458
unix  3      [ ]         STREAM     CONNECTED     13424
unix  3      [ ]         STREAM     CONNECTED     13421    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13420
unix  3      [ ]         STREAM     CONNECTED     13417    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13416
unix  3      [ ]         STREAM     CONNECTED     13412    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13411
unix  3      [ ]         STREAM     CONNECTED     13405    /tmp/orbit-genesis/linc-13a3-0-43923d42e7662
unix  3      [ ]         STREAM     CONNECTED     13404
unix  3      [ ]         STREAM     CONNECTED     13403    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13402
unix  3      [ ]         STREAM     CONNECTED     13399    @/tmp/dbus-b5axr9Ksmpunix  3      [ ]         STREAM     CONNECTED     13398
unix  3      [ ]         STREAM     CONNECTED     13397    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13396
unix  2      [ ]         DGRAM                    13395
unix  3      [ ]         STREAM     CONNECTED     13394    /tmp/orbit-genesis/linc-13b4-0-70fcfef487bbe
unix  3      [ ]         STREAM     CONNECTED     13393
unix  3      [ ]         STREAM     CONNECTED     13390    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13388
unix  3      [ ]         STREAM     CONNECTED     13385    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13384
unix  3      [ ]         STREAM     CONNECTED     13380    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13379
unix  3      [ ]         STREAM     CONNECTED     13376    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13375
unix  3      [ ]         STREAM     CONNECTED     13372    @/tmp/dbus-b5axr9Ksmpunix  3      [ ]         STREAM     CONNECTED     13371
unix  3      [ ]         STREAM     CONNECTED     13368    /tmp/orbit-genesis/linc-13ae-0-70fcfef4576c1
unix  3      [ ]         STREAM     CONNECTED     13367
unix  3      [ ]         STREAM     CONNECTED     13369    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13364
unix  3      [ ]         STREAM     CONNECTED     13357    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13356
unix  3      [ ]         STREAM     CONNECTED     13351    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13350
unix  3      [ ]         STREAM     CONNECTED     13346    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13345
unix  3      [ ]         STREAM     CONNECTED     13342    /tmp/orbit-genesis/linc-13a3-0-43923d42e7662
unix  3      [ ]         STREAM     CONNECTED     13340
unix  3      [ ]         STREAM     CONNECTED     13333    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13330
unix  3      [ ]         STREAM     CONNECTED     13323    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13322
unix  3      [ ]         STREAM     CONNECTED     13318    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13317
unix  3      [ ]         STREAM     CONNECTED     13309    @/tmp/dbus-b5axr9Ksmpunix  3      [ ]         STREAM     CONNECTED     13308
unix  3      [ ]         STREAM     CONNECTED     13306    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13305
unix  3      [ ]         STREAM     CONNECTED     13304    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13303
unix  3      [ ]         STREAM     CONNECTED     13302    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13301
unix  3      [ ]         STREAM     CONNECTED     13300    /tmp/orbit-genesis/linc-13a5-0-43923d429e2d5
unix  3      [ ]         STREAM     CONNECTED     13299
unix  3      [ ]         STREAM     CONNECTED     13296    /tmp/orbit-genesis/linc-13a1-0-43923d429bd8d
unix  3      [ ]         STREAM     CONNECTED     13295
unix  3      [ ]         STREAM     CONNECTED     13292    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13290
unix  3      [ ]         STREAM     CONNECTED     13287    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13286
unix  3      [ ]         STREAM     CONNECTED     13291    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13285
unix  3      [ ]         STREAM     CONNECTED     13282    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13281
unix  3      [ ]         STREAM     CONNECTED     13277    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13276
unix  3      [ ]         STREAM     CONNECTED     13272    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13271
unix  3      [ ]         STREAM     CONNECTED     13254    /tmp/.ICE-unix/4953
unix  3      [ ]         STREAM     CONNECTED     13253
unix  3      [ ]         STREAM     CONNECTED     13252    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13251
unix  3      [ ]         STREAM     CONNECTED     13250    /tmp/orbit-genesis/linc-139c-0-4ecf0cc8161
unix  3      [ ]         STREAM     CONNECTED     13249
unix  3      [ ]         STREAM     CONNECTED     13246    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13245
unix  3      [ ]         STREAM     CONNECTED     13231    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13230
unix  2      [ ]         STREAM                   13219
unix  3      [ ]         STREAM     CONNECTED     13217    /tmp/orbit-genesis/linc-1393-0-1c32a6fa7432e
unix  3      [ ]         STREAM     CONNECTED     13216
unix  3      [ ]         STREAM     CONNECTED     13213    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     13212
unix  3      [ ]         STREAM     CONNECTED     13208    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13207
unix  3      [ ]         STREAM     CONNECTED     13196    /tmp/orbit-genesis/linc-1359-0-64d8957080db9
unix  3      [ ]         STREAM     CONNECTED     13195
unix  3      [ ]         STREAM     CONNECTED     13194    /tmp/orbit-genesis/linc-1391-0-73998dd88257
unix  3      [ ]         STREAM     CONNECTED     13193
unix  3      [ ]         STREAM     CONNECTED     13155    /tmp/orbit-genesis/linc-1359-0-64d8957080db9
unix  3      [ ]         STREAM     CONNECTED     13154
unix  3      [ ]         STREAM     CONNECTED     13153    /tmp/orbit-genesis/linc-138c-0-75468e4464cac
unix  3      [ ]         STREAM     CONNECTED     12986
unix  2      [ ]         DGRAM                    12972
unix  3      [ ]         STREAM     CONNECTED     12966    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12965
unix  3      [ ]         STREAM     CONNECTED     12962    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12961
unix  3      [ ]         STREAM     CONNECTED     12960
unix  3      [ ]         STREAM     CONNECTED     12959
unix  2      [ ]         DGRAM                    12904
unix  2      [ ]         DGRAM                    12797
unix  2      [ ]         DGRAM                    12587
unix  3      [ ]         STREAM     CONNECTED     12584    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12583
unix  2      [ ]         DGRAM                    12577
unix  3      [ ]         STREAM     CONNECTED     12474    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12473
unix  3      [ ]         STREAM     CONNECTED     11937    @/tmp/hald-local/dbus-NTqS52kSwD
unix  3      [ ]         STREAM     CONNECTED     11936
unix  3      [ ]         STREAM     CONNECTED     11927    @/tmp/hald-local/dbus-NTqS52kSwD
unix  3      [ ]         STREAM     CONNECTED     11926
unix  3      [ ]         STREAM     CONNECTED     11881    @/tmp/hald-local/dbus-NTqS52kSwD
unix  3      [ ]         STREAM     CONNECTED     11876
unix  3      [ ]         STREAM     CONNECTED     11770    @/tmp/hald-local/dbus-NTqS52kSwD
unix  3      [ ]         STREAM     CONNECTED     11765
unix  3      [ ]         STREAM     CONNECTED     11731    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     11730
unix  3      [ ]         STREAM     CONNECTED     11734    @/tmp/hald-local/dbus-NTqS52kSwD
unix  3      [ ]         STREAM     CONNECTED     11725
unix  3      [ ]         STREAM     CONNECTED     11551    @/tmp/hald-runner/dbus-BQilCQYpwh
unix  3      [ ]         STREAM     CONNECTED     11550
unix  3      [ ]         STREAM     CONNECTED     11527
unix  3      [ ]         STREAM     CONNECTED     11526
unix  3      [ ]         STREAM     CONNECTED     11502    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     11501
unix  2      [ ]         DGRAM                    11498
unix  2      [ ]         DGRAM                    11349
unix  4      [ ]         STREAM     CONNECTED     12869    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11323
unix  2      [ ]         DGRAM                    10446
genesis@Ubuntuj:~$

```

I would run a process monitor to see what services and programs are running but as i am a n00b in linux i have no idea what everything is.

```
genesis@Ubuntuj:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  116 ?        00:00:00 pdflush
  117 ?        00:00:00 pdflush
  119 ?        00:00:00 aio/0
  118 ?        00:00:00 kswapd0
  706 ?        00:00:00 kseriod
 1869 ?        00:00:00 khubd
 1989 ?        00:00:00 kjournald
 2215 ?        00:00:00 udevd
 3071 ?        00:00:00 shpchpd_event
 3081 ?        00:00:00 kgameportd
 4023 ?        00:00:00 acpid
 4116 ?        00:00:00 syslogd
 4142 ?        00:00:00 dd
 4144 ?        00:00:00 klogd
 4463 ?        00:00:00 gdm
 4478 ?        00:00:00 gdm
 4497 tty7     00:05:03 Xorg
 4506 ?        00:00:00 hpiod
 4520 ?        00:00:00 python
 4582 ?        00:00:24 atieventsd
 4596 ?        00:00:00 dbus-daemon
 4611 ?        00:00:01 hald
 4612 ?        00:00:00 hald-runner
 4617 ?        00:00:00 hald-addon-acpi
 4626 ?        00:00:00 hald-addon-keyb
 4676 ?        00:00:00 hald-addon-keyb
 4686 ?        00:00:01 hald-addon-stor
 4689 ?        00:00:02 hald-addon-stor
 4774 ?        00:00:00 hcid
 4778 ?        00:00:00 sdpd
 4788 ?        00:00:00 krfcommd
 4801 ?        00:00:00 mdadm
 4835 ?        00:00:00 atd
 4848 ?        00:00:00 cron
 4911 ?        00:00:00 miniserv.pl
 4927 tty1     00:00:00 getty
 4928 tty2     00:00:00 getty
 4929 tty3     00:00:00 getty
 4930 tty4     00:00:00 getty
 4931 tty5     00:00:00 getty
 4932 tty6     00:00:00 getty
 4953 ?        00:00:00 x-session-manag
 4998 ?        00:00:00 ssh-agent
 5001 ?        00:00:00 dbus-launch
 5002 ?        00:00:00 dbus-daemon
 5004 ?        00:00:01 gconfd-2
 5007 ?        00:00:00 gnome-keyring-d
 5009 ?        00:00:00 bonobo-activati
 5011 ?        00:00:06 gnome-settings-
 5013 ?        00:00:00 esd
 5020 ?        00:01:08 metacity
 5025 ?        00:01:10 gnome-panel
 5027 ?        00:01:16 nautilus
 5031 ?        00:00:00 gnome-volume-ma
 5038 ?        00:00:01 update-notifier
 5046 ?        00:00:00 gnome-cups-icon
 5054 ?        00:00:00 gnome-vfs-daemo
 5068 ?        00:00:01 gnome-power-man
 5075 ?        00:00:01 trashapplet
 5080 ?        00:00:00 mapping-daemon
 5093 ?        00:00:00 clock-applet
 5095 ?        00:00:01 mixer_applet2
 5111 ?        00:00:07 gnome-screensav
 5394 ?        00:02:20 wish
 5635 ?        00:00:00 firefox-bin <defunct>
10586 ?        00:00:00 miniserv.pl
11795 ?        00:00:05 beep-media-play
12505 ?        00:02:08 firefox-bin
12617 ?        00:00:00 at-spi-registry
13233 ?        00:00:00 beep-media-play
14048 ?        00:00:00 evolution-excha
14301 ?        00:00:06 gnome-terminal
14302 ?        00:00:00 gnome-pty-helpe
14303 pts/0    00:00:00 bash
14753 pts/0    00:00:00 ps

```



Can you guys see anything here that shouldn't be open?
OMG i under a lot of stress....
Please note that i am behind a NATed windows XP machine so it looks kind of hard to get hijacked with that ease considering that the guy has to penetrate two systems to get to me. 
Am i saying anything wrong? Can it just be the mouse and keyboard drivers?

Heeeeeeeelp! :(

---

### Post by T700 on 2006-07-24
Considering that the installation is new, I'd just save my data, format and reinstall.  You might also very carefully check the Windows box to see if it is infected/zombied/rooted or god knows what else they're prone to.  If it is, having your Linux machine connect through it is like running naked on the internet.

Paul

---

### Post by dbott67 on 2006-07-24
What happens if you leave it disconnected from the network and use it?  Any weird happenings?

---

### Post by onlythetim on 2006-07-24
you can use the w command to see if anyone is logged into a session on your system.


windows xp won't protect you.  Actually, it probably makes you more prone.  What is your network configuration?  Are you behind any firewalls (other than windows?  i.e. do you have a router with a hardware firewall?)

Find a howto on iptables, and set up a good firewall for yourself.  Until it's set up, try commenting out everything in /etc/hosts.allow, and editting hosts.deny to block some stuff.  If you are really desperate, try adding
ALL : ALL

however, that might not let you do anything on the web....


I'm no expert on this, but these are the first things I would try.

---

### Post by djgenesis on 2006-07-25
Thanks for the replies all.

**T700,** i don't think my windows machine has been compromised and i am running a strong antivirus on it. I have something like 6 PC on this LAN and none of these ever occured anything weird. 

**Dbott67** : I have to try this and let you know. Although it doesn't always happen when i am online. 
[B]
onlythetim:[/B] Thanks for the w command tip friend. I will give it a go. In this case, i don't think that a firewall will solve anything as i don't think it is a trojan or a worm.

My topology:
```

INTERNET
|
|
V
NAT ----------------------->PC1 (Ubuntu)
(Win XP SP2 )              IP: 192.168.0.2
192.168.0.1                GTW: 192.168.0.1
xxx.xxx.xxx.xxx            DNS: 192.168.0.1
|
|
V
PC2 (winXP):
IP:192.168.0.3
GTW:192.168.0.1
DNS:192.168.0.1
---->The rest of the PCs are configured with the same manner<----

```
It is extremelly difficult for someone to plant something on my server at home and NOT target my other windows machines, but have a cross platform worm/trojan/virus that infects only ubuntu.

Therefore i think there might be something inside my processes that enables the attacker to acquire my IP and connect to my machine. 
Thats why i am asking for you guys to pinpoint anything weird on my services. 
Note that i switched off the "remote destop" feature. 

Thanks again for your replies.

Genxx

---

### Post by mpvano on 2006-07-25
I've never heard of a hack that moves your mouse around. Why would anyone write such a thing?

However, there are all kinds of system bugs and misconfigurations that can cause the behavior you describe. That's a lot more likely explanation.

Here are a couple of things that have done that to me:

- misconfigured mouse settings (there's more than one protocol - if you set the wrong one the mouse often goes nuts just as described).

- misconfigured touchpad or other nonstandard pointer device. Many people would describe the default touchpad settings shipped with x.org as acting that way on some machines. Mine was pretty unusable until I reconfigured it properly. Especially under high humidity!

- Processor too slow or stuck background process, along with slow mouse device. I see behavior like this all the time on machines that are too slow for modern X-windows systems. All it takes is a busy background task to make the mouse jump all over instead of moving properly. I think gnome/gtk applications don't handle the mouse properly. This shouldn't happen. It's particularly bad if your slow CPU also has a slow mouse interface (i.e. serial).

- buggy ACPI/APM interface via keyboard controller. A recent update made almost everyone running an older, slower VAIO, and some other notebooks share your experience. It was quickly superceded by another update that fixed the problem. Some older machines send battery and other system status information via magic codes through the keyboard/mouse interface chip. It was never a good idea, but when it goes wrong, lookout...

Hope this gives some more plausible explanations for your scare. As I said, I've never heard of a hack that worked that way. What would be the point?

In any event, a reinstall may be the simplest solution.

Mario

---

### Post by ltolledo on 2006-07-26
Hello, I hope this helps,

The same thing happens to my Linux installations (FC4, U5.1, U6.06) whenever I change over from my windows PC to Linux PC via a KVM switch. I cant control the darn mouse (moves erratic and closes/opens apps). To top off that, the Linux PC is not even connected to the network (physically not connected)

My countermeasure was to provide separate keyboard, mouse and monitor for the  Linux PC.

---

### Post by Liam on 2006-07-26
> **ltolledo said:**
> Hello, I hope this helps,

The same thing happens to my Linux installations (FC4, U5.1, U6.06) whenever I change over from my windows PC to Linux PC via a KVM switch. I cant control the darn mouse (moves erratic and closes/opens apps). To top off that, the Linux PC is not even connected to the network (physically not connected)

My countermeasure was to provide separate keyboard, mouse and monitor for the  Linux PC.

What he said.

I've got a cheapo bus-powered 2-port KVM. If I reboot one machine, flip over the the other, and enter some kind of input, invariably the mouse input on my Linux machine will go crazy.

Try rebooting *both* machines, and let them come up completely before you touch anything. In the future, if you need to reboot the either box, let it cycle completely before you switch over and start messing with the other one.

---

### Post by djgenesis on 2006-07-27
Hello guys, thanks for all your concerns. I haven't got a KVM switch installed though. Its a dual boot win-lin machine. 

These look moslty appealing..
> 
- misconfigured mouse settings (there's more than one protocol - if you set the wrong one the mouse often goes nuts just as described).

- misconfigured touchpad or other nonstandard pointer device. Many people would describe the default touchpad settings shipped with x.org as acting that way on some machines. Mine was pretty unusable until I reconfigured it properly. Especially under high humidity!

- Processor too slow or stuck background process, along with slow mouse device. I see behavior like this all the time on machines that are too slow for modern X-windows systems. All it takes is a busy background task to make the mouse jump all over instead of moving properly. I think gnome/gtk applications don't handle the mouse properly. This shouldn't happen. It's particularly bad if your slow CPU also has a slow mouse interface (i.e. serial).

- buggy ACPI/APM interface via keyboard controller. A recent update made almost everyone running an older, slower VAIO, and some other notebooks share your experience. It was quickly superceded by another update that fixed the problem. Some older machines send battery and other system status information via magic codes through the keyboard/mouse interface chip. It was never a good idea, but when it goes wrong, lookout...



Trojan Horses, are indeed hacks like that. They open CD trays and mouve the cursors around apart from controlling your system. 

Where should i look for the misconfigured mouse? Xorg.conf? I have a destop not a laptop and in my xorg.conf there is alternative user input. Should i delete it ?


A reinstall is not an option. The only good thing windows has taught me is: "Never format your drive for a simple problem. There is NOTHING that can't be fixed" 
Besides.... i don't know how to keep backups yet :oops:

---

### Post by Indras on 2006-07-30
A buddy of mine had this happen to him in Windows.  He immediately logged off the internet (using dialup) and the problem didn't go away.  Turns out his new wireless mouse was getting interference from another wireless mouse in the next apartment over.

You don't happen to be using a wireless mouse, do you?

---

### Post by T700 on 2006-07-30
> **djgenesis said:**
> A reinstall is not an option. The only good thing windows has taught me is: "Never format your drive for a simple problem. There is NOTHING that can't be fixed" 
Besides.... i don't know how to keep backups yet :oops:

Windows taught you wrong.  If a box is rooted or otherwise compromised at that level, a format and reinstall is often the solution of choice, as it is never possible to fully trust that installation again. 

Paul

---

### Post by F Cocquyt on 2006-07-30
I'm having the same problem at the moment. It's very recently showed up. And on my machine it's not a fresh install (working with ubuntu since warthy). There is no Windows installed on my machine and since yesterday there seems to be something going on with my mousepointer. it just jumps a few pixels from right to the left, from the bottom to the top. It's very annoying, but I haven't had time to look into it. 
Perhaps my touchpad is broken? (I'am working on a laptop with a touchpad)

---

### Post by djgenesis on 2006-07-30
Nope, it turns out that it wasn't haedware related.
I changed to KDE gui today and it stopped. Probably there was something in Gnome that was making it happen.

Thanks all for your replies 
Greatly appreciated.

Genxx

---

