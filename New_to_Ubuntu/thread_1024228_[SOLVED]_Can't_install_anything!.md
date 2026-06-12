---
title: "[SOLVED] Can't install anything!"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by esotericguy on 2008-12-28
I can't install any programs outside of add/remove... There is definitely no other installers or terminals open.  I've tried 
typing in "sudo rm /var/lib/dpkg/lock" to delete the lock. and it would delete it but when i tried again to install the program the lock file would be recreated and it wouldn't install. bring me back to square one.

I also got the advice to try ps aux and this is what i got:
```
eddie@ubuntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3056  1884 ?        Ss   16:04   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   16:04   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   16:04   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   16:04   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   16:04   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   16:04   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   16:04   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   16:04   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   16:04   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   16:04   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   16:04   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   16:04   0:00 [kintegrityd/0]
root        47  0.0  0.0      0     0 ?        S<   16:04   0:00 [kintegrityd/1]
root        49  0.0  0.0      0     0 ?        S<   16:04   0:00 [kblockd/0]
root        50  0.0  0.0      0     0 ?        S<   16:04   0:00 [kblockd/1]
root        52  0.0  0.0      0     0 ?        S<   16:04   0:00 [kacpid]
root        53  0.0  0.0      0     0 ?        S<   16:04   0:00 [kacpi_notify]
root       133  0.0  0.0      0     0 ?        S<   16:04   0:00 [cqueue]
root       137  0.0  0.0      0     0 ?        S<   16:04   0:00 [kseriod]
root       182  0.0  0.0      0     0 ?        S    16:05   0:00 [pdflush]
root       183  0.0  0.0      0     0 ?        S    16:05   0:00 [pdflush]
root       184  0.0  0.0      0     0 ?        S<   16:05   0:00 [kswapd0]
root       226  0.0  0.0      0     0 ?        S<   16:05   0:00 [aio/0]
root       227  0.0  0.0      0     0 ?        S<   16:05   0:00 [aio/1]
root      1303  0.0  0.0      0     0 ?        S<   16:05   0:00 [ksuspend_usbd]
root      1306  0.0  0.0      0     0 ?        S<   16:05   0:00 [khubd]
root      1397  0.0  0.0      0     0 ?        S<   16:05   0:00 [ata/0]
root      1398  0.0  0.0      0     0 ?        S<   16:05   0:00 [ata/1]
root      1399  0.0  0.0      0     0 ?        S<   16:05   0:00 [ata_aux]
root      2067  0.0  0.0      0     0 ?        S<   16:05   0:00 [scsi_eh_0]
root      2068  0.0  0.0      0     0 ?        S<   16:05   0:00 [scsi_eh_1]
root      2212  1.5  0.1   3744  1164 ?        Ss   16:05   0:46 mount.ntfs -o locale=en_US.utf8 /dev
root      2251  0.0  0.0      0     0 ?        S<   16:05   0:02 [loop0]
root      2253  0.0  0.0      0     0 ?        S<   16:05   0:00 [kjournald]
root      2409  0.0  0.0   2528  1020 ?        S<s  16:05   0:01 /sbin/udevd --daemon
root      2678  0.0  0.0      0     0 ?        S<   16:05   0:00 [kpsmoused]
root      2709  0.3  0.0      0     0 ?        S<   16:05   0:10 [ath5k_pci]
root      4307  0.0  0.0   1780   540 tty4     Ss+  16:06   0:00 /sbin/getty 38400 tty4
root      4308  0.0  0.0   1780   536 tty5     Ss+  16:06   0:00 /sbin/getty 38400 tty5
root      4311  0.0  0.0   1780   540 tty2     Ss+  16:06   0:00 /sbin/getty 38400 tty2
root      4314  0.0  0.0   1780   536 tty3     Ss+  16:06   0:00 /sbin/getty 38400 tty3
root      4315  0.0  0.0   1780   536 tty6     Ss+  16:06   0:00 /sbin/getty 38400 tty6
root      4495  0.0  0.1   2968  1836 ?        Ss   16:06   0:00 /usr/sbin/acpid -c /etc/acpi/events
root      4539  0.0  0.0      0     0 ?        S<   16:06   0:00 [kondemand/0]
root      4541  0.0  0.0      0     0 ?        S<   16:06   0:00 [kondemand/1]
syslog    4618  0.0  0.0   2012   676 ?        Ss   16:06   0:00 /sbin/syslogd -u syslog
root      4666  0.0  0.0   1940   540 ?        S    16:06   0:00 /bin/dd bs 1 if /proc/kmsg of /var/r
klog      4668  0.0  0.2   3504  2308 ?        Ss   16:06   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4689  0.0  0.1   2992  1256 ?        Ss   16:06   0:02 /bin/dbus-daemon --system
avahi     4709  0.0  0.1   2888  1468 ?        Ss   16:06   0:00 avahi-daemon: running [ubuntu.local]
avahi     4710  0.0  0.0   2888   496 ?        Ss   16:06   0:00 avahi-daemon: chroot helper
root      4745  0.0  0.2   6432  2380 ?        Ss   16:06   0:00 /usr/sbin/cupsd
root      4800  0.0  0.1   9216  1432 ?        Ss   16:06   0:00 /usr/sbin/winbindd
root      4811  0.0  0.1   9216  1156 ?        S    16:06   0:00 /usr/sbin/winbindd
111       4821  0.0  0.4   6296  4288 ?        Ss   16:06   0:02 /usr/sbin/hald
root      4824  0.0  0.2  17412  2572 ?        Ssl  16:06   0:00 /usr/sbin/console-kit-daemon
root      4825  0.0  0.1   3364  1108 ?        S    16:06   0:00 hald-runner
root      4907  0.0  0.1   3436  1064 ?        S    16:06   0:00 hald-addon-input: Listening on /dev/
root      4918  0.0  0.1   3448  1036 ?        S    16:06   0:00 /usr/lib/hal/hald-addon-cpufreq
111       4919  0.0  0.0   2296   944 ?        S    16:06   0:00 hald-addon-acpi: listening on acpid 
root      4969  0.0  0.1   3488  1552 ?        Ss   16:06   0:00 /usr/sbin/bluetoothd
root      4975  0.0  0.0      0     0 ?        S<   16:06   0:00 [btaddconn]
root      4977  0.0  0.0      0     0 ?        S<   16:06   0:00 [btdelconn]
root      4991  0.0  0.0      0     0 ?        S<   16:06   0:00 [krfcommd]
root      5020  0.0  0.2  14756  2640 ?        Ssl  16:06   0:01 /usr/sbin/NetworkManager
root      5029  0.0  0.1   4240  1892 ?        S    16:06   0:00 /sbin/wpa_supplicant -u -f /var/log/
root      5037  0.0  0.2   6772  2972 ?        S    16:06   0:00 /usr/sbin/nm-system-settings --confi
root      5051  0.0  0.1  14240  1784 ?        Ss   16:06   0:00 /usr/sbin/gdm
root      5054  0.0  0.3  14776  3236 ?        S    16:06   0:00 /usr/sbin/gdm
root      5071  8.3  3.3  60740 33972 tty7     Rs+  16:06   3:56 /usr/X11R6/bin/X :0 -br -audit 0 -au
root      5073  0.0  0.1   4336  1152 ?        Ss   16:06   0:00 /usr/bin/system-tools-backends
daemon    5108  0.0  0.0   2068   452 ?        Ss   16:06   0:00 /usr/sbin/atd
root      5136  0.0  0.1   3412  1028 ?        Ss   16:06   0:00 /usr/sbin/cron
root      5210  0.0  0.0   1780   536 tty1     Ss+  16:06   0:00 /sbin/getty 38400 tty1
eddie     5268  0.0  0.1  22896  2000 ?        S    16:06   0:00 /usr/bin/gnome-keyring-daemon -d --l
eddie     5279  0.0  0.5  24760  5764 ?        Ssl  16:06   0:00 x-session-manager
eddie     5357  0.0  0.0   3124   672 ?        S    16:06   0:00 /usr/bin/dbus-launch --exit-with-ses
eddie     5358  0.0  0.1   3036  1208 ?        Ss   16:06   0:00 //bin/dbus-daemon --fork --print-pid
eddie     5361  0.4  0.4  29832  4416 ?        Ssl  16:06   0:11 /usr/bin/pulseaudio -D --log-target=
eddie     5364  0.0  0.2   7528  2552 ?        S    16:06   0:00 /usr/lib/pulseaudio/pulse/gconf-help
eddie     5366  0.1  0.4   7744  4744 ?        S    16:06   0:03 /usr/lib/libgconf2-4/gconfd-2
eddie     5372  0.0  0.6  17704  6348 ?        Ss   16:06   0:00 /usr/bin/seahorse-agent --execute x-
eddie     5374  0.0  0.3  13916  3644 ?        S    16:06   0:00 /usr/lib/gnome-session/helpers/gnome
eddie     5379  0.1  2.3  54168 23720 ?        Ssl  16:06   0:03 /usr/lib/gnome-settings-daemon/gnome
eddie     5380  0.0  0.0   1844   552 ?        S    16:06   0:00 /bin/sh /usr/bin/compiz
eddie     5417  0.0  0.2   5556  2172 ?        S    16:06   0:00 /usr/lib/gvfs/gvfsd
eddie     5447  1.0  1.9  29236 20400 ?        S    16:06   0:28 /usr/bin/compiz.real --ignore-deskto
eddie     5451  0.0  0.1  29196  2036 ?        Ssl  16:06   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /hom
eddie     5467  0.2  0.3  21212  3168 ?        Ss   16:06   0:07 gnome-screensaver
eddie     5468  0.0  0.0   1844   492 ?        Ss   16:06   0:00 /bin/sh -c /usr/bin/compiz-decorator
eddie     5469  0.0  0.0   1844   524 ?        S    16:06   0:00 /bin/sh /usr/bin/compiz-decorator
eddie     5471  0.1  1.1  21080 12164 ?        S    16:06   0:03 /usr/bin/gtk-window-decorator
eddie     5472  0.2  1.9  35300 19540 ?        S    16:06   0:07 gnome-panel
eddie     5474  0.1  3.1  67508 31956 ?        S    16:06   0:03 nautilus --no-desktop --browser
eddie     5476  0.0  0.3  41616  3500 ?        Ssl  16:06   0:00 /usr/lib/bonobo-activation/bonobo-ac
eddie     5486  0.0  0.2   5936  2804 ?        S    16:06   0:00 /usr/lib/gvfs/gvfs-hal-volume-monito
eddie     5488  0.0  0.2   5560  2192 ?        S    16:06   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-mo
eddie     5491  0.0  0.2   5556  2220 ?        S    16:06   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :
eddie     5494  0.0  0.2  13996  2744 ?        S    16:06   0:00 /usr/lib/gvfs/gvfsd-trash --spawner
eddie     5504  0.0  1.5  45128 16036 ?        Sl   16:06   0:00 /usr/lib/gnome-applets/mixer_applet2
eddie     5515  0.0  0.5  15552  5584 ?        S    16:06   0:00 tracker-applet
eddie     5516  0.0  1.4  27148 15092 ?        S    16:07   0:00 update-notifier
eddie     5518  0.0  0.5  14752  5856 ?        S    16:07   0:00 bluetooth-applet
eddie     5522  0.0  1.6  26752 16660 ?        S    16:07   0:02 nm-applet --sm-disable
eddie     5527  0.0  1.0  31540 10524 ?        SNl  16:07   0:00 trackerd
eddie     5530  0.0  1.2  25484 12968 ?        S    16:07   0:00 python /usr/share/system-config-prin
eddie     5531  0.0  1.3  70668 14116 ?        Ssl  16:07   0:01 gnome-power-manager
eddie     5590 20.8 10.8 246252 111632 ?       Sl   16:07   9:37 /usr/lib/firefox-3.0.5/firefox
eddie     5593  0.1  1.4  24536 14624 ?        S    16:07   0:02 /usr/lib/notification-daemon/notific
root      5610  0.0  0.0   2252   944 ?        S    16:07   0:00 /sbin/dhclient -d -sf /usr/lib/Netwo
eddie     6022  0.0  0.7  61548  7212 ?        Sl   16:09   0:00 /usr/lib/evolution/evolution-data-se
eddie     6045  0.0  0.9  33440  9948 ?        Sl   16:09   0:00 /usr/lib/evolution/2.24/evolution-ex
eddie     6057  0.0  1.0  65192 10672 ?        Sl   16:09   0:00 /usr/lib/evolution/2.24/evolution-al
eddie     6358  5.1  2.2  78864 23000 ?        Rl   16:52   0:01 gnome-terminal
eddie     6361  0.0  0.0   2912   760 ?        S    16:52   0:00 gnome-pty-helper
eddie     6362  1.5  0.3   5744  3116 pts/0    Ss   16:52   0:00 bash
eddie     6380  0.0  0.0   2744  1020 pts/0    R+   16:53   0:00 ps aux
eddie@ubuntu:~$ ps aux | grep -i synaptic
eddie     6382  0.0  0.0   3236   868 pts/0    S+   16:53   0:00 grep -i synaptic
eddie@ubuntu:~$ ps aux | grep -i apt
eddie     6384  0.0  0.0   3236   864 pts/0    S+   16:54   0:00 grep -i apt
eddie@ubuntu:~$ 

```

I then tried installing a couple things and this error came up:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

I no little to nothing about linux at this point so any help is appreciated.
tips tricks and help?

---

### Post by tuxxy on 2008-12-28
Run the following command in terminal and try again

```
sudo dpkg --configure -a
```

---

### Post by taurus on 2008-12-28
Run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by pdtpatrick on 2008-12-28
sudo dkpg --configure -a 

also after .. run sudo apt-get update

then sudo dkpg -i <package your are trying to install>

---

