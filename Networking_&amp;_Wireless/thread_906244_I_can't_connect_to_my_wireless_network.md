---
title: "I can't connect to my wireless network"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Janjaya on 2008-08-31
Hello

I've tried to fix my wireless connection myself. I've tried this guide: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

It was working fine until I got to '1.  Validate you don't have loaded' in [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt), got 'ERROR module ****** does not exist'.

So far it seems like I can locate wireless networks, but I can't connect them. I tried to use Wicd, but I've removed it now - could connect with a wire on Wicd, but not the wireless. I think I've NM (Network manager) now. I'm a newbeginner in Ubuntu, so please write to me step by step text - so I can follow your toughts. Thanks for any anwers.

**Computer:** HP Pavilion dv6014ea

'iwlist scan' result:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 02 - Address: 00:02:CF:67:FC:B0
                    ESSID:"privat4987pen"
                    Mode:Master
                    Channel:13
                    Frequency:2.472 GHz
                    Quality=76/100  Signal level=-57 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001324c8321cf

```


'lshw -C Network' result:

```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:c3:c0:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

'cat /etc/modprobe.d/blacklist' result:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

[Added these myself]:
blacklist b43
blacklist b43legacy
blacklist ssb
```

'lspci -nn | grep -i broadcom' result:


```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

---

### Post by Janjaya on 2008-08-31
I can confirm that my wire connection is working. That's a good thing :)

---

### Post by Janjaya on 2008-08-31
Anyone? :(

---

