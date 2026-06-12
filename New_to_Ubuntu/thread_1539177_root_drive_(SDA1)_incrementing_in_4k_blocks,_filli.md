---
title: "root drive (SDA1) incrementing in 4k blocks, filling up drive"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by dragonneus on 2010-07-26
I have UNR on an Asus EEE 1000 with SSD drives and have had no issues on it. Noticed when checking on hard drive space that the root/ubuntu drive has been incrementing 4k every few seconds and doesn't stop. Ive run rkhunter and clamav in case something has infected files. Can anyone shed a light on this or perhaps is there a fix (if needed)?

for example:

/dev/sda1              7372864   4079548   2918788  59% 
/dev/sda1              7372864   4079552   2918784  59%
/dev/sda1              7372864   4079556   2918780  59%

Thank you for your responses

Dragonneus

---

### Post by cariboo on 2010-07-26
Check the log files located in /var/log, to see which one is filling up your drive.

---

### Post by dragonneus on 2010-07-27
I removed  all archived and old  logs. Watched and nothing out of the ordinary. Drive still filling in 4k increments. Thank you for your help.

---

### Post by anewguy on 2010-07-27
Post the output of ps -al from a terminal window.

---

### Post by dragonneus on 2010-07-28
dragonneus@FIREDRAKE:~$ ps -al
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 R  1000 14471 14367  0  80   0 -   624 -      pts/0    00:00:00 ps

---

### Post by anewguy on 2010-07-29
Sorry - make that sudo ps -al

---

### Post by dragonneus on 2010-07-29
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 R     0 15363 15346  5  80   0 -   624 -      pts/0    00:00:00 ps

---

### Post by anewguy on 2010-07-30
Sorry - I must have screwed up again as it is only showing 1 process.  I *think* what you need to do is ps -e  - try that and if you get a long list of processes that is what I really need to see.  If not, let me know and I'll figure out how I got so stupid ;)

Dave ;)

---

### Post by dragonneus on 2010-08-03
dragonneus@FIREDRAKE:~/DOWNLOADS$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:00 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:00 kblockd/0
   22 ?        00:00:00 kblockd/1
   23 ?        00:00:00 kacpid
   24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata/0
   27 ?        00:00:00 ata/1
   28 ?        00:00:00 ata_aux
   29 ?        00:00:00 ksuspend_usbd
   30 ?        00:00:00 khubd
   31 ?        00:00:00 kseriod
   32 ?        00:00:00 kmmcd
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 aio/0
   39 ?        00:00:00 aio/1
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto/0
   42 ?        00:00:00 crypto/1
   56 ?        00:00:00 scsi_eh_0
   57 ?        00:00:00 scsi_eh_1
   60 ?        00:00:00 kstriped
   61 ?        00:00:00 kmpathd/0
   62 ?        00:00:00 kmpathd/1
   63 ?        00:00:00 kmpath_handlerd
   64 ?        00:00:00 ksnapd
   65 ?        00:00:00 kondemand/0
   66 ?        00:00:00 kondemand/1
   67 ?        00:00:00 kconservative/0
   68 ?        00:00:00 kconservative/1
  260 ?        00:00:00 jbd2/sda1-8
  261 ?        00:00:00 ext4-dio-unwrit
  262 ?        00:00:00 ext4-dio-unwrit
  294 ?        00:00:00 flush-8:0
  323 ?        00:00:00 upstart-udev-br
  327 ?        00:00:00 udevd
  555 ?        00:00:00 kpsmoused
  569 ?        00:00:00 bluetooth
  576 ?        00:00:00 scsi_eh_2
  577 ?        00:00:00 usb-storage
  579 ?        00:00:00 scsi_eh_3
  580 ?        00:00:01 usb-storage
  664 ?        00:00:00 i915
  699 ?        00:00:00 hd-audio0
  782 ?        00:00:00 smbd
  790 ?        00:00:00 rsyslogd
  801 ?        00:00:01 dbus-daemon
  817 ?        00:00:00 gdm-binary
  823 ?        00:00:00 NetworkManager
  827 ?        00:00:00 smbd
  828 ?        00:00:00 avahi-daemon
  831 ?        00:00:00 avahi-daemon
  832 ?        00:00:00 modem-manager
  837 ?        00:00:00 console-kit-dae
  913 ?        00:00:00 gdm-simple-slav
  919 ?        00:00:00 wpa_supplicant
  944 tty7     00:00:52 Xorg
  954 tty4     00:00:00 getty
  966 tty5     00:00:00 getty
  973 tty2     00:00:00 getty
  975 tty3     00:00:00 getty
  977 tty6     00:00:00 getty
  982 ?        00:00:00 acpid
  984 ?        00:00:00 cron
  985 ?        00:00:00 atd
 1109 ?        00:00:00 freshclam
 1363 ?        00:00:00 exim4
 1418 ?        00:00:00 dbus-launch
 1449 ?        00:00:00 winbindd
 1451 ?        00:00:00 winbindd
 1458 ?        00:00:00 bluetoothd
 1466 ?        00:00:00 gpsd
 1501 ?        00:00:00 cupsd
 1519 ?        00:00:00 krfcommd
 1610 tty1     00:00:00 getty
 1620 ?        00:00:00 rtkit-daemon
 1624 ?        00:00:00 polkitd
 1625 ?        00:00:00 gdm-session-wor
 1627 ?        00:00:01 upowerd
 1672 ?        00:00:00 gnome-screensav
 1761 ?        00:00:00 gnome-keyring-d
 1779 ?        00:00:00 gnome-session
 1834 ?        00:00:00 ssh-agent
 1837 ?        00:00:00 dbus-launch
 1838 ?        00:00:01 dbus-daemon
 1841 ?        00:00:00 gconfd-2
 1848 ?        00:00:01 gnome-settings-
 1850 ?        00:00:00 gvfsd
 1855 ?        00:00:00 gvfs-fuse-daemo
 1859 ?        00:00:01 metacity
 1862 ?        00:00:09 pulseaudio
 1863 ?        00:00:00 sh
 1864 ?        00:00:14 netbook-launche
 1865 ?        00:00:01 gnome-power-man
 1866 ?        00:00:01 gnome-panel
 1867 ?        00:00:00 nautilus
 1870 ?        00:00:01 nm-applet
 1871 ?        00:00:00 bluetooth-apple
 1872 ?        00:00:00 eee-applet
 1873 ?        00:00:00 maximus
 1874 ?        00:00:00 polkit-gnome-au
 1877 ?        00:00:00 gconf-helper
 1881 ?        00:00:00 gvfs-gdu-volume
 1883 ?        00:00:01 syndaemon
 1885 ?        00:00:00 udisks-daemon
 1886 ?        00:00:00 udisks-daemon
 1888 ?        00:00:00 bonobo-activati
 1906 ?        00:00:00 indicator-apple
 1908 ?        00:00:03 window-picker-a
 1911 ?        00:00:00 go-home-applet
 1912 ?        00:00:00 notification-ar
 1913 ?        00:00:01 indicator-apple
 1914 ?        00:00:00 clock-applet
 1923 ?        00:00:00 gvfsd-metadata
 1925 ?        00:00:00 indicator-me-se
 1927 ?        00:00:00 gvfs-afc-volume
 1930 ?        00:00:00 gvfs-gphoto2-vo
 1933 ?        00:00:00 indicator-messa
 1935 ?        00:00:00 indicator-sessi
 1938 ?        00:00:00 kjournald
 1942 ?        00:00:00 indicator-sound
 1944 ?        00:00:00 indicator-appli
 1948 ?        00:00:00 gnome-screensav
 1949 ?        00:00:00 dhclient
 1957 ?        00:00:00 gdu-notificatio
 1962 ?        00:00:00 notify-osd
 2011 ?        00:00:00 nmbd
 2013 ?        00:00:00 gnome-user-shar
 2015 ?        00:00:00 obex-data-serve
 2027 ?        00:00:00 dbus-launch
 2028 ?        00:00:00 dbus-daemon
 2048 ?        00:00:00 python
 2062 ?        00:00:00 update-notifier
 2069 ?        00:00:00 system-service-
 2233 ?        00:00:14 gnome-terminal
 2234 ?        00:00:00 gnome-pty-helpe
 2419 pts/1    00:00:01 bash
 2443 pts/1    00:00:01 nweather.py
 2459 pts/1    00:00:02 nweather.py
 2545 ?        00:00:00 udevd
 2546 ?        00:00:00 udevd
 2590 ?        00:00:00 flush-8:16
 2632 ?        00:00:00 flush-8:48
 2648 pts/0    00:00:00 bash
 2713 ?        00:00:08 chrome
 2716 ?        00:00:00 chrome
 2718 ?        00:00:00 chrome
 2791 ?        00:00:05 chrome
 2803 pts/1    00:00:00 ps

---

