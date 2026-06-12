---
title: "&quot;wired&quot; not showing in network manager, no ethernet access"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by langendoerfer on 2017-10-16
Hello, i've installed 16.04lts gnome on two machines from the same source. On one of my machines the network manager does not display a wired option and ethernet is not recognized when plugged in. I've attached a screen shot of the network manager. I'd greatly appreciate any advice on resolving this issue. Thanks!

ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168483 (168.4 KB)  TX bytes:168483 (168.4 KB)


wlp2s0    Link encap:Ethernet  HWaddr 88:53:2e:96:84:4e  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8a53:2eff:fe96:844e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25143375 (25.1 MB)  TX bytes:3398527 (3.3 MB)

```

sudo lshw -c network:
```

 *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 34
       serial: 88:53:2e:96:84:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-37-generic firmware=18.168.6.1 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:37 memory:c0600000-c0601fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```

cat /ect/network/interfaces:

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by leunam12 on 2017-10-16
Bad network card?

---

### Post by jeremy31 on 2017-10-16
Moved to networking
What happens when you
```
sudo modprobe -v r8169
```

---

### Post by langendoerfer on 2017-10-16
when I boot into windows 7 it recognizes the wired connection no problem.

---

### Post by langendoerfer on 2017-10-16
sudo modprobe -v r8169

```

insmod /lib/modules/4.10.0-37-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/4.10.0-37-generic/kernel/drivers/net/ethernet/realtek/r8169.ko 

```

---

### Post by praseodym on 2017-10-16
Change the driver:
```

sudo apt-get install r8168-dkms
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by ajgreeny on 2017-10-16
Can you ping your router, if you have one?

The router's IP to ping is usually noted on the router itself, on a label, but is usually 192.168.1.1 or 192.186.0.1

---

### Post by langendoerfer on 2017-10-16
Success! After replacing the driver and a reboot I'm now showing a "wired" field in the network manager and LAN is recognized when plugged in. Thank you all for the help this was driving me nuts!

---

### Post by ajgreeny on 2017-10-16
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

