---
title: "too many network login retries at startup - lubuntu 12.04"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by joserodgt on 2017-05-15
Every time i startup the computer, lightdm login shows up, the first few times I try to login to linux server it wont login and no error message displayed just prompts again for credentials. I have to wait 2 to 3 minutes for the login to be successful.
```
Cheking the log (var/log/auth.log) i can see that on the failed attempts, lightdm fails to send the user to the server:
lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=
while waiting 2 or 3 minutes, on the succesful login, the user is passed on the call:
pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "v.jimenez"
pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=v.jimenez

```
It is annoying  waiting for almost 4 minutes to login to the network for the lightdm login to work.

Anyone have an idea what is going on?

thanks

---

### Post by TheFu on 2017-05-16
Support for 12.04 ended last month.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)   12.04 is end-of-life.

I see the same "authentication failure" here on a 16.04 machine, but it still logs in quickly.  I don't think those messages are relevant.  There is a way to get a graph of everything run at boot. Don't remember the tool name that does it, but google should find it quickly.  

On 16.04, **systemd-analyze blame** is the tool.
```
$ systemd-analyze blame
          9.472s networking.service
          1.824s wicd.service
          1.412s ModemManager.service
          1.397s accounts-daemon.service
          1.378s apport.service
          1.360s rsyslog.service
          1.339s grub-common.service
          1.331s irqbalance.service
          1.203s lightdm.service
          1.152s polkitd.service
           739ms dev-mapper-ubuntu\x2d\x2dmate\x2d\x2dvg\x2droot.device
           529ms fail2ban.service
           499ms apt-daily.service
           489ms postfix.service
           480ms lvm2-monitor.service
           265ms libvirt-bin.service
           229ms ufw.service
           217ms systemd-logind.service
           213ms autofs.service
           156ms ondemand.service
           152ms sysstat.service
           147ms apparmor.service
           141ms speech-dispatcher.service
           141ms keyboard-setup.service
           133ms atop.service
           131ms ntp.service
           118ms qemu-kvm.service
            99ms systemd-journald.service
            98ms glances.service
            89ms console-setup.service
            85ms systemd-user-sessions.service
            84ms systemd-modules-load.service
            81ms gpu-manager.service
            71ms run-rpc_pipefs.mount
            70ms upower.service
            69ms systemd-udev-trigger.service
            68ms hddtemp.service
            63ms udisks2.service
            63ms binfmt-support.service
            59ms alsa-restore.service
            57ms ebtables.service
            56ms pppd-dns.service
            53ms systemd-tmpfiles-setup.service
            42ms systemd-journal-flush.service
            41ms systemd-tmpfiles-setup-dev.service
            40ms lm-sensors.service
            38ms snapd.autoimport.service
            32ms systemd-udevd.service
            29ms inetutils-inetd.service
            29ms systemd-tmpfiles-clean.service
            25ms resolvconf.service
            23ms ssh.service
            23ms openvpn.service
            21ms [email]user@1000.servic[/email]e
            21ms plymouth-start.service
            21ms samba-ad-dc.service
            19ms atftpd.service
            18ms systemd-rfkill.service
            17ms systemd-update-utmp.service
            17ms systemd-sysctl.service
            17ms snapd.socket
            16ms kmod-static-nodes.service
            16ms plymouth-read-write.service
            16ms rpc-statd.service
            16ms sys-fs-fuse-connections.mount
            15ms netfilter-persistent.service
            14ms dev-hugepages.mount
            14ms systemd-fsck@dev-disk-by\x2duuid-a5a832c2\x2dde80\x2d4301\x2d93
            13ms dev-mqueue.mount
            13ms rc-local.service
            12ms systemd-remount-fs.service
            10ms dev-mapper-ubuntu\x2d\x2dmate\x2d\x2dvg\x2dswap_1.swap
             8ms proc-sys-fs-binfmt_misc.mount
             8ms boot.mount
             8ms libvirt-guests.service
             7ms nfs-config.service
             6ms systemd-random-seed.service
             6ms setvtrgb.service
             6ms ureadahead-stop.service
             6ms sys-kernel-debug.mount
             6ms systemd-update-utmp-runlevel.service
             6ms rtkit-daemon.service
             5ms rpcbind.service
             4ms rpc-statd-notify.service
             3ms plymouth-quit-wait.service
             3ms [email]systemd-cryptsetup@sda5_crypt.servic[/email]e
             2ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
```
Sorted by where the time is used.

Sorry, can't help for 12.04.

---

