---
title: "System Monitor Show This"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by ssdt on 2010-06-30
This is what my system monitor shows me, some kind of a process without any name or any icon. 

[[IMG]http://img808.imageshack.us/img808/5285/screenshotsystemmonitorg.png[/IMG]](http://img808.imageshack.us/i/screenshotsystemmonitorg.png/)
[/URL]

Can anyone please tell me what this is and why it's showing up?

Thank you

---

### Post by matt-fender on 2010-06-30
O_o

Does it disappear after restart?

---

### Post by hansdown on 2010-06-30
Hi ssdt.

If you hover your mouse over it, you will see what it is.

---

### Post by Rubi1200 on 2010-06-30
If it is still there, or appears again, you can try and identify what it is by running any of these commands from the terminal:

```
top
```

```
ps aux #
```

```
pstree
```

These should help you track it down and keep an eye on your processes in general.

---

### Post by ssdt on 2010-07-02
Yeah, every restart gets this thing up. It's like from the startup. When I mouseover it, I actually see the mousetip saying nothing and then the scrollbar moving down and those two processes disappering. Then when I go up again (scroll up), it shows up.

---

### Post by ssdt on 2010-07-02
Here is the results of different executes:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   2796  1648 ?        Ss   10:55   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:55   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    10:55   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    10:55   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    10:55   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    10:55   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    10:55   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    10:55   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    10:55   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    10:55   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    10:55   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    10:55   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    10:55   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    10:55   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    10:55   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    10:55   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    10:55   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    10:55   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    10:55   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    10:55   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    10:55   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    10:55   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    10:55   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    10:55   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    10:55   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    10:55   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    10:55   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    10:55   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    10:55   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    10:55   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    10:55   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    10:55   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    10:55   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   10:55   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    10:55   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    10:55   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    10:55   0:00 [ecryptfs-kthr]
root        41  0.0  0.0      0     0 ?        S    10:55   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    10:55   0:00 [crypto/1]
root        46  0.0  0.0      0     0 ?        S    10:55   0:00 [scsi_eh_0]
root        47  0.0  0.0      0     0 ?        S    10:55   0:00 [scsi_eh_1]
root        49  0.0  0.0      0     0 ?        S    10:55   0:00 [scsi_eh_2]
root        51  0.0  0.0      0     0 ?        S    10:55   0:00 [scsi_eh_3]
root        53  0.0  0.0      0     0 ?        S    10:55   0:00 [kstriped]
root        54  0.0  0.0      0     0 ?        S    10:55   0:00 [kmpathd/0]
root        55  0.0  0.0      0     0 ?        S    10:55   0:00 [kmpathd/1]
root        56  0.0  0.0      0     0 ?        S    10:55   0:00 [kmpath_handle]
root        57  0.0  0.0      0     0 ?        S    10:55   0:00 [ksnapd]
root        58  0.0  0.0      0     0 ?        S    10:55   0:00 [kondemand/0]
root        59  0.0  0.0      0     0 ?        S    10:55   0:00 [kondemand/1]
root        60  0.0  0.0      0     0 ?        S    10:55   0:00 [kconservative]
root        61  0.0  0.0      0     0 ?        S    10:55   0:00 [kconservative]
root       258  0.2  0.0      0     0 ?        S    10:55   0:00 [kjournald]
root       275  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:0]
root       276  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:1]
root       277  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:2]
root       278  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:3]
root       279  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:4]
root       280  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:5]
root       281  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:6]
root       282  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:7]
root       283  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:8]
root       284  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:9]
root       285  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:10]
root       286  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:11]
root       287  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:12]
root       288  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:13]
root       289  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:14]
root       290  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-1:15]
root       291  0.0  0.0      0     0 ?        S    10:55   0:00 [flush-8:0]
root       317  0.0  0.0   2312   900 ?        S    10:55   0:00 upstart-udev-br
root       320  0.0  0.0   2700  1088 ?        S<s  10:55   0:00 udevd --daemon
root       464  0.0  0.0   2696  1004 ?        S<   10:55   0:00 udevd --daemon
root       465  0.0  0.0   2696   996 ?        S<   10:55   0:00 udevd --daemon
root       602  0.0  0.0      0     0 ?        S    10:55   0:00 [usbhid_resume]
root       603  0.0  0.0      0     0 ?        S    10:55   0:00 [kpsmoused]
root       625  0.0  0.0      0     0 ?        S    10:55   0:00 [i915]
syslog     691  0.0  0.0  34940  1788 ?        Sl   10:55   0:00 rsyslogd -c4
108        698  0.0  0.0   3200  1540 ?        Ss   10:55   0:00 dbus-daemon --s
root       711  0.0  0.1  18648  3820 ?        Ssl  10:55   0:00 NetworkManager
root       712  0.1  0.1  19508  3120 ?        Ssl  10:55   0:00 gdm-binary
avahi      719  0.0  0.0   2924  1556 ?        S    10:55   0:00 avahi-daemon: r
root       720  0.0  0.1   4164  2296 ?        S    10:55   0:00 /usr/sbin/modem
root       783  0.0  0.1  19740  3244 ?        Sl   10:55   0:00 /usr/sbin/conso
avahi      848  0.0  0.0   2924   548 ?        Ss   10:55   0:00 avahi-daemon: c
root       851  0.0  0.1  21572  3628 ?        Sl   10:55   0:00 /usr/lib/gdm/gd
root       857  0.0  0.0   4824  1736 ?        S    10:55   0:00 /sbin/wpa_suppl
root       859  0.0  0.0      0     0 ?        S    10:55   0:00 [hd-audio0]
root       863  0.0  0.0   1788   564 tty4     Ss+  10:55   0:00 /sbin/getty -8
root       867  0.0  0.0   1788   564 tty5     Ss+  10:55   0:00 /sbin/getty -8
root       876  0.0  0.0   1788   568 tty2     Ss+  10:55   0:00 /sbin/getty -8
root       877  0.0  0.0   1788   564 tty3     Ss+  10:55   0:00 /sbin/getty -8
root       880  0.0  0.0   1788   568 tty6     Ss+  10:55   0:00 /sbin/getty -8
root       883  0.0  0.0   2044   860 ?        Ss   10:55   0:00 acpid -c /etc/a
root       896  8.2  0.7  23704 15084 tty7     Ss+  10:55   0:14 /usr/bin/X :0 -
daemon     903  0.0  0.0   2244   436 ?        Ss   10:55   0:00 atd
root       904  0.0  0.0   2372   900 ?        Ss   10:55   0:00 cron
root       967  0.0  0.0  11732  1376 ?        Ss   10:55   0:00 /usr/sbin/winbi
root       969  0.0  0.0  11732  1188 ?        S    10:55   0:00 /usr/sbin/winbi
root      1024  0.0  0.1   6808  2620 ?        Ss   10:55   0:00 /usr/sbin/cupsd
root      1053  0.0  0.1  20028  3124 ?        Sl   10:55   0:00 /usr/lib/gdm/gd
datta     1085  2.7  0.3  27020  6784 ?        Rsl  10:55   0:04 gnome-session
root      1147  0.0  0.0   1788   564 tty1     Ss+  10:55   0:00 /sbin/getty -8
datta     1177  0.0  0.0   5748  1312 ?        Ss   10:55   0:00 /usr/lib/scim-1
datta     1181  0.0  0.0   5592   832 ?        Ss   10:55   0:00 /usr/lib/scim-1
datta     1182  0.0  0.2  29320  5804 ?        Ssl  10:55   0:00 /usr/lib/scim-1
datta     1184  0.0  0.0   7160  1788 ?        Ss   10:55   0:00 /usr/lib/scim-1
datta     1188  0.0  0.0   3280   360 ?        Ss   10:55   0:00 /usr/bin/ssh-ag
datta     1191  0.0  0.0   3380   764 ?        S    10:55   0:00 /usr/bin/dbus-l
datta     1192  6.3  0.0   3184  1468 ?        Rs   10:55   0:10 /bin/dbus-daemo
datta     1195  8.9  0.2   9324  4960 ?        S    10:55   0:15 /usr/lib/libgco
datta     1199  0.9  0.4  90508  9732 ?        Ss   10:55   0:01 /usr/lib/gnome-
datta     1200  0.4  0.1  25032  2196 ?        Sl   10:55   0:00 /usr/bin/gnome-
datta     1204  0.5  0.1   7452  2288 ?        S    10:55   0:00 /usr/lib/gvfs/g
datta     1209  0.0  0.1  30200  2500 ?        Ssl  10:55   0:00 /usr/lib/gvfs//
datta     1215  1.6  0.2 169296  5748 ?        S<sl 10:55   0:02 /usr/bin/pulsea
rtkit     1217  0.0  0.0  22904  1212 ?        SNl  10:55   0:00 /usr/lib/rtkit/
datta     1218  0.8  0.5  28256 10768 ?        S    10:55   0:01 /usr/lib/tracke
datta     1219  0.7  0.3  20088  7396 ?        S    10:55   0:01 bluetooth-apple
root      1223  0.0  0.1   6144  3688 ?        S    10:55   0:00 /usr/lib/policy
datta     1224  0.7  0.3  19560  6668 ?        S    10:55   0:01 tracker-applet
datta     1226  2.2  0.7  43012 15736 ?        S    10:55   0:03 gnome-panel
datta     1231  0.6  0.9  79928 19044 ?        Sl   10:55   0:01 nautilus
111       1233  0.0  0.1  16492  4072 ?        Ssl  10:55   0:00 /usr/sbin/hald
datta     1234  0.8  0.5  50820 11316 ?        S    10:55   0:01 nm-applet --sm-
root      1235  0.0  0.0   3528  1284 ?        S    10:55   0:00 hald-runner
datta     1236  0.6  0.5  22176 10684 ?        S    10:55   0:01 metacity --repl
datta     1247  1.3  0.3  20748  7520 ?        S    10:55   0:02 gnome-power-man
datta     1249  0.0  0.3  19524  6156 ?        S    10:55   0:00 /usr/lib/policy
root      1277  0.0  0.1   5564  2896 ?        S    10:55   0:00 /usr/lib/upower
root      1280  0.0  0.0   3604  1240 ?        S    10:55   0:00 hald-addon-inpu
root      1298  0.0  0.0   3608  1236 ?        S    10:55   0:00 hald-addon-stor
root      1300  0.0  0.0   3616  1220 ?        S    10:55   0:00 /usr/lib/hal/ha
111       1301  0.0  0.0   3416  1172 ?        S    10:55   0:00 hald-addon-acpi
datta     1334  0.0  0.1   7804  2896 ?        S    10:55   0:00 /usr/lib/gvfs/g
datta     1337  0.8  0.5  28176 10604 ?        SN   10:55   0:01 /usr/lib/tracke
datta     1346  0.0  0.1   8824  3224 ?        S    10:55   0:00 /usr/lib/gvfs/g
root      1348  0.0  0.1  15640  3048 ?        Sl   10:55   0:00 /usr/lib/udisks
root      1349  0.0  0.0   5176   880 ?        S    10:55   0:00 udisks-daemon: 
datta     1354  0.0  0.1   8200  2400 ?        S    10:55   0:00 /usr/lib/gvfs/g
root      1355  0.0  0.0   2228   996 ?        S    10:55   0:00 /sbin/dhclient
datta     1358  0.0  0.1  10748  2992 ?        S    10:55   0:00 /usr/lib/pulsea
datta     1363  0.0  0.1  18024  2360 ?        Sl   10:55   0:00 /usr/lib/gvfs/g
datta     1367  0.0  0.1  42964  3480 ?        Ssl  10:55   0:00 /usr/lib/bonobo
datta     1375  0.4  0.6  40592 13068 ?        S    10:55   0:00 /usr/lib/gnome-
datta     1377  0.0  0.5  38688 10328 ?        S    10:55   0:00 /usr/lib/gnome-
datta     1394  0.0  0.4  23688  8432 ?        S    10:55   0:00 /usr/lib/gnome-
datta     1395  0.8  0.6  48560 12308 ?        S    10:55   0:01 /usr/lib/indica
datta     1396  0.7  0.7  54936 15008 ?        S    10:55   0:01 /usr/lib/gnome-
datta     1408  0.0  0.0   8280  1848 ?        S    10:55   0:00 /usr/bin/gnome-
datta     1420  0.0  0.0   7372  2040 ?        S    10:55   0:00 /usr/lib/gvfs/g
datta     1422  0.6  0.2  18472  4364 ?        S    10:55   0:01 /usr/lib/indica
datta     1431  0.5  0.2  24096  4172 ?        S    10:55   0:00 /usr/lib/indica
datta     1434  0.5  0.2  86152  4576 ?        S    10:55   0:00 /usr/lib/indica
datta     1458  0.0  0.1   7452  2392 ?        S    10:55   0:00 /usr/lib/gvfs/g
datta     1650  0.0  0.5  36876 11488 ?        S    10:55   0:00 /usr/lib/notify
datta     1739  0.7  0.1  18924  2680 ?        Ss   10:55   0:01 /usr/bin/gnome-
datta     1922 41.6  7.8 454900 160464 ?       Rl   10:55   1:07 epiphany-browse
datta     2384  0.0  0.3  19536  6796 ?        S    10:55   0:00 /usr/lib/gnome-
datta     3513  0.0  0.0   1828   556 ?        S    10:56   0:00 /bin/sh /usr/li
datta     3524  0.0  0.0   1828   572 ?        S    10:56   0:00 /bin/sh /usr/li
datta     3528  6.6  4.3 262008 88812 ?        Sl   10:56   0:09 /usr/lib/firefo
datta     4089  1.6  0.7  32604 15228 ?        S    10:56   0:02 python /usr/sha
datta     8087  2.3  0.6  47804 13516 ?        Rl   10:56   0:02 gnome-terminal
datta     8125  0.0  0.0   1984   712 ?        S    10:56   0:00 gnome-pty-helpe
datta    13366  2.0  0.1   7600  3912 pts/1    Ss   10:58   0:00 bash
datta    14020  0.0  0.0   1828   548 ?        S    10:58   0:00 /bin/sh /usr/bi
datta    14021  0.0  0.0   3788  1076 pts/1    R+   10:58   0:00 ps aux
```

```
~$ pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activat}
     &#9500;&#9472;clock-applet
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-da}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;epiphany-browse&#9472;&#9472;&#9472;20*[{epiphany-brows}]
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;run-mozilla.sh&#9472;&#9472;&#9472;firefox-bin&#9472;&#9472;&#9472;13*[{firefox-bin}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm-binary&#9472;&#9516;&#9472;gdm-simple-slav&#9472;&#9516;&#9472;Xorg
     &#9474;            &#9474;                 &#9500;&#9472;gdm-session-wor&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;bluetoo+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gdu-not+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;2*[meta+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nautilu+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nm-appl+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;polkit-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;python
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;ssh-age+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;tracker+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;tracker+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9492;&#9472;{gnome-+
     &#9474;            &#9474;                 &#9474;                 &#9492;&#9472;{gdm-session-wo}
     &#9474;            &#9474;                 &#9492;&#9472;{gdm-simple-sla}
     &#9474;            &#9492;&#9472;{gdm-binary}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;2*[{gnome-keyring-}]
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9516;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-cpuf
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-inpu
     &#9474;      &#9474;             &#9492;&#9472;hald-addon-stor
     &#9474;      &#9492;&#9472;{hald}
     &#9500;&#9472;indicator-apple
     &#9500;&#9472;indicator-appli
     &#9500;&#9472;indicator-messa
     &#9500;&#9472;indicator-sound
     &#9500;&#9472;modem-manager
     &#9500;&#9472;notification-ar
     &#9500;&#9472;notify-osd
     &#9500;&#9472;polkitd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;3*[{pulseaudio}]
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;2*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;scim-helper-man
     &#9500;&#9472;2*[scim-launcher]
     &#9500;&#9472;scim-panel-gtk&#9472;&#9472;&#9472;{scim-panel-gtk}
     &#9500;&#9472;tracker-indexer
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;{udisks-daemon}
     &#9500;&#9472;upowerd
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9500;&#9472;wnck-applet
     &#9492;&#9472;wpa_supplicant
```

Here is the result from top: [IMG]http://img684.imageshack.us/img684/5066/screenshotdattadattades.png[/IMG]

Please help me identify the problem as I can see nothing wrong here.

---

### Post by lkjoel on 2010-07-02
Its just a process thats is being ended.
It has N/A ram.

---

