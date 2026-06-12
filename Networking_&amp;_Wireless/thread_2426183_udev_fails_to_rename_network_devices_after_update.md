---
title: "udev fails to rename network devices after update"
date: 2019-09-05
forum: Networking &amp; Wireless
---

### Post by geek-n on 2019-09-05
Today I saw there was a set of updates so I installed them and it required a reboot. After the reboot came up, I had no networking on either of two interfaces. A second reboot didn't help.

From syslog it appears udev can no longer rename eth0 and eth1 according to the MAC addresses. It may have something to do with incompatible systemd changes, resulting in a loss of functionality so that one can no longer rename network devices to names that the kernel would otherwise assign.

Sep  5 13:51:32 server systemd-udevd[552]: Error changing net interface name 'eth0' to 'eth1': File exists
Sep  5 13:51:32 server systemd-udevd[552]: could not rename interface '2' from 'eth0' to 'eth1': File exists

If I change the names to something besides eth*, it works, but I'm going to have to go through /etc and other places and hopefully not miss any references to eth0 and eth1. I hate to think what might happen to people attempting to upgrade headless servers. This is not good. I wanted them to remain eth0 and eth1 as I've done for the last 15 years.

root@server:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"

root@server:~# uname -a
Linux server 4.15.0-60-generic #67-Ubuntu SMP Thu Aug 22 16:55:30 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by k-markus on 2019-09-09
I'm experiencing the same issue on all my newly installed Ubuntu 18.04 machines since 2-3 weeks back.


This is my setup on how to rename the network interfaces.


```
$ cat /etc/default/grub
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet net.ifnames=0"
...

```

```
$ cat /etc/udev/rules.d/10-network.rules
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="c8:d9:d2:0d:50:2c", NAME="eth1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="68:05:ca:9d:ee:73", NAME="eth0"

```

Some info about how the networking is setup.

```
$ cat /etc/netplan/01-network-manager-all.yaml 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

```
$ cat /etc/network/interfaces
auto lo eth0 eth1 
iface lo inet loopback


iface eth1 inet dhcp
    wpa-driver wired
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf


iface eth0 inet static
    address 192.168.0.1
    netmask 255.255.255.0

```

As [COLOR=#000000]geek-n mentions, this has been working for a long time.[/COLOR]

---

### Post by k-markus on 2019-09-10
Bug report [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1842651](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1842651)

---

### Post by k-markus on 2019-09-10
The new version of systemd ([COLOR=#333333][FONT=monospace]237-3ubuntu10.29) fixed it for me.

[/FONT][/COLOR]systemd (237-3ubuntu10.29) bionic; urgency=medium


  * d/p/d/Revert-udev-network-device-renaming-immediately-give.patch:
    - udev: add Revert-udev-network-device-renaming-immediately-give.patch back
      Dropping this patch will cause the persistent network regression.
      (LP: #1842651)


 -- Shih-Yuan Lee (FourDollars) <sylee@canonical.com> Thu, 05 Sep 2019 11:59:51 +0800

---

