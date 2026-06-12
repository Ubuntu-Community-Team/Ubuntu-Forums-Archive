---
title: "Wireless drivers for Mediatek MT7630e on ASUS X555LB with Ubuntu 15.10"
date: 2015-10-23
forum: Networking &amp; Wireless
---

### Post by aljaz3 on 2015-10-23
Recently i've installed Ubuntu 15.10 and so far i failed to get the wireless drivers running. 
I have ASUS X555LB with Mediatek MT7630e 802.11bgn Wireless Network Adapter. So far i tried all the drivers i could find and none of them works. Another information that may be usseful, previously i had Ubuntu 14.04 LTS which started freezing randomly and i decided to upgrade.
The same problem also appeared on Ubuntu 14.04 LTS, most of drivers didn't work for that version also. Most of drivers appeared to work for older version of Kernel, but after few days of googling i managed to fix it with [https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)
I've reached a dead end and i'm looking forward to a sollution, and in advanced thank you for your time.

On other but reports similar to mine people found following informations usseful.
```
aljazm@aljazm-X555LB:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
```
aljazm@aljazm-X555LB:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.
```
```
aljazm@aljazm-X555LB:~$ uname -a
Linux aljazm-X555LB 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


```
```
aljazm@aljazm-X555LB:~$ sudo lshw -C network;
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 1c:b7:2c:93:3e:6d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.235 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:48 ioport:e000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
  *-network UNCLAIMED
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7100000-f71fffff


```
[ATTACH]265129[/ATTACH]

---

### Post by chili555 on 2015-10-23
With a temporary working internet connection by ethernet, tether or whatever means possible, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential git
```One or more may be already installed, please continue:```
git clone https://github.com/benjarobin/MT7630E.git
cd MT7630E/rt2x00
make
sudo make install
sudo modprobe mt7630e
```Your wireless should now be working.

You will have built the driver for your currently running kernel version only. When Update Manager installs a later kernel version, also known as linux-image, after the requested reboot, recompile:```
cd MT7630E/rt2x00
make clean
make
sudo make install
sudo modprobe mt7630e
```Please retain the file and these instructions for that time.

The driver may require firmware. If your wireless device doesn't work as expected, check the log for clues:```
dmesg | grep mt76
```

---

### Post by aljaz3 on 2015-10-24
First off all thank you for your time.
I got stuck after making file in MT7630E/rt2x00. Command make succeed. File called install doesn't exist. Am i missing something?
```
aljazm@aljazm-X555LB:~/Downloads/MT7630E/rt2x00$ sudo make install
make: *** No rule to make target 'install'.  Stop.
```

I appreciate your help.

---

### Post by praseodym on 2015-10-24
Please show the outputs of:
```

make clean
make
```

---

### Post by aljaz3 on 2015-10-24
Here you go.
```
aljazm@aljazm-X555LB:~/Downloads/MT7630E/rt2x00$ make clean
make -C /lib/modules/`uname -r`/build M=/home/aljazm/Downloads/MT7630E/rt2x00 clean
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic'
  CLEAN   /home/aljazm/Downloads/MT7630E/rt2x00/.tmp_versions
  CLEAN   /home/aljazm/Downloads/MT7630E/rt2x00/Module.symvers
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'


```
```
aljazm@aljazm-X555LB:~/Downloads/MT7630E/rt2x00$ make
make -C /lib/modules/`uname -r`/build M=/home/aljazm/Downloads/MT7630E/rt2x00 modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic'
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00dev.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00mac.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00config.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00queue.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00link.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/mt_linux.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00crypto.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00firmware.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00leds.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00mmio.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2x00pci.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2800lib.o
  CC [M]  /home/aljazm/Downloads/MT7630E/rt2x00/rt2800pci.o
  LD [M]  /home/aljazm/Downloads/MT7630E/rt2x00/mt7630e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/aljazm/Downloads/MT7630E/rt2x00/mt7630e.mod.o
  LD [M]  /home/aljazm/Downloads/MT7630E/rt2x00/mt7630e.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
```

Thank you

---

### Post by praseodym on 2015-10-24
Hm, maybe it doesn't work with kernel 4.2?! Try now
```

sudo make install
```

---

### Post by aljaz3 on 2015-10-24
Still doesn't work, output is same as before.
```
aljazm@aljazm-X555LB:~/Downloads/MT7630E/rt2x00$ sudo make install
make: *** No rule to make target 'install'.  Stop.


```

---

### Post by praseodym on 2015-10-24
Lets try this one instead, it compiles with kernel 3.16 here:
```

sudo apt-get install dkms
git clone https://github.com/kuba-moo/mt7630e
cd mt7630e
make
sudo make install
```

---

### Post by aljaz3 on 2015-10-24
Unfortunately this one fails at make
```
aljazm@aljazm-X555LB:~/Downloads/mt7630e$ make
make -C /lib/modules/`uname -r`/build M=/home/aljazm/Downloads/mt7630e/rt2x00 modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic'
  CC [M]  /home/aljazm/Downloads/mt7630e/rt2x00/rt2x00dev.o
  CC [M]  /home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.o
/home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.c: In function ‘rt2x00mac_configure_filter’:
/home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.c:359:6: error: ‘FIF_PROMISC_IN_BSS’ undeclared (first use in this function)
      FIF_PROMISC_IN_BSS;
      ^
/home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.c:359:6: note: each undeclared identifier is reported only once for each function it appears in
scripts/Makefile.build:258: recipe for target '/home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.o' failed
make[2]: *** [/home/aljazm/Downloads/mt7630e/rt2x00/rt2x00mac.o] Error 1
Makefile:1398: recipe for target '_module_/home/aljazm/Downloads/mt7630e/rt2x00' failed
make[1]: *** [_module_/home/aljazm/Downloads/mt7630e/rt2x00] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
Makefile:7: recipe for target 'all' failed
make: *** [all] Error 2


```

---

### Post by praseodym on 2015-10-24
Obviously, it does not work with this kernel. Try 14.04 instead.

---

### Post by dcialdella on 2015-10-24
I have an ASUS TP300lA Transformer and upgrade from 15.04 to 15.10 too.

the same issue with the same wifi card   MT7630E

the old solution for 15.04 don't work in 15.10
(download from git, make , make install)


still waiting for a valid source to compile.

---

### Post by aljaz3 on 2015-10-25
Thanks to lord and savior, master neurobin we now have a working driver for latest kernel. Here's the link [https://github.com/neurobin/MT7630E/](https://github.com/neurobin/MT7630E/). Oh and how do i tag this post as solved?

---

### Post by praseodym on 2015-10-25
Thanks for the information. For those not familiar, here is the instruction manual:
```

sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
git clone https://github.com/neurobin/MT7630E/
cd MT7630E/
make
sudo make install
```
Reboot.

It compiles here with kernel 3.16.

---

