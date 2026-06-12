---
title: "USB Wifi Dongle : Cannot get Wifi Working"
date: 2018-12-16
forum: Networking &amp; Wireless
---

### Post by Scot_McKelvie on 2018-12-16
Hello,

I'd be very very grateful of some help please. The network card on my motherboard became unreliable and as a result I have bought a USB Wife Dongle ([https://www.amazon.co.uk/gp/product/B079LYDWCC/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B079LYDWCC/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)) instead. However, for the life of me I cannot get this to work...please help. I've spent probably a day on this and below I have hopefully captured the more useful information. 

```

lshw -C network
  *-network                 
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:f7c00000-f7c07fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.2
       logical name: wlxbcec23c367e1
       serial: bc:ec:23:c3:67:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88x2bu multicast=yes wireless=unassociated

rfkill list
0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

nmcli -f all dev show wlxbcec23c367e1
GENERAL.DEVICE:                         wlxbcec23c367e1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB3.0 802.11ac 1200M Adapter
GENERAL.DRIVER:                         rtl88x2bu
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         BC:EC:23:C3:67:E1
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/net/wlxbcec23c367e1
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


```


From above you can see that the USB network is disabled. However, If I enable the network using the command below then it makes no difference.

```
sudo ifconfig wlxbcec23c367e1 up
```

Below  is the same info that I detailed above after enabling the network. Note. Doing a diff between the details above and the details below yields no differences, apart from the the "*-network" is no longer DISABLED.

```

lshw -C network
  *-network                 
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:f7c00000-f7c07fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.2
       logical name: wlxbcec23c367e1
       serial: bc:ec:23:c3:67:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88x2bu multicast=yes wireless=unassociated

rfkill list
0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

nmcli -f all dev show wlxbcec23c367e1
GENERAL.DEVICE:                         wlxbcec23c367e1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB3.0 802.11ac 1200M Adapter
GENERAL.DRIVER:                         rtl88x2bu
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         BC:EC:23:C3:67:E1
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/net/wlxbcec23c367e1
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

```

Here also are a couple of screen grabs that may also help:

[ATTACH=CONFIG]281937[/ATTACH]

[ATTACH=CONFIG]281938[/ATTACH]

Thanks in advance for any help as I am well and truly stuck!

---

### Post by chili555 on 2018-12-16
Why wouldn't you prefer to use the internal Broadcom device?

May we see:```
lsmod | grep dell
```

---

### Post by Scot_McKelvie on 2018-12-16
@chilli555, firstly thanks for your reply.
> Why wouldn't you prefer to use the internal Broadcom device? I would, but it has been on its way out for a while now. Over the last couple of month the performance/stability has been dropping and dropping. I swapped to a wired connection and it has also now given up the ghost, hence the USB Wifi Dongle.
> May we see:

```

lsmod | grep dell

dell_smm_hwmon         16384  0
dell_laptop            20480  0
dell_wmi               16384  0
dell_smbios            24576  2 dell_wmi,dell_laptop
dcdbas                 16384  1 dell_smbios
sparse_keymap          16384  1 dell_wmi
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios
dell_rbtn              16384  0
wmi                    24576  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  45056  3 dell_wmi,dell_laptop,i915

```

---

### Post by jeremy31 on 2018-12-16
What model Dell?

---

### Post by chili555 on 2018-12-16
Please try from the terminal:```
sudo -i
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist dell-rbtn"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

### Post by Scot_McKelvie on 2018-12-16
Chill555, if you weren't in another continent I'd come and give you a big fat kiss. Fully working. Thank you very much indeed! I spent a long time on that and you got there very, very quickly! Greatly appreciated!
@jeremy31, > What model Dell? It is an Inspiron 17, 5000 series. Quite an old machine but good for my son and homework.
Not sure if I have said thanks yet....but thanks again.
Scot

---

### Post by chili555 on 2018-12-17
> Fully working. Thank you very much indeed! Awesome! Glad it's working. Have fun!

---

