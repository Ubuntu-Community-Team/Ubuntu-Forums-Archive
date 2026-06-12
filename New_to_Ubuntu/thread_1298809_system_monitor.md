---
title: "system monitor"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by jrandolph on 2009-10-23
Can anyone tell me why I have so many of the same processes running
gvfsd
gvfsd-burn
gvfsd-trash
trackerd

There is like 8-9 of each of these

---

### Post by BbUiDgZ on 2009-10-23
i cant see the screenshot.

can you do
```
ps -A
```

and paste the output please

---

### Post by jrandolph on 2009-10-23
jacob@jacob:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  159 ?        00:00:00 kseriod
  201 ?        00:00:00 pdflush
  202 ?        00:00:00 pdflush
  203 ?        00:00:00 kswapd0
  244 ?        00:00:00 aio/0
  245 ?        00:00:00 aio/1
 1548 ?        00:00:00 ksuspend_usbd
 1554 ?        00:00:00 khubd
 1559 ?        00:00:00 ata/0
 1563 ?        00:00:00 ata/1
 1568 ?        00:00:00 ata_aux
 1961 ?        00:00:00 scsi_eh_0
 1963 ?        00:00:00 scsi_eh_1
 2344 ?        00:00:00 scsi_eh_2
 2345 ?        00:00:00 scsi_eh_3
 2377 ?        00:00:00 scsi_eh_4
 2378 ?        00:00:00 scsi_eh_5
 2643 ?        00:00:00 kjournald
 2846 ?        00:00:00 udevd
 4593 tty4     00:00:00 getty
 4594 tty5     00:00:00 getty
 4596 tty2     00:00:00 getty
 4599 tty3     00:00:00 getty
 4600 tty6     00:00:00 getty
 4780 ?        00:00:00 acpid
 4815 ?        00:00:00 kondemand/0
 4816 ?        00:00:00 kondemand/1
 4901 ?        00:00:00 syslogd
 4957 ?        00:00:00 dd
 4959 ?        00:00:00 klogd
 4981 ?        00:00:00 dbus-daemon
 4997 ?        00:00:00 NetworkManager
 5011 ?        00:00:00 NetworkManagerD
 5024 ?        00:00:00 system-tools-ba
 5044 ?        00:00:00 avahi-daemon
 5045 ?        00:00:00 avahi-daemon
 5100 ?        00:00:00 cupsd
 5177 ?        00:00:00 dhcdbd
 5196 ?        00:00:01 hald
 5199 ?        00:00:00 console-kit-dae
 5261 ?        00:00:00 hald-runner
 5274 ?        00:00:08 hald-addon-usb-
 5282 ?        00:00:00 hald-addon-acpi
 5291 ?        00:00:00 hald-addon-inpu
 5307 ?        00:00:01 hald-addon-stor
 5330 ?        00:00:00 hcid
 5339 ?        00:00:00 btaddconn
 5340 ?        00:00:00 btdelconn
 5353 ?        00:00:00 bluetoothd-serv
 5354 ?        00:00:00 krfcommd
 5377 ?        00:00:00 bluetoothd-serv
 5422 ?        00:00:00 gdm
 5443 ?        00:00:00 dhclient
 5494 ?        00:00:00 atd
 5508 ?        00:00:00 cron
 5593 tty1     00:00:00 getty
 5689 ?        00:00:02 gconfd-2
 5807 ?        00:00:00 dbus-daemon
 5872 ?        00:00:00 gvfsd
 5907 ?        00:00:00 gvfs-fuse-daemo
 5923 ?        00:00:00 trackerd
 5944 ?        00:00:00 gvfsd-trash
 5954 ?        00:00:00 gvfsd-burn
 7788 ?        00:00:00 dbus-daemon
 7830 ?        00:00:00 gvfsd
 7868 ?        00:00:00 gvfsd-trash
 7924 ?        00:00:00 trackerd
 7942 ?        00:00:00 gvfsd-burn
 8181 ?        00:00:00 dbus-daemon
 8222 ?        00:00:00 gvfsd
 8249 ?        00:00:00 gvfsd-trash
 8315 ?        00:00:00 trackerd
 8327 ?        00:00:00 gvfsd-burn
 8581 ?        00:00:00 dbus-daemon
 8639 ?        00:00:00 gvfsd
 8678 ?        00:00:00 gvfsd-trash
 8706 ?        00:00:00 trackerd
 8730 ?        00:00:00 gvfsd-burn
 8942 ?        00:00:00 dbus-daemon
 9017 ?        00:00:00 gvfsd
 9058 ?        00:00:00 gvfsd-trash
 9082 ?        00:00:00 trackerd
 9109 ?        00:00:00 gvfsd-burn
 9336 ?        00:00:00 dbus-daemon
 9388 ?        00:00:00 gvfsd
 9419 ?        00:00:00 gvfsd-trash
 9464 ?        00:00:00 trackerd
 9493 ?        00:00:00 gvfsd-burn
 9699 ?        00:00:00 dbus-daemon
 9753 ?        00:00:00 gvfsd
 9788 ?        00:00:00 gvfsd-trash
 9827 ?        00:00:00 trackerd
 9848 ?        00:00:00 gvfsd-burn
10080 ?        00:00:00 dbus-daemon
10141 ?        00:00:00 gvfsd
10172 ?        00:00:00 gvfsd-trash
10208 ?        00:00:00 trackerd
10237 ?        00:00:00 gvfsd-burn
10878 ?        00:00:00 gnome-vfs-daemo
12070 ?        00:00:00 gdm
12105 tty7     00:00:50 Xorg
12115 tty7     00:00:00 Xorg
12132 ?        00:00:00 gnome-keyring-d
12133 ?        00:00:00 x-session-manag
12230 ?        00:00:00 seahorse-agent
12248 ?        00:00:00 dbus-daemon
12257 ?        00:00:00 pulseaudio
12260 ?        00:00:00 gconf-helper
12269 ?        00:00:00 compiz
12276 ?        00:00:03 gnome-panel
12277 ?        00:00:04 nautilus
12278 ?        00:00:00 gnome-screensav
12284 ?        00:00:00 bonobo-activati
12296 ?        00:00:00 gvfsd
12322 ?        00:00:00 trashapplet
12334 ?        00:00:00 gvfsd-trash
12357 ?        00:00:01 multiload-apple
12364 ?        00:00:00 mixer_applet2
12367 ?        00:00:00 fast-user-switc
12380 ?        00:00:05 compiz.real
12381 ?        00:00:00 bluetooth-apple
12385 ?        00:00:00 update-notifier
12388 ?        00:00:00 tracker-applet
12390 ?        00:00:00 evolution-alarm
12393 ?        00:00:00 trackerd
12397 ?        00:00:01 nm-applet
12398 ?        00:00:00 python
12400 ?        00:00:00 gnome-volume-ma
12401 ?        00:00:00 gnome-power-man
12404 ?        00:00:00 gvfsd-burn
12412 ?        00:00:00 sh
12413 ?        00:00:00 compiz-decorato
12415 ?        00:00:01 gtk-window-deco
12488 ?        00:00:00 gnome-settings-
12564 ?        00:00:00 gnome-vfs-daemo
12613 ?        00:00:11 opera
12665 ?        00:00:00 xterm
12666 pts/0    00:00:00 tn5250
12706 ?        00:00:00 gnome-terminal
12708 ?        00:00:00 gnome-pty-helpe
12709 pts/1    00:00:00 bash
12727 pts/1    00:00:00 ps

---

### Post by jrandolph on 2009-10-23
seems like alot of stuff to me 
I dont think i have ever seen this much in the past

---

### Post by jrandolph on 2009-10-23
Does anyone know why i have all this on my system monitor?

---

