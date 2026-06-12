---
title: "RTL8168 Weird Problem (Not the usual one)"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by yianniscy84 on 2007-09-27
Hello,

i need desperately your help :p. 
I am running ubuntu 7.04 from my ASUS G1s laptop. I have RTL 8169 eth card. 
When i am at home i have internet and the network is working fine but when i am at the university.
I had this problem for a long time so i tried to do a clean install to see what was going wrong while I was at 
the university. I found out that while running Ubuntu from LiveCD i have internet and after when i booted for the first time everything kept working fine. So I downloaded the updates and when i booted back the internet wasn't working anymore. I thought maybe it was of the kernel change .15 to .20 but i cant connect even in the .15 kernel. I think maybe is that eth0:avah i see in ifconfig that does the damage because it gets ip with dhcp while eth0 doesn't. In the meanwhile at home works fine. Dont tell me it's the shutdown wake on lan because it's enabled, the university network because it works both for vista and before update ubuntu or to rollback the ethernets drivers.

Thanks in advance

---

### Post by yianniscy84 on 2007-09-27
Please can someone answer me. It's very urgent i need networking for my thesis [-o< [-o< [-o< [-o<

---

### Post by lisati on 2007-09-27
I'm not familiar with the particular card you have - is it wired or wireless?

---

### Post by noob12 on 2007-09-27
It's a wired device.

When you plug into the university net next time check these things, substitute appropriate interface name if you interface is not eth0:

```

sudo ethtool eth0

```

Make sure you do have "Link detected: yes".   If not, you are plugging into a dead port or you do have the "usual" problem with Windows disabling the wake-on-lan.

Check this:
```

ifconfig -a

```

If you don't have an IP v4 dotted quad address on eth0, that's a problem.  Check these logs:

Make sure you aren't running a firewall that's blocking DHCP.

Try manually bouncing the interface **sudo ifdown eth0** and **sudo ifup eth0**.

Save and later post the outputs of these if you still can't connect:
```

ifconfig -a

cat /etc/network/interfaces

route -n

cat /etc/resolv.conf

grep dhclient /var/log/syslog

tail -50 /var/log/kern.log

sudo iptables -nL

```

---

### Post by yianniscy84 on 2007-09-28
OK thanks. I'll do that next time i am at university.
For now i'm facing another problem. 
When i boot in ubuntu and the ethernet cable is not connected i dont have internet even when i connect it afterwards. Is there a way to re-initialize the network or something????

---

### Post by noob12 on 2007-09-28
That problem is a known bug in the driver:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

You have to be plugged in.  You can probably workaround by unloading/reloading the driver while plugged in.

Send me the diagnostics for your other problem when you get a chance.

---

### Post by yianniscy84 on 2007-10-04
Sorry for the delay but here it is. 

yiannis@yiannis-laptop:~$ sudo rmmod r8169
Password:
yiannis@yiannis-laptop:~$ sudo modprobe r8169
yiannis@yiannis-laptop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no
yiannis@yiannis-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:94:75:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:610 (610.0 b)  TX bytes:610 (610.0 b)

yiannis@yiannis-laptop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5951
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:fc:94:75:f3
Sending on   LPF/eth0/00:1b:fc:94:75:f3
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
yiannis@yiannis-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:fc:94:75:f3
Sending on   LPF/eth0/00:1b:fc:94:75:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
yiannis@yiannis-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:94:75:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63976 (62.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:FC:94:75:F3  
          inet addr:169.254.10.99  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23552 (23.0 KiB)  TX bytes:23552 (23.0 KiB)

yiannis@yiannis-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

yiannis@yiannis-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
yiannis@yiannis-laptop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 195.14.130.170


yiannis@yiannis-laptop:~$ grep dhclient /var/log/syslog
Oct  4 09:48:45 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  4 09:48:55 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct  4 09:49:04 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Oct  4 09:49:05 yiannis-laptop dhclient: No DHCPOFFERS received.
Oct  4 09:49:05 yiannis-laptop dhclient: No working leases in persistent database - sleeping.
Oct  4 09:51:00 yiannis-laptop dhclient: receive_packet failed on eth0: Network is down
Oct  4 09:52:21 yiannis-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5951
Oct  4 09:52:21 yiannis-laptop dhclient: killed old client process, removed PID file
Oct  4 09:52:21 yiannis-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Oct  4 09:52:21 yiannis-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Oct  4 09:52:21 yiannis-laptop dhclient: All rights reserved.
Oct  4 09:52:21 yiannis-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct  4 09:52:21 yiannis-laptop dhclient: 
Oct  4 09:52:21 yiannis-laptop dhclient: Listening on LPF/eth0/00:1b:fc:94:75:f3
Oct  4 09:52:21 yiannis-laptop dhclient: Sending on   LPF/eth0/00:1b:fc:94:75:f3
Oct  4 09:52:21 yiannis-laptop dhclient: Sending on   Socket/fallback
Oct  4 09:52:21 yiannis-laptop dhclient: DHCPRELEASE on eth0 to 192.168.1.254 port 67
Oct  4 09:52:21 yiannis-laptop dhclient: send_packet: Network is unreachable
Oct  4 09:52:21 yiannis-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Oct  4 09:52:37 yiannis-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Oct  4 09:52:37 yiannis-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Oct  4 09:52:37 yiannis-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Oct  4 09:52:37 yiannis-laptop dhclient: All rights reserved.
Oct  4 09:52:37 yiannis-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct  4 09:52:37 yiannis-laptop dhclient: 
Oct  4 09:52:38 yiannis-laptop dhclient: Listening on LPF/eth0/00:1b:fc:94:75:f3
Oct  4 09:52:38 yiannis-laptop dhclient: Sending on   LPF/eth0/00:1b:fc:94:75:f3
Oct  4 09:52:38 yiannis-laptop dhclient: Sending on   Socket/fallback
Oct  4 09:52:38 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct  4 09:52:43 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Oct  4 09:52:57 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Oct  4 09:53:09 yiannis-laptop dhclient: No DHCPOFFERS received.
Oct  4 09:53:09 yiannis-laptop dhclient: No working leases in persistent database - sleeping.
Oct  4 09:56:15 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct  4 09:56:20 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Oct  4 09:56:32 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct  4 09:56:41 yiannis-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct  4 09:56:46 yiannis-laptop dhclient: No DHCPOFFERS received.
Oct  4 09:56:46 yiannis-laptop dhclient: No working leases in persistent database - sleeping.
yiannis@yiannis-laptop:~$ tail -50 /var/log/kern.log
Oct  4 09:48:41 yiannis-laptop kernel: [   31.288000] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam  (04f2:b012)
Oct  4 09:48:41 yiannis-laptop kernel: [   31.288000] usbcore: registered new interface driver uvcvideo
Oct  4 09:48:41 yiannis-laptop kernel: [   31.288000] USB Video Class driver (v0.1.0)
Oct  4 09:48:41 yiannis-laptop kernel: [   31.368000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
Oct  4 09:48:41 yiannis-laptop kernel: [   31.368000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct  4 09:48:41 yiannis-laptop kernel: [   31.932000] fuse init (API version 7.8)
Oct  4 09:48:41 yiannis-laptop kernel: [   31.996000] lp: driver loaded but no devices found
Oct  4 09:48:41 yiannis-laptop kernel: [   32.040000] Adding 921564k swap on /dev/disk/by-uuid/2a3565be-8ed3-4a10-8381-bba1d4fc149b.  Priority:-1 extents:1 across:921564k
Oct  4 09:48:41 yiannis-laptop kernel: [   32.228000] EXT3 FS on sda6, internal journal
Oct  4 09:48:41 yiannis-laptop kernel: [   38.696000] ACPI: Battery Slot [BAT0] (battery present)
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] input: Power Button (FF) as /class/input/input6
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] ACPI: Power Button (FF) [PWRF]
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] input: Sleep Button (CM) as /class/input/input7
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] ACPI: Sleep Button (CM) [SLPB]
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] input: Lid Switch as /class/input/input8
Oct  4 09:48:41 yiannis-laptop kernel: [   38.716000] ACPI: Lid Switch [LID]
Oct  4 09:48:41 yiannis-laptop kernel: [   38.732000] Using specific hotkey driver
Oct  4 09:48:41 yiannis-laptop kernel: [   38.844000] No dock devices found.
Oct  4 09:48:41 yiannis-laptop kernel: [   38.856000] ACPI: AC Adapter [AC0] (on-line)
Oct  4 09:48:41 yiannis-laptop kernel: [   38.868000] ibm_acpi: ec object not found
Oct  4 09:48:41 yiannis-laptop kernel: [   38.900000] Asus Laptop ACPI Extras version 0.30
Oct  4 09:48:41 yiannis-laptop kernel: [   38.900000]   unsupported model G1S, trying default values
Oct  4 09:48:41 yiannis-laptop kernel: [   38.900000]   send /proc/acpi/dsdt to the developers
Oct  4 09:48:41 yiannis-laptop kernel: [   38.924000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct  4 09:48:41 yiannis-laptop kernel: [   38.932000] pcc_acpi: loading...
Oct  4 09:48:47 yiannis-laptop kernel: [   45.316000] ppdev: user-space parallel port driver
Oct  4 09:48:47 yiannis-laptop kernel: [   45.940000] apm: BIOS not found.
Oct  4 09:48:48 yiannis-laptop kernel: [   46.560000] Bluetooth: Core ver 2.11
Oct  4 09:48:48 yiannis-laptop kernel: [   46.560000] NET: Registered protocol family 31
Oct  4 09:48:48 yiannis-laptop kernel: [   46.560000] Bluetooth: HCI device and connection manager initialized
Oct  4 09:48:48 yiannis-laptop kernel: [   46.560000] Bluetooth: HCI socket layer initialized
Oct  4 09:48:48 yiannis-laptop kernel: [   46.580000] Bluetooth: L2CAP ver 2.8
Oct  4 09:48:48 yiannis-laptop kernel: [   46.580000] Bluetooth: L2CAP socket layer initialized
Oct  4 09:48:48 yiannis-laptop kernel: [   46.616000] usb 6-2: reset high speed USB device using ehci_hcd and address 3
Oct  4 09:48:48 yiannis-laptop kernel: [   46.932000] Bluetooth: RFCOMM socket layer initialized
Oct  4 09:48:48 yiannis-laptop kernel: [   46.932000] Bluetooth: RFCOMM TTY layer initialized
Oct  4 09:48:48 yiannis-laptop kernel: [   46.932000] Bluetooth: RFCOMM ver 1.8
Oct  4 09:48:49 yiannis-laptop kernel: [   47.996000] usb 6-2: reset high speed USB device using ehci_hcd and address 3
Oct  4 09:49:16 yiannis-laptop kernel: [   74.300000] NET: Registered protocol family 10
Oct  4 09:49:16 yiannis-laptop kernel: [   74.300000] lo: Disabled Privacy Extensions
Oct  4 09:49:16 yiannis-laptop kernel: [   74.300000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 09:51:00 yiannis-laptop kernel: [  178.668000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Oct  4 09:51:17 yiannis-laptop kernel: [  195.740000] r8169 Gigabit Ethernet driver 2.2LK loaded
Oct  4 09:51:17 yiannis-laptop kernel: [  195.740000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  4 09:51:17 yiannis-laptop kernel: [  195.740000] PCI: Setting latency timer of device 0000:02:00.0 to 64
Oct  4 09:51:17 yiannis-laptop kernel: [  195.744000] eth0: RTL8168b/8111b at 0xf88d8000, 00:1b:fc:94:75:f3, IRQ 16
Oct  4 09:51:17 yiannis-laptop kernel: [  195.804000] r8169: eth0: link down
Oct  4 09:51:17 yiannis-laptop kernel: [  195.804000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 09:52:37 yiannis-laptop kernel: [  275.564000] r8169: eth0: link down
Oct  4 09:52:37 yiannis-laptop kernel: [  275.564000] ADDRCONF(NETDEV_UP): eth0: link is not ready
yiannis@yiannis-laptop:~$ sudo iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by noob12 on 2007-10-04
Hmm.  You said your problem is not the usual one but it sure looks like it.  Either that or the port you are plugging into really is dead.   When you said "not the usual one", did you mean you had already looked at the material in this other thread here:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)  ?

Check out the suggestions there.  Fundamentally you have to get over the link down state.  Until you've gotten the link up, you won't get any further.

The eththool output says:
```

Link detected: no

```

Your dmesg says:
```

Oct 4 09:51:17 yiannis-laptop kernel: [ 195.744000] eth0: RTL8168b/8111b at 0xf88d8000, 00:1b:fc:94:75:f3, IRQ 16
Oct 4 09:51:17 yiannis-laptop kernel: [ 195.804000] r8169: eth0: link down
Oct 4 09:51:17 yiannis-laptop kernel: [ 195.804000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 4 09:52:37 yiannis-laptop kernel: [ 275.564000] r8169: eth0: link down
Oct 4 09:52:37 yiannis-laptop kernel: [ 275.564000] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by yianniscy84 on 2007-10-04
> **noob12 said:**
> Hmm.  You said your problem is not the usual one but it sure looks like it.  Either that or the port you are plugging into really is dead.   When you said "not the usual one", did you mean you had already looked at the material in this other thread here:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)  ?

Check out the suggestions there.  Fundamentally you have to get over the link down state.  Until you've gotten the link up, you won't get any further.

The eththool output says:
```

Link detected: no

```

Your dmesg says:
```

Oct 4 09:51:17 yiannis-laptop kernel: [ 195.744000] eth0: RTL8168b/8111b at 0xf88d8000, 00:1b:fc:94:75:f3, IRQ 16
Oct 4 09:51:17 yiannis-laptop kernel: [ 195.804000] r8169: eth0: link down
Oct 4 09:51:17 yiannis-laptop kernel: [ 195.804000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 4 09:52:37 yiannis-laptop kernel: [ 275.564000] r8169: eth0: link down
Oct 4 09:52:37 yiannis-laptop kernel: [ 275.564000] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

It's not the usual one because my ethernet works everywhere except the university. What is going on there? Is it something special or sth. 
Isn't there something like repair or get a new ip from dhcp in ubuntu like in windows?

PS: I followed the instructions at the link but didnt work

---

### Post by noob12 on 2007-10-04
Have you tried plugging some other computer into that port?  Are you sure the port you are using is live?

This isn't a DHCP issue.  The link is not active.

---

### Post by yianniscy84 on 2007-10-05
> **noob12 said:**
> Have you tried plugging some other computer into that port?  Are you sure the port you are using is live?

This isn't a DHCP issue.  The link is not active.

I use the same port for windows and they connect but sometimes i need to repair the connection to get a new ip. And it's not just one port. It's a computer laboratory full of ports that doesnt work for me.

---

### Post by yianniscy84 on 2007-10-05
Another thing that i remembered is that i installed ubuntu with a live cd on a port in that lab and i had internet even after the reboot. i downloaded the updates but then when i restarted a new kernel was installed .20.16 and i couldnt connect.

---

### Post by noob12 on 2007-10-05
Whenever you plug in, check the link state. One thing is for sure.   If it remains "Link detected: no" in ethtool output, you aren't going to get further.   This is equivalent to being unplugged.  No traffic will flow.  So you really must address that problem before you have any hope of sending a packet over that link.  Let's try to get there first.

Did you try going through the steps in the other thread yet to address the link detection issue?

Based on your Windows experience, you may have a DHCP issue too, but if that happens, it would happen *after* you solve the link issue.

---

