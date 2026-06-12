---
title: "Is this a normal amount of network activity?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-29
My machine has been up for 2 hours with nothing but gmail running and the occasional chat in gmail. 

26MB in and 3MB out. 

That seems excessive. Haven't received any email during this time. 

Constant in and out on the nic in small amounts.

Gmail recently updated to include phone dial out but I disabled it and it didn't have effect. 

Why would there be that much data over that short a period of time with nothing going on and why would there be a constant stream of traffic in and out?

---

### Post by chaanakya_chiraag on 2010-08-29
Do you have anything like Samba (sharing files with Windows), ssh (secure shell), etc. running?

---

### Post by Rumpletumbler on 2010-08-29
> **chaanakya_chiraag said:**
> Do you have anything like Samba (sharing files with Windows), ssh (secure shell), etc. running?

Nope.

---

### Post by Rumpletumbler on 2010-08-29
> **chaanakya_chiraag said:**
> Do you have anything like Samba (sharing files with Windows), ssh (secure shell), etc. running?

In system monitor there is a process call ssh-agent and one called sh. Do these have anything to do with what you asked?

Edit: when I look in startup apps it looks like ssh-agent might be the keyring.

---

### Post by chaanakya_chiraag on 2010-08-29
> **Rumpletumbler said:**
> In system monitor there is a process call ssh-agent and one called sh. Do these have anything to do with what you asked?

Edit: when I look in startup apps it looks like ssh-agent might be the keyring.
The one called sh is (I think) a process necessary for the system -- it always get started up and I can never kill it ;)
ssh-agent is an authentication agent.  As long as you don't have ssh itself starting up, it's not causing the problem.  Can you do ```
ps aux > processes.txt
``` and paste it between code tags?  To run the command, go to Applications->Accessories->Terminal and type in the code.  All it will do is output a huge list of all running processes.

---

### Post by Rumpletumbler on 2010-08-29
> **chaanakya_chiraag said:**
> The one called sh is (I think) a process necessary for the system -- it always get started up and I can never kill it ;)
ssh-agent is an authentication agent.  As long as you don't have ssh itself starting up, it's not causing the problem.  Can you do ```
ps aux > processes.txt
``` and paste it between code tags?  To run the command, go to Applications->Accessories->Terminal and type in the code.  All it will do is output a huge list of all running processes.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2808  1684 ?        Ss   17:58   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:58   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:58   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    17:58   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    17:58   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    17:58   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    17:58   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    17:58   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    17:58   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    17:58   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    17:58   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    17:58   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    17:58   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    17:58   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    17:58   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    17:58   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    17:58   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    17:58   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    17:58   0:00 [ata/0]
root        20  0.0  0.0      0     0 ?        S    17:58   0:00 [ata_aux]
root        21  0.0  0.0      0     0 ?        S    17:58   0:00 [ksuspend_usbd]
root        22  0.0  0.0      0     0 ?        S    17:58   0:00 [khubd]
root        23  0.0  0.0      0     0 ?        S    17:58   0:00 [kseriod]
root        24  0.0  0.0      0     0 ?        S    17:58   0:00 [kmmcd]
root        27  0.0  0.0      0     0 ?        S    17:58   0:00 [khungtaskd]
root        28  0.0  0.0      0     0 ?        S    17:58   0:00 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   17:58   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        S    17:58   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        S    17:58   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S    17:58   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    17:58   0:00 [scsi_eh_0]
root        37  0.0  0.0      0     0 ?        S    17:58   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S    17:58   0:00 [kstriped]
root        41  0.0  0.0      0     0 ?        S    17:58   0:00 [kmpathd/0]
root        42  0.0  0.0      0     0 ?        S    17:58   0:00 [kmpath_handlerd]
root        43  0.0  0.0      0     0 ?        S    17:58   0:00 [ksnapd]
root        44  0.0  0.0      0     0 ?        S    17:58   0:00 [kondemand/0]
root        45  0.0  0.0      0     0 ?        S    17:58   0:00 [kconservative/0]
root       182  0.0  0.0      0     0 ?        S    17:58   0:00 [radeon/0]
root       183  0.0  0.0      0     0 ?        S    17:58   0:00 [ttm_swap]
root       249  0.0  0.0      0     0 ?        S    17:58   0:00 [jbd2/sda1-8]
root       250  0.0  0.0      0     0 ?        S    17:58   0:00 [ext4-dio-unwrit]
root       292  0.0  0.1   2316   840 ?        S    17:58   0:00 upstart-udev-bridge --daemon
root       300  0.0  0.1   2524   904 ?        S<s  17:58   0:00 udevd --daemon
root       447  0.0  0.1   2520   884 ?        S<   17:58   0:00 udevd --daemon
root       459  0.0  0.1   2520   872 ?        S<   17:58   0:00 udevd --daemon
root       461  0.0  0.0      0     0 ?        S    17:58   0:00 [kpsmoused]
syslog     524  0.0  0.2  33512  1480 ?        Sl   17:58   0:00 rsyslogd -c4
102        559  0.0  0.2   3232  1520 ?        Ss   17:58   0:00 dbus-daemon --system --fork
root       584  0.0  0.5  18780  3240 ?        Ssl  17:58   0:00 gdm-binary
root       594  0.0  0.6  18876  3912 ?        Ssl  17:58   0:00 NetworkManager
avahi      595  0.0  0.2   3024  1556 ?        S    17:58   0:00 avahi-daemon: running [machinename.local]
avahi      597  0.0  0.0   2928   544 ?        Ss   17:58   0:00 avahi-daemon: chroot helper
root       601  0.0  0.3   4168  2264 ?        S    17:58   0:00 /usr/sbin/modem-manager
root       614  0.0  0.4  20592  3128 ?        Sl   17:58   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       692  0.0  0.2   4828  1712 ?        S    17:58   0:00 /sbin/wpa_supplicant -u -s
root       695  0.0  0.5  20496  3756 ?        Sl   17:58   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root       702  0.0  0.0      0     0 ?        S    17:58   0:00 [kgameportd]
root       716  4.3  2.5  25404 16420 tty7     Rs+  17:58   0:54 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-wQYKkQ/database -nolisten tcp vt7
root       811  0.0  0.0   1792   560 tty4     Ss+  17:58   0:00 /sbin/getty -8 38400 tty4
root       817  0.0  0.0   1792   568 tty5     Ss+  17:58   0:00 /sbin/getty -8 38400 tty5
root       830  0.0  0.0   1792   564 tty2     Ss+  17:58   0:00 /sbin/getty -8 38400 tty2
root       832  0.0  0.0   1792   568 tty3     Ss+  17:58   0:00 /sbin/getty -8 38400 tty3
root       837  0.0  0.0   1792   564 tty6     Ss+  17:58   0:00 /sbin/getty -8 38400 tty6
root       844  0.0  0.1   2048   856 ?        Ss   17:58   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       846  0.0  0.1   2376   892 ?        Ss   17:58   0:00 cron
daemon     847  0.0  0.0   2248   428 ?        Ss   17:58   0:00 atd
privoxy    877  0.5  0.2  33856  1880 ?        Ss   17:58   0:06 /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
root       977  0.0  0.0      0     0 ?        S    17:58   0:00 [kdmflush]
root      1020  0.0  0.0      0     0 ?        S    17:58   0:00 [kcryptd_io]
root      1021  0.0  0.0      0     0 ?        S    17:58   0:00 [kcryptd]
gdm       1095  0.0  0.1   3384   756 ?        S    17:58   0:00 /usr/bin/dbus-launch --exit-with-session
root      1152  0.0  0.3  11536  2044 ?        Ss   17:58   0:00 sendmail: MTA: accepting connections          
root      1183  0.0  0.5  20836  3520 ?        Sl   17:58   0:00 /usr/lib/gdm/gdm-session-worker
root      1187  0.0  0.4   5500  2700 ?        S    17:58   0:00 /usr/lib/upower/upowerd
rtkit     1195  0.0  0.1  22908  1192 ?        SNl  17:58   0:00 /usr/lib/rtkit/rtkit-daemon
root      1199  0.0  0.5   6208  3768 ?        S    17:58   0:00 /usr/lib/policykit-1/polkitd
108       1244  0.0  0.6  16840  4388 ?        Ssl  17:58   0:00 /usr/sbin/hald
root      1247  0.0  0.1   3532  1256 ?        S    17:58   0:00 hald-runner
root      1287  0.0  0.3   6700  2492 ?        Ss   17:58   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1335  0.0  0.1   3608  1216 ?        S    17:58   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event0 /dev/input/event1
root      1364  0.0  0.1   3612  1216 ?        S    17:58   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
108       1366  0.0  0.1   3420  1148 ?        S    17:58   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1380  0.0  0.0   1792   568 tty1     Ss+  17:58   0:00 /sbin/getty -8 38400 tty1
user      1390  0.0  0.3  23984  2424 ?        Sl   17:58   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
user      1408  0.0  1.0  25876  6668 ?        Ssl  17:58   0:00 gnome-session
user      1442  0.0  0.0   3284   356 ?        Ss   17:58   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
user      1445  0.0  0.1   3384   748 ?        S    17:58   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
user      1446  0.0  0.2   3188  1328 ?        Ss   17:58   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
user      1449  0.0  0.6   7580  4268 ?        S    17:58   0:00 /usr/lib/libgconf2-4/gconfd-2
user      1456  0.0  1.4  89128  9264 ?        Ss   17:58   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
user      1458  0.0  0.3   6380  2252 ?        S    17:58   0:00 /usr/lib/gvfs/gvfsd
user      1463  0.0  0.4  30280  2596 ?        Ssl  17:58   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/user/.gvfs
user      1467  0.7  3.7  52596 23840 ?        S    17:58   0:08 compiz
user      1470  0.0  0.7  86156  4480 ?        S<sl 17:58   0:00 /usr/bin/pulseaudio --start --log-target=syslog
user      1478  0.0  0.4  10752  2968 ?        S    17:58   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
user      1479  0.6  4.6  72716 29572 ?        Sl   17:58   0:07 mono /usr/lib/docky/Docky.exe
user      1480  0.0  0.1   4192  1228 ?        S    17:58   0:00 /bin/bash /home/user/.conky_start.sh
user      1488  0.0  0.9  18404  6048 ?        S    17:58   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
user      1490  0.1  2.2  40672 14620 ?        S    17:58   0:01 gnome-panel
user      1491  0.0  2.0  50388 13144 ?        S    17:58   0:00 nm-applet --sm-disable
user      1493  0.1  2.5  59844 16516 ?        S    17:58   0:02 nautilus
user      1498  0.0  0.5   7796  3216 ?        S    17:58   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1501  0.0  0.4  15664  3036 ?        Sl   17:58   0:00 /usr/lib/udisks/udisks-daemon
root      1503  0.0  0.1   5180   856 ?        S    17:58   0:00 udisks-daemon: polling /dev/sr0
user      1506  0.0  0.3   7128  2324 ?        S    17:59   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
user      1508  0.0  0.3  16952  2324 ?        Sl   17:59   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
user      1511  0.0  0.4   6808  2952 ?        S    17:59   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
user      1513  0.0  0.5  40948  3508 ?        Ssl  17:59   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
user      1522  0.0  1.9  38732 12548 ?        S    17:59   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
user      1523  0.0  1.6  37340 10684 ?        S    17:59   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=26
user      1526  0.0  2.0  47084 12820 ?        S    17:59   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=21
user      1530  0.0  2.0  32032 13332 ?        S    17:59   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=30
user      1533  0.0  1.9  46872 12512 ?        S    17:59   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=24
user      1534  0.0  1.4  23108  8960 ?        S    17:59   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=39
user      1540  0.0  0.3   6252  1956 ?        S    17:59   0:00 /usr/lib/gvfs/gvfsd-metadata
user      1543  0.0  0.7  17984  4756 ?        S    17:59   0:00 /usr/lib/indicator-session/indicator-session-service
user      1547  0.0  0.6  17524  4284 ?        S    17:59   0:00 /usr/lib/indicator-messages/indicator-messages-service
user      1548  0.0  0.0   1832   492 ?        Ss   17:59   0:00 /bin/sh -c /usr/bin/compiz-decorator
user      1549  0.0  1.4  20236  9564 ?        S    17:59   0:00 /usr/bin/gtk-window-decorator
user      1552  0.0  0.7  18872  4868 ?        S    17:59   0:00 /usr/lib/indicator-me/indicator-me-service
user      1554  0.0  0.7  85076  4532 ?        S    17:59   0:00 /usr/lib/indicator-sound/indicator-sound-service
user      1555  0.0  0.4  17804  2708 ?        Ss   17:59   0:00 gnome-screensaver
user      1561  0.0  0.5  15576  3596 ?        S    17:59   0:00 /usr/lib/indicator-application/indicator-application-service
user      1566  0.0  0.3   6380  2352 ?        S    17:59   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
user      1567  0.0  1.1  18920  7168 ?        S    17:59   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
user      1569  0.0  2.3  31508 15180 ?        S    17:59   0:00 python /usr/share/system-config-printer/applet.py
user      1573  3.1  0.6  79772  4464 ?        Sl   17:59   0:37 conky
user      1619  0.0  1.7  35364 11452 ?        S    17:59   0:00 update-notifier
root      1888  0.0  1.2  13672  8004 ?        S    18:00   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
user      1920  0.0  1.7  35080 11316 ?        S    18:00   0:00 /usr/lib/notify-osd/notify-osd
user      1928  0.0  0.0   1832   532 ?        S    18:17   0:00 /bin/sh /usr/lib/firefox-3.6.8/firefox
user      1933  0.0  0.0   1832   540 ?        S    18:17   0:00 /bin/sh /usr/lib/firefox-3.6.8/run-mozilla.sh /usr/lib/firefox-3.6.8/firefox-bin
user      1937 12.5  9.7 275896 61948 ?        Sl   18:17   0:20 /usr/lib/firefox-3.6.8/firefox-bin
root      1938  0.0  0.0      0     0 ?        S    18:17   0:00 [flush-8:0]
root      1949  0.0  0.1   2232   976 ?        S    18:17   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-a716936f-b9c3-4ffc-a2ab-c4e17765ada8-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
user      2050  4.0  2.0  45228 13068 ?        Sl   18:19   0:00 gnome-terminal
user      2051  0.0  0.1   1988   700 ?        S    18:19   0:00 gnome-pty-helper
user      2052  3.2  0.5   5888  3240 pts/0    Ss   18:19   0:00 bash
user      2070  0.0  0.1   2716  1040 pts/0    R+   18:19   0:00 ps aux
```

I've found that it seems to be gmail related. If I run firefox and use other sites the network activity stops when I'm not using the page but with gmail it constantly increments. If I log out of gmail and close the tab it still increments, however, if I close the browser and restart it works normally until loading gmail again.

---

### Post by Rumpletumbler on 2010-08-30
Anyone else have this constant communication to and from when running gmail now? I 'assume' it's communicating with google. This behavior hasn't been true in the past though. I just wonder if I'm the only one or if anyone else is experiencing the same thing.

---

### Post by Rumpletumbler on 2010-08-30
This is with Firefox closed.

```

COMMAND     PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
avahi-dae   595   avahi   13u  IPv4    3911      0t0  UDP *:5353 
avahi-dae   595   avahi   14u  IPv4    3912      0t0  UDP *:52683 
privoxy     877 privoxy    1u  IPv4    4470      0t0  TCP 127.0.0.1:8118 (LISTEN)
sendmail-  1152    root    4u  IPv4    5166      0t0  TCP 127.0.0.1:25 (LISTEN)
sendmail-  1152    root    5u  IPv4    5167      0t0  TCP 127.0.0.1:587 (LISTEN)
cupsd      1287    root    5u  IPv6 3465625      0t0  TCP [::1]:631 (LISTEN)
cupsd      1287    root    6u  IPv4 3465626      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  20014    root    5u  IPv4 2884938      0t0  UDP *:68 
```

This is logged into Gmail. 

```
COMMAND     PID    USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
avahi-dae   595   avahi   13u  IPv4    3911      0t0  UDP *:5353 
avahi-dae   595   avahi   14u  IPv4    3912      0t0  UDP *:52683 
privoxy     877 privoxy    1u  IPv4    4470      0t0  TCP 127.0.0.1:8118 (LISTEN)
privoxy     877 privoxy    2u  IPv4 4127084      0t0  TCP 127.0.0.1:8118->127.0.0.1:32960 (ESTABLISHED)
privoxy     877 privoxy    3u  IPv4 4129597      0t0  TCP 127.0.0.1:8118->127.0.0.1:32975 (ESTABLISHED)
privoxy     877 privoxy    4u  IPv4 4127123      0t0  TCP 127.0.0.1:8118->127.0.0.1:32963 (ESTABLISHED)
privoxy     877 privoxy    5u  IPv4 4127176      0t0  TCP 192.168.1.104:55694->74.125.65.105:443 (ESTABLISHED)
privoxy     877 privoxy    6u  IPv4 4127903      0t0  TCP 192.168.1.104:46604->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy    7u  IPv4 4127307      0t0  TCP 127.0.0.1:8118->127.0.0.1:32965 (ESTABLISHED)
privoxy     877 privoxy    8u  IPv4 4127310      0t0  TCP 127.0.0.1:8118->127.0.0.1:32967 (ESTABLISHED)
privoxy     877 privoxy    9u  IPv4 4127317      0t0  TCP 192.168.1.104:46598->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   10u  IPv4 4129600      0t0  TCP 192.168.1.104:46606->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   11u  IPv4 4129663      0t0  TCP 127.0.0.1:8118->127.0.0.1:32976 (ESTABLISHED)
privoxy     877 privoxy   12u  IPv4 4127387      0t0  TCP 127.0.0.1:8118->127.0.0.1:32973 (ESTABLISHED)
privoxy     877 privoxy   13u  IPv4 4127390      0t0  TCP 192.168.1.104:46602->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   14u  IPv4 4129665      0t0  TCP 127.0.0.1:8118->127.0.0.1:32977 (ESTABLISHED)
privoxy     877 privoxy   15u  IPv4 4129667      0t0  TCP 127.0.0.1:8118->127.0.0.1:32981 (ESTABLISHED)
privoxy     877 privoxy   16u  IPv4 4130365      0t0  TCP 192.168.1.104:46612->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   17u  IPv4 4129915      0t0  TCP 192.168.1.104:46610->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   18u  IPv4 4130165      0t0  TCP 192.168.1.104:46611->74.125.67.18:443 (ESTABLISHED)
privoxy     877 privoxy   20u  IPv4 4135257      0t0  TCP 192.168.1.104:45010->74.125.67.189:443 (ESTABLISHED)
sendmail-  1152    root    4u  IPv4    5166      0t0  TCP 127.0.0.1:25 (LISTEN)
sendmail-  1152    root    5u  IPv4    5167      0t0  TCP 127.0.0.1:587 (LISTEN)
cupsd      1287    root    5u  IPv6 3465625      0t0  TCP [::1]:631 (LISTEN)
cupsd      1287    root    6u  IPv4 3465626      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient  20014    root    5u  IPv4 2884938      0t0  UDP *:68 
firefox-b 23965    username   46u  IPv4 4135253      0t0  TCP 127.0.0.1:32981->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   55u  IPv4 4127303      0t0  TCP 127.0.0.1:32963->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   60u  IPv4 4127122      0t0  TCP 127.0.0.1:32960->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   63u  IPv4 4129596      0t0  TCP 127.0.0.1:32973->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   64u  IPv4 4127309      0t0  TCP 127.0.0.1:32965->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   65u  IPv4 4127320      0t0  TCP 127.0.0.1:32967->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   66u  IPv4 4129662      0t0  TCP 127.0.0.1:32975->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   67u  IPv4 4129664      0t0  TCP 127.0.0.1:32976->127.0.0.1:8118 (ESTABLISHED)
firefox-b 23965    username   68u  IPv4 4129666      0t0  TCP 127.0.0.1:32977->127.0.0.1:8118 (ESTABLISHED)
```

Is that normal? Seems like too many connections.

---

### Post by chaanakya_chiraag on 2010-08-30
Do you have pipelining enabled?

---

### Post by Rumpletumbler on 2010-08-30
> **chaanakya_chiraag said:**
> Do you have pipelining enabled?

I don't know what that means, so I would guess no.

---

### Post by chaanakya_chiraag on 2010-08-31
Hmmm...what command did you use to display the active connections?  I'll try it out and see if I'm getting the same number of connections.

---

### Post by Rumpletumbler on 2010-08-31
> **chaanakya_chiraag said:**
> Hmmm...what command did you use to display the active connections?  I'll try it out and see if I'm getting the same number of connections.
```

sudo lsof -n -i -P
```

Could you also see if you have constant network traffic in and out while logged in please?

---

### Post by Pough913 on 2010-08-31
Its normal just as the page auto. refreshes.

---

### Post by Rumpletumbler on 2010-08-31
> **Pough913 said:**
> Its normal just as the page auto. refreshes.

In 5.5 hours I have 93MB in 27MB out with an occasional look around here and Gmail. 

It's hard for me to believe that it takes that much data to keep the mailbox refreshed.

Edit: not to mention there's no activity on the NIC in Windows after the page loads so that wouldn't be it.

---

