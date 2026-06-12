---
title: "Realtek LAN woes on MSI Z87M-G43"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by pmackinney on 2014-02-16
Like many, I have issues with an onboard Realtek LAN adapter, unlike many the Realtek proprietary driver does nothing for me. I'm on my way to buy an Intel PCI-E adapter since all the others seem to use the Realtek chips. It would be nice to get the onboard working, of course. Any advice or comments appreciated.

Sanity checks: The LAN cable is good, and the host that I ping at the end is good. I have tried an enormous variety of suggestions from the net: toggling different BIOS settings (Intel Smart connect Technology, Resume by PCI-E Device), turning it off and pulling the power cord for 10 seconds, etc.

One other issue with this system: It won't boot without adding apci=off to the grub kernel line (for booting Live CD, install, or installed system).

src/r8168-8.037.00/log.txt, after disabling r8169 driver, downloading from Realtek and running autorun.sh as root:
```
-------------------------------
Sun Feb 16 10:37:09 PST 2014
make -C src/ clean
make[1]: Entering directory `/root/src/r8168-8.037.00/src'
make -C /lib/modules/3.11.0-15-generic/build SUBDIRS=/root/src/r8168-8.037.00/src clean
make[2]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make[1]: Leaving directory `/root/src/r8168-8.037.00/src'
make -C src/ modules
make[1]: Entering directory `/root/src/r8168-8.037.00/src'
make -C /lib/modules/3.11.0-15-generic/build SUBDIRS=/root/src/r8168-8.037.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /root/src/r8168-8.037.00/src/r8168_n.o
  CC [M]  /root/src/r8168-8.037.00/src/r8168_asf.o
  CC [M]  /root/src/r8168-8.037.00/src/rtl_eeprom.o
  CC [M]  /root/src/r8168-8.037.00/src/rtltool.o
  LD [M]  /root/src/r8168-8.037.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/src/r8168-8.037.00/src/r8168.mod.o
  LD [M]  /root/src/r8168-8.037.00/src/r8168.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make[1]: Leaving directory `/root/src/r8168-8.037.00/src'
make -C src/ install
make[1]: Entering directory `/root/src/r8168-8.037.00/src'
make -C /lib/modules/3.11.0-15-generic/build SUBDIRS=/root/src/r8168-8.037.00/src INSTALL_MOD_DIR=kernel/drivers/net/ethernet/realtek modules_install
make[2]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  INSTALL /root/src/r8168-8.037.00/src/r8168.ko
  DEPMOD  3.11.0-15-generic
make[2]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make[1]: Leaving directory `/root/src/r8168-8.037.00/src'
r8168-8.037.00
```

Typical diagnostics
```
root@ws:~# lsmod | grep ^r816
r8168                 261399  0 

root@ws:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

root@ws:~# mii-tool eth0
eth0: negotiated 1000baseT-FD flow-control, link ok

root@ws:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr d4:3d:7e:ed:08:d6  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe08::6d3d:7eff:feed:08d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:42 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x6000 
```
At this point it can ping itself at IP address 192.168.1.16, but nothing else on the network.

---

### Post by praseodym on 2014-02-16
Uninstall it and try this one with dkms```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/14/03/3005217-r8168-dkms-8.037.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.037.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.037.00
sudo dkms build -m r8168-dkms -v 8.037.00
sudo dkms install -m r8168-dkms -v 8.037.00
sudo depmod -a
sudo update-initramfs -u 
```
Reboot.

---

