---
title: "Can't get D-LINK DWL-122 (prism2_usb) to work on Ubuntu 16.04 LTS"
date: 2017-09-25
forum: Networking &amp; Wireless
---

### Post by inte2 on 2017-09-25
Hello,

I have an older D-Link DWL-122 USB-Wifi adapter which I want to use on Ubuntu 16.04 to connect to a local AP on 2397 Mhz.
Even though this frequency is a bit below the "normal" ISM/WiFi spectrum I was hoping this might be feasible through the prism2_usb kernel module and linux-wlan-ng firmware which is open source and can be customized.
However, I could not even get this device to work on the regular WiFi bands.
Here is what I found in the syslog:

```

Sep 25 08:58:40 ThinkPad-X200 kernel: [44163.630438] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): prism2_usb: Checking for firmware prism2_ru.fw
Sep 25 08:58:40 ThinkPad-X200 wpa_supplicant[1197]: wls1: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Sep 25 08:58:40 ThinkPad-X200 kernel: [44163.894649] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): prism2_usb: prism2_ru.fw will be processed, size 90662
Sep 25 08:58:40 ThinkPad-X200 systemd[1]: Starting Load/Save RF Kill Switch Status...
Sep 25 08:58:42 ThinkPad-X200 kernel: [44165.916047] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): CTLX[1] error: state(Request failed)
Sep 25 08:58:45 ThinkPad-X200 kernel: [44168.956075] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): CTLX[1] error: state(Request failed)
Sep 25 08:58:45 ThinkPad-X200 kernel: [44168.956080] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): cmd_initialize() failed on two attempts, results -5 and -5
Sep 25 08:58:45 ThinkPad-X200 kernel: [44168.957283] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): hfa384x_drvr_start() failed,result=-5
Sep 25 08:58:45 ThinkPad-X200 kernel: [44168.957287] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): PDA may only be read in the fwload state.
Sep 25 08:58:45 ThinkPad-X200 kernel: [44168.957289] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): load_cardpda failed, exiting.
Sep 25 08:58:47 ThinkPad-X200 kernel: [44170.972056] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): CTLX[1] error: state(Request failed)
Sep 25 08:58:50 ThinkPad-X200 kernel: [44174.012116] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): CTLX[1] error: state(Request failed)
Sep 25 08:58:50 ThinkPad-X200 kernel: [44174.012120] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): cmd_initialize() failed on two attempts, results -5 and -5
Sep 25 08:58:50 ThinkPad-X200 kernel: [44174.013393] prism2_usb 6-2:1.0 (unnamed net_device) (uninitialized): hfa384x_drvr_start() failed,result=-5

```

Is the prism2 driver broken?
Thank you in advance!

---

### Post by wildmanne39 on 2017-09-25
If you are in the United States you will not be able to use that channel because it is not a supported channel or frequency. I believe it is not support anywhere.

---

### Post by wildmanne39 on 2017-09-25
*Thread moved to **Networking & Wireless for better fit**.*

---

### Post by inte2 on 2017-09-26
Thank you for your replies.
This is what the script finds about this particular network interface:

```
GENERAL.DEVICE:                         wlp0s26f0u1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         2001
GENERAL.PRODUCT:                        3700
GENERAL.DRIVER:                         prism2_usb
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/net/wlp0s26f0u1
GENERAL.IP-IFACE:                       
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    no
WIFI-PROPERTIES.WPA2:                   no
WIFI-PROPERTIES.TKIP:                   no
WIFI-PROPERTIES.CCMP:                   no
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no

wlp0s26f0u1  14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

wlp0s26f0u1  Interface doesn't support scanning : Network is down


22226.103531] prism2_usb 3-1:1.0 (unnamed net_device) (uninitialized): prism2_usb: Checking for firmware prism2_ru.fw
[22236.411332] prism2_usb 3-1:1.0 wlp0s26f0u1: renamed from wlan0
[22238.940090] prism2_usb 3-1:1.0 wlp0s26f0u1: CTLX[1] error: state(Request failed) (repeated 2 times)
[22241.980042] prism2_usb 3-1:1.0 wlp0s26f0u1: cmd_initialize() failed on two attempts, results -5 and -5
[22241.981674] prism2_usb 3-1:1.0 wlp0s26f0u1: hfa384x_drvr_start() failed,result=-5
[22242.409835] IPv6: ADDRCONF(NETDEV_UP): wlp0s26f0u1: link is not ready

I understand this card does not support the frequency I'm trying to configure out of the box. I was only hoping I might be able to modify the driver later.
However, currently I cannot even configure this card for the regular ISM/WiFi band.
```

---

### Post by wildmanne39 on 2017-09-26
Is this a 5ghz frequency you are trying to use?

What Country are you in?

We need to see the rest of the file created by the script to even have a chance of helping.

---

### Post by inte2 on 2017-09-26
2397 Mhz is a bit below the standard ISM 2,4 Ghz band. I'm located in Germany.
However, this adapter is not even working on a supported frequency at the moment.
The output of the wireless script is a bit too large to attach it directly since it contains all network adapters...
I tried to remove as much unneccessary data from the output as possible but since it was still too big I eventually compressed it.
Thanks in advance!

[ATTACH]276856[/ATTACH]

---

### Post by inte2 on 2017-09-28
No more replies, I would therefore assume support for prism2_usb is deprecated/can be considered as broken in current Ubuntu releases an will not be fixed since it is old hardware?
Sad to here about that :(

---

### Post by chili555 on 2017-09-28
> prism2_usb 3-1:1.0 (unnamed net_device) (uninitialized): prism2_usb: Checking for firmware prism2_ru.fwDo you have this on your system??```
ls /lib/firmware | grep prism
```If not, I suggest that you install it:```
sudo apt-get install prism2-usb-firmware-installer
```Reboot and tell us if there is any change.

I doubt that you will ever connect to an unlisted frequency, however.

---

### Post by inte2 on 2017-09-29
Hello again.
The firmware files are in place: prism2_ru.fw   prism2_ru.hex  

I also tried the firmware installer script from the package "linux-wlan-ng-firmware" located at /usr/bin/linux-wlan-ng-build-firmware-deb
However, this script fails since the svn it tries to access is not applicable anymore.

I thought the firmware sourcecode was available and therefore it might be possible to change the frequency to somewhere a bit outside the official ISM spectrum, like it is possible with e.g. Ubiquity hardware. I only found a description of the hex file yet, and altering this file would only switch between the US and European frequency plan, enable AP mode etc. but would not enable any additional frequency.
In either case, I can't get this card running at all. It would already be nice to use it to connect to Freifunk over a long distance (I have an external antenna).
Thank you.

---

