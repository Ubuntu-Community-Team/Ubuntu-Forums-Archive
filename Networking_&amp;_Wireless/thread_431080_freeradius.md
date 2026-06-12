---
title: "freeradius"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by rugby82 on 2007-05-02
hallo i have a problem with freeradius!!!!

when i launch: "freeradius -x" it give me 
[HTML]in: lower_user = "no"
 main: lower_pass = "no"
 main: nospace_user = "no"
 main: nospace_pass = "no"
 main: checkrad = "/usr/sbin/checkrad"
 main: proxy_requests = yes
 proxy: retry_delay = 5
 proxy: retry_count = 3
 proxy: synchronous = no
 proxy: default_fallback = yes
 proxy: dead_time = 120
 proxy: post_proxy_authorize = no
 proxy: wake_all_if_all_dead = no
 security: max_attributes = 200
 security: reject_delay = 1
 security: status_server = no
 main: debug_level = 0
read_config_files:  reading dictionary
read_config_files:  reading naslist
Using deprecated naslist file.  Support for this will go away soon.
read_config_files:  reading clients
read_config_files:  reading realms
There appears to be another RADIUS server running on the authentication port 1812
[/HTML]
what mean? 
ps aux give me 
[HTML]USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1568   528 ?        S    May02   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   May02   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    May02   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   May02   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   May02   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   May02   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   May02   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   May02   0:00 [kacpid]
root       108  0.0  0.0      0     0 ?        S    May02   0:00 [pdflush]
root       109  0.0  0.0      0     0 ?        S    May02   0:00 [pdflush]
root       111  0.0  0.0      0     0 ?        S<   May02   0:00 [aio/0]
root       110  0.0  0.0      0     0 ?        S    May02   0:00 [kswapd0]
root       698  0.0  0.0      0     0 ?        S<   May02   0:00 [kseriod]
root      1809  0.0  0.0      0     0 ?        S<   May02   0:00 [scsi_eh_0]
root      1826  0.0  0.0      0     0 ?        S<   May02   0:00 [khubd]
root      1897  0.0  0.0      0     0 ?        S    May02   0:00 [kjournald]
root      2125  0.0  0.1   2432   920 ?        S<s  May02   0:00 /sbin/udevd --daemon
root      2937  0.0  0.0      0     0 ?        S    May02   0:00 [shpchpd_event]
root      2995  0.0  0.0      0     0 ?        S<   May02   0:00 [kgameportd]
root      3773  0.0  0.2   2156  1200 ?        Ss   May02   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
dhcp      3873  0.0  0.1   2336   788 ?        S<s  May02   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
syslog    3875  0.0  0.1   1768   672 ?        Ss   May02   0:00 /sbin/syslogd -u syslog
root      3912  0.0  0.0   1676   492 ?        Ss   May02   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3914  0.0  0.2   2392  1312 ?        Ss   May02   0:00 /sbin/klogd -P /var/run/klogd/kmsg
104       3933  0.0  0.1   2188   852 ?        Ss   May02   0:00 /usr/bin/dbus-daemon --system
108       3948  0.0  1.0   6760  5356 ?        Ss   May02   0:01 /usr/sbin/hald
root      3949  0.0  0.1   2720   980 ?        S    May02   0:00 hald-runner
108       3954  0.0  0.1   2000   788 ?        S    May02   0:00 /usr/lib/hal/hald-addon-acpi
108       4004  0.0  0.1   2000   788 ?        S    May02   0:00 /usr/lib/hal/hald-addon-keyboard
108       4015  0.0  0.1   2008   860 ?        S    May02   0:00 /usr/lib/hal/hald-addon-storage
108       4016  0.0  0.1   2004   860 ?        S    May02   0:00 /usr/lib/hal/hald-addon-storage
108       4018  0.0  0.1   2004   816 ?        S    May02   0:00 /usr/lib/hal/hald-addon-storage
108       4019  0.0  0.1   2004   812 ?        S    May02   0:00 /usr/lib/hal/hald-addon-storage
root      4343  0.0  0.3  10908  1800 ?        Ss   May02   0:00 /usr/sbin/gdm
root      4372  0.0  0.5  11348  2692 ?        S    May02   0:00 /usr/sbin/gdm
root      4377  2.9  5.2  32288 26860 tty7     Rs+  May02   2:43 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
hplip     4386  0.0  0.1  12876   920 ?        Ssl  May02   0:00 /usr/sbin/hpiod
hplip     4390  0.0  0.9   9412  4672 ?        S    May02   0:00 python /usr/sbin/hpssd
cupsys    4437  0.0  0.3   4200  1784 ?        Ss   May02   0:00 /usr/sbin/cupsd
root      4522  0.0  0.1   1968   704 ?        Ss   May02   0:00 hcid: processing events
root      4526  0.0  0.0   1616   456 ?        Ss   May02   0:00 /usr/sbin/sdpd
root      4537  0.0  0.0      0     0 ?        S<   May02   0:00 [krfcommd]
root      4550  0.0  0.0   1628   296 ?        Ss   May02   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
freerad   4577  0.0  0.2  44296  1508 ?        Ssl  May02   0:00 /usr/sbin/freeradius
daemon    4613  0.0  0.0   1796   392 ?        Ss   May02   0:00 /usr/sbin/atd
root      4626  0.0  0.1   2116   836 ?        Ss   May02   0:00 /usr/sbin/cron
root      4671  0.0  0.7  11796  3672 ?        Ss   May02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4718  0.0  0.4  11796  2264 ?        S    May02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4719  0.0  0.4  11796  2264 ?        S    May02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4720  0.0  0.4  11796  2264 ?        S    May02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4721  0.0  0.4  11796  2264 ?        S    May02   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4722  0.0  0.4  11796  2264 ?        S    May02   0:00 /usr/sbin/apache2 -k start -DSSL
root      4742  0.0  0.0   1560   492 tty1     Ss+  May02   0:00 /sbin/getty 38400 tty1
root      4743  0.0  0.0   1564   492 tty2     Ss+  May02   0:00 /sbin/getty 38400 tty2
root      4744  0.0  0.0   1564   496 tty3     Ss+  May02   0:00 /sbin/getty 38400 tty3
root      4745  0.0  0.0   1564   492 tty4     Ss+  May02   0:00 /sbin/getty 38400 tty4
root      4746  0.0  0.0   1564   496 tty5     Ss+  May02   0:00 /sbin/getty 38400 tty5
root      4747  0.0  0.0   1564   496 tty6     Ss+  May02   0:00 /sbin/getty 38400 tty6
giulio    4766  0.0  2.1  20788 11240 ?        Ss   May02   0:01 x-session-manager
giulio    4808  0.0  0.1   4332   692 ?        Ss   May02   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
giulio    4811  0.0  0.1   2708   648 ?        S    May02   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
giulio    4812  0.0  0.1   2188   900 ?        Ss   May02   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
giulio    4814  0.0  0.8   6652  4128 ?        S    May02   0:00 /usr/lib/libgconf2-4/gconfd-2 5
giulio    4817  0.0  0.5   6508  3092 ?        Ss   May02   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=15
giulio    4819  0.2  1.6  15372  8708 ?        S    May02   0:09 /usr/lib/at-spi/at-spi-registryd --oaf-activate-iid=OAFIID:Accessibility_Registry:1.0 --oaf-giulio    4821  0.0  0.1   2336   724 ?        S    May02   0:00 /usr/bin/gnome-keyring-daemon
giulio    4823  0.0  1.9  28552 10196 ?        Sl   May02   0:02 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemongiulio    4827  0.0  0.8   5936  4536 ?        SL   May02   0:00 /usr/bin/esd -nobeeps
giulio    4832  0.0  0.0   2948   480 ?        Ss   May02   0:00 /usr/bin/esd -nobeeps
giulio    4835  0.4  2.6  26712 13536 ?        Ss   May02   0:19 /usr/bin/metacity --sm-client-id=default0
giulio    4847  0.3  4.7  52816 24268 ?        Ssl  May02   0:13 gnome-panel --sm-client-id default1
giulio    4849  0.0  3.6  76064 18660 ?        Ssl  May02   0:02 nautilus --no-default-window --sm-client-id default2
giulio    4852  0.0  1.1  18468  5712 ?        Ss   May02   0:00 gnome-volume-manager --sm-client-id default4
giulio    4871  0.0  2.2  20312 11436 ?        Ss   May02   0:01 update-notifier
giulio    4874  0.0  0.7   8872  4012 ?        Sl   May02   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory -giulio    4881  0.0  1.7  55308  9008 ?        Ss   May02   0:00 gnome-cups-icon --sm-client-id default3
giulio    4893  0.0  1.8  38972  9520 ?        Sl   May02   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factorygiulio    4907  0.0  1.1  18824  5780 ?        Ss   May02   0:00 gnome-power-manager
giulio    4910  0.0  0.1   2280   796 ?        S    May02   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
giulio    4919  0.0  1.6  18568  8684 ?        S    May02   0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Fagiulio    4921  0.0  2.3  32352 12024 ?        S    May02   0:02 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID:GNOME_StickyNotesApplet_giulio    4923  0.0  2.3  33208 12228 ?        S    May02   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --ogiulio    4927  0.0  2.3  24672 12020 ?        S    May02   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-giulio    4929  2.8 13.8 171052 71560 ?        Sl   May02   1:55 /usr/lib/firefox/firefox-bin -a firefox
giulio    4949  0.0  0.6  16064  3128 ?        Ss   May02   0:02 gnome-screensaver
giulio    5352  0.4  3.2  46868 17020 ?        Rl   May02   0:14 gnome-terminal
giulio    5355  0.0  0.1   2280   680 ?        S    May02   0:00 gnome-pty-helper
giulio    5356  0.0  0.6   5788  3376 pts/0    Ss   May02   0:00 bash
root      5480  0.0  0.2   3688  1204 pts/0    S    May02   0:00 su
root      5481  0.0  0.3   3988  1900 pts/0    S    May02   0:00 bash
root      5505  0.0  0.5   6380  3020 ?        Ss   May02   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=12
root      5507  0.0  1.1  12652  5904 ?        S    May02   0:02 /usr/lib/at-spi/at-spi-registryd --oaf-activate-iid=OAFIID:Accessibility_Registry:1.0 --oaf-root      5764  0.0  0.3   3508  1556 pts/0    S+   May02   0:00 man radiusd
root      5772  0.0  0.1   3024   996 pts/0    S+   May02   0:00 pager -s
giulio    6656  0.0  0.6   5788  3348 pts/1    Ss   00:13   0:00 bash
giulio    6991  0.0  0.1   2392  1016 pts/1    R+   00:25   0:00 ps aux
[/HTML] thank you

---

