---
title: "Ubuntu 16 - wired connection not working"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by linuxgsm on 2016-12-12
Hello,


My wired ethernet connection is not working in ubuntu 16.


I have read the following threads and tried most of the suggestions posted there:


[Ubuntu 16.04: Wired connection not working, "eth0" renamed to "eno1". Can't connect]("https://ubuntuforums.org/showthread.php?t=2324354")


[no wired connection after upgrade to 16.04]("https://askubuntu.com/questions/762967/no-wired-connection-after-upgrade-to-16-04")


[Ubuntu 16.04 LTS Wired/Ethernet Internet Timeout - Not working]("https://askubuntu.com/questions/801537/ubuntu-16-04-lts-wired-ethernet-internet-timeout-not-working")


[Ubuntu 16.04 Ethernet issues]("https://askubuntu.com/questions/761036/ubuntu-16-04-ethernet-issues")


[Why Wired Internet is not working in Ubuntu 16.04 LTS?]("https://askubuntu.com/questions/763785/why-wired-internet-is-not-working-in-ubuntu-16-04-lts")


i did sys apt update and sys apt upgrade.


here are the contents of my /etc/network/interfaces file, i added the last two lines:


```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto enp7s0
iface enp7s0 inet dhcp

```

i tried deleting and recreating the connection, restarting the network, and most or all of the other suggestions at the links above, no joy.


does anybody know what else i could try?


regards,
erik

---

### Post by TheFu on 2016-12-12
Please post the the cmd and output for these things:

```
sudo lshw -C network
ping {ip-of-router}
ping 8.8.8.8
ping google.com

```
At this stage, we don't know if there is a driver issue, HW issue, misconfiguration, DNS issue, cable/port issue. We need FACTS. Interpretation of the facts isn't always helpful, which is why the actual cmd and output is necessary.

For example, is enp7s0 the correct device name? Please prove it. ;) That's what those cmds will do.

Definitely appreciate that you've attempted to fix this already. Wired usually isn't that hard to fix.

---

### Post by Ossipon on 2016-12-12
**In my case it was a hardware issue**

I had this problem too today. My network interface was renamed from eth0 to enp1s0. syslog was reporting messages like these, continuously:

```
Dec 12 19:11:58 wotan kernel: [ 1494.524821] r8169 0000:01:00.0 enp1s0: link up
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8614] device (enp1s0): link connected
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8626] device (enp1s0): state change: unava
ilable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8635] policy: auto-activating connection '
Wired connection 1'
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8645] device (enp1s0): Activation: startin
g connection 'Wired connection 1' (f661ffeb-b161-3b65-a7a3-58f1bd51e6c4)
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8648] device (enp1s0): state change: disco
nnected -> prepare (reason 'none') [30 40 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8649] manager: NetworkManager state is now
 CONNECTING
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8703] device (enp1s0): state change: prepa
re -> config (reason 'none') [40 50 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8742] device (enp1s0): state change: confi
g -> ip-config (reason 'none') [50 70 0]
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8746] dhcp4 (enp1s0): activation: beginnin
g transaction (timeout in 45 seconds)
Dec 12 19:11:58 wotan NetworkManager[1485]: <info>  [1481566318.8760] dhcp4 (enp1s0): dhclient started wit
h pid 6511
Dec 12 19:11:58 wotan dhclient[6511]: DHCPREQUEST of 192.168.1.3 on enp1s0 to 255.255.255.255 port 67 (xid
=0x115e7347)
Dec 12 19:11:59 wotan kernel: [ 1495.267912] r8169 0000:01:00.0 enp1s0: link down
Dec 12 19:11:59 wotan NetworkManager[1485]: <info>  [1481566319.8739] device (enp1s0): link disconnected (
deferring action for 4 seconds)
Dec 12 19:12:00 wotan avahi-daemon[1450]: Joining mDNS multicast group on interface enp1s0.IPv6 with address fe80::a462:a773:1523:5d4d.
Dec 12 19:12:00 wotan avahi-daemon[1450]: New relevant interface enp1s0.IPv6 for mDNS.
Dec 12 19:12:00 wotan avahi-daemon[1450]: Registering new address record for fe80::a462:a773:1523:5d4d on enp1s0.*.
Dec 12 19:12:01 wotan dhclient[6511]: DHCPREQUEST of 192.168.1.3 on enp1s0 to 255.255.255.255 port 67 (xid=0x115e7347)
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0416] device (enp1s0): link disconnected (calling deferred action)
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0419] device (enp1s0): state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0741] dhcp4 (enp1s0): canceled DHCP transaction, DHCP client pid 6511
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0741] dhcp4 (enp1s0): state changed unknown -> done
Dec 12 19:12:04 wotan avahi-daemon[1450]: Withdrawing address record for fe80::a462:a773:1523:5d4d on enp1s0.
Dec 12 19:12:04 wotan avahi-daemon[1450]: Leaving mDNS multicast group on interface enp1s0.IPv6 with address fe80::a462:a773:1523:5d4d.
Dec 12 19:12:04 wotan NetworkManager[1485]: <info>  [1481566324.0749] manager: NetworkManager state is now DISCONNECTED
Dec 12 19:12:04 wotan avahi-daemon[1450]: Interface enp1s0.IPv6 no longer relevant for mDNS.
Dec 12 19:12:08 wotan NetworkManager[1485]: <info>  [1481566328.0727] device (enp1s0): link connected
```

It turned out my windows installation had the same issue. When I disconnected my switch and connected to my modem directly, the connection was restored. I then tried different ports on the switch and found a combination that works. Apparently one or more ports on the switch are broken.

---

### Post by linuxgsm on 2016-12-13
> **Ossipon said:**
> It turned out my windows installation had the same issue. When I disconnected my switch and connected to my modem directly, the connection was restored. I then tried different ports on the switch and found a combination that works. Apparently one or more ports on the switch are broken.i forgot to mention.  on this machine, wired and wireless is working from the windows partition, and wireless is working from the linux partition.

also, i disabled ipv6, that had no effect.> **TheFu said:**
> Please post the the cmd and output for these things:here it is, with the wireless connection working and the wired connection not working:```
$ sudo lshw -C network

  *-network

       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: e0:db:55:d6:82:af
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:26 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff

  *-network

       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlp8s0
       version: c4
       serial: 60:36:dd:5d:18:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-53-generic firmware=18.168.6.1 ip=192.168.1.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:31 memory:c1500000-c1501fff
```

```
$ ping 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.96 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.94 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.81 ms
```

```
$ ping 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=29.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=47 time=29.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=47 time=29.4 ms
```

```
$ ping google.com

PING google.com (216.58.214.46) 56(84) bytes of data.
64 bytes from fra15s09-in-f14.1e100.net (216.58.214.46): icmp_seq=1 ttl=54 time=51.8 ms
64 bytes from fra15s09-in-f14.1e100.net (216.58.214.46): icmp_seq=2 ttl=54 time=32.1 ms
64 bytes from fra15s09-in-f14.1e100.net (216.58.214.46): icmp_seq=3 ttl=54 time=38.9 ms
```

> At this stage, we don't know if there is a driver issue, HW issue, misconfiguration, DNS issue, cable/port issue. We need FACTS. Interpretation of the facts isn't always helpful, which is why the actual cmd and output is necessary.For example, is enp7s0 the correct device name? Please prove it. ;) That's what those cmds will do.Definitely appreciate that you've attempted to fix this already. Wired usually isn't that hard to fix.i am grateful to you for your response.  i am happy to provide whatever information might be helpful, but i don't know much about networking.

---

### Post by TheFu on 2016-12-13
The realtek driver appears to be an issue and arises when dual booting with Windows according to what I've read.   [https://en.opensuse.org/SDB:Realtek_8169_driver_problem](https://en.opensuse.org/SDB:Realtek_8169_driver_problem)  ; appears there are possible fixes.  Blacklist the r8169, get the r8168 driver source, build it, install it, add it to the kernel with modprobe. There are steps in other posts here for how to accomplish it.

Don't know what happened with the past, but the there should be new lines as appropriate inside the code tags. It should look like it does in a terminal. Don't know why this happened. 

I always prefer Intel NICs for a few reasons. This is just one of the issues with RT stuff.

---

### Post by linuxgsm on 2016-12-13
i am typing this message under ubuntu with a wired, and not wireless, connection.  and you, my friend, are a supersonic superstar.  i owe you a beer.> **TheFu said:**
> Blacklist the r8169, get the r8168 driver source, build it, install it, add it to the kernel with modprobe.that sounds like more effort than i would be prepared to invest.  

however.  from the page that you linked:> You power down the machine completely and unplug the power supply for a few seconds (about 10 will do). This seems to reset the card and the Linux driver work until you boot Windows again.that right there is good enough for me.  

why did this work OK in the previous release of ubuntu?  the problem only arose after i upgraded to 16.> **TheFu said:**
> Don't know what happened with the post, but the there should be new lines as appropriate inside the code tags. It should look like it does in a terminal.i saw that.  i even tried to go back and edit the post and put the carriage returns back in by hand but they did not stick.  i suspect a bug in the forum software.  edit: it seems that by hitting enter twice i can generate a single carriage return...

anyway.  many thanks again.

---

### Post by TheFu on 2016-12-13
I don't know what changed.  Doubtful anything did on the Linux side. Perhaps a new driver was installed on the Windows side?  OTOH, I dunno.

But ... regardless - please mark the thread as SOLVED using the thread tools button near the top.

---

### Post by linuxgsm on 2016-12-13
i did not change anything on the windows side.  i did a bare metal reinstall of the linux partition.  looks to me like a new bug introduced by ubuntu 16.

---

### Post by TheFu on 2016-12-13
> **linuxgsm said:**
> i did not change anything on the windows side.  i did a bare metal reinstall of the linux partition.  looks to me like a new bug introduced by ubuntu 16.

Glad is it working.  Replacing the driver isn't THAT hard. Lots of how-to guides for this problem, since pretty much everyone dual booting with a gigE realtek NIC runs into it.  I've had to build and relink touchpad drivers with every kernel change manually for months before an update fixed the issue. It is a hassle, but once scripted, it isn't a big deal.  Imagine trying to do that without a mouse ... I'm fairly good with keyboard only use, but launching a terminal was something I'd always used a mouse for prior to that.  Now I've setup accel keys for all my favorite tools/programs.  Have about 15 that launch without any mouse. Faster and handy.

Doubtful Canonical had anything to do with this.  It is probably the upstream. In this case, kernel.org.  I say that since SuSE is also having it and they are not Debian, so it has to come from somewhere higher ... which is the kernel.

Over the decades, after being burned many times, I've gotten picky about which hardware I use.  Network stuff is something I'm especially picky about - always use Intel PRO/1000 NICs on systems that don't need 10Gbps connections.  There are lots of different compatible chips used, but the e1000 driver is rock solid and has been for over a decade.

Printers, scanners, video cards, mice, webcams, microphones ... all have issues with non-friendly-to-Linux brands.  I used to be about saving $10.  Then worked out that 20 hrs of frustration was worth $10 more for HW that "just worked."  Took me much too long to realize, but I'm dumb that way.

---

### Post by linuxgsm on 2016-12-14
yes, i bet you are right, this problem must be upstream somewhere, but not in ubuntu itself.

i think you are a million miles ahead of me.  i am a techie, but this is not my area.  i did recompile the kernel once, back when it did not support NTFS out of the box.  but i have lost too many evenings and weekends on this stuff, so in this case just powering down the machine is good enough for me.  i hope this will get fixed in a future update, it worked before.

i should pay more attention when purchasing hardware.  i always seem to buy in a rush and regret later.  and i completely agree, paying a little more to avoid compatibility problems is absolutely worth it...

---

### Post by linuxgsm on 2016-12-17
P.S. the connection also drops when the machine goes to sleep, and does not come back.  so if the machine hibernates you have to do another cold reboot.  getting to be kind of a hassle in fact.

---

