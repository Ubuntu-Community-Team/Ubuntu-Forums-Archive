---
title: "Apache2 cpu problem"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2008-12-09
I recently tried installing Apache 2, because I use graphics packs for online games, and I can use Apache to load the graphics pack via [http://localhost](http://localhost). So I downloaded the program, configured, made, installed, and I went to move my files into the htdocs folder, just like I did on windows. It didn't work. So I went to Google for help and found this: [http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/)
I followed that walkthrough and it all installed fine. I then used gksu nautilus to be able to move the graphics pack to the folder where Apache2 was this time(it was in a different place this time). I started AstroEmpires(the game using the graphics pack) and it loaded it only one massive problem. Ubuntu slows to a crawl and my dual core 2.1ghz processors go to 100% and the system slows down so much that you can't open anything, click any links, or even kill the firefox process, unless you wait like five minutes for the system to catch up. I want to be able to use Apache so I can load the graphics pack into AstroEmpires, but I don want my comp slowing down to such a dreadful speed, I'm pretty sure Apache2 doesn't take up that much CPU usage as I have been using it in windows for about a year doing the same time, so I have no idea what I could have done wrong. Any help would be greatly appreciated.

---

### Post by stevoo on 2008-12-09
Scratch everything and start from scratch ... 

You have a too vague reason in what you are telling us. It could be anything.

So i would try to remove apache and resintalling it :)

---

### Post by MasterShihoChief on 2008-12-09
Ok i used the same guide i used in reverse and replaced apt-get install with apt-get remove. Everything was removed and then i only installed apache2 this time with apt-get. I went to the var/www folder to copy the files back and they were already there, i guess they were never deleted. So I tried using them on the game, and again the computer screeched to a halt.

---

### Post by stevoo on 2008-12-09
what exactly are you doing to use them on the game ? 
Are you doing it from the shell ? any errors coming out ? can you go into the shell and do a ps aux to see the process that is killing the pc.

---

### Post by MasterShihoChief on 2008-12-09
I took the following while the problem was occuring. The system took a full minute to respond, and both cores went straight to 100% usage.Problem is there isn't anything in the processes that is using that much, they aren't even using that much put together. As for the use in the game, all i do is drop an image pack into the /var/www that way they are accessible through [http://localhost](http://localhost). So for example when i go into my game account to activate the pack i type in [http://localhost/AstroEmpires](http://localhost/AstroEmpires), and then instead of always downloading images from the server, which slows it down, it loads the images from my hdd. Nothing very intensive thats for sure.

mastershihochief@CortanaMobile:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3056  1884 ?        Ss   Dec08   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Dec08   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Dec08   0:09 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Dec08   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Dec08   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   Dec08   0:10 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   Dec08   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   Dec08   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   Dec08   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   Dec08   0:00 [khelper]
root        51  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kintegrityd/0]
root        52  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kintegrityd/1]
root        54  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kblockd/0]
root        55  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kblockd/1]
root        57  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kacpid]
root        58  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kacpi_notify]
root       165  0.0  0.0      0     0 ?        S<   Dec08   0:00 [cqueue]
root       169  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kseriod]
root       215  0.0  0.0      0     0 ?        S    Dec08   0:02 [pdflush]
root       216  0.0  0.0      0     0 ?        S<   Dec08   0:02 [kswapd0]
root       258  0.0  0.0      0     0 ?        S<   Dec08   0:00 [aio/0]
root       259  0.0  0.0      0     0 ?        S<   Dec08   0:00 [aio/1]
root      1251  0.0  0.0      0     0 ?        S<   Dec08   0:00 [ksuspend_usbd]
root      1259  0.0  0.0      0     0 ?        S<   Dec08   0:00 [khubd]
root      1287  0.0  0.0      0     0 ?        S<   Dec08   0:00 [ata/0]
root      1288  0.0  0.0      0     0 ?        S<   Dec08   0:00 [ata/1]
root      1289  0.0  0.0      0     0 ?        S<   Dec08   0:00 [ata_aux]
root      1321  0.0  0.0      0     0 ?        S<   Dec08   0:00 [khpsbpkt]
1000      1499  9.4  5.4 264216 113584 ?       Sl   01:20  13:54 /usr/lib/firefox-3.0.4/firefox
root      2056  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_0]
root      2057  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_1]
root      2058  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_2]
root      2120  0.0  0.0      0     0 ?        S<   Dec08   0:01 [scsi_eh_3]
root      2144  0.0  0.0      0     0 ?        S<   Dec08   0:00 [knodemgrd_0]
root      2160  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_4]
root      2161  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_5]
root      2305  0.0  0.0      0     0 ?        S<   Dec08   0:04 [kjournald]
root      2479  0.0  0.0   2536  1028 ?        S<s  Dec08   0:00 /sbin/udevd --daemon
root      2692  0.0  0.0      0     0 ?        S<   Dec08   0:00 [led_workqueue]
root      2987  0.0  0.0      0     0 ?        S<   Dec08   0:00 [btaddconn]
root      2988  0.0  0.0      0     0 ?        S<   Dec08   0:00 [btdelconn]
root      3014  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kpsmoused]
root      3022  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_6]
root      3023  0.0  0.0      0     0 ?        S<   Dec08   0:00 [usb-storage]
root      3029  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_8]
root      3030  0.0  0.0      0     0 ?        S<   Dec08   0:00 [usb-storage]
root      3168  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kmmcd]
root      3213  0.0  0.0      0     0 ?        S<   Dec08   0:02 [iwlagn/0]
root      3214  0.0  0.0      0     0 ?        S<   Dec08   0:02 [iwlagn/1]
root      3215  0.0  0.0      0     0 ?        S<   Dec08   0:07 [iwlagn]
1000      4381  0.1  3.5 200104 72544 ?        Sl   02:42   0:07 /usr/lib/openoffice/program/soffice.bin -writer file:///media/CORTANAMINI/Piracy.doc -splash-pipe=5
root      4424  0.0  0.0   4120  1392 ?        Ss   Dec08   0:46 /sbin/mount.ntfs-3g /dev/sda1 /media/WINXP -o rw,locale=en_US.UTF-8
root      4428  0.0  0.0   3900  1040 ?        Ss   Dec08   0:00 /sbin/mount.ntfs-3g /dev/sda2 /media/Respawn Recovery -o rw,locale=en_US.UTF-8
root      4819  0.0  0.0   1780   532 tty4     Ss+  Dec08   0:00 /sbin/getty 38400 tty4
root      4820  0.0  0.0   1780   532 tty5     Ss+  Dec08   0:00 /sbin/getty 38400 tty5
root      4823  0.0  0.0   1780   536 tty2     Ss+  Dec08   0:00 /sbin/getty 38400 tty2
root      4824  0.0  0.0   1780   540 tty3     Ss+  Dec08   0:00 /sbin/getty 38400 tty3
root      4825  0.0  0.0   1780   540 tty6     Ss+  Dec08   0:00 /sbin/getty 38400 tty6
root      5004  0.0  0.0   2968  1896 ?        Ss   Dec08   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5038  0.0  0.0      0     0 ?        S<   Dec08   0:07 [kondemand/0]
root      5040  0.0  0.0      0     0 ?        S<   Dec08   0:00 [kondemand/1]
syslog    5129  0.0  0.0   2012   676 ?        Ss   Dec08   0:00 /sbin/syslogd -u syslog
root      5183  0.0  0.0   1940   544 ?        S    Dec08   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5185  0.0  0.1   4308  3048 ?        Ss   Dec08   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5208  0.0  0.0   3080  1316 ?        Ss   Dec08   0:15 /bin/dbus-daemon --system
avahi     5230  0.0  0.0   3000  1532 ?        Ss   Dec08   0:00 avahi-daemon: running [CortanaMobile.local]
avahi     5231  0.0  0.0   2888   496 ?        Ss   Dec08   0:00 avahi-daemon: chroot helper
root      5278  0.0  0.1   6708  2676 ?        Ss   Dec08   0:00 /usr/sbin/cupsd
root      5428  0.0  0.0   9216  1432 ?        Ss   Dec08   0:00 /usr/sbin/winbindd
root      5450  0.0  0.0   9216  1152 ?        S    Dec08   0:00 /usr/sbin/winbindd
111       5451  0.0  0.2   6608  4696 ?        Ss   Dec08   0:11 /usr/sbin/hald
root      5454  0.0  0.1  17480  2608 ?        Ssl  Dec08   0:00 /usr/sbin/console-kit-daemon
root      5455  0.0  0.0   3364  1172 ?        S    Dec08   0:00 hald-runner
root      5543  0.0  0.0   3436  1076 ?        S    Dec08   0:00 hald-addon-input: Listening on /dev/input/event2 /dev/input/event5 /dev/input/event4 /dev/input/event3 /dev/input/event1
root      5546  0.0  0.0   3448  1040 ?        S    Dec08   0:00 /usr/lib/hal/hald-addon-cpufreq
111       5547  0.0  0.0   2296   944 ?        S    Dec08   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5567  0.0  0.0   3440  1168 ?        S    Dec08   0:13 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5570  0.0  0.0   3440  1056 ?        S    Dec08   0:02 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      5580  0.0  0.0   3440  1056 ?        S    Dec08   0:02 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      5622  0.0  0.0   3488  1712 ?        Ss   Dec08   0:00 /usr/sbin/bluetoothd
root      5636  0.0  0.0      0     0 ?        S<   Dec08   0:00 [krfcommd]
root      5677  0.0  0.1  14764  2700 ?        Ssl  Dec08   0:15 /usr/sbin/NetworkManager
root      5687  0.0  0.0   4240  1892 ?        S    Dec08   0:03 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      5689  0.0  0.1   6768  2980 ?        S    Dec08   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      5716  0.0  0.0  14240  1780 ?        Ss   Dec08   0:00 /usr/sbin/gdm
root      5719  0.0  0.1  14784  3240 ?        S    Dec08   0:00 /usr/sbin/gdm
root      5724 17.3  3.9  94068 81164 tty7     RLs+ Dec08 146:24 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5739  0.0  0.0   4336  1152 ?        Ss   Dec08   0:00 /usr/bin/system-tools-backends
daemon    5774  0.0  0.0   2068   456 ?        Ss   Dec08   0:00 /usr/sbin/atd
root      5802  0.0  0.0   3412  1024 ?        Ss   Dec08   0:00 /usr/sbin/cron
root      5878  0.0  0.0   1780   536 tty1     Ss+  Dec08   0:00 /sbin/getty 38400 tty1
1000      5984  0.0  0.1  14700  2196 ?        S    Dec08   0:00 /usr/bin/gnome-keyring-daemon -d --login
1000      5995  0.0  0.0   4356  1540 ?        Ss   Dec08   0:00 /bin/bash /usr/bin/keytouchd-launch x-session-manager
1000      6105  0.0  0.0   3124   684 ?        S    Dec08   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/keytouchd-launch x-ses
1000      6106  0.0  0.0   3160  1396 ?        Ss   Dec08   0:01 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
1000      6114  0.0  0.2   7800  4812 ?        S    Dec08   0:14 /usr/lib/libgconf2-4/gconfd-2
1000      6120  0.0  0.3  17728  6348 ?        Ss   Dec08   0:00 /usr/bin/seahorse-agent --execute /usr/bin/keytouchd-launch x-session-manager
1000      6122  0.0  0.7  33608 15240 ?        Sl   Dec08   0:00 x-session-manager
1000      6124  0.0  0.1  13916  3644 ?        S    Dec08   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
1000      6129  0.0  0.7  44988 15224 ?        Ssl  Dec08   0:20 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
1000      6161  0.0  0.1   6480  3016 ?        S    Dec08   0:00 /usr/lib/gvfs/gvfsd
1000      6173  0.0  0.1  37660  2368 ?        Ssl  Dec08   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/mastershihochief/.gvfs
1000      6211  0.2  0.3  21912  6872 ?        Ss   Dec08   1:48 gnome-screensaver
1000      6292  0.3  1.6  75736 34248 ?        S    Dec08   2:32 gnome-panel
1000      6298  0.2  2.2 104200 45680 ?        Sl   Dec08   1:49 nautilus --no-desktop --browser
1000      6314  0.0  0.1  33504  3492 ?        Ssl  Dec08   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
1000      6409  0.0  0.1  23732  3372 ?        Sl   Dec08   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
1000      6439  0.0  0.1   5904  2652 ?        S    Dec08   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1000      6443  0.0  0.5  23196 10936 ?        S    Dec08   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=20
1000      6445  0.0  0.1   5556  2224 ?        S    Dec08   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.11 /org/gtk/gvfs/exec_spaw/0
1000      6447  0.0  0.1  23216  2812 ?        S    Dec08   0:03 /usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/gvfs/exec_spaw/1
root      6575  0.0  0.1  13484  2892 ?        Ss   03:31   0:00 /usr/sbin/apache2 -k start
www-data  6577  0.0  0.1  13256  2184 ?        S    03:31   0:00 /usr/sbin/apache2 -k start
www-data  6580  0.0  0.1 234836  3228 ?        Sl   03:31   0:00 /usr/sbin/apache2 -k start
www-data  6583  0.0  0.1 234976  3324 ?        Sl   03:31   0:00 /usr/sbin/apache2 -k start
1000      6585  0.0  0.7  26928 14640 ?        S    Dec08   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-f
1000      6682  0.0  0.8  38488 17228 ?        S    Dec08   0:34 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=22
1000      6825  0.0  0.6  25456 13008 ?        S    Dec08   0:00 python /usr/share/system-config-printer/applet.py
1000      6826  0.0  0.2  15560  5584 ?        S    Dec08   0:00 tracker-applet
1000      6827  0.0  0.5  31928 10516 ?        SNl  Dec08   0:00 trackerd
1000      6829  0.0  0.5  65324 10688 ?        Sl   Dec08   0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
1000      6835  0.0  0.4  18972  9384 ?        S    Dec08   0:00 bluetooth-applet
1000      6858  0.0  0.7  27596 15488 ?        S    Dec08   0:02 update-notifier
1000      6860  0.0  0.8  28140 17776 ?        S    Dec08   0:05 nm-applet --sm-disable
1000      6865  0.0  0.5  26328 11864 ?        Ss   Dec08   0:02 gnome-power-manager
1000      7007  0.0  0.7  25064 14976 ?        S    Dec08   0:09 /usr/lib/notification-daemon/notification-daemon
1000      7054  0.0  0.4  40612 10276 ?        Sl   Dec08   0:00 /usr/lib/evolution/2.24/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --
1000      7060  0.0  0.3  69744  7420 ?        Sl   Dec08   0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=29
1000      7267  1.0  1.1  92152 23356 ?        Sl   03:47   0:00 gnome-terminal
1000      7270  0.0  0.0   2912   764 ?        S    03:47   0:00 gnome-pty-helper
1000      7271  0.1  0.1   6416  3784 pts/0    Ss   03:47   0:00 bash
1000      7333  0.0  0.0   2744  1016 pts/0    R+   03:48   0:00 ps aux
1000      7995  0.1  1.4  67240 30652 ?        S    Dec08   0:58 emerald --replace
1000      8065  1.6  2.0  60812 42376 ?        Sl   Dec08  14:08 wish8.5 /usr/bin/amsn
1000      8588  0.5  1.2  47208 24988 ?        Sl   Dec08   4:08 xchat
1000      8716  0.0  0.1   8344  2544 ?        S    Dec08   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.11 /org/gtk/gvfs/exec_spaw/4
root     10170  0.0  0.0      0     0 ?        S<   Dec08   0:00 [scsi_eh_9]
root     10172  0.0  0.0      0     0 ?        S<   Dec08   0:00 [usb-storage]
root     10216  0.0  0.0   3440  1060 ?        S    Dec08   0:02 hald-addon-storage: polling /dev/sdd (every 2 sec)
1000     17895  0.0  0.0   1844   552 ?        S    Dec08   0:00 /bin/sh /usr/bin/compiz --replace
1000     17946  7.2  3.1  97816 66128 ?        SL   Dec08  38:06 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --replace core ccp
1000     20655  0.0  0.4  21180  9064 ?        S    Dec08   0:00 /usr/bin/seahorse-daemon -d
1000     22196  0.0  0.1  14752  3332 ?        S    Dec08   0:00 /usr/lib/gvfs/gvfsd-archive file=file:///home/mastershihochief/Desktop/Warcraft%20III%20Reign%20of%20Chaos,%20The%20Frozen%20Thro
root     28757  0.0  0.0   3124   696 ?        S    00:02   0:00 dbus-launch --autolaunch 7a83ff2088354c9391e991b14934d326 --binary-syntax --close-stderr
root     28758  0.0  0.0   2640   768 ?        Ss   00:02   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root     29057  0.0  0.0      0     0 ?        S    00:08   0:00 [pdflush]
1000     32048 11.3  3.0 143792 63516 ?        SLl  00:44  20:51 amarokapp
1000     32051  0.0  0.2  25428  5228 ?        Ss   00:44   0:00 kdeinit Running...                      
1000     32055  0.0  0.1  25056  4056 ?        S    00:44   0:00 dcopserver [kdeinit] --nosid --suicide  
1000     32058  0.0  0.3  25732  6344 ?        S    00:44   0:00 klauncher [kdeinit] --new-startup       
1000     32060  0.0  0.4  27048  8396 ?        S    00:44   0:02 kded [kdeinit] --new-startup            
1000     32066  0.0  0.6  29688 12480 ?        S    00:44   0:00 kio_uiserver [kdeinit]                  
1000     32068  0.0  0.2  25732  5352 ?        S    00:44   0:00 kio_file [kdeinit] file /tmp/ksocket-m  
1000     32080  0.0  0.1   4460  2832 ?        S    00:44   0:00 ruby /usr/share/apps/amarok/scripts/score_default/score_default.rb
root     32555  0.0  0.0   5392  1032 ?        Ss   00:52   0:00 /usr/sbin/sshd
root     32717  0.0  0.0   2252   944 ?        S    00:53   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/run/dhclient-eth0.lea
mastershihochief@CortanaMobile:~$

---

### Post by MasterShihoChief on 2008-12-09
Ok i did a htop and found that whenever that web game tab in firefox is the active window being used, the following process goes to 100% cpu usage and is responsible for the massive slow down of my computer. When i click a nother program or another tab in firefox, the process immediately goes back down to normal cpu usage. Any help with this xorg problem would be greatly appreciated

root      5724 15.9  3.7  90252 77144 tty7     SLs+ Dec08 237:38 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

---

### Post by MasterShihoChief on 2008-12-09
It seems that no one seems to want to help me here or on irc, and I'm frankly started to get a little irritated as I have been trying to fix it for days, and I have been asking for help here and on irc all day and it seems I just get ignored. I am almost ready to just say screw it but I really want to have this X problem fixed, so is there anyone who can help me fix this?


I have attached pictures this time so you can see. The first pic shows the problem and shows x hogging the processor. It also shows you the web game I have open. As I have said in my previous posts, I am having firefox load images i dropped into my var/www folder so that i can access them from [http://localhost](http://localhost) and load them into the game, instead of loading them from the server, as the server is slow. I had no problems like this on windows xp, or vista, it seems i only get this issue in ubuntu 8.10 intrepid. The second image i have attached is when i click on another tab, and you see the game tab is still open but its not active so x falls down to normal cpu usage.

Please help me I have wasted my entire day tinkering with install/reinstall/ config files i dont understand, and being ignored on irc and on the forums, if anyone has any ideas at all please help me. Thanks very much.
<mastershihochief> [http://i38.tinypic.com/qn6w4z.jpg](http://i38.tinypic.com/qn6w4z.jpg)   <<<my problem; [http://i33.tinypic.com/2rgnxw7.jpg](http://i33.tinypic.com/2rgnxw7.jpg)  <<< What it is when that tab isnt active

---

### Post by MasterShihoChief on 2008-12-09
Ok i'm really sick of not getting help, everyone tells me oh linux is good you will get help and have your issue fixed in like a few hours. I have spent all day trying to fix this stuff and have been begging for help as i have been using it for only a week. Guess what everyone and their damn dog ignores me. ](*,)

I am having this issue which was ignored: [http://ubuntuforums.org/showthread.php?t=1006215](http://ubuntuforums.org/showthread.php?t=1006215)

Now my system froze and i had to restart and guess what now nothing works. The environment is all screwed up as hell. All the windows and bars all keep blinking like they are stuck in a looping refresh without end. I have no desktop icons that i used to have there, that if you open the destop folder show up. My compiz cube is buted, and my effects keep being reset all the time. My ubuntu 8.10 intrepid is busted and is bricked. I am so frustrated i have picked up this POS laptop, have taken outside to the pool area and am ready to chuck it in and be done with this crap. Please help me I have had enough of being ignored, and genuinely need help. I'm pretty sure its an X problem. Thanks very much.

---

### Post by gettinoriginal on 2008-12-09
Ignore

---

### Post by gettinoriginal on 2008-12-09
Ignore

---

### Post by overdrank on 2008-12-09
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by modmadmike on 2008-12-09
I would try to help but I cant figure it out by myself. The closest thing to your problem was with a bad video card in windows that would Overload the cpu whenever a DirectX game ran (the biggest trigger was WoW)- no bluescreen or anything just a system overload on a quad core pc. The game is running on a different PC and the one with the problem is the Apache server right? If so try running a live CD or USB key with Apache and if it works then then its install related if not its linux hardware compatibility. Sorry for not being of much help :(

---

### Post by MasterShihoChief on 2008-12-09
I ran exaclty what you said, but I guess it couldn't connect to the repos or something cuz it errored on the fixing packages part when trying to read from them. I also did the fix x server and that ran fine. I am now able to boot into ubuntu again and actually be able to use it without the windows disappearing and reappearing every few seconds. However the desktop icons that should be there are not there, unless you look in the desktop folder itself. I can't right click on the desktop (though i dont remember if i could ever right click on the desktop itself and not the icons) My compiz settings are shot, and even though I put all the settings back into compiz for the cube it doesn't come back. Good news on the original problem. xorg doesnt gobble up all my cpu when i run apache2 on that game :). So now I need to figure out how to fix compiz, and bring back my desktop and then it will be back to being perfect ^^

---

### Post by modmadmike on 2008-12-09
> **MasterShihoChief said:**
> I ran exaclty what you said, but I guess it couldn't connect to the repos or something cuz it errored on the fixing packages part when trying to read from them. I also did the fix x server and that ran fine. I am now able to boot into ubuntu again and actually be able to use it without the windows disappearing and reappearing every few seconds. However the desktop icons that should be there are not there, unless you look in the desktop folder itself. I can't right click on the desktop (though i dont remember if i could ever right click on the desktop itself and not the icons) My compiz settings are shot, and even though I put all the settings back into compiz for the cube it doesn't come back. Good news on the original problem. xorg doesnt gobble up all my cpu when i run apache2 on that game :). So now I need to figure out how to fix compiz, and bring back my desktop and then it will be back to being perfect ^^

Try killing nautilus (sudo killall nautilus) and then restarting it (nautilus) if that does not work then try loging on through a different Terminal
1. press ctrl+alt+F1 
2. logon
3. sudo killall gdm
4. startx (if that wont run sudo rm -rf /tmp/.X0-lock) (if it still wont run type sudo startx)

Or you can just make a new User and copy the files over

---

### Post by MasterShihoChief on 2008-12-09
ok so i guess i needed to reinstall the nvidia drivers so i did so, and restarted. I came back and the desktop came back. But guess what? Hello to the blinking windows again. What i notice is compiz is freaking out switching between the cube settings and its default settings and it kept doing that until i turned off video effects in system>preferences>appearance

Now i have 8 desktops at the bottom right hand corner, and i will try to fix compiz settings again, then try to do compiz --replace after i re-enable full video effects again.

---

### Post by MasterShihoChief on 2008-12-09
I can't stop the blinking now. The moment I types compiz --replace it's stuck in a infinite refresh loop so I can't use anything now. There's something wrong with either compiz or the nvidia drivers but I honestly am so lost now I don't know what to do. I can't use the system again X_X

Sent from my iPhone.

---

### Post by rev0lv3r on 2008-12-09
Worth a shot

Try xUbuntu or kUbuntu (former first, it'll probably be quicker)

Maybe your problem is gnome desktop manager?

---

### Post by MasterShihoChief on 2008-12-09
ok now everything is busted again. Apache 2 problem is back and xorg is eating 100% cpu when i go to that game, this was after i re-installed the recommended nvidia driver from System>Administration>Hardware Drivers . The compiz is FUBAR. I have 8 desktops but the settings in the compiz setting manager show 4.  I only recovered by luckily typing in emerald --replace very slowly between the refreshes. Sigh.... What a big mess. I tried ubuntu a year ago with a different computer and had ati driver and x org issues back then too, and i gave up on linux then. I dont want to get rid of my ubuntu because of these problems, it was working perfectly fine a couple days ago. Any other ideas?

---

### Post by modmadmike on 2008-12-09
I had the same problems with my Eee-PC try updating Compiz from the terminal (Ctrl-alt-F1) then typing sudo apt-get update compiz. Also what GPU are you using. Don't try switching WM's if you are comfortable with gnome just try to fix compiz. Also download the new nvidia linux drivers (not the ones from synaptic but from nvidia.com) and install them using the instructions from the site.

---

### Post by rev0lv3r on 2008-12-09
Ohhh
You have compiz enabled
Might want to disable all of that fancy stuff for troubleshooting purposes for right now

I know there are some (3d games) games I play that compiz breaks.

---

### Post by modmadmike on 2008-12-09
Before you install the official drivers be sure to remove the old ones.

---

### Post by modmadmike on 2008-12-09
> **rev0lv3r said:**
> Ohhh
You have compiz enabled
Might want to disable all of that fancy stuff for troubleshooting purposes for right now

I know there are some (3d games) games I play that compiz breaks.

he needs to uninstall it from the terminal because as he said he has no GUI.

---

### Post by modmadmike on 2008-12-09
Im going to have to go to school at 6 am tomorrow and everything is barracuda'd so I cant help you till 2:30pm EST

---

### Post by MasterShihoChief on 2008-12-09
no i have gui now, its just when i go to use compiz again the gui refreshes and blinks like crazy so its like i have no gui cuz theres times when everything vanishes for minutes and comes back and then vanishes again. The old drivers werent there, it said there were no drivers installed so thats why i installed them from hardware drivers menu. Now like i said if i use compiz or enable visual effects with this new driver i get the refresh problem

---

### Post by modmadmike on 2008-12-09
as i said install them from the NVIDIA site not from Ubuntu itself.

---

### Post by rev0lv3r on 2008-12-09
> **MasterShihoChief said:**
>  Now like i said if i use compiz or enable visual effects with this new driver i get the refresh problem

So to clarify, when you turn off compiz/visual effects, the new driver works?

Or, you have no GUI PERIOD. Not even a basic one?

---

### Post by modmadmike on 2008-12-09
> **rev0lv3r said:**
> So to clarify, when you turn off compiz/visual effects, the new driver works?

Or, you have no GUI PERIOD. Not even a basic one?

He just Said he has a GUI lol but compiz is <CENSORED> everything up. I know it has to do with the new version of compiz because I have the same problem on my Eee-PC.

---

### Post by rev0lv3r on 2008-12-09
> **modmadmike said:**
> He just Said he has a GUI lol but compiz is <CENSORED> everything up. I know it has to do with the new version of compiz because I have the same problem on my Eee-PC.

So if you have the plain-jane GUI, does the problem still exist of Apache2 using lots of CPU time?

Or is the original problem no longer happening (because a new, Compiz issue is happening)

Sorry, I am slightly lost, even after re reading the thread a while :)

Hope I can help

---

### Post by MasterShihoChief on 2008-12-09
So if you have the plain-jane GUI, does the problem still exist of Apache2 using lots of CPU time? <<<YES

Or is the original problem no longer happening (because a new, Compiz issue is happening)<<<Compiz issue started after a restart of linux after the Apache2 problem started. 

I successfully installed the new driver directly from nvidia. I even got the nvidia splash screen before the log in screen so i know its working. Guess what? It fixed absolutly nothing. I had to do emerald --replace so compiz didnt freak out again. The Apache2 problem is still plagueing me. I was however able to set visual settings to the highest (extra) successfully.

EDIT: I have my compiz cube back even though i typed emerald --replace. Now we are back to square one with the Apache2 issue

---

### Post by rev0lv3r on 2008-12-09
So can you post a htop screenshot again of the apache2 process going out of control or something?

Because your previous screenshots show gdm maxing out CPU usag.e

---

### Post by MasterShihoChief on 2008-12-10
thats the only process that goes out of control, but it only occurs when apache2 is active on a site, aka its using the files from [http://localhost](http://localhost) to load the page. So i thought apache2 had something to do with it. I also notice that there are many many apache and daemon processes going on in htop that dont show in ps aux. I have about 25 apache and 25 daemon but i dont know if that helps at all.

---

### Post by MasterShihoChief on 2008-12-10
bump

---

### Post by MasterShihoChief on 2008-12-10
bump T_T

---

### Post by MasterShihoChief on 2008-12-11
bump bump bump T_T

---

### Post by overdrank on 2008-12-11
Please do not bump your thread so quickly. Once a day is sufficient.

---

### Post by MasterShihoChief on 2008-12-12
bump

---

### Post by modmadmike on 2008-12-12
Are you running 8.10 or 8.04? 8.04 is more refined but 8.10 is newer, if you have the one then try the other.

---

### Post by MasterShihoChief on 2008-12-12
running 8.10 but I guess I can downgrade to 8.4 I'll let u know how it goes unless someone has any other ideas

---

### Post by MasterShihoChief on 2008-12-14
no effect still have the problem and bump please. I am now back to 8.10 after 8.4 had same issue

---

### Post by MasterShihoChief on 2008-12-21
so i sent these files to a yahoo webserver i am a webmaster of to see if indeed it was an apache problem. Tested the images first and no problem. So i continued the upload. Once the css file was uploaded firefox went back to crashing and that process going up to a 100%. I dont know what the hell is causing it, its definitely not apache2, since i tested it on a yahoo webserver. I have been patient for a couple weeks trying to fix this, how about helping me out. Once i disable css (its an option on the website im trying to use the graphics pack on) it works fine but doesnt look like its suppose too, so its definitly css, any ideas?

---

### Post by kixome on 2008-12-21
here is your definitive answer. Disable all desktop effects before running said game, and stay with LTS releases. 

Remember, any eye-candied desktop environment is a resource hog! Eye candy is useless other than to wow your buddies, this doesn't just apply to OSes but to all of life. Tell me the last beautiful girlfriend/car/house ect. that wasn't a resource/ money/ time Hog!

---

### Post by kixome on 2008-12-21
Also I have had problems with video when both Gnome and KDE are installed, so make sure if you are running one DE that processes from the other Desktop Environment are not running as they seem to conflict with one another! 

GOOD LUCK! HOPE THIS HELPS!

---

### Post by MasterShihoChief on 2008-12-21
nope didnt work, tried that on both versions, this is a cascading style sheet problem on any websites using CSS, not a desktop effects problem. Plus i have the video cards, memory, and processor to handle those effects

---

### Post by kixome on 2008-12-21
Well, I wish I were wiser. I hope you get it. If I think of something else I will post asap!

---

### Post by kixome on 2008-12-21
Tell me do you have video clipping, tearing, or flaching when you play a movie file while desktop effects are enabled? If not please reply with what graphics card you are using because I want one.

---

### Post by MasterShihoChief on 2008-12-21
I dont have a problem watching videos unless its youtube, then it flickers horribly. If its my anime that is encoded in HD h.264 format(which is obviously more demanding than youtube videos)then there is no problem. I set up mplayer to work flawlesly without as much as a hiccup.

My Computer Specs:

Alienware M17x Laptop
120GB Sata 7200rpm HDD
2GB DDR2 RAM
2XNvidia Geforce 8600M GT w/SLI
C2D 2.1ghz Processor
Resolution 1920x1200 WUXGA 17" screen

---

### Post by rev0lv3r on 2008-12-21
Try another browser?

Ephiphiny is based on Webkit right?

---

### Post by kixome on 2008-12-21
thank you for the reply, I have an ati x300 and it skroos the pooch if I have D.Effects enabled and try to play video, this may be your youtube problem. I have as of yet to have any problems with youtube, but hulu, and movie player(gstreamer) can be a bit slow and pixelated sometimes, must be my graphics.  Sorry abbout going off topic.

---

### Post by MasterShihoChief on 2008-12-21
negative on the browser, no its not a desktop effects problem for youtube, its a youube problem, because it happens on every computer in my area all the time. In my area youtube is so overloaded that sometimes videos dont load at all on any computer. There are plenty of times where i have flawless play back on youtube. My computer is a $3000 computer and scores very very high in performance, and shouldnt have this issue as its non existant in windows xp, vista, or even osx. I tried looking for a Cascading Style Sheet package and installed a few to see what would happen, and nothing happened at all, still messed up. Any other ideas?

---

### Post by modmadmike on 2008-12-21
Have you tried opera its closed source but its much faster than firefox (which i still use). Or have you tried the new 64bit version of flash (google it i forgot were to get it unless you want me to email the file which i can do) it's still in alpha but it works soo much better than the old one.

---

### Post by MasterShihoChief on 2008-12-21
tried opera, since i love opera a lot, but it had the same problem(this was the first thing i tried. I have 32bit ubuntu, not 64. I have a 64 bit processor but i find 32 bit to be a lot more stable then 64. Plus i doubt this is a flash problem, its Cascading Style Sheets (CSS), it has nothing to do with flash(i dont think XD)

---

### Post by modmadmike on 2008-12-22
thats odd i find 64bit just as stable (if not more so) try coping your /home directory to a separate Partition and install ubuntu 8.10 (or 8.04) x64 edition, for me i have no problems with it except with myth-tv which is not a 64 bit problem.

---

### Post by modmadmike on 2008-12-22
you want i can SSH into your box and try to fix it for you.

---

### Post by MasterShihoChief on 2008-12-23
i dont have any objections to someone trying to take control of my comp to fix it, i do have teamviewer4 via wine that works awesome, or you can ssh or whatever you prefer. If i have to reinstall ubuntu to get x64(my hdd is completly full) then i will.

---

### Post by MasterShihoChief on 2008-12-24
bump...come on i wanna fix this issue, its been ongoing for over 2 weeks, going on 3 pretty soon. Isn't there anyone who can help me address this issue?

---

### Post by MasterShihoChief on 2008-12-25
bump

---

### Post by MasterShihoChief on 2008-12-26
bump

---

### Post by MasterShihoChief on 2008-12-27
bump

---

### Post by MasterShihoChief on 2008-12-28
bump

---

### Post by modmadmike on 2008-12-29
ok can you set up remote desktop (set a password and email it to me) and map port 5900 in your router to your pc.

---

### Post by modmadmike on 2008-12-29
oh and go to [http://whatsmyip.org/](http://whatsmyip.org/) and send me the ip address at the top of the page.

---

### Post by MasterShihoChief on 2009-01-29
I just updated my kernel to the latest version and reinstalled the video driver shortly thereafter and this problem has vanished XD

so anyone who has issues with browsing websites with Cascading Style Sheets freezing up your comp, just update your kernel, reinstall your video driver and thats that. thanks to everyone who assisted me in fixing this.

---

