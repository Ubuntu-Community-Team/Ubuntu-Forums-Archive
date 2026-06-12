---
title: "Can't delete wired connection"
date: 2020-10-12
forum: Networking &amp; Wireless
---

### Post by py-ohayo on 2020-10-12
Hello,

I am facing a strange problem: I cannot remove a wired connection.
Every time I restart the system, this connection reappears.
On the screenshot below, there is the connection with the IP **169.254.8.32** which is not removable.
[https://i.postimg.cc/1zb2qpqj/Screenshot-from-2020-10-12-19-24-08.png](https://i.postimg.cc/1zb2qpqj/Screenshot-from-2020-10-12-19-24-08.png)

What should I check to remove it definitely ?
Another oddity (probably related to this issue): Ubuntu boot time has become very long - at least 3 min.

Thanks in advance.

---

### Post by praseodym on 2020-10-13
Please show
```

cat /etc/network/interfaces
ifconfig -a
route -n
cat /etc/resolv.conf
```

---

### Post by ajgreeny on 2020-10-13
Is that ethernet connection no longer available?
Do you have an ethernet connection of any kind?
Do you have a wireless connection?
Why do you want to remove the ethernet connection?

The long boot time may well be related to a network problem but let's see the terminal output of ***systemd-analyze blame***
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
Also, please do not add large images in your posts; use the attachment facility by clicking on the paperclip icon in the toolbar of the "Reply to thread" text entry window.

---

### Post by py-ohayo on 2020-10-14
```
pavel@ALABAMA:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto enp8s0
iface enp8s0 inet dhcp
pavel@ALABAMA:~$ ifconfig -a
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:c9:03:30:25  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp8s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 8c:16:45:a9:fe:44  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp8s0:avahi: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 169.254.8.232  netmask 255.255.0.0  broadcast 169.254.255.255
        ether 8c:16:45:a9:fe:44  txqueuelen 1000  (Ethernet)

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16617  bytes 1751279 (1.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16617  bytes 1751279 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.252  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2001:171b:227c:8320:bdfd:2047:6cd3:8090  prefixlen 128  scopeid 0x0<global>
        inet6 2001:171b:227c:8320:31a6:a75:a1d1:ec54  prefixlen 64  scopeid 0x0<global>
        inet6 fdaa:bbcc:ddee:0:31a6:a75:a1d1:ec54  prefixlen 64  scopeid 0x0<global>
        inet6 fdaa:bbcc:ddee:0:1ffd:69b9:6949:cc83  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::66f8:f168:baa9:3769  prefixlen 64  scopeid 0x20<link>
        inet6 2001:171b:227c:8320:e3e5:53c7:9824:b200  prefixlen 64  scopeid 0x0<global>
        ether 14:4f:8a:ac:fb:66  txqueuelen 1000  (Ethernet)
        RX packets 21541284  bytes 32103797704 (32.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8251916  bytes 922103289 (922.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

```
pavel@ALABAMA:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp7s0
0.0.0.0         0.0.0.0         0.0.0.0         U     1002   0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 enp8s0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp7s0
pavel@ALABAMA:~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0
search home
pavel@ALABAMA:~$
```

---

### Post by py-ohayo on 2020-10-14
> **ajgreeny said:**
> Is that ethernet connection no longer available?
Do you have an ethernet connection of any kind?
Do you have a wireless connection?
Why do you want to remove the ethernet connection?

The long boot time may well be related to a network problem but let's see the terminal output of ***systemd-analyze blame***
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
Also, please do not add large images in your posts; use the attachment facility by clicking on the paperclip icon in the toolbar of the "Reply to thread" text entry window.

[COLOR=#0000ff]*Is that ethernet connection no longer available?*[/COLOR]
It becomes available when I connect external device over Ethernet cable.

[COLOR=#0000ff]*Do you have an ethernet connection of any kind?*[/COLOR]
No, I use Ethernet to communicate with external board.
[COLOR=#0000ff][I]
Do you have a wireless connection?[/I][/COLOR]
Yes

[COLOR=#0000ff]*Why do you want to remove the ethernet connection?*[/COLOR]
Actually there are 2 ethernet connections with different IPs. That I want to delete masks other which is useful.

The long boot time may well be related to a network problem but let's see the terminal output of [B][I]systemd-analyze blame
[/I][/B]```
pavel@ALABAMA:~$ systemd-analyze blame
     5min 1.592s networking.service
    2min 59.025s apt-daily-upgrade.service
         55.566s apt-daily.service
         20.909s plymouth-quit-wait.service
          6.476s NetworkManager-wait-online.service
          3.010s snapd.service
          1.311s snap-gnome\x2dcalculator-748.mount
          1.267s snap-gnome\x2dlogs-93.mount
          1.252s snap-gnome\x2d3\x2d26\x2d1604-100.mount
          1.237s snap-core18-1880.mount
          1.122s snap-gnome\x2d3\x2d34\x2d1804-36.mount
          1.075s snap-gnome\x2d3\x2d28\x2d1804-128.mount
          1.048s dev-loop3.device
          1.042s snap-gtk\x2dcommon\x2dthemes-1506.mount
          1.012s snap-gnome\x2dlogs-100.mount
           998ms nvidia-persistenced.service
           976ms dev-loop4.device
           965ms snap-inkscape-7947.mount
           961ms snap-gnome\x2dsystem\x2dmonitor-145.mount
           948ms dev-loop5.device
           946ms dev-loop6.device
           925ms dev-nvme0n1p1.device
           839ms dev-loop8.device
           769ms systemd-rfkill.service
           768ms dev-loop10.device
           724ms dev-loop9.device
           684ms docker.service
           628ms dev-loop15.device
           628ms dev-loop1.device
           546ms apparmor.service
           542ms snap-gnome\x2d3\x2d26\x2d1604-98.mount
           522ms dev-loop0.device
           506ms dev-loop12.device
           505ms dev-loop16.device
           503ms dev-loop11.device
           444ms snap-gnome\x2dcharacters-550.mount
           438ms snap-gnome\x2dcharacters-570.mount
           436ms dev-loop21.device
           436ms dev-loop2.device
           418ms dev-loop14.device
           409ms dev-loop17.device
           401ms snap-gnome\x2dsystem\x2dmonitor-148.mount
           389ms dev-loop13.device
           378ms dev-loop18.device
           372ms dev-loop19.device
           353ms gpu-manager.service
           343ms snap-core-9993.mount
           341ms snap-gtk\x2dcommon\x2dthemes-1502.mount
           338ms snap-gnome\x2d3\x2d28\x2d1804-145.mount
           324ms snap-gnome\x2dcalculator-826.mount
           319ms dev-loop20.device
           273ms systemd-journal-flush.service
           248ms NetworkManager.service
           229ms containerd.service
           228ms upower.service
           225ms apport.service
           176ms systemd-udev-trigger.service
           168ms networkd-dispatcher.service
           166ms pppd-dns.service
           161ms udisks2.service
           142ms snap-core18-1885.mount
           140ms ModemManager.service
           124ms systemd-journald.service
           120ms speech-dispatcher.service
           114ms systemd-logind.service
           114ms snap-gnome\x2d3\x2d34\x2d1804-60.mount
           114ms grub-common.service
           100ms swapfile.swap
           100ms thermald.service
            99ms avahi-daemon.service
            96ms smbd.service
            82ms dns-clean.service
            77ms lm-sensors.service
            75ms nmbd.service
            75ms keyboard-setup.service
            75ms packagekit.service
            70ms systemd-timesyncd.service
            65ms snapd.apparmor.service
            62ms plymouth-start.service
            62ms accounts-daemon.service
            62ms user@1000.service
            61ms snap-core-10126.mount
            58ms systemd-modules-load.service
            52ms binfmt-support.service
            44ms wpa_supplicant.service
            44ms systemd-udevd.service
            42ms bolt.service
            39ms systemd-tmpfiles-clean.service
            39ms systemd-resolved.service
            38ms hddtemp.service
            37ms rsyslog.service
            33ms gdm.service
            31ms console-setup.service
            31ms plymouth-read-write.service
            29ms motd-news.service
            26ms kerneloops.service
            25ms snapd.seeded.service
            21ms systemd-tmpfiles-setup.service
            21ms systemd-update-utmp.service
            20ms systemd-remount-fs.service
            19ms systemd-user-sessions.service
            19ms systemd-backlight@backlight:intel_backlight.service
            19ms polkit.service
            18ms colord.service
            15ms dev-mqueue.mount
            15ms kmod-static-nodes.service
            15ms ufw.service
            14ms bluetooth.service
            13ms systemd-tmpfiles-setup-dev.service
            10ms dev-hugepages.mount
            10ms systemd-update-utmp-runlevel.service
             9ms ureadahead-stop.service
             8ms proc-sys-fs-binfmt_misc.mount
             7ms systemd-sysctl.service
             7ms sys-kernel-debug.mount
             4ms rtkit-daemon.service
             4ms systemd-random-seed.service
             4ms setvtrgb.service
             3ms snapd.socket
             3ms sys-kernel-config.mount
             2ms sys-fs-fuse-connections.mount
             2ms docker.socket
lines 100-122/122 (END)

```

[COLOR=#0000ff]*Also, please do not add large images in your posts; use the attachment  facility by clicking on the paperclip icon in the toolbar of the "Reply  to thread" text entry window.*[/COLOR]
Ok

---

### Post by py-ohayo on 2020-10-16
Recently I also discovered the problem with wireless: the connection is frequently lost while on the Windows PC, connected to the same router, there is no loss of connection.
Is there a way to fix whole this network staff ?

---

### Post by praseodym on 2020-10-16
```
auto lo
iface lo inet loopback
[COLOR="#FF0000"]auto enp8s0
iface enp8s0 inet dhcp[/COLOR]
```
Delete these two lines via
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot

---

### Post by py-ohayo on 2020-10-16
Thanks !
The issue with long boot disappeared.
The instability of wireless persists.

---

