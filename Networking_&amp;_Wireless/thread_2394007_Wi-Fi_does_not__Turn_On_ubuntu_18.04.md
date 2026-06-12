---
title: "Wi-Fi does not  Turn On ubuntu 18.04"
date: 2018-06-11
forum: Networking &amp; Wireless
---

### Post by aiknr on 2018-06-11
PCI , USB WiFi neither is turning on. PCI Wi-Fi Device: RT3290 Wireless 802.11n 1T/1R PCIe, USB WiFi Device: TP-LINK TL-WN722N (Device ID: 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n)
[ATTACH=CONFIG]280082[/ATTACH] Like in the picture Clicking on Turn On does not do anything. I've also tried in the Wi-Fi settings.
```
# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```
rfkill shows USB wifi is not blocked.

```

# lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: f8:a9:63:91:7f:05
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:b2600000-b2600fff memory:b2400000-b2403fff
  *-network DISABLED
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlo1
       version: 00
       serial: 00:71:cc:5b:a4:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.15.0-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:b2510000-b251ffff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:3
       logical name: wlxf8d111b4cda3
       serial: f8:d1:11:b4:cd:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=4.15.0-22-generic firmware=1.4 link=no multicast=yes wireless=IEEE 802.11

```

From here using the logical name of the USB Wi-Fi when I ran ```
# ifconfig wlxf8d111b4cda3 up
``` the green light on the USB Wi-Fi lights up but nothing else happens. 
ath9k_htc Firmwire is installed.
I've also tried installing WICD while removing the network-manager, but it didn't work. But on ubuntu 16.04, using WICD I could run the USB Wi-Fi.

---

### Post by chili555 on 2018-06-11
> 0: phy0: Wireless LAN
    Soft blocked: no
   [COLOR="#FF0000"] Hard blocked: yes[/COLOR]
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: noWhat's the position of the wireless or airplane mode switch on your laptop? Until you find it and switch it, the wireless will probably not ever work.

---

### Post by aiknr on 2018-06-11
yes I tried that also. nothing happens. f12 is the wireless enable key.(tried f12 and fn+f12 and there is no option in BIOS too)

---

### Post by chili555 on 2018-06-11
What brand and model is the laptop? Please run and post:```
lsusb
```

---

### Post by aiknr on 2018-06-11
hp 14-r009tu
```
# lsusb
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 002 Device 009: ID 19d2:0039 ZTE WCDMA Technologies MSM 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by chili555 on 2018-06-11
My apologies; I meant to ask about: ```
lsmod
```Since we know it's an HP, then let's see:```
lsmod | grep hp
```

---

### Post by aiknr on 2018-06-11
```

# lsmod | grep hp
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
shpchp                 36864  0
hp_wireless            16384  0
wmi                    24576  2 wmi_bmof,hp_wmi

```

---

### Post by chili555 on 2018-06-11
The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all
```

Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the *wrong *sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

The only good news here is that I notice that the USB wireless appears to NOT be blocked. Let's try blacklisting the driver for the internal:```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and show us:```
iwconfig
dmesg | grep ath
```

---

### Post by aiknr on 2018-06-11
First, tried removing the helper module hp_wmi followed by switching the wireless on with the key combination, but nothing happened.
Next, as currently I do not have the right tools, couldn't tape of the pin 20.
Finally after blacklisting the driver for the internal when I rebooted,  the USB Wi-Fi green LED lit up :D :D , and everything is fine now except the wireless control button. 
Thank you very much for helping. :D :D
```
$ iwconfig
wlxf8d111b4cda3  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp8s0    no wireless extensions.

lo        no wireless extensions.

ppp0      no wireless extensions.


```

```
$ dmesg | grep ath
[   10.515805] usb 2-3: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[   10.515871] usbcore: registered new interface driver ath9k_htc
[   10.961949] usb 2-3: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[   11.213415] ath9k_htc 2-3:1.0: ath9k_htc: HTC initialized with 33 credits
[   11.477540] ath9k_htc 2-3:1.0: ath9k_htc: FW Version: 1.4
[   11.477543] ath9k_htc 2-3:1.0: FW RMW support: On
[   11.477544] ath: EEPROM regdomain: 0x809c
[   11.477545] ath: EEPROM indicates we should expect a country code
[   11.477546] ath: doing EEPROM country->regdmn map search
[   11.477547] ath: country maps to regdmn code: 0x52
[   11.477548] ath: Country alpha2 being used: CN
[   11.477549] ath: Regpair used: 0x52
[   12.638419] ath9k_htc 2-3:1.0 wlxf8d111b4cda3: renamed from wlan0
```

---

### Post by chili555 on 2018-06-11
Glad it's working. Have fun!

---

