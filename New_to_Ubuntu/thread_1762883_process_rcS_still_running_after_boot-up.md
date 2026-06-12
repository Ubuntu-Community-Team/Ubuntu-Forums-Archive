---
title: "process rcS still running after boot-up"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by john009 on 2011-05-19
Ubuntu 10.04.  First noticed that cpu usage was always at 100%. After 'googling' it and following some advice on how to identify what process is using the resource (my System Monitor did not have 'all processes' ticked), I identified rcS as the culprit (with the 'top' command).  Further 'googling' the problem ('process rcS still running after boot-up' and variations thereof) didn't help much, but did lead me to understand that the process should terminate and not be running after boot-up (have I understood that correctly?). Killing the process restores cpu usage to normal levels.

The problem may be linked to the fact that neither apache2 or the firebird2.1 server are started during boot-up.  All 3 problems seem to coincide with the installation of php5-interbase (5.3.2-0ubuntu) 2 weeks ago.  Again, it's easy enough to start these services, but I'd like the system to work how it's supposed to work.

Thanks in advance for any help that anyone can offer me.

Here's the output from first 'top' & then 'ps -el':
-----------------------------------------------------------------------------
john@beast:~$ top

top - 17:27:38 up 12 min,  2 users,  load average: 1.41, 1.42, 0.91
Tasks: 157 total,   2 running, 155 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.2%us, 62.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1544072k total,   737576k used,   806496k free,    77268k buffers
Swap:  3318776k total,        0k used,  3318776k free,   317116k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                       
  671 root      20   0  1832  496  432 R 91.9  0.0   9:24.64 rcS                                                           
 1520 john      20   0  136m  37m  16m S  6.3  2.5   0:31.15 chromium-browse                                               
    4 root      20   0     0    0    0 S  0.3  0.0   0:00.99 ksoftirqd/0                                                   
  847 root      20   0 60000  25m 8688 S  0.3  1.7   0:32.63 Xorg                                                          
 1342 john      20   0  110m  11m 9612 S  0.3  0.8   0:01.98 gnome-terminal                                                
    1 root      20   0  2788 1560 1132 S  0.0  0.1   0:00.38 init                                                          
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                      
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                   
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                    
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.27 events/0                                                      
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                        
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                                       
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                                         
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                                     
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                                            
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                                                   
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                   
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                 
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                     
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                        
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                  
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                                                 
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.35 ata/0                                                         
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                       
john@beast:~$ ps -el
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0     1     0  0  80   0 -   697 poll_s ?        00:00:00 init
1 S     0     2     0  0  80   0 -     0 kthrea ?        00:00:00 kthreadd
1 S     0     3     2  0 -40   - -     0 migrat ?        00:00:00 migration/0
1 S     0     4     2  0  80   0 -     0 ksofti ?        00:00:01 ksoftirqd/0
5 S     0     5     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/0
1 S     0     6     2  0  80   0 -     0 worker ?        00:00:00 events/0
1 S     0     7     2  0  80   0 -     0 worker ?        00:00:00 cpuset
1 S     0     8     2  0  80   0 -     0 worker ?        00:00:00 khelper
1 S     0     9     2  0  80   0 -     0 worker ?        00:00:00 netns
1 S     0    10     2  0  80   0 -     0 async_ ?        00:00:00 async/mgr
1 S     0    11     2  0  80   0 -     0 worker ?        00:00:00 pm
1 S     0    12     2  0  80   0 -     0 bdi_sy ?        00:00:00 sync_supers
1 S     0    13     2  0  80   0 -     0 bdi_fo ?        00:00:00 bdi-default
1 S     0    14     2  0  80   0 -     0 worker ?        00:00:00 kintegrityd/0
1 S     0    15     2  0  80   0 -     0 worker ?        00:00:00 kblockd/0
1 S     0    16     2  0  80   0 -     0 worker ?        00:00:00 kacpid
1 S     0    17     2  0  80   0 -     0 worker ?        00:00:00 kacpi_notify
1 S     0    18     2  0  80   0 -     0 worker ?        00:00:00 kacpi_hotplug
1 S     0    19     2  0  80   0 -     0 worker ?        00:00:00 ata/0
1 S     0    20     2  0  80   0 -     0 worker ?        00:00:00 ata_aux
1 S     0    21     2  0  80   0 -     0 worker ?        00:00:00 ksuspend_usbd
5 S     0    22     2  0  80   0 -     0 hub_th ?        00:00:00 khubd
5 S     0    23     2  0  80   0 -     0 serio_ ?        00:00:00 kseriod
1 S     0    24     2  0  80   0 -     0 worker ?        00:00:00 kmmcd
1 S     0    27     2  0  80   0 -     0 watchd ?        00:00:00 khungtaskd
1 S     0    28     2  0  80   0 -     0 kswapd ?        00:00:00 kswapd0
1 S     0    29     2  0  85   5 -     0 ksm_sc ?        00:00:00 ksmd
1 S     0    30     2  0  80   0 -     0 worker ?        00:00:00 aio/0
1 S     0    31     2  0  80   0 -     0 ecrypt ?        00:00:00 ecryptfs-kthrea
1 S     0    32     2  0  80   0 -     0 worker ?        00:00:00 crypto/0
1 S     0    36     2  0  80   0 -     0 worker ?        00:00:00 kstriped
1 S     0    37     2  0  80   0 -     0 worker ?        00:00:00 kmpathd/0
1 S     0    38     2  0  80   0 -     0 worker ?        00:00:00 kmpath_handlerd
1 S     0    39     2  0  80   0 -     0 worker ?        00:00:00 ksnapd
1 S     0    40     2  0  80   0 -     0 worker ?        00:00:00 kondemand/0
1 S     0    41     2  0  80   0 -     0 worker ?        00:00:00 kconservative/0
1 S     0   190     2  0  80   0 -     0 scsi_e ?        00:00:00 scsi_eh_0
1 S     0   191     2  0  80   0 -     0 scsi_e ?        00:00:01 scsi_eh_1
1 S     0   192     2  0  80   0 -     0 scsi_e ?        00:00:00 scsi_eh_2
1 S     0   193     2  0  80   0 -     0 usb_st ?        00:00:00 usb-storage
1 S     0   230     2  0  80   0 -     0 kjourn ?        00:00:00 jbd2/sda1-8
1 S     0   231     2  0  80   0 -     0 worker ?        00:00:00 ext4-dio-unwrit
1 S     0   265     2  0  80   0 -     0 bdi_wr ?        00:00:00 flush-8:0
1 S     0   295     1  0  80   0 -   578 poll_s ?        00:00:00 upstart-udev-br
5 S     0   297     1  0  76  -4 -   637 poll_s ?        00:00:00 udevd
1 S     0   523     2  0  80   0 -     0 gamepo ?        00:00:00 kgameportd
1 S     0   533     2  0  80   0 -     0 worker ?        00:00:00 kpsmoused
1 S     0   605     2  0  80   0 -     0 worker ?        00:00:00 usbhid_resumer
1 S     0   621     2  0  80   0 -     0 worker ?        00:00:00 phy0
0 S     0   657     1  0  80   0 -   458 wait   ?        00:00:00 sh
4 S     0   661     1  0  80   0 -  3832 poll_s ?        00:00:00 smbd
0 R     0   671   657 77  80   0 -    77 ?      ?        00:09:37 rcS
5 S   101   673     1  0  80   0 -  8416 poll_s ?        00:00:00 rsyslogd
1 S     0   675     2  0  80   0 -     0 worker ?        00:00:00 radeon/0
1 S     0   677     2  0  80   0 -     0 worker ?        00:00:00 ttm_swap
5 S     0   680   297  0  78  -2 -   658 poll_s ?        00:00:00 udevd
5 S     0   684   297  0  78  -2 -   658 poll_s ?        00:00:00 udevd
5 S   102   698     1  0  80   0 -   871 poll_s ?        00:00:01 dbus-daemon
5 S   105   714     1  0  80   0 -   731 poll_s ?        00:00:00 avahi-daemon
5 S     0   715     1  0  80   0 -  4746 poll_s ?        00:00:00 NetworkManager
1 S   105   718   714  0  80   0 -   731 unix_s ?        00:00:00 avahi-daemon
1 S     0   719   661  0  80   0 -  3832 poll_s ?        00:00:00 smbd
4 S     0   722     1  0  80   0 -  1042 poll_s ?        00:00:00 modem-manager
4 S     0   737     1  0  80   0 -  1208 poll_s ?        00:00:00 wpa_supplicant
4 S     0   753     1  0  80   0 -  4691 poll_s ?        00:00:00 gdm-binary
4 S     0   758     1  0  80   0 -  4923 poll_s ?        00:00:00 console-kit-dae
4 S     0   825   753  0  80   0 -  5123 poll_s ?        00:00:00 gdm-simple-slav
4 S     0   847   825  4  80   0 - 12557 poll_s tty7     00:00:32 Xorg
1 S   116   868     1  0  80   0 -   845 poll_s ?        00:00:00 dbus-launch
4 S     0   885   715  0  80   0 -  1741 poll_s ?        00:00:00 pppd
4 S     0   900   825  0  80   0 -  5196 poll_s ?        00:00:00 gdm-session-wor
4 S     0   903     1  0  80   0 -  1382 poll_s ?        00:00:00 upowerd
4 S   112   907     1  0  81   1 -  5726 poll_s ?        00:00:00 rtkit-daemon
4 S     0   911     1  0  80   0 -  1583 poll_s ?        00:00:00 polkitd
5 S   110   969     1  0  80   0 -  4287 poll_s ?        00:00:00 hald
0 S     0   971   969  0  80   0 -   883 poll_s ?        00:00:00 hald-runner
0 S     0   999   971  0  80   0 -   901 poll_s ?        00:00:00 hald-addon-inpu
0 S     0  1001   971  0  80   0 -   901 poll_s ?        00:00:00 hald-addon-rfki
0 S     0  1002   971  0  80   0 -   901 poll_s ?        00:00:00 hald-addon-leds
0 S     0  1018   971  0  80   0 -   902 poll_s ?        00:00:00 hald-addon-stor
4 S   110  1020   971  0  80   0 -   853 hrtime ?        00:00:00 hald-addon-acpi
4 S     0  1021   971  0  80   0 -   902 poll_s ?        00:00:00 hald-addon-stor
0 S     0  1026   971  0  80   0 -   902 poll_s ?        00:00:00 hald-addon-stor
0 S     0  1027   971  0  80   0 -   902 poll_s ?        00:00:00 hald-addon-stor
4 S     0  1079     1  0  80   0 -  1708 ep_pol ?        00:00:00 cupsd
5 S     0  1118     1  0  80   0 -  2159 hrtime ?        00:00:00 nmbd
1 S  1000  1121     1  0  80   0 -  5994 poll_s ?        00:00:00 gnome-keyring-d
4 S  1000  1140   900  0  80   0 -  6433 poll_s ?        00:00:00 gnome-session
1 S  1000  1182  1140  0  80   0 -   820 poll_s ?        00:00:00 ssh-agent
1 S  1000  1183  1140  0  80   0 -  1041 poll_s ?        00:00:00 gpg-agent
1 S  1000  1186     1  0  80   0 -   845 poll_s ?        00:00:00 dbus-launch
1 S  1000  1187     1  0  80   0 -   796 poll_s ?        00:00:00 dbus-daemon
0 S  1000  1190     1  0  80   0 -  1882 poll_s ?        00:00:00 gconfd-2
1 S  1000  1197     1  0  80   0 -  4216 poll_s ?        00:00:00 gnome-settings-
0 S  1000  1198  1140  1  80   0 - 16794 poll_s ?        00:00:08 compiz
0 S  1000  1206  1140  0  80   0 -  4562 poll_s ?        00:00:00 polkit-gnome-au
0 S  1000  1207  1140  0  80   0 - 28924 poll_s ?        00:00:00 blueman-applet
0 S  1000  1208  1140  0  80   0 - 46111 poll_s ?        00:00:00 nm-applet
0 S  1000  1210  1140  0  80   0 - 39900 poll_s ?        00:00:00 nautilus
0 S  1000  1211  1140  0  80   0 - 27216 poll_s ?        00:00:01 gnome-panel
0 S  1000  1216  1140  0  80   0 -  4838 poll_s ?        00:00:00 gnome-power-man
0 S  1000  1217     1  0  80   0 -  8742 poll_s ?        00:00:01 hermes_hardware
0 S  1000  1218  1140  0  80   0 -  4670 poll_s ?        00:00:00 bluetooth-apple
0 S  1000  1220  1140  0  80   0 -   458 wait   ?        00:00:00 mount-systray
0 S  1000  1222  1220  0  80   0 - 29145 poll_s ?        00:00:00 /usr/share/moun
0 S  1000  1228     1  0  80   0 - 45858 poll_s ?        00:00:04 cairo-dock
1 S  1000  1230     1  0  69 -11 - 23609 poll_s ?        00:00:01 pulseaudio
0 S  1000  1232     1  0  80   0 -  1594 poll_s ?        00:00:00 gvfsd
1 S  1000  1238     1  0  80   0 -  7570 futex_ ?        00:00:00 gvfs-fuse-daemo
0 S  1000  1243     1  0  80   0 -  1702 poll_s ?        00:00:00 gvfsd-trash
0 S  1000  1246     1  0  80   0 -  1937 poll_s ?        00:00:00 gvfs-gdu-volume
4 S     0  1248     1  0  80   0 -  3919 poll_s ?        00:00:00 udisks-daemon
1 S     0  1249  1248  0  80   0 -  1294 poll_s ?        00:00:00 udisks-daemon
0 S  1000  1252  1230  0  80   0 -  2683 poll_s ?        00:00:00 gconf-helper
0 S  1000  1256     1  0  80   0 -  4239 poll_s ?        00:00:00 gvfs-afc-volume
0 S  1000  1259     1  0  80   0 -  1781 poll_s ?        00:00:00 gvfs-gphoto2-vo
0 S  1000  1261     1  0  80   0 - 10516 poll_s ?        00:00:00 bonobo-activati
0 S  1000  1278     1  0  80   0 - 25964 poll_s ?        00:00:00 gnome-netstatus
0 S  1000  1279     1  0  80   0 - 26606 poll_s ?        00:00:00 gnome-dictionar
0 S  1000  1280     1  0  80   0 -  5606 poll_s ?        00:00:00 notification-ar
0 S  1000  1281     1  0  80   0 -  7750 poll_s ?        00:00:00 clock-applet
0 S  1000  1283     1  0  80   0 - 28518 poll_s ?        00:00:00 indicator-apple
0 S  1000  1286     1  0  80   0 -  5378 poll_s ?        00:00:00 notification-da
0 S  1000  1300     1  0  80   0 -  1595 poll_s ?        00:00:00 gvfsd-burn
0 S  1000  1304     1  0  80   0 -  2728 poll_s ?        00:00:00 obex-data-serve
0 S  1000  1305  1198  0  80   0 -   458 wait   ?        00:00:00 sh
0 S  1000  1306  1305  0  80   0 -  5087 poll_s ?        00:00:00 gtk-window-deco
1 S  1000  1308     1  0  80   0 -  4379 poll_s ?        00:00:00 gnome-screensav
0 S  1000  1318     1  0  80   0 -  1621 poll_s ?        00:00:00 gvfsd-metadata
0 S  1000  1320     1  0  80   0 -  6075 poll_s ?        00:00:00 indicator-appli
0 S  1000  1322     1  0  80   0 -  4389 poll_s ?        00:00:00 indicator-messa
0 S  1000  1324     1  0  80   0 - 21272 poll_s ?        00:00:00 indicator-sound
0 S  1000  1325  1140  0  80   0 -  4584 poll_s ?        00:00:00 gdu-notificatio
0 S  1000  1337     1  0  80   0 -  1702 poll_s ?        00:00:00 gvfsd-computer
0 S  1000  1342     1  0  80   0 - 28375 poll_s ?        00:00:02 gnome-terminal
0 S  1000  1343  1342  0  80   0 -   496 unix_s ?        00:00:00 gnome-pty-helpe
0 S  1000  1344  1342  0  80   0 -  1642 wait   pts/0    00:00:00 bash
0 S  1000  1363  1140  0  80   0 - 16810 poll_s ?        00:00:00 evolution-alarm
0 S  1000  1365  1140  0  80   0 -  7798 poll_s ?        00:00:00 python
0 S  1000  1374     1  0  80   0 - 19186 poll_s ?        00:00:00 evolution-data-
0 S  1000  1427     1  0  80   0 - 30332 poll_s ?        00:00:02 gedit
0 S  1000  1432     1  5  80   0 - 86322 poll_s ?        00:00:29 chromium-browse
1 S  1000  1434  1432  0  80   0 - 17642 poll_s ?        00:00:01 chromium-browse
4 S  1000  1436     1  0  80   0 - 21061 skb_re ?        00:00:00 chromium-browse
1 S  1000  1459  1436  0  85   5 - 32507 futex_ ?        00:00:02 chromium-browse
1 S  1000  1463  1436  0  80   0 - 31883 futex_ ?        00:00:00 chromium-browse
1 S  1000  1481  1436  0  80   0 - 32747 futex_ ?        00:00:03 chromium-browse
1 S  1000  1498  1436  0  80   0 - 30023 futex_ ?        00:00:00 chromium-browse
1 S  1000  1507  1436  0  80   0 - 30023 futex_ ?        00:00:00 chromium-browse
1 S  1000  1514  1436  0  80   0 - 32218 futex_ ?        00:00:00 chromium-browse
1 S  1000  1517  1436  0  80   0 - 32109 futex_ ?        00:00:00 chromium-browse
1 S  1000  1520  1436  6  80   0 - 34995 futex_ ?        00:00:31 chromium-browse
1 S  1000  1526  1436  0  85   5 - 32882 futex_ ?        00:00:02 chromium-browse
1 S  1000  1597  1436  2  80   0 - 32833 futex_ ?        00:00:08 chromium-browse
0 S  1000  1661     1  0  80   0 - 48172 poll_s ?        00:00:02 evolution
1 S  1000  1707  1436  0  85   5 - 31202 futex_ ?        00:00:01 chromium-browse
0 R  1000  1739  1344  0  80   0 -   625 -      pts/0    00:00:00 ps
john@beast:~$ 
-----------------------------------------------------------------------------
If there is further information that any helper would like, please be explicit in your request and subsequent instructions (of how to obtain the required information), i.e. assume I know nothing!

---

### Post by john009 on 2011-07-04
Additional Info: Attempting to run the 'merge' command resulted in a message telling me that I needed to install process rcs!  I did and 'merge' worked, but it made no difference to the start-up problem, i.e. rsc still running after the boot-up has completed and using all available cpu capacity.

However, the problem has now been solved by upgrading to 10.10.  I'll mark this post as such.

Surprised though, not to get ANY suggestions from anybody!  A problem that's defeated all you gurus (or maybe the right person didn't get to read this post).

---

