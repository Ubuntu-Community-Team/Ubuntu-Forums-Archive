---
title: "Can't download anything because another installer is running?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by bellabrokenxx on 2009-07-21
I want to download limewire, and when i go to download the installer runs and a popup comes up and informs me that only one software manager is allowed to run at one time.
Nothing else is open, and i can't find what else is running. I have restarted my computer hoping it would close everything out, but It keeps doing this.

Help?

---

### Post by devildoc5 on 2009-07-21
ok this seems to be a two pronged issue here......

First issue DO NOT use Limewire, use Frostwire instead.....Basically the same thing, just with an open source.

Secondly if you are 100% certain that you did not open a package to try and install previously then try this in a terminal:

```

sudo killall synaptic

```
 if that does not work try replacing "synaptic" with "gdebi" and try again.

---

### Post by bellabrokenxx on 2009-07-21
OK, i did that but it says no process killed for both.

---

### Post by devildoc5 on 2009-07-21
and it still wont allow you to install the package you are trying to install?

---

### Post by bellabrokenxx on 2009-07-21
correct.

---

### Post by devildoc5 on 2009-07-21
well the only thing I can think of then would be to try and replace the synaptic from above with "aptitude".  If that does not work though............

I did notice it says you are using 8.04 is that still correct?

It could be possible that your system is trying to update to the new version and that is what is causing this problem as well......

---

### Post by bellabrokenxx on 2009-07-21
nope, but thanks. and i honestly wouldnt know.

---

### Post by devildoc5 on 2009-07-21
is update manager running?  that is how you would be able to tell if it was updating....

Unfortunately if that is not the issue then I would honestly have to say that someone else is going to have to help you, as I have never come across this problem myself and I am still for all intents and purposes a N00b

---

### Post by bellabrokenxx on 2009-07-21
haahaha, well thank you anyways. :]

---

### Post by devildoc5 on 2009-07-21
someone should be along to help you.  Although you could always try the ubuntu IRC channel aswell......

---

### Post by slakkie on 2009-07-21
There is a lockfile left behind I guess.

Open a terminal and do the following:

```

sudo rm /var/lib/dpkg/lock

```

And then try to do whatever you want to do.

---

### Post by bellabrokenxx on 2009-07-22
> **slakkie said:**
> There is a lockfile left behind I guess.

Open a terminal and do the following:

```

sudo rm /var/lib/dpkg/lock

```

And then try to do whatever you want to do.


and with that i got

```
bella@Rawr:~$ sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
bella@Rawr:~$ 

```

---

### Post by Durden on 2009-07-22
What happens when you reboot?

If you reboot and it still does it then open a terminal and make it fullscreen for a second. Type "ps auxg" and copy and paste the output here for us.

---

### Post by bellabrokenxx on 2009-07-22
```
bella@Rawr:~$ ps auxg
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1688 ?        Ss   18:58   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   18:58   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   18:58   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   18:58   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   18:58   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   18:58   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   18:58   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   18:58   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   18:58   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   18:58   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   18:58   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   18:58   0:00 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<   18:58   0:00 [kblockd/1]
root        50  0.0  0.0      0     0 ?        S<   18:58   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   18:58   0:00 [kacpi_notify]
root       149  0.0  0.0      0     0 ?        S<   18:58   0:00 [kseriod]
root       191  0.0  0.0      0     0 ?        S    18:58   0:00 [pdflush]
root       192  0.0  0.0      0     0 ?        S    18:58   0:00 [pdflush]
root       193  0.0  0.0      0     0 ?        S<   18:58   0:00 [kswapd0]
root       234  0.0  0.0      0     0 ?        S<   18:58   0:00 [aio/0]
root       235  0.0  0.0      0     0 ?        S<   18:58   0:00 [aio/1]
root      1496  0.0  0.0      0     0 ?        S<   18:58   0:00 [ksuspend_usbd]
root      1499  0.0  0.0      0     0 ?        S<   18:58   0:00 [khubd]
root      1602  0.0  0.0      0     0 ?        S<   18:58   0:00 [ata/0]
root      1603  0.0  0.0      0     0 ?        S<   18:58   0:00 [ata/1]
root      1604  0.0  0.0      0     0 ?        S<   18:58   0:00 [ata_aux]
root      1613  0.0  0.0      0     0 ?        S<   18:58   0:00 [khpsbpkt]
root      1747  0.0  0.0      0     0 ?        S<   18:58   0:00 [knodemgrd_0]
root      2336  0.0  0.0      0     0 ?        S<   18:58   0:00 [scsi_eh_0]
root      2337  0.0  0.0      0     0 ?        S<   18:58   0:00 [scsi_eh_1]
root      2338  0.0  0.0      0     0 ?        S<   18:58   0:00 [scsi_eh_2]
root      2434  0.0  0.0      0     0 ?        S<   18:58   0:00 [scsi_eh_3]
root      2436  0.0  0.0      0     0 ?        S<   18:58   0:00 [scsi_eh_4]
root      2638  0.0  0.0      0     0 ?        S<   18:58   0:00 [kjournald]
root      2841  0.0  0.0   2440   988 ?        S<s  18:58   0:00 /sbin/udevd --daemon
root      3222  0.0  0.0      0     0 ?        S<   18:58   0:00 [kmmcd]
root      3264  0.0  0.0      0     0 ?        S<   18:58   0:00 [kpsmoused]
root      3288  0.0  0.0      0     0 ?        S<   18:58   0:00 [iwl4965/0]
root      3289  0.0  0.0      0     0 ?        S<   18:58   0:00 [iwl4965/1]
root      4335  0.0  0.0      0     0 ?        S<   18:58   0:00 [iwl4965]
root      4695  0.0  0.0   1716   508 tty4     Ss+  18:58   0:00 /sbin/getty 38400 tty4
root      4696  0.0  0.0   1716   512 tty5     Ss+  18:58   0:00 /sbin/getty 38400 tty5
root      4698  0.0  0.0   1716   508 tty2     Ss+  18:58   0:00 /sbin/getty 38400 tty2
root      4700  0.0  0.0   1716   508 tty3     Ss+  18:58   0:00 /sbin/getty 38400 tty3
root      4702  0.0  0.0   1716   512 tty6     Ss+  18:58   0:00 /sbin/getty 38400 tty6
root      4886  0.0  0.0   2456  1456 ?        Ss   18:58   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4926  0.0  0.0      0     0 ?        S<   18:58   0:00 [kondemand/0]
root      4927  0.0  0.0      0     0 ?        S<   18:58   0:00 [kondemand/1]
syslog    5004  0.0  0.0   1936   644 ?        Ss   18:58   0:00 /sbin/syslogd -u syslog
root      5057  0.0  0.0   1872   536 ?        S    18:58   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5059  0.0  0.0   3384  2184 ?        Ss   18:58   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5081  0.0  0.0   2836  1340 ?        Ss   18:58   0:04 /usr/bin/dbus-daemon --system
root      5097  0.0  0.0  30192  2248 ?        Ssl  18:58   0:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5111  0.0  0.0   3416  1292 ?        Ss   18:58   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatch
root      5124  0.0  0.0   4112  1108 ?        Ss   18:58   0:00 /usr/bin/system-tools-backends
avahi     5144  0.0  0.0   2760  1420 ?        Ss   18:58   0:00 avahi-daemon: running [Rawr.local]
avahi     5145  0.0  0.0   2760   468 ?        Ss   18:58   0:00 avahi-daemon: chroot helper
root      5187  0.0  0.0   5916  2300 ?        Ss   18:58   0:00 /usr/sbin/cupsd
root      5261  0.0  0.0   2020   908 ?        Ss   18:58   0:00 /usr/sbin/dhcdbd --system
111       5280  0.0  0.1   6228  4316 ?        Ss   18:58   0:05 /usr/sbin/hald
root      5283  0.0  0.0   8788  2344 ?        Ssl  18:58   0:00 /usr/sbin/console-kit-daemon
root      5284  0.0  0.0   3236  1068 ?        S    18:58   0:00 hald-runner
root      5357  0.0  0.0   3300  1064 ?        S    18:58   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event7 /dev/input/event1 /dev/in
root      5363  0.0  0.0   3312  1160 ?        S    18:58   0:00 /usr/lib/hal/hald-addon-cpufreq
111       5364  0.0  0.0   2204   956 ?        S    18:58   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5389  0.0  0.0   3304  1036 ?        S    18:58   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5410  0.0  0.0   3052  1232 ?        Ss   18:58   0:00 /usr/sbin/hcid -x -s
root      5419  0.0  0.0      0     0 ?        S<   18:58   0:00 [btaddconn]
root      5420  0.0  0.0      0     0 ?        S<   18:58   0:00 [btdelconn]
root      5430  0.0  0.0   2900  1020 ?        S    18:58   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5436  0.0  0.0   2964  1220 ?        S    18:58   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5459  0.0  0.0      0     0 ?        S<   18:58   0:00 [krfcommd]
root      5539  0.0  0.0  14048  1596 ?        Ss   18:58   0:00 /usr/sbin/gdm
root      5540  0.0  0.0  14508  2996 ?        S    18:58   0:00 /usr/sbin/gdm
root      5545  0.8  1.8  66040 57004 tty7     Rs+  18:58   1:17 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5584  0.0  0.0   1984   420 ?        Ss   18:58   0:00 /usr/sbin/atd
root      5598  0.0  0.0   2104   892 ?        Ss   18:58   0:00 /usr/sbin/cron
root      5690  0.0  0.0   1716   504 tty1     Ss+  18:58   0:00 /sbin/getty 38400 tty1
bella     5738  0.0  0.1   7168  4292 ?        S    18:58   0:01 /usr/lib/libgconf2-4/gconfd-2 4
bella     5744  0.0  0.0  14240  2112 ?        S    18:58   0:00 /usr/bin/gnome-keyring-daemon -d --login
bella     5745  0.0  0.2  28864  7528 ?        Ssl  18:58   0:00 x-session-manager
bella     5798  0.0  0.2  23052  6812 ?        Ss   18:58   0:00 /usr/bin/seahorse-agent --execute x-session-manager
bella     5802  0.0  0.0   2696  1156 ?        Ss   18:58   0:00 dbus-daemon --fork --print-address 20 --print-pid 22 --session
bella     5803  0.0  0.3  42640 11760 ?        Sl   18:58   0:00 gnome-settings-daemon
bella     5820  0.1  0.1  54132  6116 ?        Sl   18:58   0:10 /usr/bin/pulseaudio --log-target=syslog
bella     5823  0.0  0.0   5676  2208 ?        S    18:58   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
bella     5833  0.0  0.1  15620  5672 ?        Ss   18:58   0:02 gnome-screensaver
bella     5838  0.0  0.0   1772   536 ?        S    18:58   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
bella     5839  0.0  0.6  51908 19140 ?        S    18:58   0:05 gnome-panel --sm-client-id default1
bella     5841  0.0  0.8  60108 25044 ?        S    18:58   0:01 nautilus --no-default-window --sm-client-id default2
bella     5850  0.0  0.1  41052  3168 ?        Ssl  18:58   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
bella     5875  0.0  0.0   5372  2100 ?        S    18:58   0:00 /usr/lib/gvfs/gvfsd
bella     5907  0.1  0.4  22480 15192 ?        S    18:58   0:17 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id de
bella     5909  0.0  0.1  14496  5672 ?        S    18:58   0:00 bluetooth-applet --singleton
bella     5911  0.0  0.0  29048  1884 ?        Ssl  18:58   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/bella/.gvfs
bella     5921  0.0  0.3  24108 12140 ?        S    18:58   0:00 update-notifier
bella     5925  0.0  0.1  15112  5456 ?        S    18:58   0:00 tracker-applet
bella     5927  0.0  0.5  40484 17820 ?        Ss   18:58   0:00 python /usr/bin/hp-systray
bella     5929  0.0  0.3  63372 10356 ?        Sl   18:58   0:00 /usr/lib/evolution/2.22/evolution-alarm-notify
bella     5931  0.0  0.3  31528 10336 ?        SNl  18:58   0:00 trackerd
bella     5936  0.0  0.3  25180 11832 ?        S    18:58   0:07 nm-applet --sm-disable
bella     5938  0.1  0.3  25656 10584 ?        Ss   18:58   0:15 gnome-power-manager
bella     5944  0.0  0.1  20668  4680 ?        Ss   18:58   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
bella     6004  0.0  0.0   5372  2144 ?        S    18:58   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
bella     6009  0.0  0.2  67968  6636 ?        Sl   18:58   0:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_Data
bella     6012  0.0  0.0  22036  2692 ?        S    18:58   0:03 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
bella     6018  0.0  0.3  23316 10308 ?        S    18:58   0:01 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory
bella     6041  0.0  0.3  30744  9704 ?        Sl   18:58   0:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution
bella     6042  0.0  0.0   1772   480 ?        Ss   18:58   0:00 /bin/sh -c /usr/bin/compiz-decorator
bella     6043  0.0  0.0   1772   508 ?        S    18:58   0:00 /bin/sh /usr/bin/compiz-decorator
bella     6045  0.0  0.2  16360  8172 ?        S    18:58   0:02 /usr/bin/gtk-window-decorator
root      6047  0.0  0.0   3880  1508 ?        S    18:58   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
bella     6057  0.0  0.4  42164 12924 ?        Sl   18:58   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --o
bella     6059  0.0  0.3  23892 11436 ?        S    18:58   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_Fas
bella     6085  0.0  0.2  16868  8164 ?        S    18:58   0:01 python /usr/bin/hp-systray
bella     6086  0.0  0.2  15408  7120 ?        S    18:58   0:00 python /usr/bin/hp-systray
dhcp      6098  0.0  0.0   2440  1188 ?        S    18:59   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -
bella     6289  0.0  0.3  19256  9684 ?        S    18:59   0:00 /usr/lib/notification-daemon/notification-daemon
bella    13941  1.9  1.0 488448 32580 ?        Sl   21:22   0:18 pidgin
bella    14004 19.9  4.0 267560 124936 ?       Rl   21:23   3:05 /usr/lib/firefox-3.0.11/firefox
bella    15238  6.4  0.5  64184 17772 ?        Rl   21:38   0:00 gnome-terminal
bella    15240  0.0  0.0   2796   756 ?        S    21:38   0:00 gnome-pty-helper
bella    15241  2.0  0.0   5652  3068 pts/0    Ss   21:38   0:00 bash
bella    15263  0.0  0.0   2644  1004 pts/0    R+   21:38   0:00 ps auxg
bella@Rawr:~$ 

```

---

### Post by Durden on 2009-07-22
I dont see anything there that shouldn't be. Is there anything in your /var/lock directory?

---

### Post by bellabrokenxx on 2009-07-23
> **Durden said:**
> I dont see anything there that shouldn't be. Is there anything in your /var/lock directory?

i have NO idea what that means. >>

---

