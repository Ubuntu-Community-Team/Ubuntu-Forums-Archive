---
title: "nameserver problems"
date: 2018-11-27
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-11-27
I just learned that a problem I have been having, literally, for a couple of years is due to the nameserver.  I solved the problem by changing the nameserver, in /etc/resolv.conf to nameserver 8.8.8.8 (google)  I think this is a temporary solution.  I then started to study on this and found that there seems to be, again literally, hundreds of solutions.  So, this is to request which solution is best for 18.04 so I can fix my systems so that my network no longer hangs forever whilst telling me everything is dandy.

Thank you...............

---

### Post by mitesh.agrwl on 2018-11-28
> **jgw said:**
> I just learned that a problem I have been having, literally, for a couple of years is due to the nameserver.  I solved the problem by changing the nameserver, in /etc/resolv.conf to nameserver 8.8.8.8 (google)  I think this is a temporary solution.  I then started to study on this and found that there seems to be, again literally, hundreds of solutions.  So, this is to request which solution is best for 18.04 so I can fix my systems so that my network no longer hangs forever whilst telling me everything is dandy.

Thank you...............

Check the nameserver supplied by DHCP using command

```
$ nmcli device show wlx1c4bd6ded3b | IP4
```

If it is same as that of Default gateway, you may need to add additional DNS server (nameserver) using network manager gui or cli. Add Open DNS, Google DNS or any other of your choice.

---

### Post by jgw on 2018-11-28
Thanks for the reply - here are the results of your suggestion:

```

greg@movies:~$ nmcli device show wlx1c4bd6ded3b | IP4
Error: Device 'wlx1c4bd6ded3b' not found.
IP4: command not found

```

however

```

greg@movies:~$ nmcli device show wlx008736326fa1
GENERAL.DEVICE:                         wlx008736326fa1
GENERAL.TYPE:                           wifi
GENERAL.HWADDR:                         00:87:36:32:6F:A1
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     CenturyLink1840_EXT 1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveCo
IP4.ADDRESS[1]:                         192.168.0.48/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt =
IP4.ROUTE[3]:                           dst = 199.115.103.10/32, nh = 192.168.0.
IP4.DNS[1]:                             192.168.0.43
IP4.DOMAIN[1]:                          Home
IP6.GATEWAY:                            --
lines 1-15/15 (END)

```

---

### Post by mitesh.agrwl on 2018-11-28
Please post the output of 

```
$ ip a
sudo lshw -class network 

```

---

### Post by jgw on 2018-11-28
I just had to change my nameserver from 127.0.0.53 to 8.8.8.8 to keep going (edited /etc/resolv.conf)

```

greg@movies:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 40:8d:5c:4d:8d:8e brd ff:ff:ff:ff:ff:ff
3: wlx008736326fa1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:87:36:32:6f:a1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.48/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx008736326fa1
       valid_lft 85640sec preferred_lft 85640sec
18: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.93.10.6 peer 10.93.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever
greg@movies:~$ 
greg@movies:~$ sudo lshw -class network
[sudo] password for greg: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:4d:8d:8e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:35 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx008736326fa1
       serial: 00:87:36:32:6f:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=4.15.0-39-generic firmware=N/A ip=192.168.0.48 link=yes multicast=yes wireless=IEEE 802.11
greg@movies:~$ 

```

---

### Post by jgw on 2018-11-28
I suspect I should also add that I am using PIA as my VPN.  I know its up but my settings seems to have no idea.  I have no idea how this works out when dealing with the nameserver but it may have something to do with this

---

### Post by mitesh.agrwl on 2018-11-29
> **jgw said:**
> Thanks for the reply - here are the results of your suggestion:

```

greg@movies:~$ nmcli device show wlx1c4bd6ded3b | IP4
Error: Device 'wlx1c4bd6ded3b' not found.
IP4: command not found

```

however

```

greg@movies:~$ nmcli device show wlx008736326fa1
GENERAL.DEVICE:                         wlx008736326fa1
GENERAL.TYPE:                           wifi
GENERAL.HWADDR:                         00:87:36:32:6F:A1
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     CenturyLink1840_EXT 1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveCo
IP4.ADDRESS[1]:                         192.168.0.48/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt =
IP4.ROUTE[3]:                           dst = 199.115.103.10/32, nh = 192.168.0.
IP4.DNS[1]:                             192.168.0.43
IP4.DOMAIN[1]:                          Home
IP6.GATEWAY:                            --
lines 1-15/15 (END)

```

Please avoid editing after a reply! It becomes hard to keep the track! the DNS server is not the expected one, it is private IP within the LAN. Does your ISP assign Private IP and have a DNS server in its network? Your routing table is little messed up here, the output shown above is not expected.

Please post the output of [CODE]$ ip route [CODE]

---

### Post by SeijiSensei on 2018-11-29
Ons solution is to edit /etc/resolvconf/resolv.conf.d/head (as root with sudo) and add

```
 nameserver 8.8.8.8
```

When you reboot, that record will appear above the 127.0.0.3 entry.

You can add other directives to this file as well like "search example.com" to handle "unqualified" hostnames.

---

### Post by jgw on 2018-11-29
Thanks for the reply.

I know about changing the nameserver but that is not permanent and dns will eventually change it.  What I am trying to get is a permanent solution.  If you google something like "ubuntu 18.04 nameserver fix" you will get hundreds of answers starting around 2016.  Here is one that might be of interest: [https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)    My problem is that there are many that might be of interest and I was hoping that somebody would tell me which one is current and fixes the problem.

---

### Post by jgw on 2018-11-29
I actually tried [https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/) and it seemed to work so far.  That being the case I am going to mark this one as solved!

I was wrong and this fixed nothing and this is NOT SOLVED!

---

### Post by jgw on 2018-11-29
the problem with this one is that, on my machine, there is no "/resolv.conf.d/head"

I find this all very strange.  I just finished looking over posts about this problem and, as far as I can tell there are NO fixes that actually work and everybody seems to have to mess with resolv.conf everytime they reboot and they reboot everytime the connection fails.

---

### Post by SeijiSensei on 2018-11-30
Yes, another solution that Ubuntu in its wisdom has removed from the distribution.

The simplest solution is to either remove or rename the symlink from /etc/resolv.conf to ../run/systemd/resolve/stub-resolv.conf.  Then build a static resolv.conf of your own.

```

cd /etc
sudo mv resolv.conf resolv.old
sudo nano resolv.conf

```

The other methods described in "[man systemd-resolved.service]("http://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html")" seem unnecessarily confusing.  I just blitz the /etc/resolv.conf link and create my own file with static "search" and "nameserver" records.

---

### Post by jgw on 2018-11-30
I deleted my resolv.conf to see what would happen and re-booted.  The system created a new one with 127.0.0.1 which is inaccessible.  I wonder why them that code don't have their software checking if something works before doing something like that.  I will try your thought and see what happens.  I have no idea how to "build a static resolv.conf" as I don't know any more than what I already have in my existing, ie:

```

nameserver ::1
nameserver  127.0.0.1  (soon to be 8.8.8.8)

../run/systemd/resolve/resolv.conf has:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888

../run/systemd/resolve/stub_resolv.conf has:
nameserver 127.0.0.53
which is inaccessable

```

I just tried to ping:
greg@greg-down:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.5 icmp_seq=1 Destination Host Unreachable

An interesting aside is that 192.168.0.5 is the address of my router

I then restarted network-manager (no cigar)
then I checked my wired connection and that didn't exist
then I brought up my wi-fi and that one actually worked
I suspect that my network-manager restart actually started working (who knows?)

None of this makes any sense to me at all.  I have also noticed that this stuff was happening in 17 too. one would think somebody would just fix it but I guess that's more wishful thinking.

My ../run/systemd/resolve/stub_resolv.conf has:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888
nameserver 192.168.0.1
# Too many DNS servers configured, the following entries may be ignored.
nameserver 205.171.2.65
search Home

top of ../run/systemd/resolv/resolv.conf had
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.
so, there are man(uals) for both resolv.conf and systemd-resolved.service  I guess I will check those out but I doubt I am going to understand much of that but I will give it a shot.  Its kinda interesting that when they say to access they say "man:whatever" instead of "man whatever".  One can only wonder why in the world this has not been fixed or a step-by-step fix posted.  There are so many posts with fixes (I have tried at least 6 to no avail but I am concerned for my entire system if I keep it up) one would think somebody who knows would just either fix or tell us how to fix.

mysteries abound.........

---

### Post by mitesh.agrwl on 2018-12-01
> greg@greg-down:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.5 icmp_seq=1 Destination Host Unreachable

An interesting aside is that 192.168.0.5 is the address of my router

Pinging IP address has nothing to do with DNS, it is a network test which shows the health of network, connectivity in this case. If the router has returned the above message, it simply means that the the router can not reach the outside address i.e. no Internet connection available at that moment. Sometimes this happens when the connectivity from ISP fails due to an upgrade or a temporary fault, in this case you should call your ISP and ask for technical assistance. DNS issues comes in picture when the Intrnet connection is working and you are able to ping an outside public address like 8.8.8.8 or 208.67.222.222 or 208.67.220.220

---

### Post by SeijiSensei on 2018-12-01
> **jgw said:**
> I have no idea how to "build a static resolv.conf"

As I suggested above, delete or rename the current /etc/resolv.conf to another name like /etc/resolv.old.  Next open an editor with sudo; the easiest choice is nano which is included by default.

```

sudo mv /etc/resolv.conf /etc/resolv.old
sudo nano /etc/resolv.conf
```

That will open the nano editor with root privileges. Now enter these two lines that reference Google's nameservers:

```

nameserver 8.8.8.8
nameserver 8.8.4.4

```

then save the file holding down the Ctrl key and hitting X, then answering "Y" for yes when prompted.

---

### Post by jgw on 2018-12-01
Thanks for the info.  I was wondering what you put into the file.  I just checked my /run/systemd/resolv/resolv.conf and found:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888

I have no idea what the second nameserver thing is.

For the heck of it I did a search for 'resolv' and you might find the results interesting:
```

greg@greg-down:/$ locate resolv
/etc/resolv.conf
/etc/resolvconf
/etc/dhcp/dhclient-enter-hooks.d/resolved
/etc/openvpn/update-resolv-conf
/etc/ppp/resolv
/etc/resolvconf/update-libc.d
/etc/resolvconf/update-libc.d/avahi-daemon
/etc/resolvconf/update-libc.d/postfix
/etc/systemd/resolved.conf
/etc/systemd/system/dbus-org.freedesktop.resolve1.service
/etc/systemd/system/multi-user.target.wants/systemd-resolved.service
/home/greg/.local/share/Trash/files/resolv.conf.2
/home/greg/.local/share/Trash/files/resolv.conf.what
/home/greg/.local/share/Trash/info/resolv.conf.2.trashinfo
/home/greg/.local/share/Trash/info/resolv.conf.what.trashinfo
/lib/modules/4.15.0-38-generic/kernel/drivers/staging/iio/resolver
/lib/modules/4.15.0-38-generic/kernel/drivers/staging/iio/resolver/ad2s1200.ko
/lib/modules/4.15.0-38-generic/kernel/drivers/staging/iio/resolver/ad2s1210.ko
/lib/modules/4.15.0-38-generic/kernel/drivers/staging/iio/resolver/ad2s90.ko
/lib/modules/4.15.0-39-generic/kernel/drivers/staging/iio/resolver
/lib/modules/4.15.0-39-generic/kernel/drivers/staging/iio/resolver/ad2s1200.ko
/lib/modules/4.15.0-39-generic/kernel/drivers/staging/iio/resolver/ad2s1210.ko
/lib/modules/4.15.0-39-generic/kernel/drivers/staging/iio/resolver/ad2s90.ko
/lib/systemd/resolv.conf
/lib/systemd/systemd-resolved
/lib/systemd/system/systemd-resolved.service
/lib/x86_64-linux-gnu/libresolv-2.27.so
/lib/x86_64-linux-gnu/libresolv.so.2
/snap/core/5662/etc/resolv.conf
/snap/core/5662/etc/resolvconf
/snap/core/5662/etc/cloud/templates/resolv.conf.tmpl
/snap/core/5662/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/core/5662/etc/dhcp/dhclient-enter-hooks.d/resolvconf
/snap/core/5662/etc/init/resolvconf.conf
/snap/core/5662/etc/init.d/resolvconf
/snap/core/5662/etc/network/if-down.d/resolvconf
/snap/core/5662/etc/network/if-up.d/000resolvconf
/snap/core/5662/etc/ppp/ip-down.d/000resolvconf
/snap/core/5662/etc/ppp/ip-up.d/000resolvconf
/snap/core/5662/etc/rc0.d/K01resolvconf
/snap/core/5662/etc/rc6.d/K01resolvconf
/snap/core/5662/etc/rcS.d/S02resolvconf
/snap/core/5662/etc/resolvconf/interface-order
/snap/core/5662/etc/resolvconf/resolv.conf.d
/snap/core/5662/etc/resolvconf/update.d
/snap/core/5662/etc/resolvconf/resolv.conf.d/base
/snap/core/5662/etc/resolvconf/resolv.conf.d/head
/snap/core/5662/etc/resolvconf/update.d/libc
/snap/core/5662/etc/systemd/resolved.conf
/snap/core/5662/etc/systemd/system/sysinit.target.wants/resolvconf.service
/snap/core/5662/lib/resolvconf
/snap/core/5662/lib/i386-linux-gnu/libresolv-2.23.so
/snap/core/5662/lib/i386-linux-gnu/libresolv.so.2
/snap/core/5662/lib/resolvconf/list-records
/snap/core/5662/lib/resolvconf/net-interface-handler
/snap/core/5662/lib/systemd/systemd-resolved
/snap/core/5662/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/core/5662/lib/systemd/system/resolvconf.service
/snap/core/5662/lib/systemd/system/resolvconf.service.wants
/snap/core/5662/lib/systemd/system/systemd-networkd-resolvconf-update.path
/snap/core/5662/lib/systemd/system/systemd-networkd-resolvconf-update.service
/snap/core/5662/lib/systemd/system/systemd-resolved.service
/snap/core/5662/lib/systemd/system/systemd-resolved.service.d
/snap/core/5662/lib/systemd/system/resolvconf.service.wants/systemd-networkd-resolvconf-update.path
/snap/core/5662/lib/systemd/system/systemd-resolved.service.d/resolvconf.conf
/snap/core/5662/lib/udev/rules.d/70-resolvconf-initramfs-copy.rules
/snap/core/5662/lib/x86_64-linux-gnu/libresolv-2.23.so
/snap/core/5662/lib/x86_64-linux-gnu/libresolv.so.2
/snap/core/5662/run/resolvconf
/snap/core/5662/run/resolvconf/enable-updates
/snap/core/5662/run/resolvconf/interface
/snap/core/5662/run/resolvconf/resolv.conf
/snap/core/5662/run/resolvconf/interface/original.resolvconf
/snap/core/5662/sbin/resolvconf
/snap/core/5662/usr/bin/sc-logresolve
/snap/core/5662/usr/bin/scmp_sys_resolver
/snap/core/5662/usr/bin/systemd-resolve
/snap/core/5662/usr/lib/python3/dist-packages/cloudinit/config/cc_resolv_conf.py
/snap/core/5662/usr/lib/python3/dist-packages/cloudinit/config/__pycache__/cc_resolv_conf.cpython-35.pyc
/snap/core/5662/usr/lib/python3/dist-packages/cloudinit/distros/parsers/resolv_conf.py
/snap/core/5662/usr/lib/python3/dist-packages/cloudinit/distros/parsers/__pycache__/resolv_conf.cpython-35.pyc
/snap/core/5662/usr/lib/python3/dist-packages/yaml/resolver.py
/snap/core/5662/usr/lib/python3/dist-packages/yaml/__pycache__/resolver.cpython-35.pyc
/snap/core/5662/usr/share/resolvconf
/snap/core/5662/usr/share/bash-completion/completions/resolvconf
/snap/core/5662/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/core/5662/usr/share/doc/resolvconf
/snap/core/5662/usr/share/doc/resolvconf/changelog.gz
/snap/core/5662/usr/share/doc/resolvconf/copyright.gz
/snap/core/5662/usr/share/resolvconf/dump-debug-info
/snap/core/5662/var/lib/resolvconf
/snap/core/5662/var/lib/resolvconf/linkified
/snap/core/5662/var/lib/systemd/deb-systemd-helper-enabled/resolvconf.service.dsh-also
/snap/core/5662/var/lib/systemd/deb-systemd-helper-enabled/sysinit.target.wants/resolvconf.service
/snap/core/5742/etc/resolv.conf
/snap/core/5742/etc/resolvconf
/snap/core/5742/etc/cloud/templates/resolv.conf.tmpl
/snap/core/5742/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/core/5742/etc/dhcp/dhclient-enter-hooks.d/resolvconf
/snap/core/5742/etc/init/resolvconf.conf
/snap/core/5742/etc/init.d/resolvconf
/snap/core/5742/etc/network/if-down.d/resolvconf
/snap/core/5742/etc/network/if-up.d/000resolvconf
/snap/core/5742/etc/ppp/ip-down.d/000resolvconf
/snap/core/5742/etc/ppp/ip-up.d/000resolvconf
/snap/core/5742/etc/rc0.d/K01resolvconf
/snap/core/5742/etc/rc6.d/K01resolvconf
/snap/core/5742/etc/rcS.d/S02resolvconf
/snap/core/5742/etc/resolvconf/interface-order
/snap/core/5742/etc/resolvconf/resolv.conf.d
/snap/core/5742/etc/resolvconf/update.d
/snap/core/5742/etc/resolvconf/resolv.conf.d/base
/snap/core/5742/etc/resolvconf/resolv.conf.d/head
/snap/core/5742/etc/resolvconf/update.d/libc
/snap/core/5742/etc/systemd/resolved.conf
/snap/core/5742/etc/systemd/system/sysinit.target.wants/resolvconf.service
/snap/core/5742/lib/resolvconf
/snap/core/5742/lib/i386-linux-gnu/libresolv-2.23.so
/snap/core/5742/lib/i386-linux-gnu/libresolv.so.2
/snap/core/5742/lib/resolvconf/list-records
/snap/core/5742/lib/resolvconf/net-interface-handler
/snap/core/5742/lib/systemd/systemd-resolved
/snap/core/5742/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/core/5742/lib/systemd/system/resolvconf.service
/snap/core/5742/lib/systemd/system/resolvconf.service.wants
/snap/core/5742/lib/systemd/system/systemd-networkd-resolvconf-update.path
/snap/core/5742/lib/systemd/system/systemd-networkd-resolvconf-update.service
/snap/core/5742/lib/systemd/system/systemd-resolved.service
/snap/core/5742/lib/systemd/system/systemd-resolved.service.d
/snap/core/5742/lib/systemd/system/resolvconf.service.wants/systemd-networkd-resolvconf-update.path
/snap/core/5742/lib/systemd/system/systemd-resolved.service.d/resolvconf.conf
/snap/core/5742/lib/udev/rules.d/70-resolvconf-initramfs-copy.rules
/snap/core/5742/lib/x86_64-linux-gnu/libresolv-2.23.so
/snap/core/5742/lib/x86_64-linux-gnu/libresolv.so.2
/snap/core/5742/run/resolvconf
/snap/core/5742/run/resolvconf/enable-updates
/snap/core/5742/run/resolvconf/interface
/snap/core/5742/run/resolvconf/resolv.conf
/snap/core/5742/run/resolvconf/interface/original.resolvconf
/snap/core/5742/sbin/resolvconf
/snap/core/5742/usr/bin/sc-logresolve
/snap/core/5742/usr/bin/scmp_sys_resolver
/snap/core/5742/usr/bin/systemd-resolve
/snap/core/5742/usr/lib/python3/dist-packages/cloudinit/config/cc_resolv_conf.py
/snap/core/5742/usr/lib/python3/dist-packages/cloudinit/config/__pycache__/cc_resolv_conf.cpython-35.pyc
/snap/core/5742/usr/lib/python3/dist-packages/cloudinit/distros/parsers/resolv_conf.py
/snap/core/5742/usr/lib/python3/dist-packages/cloudinit/distros/parsers/__pycache__/resolv_conf.cpython-35.pyc
/snap/core/5742/usr/lib/python3/dist-packages/yaml/resolver.py
/snap/core/5742/usr/lib/python3/dist-packages/yaml/__pycache__/resolver.cpython-35.pyc
/snap/core/5742/usr/share/resolvconf
/snap/core/5742/usr/share/bash-completion/completions/resolvconf
/snap/core/5742/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/core/5742/usr/share/doc/resolvconf
/snap/core/5742/usr/share/doc/resolvconf/changelog.gz
/snap/core/5742/usr/share/doc/resolvconf/copyright.gz
/snap/core/5742/usr/share/resolvconf/dump-debug-info
/snap/core/5742/var/lib/resolvconf
/snap/core/5742/var/lib/resolvconf/linkified
/snap/core/5742/var/lib/systemd/deb-systemd-helper-enabled/resolvconf.service.dsh-also
/snap/core/5742/var/lib/systemd/deb-systemd-helper-enabled/sysinit.target.wants/resolvconf.service
/snap/core/5897/etc/resolv.conf
/snap/core/5897/etc/resolvconf
/snap/core/5897/etc/cloud/templates/resolv.conf.tmpl
/snap/core/5897/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/core/5897/etc/dhcp/dhclient-enter-hooks.d/resolvconf
/snap/core/5897/etc/init/resolvconf.conf
/snap/core/5897/etc/init.d/resolvconf
/snap/core/5897/etc/network/if-down.d/resolvconf
/snap/core/5897/etc/network/if-up.d/000resolvconf
/snap/core/5897/etc/ppp/ip-down.d/000resolvconf
/snap/core/5897/etc/ppp/ip-up.d/000resolvconf
/snap/core/5897/etc/rc0.d/K01resolvconf
/snap/core/5897/etc/rc6.d/K01resolvconf
/snap/core/5897/etc/rcS.d/S02resolvconf
/snap/core/5897/etc/resolvconf/interface-order
/snap/core/5897/etc/resolvconf/resolv.conf.d
/snap/core/5897/etc/resolvconf/update.d
/snap/core/5897/etc/resolvconf/resolv.conf.d/base
/snap/core/5897/etc/resolvconf/resolv.conf.d/head
/snap/core/5897/etc/resolvconf/update.d/libc
/snap/core/5897/etc/systemd/resolved.conf
/snap/core/5897/etc/systemd/system/sysinit.target.wants/resolvconf.service
/snap/core/5897/lib/resolvconf
/snap/core/5897/lib/i386-linux-gnu/libresolv-2.23.so
/snap/core/5897/lib/i386-linux-gnu/libresolv.so.2
/snap/core/5897/lib/resolvconf/list-records
/snap/core/5897/lib/resolvconf/net-interface-handler
/snap/core/5897/lib/systemd/systemd-resolved
/snap/core/5897/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/core/5897/lib/systemd/system/resolvconf.service
/snap/core/5897/lib/systemd/system/resolvconf.service.wants
/snap/core/5897/lib/systemd/system/systemd-networkd-resolvconf-update.path
/snap/core/5897/lib/systemd/system/systemd-networkd-resolvconf-update.service
/snap/core/5897/lib/systemd/system/systemd-resolved.service
/snap/core/5897/lib/systemd/system/systemd-resolved.service.d
/snap/core/5897/lib/systemd/system/resolvconf.service.wants/systemd-networkd-resolvconf-update.path
/snap/core/5897/lib/systemd/system/systemd-resolved.service.d/resolvconf.conf
/snap/core/5897/lib/udev/rules.d/70-resolvconf-initramfs-copy.rules
/snap/core/5897/lib/x86_64-linux-gnu/libresolv-2.23.so
/snap/core/5897/lib/x86_64-linux-gnu/libresolv.so.2
/snap/core/5897/run/resolvconf
/snap/core/5897/run/resolvconf/enable-updates
/snap/core/5897/run/resolvconf/interface
/snap/core/5897/run/resolvconf/resolv.conf
/snap/core/5897/run/resolvconf/interface/original.resolvconf
/snap/core/5897/sbin/resolvconf
/snap/core/5897/usr/bin/sc-logresolve
/snap/core/5897/usr/bin/scmp_sys_resolver
/snap/core/5897/usr/bin/systemd-resolve
/snap/core/5897/usr/lib/python3/dist-packages/cloudinit/config/cc_resolv_conf.py
/snap/core/5897/usr/lib/python3/dist-packages/cloudinit/config/__pycache__/cc_resolv_conf.cpython-35.pyc
/snap/core/5897/usr/lib/python3/dist-packages/cloudinit/distros/parsers/resolv_conf.py
/snap/core/5897/usr/lib/python3/dist-packages/cloudinit/distros/parsers/__pycache__/resolv_conf.cpython-35.pyc
/snap/core/5897/usr/lib/python3/dist-packages/yaml/resolver.py
/snap/core/5897/usr/lib/python3/dist-packages/yaml/__pycache__/resolver.cpython-35.pyc
/snap/core/5897/usr/share/resolvconf
/snap/core/5897/usr/share/bash-completion/completions/resolvconf
/snap/core/5897/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/core/5897/usr/share/doc/resolvconf
/snap/core/5897/usr/share/doc/resolvconf/changelog.gz
/snap/core/5897/usr/share/doc/resolvconf/copyright.gz
/snap/core/5897/usr/share/resolvconf/dump-debug-info
/snap/core/5897/var/lib/resolvconf
/snap/core/5897/var/lib/resolvconf/linkified
/snap/core/5897/var/lib/systemd/deb-systemd-helper-enabled/resolvconf.service.dsh-also
/snap/core/5897/var/lib/systemd/deb-systemd-helper-enabled/sysinit.target.wants/resolvconf.service
/snap/gnome-logs/40/usr/bin/systemd-resolve
/snap/gnome-logs/40/usr/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/gnome-logs/40/usr/etc/systemd/resolved.conf
/snap/gnome-logs/40/usr/etc/systemd/system/multi-user.target.wants/systemd-resolved.service
/snap/gnome-logs/40/usr/lib/libnss_resolve.so.2
/snap/gnome-logs/40/usr/lib/systemd/resolv.conf
/snap/gnome-logs/40/usr/lib/systemd/systemd-resolved
/snap/gnome-logs/40/usr/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/gnome-logs/40/usr/lib/systemd/system/org.freedesktop.resolve1.busname
/snap/gnome-logs/40/usr/lib/systemd/system/systemd-resolved.service
/snap/gnome-logs/40/usr/lib/systemd/system/busnames.target.wants/org.freedesktop.resolve1.busname
/snap/gnome-logs/40/usr/share/bash-completion/completions/systemd-resolve
/snap/gnome-logs/40/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/gnome-logs/40/usr/share/man/man1/systemd-resolve.1
/snap/gnome-logs/40/usr/share/man/man5/resolved.conf.5
/snap/gnome-logs/40/usr/share/man/man5/resolved.conf.d.5
/snap/gnome-logs/40/usr/share/man/man8/libnss_resolve.so.2.8
/snap/gnome-logs/40/usr/share/man/man8/nss-resolve.8
/snap/gnome-logs/40/usr/share/man/man8/systemd-resolved.8
/snap/gnome-logs/40/usr/share/man/man8/systemd-resolved.service.8
/snap/gnome-logs/40/usr/share/zsh/site-functions/_systemd-resolve
/snap/gnome-logs/43/usr/bin/systemd-resolve
/snap/gnome-logs/43/usr/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/gnome-logs/43/usr/etc/systemd/resolved.conf
/snap/gnome-logs/43/usr/etc/systemd/system/multi-user.target.wants/systemd-resolved.service
/snap/gnome-logs/43/usr/lib/libnss_resolve.so.2
/snap/gnome-logs/43/usr/lib/systemd/resolv.conf
/snap/gnome-logs/43/usr/lib/systemd/systemd-resolved
/snap/gnome-logs/43/usr/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/gnome-logs/43/usr/lib/systemd/system/org.freedesktop.resolve1.busname
/snap/gnome-logs/43/usr/lib/systemd/system/systemd-resolved.service
/snap/gnome-logs/43/usr/lib/systemd/system/busnames.target.wants/org.freedesktop.resolve1.busname
/snap/gnome-logs/43/usr/share/bash-completion/completions/systemd-resolve
/snap/gnome-logs/43/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/gnome-logs/43/usr/share/man/man1/systemd-resolve.1
/snap/gnome-logs/43/usr/share/man/man5/resolved.conf.5
/snap/gnome-logs/43/usr/share/man/man5/resolved.conf.d.5
/snap/gnome-logs/43/usr/share/man/man8/libnss_resolve.so.2.8
/snap/gnome-logs/43/usr/share/man/man8/nss-resolve.8
/snap/gnome-logs/43/usr/share/man/man8/systemd-resolved.8
/snap/gnome-logs/43/usr/share/man/man8/systemd-resolved.service.8
/snap/gnome-logs/43/usr/share/zsh/site-functions/_systemd-resolve
/snap/gnome-logs/45/usr/bin/systemd-resolve
/snap/gnome-logs/45/usr/etc/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/gnome-logs/45/usr/etc/systemd/resolved.conf
/snap/gnome-logs/45/usr/etc/systemd/system/multi-user.target.wants/systemd-resolved.service
/snap/gnome-logs/45/usr/lib/libnss_resolve.so.2
/snap/gnome-logs/45/usr/lib/systemd/resolv.conf
/snap/gnome-logs/45/usr/lib/systemd/systemd-resolved
/snap/gnome-logs/45/usr/lib/systemd/system/dbus-org.freedesktop.resolve1.service
/snap/gnome-logs/45/usr/lib/systemd/system/org.freedesktop.resolve1.busname
/snap/gnome-logs/45/usr/lib/systemd/system/systemd-resolved.service
/snap/gnome-logs/45/usr/lib/systemd/system/busnames.target.wants/org.freedesktop.resolve1.busname
/snap/gnome-logs/45/usr/share/bash-completion/completions/systemd-resolve
/snap/gnome-logs/45/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/snap/gnome-logs/45/usr/share/man/man1/systemd-resolve.1
/snap/gnome-logs/45/usr/share/man/man5/resolved.conf.5
/snap/gnome-logs/45/usr/share/man/man5/resolved.conf.d.5
/snap/gnome-logs/45/usr/share/man/man8/libnss_resolve.so.2.8
/snap/gnome-logs/45/usr/share/man/man8/nss-resolve.8
/snap/gnome-logs/45/usr/share/man/man8/systemd-resolved.8
/snap/gnome-logs/45/usr/share/man/man8/systemd-resolved.service.8
/snap/gnome-logs/45/usr/share/zsh/site-functions/_systemd-resolve
/snap/network-manager/263/usr/lib/x86_64-linux-gnu/libresolv.so
/snap/polarr/9/app/resources/app.asar.unpacked/node_modules/sharp/vendor/include/glib-2.0/gio/gproxyresolver.h
/snap/polarr/9/app/resources/app.asar.unpacked/node_modules/sharp/vendor/include/glib-2.0/gio/gresolver.h
/snap/polarr/9/app/resources/app.asar.unpacked/node_modules/sharp/vendor/include/glib-2.0/gio/gsimpleproxyresolver.h
/usr/bin/avahi-resolve
/usr/bin/avahi-resolve-address
/usr/bin/avahi-resolve-host-name
/usr/bin/systemd-resolve
/usr/include/resolv.h
/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf
/usr/lib/debug/lib/x86_64-linux-gnu/libresolv-2.27.so
/usr/lib/jvm/java-11-openjdk-amd64/legal/jdk.xml.bind/xmlresolver.md
/usr/lib/libreoffice/program/libuuresolverlo.so
/usr/lib/python2.7/dist-packages/cssutils/tests/sheets/2resolve.css
/usr/lib/python2.7/dist-packages/dns/resolver.py
/usr/lib/python2.7/dist-packages/dns/resolver.pyc
/usr/lib/python2.7/dist-packages/yaml/resolver.py
/usr/lib/python2.7/dist-packages/yaml/resolver.pyc
/usr/lib/python3/dist-packages/yaml/resolver.py
/usr/lib/python3/dist-packages/yaml/__pycache__/resolver.cpython-36.pyc
/usr/lib/tmpfiles.d/connman_resolvconf.conf
/usr/lib/x86_64-linux-gnu/libresolv.a
/usr/lib/x86_64-linux-gnu/libresolv.so
/usr/lib/x86_64-linux-gnu/samba/ldb/resolve_oids.so
/usr/share/bash-completion/completions/resolvconf
/usr/share/bash-completion/completions/systemd-resolve
/usr/share/dbus-1/system-services/org.freedesktop.resolve1.service
/usr/share/dbus-1/system.d/org.freedesktop.resolve1.conf
/usr/share/doc/libnet-dns-perl/examples/demo/mresolv
/usr/share/doc/python-libxml2/examples/resolver.py
/usr/share/icons/hicolor/16x16/animations/aptdaemon-action-resolving.png
/usr/share/icons/hicolor/16x16/status/aptdaemon-resolve.png
/usr/share/icons/hicolor/22x22/animations/aptdaemon-action-resolving.png
/usr/share/icons/hicolor/22x22/status/aptdaemon-resolve.png
/usr/share/icons/hicolor/24x24/animations/aptdaemon-action-resolving.png
/usr/share/icons/hicolor/24x24/status/aptdaemon-resolve.png
/usr/share/icons/hicolor/48x48/animations/aptdaemon-action-resolving.png
/usr/share/icons/hicolor/48x48/status/aptdaemon-resolve.png
/usr/share/man/man1/avahi-resolve-address.1.gz
/usr/share/man/man1/avahi-resolve-host-name.1.gz
/usr/share/man/man1/avahi-resolve.1.gz
/usr/share/man/man1/systemd-resolve.1.gz
/usr/share/man/man3/resolver.3.gz
/usr/share/man/man5/resolv.conf.5.gz
/usr/share/man/man5/resolved.conf.5.gz
/usr/share/man/man5/resolved.conf.d.5.gz
/usr/share/man/man5/resolver.5.gz
/usr/share/man/man8/systemd-resolved.8.gz
/usr/share/man/man8/systemd-resolved.service.8.gz
/usr/share/polkit-1/actions/org.freedesktop.resolve1.policy
/usr/share/system-config-printer/dnssdresolve.py
/usr/share/system-config-printer/__pycache__/dnssdresolve.cpython-36.pyc
/usr/share/zsh/vendor-completions/_systemd-resolve
/usr/src/linux-headers-4.15.0-38/drivers/staging/iio/resolver
/usr/src/linux-headers-4.15.0-38/drivers/staging/iio/resolver/Kconfig
/usr/src/linux-headers-4.15.0-38/drivers/staging/iio/resolver/Makefile
/usr/src/linux-headers-4.15.0-38/include/keys/dns_resolver-type.h
/usr/src/linux-headers-4.15.0-38/include/linux/dns_resolver.h
/usr/src/linux-headers-4.15.0-38/net/dns_resolver
/usr/src/linux-headers-4.15.0-38/net/dns_resolver/Kconfig
/usr/src/linux-headers-4.15.0-38/net/dns_resolver/Makefile
/usr/src/linux-headers-4.15.0-38-generic/include/config/ceph/lib/use/dns/resolver.h
/usr/src/linux-headers-4.15.0-38-generic/include/config/dns/resolver.h
/usr/src/linux-headers-4.15.0-39/drivers/staging/iio/resolver
/usr/src/linux-headers-4.15.0-39/drivers/staging/iio/resolver/Kconfig
/usr/src/linux-headers-4.15.0-39/drivers/staging/iio/resolver/Makefile
/usr/src/linux-headers-4.15.0-39/include/keys/dns_resolver-type.h
/usr/src/linux-headers-4.15.0-39/include/linux/dns_resolver.h
/usr/src/linux-headers-4.15.0-39/net/dns_resolver
/usr/src/linux-headers-4.15.0-39/net/dns_resolver/Kconfig
/usr/src/linux-headers-4.15.0-39/net/dns_resolver/Makefile
/usr/src/linux-headers-4.15.0-39-generic/include/config/ceph/lib/use/dns/resolver.h
/usr/src/linux-headers-4.15.0-39-generic/include/config/dns/resolver.h
/var/lib/app-info/icons/ubuntu-bionic-universe/64x64/gresolver_gresolver.png
/var/tmp/systemd-private-c80ab8e3f0cb48b2bb24792dbbd27528-systemd-resolved.service-sHzNJk
greg@greg-down:/$ 

```


Thanks again!

---

### Post by jgw on 2018-12-01
lost the internet, rebooted, my /etc/resolv.conf now looks like:
# Generated by Connection Manager
nameserver ::1
nameserver 127.0.0.1

for what its worth.  There is a command "nm-connection-editor" which lets one edit connections differently from what you get in settings
The other thing is that it lists connections that are used.  For instance, in my ethernet/wired connections I have:
enp2s0                      3 minutes ago
enp2s0                     51 minutes ago     
wired connection 1     9 days ago

For my wireless I have:
TP_LINK 7496C2 3           1 day ago
TP_LINK 7496C2 2           4 days ago
TP_LINK 7496C2 1           4 days ago
TP_LINK 7496C2              1 month ago

it also lists when the connection was last used.  When I check these out they are slightly different settings.  One can also setup exactly how they operate.  I am tempted to mess with them but fear I will REALLY screw things up so I will leave them alone.  I use both because I think there is something wrong with my wired connection as it, sometimes, just fails for absolutely no reason.  I have another machine hooked to a hub which doesn't have any problems in this regard hence my thought on my ethernet connection.  I am working on that one.

I should also mention that the other machine also seems to be a lot more firm insofar as its connection to the internet, nameserver stuff, etc.  I am also tempted to copy its settings to this machine but, again, especially given just how many 'resolv' things are on my system (seriously complicated) that I just don't have the guts.  I am starting to think I should download the greatest and latest ubuntu and just reinstall <sigh>

---

### Post by SeijiSensei on 2018-12-01
> **jgw said:**
> Thanks for the info.  I was wondering what you put into the file.  I just checked my /run/systemd/resolv/resolv.conf and found:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888

I have no idea what the second nameserver thing is.

It is the IP version 6 address of the same nameserver.

```

host 2001:4860:4860::8888
8.8.8.8.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.6.8.4.0.6.8.4.1.0.0.2.ip6.arpa domain name pointer google-public-dns-a.google.com.

host 8.8.8.8
8.8.8.8.in-addr.arpa domain name pointer google-public-dns-a.google.com.

```

---

### Post by jgw on 2018-12-01
I am curious.  

8.8.8.8 is a valid nameserver address
would the address of my internet router 192.168.0.1 also be a valid nameserver address?

---

### Post by SeijiSensei on 2018-12-02
Many routers have a built-in DNS server.  So it's possible that the router's address is a valid DNS server for your network.

---

### Post by jgw on 2018-12-02
thank you.........

Thought I would offer this stuff.  My machine is now breaking a record for not stopping my internet connection, at least for my wired connection.  Hopefully it will last.

I have setup my wired connection with setting DHCP to automatic and 127.168.0.1 as DNS  (DNS automatic option not chosen)

my /etc/resolv.conf:
nameserver ::1
nameserver 127.0.0.1

my /run/systemd/resolve/resolv.conf:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888
nameserver 192.168.0.1

Here are a couple of other quests for info.  In the first one the "IP4.DNS[1]" is the color red (have no idea what that is about but, hopefully, its a good thing)
greg@greg-down:~$  nmcli dev show | grep 'IP4.DNS'
IP4.DNS[1]:                             192.168.0.1

greg@greg-down:~$ systemd-resolve --status | grep 'DNS Servers'
         DNS Servers: 8.8.8.8
         DNS Servers: 192.168.0.1
greg@greg-down:~$ 


```

         DNS Servers: 8.8.8.8
                      2001:4860:4860::8888
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 3 (wlx1c4bd6ded3b0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 2 (enp2s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.0.1
lines 17-45/45 (END)

```

---

### Post by jgw on 2018-12-03
I am on my second day without a problem!    I think my change in the wired connection did it and there is no reason why the same shouldn't hold true for the wifi connection.   I could test it but I don't want to risk my current connection.  If this holds true through tomorrow I will mark it solved.  Its been about 5 minutes since my last post and suddenly my machine flashed a connection loss and went away.  I tested it and it reconnected on its own.  Still have my fingers crossed. 

At the same time as the loss logs reported: 11:03:36 AM kernel: nouveau 0000:01:00.0: bsp: init failed, -2

---

### Post by jgw on 2018-12-04
Third day - on first boot I had strange things happening then lost my connection.  I think it was just a bad boot (under heading of "stuff happens" - I rebooted and everything is dandy so far.

---

### Post by jgw on 2018-12-07
Its now been about 5 days with only one little blip so I am going to mark this one as solved.  Here is what I did (again) if anybody is still wondering:
I have setup my wired connection with setting DHCP to automatic and 127.168.0.1 as DNS (DNS automatic option not chosen
my /etc/resolv.conf:
nameserver ::1
nameserver 127.0.0.1  (this is the address of my router - I can enter it into my browser and get access to that router which is an Actiontek C2000A-D)

my /run/systemd/resolve/resolv.conf:
nameserver 8.8.8.8
nameserver 2001:4860:4860::8888
nameserver 192.168.0.1

---

