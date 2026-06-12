---
title: "remove heat daemon"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Falc7 on 2009-01-07
I installed gdesklets, and it asked if i wanted to install a daemon to tell me the hard drive temperature, and it said this daemon would start every time the computer started. Now i have uninstalled gdesklets, is there a way to check if that daemon is still there, i dont want to have it on as i have noticed ubuntu takes a bit longer to load up once i log in.

---

### Post by Michael.Godawski on 2009-01-07
hi

check with these commands if you find your daemon somewhere:

```
ps -e

top

ls /etc/init.d
```

---

### Post by Falc7 on 2009-01-07
```
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
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  146 ?        00:00:00 cqueue
  150 ?        00:00:00 kseriod
  195 ?        00:00:00 pdflush
  196 ?        00:00:00 pdflush
  197 ?        00:00:00 kswapd0
  239 ?        00:00:00 aio/0
  240 ?        00:00:00 aio/1
 1196 ?        00:00:00 ksuspend_usbd
 1201 ?        00:00:00 khubd
 1433 ?        00:00:00 ata/0
 1435 ?        00:00:00 ata/1
 1436 ?        00:00:00 ata_aux
 2080 ?        00:00:00 scsi_eh_0
 2081 ?        00:00:00 scsi_eh_1
 2083 ?        00:00:00 scsi_eh_2
 2084 ?        00:00:00 scsi_eh_3
 2085 ?        00:00:00 scsi_eh_4
 2087 ?        00:00:00 scsi_eh_5
 2304 ?        00:00:00 kjournald
 2478 ?        00:00:00 udevd
 2875 ?        00:00:00 iwlagn/0
 2882 ?        00:00:02 iwlagn/1
 2884 ?        00:00:00 iwlagn
 2892 ?        00:00:00 kmmcd
 2922 ?        00:00:00 kpsmoused
 4504 tty4     00:00:00 getty
 4505 tty5     00:00:00 getty
 4508 tty2     00:00:00 getty
 4509 tty3     00:00:00 getty
 4510 tty6     00:00:00 getty
 4696 ?        00:00:00 acpid
 4754 ?        00:00:00 kondemand/0
 4755 ?        00:00:00 kondemand/1
 4822 ?        00:00:00 syslogd
 4871 ?        00:00:00 dd
 4873 ?        00:00:00 klogd
 4896 ?        00:00:00 dbus-daemon
 4918 ?        00:00:00 avahi-daemon
 4919 ?        00:00:00 avahi-daemon
 4966 ?        00:00:00 cupsd
 5111 ?        00:00:00 hddtemp
 5148 ?        00:00:00 nullmailer-send
 5173 ?        00:00:00 privoxy
 5194 ?        00:00:00 nmbd
 5196 ?        00:00:00 smbd
 5208 ?        00:00:00 smbd
 5213 ?        00:00:03 tor
 5236 ?        00:00:00 winbindd
 5258 ?        00:00:00 winbindd
 5259 ?        00:00:00 hald
 5262 ?        00:00:00 console-kit-dae
 5325 ?        00:00:00 hald-runner
 5345 ?        00:00:00 hald-addon-inpu
 5361 ?        00:00:00 hald-addon-cpuf
 5362 ?        00:00:00 hald-addon-acpi
 5379 ?        00:00:00 hald-addon-stor
 5415 ?        00:00:00 bluetoothd
 5422 ?        00:00:00 btaddconn
 5423 ?        00:00:00 btdelconn
 5454 ?        00:00:00 krfcommd
 5477 ?        00:00:00 NetworkManager
 5488 ?        00:00:00 wpa_supplicant
 5493 ?        00:00:00 nm-system-setti
 5515 ?        00:00:00 gdm
 5518 ?        00:00:00 gdm
 5522 tty7     00:06:52 Xorg
 5539 ?        00:00:00 system-tools-ba
 5576 ?        00:00:00 atd
 5605 ?        00:00:00 cron
 5686 tty1     00:00:00 getty
 5723 ?        00:00:00 gnome-keyring-d
 5734 ?        00:00:00 x-session-manag
 5790 ?        00:00:00 dbus-launch
 5791 ?        00:00:00 dbus-daemon
 5794 ?        00:00:16 pulseaudio
 5797 ?        00:00:00 gconf-helper
 5799 ?        00:00:02 gconfd-2
 5805 ?        00:00:00 seahorse-agent
 5811 ?        00:00:00 gnome-keyring-d
 5813 ?        00:00:02 gnome-settings-
 5814 ?        00:00:00 compiz
 5845 ?        00:00:00 gvfsd
 5872 ?        00:00:00 gvfs-fuse-daemo
 5884 ?        00:01:38 compiz.real
 5896 ?        00:00:12 gnome-screensav
 5897 ?        00:00:00 sh
 5898 ?        00:00:04 gtk-window-deco
 5899 ?        00:00:11 gnome-panel
 5901 ?        00:00:13 nautilus
 5903 ?        00:00:00 bonobo-activati
 5914 ?        00:00:00 gvfs-hal-volume
 5916 ?        00:00:00 gvfs-gphoto2-vo
 5922 ?        00:00:00 trashapplet
 5924 ?        00:00:00 gvfsd-trash
 5927 ?        00:00:00 gvfsd-burn
 5936 ?        00:00:00 python
 5940 ?        00:00:00 evolution-alarm
 5945 ?        00:00:00 bluetooth-apple
 5946 ?        00:00:00 trackerd
 5947 ?        00:00:00 update-notifier
 5950 ?        00:00:00 python
 5952 ?        00:00:01 python
 5953 ?        00:00:00 tracker-applet
 5954 ?        00:00:00 python
 5956 ?        00:00:00 nm-applet
 5959 ?        00:00:00 gnome-power-man
 5967 ?        00:00:00 evolution-excha
 5977 ?        00:00:00 gnome-brightnes
 5979 ?        00:00:00 fast-user-switc
 5997 ?        00:00:00 evolution-data-
 6067 ?        00:00:01 mixer_applet2
 6076 ?        00:00:00 at-spi-registry
 6094 ?        00:00:00 dhclient
 6115 ?        00:00:00 espeak-synthesi
 6118 ?        00:00:00 espeak-synthesi
 6187 ?        00:00:01 notification-da
 6191 ?        00:07:22 firefox
 6236 ?        00:00:00 winbindd
 6237 ?        00:00:00 winbindd
 6547 ?        00:00:22 soffice.bin
 7807 ?        00:00:00 gnome-terminal
 7809 ?        00:00:00 gnome-pty-helpe
 7810 pts/0    00:00:00 bash
 7828 pts/0    00:00:00 ps


```

```
wer@wer-laptop:~$ ls /etc/init.d
acpid                            mtab.sh
acpi-support                     networking
alsa-utils                       NetworkManager
anacron                          nullmailer
apmd                             pcmciautils
apparmor                         policykit
apport                           powernowd
atd                              powernowd.early
avahi-daemon                     pppd-dns
binfmt-support                   privoxy
bluetooth                        procps
bootlogd                         pulseaudio
bootmisc.sh                      rc
brltty                           rc.local
checkfs.sh                       rcS
checkroot.sh                     readahead
console-screen.kbd.sh            readahead-desktop
console-setup                    README
cron                             reboot
cups                             rmnologin
dbus                             rsync
dkms_autoinstaller               samba
dns-clean                        screen-cleanup
gdm                              sendsigs
glibc.sh                         single
hal                              skeleton
halt                             stop-bootlogd
hddtemp                          stop-bootlogd-single
hostname.sh                      stop-readahead
hotkey-setup                     sysklogd
hwclockfirst.sh                  system-tools-backends
hwclock.sh                       tor
keyboard-setup                   udev
killprocs                        udev-finish
klogd                            ufw
laptop-mode                      umountfs
linux-restricted-modules-common  umountnfs.sh
loopback                         umountroot
module-init-tools                urandom
mountall-bootclean.sh            usplash
mountall.sh                      vbesave
mountdevsubfs.sh                 winbind
mountkernfs.sh                   wpa-ifupdown
mountnfs-bootclean.sh            x11-common
mountnfs.sh                      xserver-xorg-input-wacom
mountoverflowtmp

```

I think it is there under HDDTemp, how do i remove it?

---

### Post by Falc7 on 2009-01-11
Anyone know?

---

### Post by Falc7 on 2009-01-17
No One?

---

