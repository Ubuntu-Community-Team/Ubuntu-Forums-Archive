---
title: "network-manager-1.10.6-2ubuntu1.1 quit working"
date: 2019-09-28
forum: Networking &amp; Wireless
---

### Post by r_widell on 2019-09-28
```
$ cat /etc/issue
Ubuntu 18.04.3 LTS \n \l
```
```
$ uname -r
4.15.0-64-generic
```
```
$ apt show network-manager
Package: network-manager
Version: 1.10.6-2ubuntu1.1
Priority: optional
Section: net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 5,927 kB
Depends: libaudit1 (>= 1:2.2.1), libbluetooth3 (>= 4.91), libc6 (>= 2.25), libcurl3-gnutls (>= 7.16.3), libglib2.0-0 (>= 2.43.2), libgnutls30 (>= 3.5.0), libjansson4 (>= 2.0.1), libmm-glib0 (>= 1.0.0), libndp0 (>= 1.2), libnewt0.52, libnl-3-200 (>= 3.2.21), libnm0 (>= 1.10.2), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.104), libpsl5 (>= 0.13.0), libreadline7 (>= 6.0), libselinux1 (>= 1.32), libsystemd0 (>= 221), libteamdctl0 (>= 1.9), libudev1 (>= 183), libuuid1 (>= 2.16), lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, adduser, isc-dhcp-client (>= 4.1.1-P1-4), libpam-systemd, policykit-1
Recommends: ppp, dnsmasq-base, iptables, modemmanager, network-manager-pptp, crda, iputils-arping
Suggests: avahi-autoipd, libteam-utils
Breaks: ppp (>= 2.4.7-3~), ppp (<< 2.4.7-2+~)
Homepage: https://wiki.gnome.org/Projects/NetworkManager
Task: ubuntu-desktop, kubuntu-desktop, kubuntu-full, xubuntu-core, xubuntu-desktop, lubuntu-gtk-desktop, lubuntu-desktop, lubuntu-qt-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 5y
Download-Size: 1,500 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * dnsmasq-base/iptables: Required for creating Ad-hoc connections and
    connection sharing.
  * libteam-utils: Network Team driver allows multiple network interfaces to be
    teamed together and act like a single one. This process is called "ethernet
    bonding", "channel teaming" or "link aggregation".

N: There is 1 additional record. Please use the '-a' switch to see it
```

Last weekend I rebooted this machine due to a kernel version upgrade.
When it came back up, Network-Manager would not configure the GigE NIC.
I tried rebooting to the previous kernel, but no joy. I primarily use this for file serving, and I had other, higher priority tasks so I just left it alone and used "sneaker net" for a few days.

When I finally got around to investigating, I tried booting a live image to ensure that the hardware hadn't failed, it hadn't. The network was working fine when running the live system.

So I rebooted the system and started looking at the logs. The networking target simply started Network-Manager and exited. So I set a static IP address and netmask to the NIC and was able to connect to my local network, but since I hadn't told it where the gateway was, it couldn't connect to the internet proper. I then issued ```
#ifdown <iface>; ifup <iface>; dhclient <iface>
``` and it could now also connect to the internet.

In both cases (static/dynamic IP address/netmask), Network manager recognized that the NIC was now active and quit throwing error messages, but I still couldn't establish a VPN connection over that link via Network-Manager (and I haven't tried connecting manually).

According to /var/log/apt/history.log the only recent update that has anything to do with networking is wpasupplicant, but this machine has no wireless (wi-fi/cellular/bluetooth) NIC so I'm not sure how that should have an impact.

Curiously, my HTPC, which is running SolydK 9, had the same issue occur at around the same time. But yet another Ubuntu-18.04.3LTS machine has not had that issue occur.

The machine which doesn't work was upgraded from previous LTS releases (10.04 IIRC), while the one that still works was installed from 18.04.1LTS media. They are both running the KDE desktop via ```
#apt-get install kubuntu-desktop
``` and the one that works has also had the HWE stack installed, while the one that doesn't is running without the HWE stack.

Is it possible that the newer kernel, etc. in the HWE stack is why Network=Manager works on one machine and not the other?

What else could be causing this behavior?

Thanks,
ron

---

### Post by r_widell on 2019-10-01
In the sincere hope that someone can tell me why Network-manager quit working and (preferably) get it working again I'm attaching a couple of files. One is history.log from /var/log/apt. The other is a file I created via: ```
#journalctl --no-pager | grep -A 5 -B 5 -n enp0s10 - > enp0s10.log
```
If there's any other info I need to provide, please let me know.

Oops. The enp0s10.log is too big, even when gzipped. I know that there's a location for uploading large files, but I can't remember where it is and my (admittedly rudimentary) search through the forum didn't yield the location. Would someone point me to it?

Thanks,
ron

---

### Post by r_widell on 2019-10-03
It appears that if you have Network-Manager configured to automatically initiate an openVPN connection when a physical connection is established (which I did) AND the openVPN can't be established, THEN Network-Manager will tear down the connection on the underlying physical interface, as well.

I had set my vpn service to automatically renew through @PayPal, which worked fine for a couple of years, until this year. This year @PayPal chose not to honor the automatic renewal, so my vpn service expired on 18 September, without notification from either @PayPal or my VPN service.

When I manually paid for another year of vpn service, the vpn connection configured in Network-Manager would sucessfully connect and Network-Manager would keep the underlying physical connection alive. There may have been error messages posted in one of the logs, but I was unable to find them.

So this is a cautionary tale for anyone trying to automatically connect to a vpn through Network-Manager.

ron

---

