---
title: "Problem with bypassing password for  'apt-get'"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by ptn107 on 2009-03-06
So I've added the following line to /etc/sudoers with the correct syntax:
```
phil	ALL=(ALL) NOPASSWD: /usr/bin/apt-get
```

Yet when I run apt-get from the command line I get the error:

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```

Ideas?

*Yes I know this is a security issue so please don't lecture me.  I am the only user of the machine and I'm already in the admin group anyway.

---

### Post by taurus on 2009-03-06
There is another process (update manager, add/remove, synpatic, etc.) using adept so until you close that first, you cannot run apt-get.

---

### Post by ptn107 on 2009-03-06
> **taurus said:**
> There is another process (update manager, add/remove, synpatic, etc.) using adept so until you close that first, you cannot run apt-get.

I've got no other package managers open.

---

### Post by taurus on 2009-03-06
Post the output of this command from a terminal.

```
ps -A
```

---

### Post by ptn107 on 2009-03-06
```
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:09 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:01 events/0
    7 ?        00:00:00 khelper
   44 ?        00:00:00 kintegrityd/0
   46 ?        00:00:01 kblockd/0
   48 ?        00:00:00 kacpid
   49 ?        00:00:00 kacpi_notify
  118 ?        00:00:00 cqueue
  122 ?        00:00:00 kseriod
  170 ?        00:00:04 kswapd0
  216 ?        00:00:00 aio/0
 1221 ?        00:00:00 ksuspend_usbd
 1226 ?        00:00:00 khubd
 1229 ?        00:00:25 ata/0
 1235 ?        00:00:00 ata_aux
 1742 ?        00:00:00 scsi_eh_0
 1743 ?        00:00:00 scsi_eh_1
 1999 ?        00:00:00 scsi_eh_2
 2000 ?        00:01:13 scsi_eh_3
 2183 ?        00:00:00 kjournald
 2359 ?        00:00:00 udevd
 2636 ?        00:00:00 kgameportd
 2660 ?        00:00:00 kpsmoused
 3923 ?        00:00:05 kjournald
 3924 ?        00:00:00 kjournald
 4334 tty4     00:00:00 getty
 4335 tty5     00:00:00 getty
 4345 tty2     00:00:00 getty
 4347 tty3     00:00:00 getty
 4349 tty6     00:00:00 getty
 4519 ?        00:00:00 acpid
 4548 ?        00:00:01 kondemand/0
 4631 ?        00:00:00 syslogd
 4681 ?        00:00:00 dd
 4683 ?        00:00:00 klogd
 4706 ?        00:00:10 dbus-daemon
 4728 ?        00:00:01 avahi-daemon
 4729 ?        00:00:00 avahi-daemon
 4752 ?        00:00:00 sshd
 4762 ?        00:00:20 spamd
 4788 ?        00:00:00 cupsd
 4971 ?        00:00:00 chipcardd4
 4972 ?        00:10:00 chipcardd4
 5008 ?        00:00:00 timevault
 5080 ?        00:00:00 gam_server
 5107 ?        00:00:01 hald
 5110 ?        00:00:00 console-kit-dae
 5173 ?        00:00:00 hald-runner
 5192 ?        00:00:00 hald-addon-inpu
 5198 ?        00:00:00 hald-addon-cpuf
 5199 ?        00:00:00 hald-addon-acpi
 5205 ?        00:00:10 hald-addon-stor
 5208 ?        00:00:10 hald-addon-stor
 5255 ?        00:00:17 NetworkManager
 5259 ?        00:00:02 wpa_supplicant
 5262 ?        00:00:00 nm-system-setti
 5293 ?        00:00:00 gdm
 5296 ?        00:00:00 gdm
 5300 tty7     00:16:03 Xorg
 5317 ?        00:00:00 system-tools-ba
 5356 ?        00:00:00 atd
 5386 ?        00:00:00 cron
 5469 tty1     00:00:00 getty
 5482 ?        00:00:00 spamd
 5483 ?        00:00:00 spamd
 5540 ?        00:00:00 gnome-keyring-d
 5550 ?        00:00:00 x-session-manag
 5669 ?        00:00:00 dbus-launch
 5670 ?        00:00:02 dbus-daemon
 5673 ?        00:02:54 pulseaudio
 5676 ?        00:00:00 gconf-helper
 5678 ?        00:00:11 gconfd-2
 5684 ?        00:00:00 seahorse-agent
 5687 ?        00:00:00 gvfsd
 5688 ?        00:00:00 gnome-keyring-d
 5698 ?        00:00:00 gvfs-fuse-daemo
 5702 ?        00:00:13 gnome-settings-
 5703 ?        00:00:00 compiz
 5767 ?        00:05:56 compiz.real
 5775 ?        00:00:36 gnome-screensav
 5776 ?        00:00:00 sh
 5777 ?        00:00:00 compiz-decorato
 5779 ?        00:00:28 gtk-window-deco
 5780 ?        00:00:44 gnome-panel
 5782 ?        00:02:16 nautilus
 5784 ?        00:00:00 bonobo-activati
 5792 ?        00:00:00 gvfs-hal-volume
 5794 ?        00:00:00 gvfs-gphoto2-vo
 5797 ?        00:00:01 trashapplet
 5800 ?        00:00:00 gvfsd-trash
 5808 ?        00:00:00 gvfsd-burn
 5813 ?        00:00:00 fast-user-switc
 5816 ?        00:00:00 mixer_applet2
 5829 ?        00:00:02 python
 5832 ?        00:00:02 update-notifier
 5834 ?        00:00:10 nm-applet
 5837 ?        00:00:00 bluetooth-apple
 5838 ?        00:00:00 tracker-applet
 5839 ?        00:00:00 timevault-notif
 5840 ?        00:00:00 trackerd
 5841 ?        00:00:01 vino-server
 5844 ?        00:00:00 evolution-alarm
 5849 ?        00:00:01 gnome-power-man
 5854 ?        00:00:05 notification-da
 5859 ?        00:00:00 evolution-data-
 5863 ?        00:00:00 evolution-excha
 5891 ?        00:00:00 dhclient
 6017 ?        00:00:03 ntpd
 6714 ?        00:00:00 pdflush
 6717 ?        00:00:04 pdflush
 8108 ?        00:01:25 gnome-terminal
 8110 ?        00:00:00 gnome-pty-helpe
 8111 pts/0    00:00:00 bash
10295 pts/0    00:00:52 wget
10297 ?        00:00:05 pidgin
10300 ?        00:06:35 firefox
10398 ?        00:04:22 amarokapp
10403 ?        00:00:00 kdeinit
10408 ?        00:00:00 dcopserver
10411 ?        00:00:00 klauncher
10413 ?        00:00:01 kded
10421 ?        00:00:00 kio_file
10430 ?        00:00:00 ruby
10678 pts/1    00:00:00 bash
10796 pts/1    00:00:00 dbus-launch
10797 ?        00:00:00 dbus-daemon
11702 ?        00:00:00 kio_http
11711 ?        00:00:20 xchat-gnome
11840 pts/1    00:00:00 ps
```

---

### Post by taurus on 2009-03-06
Do you see an icon on the upper right corner telling you that you have updates?

---

### Post by ptn107 on 2009-03-06
I figured it out.  Even though I tell /etc/sudoers NOPASSWD, I still have to prefix the command with sudo.  Grr.

---

