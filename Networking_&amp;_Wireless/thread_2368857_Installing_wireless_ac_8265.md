---
title: "Installing wireless ac 8265"
date: 2017-08-16
forum: Networking &amp; Wireless
---

### Post by simoncks1994 on 2017-08-16
Hi everyone,

I am using Ubuntu 16.04 on Lenovo T470. After unsuccessful debugging, the default wireless-bluetooth card is now replaced by Intel Wireless AC8265 to gain better support. However, I am new to installing wireless device driver. I placed the driver downloaded from [here]("https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html"), to /lib/firmware and it did not work. A list of command output is attached.

```
uname -r
4.8.0-58-generic

```

```
sudo lshw -C netowork 
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ec100000-ec101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 54:e1:ad:1f:de:57
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:122 memory:ec200000-ec21ffff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: ham0
       serial: 7a:79:19:2b:37:e0
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full ip=25.43.55.224 link=yes multicast=yes port=twisted pair speed=10Mbit/s
```

```
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:5904] (rev 02)
    Subsystem: Lenovo Device [17aa:2245]
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5916] (rev 02)
    Subsystem: Lenovo Device [17aa:2245]
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP USB 3.0 xHCI Controller [17aa:2245]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP Thermal subsystem [17aa:2245]
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI [8086:9d3a] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP CSME HECI [17aa:2245]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d10] (rev f1)
    Kernel driver in use: pcieport
00:1c.6 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #7 [8086:9d16] (rev f1)
    Kernel driver in use: pcieport
00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 [8086:9d18] (rev f1)
    Kernel driver in use: pcieport
00:1d.2 PCI bridge [0604]: Intel Corporation Device [8086:9d1a] (rev f1)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d58] (rev 21)
    Subsystem: Lenovo Device [17aa:2245]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP PMC [17aa:2245]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
    Subsystem: Lenovo Device [17aa:2245]
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem: Lenovo Sunrise Point-LP SMBus [17aa:2245]
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-V [17aa:2245]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
04:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 50)
    Subsystem: Intel Corporation Device [8086:0050]
3e:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0115] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: nvme
    Kernel modules: nvme
```

Would anyone kindly offer a more solution?

Thanks in advance.

---

### Post by shridhar-kapshikar on 2017-08-16
Usually, you have to untar the driver bundle and execute the install.sh file from that bundle. Do you find any file with such name inside the bundle?

---

### Post by praseodym on 2017-08-16
Did you install
```

sudo apt-get install linux-image-extra-$(uname -r)
``` Driver iwlwifi should work with that. BIOS is up to date?

Edit: Firmware update via
```

sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by simoncks1994 on 2017-08-16
According to the link (downloading firmware), I do not need bash file.

> [COLOR=#555555][FONT=intel-clear]To install firmware:[/FONT][/COLOR]
[LIST=1]
[*]Copy the files into the distribution-specific firmware directory, /lib/firmware.
[*]If the directory does not work, consult your distribution documentation.
[*]If you configure the kernel yourself, make sure firmware loading is enabled.
[/LIST]


I did place the files into /lib/firmware but it didn't work.

---

### Post by simoncks1994 on 2017-08-16
Thanks praseodym. Now it is working properly. :D

---

### Post by praseodym on 2017-08-16
Driver? Firmware? Both?

---

### Post by vocx on 2017-08-16
> **simoncks1994 said:**
> According to the link (downloading firmware), I do not need bash file.

I did place the files into /lib/firmware but it didn't work.
Please understand that just unpacking things in the "/lib/firmware" directory is not the normal way of "installing" new drivers. You were probably following some guide, but you probably did not understand everything there. So don't try to do this regularly if you have problems in the future.

Basically, your laptop, as well as many other Lenovo laptops, has the AC8265 wireless card. This card works with the "iwlwifi" kernel driver, which is normally included in your system. Then, praseodym suggested installing the extra kernel modules and a newer firmware for that driver. For this case, installing the newer firmware may have been the solution.

> **praseodym said:**
> Did you install
```

sudo apt-get install linux-image-extra-$(uname -r)
``` Driver iwlwifi should work with that. BIOS is up to date?

Edit: Firmware update via
```

sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

