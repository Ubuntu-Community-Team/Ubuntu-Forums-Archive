---
title: "Unknown Bandwidth Drain"
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by coljohnhannibalsmith on 2015-11-15
Hello,

My network connection has a continuous drain of about 30K and I can't identify the process/es that are causing it. I do have I2P installed, which launches on startup; so I suspect that this is the cause. I have included the output of ps -A:

  ```
PID TTY          TIME CMD
    1 ?        00:00:03 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 kworker/0:0H
    7 ?        00:00:50 rcu_sched
    8 ?        00:00:00 rcu_bh
    9 ?        00:00:11 rcuos/0
   10 ?        00:00:00 rcuob/0
   11 ?        00:00:00 migration/0
   12 ?        00:00:00 watchdog/0
   13 ?        00:00:00 watchdog/1
   14 ?        00:00:00 migration/1
   15 ?        00:00:00 ksoftirqd/1
   17 ?        00:00:00 kworker/1:0H
   18 ?        00:00:03 rcuos/1
   19 ?        00:00:00 rcuob/1
   20 ?        00:00:00 watchdog/2
   21 ?        00:00:00 migration/2
   22 ?        00:00:00 ksoftirqd/2
   24 ?        00:00:00 kworker/2:0H
   25 ?        00:00:10 rcuos/2
   26 ?        00:00:00 rcuob/2
   27 ?        00:00:00 watchdog/3
   28 ?        00:00:00 migration/3
   29 ?        00:00:00 ksoftirqd/3
   31 ?        00:00:00 kworker/3:0H
   32 ?        00:00:03 rcuos/3
   33 ?        00:00:00 rcuob/3
   34 ?        00:00:00 watchdog/4
   35 ?        00:00:00 migration/4
   36 ?        00:00:00 ksoftirqd/4
   38 ?        00:00:00 kworker/4:0H
   39 ?        00:00:09 rcuos/4
   40 ?        00:00:00 rcuob/4
   41 ?        00:00:00 watchdog/5
   42 ?        00:00:00 migration/5
   43 ?        00:00:00 ksoftirqd/5
   45 ?        00:00:00 kworker/5:0H
   46 ?        00:00:03 rcuos/5
   47 ?        00:00:00 rcuob/5
   48 ?        00:00:00 watchdog/6
   49 ?        00:00:00 migration/6
   50 ?        00:00:01 ksoftirqd/6
   52 ?        00:00:00 kworker/6:0H
   53 ?        00:00:19 rcuos/6
   54 ?        00:00:00 rcuob/6
   55 ?        00:00:00 watchdog/7
   56 ?        00:00:00 migration/7
   57 ?        00:00:00 ksoftirqd/7
   59 ?        00:00:00 kworker/7:0H
   60 ?        00:00:03 rcuos/7
   61 ?        00:00:00 rcuob/7
   62 ?        00:00:00 khelper
   63 ?        00:00:00 kdevtmpfs
   64 ?        00:00:00 netns
   65 ?        00:00:00 perf
   66 ?        00:00:00 khungtaskd
   67 ?        00:00:00 writeback
   68 ?        00:00:00 ksmd
   69 ?        00:00:05 khugepaged
   70 ?        00:00:00 crypto
   71 ?        00:00:00 kintegrityd
   72 ?        00:00:00 bioset
   73 ?        00:00:00 kblockd
   74 ?        00:00:00 ata_sff
   75 ?        00:00:00 md
   76 ?        00:00:00 devfreq_wq
   80 ?        00:00:03 kswapd0
   81 ?        00:00:00 fsnotify_mark
   82 ?        00:00:00 ecryptfs-kthrea
   94 ?        00:00:00 kthrotld
   95 ?        00:00:00 acpi_thermal_pm
  101 ?        00:00:00 ipv6_addrconf
  121 ?        00:00:00 deferwq
  122 ?        00:00:00 charger_manager
  182 ?        00:00:00 kpsmoused
  184 ?        00:00:00 scsi_eh_0
  185 ?        00:00:00 scsi_tmf_0
  186 ?        00:00:00 scsi_eh_1
  187 ?        00:00:00 scsi_tmf_1
  188 ?        00:00:00 scsi_eh_2
  189 ?        00:00:00 scsi_tmf_2
  190 ?        00:00:00 scsi_eh_3
  191 ?        00:00:00 scsi_tmf_3
  192 ?        00:00:00 scsi_eh_4
  193 ?        00:00:00 scsi_tmf_4
  194 ?        00:00:00 scsi_eh_5
  195 ?        00:00:00 scsi_tmf_5
  218 ?        00:00:03 jbd2/sda5-8
  219 ?        00:00:00 ext4-rsv-conver
  394 ?        00:00:00 upstart-udev-br
  399 ?        00:00:00 systemd-udevd
  463 ?        00:00:00 irq/27-mei_me
  486 ?        00:00:00 cfg80211
  493 ?        00:00:01 irq/28-iwlwifi
  514 ?        00:00:00 kworker/4:1H
  516 ?        00:00:00 kworker/1:1H
  541 ?        00:00:00 kworker/5:1H
  550 ?        00:00:00 kworker/u17:0
  552 ?        00:00:00 hci0
  553 ?        00:00:00 hci0
  555 ?        00:00:00 kworker/u17:2
  556 ?        00:00:00 kvm-irqfd-clean
  561 ?        00:00:00 kworker/0:1H
  609 ?        00:00:00 iwlwifi
  658 ?        00:00:00 upstart-socket-
  689 ?        00:00:00 kmemstick
  744 ?        00:00:02 rtsx_usb_ms_1
  747 ?        00:00:00 hd-audio0
  816 ?        00:00:01 smbd
  857 ?        00:00:07 dbus-daemon
  884 ?        00:00:00 ModemManager
  885 ?        00:00:00 bluetoothd
  895 ?        00:00:00 upstart-file-br
  929 ?        00:00:00 krfcommd
  931 ?        00:00:00 rsyslogd
  941 ?        00:00:00 kworker/3:1H
  944 ?        00:00:00 kworker/2:1H
  946 ?        00:00:00 avahi-daemon
  961 ?        00:00:00 kworker/6:1H
  968 ?        00:00:00 systemd-logind
  970 ?        00:00:00 avahi-daemon
  977 ?        00:00:04 NetworkManager
  983 ?        00:00:02 polkitd
  992 ?        00:00:00 smbd
 1159 tty4     00:00:00 getty
 1163 tty5     00:00:00 getty
 1164 ?        00:00:04 thermald
 1178 tty2     00:00:00 getty
 1179 tty3     00:00:00 getty
 1183 tty6     00:00:00 getty
 1211 ?        00:00:01 wpa_supplicant
 1241 ?        00:00:00 atd
 1242 ?        00:00:00 cron
 1271 ?        00:00:00 cups-browsed
 1279 ?        00:00:05 irqbalance
 1281 ?        00:00:00 acpid
 1359 ?        00:00:48 wrapper
 1365 ?        00:00:50 mysqld
 1373 ?        00:00:00 dhclient
 1379 ?        00:00:00 whoopsie
 1409 ?        00:00:00 kerneloops
 1429 ?        00:59:08 java
 1430 ?        00:00:00 kworker/7:1H
 1442 ?        00:00:00 libvirtd
 1467 ?        00:00:05 dnsmasq
 1638 ?        00:00:00 winbindd
 1672 ?        00:00:00 winbindd
 1673 ?        00:00:00 nmbd
 1997 ?        00:00:00 dnsmasq
 2066 ?        00:00:01 lightdm
 2102 tty7     01:20:10 Xorg
 2108 ?        00:00:07 accounts-daemon
 2133 ?        00:00:00 kauditd
 2204 ?        00:00:00 lightdm
 2246 ?        00:00:00 upowerd
 2261 ?        00:00:00 rtkit-daemon
 2466 ?        00:00:00 colord
 2628 ?        00:00:00 gnome-keyring-d
 2650 tty1     00:00:00 getty
 2654 ?        00:00:00 init
 2752 ?        00:00:05 dbus-daemon
 2763 ?        00:00:00 upstart-event-b
 2770 ?        00:00:00 window-stack-br
 2778 ?        00:00:35 ibus-daemon
 2820 ?        00:00:03 unity-settings-
 2825 ?        00:00:00 at-spi-bus-laun
 2826 ?        00:00:01 gnome-session
 2831 ?        00:00:00 dbus-daemon
 2834 ?        00:00:00 upstart-dbus-br
 2837 ?        00:00:00 upstart-file-br
 2838 ?        00:00:00 upstart-dbus-br
 2840 ?        00:00:01 at-spi2-registr
 2847 ?        00:00:04 bamfdaemon
 2849 ?        00:00:00 gvfsd
 2854 ?        00:00:00 gvfsd-fuse
 2881 ?        00:00:00 ibus-dconf
 2882 ?        00:00:09 ibus-ui-gtk3
 2884 ?        00:00:00 ibus-x11
 2910 ?        00:00:08 ibus-engine-sim
 2919 ?        00:00:02 dconf-service
 2924 ?        00:00:00 syndaemon
 2928 ?        00:00:11 pulseaudio
 2959 ?        00:40:59 compiz
 2966 ?        00:00:25 gnome-panel
 2970 ?        00:00:00 cairo-clock
 2973 ?        00:00:00 indicator-bluet
 2974 ?        00:00:00 python
 2978 ?        00:00:00 indicator-appli
 2984 ?        00:00:00 nm-applet
 2985 ?        00:02:45 nautilus
 2991 ?        00:00:00 gconfd-2
 2992 ?        00:00:00 polkit-gnome-au
 2993 ?        00:00:00 unity-fallback-
 2994 ?        00:00:00 initctl
 2995 ?        00:00:00 conky
 2997 ?        00:00:01 indicator-messa
 3000 ?        00:00:00 indicator-power
 3001 ?        00:00:01 indicator-datet
 3006 ?        00:00:05 indicator-sound
 3010 ?        00:00:03 indicator-sessi
 3042 ?        00:00:00 xscreensaver
 3094 ?        00:00:02 notify-osd
 3103 ?        00:00:00 gvfs-udisks2-vo
 3105 ?        00:00:00 evolution-sourc
 3109 ?        00:00:14 udisksd
 3121 ?        00:00:00 gvfs-gphoto2-vo
 3125 ?        00:00:00 gvfs-afc-volume
 3130 ?        00:00:00 gvfs-mtp-volume
 3137 ?        00:00:04 python
 3138 ?        00:00:03 python
 3140 ?        00:00:00 sh
 3141 ?        00:00:06 gtk-window-deco
 3147 ?        00:00:00 evolution-calen
 3153 ?        00:33:59 cairo-clock
 3154 ?        00:09:23 conky
 3158 ?        00:00:00 gvfsd-burn
 3165 ?        00:00:00 gvfsd-trash
 3181 ?        00:00:04 xscreensaver
 3192 ?        00:00:00 gvfsd-metadata
 3205 ?        00:00:00 telepathy-indic
 3211 ?        00:00:00 mission-control
 3235 ?        00:00:01 zeitgeist-datah
 3240 ?        00:00:00 zeitgeist-daemo
 3246 ?        00:00:00 zeitgeist-fts
 3259 ?        00:01:59 variety
 3273 ?        00:00:00 cat
 3277 ?        00:00:00 trashapplet
 3285 ?        00:00:14 indicator-apple
 3290 ?        00:00:00 indicator-keybo
 3407 ?        00:00:00 update-notifier
 3513 ?        00:00:00 deja-dup-monito
 3608 ?        00:00:00 geoclue-master
 3612 ?        00:00:00 ubuntu-geoip-pr
 3658 ?        00:00:00 gvfsd-http
 4239 ?        00:00:00 kworker/4:2
 4960 ?        00:00:00 sh
 4961 ?        00:00:00 gnome-terminal
 4968 ?        00:00:00 gnome-pty-helpe
 4969 pts/5    00:00:00 bash
 4981 pts/5    00:02:47 boincmgr
 4994 pts/5    00:01:08 boinc
 5973 ?        00:01:36 chrome
 5982 ?        00:00:00 cat
 5983 ?        00:00:00 cat
 5986 ?        00:00:00 chrome
 5988 ?        00:00:00 nacl_helper
 5991 ?        00:00:00 chrome
 6033 ?        00:00:28 chrome
 6048 ?        00:00:00 chrome
 6088 ?        00:00:00 chrome
 6093 ?        00:00:25 chrome
 6106 ?        00:00:22 chrome
 6110 ?        00:00:00 chrome
 6114 ?        00:00:04 chrome
 6118 ?        00:00:05 chrome
 6122 ?        00:00:04 chrome
 6126 ?        00:00:00 chrome
 6134 ?        00:00:00 chrome
 6138 ?        00:00:10 chrome
 7615 ?        00:00:00 azureus
 7723 ?        01:33:32 java
11238 ?        00:00:06 kworker/u16:3
11337 ?        00:00:00 kworker/5:2
13389 ?        00:00:00 kworker/2:2
13511 ?        00:00:00 hp-upgrade <defunct>
15005 pts/5    02:28:36 pdsat_3.20_x86_
15632 ?        00:00:01 kworker/u16:1
15836 pts/5    01:44:31 pdsat_3.20_x86_
15885 ?        00:00:00 kworker/0:0
16214 pts/5    01:26:31 pdsat_3.20_x86_
16259 pts/5    01:24:27 pdsat_3.20_x86_
16278 pts/5    01:23:19 pdsat_3.20_x86_
16280 pts/5    01:23:20 pdsat_3.20_x86_
16330 ?        00:00:01 kworker/u16:2
16432 pts/5    01:16:47 pdsat_3.20_x86_
16886 ?        00:00:00 kworker/1:1
16889 ?        00:00:00 kworker/4:0
16890 ?        00:00:00 kworker/7:2
16951 pts/5    00:48:14 pdsat_3.20_x86_
17125 ?        00:00:00 kworker/7:0
17158 ?        00:00:00 kworker/6:0
17277 ?        00:00:00 kworker/5:0
17278 ?        00:00:00 kworker/6:2
17311 ?        00:00:00 kworker/3:1
17581 ?        00:00:00 kworker/0:2
17660 ?        00:00:00 kworker/3:2
19188 ?        00:02:09 firefox
19340 ?        00:00:00 kworker/2:1
19393 ?        00:00:00 kworker/1:2
19652 pts/6    00:00:00 bash
19667 pts/6    00:00:00 ps
28502 ?        00:00:00 cupsd


```

---

### Post by tgalati4 on 2015-11-16
Install *etherape* and examine where those packets are going.

```
sudo apt-get install etherape
etherape
```

Any open browser (like Chrome, in your process listing) will have continuous tracking traffic.  Use *firefox* with the Lightbeam plug-in and you can see the traffic.

---

### Post by coljohnhannibalsmith on 2015-11-16
> **tgalati4 said:**
> Install *etherape* and examine where those packets are going.

```
sudo apt-get install etherape
etherape
```

Any open browser (like Chrome, in your process listing) will have continuous tracking traffic.  Use *firefox* with the Lightbeam plug-in and you can see the traffic.

[COLOR=#0000cd][I]It's full of stars....

[IMG]http://www.enterprisemission.com/h_in_2001_bowman_03.jpg[/IMG]

[/I][/COLOR]Well, it's got plenty of data points. Please see the attachment. I have no idea what any of this means.

---

### Post by tgalati4 on 2015-11-16
That's internet traffic to an from your machine, broken down by IP and color-coded by packet/protocol type.  You can capture a text file (when you run it with *sudo*) or you can click on the protocol icon and get a chart with accumulated traffic categorized by protocol.  Your etherape vines show where that 30 kB are going.

Run it after a fresh boot, before opening any email or browser and check your traffic.

---

### Post by coljohnhannibalsmith on 2015-11-18
> **tgalati4 said:**
> That's internet traffic to an from your machine, broken down by IP and color-coded by packet/protocol type.  You can capture a text file (when you run it with *sudo*) or you can click on the protocol icon and get a chart with accumulated traffic categorized by protocol.  Your etherape vines show where that 30 kB are going.

Run it after a fresh boot, before opening any email or browser and check your traffic.

The etherape screenshot was taken within seconds of rebooting. The lightbeam screemshot was taken immediately after opening firefox. Kind of seems like a lot.

---

### Post by tgalati4 on 2015-11-18
Don't use Bing as your primary web search engine.  

Not sure as to why you have so much traffic after a fresh boot.  What services are you running?  I'm not familiar with I2P.

---

