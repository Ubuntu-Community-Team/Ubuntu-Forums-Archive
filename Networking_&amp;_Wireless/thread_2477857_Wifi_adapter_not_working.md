---
title: "Wifi adapter not working"
date: 2022-08-09
forum: Networking &amp; Wireless
---

### Post by g2ragrawal on 2022-08-09
Hi all,

I have a laptop **hp-15ay503tx** with os **Ubuntu 20.04.4 LTS** and kernel **5.15.0-41-generic**.

My inbuilt wifi lan card was giving a range of 3-4 meters and if I create a hotspot it was giving a maximum 100kBps speed. I am using this laptop for the last 5.5 years and wifi card worked properly till the last November. (I tried installing windows and was having the same issue.)
so, to overcome the wifi issue I bought zebronics USB150wf1 USB wifi adapter but it is not working. 

I downloaded the driver** RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105** from the website and tried to install it with the provided install.sh file but it gives an error and also tried to build from the following git repo [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver) . it was built successfully but when I run am_i_using_this_driver.sh it says no.

below are some of output that might be use full

rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

sudo lshw -c network
```

[sudo] password for jeet: 
  *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 07
       serial: 30:e1:71:15:19:7c
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-41-generic firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:a1200000-a1200fff memory:a1000000-a1003fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 00
       serial: 58:00:e3:81:31:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=5.15.0-41-generic firmware=N/A ip=192.168.77.30 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 ioport:3000(size=256) memory:a1100000-a1103fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: virbr0-nic
       serial: 52:54:00:47:d5:b4
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 4
       bus info: usb@1:2
       logical name: wlx00e04c818802
       serial: 00:e0:4c:81:88:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu driverversion=5.15.0-41-generic multicast=yes wireless=unassociated

```

iwconfig
```

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlo1      IEEE 802.11  ESSID:"jeet"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: BA:BA:1A:A7:0E:F9   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:210   Missed beacon:0

virbr0    no wireless extensions.

virbr0-nic  no wireless extensions.

wlx00e04c818802  unassociated  ESSID:""  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lsusb
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b56c Chicony Electronics Co., Ltd HP TrueVision HD
Bus 001 Device 003: ID 0bda:b008 Realtek Semiconductor Corp. Bluetooth Radio 
Bus 001 Device 002: ID 0bda:f179 Realtek Semiconductor Corp. 802.11n    //wifi adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:81ec]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Sanji2 
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be

```

nmcli -f all dev show wlx00e04c818802
```

GENERAL.DEVICE:                         wlx00e04c818802
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices>
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        802.11n
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 5.15.0-41-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         00:E0:4C:81:88:02
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/us>
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
```

[IMG]https://imgur.com/gDA8qvH[/IMG]

---

### Post by chili555 on 2022-08-09
> worked properly till the last November. (I tried installing windows and was having the same issue.)This strongly suggests a hardware problem, so let's set the internal device aside and concentrate on the USB. In order to prevent any conflicts, let's blacklist the internal device:```
sudo -i
modprobe -r rtl8723be
echo "blacklist rtl8723be"  >>  /etc/modprobe.d/blacklist.conf
exit

```Now, as to the USB, it appears that the built-in kernel driver r8188eu is in use. It has a very bad reputation. I recommend a better driver in the alternative. Please follow the process I've described here: [https://askubuntu.com/questions/1415272/driver-installation-of-r8188eu-or-rtl8188ftv-not-sure-which-one-to-install/1416261#1416261](https://askubuntu.com/questions/1415272/driver-installation-of-r8188eu-or-rtl8188ftv-not-sure-which-one-to-install/1416261#1416261)

---

### Post by howefield on 2022-08-09
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by g2ragrawal on 2022-08-11
> **chili555 said:**
> This strongly suggests a hardware problem, so let's set the internal device aside and concentrate on the USB. In order to prevent any conflicts, let's blacklist the internal device:```
sudo -i
modprobe -r rtl8723be
echo "blacklist rtl8723be"  >>  /etc/modprobe.d/blacklist.conf
exit

```Now, as to the USB, it appears that the built-in kernel driver r8188eu is in use. It has a very bad reputation. I recommend a better driver in the alternative. Please follow the process I've described here: [https://askubuntu.com/questions/1415272/driver-installation-of-r8188eu-or-rtl8188ftv-not-sure-which-one-to-install/1416261#1416261](https://askubuntu.com/questions/1415272/driver-installation-of-r8188eu-or-rtl8188ftv-not-sure-which-one-to-install/1416261#1416261)

thank you worked. I had installed rtl8188fu drivers but didn't blacklist r8188eu.

---

### Post by chili555 on 2022-08-11
> **g2ragrawal said:**
> thank you worked. I had installed rtl8188fu drivers but didn't blacklist r8188eu.Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

