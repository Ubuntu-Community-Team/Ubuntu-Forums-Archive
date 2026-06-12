---
title: "systemd.link file does not change ethernet adapter name"
date: 2018-08-10
forum: Networking &amp; Wireless
---

### Post by jesse-kaukonen on 2018-08-10
Ubuntu 18.04.1, server version
kernel: 4.15.18 built from git://kernel.ubuntu.com/ubuntu/ubuntu-bionic.git, with i915 disabled due to hardware problems with the SOC ([https://bugs.freedesktop.org/show_bug.cgi?id=106721](https://bugs.freedesktop.org/show_bug.cgi?id=106721))
Latest updates installed

I'm attempting to set up a predictable device name for a USB 4G ethernet adapter. The scenario is that I'm making a SOC device which will be cloned on multiple identical SOC devices, and each of them will get their own USB ethernet adapter. These adapters have varying firmwares and builds, and I have to be absolutely certain they are properly configured using DHCP. To do this, I'm adding rules in /etc/netplan/ like so

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: yes
    enp0s20u1:
      dhcp4: yes
    enp0s20u2:
      dhcp4: yes
    enp0s20u3:
      dhcp4: yes
    enp0s20u4:
      dhcp4: yes
    enp0s20u7u1:
      dhcp4: yes
```

The problem is that I can't be 100% certain the device names will always be this format (this format is based on location, most likely USB port). I'd much prefer to name the devices based on the used driver, so they are: cdc_ether_zte0, cdc_ether_zte1, etc. For this, I set up a systemd.link ([https://www.freedesktop.org/software/systemd/man/systemd.link.html](https://www.freedesktop.org/software/systemd/man/systemd.link.html)) file that sets the name, but the names refuse to change on reboot, or they change to usb0 for whatever reason.

```

root@hostname:~# cat /etc/systemd/network/10-zte.link
[Match]
Driver=cdc_ether,rndis_host

[Link]
Name=cdc_ether_zte0
```


```
root@hostname:~# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0424:2530 Standard Microsystems Corp.
Bus 001 Device 003: ID 19d2:1405 ZTE WCDMA Technologies MSM
Bus 001 Device 002: ID 0424:4603 Standard Microsystems Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
root@hostname:~# udevadm test-builtin net_setup_link /dev/bus/usb/001/003
calling: test-builtin
Load module index
Parsed configuration file /lib/systemd/network/99-default.link
Parsed configuration file /etc/systemd/network/10-zte.link
Created link configuration context.
unable to open device '/sys/dev/bus/usb/001/003'

Unload module index
Unloaded link configuration context.
```


```
root@hostname:~# file /dev/bus/usb/001/003
/dev/bus/usb/001/003: character special (189/2)
```

```

root@hostname:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:07:32:4e:59:f2 brd ff:ff:ff:ff:ff:ff
3: enp0s20u7u1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 56:a4:92:34:2c:67 brd ff:ff:ff:ff:ff:ff
```


```
root@hostname:~# lshw

  <-- snip-->

  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 56:a4:92:34:2c:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=ZTE CDC Ethernet Device link=no multicast=yes
```


If boot with: GRUB_CMDLINE_LINUX="net.ifnames=0 console=tty0 console=ttyS0,115200n8"

```
root@hostname:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:07:32:4e:59:f2 brd ff:ff:ff:ff:ff:ff
3: usb0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 56:a4:92:34:2c:67 brd ff:ff:ff:ff:ff:ff
```

The systemd.link documentation says:

```

NamePolicy=
    An ordered, space-separated list of policies by which the interface name should be set. "NamePolicy" may be disabled by specifying "net.ifnames=0" on the kernel command line.

<-- snip -->

Name
    The interface name to use in case all the policies specified in NamePolicy= fail, or in case NamePolicy= is missing or disabled.

```


Edit: If I figured out how to disable / remove netplan, I could simply get this done by using systemd-networkd, by writing:

```

root@hostname:~# cat /etc/systemd/network/12-dhcp.network 
[Match]
Name=en*

[Network]
DHCP=yes

```

However I'm not sure how to get rid of netplan.

Edit 2: It seems Ubuntu isn't launching systemd-networkd.service. I manually executed systemctl enable systemd-network.service & rebooted, but still can't see the interfaces changing names. I also verified the link file isn't being used for the adapter:

```

root@hostname:~# networkctl status enp0s20u7u1
&#9679; 3: enp0s20u7u1
       Link File: /lib/systemd/network/99-default.link
    Network File: n/a
            Type: ether
           State: off (unmanaged)
            Path: pci-0000:00:14.0-usb-0:7.1:1.0
          Driver: cdc_ether
          Vendor: ZTE WCDMA Technologies MSM
           Model: ZTE_Technologies_MSM
      HW Address: 56:a4:92:34:2c:67


root@hostname:~# dmesg |grep -i renamed
[    4.780593] r8169 0000:01:00.0 enp1s0: renamed from eth0
[    9.740242] cdc_ether 1-7.1:1.0 enp0s20u7u1: renamed from usb0



```

---

### Post by jesse-kaukonen on 2018-08-10
I did two mistakes: I used the wrong path for my udevadm tests, and the Driver section of a Match rule must be separated by whitespace, not comma. So:

```

root@hostname:~# cat /etc/systemd/network/10-zte.link 
[Match]
Driver=cdc_ether rndis_host

[Link]
Name=cdc_ether_zte0

root@hostname:~# udevadm test-builtin net_setup_link /sys/class/net/enp0s20u7u1/
calling: test-builtin
Load module index
Parsed configuration file /lib/systemd/network/99-default.link
Parsed configuration file /etc/systemd/network/10-zte.link
Created link configuration context.
ID_NET_DRIVER=cdc_ether
Config file /etc/systemd/network/10-zte.link applies to device enp0s20u7u1
link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
ID_NET_LINK_FILE=/etc/systemd/network/10-zte.link
Unload module index
Unloaded link configuration context.

```

However, renaming still doesn't happen.

EDIT 3: And it's solved I had to execute:

```

update-initramfs -k all -c

```

Thanks for the help!

---

