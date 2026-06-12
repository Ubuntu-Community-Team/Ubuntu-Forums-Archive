---
title: "unknown program - prevents shutdown"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by jbehl on 2009-03-02
I'm getting an error when I try to shutdown my computer. Apparently there is an unknown program running that prevents shutdown. The dialog box asks if I want to shutdown anyway, I click yes and it shuts down fine. Is there a way to see what program is causing the problem?

Thanks

---

### Post by cmay on 2009-03-02
[PHP]ps ax[/PHP]
this will list the running procceses.

---

### Post by jbehl on 2009-03-02
> **cmay said:**
> [PHP]ps ax[/PHP]
this will list the running procceses.
```

 PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:00 /sbin/init
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        S<     0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0]
    6 ?        S<     0:00 [events/0]
    7 ?        S<     0:00 [khelper]
   44 ?        S<     0:00 [kintegrityd/0]
   46 ?        S<     0:00 [kblockd/0]
   48 ?        S<     0:00 [kacpid]
   49 ?        S<     0:00 [kacpi_notify]
  151 ?        S<     0:00 [cqueue]
  155 ?        S<     0:00 [kseriod]
  201 ?        S      0:00 [pdflush]
  202 ?        S      0:00 [pdflush]
  203 ?        S<     0:00 [kswapd0]
  249 ?        S<     0:00 [aio/0]
 1289 ?        S<     0:00 [ksuspend_usbd]
 1292 ?        S<     0:00 [khubd]
 1315 ?        S<     0:00 [ata/0]
 1318 ?        S<     0:00 [ata_aux]
 1330 ?        S<     0:00 [khpsbpkt]
 2059 ?        S<     0:00 [scsi_eh_0]
 2061 ?        S<     0:00 [scsi_eh_1]
 2063 ?        S<     0:00 [knodemgrd_0]
 2066 ?        S<     0:00 [knodemgrd_1]
 2101 ?        S<     0:00 [scsi_eh_2]
 2105 ?        S<     0:00 [scsi_eh_3]
 2153 ?        S<     0:00 [scsi_eh_4]
 2154 ?        S<     0:00 [scsi_eh_5]
 2326 ?        S<     0:00 [kjournald]
 2500 ?        S<s    0:00 /sbin/udevd --daemon
 2858 ?        S<     0:00 [kgameportd]
 2892 ?        S<     0:00 [kpsmoused]
 4177 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/sdb1 /media/Storage1 -o rw,l
 4441 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4442 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4448 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4449 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4450 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4626 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4678 ?        S<     0:00 [kondemand/0]
 4738 ?        Ss     0:00 /sbin/syslogd -u syslog
 4788 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4790 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4813 ?        Ss     0:00 /bin/dbus-daemon --system
 4835 ?        Ss     0:00 avahi-daemon: running [Behl-Desktop.local]
 4836 ?        Ss     0:00 avahi-daemon: chroot helper
 4869 ?        Ss     0:00 /usr/sbin/cupsd
 4990 ?        S      0:00 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chip
 4991 ?        S      0:16 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chip
 5032 ?        Ss     0:00 /usr/sbin/nmbd -D
 5034 ?        Ss     0:00 /usr/sbin/smbd -D
 5055 ?        S      0:00 /usr/sbin/smbd -D
 5060 ?        Ss     0:00 /usr/sbin/winbindd
 5083 ?        Ss     0:00 /usr/sbin/hald
 5084 ?        S      0:00 /usr/sbin/winbindd
 5087 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 5150 ?        S      0:00 hald-runner
 5172 ?        S      0:01 hald-addon-usb-csr: listening on 'Mouse Receiver'
 5173 ?        S      0:00 hald-addon-input: Listening on /dev/input/event5 /dev
 5179 ?        S      0:00 /usr/lib/hal/hald-addon-cpufreq
 5180 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/a
 5208 ?        S      0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 5255 ?        Ss     0:00 /usr/sbin/bluetoothd
 5263 ?        S<     0:00 [btaddconn]
 5265 ?        S<     0:00 [btdelconn]
 5278 ?        S<     0:00 [krfcommd]
 5312 ?        Ssl    0:00 /usr/sbin/NetworkManager
 5316 ?        S      0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.lo
 5319 ?        S      0:00 /usr/sbin/nm-system-settings --config /etc/NetworkMan
 5358 ?        Ss     0:00 /usr/sbin/gdm
 5361 ?        S      0:00 /usr/sbin/gdm
 5364 tty7     SLs+   0:41 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:
 5385 ?        Ss     0:00 /usr/bin/system-tools-backends
 5406 ?        Ss     0:00 /usr/sbin/anacron -s
 5422 ?        Ss     0:00 /usr/sbin/atd
 5450 ?        Ss     0:00 /usr/sbin/cron
 5468 ?        S      0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp
 5536 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5558 ?        Ssl    0:00 x-session-manager
 5616 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5619 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pul
 5620 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 6 --print-addres
 5623 ?        Ssl    0:00 /usr/bin/pulseaudio -D --log-target=syslog
 5628 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 5630 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2
 5638 ?        Ss     0:00 /usr/bin/seahorse-agent --execute x-session-manager
 5693 ?        S      0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-w
 5698 ?        SL     0:00 /usr/bin/gnome-keyring-daemon
 5701 ?        S      0:00 /usr/lib/gvfs/gvfsd
 5702 ?        Ssl    0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 5703 ?        S      0:04 metacity
 5711 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/james/.gvfs
 5718 ?        S      0:06 gnome-panel
 5721 ?        S      0:01 nautilus --no-desktop --browser
 5724 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5743 ?        Ss     0:02 gnome-screensaver
 5745 ?        S      0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
 5747 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 5750 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs
 5752 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5756 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvf
 5773 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 5776 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5797 ?        S      0:00 tracker-applet
 5799 ?        S      0:00 update-notifier
 5803 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 5804 ?        Sl     0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
 5805 ?        S      0:00 bluetooth-applet
 5806 ?        S      0:00 nm-applet --sm-disable
 5807 ?        SNl    0:00 trackerd
 5808 ?        Ss     0:00 gnome-power-manager
 5817 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 5821 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-a
 6042 ?        S      0:00 /bin/sh -c nice run-parts --report /etc/cron.daily
 6043 ?        SN     0:00 run-parts --report /etc/cron.daily
 6441 ?        Ss     0:00 kdeinit4: kdeinit4 Running...
 6444 ?        S      0:00 klauncher
 6446 ?        S      0:00 kded4
 6461 ?        S      0:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-
 6853 ?        Sl     0:00 gnome-terminal
 6855 ?        S      0:00 gnome-pty-helper
 6856 pts/0    Ss     0:00 bash
 6874 ?        RN     0:00 /usr/bin/python /usr/lib/update-notifier/apt-check
 6892 ?        SN     0:00 /bin/sh /etc/cron.daily/logrotate
 6893 ?        SN     0:00 /usr/sbin/logrotate /etc/logrotate.conf
 6894 ?        RN     0:00 /bin/gzip
 6895 pts/0    R+     0:00 ps ax

```

Any ideas what it might be? I only noticed it once I installed the last updates.

---

### Post by handy on 2009-03-03
If when you type htop in the terminal it is not there, then I suggest you install it from synaptic, as it is a very light & powerful system monitor that will show all running processes, their CPU, memory demands & more.

Htop is what I would use to work out what is causing your problem.

---

### Post by richardh9936 on 2009-03-17
Don't panic.  These people think it's a remnant from Firefox.  See 
 [http://ubuntuforums.org/showpost.php?p=6629969&postcount=9]("http://ubuntuforums.org/showpost.php?p=6629969&postcount=9")

---

### Post by Crosbie on 2009-05-29
I can confirm that I've had this after using Firefox for internet browsing, and it isn't triggered after using Epiphany instead.

I didn't use to have this problem with FF; I recently installed AdBlock as an add-on - I wonder whether this is the cause?

[EDIT]

Hm, following up: after having switched to Epiphany for testing purposes, on switching back to FF the issue seems to have gone.  Didn't change AdBlock.  Still, something to try if you're having this problem.

---

### Post by gcbzzzz on 2009-10-06
ubuntu 9.04 fully updated.

closed all instances of firefox. so it's not it.

shutdown shows UNKNOW program.

this is really confusing. why that dialog does not show a PID or process name?

what exactly it checks to assume something is running? is there a standard for X programs to notify that they need user response before exiting?

---

### Post by yochaigal on 2009-12-12
For now, you can do:
Alt+F2
type: gconf-editor
Go to -> apps -> indicator-session and set suppress_logout_restart_shutdown to true (a checkmark).

---

### Post by 4Orbs on 2009-12-12
This happened to me once when I hadn't finished configuring Evolution email and forgot about it.

---

