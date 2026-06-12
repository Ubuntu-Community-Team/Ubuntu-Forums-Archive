---
title: "Removed Bluez - Now NO Internet in v22.04"
date: 2024-06-09
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2024-06-09
After removing / deleting Bluez, since I have no BlueTooth tech on my Desktop, I now have NO internet. 
After much searching ... cannot find an answer of How to Enable Networking in v22.04? And before you fail to read the below output ... NO v22.04 did not install ifconfig or Net Tools.

```

ms7640:~$ sudo lshw -C network

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 44:8a:5b:97:f6:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=6.5.0-35-lowlatency latency=0 link=no multicast=yes
       resources: irq:31 ioport:d000(size=256) memory:fe904000-fe904fff memory:fe900000-fe903fff


```

So, my Network is down ... How to Re-Enable it ? ? ?

```

ms7640:~$ ifconfig -a
Command 'ifconfig' not found, but can be installed with:
sudo apt install net-tools
</code>

Cannot install anything with no internet. Can't find Network Mgr new System  Settings.
After reading a number of blogs, v22.04 maybe using Netplan. So;

<code>
ms7640:~$ netplan status
     Online state: offline
    DNS Addresses: 127.0.0.53 (stub)
       DNS Search: .

&#9679;  1: lo ethernet UNKNOWN/UP (unmanaged)
      MAC Address: 00:00:00:00:00:00
        Addresses: 127.0.0.1/8
                   ::1/128
           Routes: ::1 metric 256

2 inactive interfaces hidden. Use "--all" to show all.

ms7640:~$ netplan try

** (process:3913): WARNING **: 11:48:28.118: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

** (generate:3915): WARNING **: 11:48:28.125: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
ERROR: cannot create file /run/systemd/system/netplan-ovs-cleanup.service: Failed to create file &#8220;/run/systemd/system/netplan-ovs-cleanup.service.E4M1O2&#8221;: Permission denied

An error occurred: the configuration could not be generated

Reverting.

** (process:3913): WARNING **: 11:48:28.128: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

** (process:3913): WARNING **: 11:48:28.129: Permissions for /tmp/tmpardgbuqq/etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
enp2s0: Failed to write 'change' to '/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0/uevent': Permission denied
lo: Failed to write 'change' to '/sys/devices/virtual/net/lo/uevent': Permission denied
virbr0: Failed to write 'change' to '/sys/devices/virtual/net/virbr0/uevent': Permission denied
Traceback (most recent call last):
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 101, in command_try
    NetplanApply().command_apply(run_generate=True, sync=True, exit_on_error=False, state_dir=self.state)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 133, in command_apply
    raise ConfigurationError("the configuration could not be generated")
netplan.configmanager.ConfigurationError: the configuration could not be generated

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/sbin/netplan", line 23, in <module>
    netplan.main()
  File "/usr/share/netplan/netplan/cli/core.py", line 56, in main
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 243, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 83, in run
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 243, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 115, in command_try
    self.revert()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 145, in revert
    NetplanApply().command_apply(run_generate=False, sync=True, exit_on_error=False, state_dir=tempdir)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 258, in command_apply
    subprocess.check_call(['udevadm', 'trigger', '--attr-match=subsystem=net'])
  File "/usr/lib/python3.10/subprocess.py", line 369, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['udevadm', 'trigger', '--attr-match=subsystem=net']' returned non-zero exit status 1.

```

So again, after removing an unecessary pkg, it has corrupted my system.
How do regain my Internet Connection / Enable Ethernet, since Enable Netplan doesn't work?

Thanks for any help!

---

### Post by Rick St. George on 2024-06-09
Attempted DNF History ...

```

ms7640:~$ sudo dnf history
sudo: dnf: command not found

```

So, tried this ...

```

ms7640:~$ resolvectl status
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 2 (enp2s0)
Current Scopes: none
     Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported

Link 3 (virbr0)
Current Scopes: none
     Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported

```

We know my Ethernet is "enp2s0". What about Network Mgr.?

```

ms7640:~$ systemctl status NetworkManager
&#9675; NetworkManager.service
     Loaded: masked (Reason: Unit NetworkManager.service is masked.)
     Active: inactive (dead)

```

Why is it masked? Removing Bluez had something to do with it. But I don't have
BlueTooth on my Desktop / Main System. Mabe I can Re-activate it?

```

ms7640:~$ systemctl unmask NetworkManager.service
Removed /etc/systemd/system/NetworkManager.service.
stephen@ms7640:~$ systemctl enable NetworkManager.service
Failed to enable unit: Unit file NetworkManager.service does not exist.
stephen@ms7640:~$ sudo service network-manager start
Failed to start network-manager.service: Unit network-manager.service not found.
stephen@ms7640:~$ sudo service NetworkManager start
Failed to start NetworkManager.service: Unit NetworkManager.service not found.
stephen@ms7640:~$ sudo service NetworkManager status
Unit NetworkManager.service could not be found.
stephen@ms7640:~$ sudo service Network-Manager status
Unit Network-Manager.service could not be found.

```

So much for that!  Let's see .... Hmmm;

```

ms7640:~$ systemctl list-unit-files
UNIT FILE                                             STATE           VENDOR PRESET
proc-sys-fs-binfmt_misc.automount                     static          -
-.mount                                               generated       -
boot-efi.mount                                        generated       -
dev-hugepages.mount                                   static          -
dev-mqueue.mount                                      static          -
home.mount                                            generated       -
proc-sys-fs-binfmt_misc.mount                         disabled        disabled
run-qemu.mount                                        enabled         enabled
snap-bare-5.mount                                     enabled         enabled
snap-brave-409.mount                                  enabled         enabled
snap-brave-411.mount                                  enabled         enabled
snap-canonical\x2dlivepatch-278.mount                 enabled         enabled
snap-core22-1122.mount                                enabled         enabled
snap-core22-1380.mount                                enabled         enabled
snap-firefox-3779.mount                               enabled         enabled
snap-firefox-4336.mount                               enabled         enabled
snap-gnome\x2d42\x2d2204-141.mount                    enabled         enabled
snap-gnome\x2d42\x2d2204-176.mount                    enabled         enabled
snap-gtk\x2dcommon\x2dthemes-1535.mount               enabled         enabled
snap-snapd-20671.mount                                enabled         enabled
snap-snapd-21759.mount                                enabled         enabled
sys-fs-fuse-connections.mount                         static          -
sys-kernel-config.mount                               static          -
sys-kernel-debug.mount                                static          -
sys-kernel-tracing.mount                              static          -
tmp.mount                                             generated       -
var-lib-machines.mount                                static          -
var-snap-firefox-common-host\x2dhunspell.mount        enabled         enabled
acpid.path                                            enabled         enabled
apport-autoreport.path                                enabled         enabled
cups.path                                             enabled         enabled
systemd-ask-password-console.path                     static          -
systemd-ask-password-plymouth.path                    static          -
systemd-ask-password-wall.path                        static          -
whoopsie.path                                         enabled         enabled
session-3.scope                                       transient       -
accounts-daemon.service                               enabled         enabled
acpid.service                                         disabled        enabled
alsa-restore.service                                  static          -
alsa-state.service                                    static          -
alsa-utils.service                                    masked          enabled
anacron.service                                       enabled         enabled
apparmor.service                                      enabled         enabled
apport-autoreport.service                             static          -
apport-forward@.service                               static          -
apport.service                                        generated       -
apt-daily-upgrade.service                             static          -
apt-daily.service                                     static          -
apt-news.service                                      static          -
autovt@.service                                       alias           -
avahi-daemon.service                                  enabled         enabled
blk-availability.service                              enabled         enabled
bluetooth.service                                     masked          enabled
bolt.service                                          static          -
clamav-daemon.service                                 enabled         enabled
clamav-freshclam.service                              enabled         enabled
colord.service                                        static          -
configure-printer@.service                            static          -
console-getty.service                                 disabled        disabled
console-setup.service                                 enabled         enabled
container-getty@.service                              static          -
cron.service                                          enabled         enabled
cryptdisks-early.service                              masked          enabled
cryptdisks.service                                    masked          enabled
cups-browsed.service                                  enabled         enabled
cups.service                                          enabled         enabled
dbus-fi.w1.wpa_supplicant1.service                    alias           -
dbus-org.bluez.service                                masked          enabled
dbus-org.freedesktop.Avahi.service                    alias           -
dbus-org.freedesktop.hostname1.service                alias           -
dbus-org.freedesktop.import1.service                  alias           -
dbus-org.freedesktop.locale1.service                  alias           -
dbus-org.freedesktop.login1.service                   alias           -
dbus-org.freedesktop.machine1.service                 alias           -
dbus-org.freedesktop.ModemManager1.service            alias           -
dbus-org.freedesktop.nm-dispatcher.service            masked          enabled
dbus-org.freedesktop.portable1.service                alias           -
dbus-org.freedesktop.resolve1.service                 alias           -
dbus-org.freedesktop.thermald.service                 alias           -
dbus-org.freedesktop.timedate1.service                alias           -
dbus-org.freedesktop.timesync1.service                alias           -
dbus.service                                          static          -
debug-shell.service                                   disabled        disabled
display-manager.service                               alias           -
dm-event.service                                      static          -
dmesg.service                                         enabled         enabled
dpkg-db-backup.service                                static          -
e2scrub@.service                                      static          -
e2scrub_all.service                                   static          -
e2scrub_fail@.service                                 static          -
e2scrub_reap.service                                  enabled         enabled
emergency.service                                     static          -
esm-cache.service                                     static          -
finalrd.service                                       enabled         enabled
friendly-recovery.service                             static          -
fstrim.service                                        static          -
fwupd-offline-update.service                          static          -
fwupd-refresh.service                                 static          -
fwupd.service                                         static          -
gdomap.service                                        generated       -
geoclue.service                                       static          -
getty-static.service                                  static          -
getty@.service                                        enabled         enabled
gpu-manager.service                                   enabled         enabled
grub-common.service                                   enabled         enabled
grub-initrd-fallback.service                          enabled         enabled
haveged.service                                       enabled         enabled
hwclock.service                                       masked          enabled
iio-sensor-proxy.service                              static          -
initrd-cleanup.service                                static          -
initrd-parse-etc.service                              static          -
initrd-switch-root.service                            static          -
initrd-udevadm-cleanup-db.service                     static          -
ipp-usb.service                                       static          -
irqbalance.service                                    enabled         enabled
kerneloops.service                                    enabled         enabled
keyboard-setup.service                                enabled         enabled
kmod-static-nodes.service                             static          -
kmod.service                                          alias           -
libvirt-guests.service                                enabled         enabled
libvirtd.service                                      enabled         enabled
logrotate.service                                     static          -
lvm2-lvmpolld.service                                 static          -
lvm2-monitor.service                                  enabled         enabled
lvm2-pvscan@.service                                  static          -
lvm2.service                                          masked          enabled
man-db.service                                        static          -
mdadm-grow-continue@.service                          static          -
mdadm-last-resort@.service                            static          -
mdcheck_continue.service                              static          -
mdcheck_start.service                                 static          -
mdmon@.service                                        static          -
mdmonitor-oneshot.service                             static          -
mdmonitor.service                                     static          -
minidlna.service                                      enabled         enabled
ModemManager.service                                  enabled         enabled
modprobe@.service                                     static          -
motd-news.service                                     static          -
netplan-ovs-cleanup.service                           enabled-runtime enabled
networkd-dispatcher.service                           enabled         enabled
NetworkManager-dispatcher.service                     masked          enabled
NetworkManager-wait-online.service                    masked          enabled
nftables.service                                      disabled        enabled
osspd.service                                         enabled         enabled
packagekit-offline-update.service                     static          -
packagekit.service                                    static          -
plocate-updatedb.service                              static          -
plymouth-halt.service                                 static          -
plymouth-kexec.service                                static          -
plymouth-log.service                                  alias           -
plymouth-poweroff.service                             static          -
plymouth-quit-wait.service                            static          -
plymouth-quit.service                                 static          -
plymouth-read-write.service                           static          -
plymouth-reboot.service                               static          -
plymouth-start.service                                static          -
plymouth-switch-root-initramfs.service                static          -
plymouth-switch-root.service                          static          -
plymouth.service                                      alias           -
polkit.service                                        static          -
power-profiles-daemon.service                         enabled         enabled
procps.service                                        alias           -
pulseaudio-enable-autospawn.service                   masked          enabled
qemu-kvm.service                                      enabled         enabled
quotaon.service                                       static          -
rc-local.service                                      static          -
rc.service                                            masked          enabled
rcS.service                                           masked          enabled
rescue.service                                        static          -
rsync.service                                         disabled        enabled
rsyslog.service                                       enabled         enabled
rtirq.service                                         generated       -
rtkit-daemon.service                                  disabled        enabled
saned.service                                         masked          enabled
saned@.service                                        indirect        enabled
sddm.service                                          enabled         enabled
secureboot-db.service                                 enabled         enabled
serial-getty@.service                                 disabled        enabled
setvtrgb.service                                      enabled         enabled
smartd.service                                        alias           -
smartmontools.service                                 enabled         enabled
snap.canonical-livepatch.canonical-livepatchd.service enabled         enabled
snapd.apparmor.service                                enabled         enabled
snapd.autoimport.service                              enabled         enabled
snapd.core-fixup.service                              enabled         enabled
snapd.failure.service                                 static          -
snapd.recovery-chooser-trigger.service                enabled         enabled
snapd.seeded.service                                  enabled         enabled
snapd.service                                         enabled         enabled
snapd.snap-repair.service                             static          -
snapd.system-shutdown.service                         enabled         enabled
spice-vdagent.service                                 alias           -
spice-vdagentd.service                                indirect        enabled
studio-system.service                                 enabled         enabled
sudo.service                                          masked          enabled
syslog.service                                        alias           -
system-update-cleanup.service                         static          -
systemd-ask-password-console.service                  static          -
systemd-ask-password-plymouth.service                 static          -
systemd-ask-password-wall.service                     static          -
systemd-backlight@.service                            static          -
systemd-binfmt.service                                static          -
systemd-bless-boot.service                            static          -
systemd-boot-check-no-failures.service                disabled        disabled
systemd-boot-system-token.service                     static          -
systemd-exit.service                                  static          -
systemd-fsck-root.service                             enabled-runtime enabled
systemd-fsck@.service                                 static          -
systemd-fsckd.service                                 static          -
systemd-halt.service                                  static          -
systemd-hibernate-resume@.service                     static          -
systemd-hibernate.service                             static          -
systemd-hostnamed.service                             static          -
systemd-hybrid-sleep.service                          static          -
systemd-importd.service                               static          -
systemd-initctl.service                               static          -
systemd-journal-flush.service                         static          -
systemd-journald.service                              static          -
systemd-journald@.service                             static          -
systemd-kexec.service                                 static          -
systemd-localed.service                               static          -
systemd-logind.service                                static          -
systemd-machine-id-commit.service                     static          -
systemd-machined.service                              static          -
systemd-modules-load.service                          static          -
systemd-network-generator.service                     disabled        enabled
systemd-networkd-wait-online.service                  disabled        disabled
systemd-networkd.service                              disabled        enabled
systemd-nspawn@.service                               disabled        enabled
systemd-portabled.service                             static          -
systemd-poweroff.service                              static          -
systemd-pstore.service                                enabled         enabled
systemd-quotacheck.service                            static          -
systemd-random-seed.service                           static          -
systemd-reboot.service                                static          -
systemd-remount-fs.service                            enabled-runtime enabled
systemd-resolved.service                              enabled         enabled
systemd-rfkill.service                                static          -
systemd-suspend-then-hibernate.service                static          -
systemd-suspend.service                               static          -
systemd-sysctl.service                                static          -
systemd-sysext.service                                disabled        enabled
systemd-sysusers.service                              static          -
systemd-time-wait-sync.service                        disabled        disabled
systemd-timedated.service                             static          -
systemd-timesyncd.service                             enabled         enabled
systemd-tmpfiles-clean.service                        static          -
systemd-tmpfiles-setup-dev.service                    static          -
systemd-tmpfiles-setup.service                        static          -
systemd-udev-settle.service                           static          -
systemd-udev-trigger.service                          static          -
systemd-udevd.service                                 static          -
systemd-update-utmp-runlevel.service                  static          -
systemd-update-utmp.service                           static          -
systemd-user-sessions.service                         static          -
systemd-volatile-root.service                         static          -
thermald.service                                      enabled         enabled
ua-reboot-cmds.service                                enabled         enabled
ua-timer.service                                      static          -
ubuntu-advantage.service                              enabled         enabled
udev.service                                          alias           -
udisks2.service                                       enabled         enabled
ufw.service                                           enabled         enabled
unattended-upgrades.service                           enabled         enabled
update-notifier-download.service                      static          -
update-notifier-motd.service                          static          -
upower.service                                        disabled        enabled
usb_modeswitch@.service                               static          -
usbmuxd.service                                       static          -
user-runtime-dir@.service                             static          -
user@.service                                         static          -
uuidd.service                                         indirect        enabled
virtlockd.service                                     indirect        enabled
virtlogd.service                                      indirect        enabled
wacom-inputattach@.service                            static          -
whoopsie.service                                      static          -
wpa_supplicant-nl80211@.service                       disabled        enabled
wpa_supplicant-wired@.service                         disabled        enabled
wpa_supplicant.service                                enabled         enabled
wpa_supplicant@.service                               disabled        enabled
x11-common.service                                    masked          enabled
xfs_scrub@.service                                    static          -
xfs_scrub_all.service                                 static          -
xfs_scrub_fail@.service                               static          -
machine.slice                                         static          -
system-systemd\x2dcryptsetup.slice                    static          -
user.slice                                            static          -
acpid.socket                                          enabled         enabled
apport-forward.socket                                 enabled         enabled
avahi-daemon.socket                                   enabled         enabled
cups.socket                                           enabled         enabled
dbus.socket                                           static          -
dm-event.socket                                       enabled         enabled
libvirtd-admin.socket                                 enabled         enabled
libvirtd-ro.socket                                    enabled         enabled
libvirtd-tcp.socket                                   disabled        enabled
libvirtd-tls.socket                                   disabled        enabled
libvirtd.socket                                       enabled         enabled
lvm2-lvmpolld.socket                                  enabled         enabled
saned.socket                                          disabled        enabled
snapd.socket                                          enabled         enabled
spice-vdagentd.socket                                 static          -
syslog.socket                                         static          -
systemd-fsckd.socket                                  static          -
systemd-initctl.socket                                static          -
systemd-journald-audit.socket                         static          -
systemd-journald-dev-log.socket                       static          -
systemd-journald-varlink@.socket                      static          -
systemd-journald.socket                               static          -
systemd-journald@.socket                              static          -
systemd-networkd.socket                               disabled        enabled
systemd-rfkill.socket                                 static          -
systemd-udevd-control.socket                          static          -
systemd-udevd-kernel.socket                           static          -
uuidd.socket                                          enabled         enabled
virtlockd-admin.socket                                enabled         enabled
virtlockd.socket                                      enabled         enabled
virtlogd-admin.socket                                 enabled         enabled
virtlogd.socket                                       enabled         enabled
basic.target                                          static          -
blockdev@.target                                      static          -
bluetooth.target                                      static          -
boot-complete.target                                  static          -
cryptsetup-pre.target                                 static          -
cryptsetup.target                                     static          -
ctrl-alt-del.target                                   alias           -
default.target                                        alias           -
emergency.target                                      static          -
exit.target                                           disabled        disabled
final.target                                          static          -
first-boot-complete.target                            static          -
friendly-recovery.target                              static          -
getty-pre.target                                      static          -
getty.target                                          static          -
graphical.target                                      static          -
halt.target                                           disabled        disabled
hibernate.target                                      static          -
hybrid-sleep.target                                   static          -
initrd-fs.target                                      static          -
initrd-root-device.target                             static          -
initrd-root-fs.target                                 static          -
initrd-switch-root.target                             static          -
initrd-usr-fs.target                                  static          -
initrd.target                                         static          -
kexec.target                                          disabled        disabled
local-fs-pre.target                                   static          -
local-fs.target                                       static          -
machines.target                                       enabled         enabled
multi-user.target                                     static          -
network-online.target                                 static          -
network-pre.target                                    static          -
network.target                                        static          -
nss-lookup.target                                     static          -
nss-user-lookup.target                                static          -
paths.target                                          static          -
poweroff.target                                       disabled        disabled
printer.target                                        static          -
reboot.target                                         disabled        enabled
remote-cryptsetup.target                              disabled        enabled
remote-fs-pre.target                                  static          -
remote-fs.target                                      enabled         enabled
remote-veritysetup.target                             disabled        enabled
rescue.target                                         static          -
rpcbind.target                                        static          -
runlevel0.target                                      alias           -
runlevel1.target                                      alias           -
runlevel2.target                                      alias           -
runlevel3.target                                      alias           -
runlevel4.target                                      alias           -
runlevel5.target                                      alias           -
runlevel6.target                                      alias           -
shutdown.target                                       static          -
sigpwr.target                                         static          -
sleep.target                                          static          -
slices.target                                         static          -
smartcard.target                                      static          -
snapd.mounts-pre.target                               static          -
snapd.mounts.target                                   static          -
sockets.target                                        static          -
sound.target                                          static          -
suspend-then-hibernate.target                         static          -
suspend.target                                        static          -
swap.target                                           static          -
sysinit.target                                        static          -
system-update-pre.target                              static          -
system-update.target                                  static          -
time-set.target                                       static          -
time-sync.target                                      static          -
timers.target                                         static          -
umount.target                                         static          -
usb-gadget.target                                     static          -
veritysetup-pre.target                                static          -
veritysetup.target                                    static          -
virt-guest-shutdown.target                            static          -
anacron.timer                                         enabled         enabled
apport-autoreport.timer                               enabled         enabled
apt-daily-upgrade.timer                               enabled         enabled
apt-daily.timer                                       enabled         enabled
dpkg-db-backup.timer                                  enabled         enabled
e2scrub_all.timer                                     enabled         enabled
fstrim.timer                                          enabled         enabled
fwupd-refresh.timer                                   enabled         enabled
logrotate.timer                                       enabled         enabled
man-db.timer                                          enabled         enabled
mdadm-last-resort@.timer                              static          -
mdcheck_continue.timer                                enabled         enabled
mdcheck_start.timer                                   enabled         enabled
mdmonitor-oneshot.timer                               enabled         enabled
motd-news.timer                                       enabled         enabled
plocate-updatedb.timer                                enabled         enabled
snapd.snap-repair.timer                               enabled         enabled
systemd-tmpfiles-clean.timer                          static          -
ua-timer.timer                                        enabled         enabled
update-notifier-download.timer                        enabled         enabled
update-notifier-motd.timer                            enabled         enabled
xfs_scrub_all.timer                                   disabled        enabled

416 unit files listed.
lines 371-419/419 (END)

```

Ok ... a number of systems are disabled or masked. Am I going to have to
Re-Install v22.04 OS for a 4th time???

Here is what the Journal shows;

```

Jun 09 07:31:11 ms7640 systemd[1]: Starting Network Manager...
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.7143] NetworkManager (version 1.36.6) is starting... (for the first time)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.7154] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf>
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.7490] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Jun 09 07:31:11 ms7640 systemd[1]: Started Network Manager.
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.7574] manager[0x58630b2e4000]: monitoring kernel firmware directory '/lib/firmware'.
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.7575] monitoring ifupdown state file '/run/network/ifstate'.
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9583] hostname: hostname: using hostnamed
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9583] hostname: static hostname changed from (none) to "ms7640"
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9630] dns-mgr[0x58630b2c22a0]: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9644] manager[0x58630b2e4000]: rfkill: Wi-Fi hardware radio set enabled
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9645] manager[0x58630b2e4000]: rfkill: WWAN hardware radio set enabled
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9721] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-team.so)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9758] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9770] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-adsl.so)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9932] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9972] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wifi.so)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9976] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9977] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9977] manager: Networking is enabled by state file
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9997] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-settings-plugin-ifupdown.so")
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9997] settings: Loaded settings plugin: keyfile (internal)
Jun 09 07:31:11 ms7640 NetworkManager[853]: <info>  [1717936271.9997] ifupdown: management mode: unmanaged
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936271.9999] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.0058] dhcp-init: Using DHCP client 'internal'
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.0058] device (lo): carrier: link connected
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.0062] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.0076] manager: (enp2s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.0083] device (enp2s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.2230] failed to open /run/network/ifstate
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.2276] modem-manager: ModemManager available
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.2439] manager: (virbr0): new Bridge device (/org/freedesktop/NetworkManager/Devices/3)
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5896] device (virbr0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5903] device (virbr0): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5912] device (virbr0): Activation: starting connection 'virbr0' (199366dc-6cd8-4b35-bdb2-717580b11966)
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5916] device (virbr0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5920] device (virbr0): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5923] device (virbr0): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5925] device (virbr0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5952] device (virbr0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5954] device (virbr0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5958] manager: NetworkManager state is now CONNECTED_LOCAL
Jun 09 07:31:12 ms7640 NetworkManager[853]: <info>  [1717936272.5962] device (virbr0): Activation: successful, device activated.
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5736] device (enp2s0): carrier: link connected
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5740] device (enp2s0): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5749] policy: auto-activating connection 'Wired connection 1' (eeeff969-ca0b-3313-99dd-179dd8c62e73)
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5756] device (enp2s0): Activation: starting connection 'Wired connection 1' (eeeff969-ca0b-3313-99dd-179dd8c62e73)
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5758] device (enp2s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5762] manager: NetworkManager state is now CONNECTING
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5764] device (enp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5772] device (enp2s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:14 ms7640 NetworkManager[853]: <info>  [1717936274.5775] dhcp4 (enp2s0): activation: beginning transaction (timeout in 45 seconds)
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5879] dhcp4 (enp2s0): state changed new lease, address=192.168.0.115
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5907] device (enp2s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5936] device (enp2s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5939] device (enp2s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5945] manager: NetworkManager state is now CONNECTED_LOCAL
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5951] manager: NetworkManager state is now CONNECTED_SITE
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5953] policy: set 'Wired connection 1' (enp2s0) as default for IPv4 routing and DNS
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5963] device (enp2s0): Activation: successful, device activated.
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5969] manager: NetworkManager state is now CONNECTED_GLOBAL
Jun 09 07:31:16 ms7640 NetworkManager[853]: <info>  [1717936276.5976] manager: startup complete
Jun 09 07:31:23 ms7640 NetworkManager[853]: <info>  [1717936283.1491] agent-manager: agent[d0f6135805d5b40f,:1.64/org.kde.plasma.networkmanagement/1000]: agent registered
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4638] caught SIGTERM, shutting down normally.
Jun 09 07:36:36 ms7640 systemd[1]: Stopping Network Manager...
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4767] dhcp4 (enp2s0): canceled DHCP transaction
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4767] dhcp4 (enp2s0): activation: beginning transaction (timeout in 45 seconds)
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4768] dhcp4 (enp2s0): state changed no lease
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4772] manager: NetworkManager state is now CONNECTED_SITE
Jun 09 07:36:36 ms7640 NetworkManager[853]: <info>  [1717936596.4836] exiting (success)
Jun 09 07:36:36 ms7640 systemd[1]: NetworkManager.service: Deactivated successfully.
Jun 09 07:36:36 ms7640 systemd[1]: Stopped Network Manager.


```

Tried this also ... modify /etc/netplan/01-network-manager-all.yaml
added "ethernets";

```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp2s0:
      dhcp4: true

```

And got this ....

```

ms7640:~$ sudo netplan apply

** (generate:2837): WARNING **: 17:52:09.109: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

** (process:2835): WARNING **: 17:52:09.462: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

** (process:2835): WARNING **: 17:52:09.688: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

** (process:2835): WARNING **: 17:52:09.688: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
Failed to start NetworkManager.service: Unit NetworkManager.service not found.
Traceback (most recent call last):
  File "/usr/sbin/netplan", line 23, in <module>
    netplan.main()
  File "/usr/share/netplan/netplan/cli/core.py", line 56, in main
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 243, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 63, in run
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 243, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 294, in command_apply
    utils.systemctl_network_manager('start', sync=sync)
  File "/usr/share/netplan/netplan/cli/utils.py", line 87, in systemctl_network_manager
    return systemctl(action, [NM_SERVICE_NAME], sync)  # pragma: nocover (covered in autopkgtest)
  File "/usr/share/netplan/netplan/cli/utils.py", line 99, in systemctl
    subprocess.check_call(command)
  File "/usr/lib/python3.10/subprocess.py", line 369, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'start', '--no-block', 'NetworkManager.service']' returned non-zero exit status 5.


```

I even followed the instructions [https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/]("https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/") under Enable Systemd. Got same Error as above.

Any real suggestions? Can it be repaired with the installation file on USB stick?

---

### Post by Rick St. George on 2024-06-11
Don't know what I did, but its working now. Maybe it was after a ReBoot the next morning. 
Don't have a GUI for Network anymore - miss that! But at least I have internet.

---

