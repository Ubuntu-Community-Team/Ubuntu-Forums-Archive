---
title: "Help getting WiFi working on an Asus Laptop running Ubuntu 13.04"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by WhiskeynBeer on 2014-02-07
Hello anybody looking to give me a hand, just wanted to thank you in advance, heres some information on my system

Machine Info: Asus U56E Intel i5 2430M @2.4 Ghz x 4

Wireless Info:

```
Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)

 iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```


modules: wimax                  34760  1 i2400m

Kernal Boot Messages:

```
[   14.132664] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   14.146780] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.146784] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.146785] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.146787] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   14.146788] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   14.146790] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   14.146851] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   14.159522] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```

Network Config:
```

 description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:60:fe:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:c0:dc:1a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
      configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:54 memory:dd400000-dd43ffff ioport:a000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 64:d4:da:5f:6f:ac
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no

[   17.632247] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.632396] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   17.911636] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.911795] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0

```

Kernal Architecture: 3.8.0-29-generic x86_64

Some of the returns from the commands were rather long so I tried to skim through and pick out the network stuff,  if I left anything out please let me know and i can get akk of the information.

Once again thank you in advance!

---

### Post by Bucky Ball on 2014-02-07
```
*-network
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 64:d4:da:5f:6f:ac
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no
```

This is a wireless USB dongle? Take it out. Trying to run two wireless devices will make it hard, if not impossible, to get the Intel up. That is possibly what is preventing it working now.

Most Intel wireless works out of the box so may be getting blocked by the confusion created by the other device. If the USB wireless is working it will probably keep the Intel switched off, or at least not connected.

---

### Post by WhiskeynBeer on 2014-02-08
I do not have a usb dongle on this machine, only thing connected is an ethernet to get help with the wifi

---

### Post by praseodym on 2014-02-08
Deactivate the N-mode of the driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```

---

### Post by WhiskeynBeer on 2014-02-08
```
jcharb03@jcharb03-U56E:~$ echo "options iwlwifi 11n_disable=1"
options iwlwifi 11n_disable=1
jcharb03@jcharb03-U56E:~$ sudo modprobe -rfv iwlwifi
[sudo] password for jcharb03: 
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 1: ignoring bad line starting with 'sudo'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 2: ignoring bad line starting with 'sudo'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 3: ignoring bad line starting with 'sudo'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 4: ignoring bad line starting with 'grep'
FATAL: Module iwlwifi is in use.
```

this was the response in the terminal

---

### Post by praseodym on 2014-02-08
Reboot then

---

### Post by mörgæs on 2014-02-08
Slightly off topic: 13.04 is out of support. You will safe yourself trouble by installing 13.10, not the least regarding security issues.

---

### Post by WhiskeynBeer on 2014-02-08
ok thanks, rebooting didnt work gave me the same errors, but im gonna update to 13.10

---

### Post by WhiskeynBeer on 2014-02-08
Finished updating to 13.10, and the wifi fixed itself, a little strange to me since ive had 13.00 with no wifi and updating to 13.04 didnt fix the wifi.  Nonetheless thanks for your help guys!

---

### Post by Bucky Ball on 2014-02-08
Please mark thread as 'solved' to help others. 

Enjoy!

---

