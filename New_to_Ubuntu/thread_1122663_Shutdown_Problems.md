---
title: "Shutdown Problems"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by VladTheImpaler on 2009-04-11
I've got a new 8.10 install on an old rig:

Dell Dimension XPS-R
PIII 1GHz
768 MB PC100
MX 440
Some old sound card (I can't remember)

The machine runs fine except on shutdown.  It hangs up at the Ubuntu splash screen when the progress bar turns black.

I tried everything suggested [here]("http://ubuntuforums.org/showthread.php?t=990768&highlight=shutdown") with no resolution, and /var/log/shutdown.log never displayed any text.

I used instructions from [here]("http://ubuntuforums.org/showthread.php?t=939790") to generate a /var/log/shutdown.log and it is:

> 
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  1 10:33 ?        00:00:02 /sbin/init
root         2     0  0 10:33 ?        00:00:00 [kthreadd]
root         3     2  0 10:33 ?        00:00:00 [migration/0]
root         4     2  0 10:33 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 10:33 ?        00:00:00 [watchdog/0]
root         6     2  0 10:33 ?        00:00:00 [events/0]
root         7     2  0 10:33 ?        00:00:00 [khelper]
root        46     2  0 10:33 ?        00:00:00 [kintegrityd/0]
root        48     2  0 10:33 ?        00:00:00 [kblockd/0]
root        69     2  0 10:33 ?        00:00:00 [cqueue]
root        73     2  0 10:33 ?        00:00:00 [kseriod]
root       118     2  0 10:33 ?        00:00:00 [pdflush]
root       119     2  0 10:33 ?        00:00:00 [pdflush]
root       120     2  0 10:33 ?        00:00:00 [kswapd0]
root       164     2  0 10:33 ?        00:00:00 [aio/0]
root      1120     2  0 10:33 ?        00:00:00 [ksuspend_usbd]
root      1124     2  0 10:33 ?        00:00:00 [khubd]
root      1130     2  0 10:33 ?        00:00:00 [ata/0]
root      1132     2  0 10:33 ?        00:00:00 [ata_aux]
root      1208     2  0 10:33 ?        00:00:00 [scsi_eh_0]
root      1209     2  0 10:33 ?        00:00:00 [scsi_eh_1]
root      1985     2  0 10:33 ?        00:00:00 [kjournald]
root      2159     1  0 10:33 ?        00:00:00 /sbin/udevd --daemon
root      2315     2  0 10:33 ?        00:00:00 [kpsmoused]
root      2529     2  0 10:33 ?        00:00:00 [kgameportd]
root      3778     1  0 10:33 tty4     00:00:00 /sbin/getty 38400 tty4
root      3779     1  0 10:33 tty5     00:00:00 /sbin/getty 38400 tty5
root      3789     1  0 10:33 tty2     00:00:00 /sbin/getty 38400 tty2
root      3791     1  0 10:33 tty3     00:00:00 /sbin/getty 38400 tty3
root      3793     1  0 10:33 tty6     00:00:00 /sbin/getty 38400 tty6
root      3858     2  0 10:33 ?        00:00:00 [kondemand/0]
syslog    3939     1  0 10:33 ?        00:00:00 /sbin/syslogd -u syslog
root      3995     1  0 10:33 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3997     1  0 10:33 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4020     1  0 10:33 ?        00:00:00 /bin/dbus-daemon --system
avahi     4042     1  0 10:33 ?        00:00:00 avahi-daemon: running [beach-desktop.local]
avahi     4043  4042  0 10:33 ?        00:00:00 avahi-daemon: chroot helper
root      4053     2  0 10:33 ?        00:00:00 [kapmd]
root      4067     1  0 10:33 ?        00:00:00 /usr/sbin/apmd -P /etc/apm/apmd_proxy --proxy-timeout 30
root      4106     1  0 10:33 ?        00:00:00 /usr/sbin/cupsd
111       4266     1  0 10:33 ?        00:00:00 /usr/sbin/hald
root      4269     1  0 10:33 ?        00:00:00 /usr/sbin/console-kit-daemon
root      4332  4266  0 10:33 ?        00:00:00 hald-runner
root      4361  4332  0 10:33 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      4364  4332  0 10:33 ?        00:00:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      4382  4332  0 10:33 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1
root      4408     1  0 10:33 ?        00:00:00 /usr/sbin/bluetoothd
root      4416     2  0 10:33 ?        00:00:00 [btaddconn]
root      4418     2  0 10:33 ?        00:00:00 [btdelconn]
root      4429     2  0 10:33 ?        00:00:00 [krfcommd]
root      4465     1  0 10:33 ?        00:00:00 /usr/sbin/NetworkManager
root      4469     1  0 10:33 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      4472     1  0 10:33 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      4503     1  0 10:33 ?        00:00:00 /usr/sbin/gdm
root      4506  4503  0 10:33 ?        00:00:00 /usr/sbin/gdm
root      4509  4506  5 10:33 tty7     00:00:05 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4526     1  0 10:33 ?        00:00:00 /usr/bin/system-tools-backends
daemon    4561     1  0 10:33 ?        00:00:00 /usr/sbin/atd
root      4589     1  0 10:33 ?        00:00:00 /usr/sbin/cron
root      4608  4465  0 10:33 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/run/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      4681     1  0 10:33 tty1     00:00:00 /sbin/getty 38400 tty1
beach     4763     1  0 10:34 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d --login
beach     4774  4506  0 10:34 ?        00:00:00 x-session-manager
beach     4900     1  0 10:34 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
beach     4901     1  0 10:34 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
beach     4904     1  0 10:34 ?        00:00:00 /usr/bin/pulseaudio -D --log-target=syslog
beach     4907  4904  0 10:34 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
beach     4909     1  1 10:34 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2
beach     4915  4774  0 10:34 ?        00:00:00 /usr/bin/seahorse-agent --execute x-session-manager
beach     4920     1  1 10:34 ?        00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
beach     4921  4774  0 10:34 ?        00:00:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
beach     4923  4774  0 10:34 ?        00:00:00 /bin/sh /usr/bin/compiz
beach     4939     1  0 10:34 ?        00:00:00 /usr/lib/gvfs/gvfsd
beach     4964     1  0 10:34 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/beach/.gvfs
beach     5005  4923  6 10:34 ?        00:00:04 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding core ccp
beach     5006     1  0 10:34 ?        00:00:00 gnome-screensaver
beach     5007  5005  0 10:34 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
beach     5008  5007  0 10:34 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator
beach     5010  5008  1 10:34 ?        00:00:00 /usr/bin/gtk-window-decorator
beach     5011  4774  4 10:34 ?        00:00:02 gnome-panel
beach     5012  4774  3 10:34 ?        00:00:02 nautilus --no-desktop --browser
beach     5015     1  0 10:34 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
beach     5023     1  0 10:34 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
beach     5025     1  0 10:34 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
beach     5029     1  0 10:34 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=20
beach     5032     1  0 10:34 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.12 /org/gtk/gvfs/exec_spaw/0
beach     5034     1  0 10:34 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.12 /org/gtk/gvfs/exec_spaw/1
beach     5042     1  1 10:34 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=21
beach     5045     1  1 10:34 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=25
beach     5051  4774  0 10:34 ?        00:00:00 /usr/lib/evolution/2.24/evolution-alarm-notify
beach     5052  4774  0 10:34 ?        00:00:00 update-notifier
beach     5053  4774  0 10:34 ?        00:00:00 bluetooth-applet
beach     5054  4774  0 10:34 ?        00:00:00 python /usr/share/system-config-printer/applet.py
beach     5055  4774  1 10:34 ?        00:00:00 nm-applet --sm-disable
beach     5056  4774  0 10:34 ?        00:00:00 tracker-applet
beach     5060  4774  1 10:34 ?        00:00:00 /usr/bin/python /usr/bin/jockey-gtk --check 60
beach     5061  4774  0 10:34 ?        00:00:00 trackerd
beach     5068     1  0 10:34 ?        00:00:00 gnome-power-manager
beach     5104     1  3 10:34 ?        00:00:01 gnome-terminal
beach     5106  5104  0 10:34 ?        00:00:00 gnome-pty-helper
beach     5107  5104  1 10:34 pts/0    00:00:00 bash
root      5129  5107  0 10:35 pts/0    00:00:00 /bin/bash /home/beach/Desktop/myshutdown.sh
root      5131  5129  0 10:35 pts/0    00:00:00 ps -ef
------ MARK----- 


Thank you in advance for your help.

---

### Post by VCoolio on 2009-04-11
For me [this]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Shutdown_freezes_sometimes") was the solution. It says:

It seems that ALSA has problems to shut down if network devices are still active. You can force ALSA during its unloading to disable the networking first (remember to backup your files!):

gksudo gedit /etc/init.d/alsa-utils

Search for "stop)" and add immediately below:

ifconfig eth0 down
ifconfig wlan0 down

"Search for "stop)": for me that was line 354.

---

