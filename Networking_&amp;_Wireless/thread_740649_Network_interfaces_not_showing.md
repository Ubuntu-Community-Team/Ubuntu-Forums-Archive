---
title: "Network interfaces not showing"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by linuxwarz on 2008-03-31
Hello,

When I boot and type ifconfig, only eth2 shows up.

I have configured eth0-3 as static in /etc/network/interfaces.

When I boot up, dmesg confirms the presence of the interface card.

> 
[   35.303489] sunhme.c:v3.00 June 23, 2006 David S. Miller (davem@davemloft.net)
[   35.305748] eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet <censored>
[   35.306069] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   35.306078] PCI: setting IRQ 12 as level-triggered
[   35.306084] ACPI: PCI Interrupt 0000:03:01.1[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   35.308347] eth1: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet <censored>
[   35.308676] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   35.308685] PCI: setting IRQ 5 as level-triggered
[   35.308690] ACPI: PCI Interrupt 0000:03:02.1[B] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   35.310978] eth2: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet <censored>
[   35.311294] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   35.311302] PCI: setting IRQ 10 as level-triggered
[   35.311307] ACPI: PCI Interrupt 0000:03:03.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   35.313740] eth3: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet <censored>


Interestingly enough, the log shows all interfaces having the same MAC address, and that is not the case. I have confirmed this interface card works with Ubuntu in another system.

Any suggestions to fix this?

I do not know the model # off the top of my head, but it is just like the one found here: [http://www.compuvest.com/Description.jsp;jsessionid=aErKgBAT46ggTsMedK?iid=444213](http://www.compuvest.com/Description.jsp;jsessionid=aErKgBAT46ggTsMedK?iid=444213)

---

### Post by Eiríkr on 2008-03-31
Please post the results of the following:
```
ifconfig
ifconfig -a
cat /etc/network/interfaces
sudo /etc/init.d/networking restart
```
And, if any of your interfaces are wireless, please also post the results of the following:
```
iwconfig
```

Cheers,

Eiríkr

---

### Post by linuxwarz on 2008-03-31
> 
nzadmin@ubuntu:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr <censored>
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:baff:fe36:ea4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:68996 (67.3 KB)  TX bytes:18624 (18.1 KB)
          Interrupt:5 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


> 
nzadmin@ubuntu:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr <censored>
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:baff:fe36:ea4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:70882 (69.2 KB)  TX bytes:21338 (20.8 KB)
          Interrupt:5 Base address:0x4800

eth0_rena Link encap:Ethernet  HWaddr <censored>
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x3800

eth1_rena Link encap:Ethernet  HWaddr <censored>
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0x4000

eth3_rena Link encap:Ethernet  HWaddr <censored>
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x5000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


> 
nzadmin@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth3
iface eth3 inet static
        address 192.168.1.251
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

auto eth2
iface eth2 inet static
        address 192.168.1.252
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

auto eth1
iface eth1 inet static
        address 192.168.1.253
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

auto eth0
iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255


> 
nzadmin@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for nzadmin:
 * Reconfiguring network interfaces...                                                                                                                                           eth3: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth3: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth3: ERROR while getting interface flags: No such device
eth3: ERROR while getting interface flags: No such device
Failed to bring up eth3.
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.


Looks nasty.

---

### Post by Eiríkr on 2008-03-31
These results, combined with all three having the same MAC addresses in dmesg, would seem to clearly indicate that something is borked at the hardware recognition level, which is beyond me.

Anyone else have any clues?

Cheers,

Eiríkr

---

