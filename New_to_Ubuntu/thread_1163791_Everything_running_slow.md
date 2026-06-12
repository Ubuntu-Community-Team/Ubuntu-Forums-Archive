---
title: "Everything running slow"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by siriusdane on 2009-05-19
I don't know what happened to my PC. Everything used to run smooth but since yesterday it takes forever to open most applications (amarok, firefox, evince, etc). The only ones that seem to work ok are wine, Thunar and the console.

I'm posting the result of the 'ps ax' command:

PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:00 /sbin/init
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        S<     0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0]
    6 ?        S<     0:00 [migration/1]
    7 ?        S<     0:00 [ksoftirqd/1]
    8 ?        S<     0:00 [watchdog/1]
    9 ?        S<     0:00 [events/0]
   10 ?        S<     0:00 [events/1]
   11 ?        S<     0:00 [khelper]
   44 ?        S<     0:00 [kblockd/0]
   45 ?        S<     0:00 [kblockd/1]
   48 ?        S<     0:00 [kacpid]
   49 ?        S<     0:00 [kacpi_notify]
  164 ?        S<     0:00 [kseriod]
  214 ?        S      0:00 [pdflush]
  215 ?        S      0:00 [pdflush]
  216 ?        S<     0:00 [kswapd0]
  259 ?        S<     0:00 [aio/0]
  260 ?        S<     0:00 [aio/1]
 1497 ?        S<     0:00 [ksuspend_usbd]
 1500 ?        S<     0:00 [khubd]
 1658 ?        S<     0:00 [ata/0]
 1661 ?        S<     0:00 [ata/1]
 1662 ?        S<     0:00 [ata_aux]
 2395 ?        S<     0:00 [scsi_eh_0]
 2396 ?        S<     0:01 [scsi_eh_1]
 2466 ?        S<     0:00 [scsi_eh_2]
 2467 ?        S<     0:00 [scsi_eh_3]
 2486 ?        S<     0:00 [scsi_eh_4]
 2487 ?        S<     0:00 [scsi_eh_5]
 2757 ?        S<     0:00 [kjournald]
 2955 ?        S<s    0:00 /sbin/udevd --daemon
 3325 ?        S<     0:00 [kpsmoused]
 4493 ?        Ss     0:03 /sbin/mount.ntfs /dev/sda1 /media/windows -o rw
 4567 ?        S<s    0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0
 4837 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4838 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4840 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4843 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4844 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5024 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 5058 ?        S<     0:00 [kondemand/0]
 5059 ?        S<     0:00 [kondemand/1]
 5137 ?        Ss     0:00 /sbin/syslogd -u syslog
 5195 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5197 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5219 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 5235 ?        Ss     0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 5249 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 5262 ?        Ss     0:00 /usr/bin/system-tools-backends
 5284 ?        Ss     0:00 /usr/sbin/sshd
 5314 ?        Ss     0:00 avahi-daemon: running [Justine.local]
 5315 ?        Ss     0:00 avahi-daemon: chroot helper
 5596 ?        S      0:00 /usr/lib/postgresql/8.3/bin/postgres -D /var/lib/post
 5599 ?        Ss     0:00 postgres: writer process                            
 5600 ?        Ss     0:00 postgres: wal writer process                        
 5643 ?        Ss     0:00 /usr/sbin/cupsd
 5831 ?        Sl     0:04 /usr/games/wesnothd
 5853 ?        Ss     0:00 /usr/sbin/winbindd
 5899 ?        S      0:00 /usr/sbin/winbindd
 5904 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 5923 ?        Ss     0:00 /usr/sbin/hald
 5926 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 5988 ?        S      0:00 hald-runner
 6006 ?        S      0:00 /usr/lib/hal/hald-addon-cpufreq
 6007 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/a
 6017 ?        S      0:00 hald-addon-input: Listening on /dev/input/event1 /dev
 6034 ?        S      0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 6037 ?        S      0:01 hald-addon-storage: polling /dev/scd1 (every 2 sec)
 6058 ?        Ss     0:00 /usr/sbin/hcid -x -s
 6067 ?        S<     0:00 [btaddconn]
 6068 ?        S<     0:00 [btdelconn]
 6081 ?        S      0:00 /usr/lib/bluetooth/bluetoothd-service-input
 6082 ?        S      0:00 /usr/lib/bluetooth/bluetoothd-service-audio
 6087 ?        S<     0:00 [krfcommd]
 6125 ?        Ss     0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 6128 ?        S      0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 6132 tty7     SLs+   1:40 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
 6174 ?        Ss     0:00 /usr/sbin/atd
 6188 ?        Ss     0:00 /usr/sbin/cron
 6320 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 6345 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 4
 6347 ?        S      0:00 /usr/bin/gnome-keyring-daemon -d --login
 6351 ?        Ss     0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xser
 6409 ?        Ss     0:00 /usr/bin/seahorse-agent --execute startxfce4
 6417 ?        S      0:00 /usr/bin/dbus-launch --sh-syntax --exit-with-session
 6418 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 6 --print-add
 6429 ?        Ss     0:00 /usr/bin/ssh-agent -s
 6431 ?        Sl     0:00 /usr/bin/xfce4-session
 6432 ?        Ss     0:02 gnome-screensaver
 6437 ?        Ss     0:00 xfce-mcs-manager
 6439 ?        Ss     0:00 kdein  
 6444 ?        S      0:00 dcops  
 6447 ?        S      0:00 klaun  
 6449 ?        S      0:00 kded   
 6456 ?        S      0:00 gnome-keyring-daemon
 6460 ?        S      0:01 xfce4-panel
 6462 ?        S      0:00 Thunar --daemon
 6464 ?        S      0:00 /usr/lib/gamin/gam_server
 6465 ?        S      0:03 /usr/lib/xfce4/panel-plugins/xfce4-menu-plugin socket
 6467 ?        S      0:00 xfdesktop
 6470 ?        Ss     0:00 xfwm4 --replace
 6472 ?        Ssl    0:09 /usr/bin/perl -w /usr/bin/checkgmail
 6481 ?        SNsl   0:00 trackerd
 6483 ?        Ss     0:01 nm-applet --sm-disable
 6495 ?        Ss     0:00 tracker-applet
 6561 ?        Ssl    0:47 /usr/lib/firefox-3.0.10/firefox
 6571 ?        Ss     0:02 xfce4-terminal
 6572 ?        S      0:00 gnome-pty-helper
 6573 pts/0    Ss     0:00 bash
 6732 ?        S      0:00 kio_f  
 7213 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 7248 ?        Sl     0:03 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --pl
 7352 ?        S      0:00 kio_h  
 7371 pts/0    R+     0:00 ps ax

The CPU usage is really low so it's not like some process is using all of my CPU. Can anyone help me? give me any suggestions... I'm powerless here...

The applications not only take long time to start... but once they start they have periods of inactivity... It has taken forever for me to post this message!

Regards,

Aquiles Lacruz

---

### Post by skymera on 2009-05-19
Type ```
 free -m 
``` That'll show you how much memory is used/free.

How much memory do you have?

---

### Post by siriusdane on 2009-05-19
free -m
             total       used       free     shared    buffers     cached
Mem:          1887       1420        467          0        281        711
-/+ buffers/cache:        427       1460
Swap:          941          0        941

---

