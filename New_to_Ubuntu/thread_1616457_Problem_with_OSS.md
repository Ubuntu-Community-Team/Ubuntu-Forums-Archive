---
title: "Problem with OSS"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by Shafaet on 2010-11-08
After facing some weird sound problem i turned to OSS from Alsa. I installed OSS using this guideline [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound).
OSS worked well after installation but after the first reboot the sound is gone. what should i do now? i checked the init script and it says the oss is on

```
shafaet@shafaet-cse:~$ ls -1 /etc/init.d
acpid
acpi-support
anacron
apparmor
apport
atd
avahi-daemon
binfmt-support
bluetooth
bootlogd
brltty
console-setup
cron
cups
dbus
dmesg
dns-clean
failsafe-x
fancontrol
gdm
grub-common
halt
hostname
hwclock
hwclock-save
irqbalance
kerneloops
killprocs
lm-sensors
module-init-tools
networking
network-interface
network-interface-security
network-manager
ondemand
oss
pcmciautils
plymouth
plymouth-log
plymouth-splash
plymouth-stop
pppd-dns
procps
rc
rc.local
rcS
README
reboot
rsync
rsyslog
saned
screen-cleanup
sendsigs
single
skeleton
speech-dispatcher
stop-bootlogd
stop-bootlogd-single
sudo
udev
udev-finish
udevmonitor
udevtrigger
ufw
umountfs
umountnfs.sh
umountroot
unattended-upgrades
urandom
x11-common
shafaet@shafaet-cse:~$ sudo soundon
OSS is already loaded.
shafaet@shafaet-cse:~$ 

```

---

