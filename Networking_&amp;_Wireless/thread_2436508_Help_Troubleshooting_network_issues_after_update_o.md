---
title: "Help Troubleshooting network issues after update on 16.04 LTS"
date: 2020-02-07
forum: Networking &amp; Wireless
---

### Post by toy71camaro on 2020-02-07
First off, not a heavily experienced Linux user, but trying to install the latest software/security updates on one of our servers and running into some issues. Previous sysadmin is no longer with the company, so its up to me to figure it out.

Currently on Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-112-generic x86_64), and attempting my first "update" since taking over the position. After running the "apt full-upgrade" command (also tried apt upgrade with the same negative result) after it successfully updates and reboots, I have no network. During boot it shows its trying to "Raise" the network interface, but then hits the timeout threshold and fails, then finishes booting up. To which I have no network access at that point. Checking the status of the networking.services states "Loaded: not-found (Reason: no such file or directory). Active: inactive (dead)"

This is a VM on a VMWare esxi host. It runs a docker container with our software for monitoring our network devices. Trying to prevent having to either forgo any further updates, or spin up a brand new VM and re-do the whole setup. AND also trying to learn some additional troubleshooting skills while I'm at it. 

I've searched and troubleshot quite a bit from what I could find. Looks like it was fairly common that the Ethernet interface card got renamed from eth0 to ens32 or some other variation. But I've checked both before and after the update with the "ipconfig -a" command, and after upgrade, there is still an entry named eth0, but now it doesn't have an IP (like it did before updating/reboot). There are SEVERAL other devices shown when running that command, but eth0 was the one that matched the IP address of the device before the updates were performed.  The /network/interfaces file is referencing eth0 and set to DHCP (now, in our Windows AD DHCP settings, we have the IP Address reserved. So its essentially static, but from the DHCP server side, not within the Ubuntu config side). I've tried rebuilding the resolvconf file (dpkg-reconfigure resolvconf), but no luck. 
Tried setting up systemd with these commands, but no luck (I don't think it really worked, as the last command didn't show anything in the file like the example shows it should have):

```
$ sudo systemctl enable systemd-networkd
$ sudo systemctl enable systemd-resolved
$ sudo systemctl start systemd-resolved
$ sudo rm /etc/resolv.conf
$ sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
$ sudo vi /etc/systemd/network/20-dhcp.network
```

Any help would be appreciated, what logs to look for, etc.

Hopefully some of this info below helps pinpoint the issue, these are what I seen as most commonly requested bits of information when others were troubleshooting similar issues that I found.... I apologize if this is TOO MUCH info. :)


If it helps, this is what gets updated when running the 'apt list --upgradable' command:
```
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-112-generic x86_64)

63 packages can be updated.
37 updates are security updates.

$ uname -r
4.4.0-112-generic
$ apt list --upgradable
Listing... Done
bsdutils/xenial-updates 1:2.27.1-6ubuntu3.10 amd64 [upgradable from: 1:2.27.1-6ubuntu3.9]
dbus/xenial-updates 1.10.6-1ubuntu3.5 amd64 [upgradable from: 1.10.6-1ubuntu3.4]
docker-ce/xenial 5:19.03.5~3-0~ubuntu-xenial amd64 [upgradable from: 18.03.0~ce-0~ubuntu]
e2fslibs/xenial-updates,xenial-security 1.42.13-1ubuntu1.2 amd64 [upgradable from: 1.42.13-1ubuntu1.1]
e2fsprogs/xenial-updates,xenial-security 1.42.13-1ubuntu1.2 amd64 [upgradable from: 1.42.13-1ubuntu1.1]
grub-common/xenial-updates 2.02~beta2-36ubuntu3.23 amd64 [upgradable from: 2.02~beta2-36ubuntu3.22]
grub-pc/xenial-updates 2.02~beta2-36ubuntu3.23 amd64 [upgradable from: 2.02~beta2-36ubuntu3.22]
grub-pc-bin/xenial-updates 2.02~beta2-36ubuntu3.23 amd64 [upgradable from: 2.02~beta2-36ubuntu3.22]
grub2-common/xenial-updates 2.02~beta2-36ubuntu3.23 amd64 [upgradable from: 2.02~beta2-36ubuntu3.22]
landscape-common/xenial-updates 16.03-0ubuntu2.16.04.7 amd64 [upgradable from: 16.03-0ubuntu2.16.04.6]
libblkid1/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
libbsd0/xenial-updates,xenial-security 0.8.2-1ubuntu0.1 amd64 [upgradable from: 0.8.2-1]
libcomerr2/xenial-updates,xenial-security 1.42.13-1ubuntu1.2 amd64 [upgradable from: 1.42.13-1ubuntu1.1]
libdbus-1-3/xenial-updates 1.10.6-1ubuntu3.5 amd64 [upgradable from: 1.10.6-1ubuntu3.4]
libfdisk1/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
libgcrypt20/xenial-updates,xenial-security 1.6.5-2ubuntu0.6 amd64 [upgradable from: 1.6.5-2ubuntu0.5]
libgnutls-openssl27/xenial-updates,xenial-security 3.4.10-4ubuntu1.7 amd64 [upgradable from: 3.4.10-4ubuntu1.5]
libgnutls30/xenial-updates,xenial-security 3.4.10-4ubuntu1.7 amd64 [upgradable from: 3.4.10-4ubuntu1.5]
libmount1/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
libpam-systemd/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
libpcap0.8/xenial-updates,xenial-security 1.7.4-2ubuntu0.1 amd64 [upgradable from: 1.7.4-2]
libsasl2-2/xenial-updates,xenial-security 2.1.26.dfsg1-14ubuntu0.2 amd64 [upgradable from: 2.1.26.dfsg1-14ubuntu0.1]
libsasl2-modules/xenial-updates,xenial-security 2.1.26.dfsg1-14ubuntu0.2 amd64 [upgradable from: 2.1.26.dfsg1-14ubuntu0.1]
libsasl2-modules-db/xenial-updates,xenial-security 2.1.26.dfsg1-14ubuntu0.2 amd64 [upgradable from: 2.1.26.dfsg1-14ubuntu0.1]
libsmartcols1/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
libsqlite3-0/xenial-updates,xenial-security 3.11.0-1ubuntu1.3 amd64 [upgradable from: 3.11.0-1ubuntu1.2]
libss2/xenial-updates,xenial-security 1.42.13-1ubuntu1.2 amd64 [upgradable from: 1.42.13-1ubuntu1.1]
libsystemd0/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
libudev1/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
libuuid1/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
linux-generic/xenial-updates,xenial-security 4.4.0.173.181 amd64 [upgradable from: 4.4.0.112.118]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.173.181 amd64 [upgradable from: 4.4.0.112.118]
linux-image-generic/xenial-updates,xenial-security 4.4.0.173.181 amd64 [upgradable from: 4.4.0.112.118]
mount/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
ntpdate/xenial-updates,xenial-security 1:4.2.8p4+dfsg-3ubuntu5.10 amd64 [upgradable from: 1:4.2.8p4+dfsg-3ubuntu5.9]
python-apt/xenial-updates,xenial-security 1.1.0~beta1ubuntu0.16.04.8 amd64 [upgradable from: 1.1.0~beta1ubuntu0.16.04.5]
python-apt-common/xenial-updates,xenial-updates,xenial-security,xenial-security 1.1.0~beta1ubuntu0.16.04.8 all [upgradable from: 1.1.0~beta1ubuntu0.16.04.5]
python3-apt/xenial-updates,xenial-security 1.1.0~beta1ubuntu0.16.04.8 amd64 [upgradable from: 1.1.0~beta1ubuntu0.16.04.5]
python3-distupgrade/xenial-updates,xenial-updates 1:16.04.29 all [upgradable from: 1:16.04.27]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.17 all [upgradable from: 1:16.04.16]
sudo/xenial-updates,xenial-security 1.8.16-0ubuntu1.9 amd64 [upgradable from: 1.8.16-0ubuntu1.8]
systemd/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
systemd-sysv/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
tcpdump/xenial-updates,xenial-security 4.9.3-0ubuntu0.16.04.1 amd64 [upgradable from: 4.9.2-0ubuntu0.16.04.1]
ubuntu-minimal/xenial-updates 1.361.4 amd64 [upgradable from: 1.361.1]
ubuntu-release-upgrader-core/xenial-updates,xenial-updates 1:16.04.29 all [upgradable from: 1:16.04.27]
udev/xenial-updates,xenial-security 229-4ubuntu21.27 amd64 [upgradable from: 229-4ubuntu21.22]
unattended-upgrades/xenial-updates,xenial-updates 1.1ubuntu1.18.04.7~16.04.5 all [upgradable from: 1.1ubuntu1.18.04.7~16.04.4]
update-manager-core/xenial-updates,xenial-updates 1:16.04.17 all [upgradable from: 1:16.04.16]
util-linux/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
uuid-runtime/xenial-updates 2.27.1-6ubuntu3.10 amd64 [upgradable from: 2.27.1-6ubuntu3.9]
zlib1g/xenial-updates,xenial-security 1:1.2.8.dfsg-2ubuntu4.3 amd64 [upgradable from: 1:1.2.8.dfsg-2ubuntu4.1]
```


Network Interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

ifconfig -a BEFORE upgrade:

```

br-76b94d429ab7 Link encap:Ethernet  HWaddr 02:42:ad:dd:21:1f
          inet addr:172.19.0.1  Bcast:172.19.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:adff:fedd:211f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1054033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:799132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:471077466 (471.0 MB)  TX bytes:640440837 (640.4 MB)

br-8a8df466ff0b Link encap:Ethernet  HWaddr 02:42:a6:18:85:b2
          inet addr:172.18.0.1  Bcast:172.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:a6ff:fe18:85b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:224 (224.0 B)  TX bytes:1098 (1.0 KB)

docker0   Link encap:Ethernet  HWaddr 02:42:6f:8a:f3:f6
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:6fff:fe8a:f3f6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:1090 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:50:56:8d:94:de
          inet addr:10.4.1.100  Bcast:10.4.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe8d:94de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5167039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5159189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4555251766 (4.5 GB)  TX bytes:1811202940 (1.8 GB)
          Interrupt:18 Memory:fd4a0000-fd4c0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1298573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1298573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:284501805 (284.5 MB)  TX bytes:284501805 (284.5 MB)

veth6434285 Link encap:Ethernet  HWaddr d2:88:ae:9e:d4:03
          inet6 addr: fe80::d088:aeff:fe9e:d403/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:426492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1276080475 (1.2 GB)  TX bytes:191632276 (191.6 MB)

veth0a87ada Link encap:Ethernet  HWaddr da:5e:8e:ef:86:14
          inet6 addr: fe80::d85e:8eff:feef:8614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:895345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:614552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:406090378 (406.0 MB)  TX bytes:595224200 (595.2 MB)

veth0f71788 Link encap:Ethernet  HWaddr 32:99:47:37:8b:98
          inet6 addr: fe80::3099:47ff:fe37:8b98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1329409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1358205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1060107735 (1.0 GB)  TX bytes:1000319110 (1.0 GB)

veth2a6ee3e Link encap:Ethernet  HWaddr fa:36:ef:b2:67:02
          inet6 addr: fe80::f836:efff:feb2:6702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2722922 (2.7 MB)  TX bytes:840369 (840.3 KB)

veth49768a9 Link encap:Ethernet  HWaddr 6e:f3:b0:45:40:00
          inet6 addr: fe80::6cf3:b0ff:fe45:4000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:809799967 (809.7 MB)  TX bytes:1700663814 (1.7 GB)

veth8472b9f Link encap:Ethernet  HWaddr 4e:89:9f:03:48:b9
          inet6 addr: fe80::4c89:9fff:fe03:48b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:1054 (1.0 KB)

vethb25f10e Link encap:Ethernet  HWaddr e2:67:7d:67:a7:8f
          inet6 addr: fe80::e067:7dff:fe67:a78f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5421786 (5.4 MB)  TX bytes:32569897 (32.5 MB)

vethb2846c1 Link encap:Ethernet  HWaddr 82:77:e8:91:cb:ba
          inet6 addr: fe80::8077:e8ff:fe91:cbba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1384802 (1.3 MB)  TX bytes:1564599 (1.5 MB)

vethc3b2f3c Link encap:Ethernet  HWaddr ee:e1:3f:d5:3b:cb
          inet6 addr: fe80::ece1:3fff:fed5:3bcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:451769048 (451.7 MB)  TX bytes:625547794 (625.5 MB)

vethc47e6d7 Link encap:Ethernet  HWaddr d6:e8:b0:d0:c6:eb
          inet6 addr: fe80::d4e8:b0ff:fed0:c6eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7001909 (7.0 MB)  TX bytes:27631658 (27.6 MB)

vethccb957b Link encap:Ethernet  HWaddr 16:3c:da:9a:19:bd
          inet6 addr: fe80::143c:daff:fe9a:19bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:373474 (373.4 KB)  TX bytes:634273 (634.2 KB)

vethd3cbaae Link encap:Ethernet  HWaddr e6:ba:00:ae:1c:41
          inet6 addr: fe80::e4ba:ff:feae:1c41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:1256 (1.2 KB)

```

Checking syslog for anything "network" shows:
```

systemd[1]: Started trigger resolvconf update for networkd DNS.
systemd[1]: Starting Raise network interfaces...
ifup[748]: /sbin/ifup: waiting for lock on /run/network/ifstate.eth0
systemd[1]: networking.service: start operation timed out. Terminating.
systemd[1]: Failed to start Raise network interfaces.
systemd[1]: networking.service: Unit entered failed state.
systemd[1]: networking.service: failed with the result 'timeout'.

```

Checking if eth0 is UP:
```

$ sudo ifup eth0
ifup: interface eth0 already configured

```

Ping internal or External IP:
```

connect: Network is unreachable

```

---

### Post by praseodym on 2020-02-09
Remove those 2 "eth0" lines from the interfaces file and reboot

---

### Post by toy71camaro on 2020-02-19
> **praseodym said:**
> Remove those 2 "eth0" lines from the interfaces file and reboot


Thanks for chiming in and trying to help. Sorry it took so long to reply (had higher priority items pop up). Anyhow, I've tried your suggestion of removing the eth0 referenced lines in the network interfaces file and rebooting, and while I no longer get the 5 minute timer for attempting to "raise the network" upon bootup, I still get no network connection at all.

I check my eth0 interface after the reboot and it still has no IP assigned to it. 

Any other suggestions and/or logs to look at?

---

### Post by praseodym on 2020-02-19
Please run the wireless script from the sticky thread

---

