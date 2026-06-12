---
title: "no wired connection when booting 14.04  from live CD or USB"
date: 2015-06-23
forum: Networking &amp; Wireless
---

### Post by majurarainer on 2015-06-23
I am trying to install Ubunu 14.04 on a brand new machine with no system installed. Booting is fine but there is no network connection. I have created a new Ethernet connection and by adding all the IPv4 settings manually I have managed to connect, but there is no driver shown on the active network connection information. This is the same on the live CD and on the USB. I am hesitant to install without an internet connection. Any idea what I need to do? Thanks for your help

---

### Post by Vladlenin5000 on 2015-06-23
Hi and welcome.

You don't need internet to install. Whatever issues you may find after a successful installation can and should be troubleshooted from there. There's no point (for now) in worrying about what happens in the live session although it may be a strong indication of the issues you might find after installing.

---

### Post by majurarainer on 2015-06-23
OK, I will install and see what happens

---

### Post by majurarainer on 2015-06-24
Ok, I have a system, some connection but no internet. Here are some outputs, any help appreciated

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr fc:aa:14:c1:45:a1  
          inet addr:192.168.0.55  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fec1:45a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:235 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100393 (100.3 KB)  TX bytes:2414 (2.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36416 (36.4 KB)  TX bytes:36416 (36.4 KB)

~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        FC:AA:14:C1:45:A1

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

majurarainer@Gollum:~$ lspci -nn |grep Ethernet
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)

majurarainer@Gollum:~$ dmesg |  grep eth0
[    1.299538] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000c5c000, fc:aa:14:c1:45:a1, XID 0c000800 IRQ 73
[    1.299540] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.625806] r8169 0000:03:00.0 eth0: link down
[    2.625836] r8169 0000:03:00.0 eth0: link down
[    2.625858] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.065461] r8169 0000:03:00.0 eth0: link up
[    5.065469] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.887088] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   64.893196] r8169 0000:03:00.0 eth0: link up
[  118.946764] r8169 0000:03:00.0 eth0: link up
[ 1403.838846] r8169 0000:03:00.0 eth0: link up
[ 4862.240292] r8169 0000:03:00.0 eth0: link up
[ 4898.265167] r8169 0000:03:00.0 eth0: link up

---

### Post by majurarainer on 2015-06-27
ok. I can connect with a wireless usb but still not with the network. very frustrating

---

### Post by Vladlenin5000 on 2015-06-27
Have you tested it before?
Hardware issues cannot be solved by software...

---

### Post by majurarainer on 2015-06-30
Ok, I have sorted it out. It was the driver, I installed a new driver from Realtek and it has solved the problem.

---

### Post by majurarainer on 2015-07-08
Here are the details: 
get Linux device driver for Realtek Ethernet controllers
unpack tar
# ./autorun.sh    (with sudo)

# lsmod | grep r8168
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. 

activate the ethX.

# ifconfig ethX up

        ,where X=0,1,2,...

---

### Post by majurarainer on 2015-07-09
Here are the details: 
get Linux device driver for Realtek Ethernet controllers
unpack tar
# ./autorun.sh    (with sudo)

# lsmod | grep r8168
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. 

activate the ethX.

# ifconfig ethX up

        ,where X=0,1,2,...

---

### Post by majurarainer on 2015-07-09
Strangely enough latest update broke connection again. I had to repeat installation of driver to make it work again. Why is it so?

---

### Post by Vladlenin5000 on 2015-07-09
Because the kernel has been updated... Any driver/module installed that way needs to be installed again. 
There's a way to avoid this by using DKMS which should be able to rebuild the modules to the new kernel.

Unfortunately I'm not the person to explain you in simple steps the how-to, and the community page is no better: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)

---

