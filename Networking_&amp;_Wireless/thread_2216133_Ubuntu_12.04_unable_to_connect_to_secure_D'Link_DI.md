---
title: "Ubuntu 12.04 unable to connect to secure D'Link DIR-655"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by 1DoLittle on 2014-04-10
Computer: Dual boot - Windows 7 and Ubuntu 12.04
Router: D'Link DIR-655, Firmware 2.07NA
OS: Ubuntu 12.04
  1. What I cannot do: Connect to secure wireless router - signal is acknowledged (strong)
  2. What I can do: Connect to unsecured signal - both guest signal anytime and removed security mode WPA-personal
  3. Router security: Security Mode: WPA-Personal, WPA Mode Auto(WPA or WPA2)

OS: Windows 7
  1. Connects to both guest mode and secure wireless properly
  2. Speed n connection

Unable to find way to utilize router push button setup or PIN number procedure

Any suggestions?

---

### Post by varunendra on 2014-04-12
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by 1DoLittle on 2014-04-13
Varun,
Since the original post, 2 non-pae computers have had LUBUNTU installed and both login to the system properly (first try).
This computer is 64 bit and had a wireless driver added (not necessary on the 2 non-pae computers) using additional drivers from the menu. Only one wireless driver appeared on the additional drivers menu.
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux HP-Laptop 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3387]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d217 Suyin Corp. 
Bus 006 Device 002: ID 0a5c:21e3 Broadcom Corp. 

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.165
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             204.194.232.200
    DNS:             204.194.234.200

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,80:C1:6E:60:38:F0,

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

eth1      26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### lsmod #####

wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   28.623901] Bluetooth: can't load firmware, may not work correctly
[   28.782294] wl: module license 'MIXED/Proprietary' taints kernel.
[   28.801523] wl 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.801537] wl 0000:03:00.0: setting latency timer to 64
[   31.961697] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   33.898317] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   33.927069] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  669.195796] ERROR @wl_dev_intvar_get : error (-1)
[  669.195812] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############

```

Thankd for your help.

---

### Post by varunendra on 2014-04-13
I assume the new installations are also the latest supported versions of Lubuntu, using kernel 3.11.

Your above installation is an older one, which is using an older kernel despite being updated regularly.

Without going into possibly confusing details, I would suggest to purge the sta driver (that comes from "Additional Drivers") and install either the latest kernel as suggested **[here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")** (this link also explains why you still have an older kernel), or just the driver from one of the latest kernels.

If you are happy with everything else in the current installation, I would recommend you install only the driver instead of upgrading the whole enablement stack. Here's how -

[indent]**1)** Open a terminal (Ctrl-Alt-T) and install the basic requirements first -
```
sudo apt-get install linux-headers-generic build-essential
```

**2)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**3)** Right-click the downloaded package > click "Extract here".

**4)** Assuming the package has been downloaded and extracted in the "Downloads" directory within your 'Home' directory, compile and install the driver with the following commands in terminal -
```
cd Downloads/backports-3.12.8-1
make defconfig-brcmsmac
make
sudo make install
```
Watch out for errors, report back if there are any.[/indent]

If the above procedure finishes smoothly without errors, purge the sta driver -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and test the connectivity.

**PS:**
I don't understand why your **/etc/modules** file is showing so many duplicate entries of "lp" and "rtc". Although they are not related, I recommend you delete the duplicate lines. They should be listed only once.

Also, it would be a good idea to delete your current udev rules file for network rules, **_after_** purging the sta driver -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
It'll be automatically regenarated when required, with only relevant entries this time.

---

### Post by 1DoLittle on 2014-04-13
Varun,
I could not make this work, it is the same as before (works on unsecured but not on secure system. Rechecked security and both the modem and computer are set on WPA & WPA2 Personal as well as rechecking the password. Between computers and operating systems functioning on the secure wireless, of which there are 6 including windows 7, windows xp, Lubuntu.
I recorded the installation for you to read.
```

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ make defconfig-brcmsmac
Generating local configuration database from kernel ... done. 
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
#
# configuration written to .config
#
larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ 

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ make
make[5]: `conf' is up to date.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/main.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.3.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.4.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.5.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/user_namespace.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.6.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.7.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.8.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat-3.9.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/backport-3.10.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/backport-3.12.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/dma-shared-helpers.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/cordic.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/compat/crc8.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/main.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/scan.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/core.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/sprom.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/driver_chipcommon.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/driver_chipcommon_pmu.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/driver_pci.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/driver_gpio.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/host_pci.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/bcma.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/ampdu.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/antsel.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/channel.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/main.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy_shim.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/pmu.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/rate.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/stf.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/aiutils.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_cmn.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_lcn.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_n.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_lcn.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_n.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_qmath.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/dma.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/brcms_trace_events.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/debug.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/led.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/utils.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/d11.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/main.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/status.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/sta_info.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/wep.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/wpa.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/scan.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/offchannel.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/ht.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/agg-tx.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/agg-rx.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/vht.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/ibss.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/iface.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/rate.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/michael.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/tkip.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/aes_ccm.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/aes_cmac.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/cfg.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/rx.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/spectmgmt.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/tx.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/key.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/util.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/wme.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/event.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/chan.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/trace.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/mlme.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/led.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/pm.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/rc80211_minstrel_ht.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/mac80211.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/core.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/sysfs.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/radiotap.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/util.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/reg.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/scan.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/nl80211.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/mlme.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/ibss.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/sme.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/chan.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/ethtool.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/mesh.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/ap.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/trace.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/wext-compat.o
  CC [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/wext-sme.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 8 modules
  CC      /home/larry/Downloads/backports-3.12.8-1/compat/compat.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/compat/compat.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/compat/cordic.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/compat/cordic.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/compat/crc8.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/compat/crc8.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/bcma.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/bcma.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/net/mac80211/mac80211.ko
  CC      /home/larry/Downloads/backports-3.12.8-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/larry/Downloads/backports-3.12.8-1/net/wireless/cfg80211.ko
larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ 

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ sudo make install
[sudo] password for larry: 
  Building modules, stage 2.
  MODPOST 8 modules
  INSTALL /home/larry/Downloads/backports-3.12.8-1/compat/compat.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/compat/cordic.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/compat/crc8.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/drivers/bcma/bcma.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/net/mac80211/mac80211.ko
  INSTALL /home/larry/Downloads/backports-3.12.8-1/net/wireless/cfg80211.ko
  DEPMOD  3.2.0-60-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ 

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-timezonemap-1.0 gir1.2-json-1.0 dkms language-pack-kde-en kde-l10n-engb language-pack-kde-en-base gir1.2-xkl-1.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
After this operation, 4,286 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 211518 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic
larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ 

larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ sudo rm /etc/udev/rules.d/70-persistent-net.rules
larry@HP-Laptop:~/Downloads/backports-3.12.8-1$ 


```

Thanks

---

### Post by varunendra on 2014-04-13
Please post the current report of wireless_script. And if by "WPA & WPA2 Personal" you mean "WPA/WPA2" mixed mode in the router, please change it to pure WPA2 only with AES (CCMP), avoid TKIP. This has to be done in the router, not in Ubuntu (Ubuntu will automatically change to what the router offers). Reboot the router after saving any changes.

If you can access the wireless card, also check its antenna contacts to make sure they are not loose.

---

### Post by 1DoLittle on 2014-04-14
Varun,
Included are screen shots of the D'Link wireless security settings and Ubuntu settings. All the other setups work with this arrangement.
Also, included is the wireless script output.
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux HP-Laptop 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: bcma-pci-bridge

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3387]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d217 Suyin Corp. 
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 006 Device 002: ID 0a5c:21e3 Broadcom Corp. 

##### PCMCIA Card Info #####

##### rfkill #####

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.165
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             204.194.232.200
    DNS:             204.194.234.200

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,80:C1:6E:60:38:F0,

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
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

##### lsmod #####

brcmsmac              526204  0 
brcmutil               15618  1 brcmsmac
cordic                 12574  1 brcmsmac
mac80211              518012  1 brcmsmac
cfg80211              567517  2 brcmsmac,mac80211
ssb                    52752  0 
bcma                   46248  2 brcmsmac
compat                 30258  4 brcmsmac,mac80211,cfg80211,bcma

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     F6DC4BDD5BA0B6A2DD11A79
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        bcma,mac80211,compat,brcmutil,cfg80211,cordic
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/updates/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/updates/drivers/bcma/bcma.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F1741C0379D921928D81E88
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        compat
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   29.031871] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.031889] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   29.031942] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   29.031972] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   29.032089] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   29.034262] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   29.050711] bcma: bus0: Bus registered
[   30.724781] b43: disagrees about version of symbol ieee80211_get_response_rate
[   30.724794] b43: Unknown symbol ieee80211_get_response_rate (err -22)
[   30.724845] b43: disagrees about version of symbol bcma_core_disable
[   30.724849] b43: Unknown symbol bcma_core_disable (err -22)
[   30.724935] b43: disagrees about version of symbol ieee80211_free_hw
[   30.724939] b43: Unknown symbol ieee80211_free_hw (err -22)
[   30.724955] b43: disagrees about version of symbol ieee80211_alloc_hw
[   30.724959] b43: Unknown symbol ieee80211_alloc_hw (err -22)
[   30.724976] b43: disagrees about version of symbol ieee80211_register_hw
[   30.724979] b43: Unknown symbol ieee80211_register_hw (err -22)
[   30.724996] b43: disagrees about version of symbol __ieee80211_get_radio_led_name
[   30.724999] b43: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   30.725007] b43: disagrees about version of symbol ieee80211_generic_frame_duration
[   30.725011] b43: Unknown symbol ieee80211_generic_frame_duration (err -22)
[   30.725022] b43: disagrees about version of symbol ieee80211_wake_queue
[   30.725025] b43: Unknown symbol ieee80211_wake_queue (err -22)
[   30.725052] b43: disagrees about version of symbol __ieee80211_get_tx_led_name
[   30.725056] b43: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[   30.725081] b43: disagrees about version of symbol bcma_core_pll_ctl
[   30.725085] b43: Unknown symbol bcma_core_pll_ctl (err -22)
[   30.725103] b43: disagrees about version of symbol bcma_driver_unregister
[   30.725106] b43: Unknown symbol bcma_driver_unregister (err -22)
[   30.725120] b43: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   30.725124] b43: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   30.725144] b43: disagrees about version of symbol bcma_core_enable
[   30.725147] b43: Unknown symbol bcma_core_enable (err -22)
[   30.725188] b43: disagrees about version of symbol bcma_core_is_enabled
[   30.725192] b43: Unknown symbol bcma_core_is_enabled (err -22)
[   30.725202] b43: disagrees about version of symbol __ieee80211_get_rx_led_name
[   30.725206] b43: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[   30.725226] b43: disagrees about version of symbol bcma_chipco_gpio_control
[   30.725230] b43: Unknown symbol bcma_chipco_gpio_control (err -22)
[   30.725253] b43: disagrees about version of symbol ieee80211_queue_delayed_work
[   30.725257] b43: Unknown symbol ieee80211_queue_delayed_work (err -22)
[   30.725267] b43: disagrees about version of symbol ieee80211_ctstoself_get
[   30.725271] b43: Unknown symbol ieee80211_ctstoself_get (err -22)
[   30.725293] b43: disagrees about version of symbol __bcma_driver_register
[   30.725296] b43: Unknown symbol __bcma_driver_register (err -22)
[   30.725316] b43: disagrees about version of symbol bcma_core_set_clockmode
[   30.725319] b43: Unknown symbol bcma_core_set_clockmode (err -22)
[   30.725372] b43: Unknown symbol ieee80211_rx (err 0)
[   30.725399] b43: disagrees about version of symbol ieee80211_wake_queues
[   30.725403] b43: Unknown symbol ieee80211_wake_queues (err -22)
[   30.725425] b43: disagrees about version of symbol bcma_core_dma_translation
[   30.725428] b43: Unknown symbol bcma_core_dma_translation (err -22)
[   30.725461] b43: disagrees about version of symbol ieee80211_tx_status
[   30.725465] b43: Unknown symbol ieee80211_tx_status (err -22)
[   30.725472] b43: disagrees about version of symbol ieee80211_stop_queue
[   30.725475] b43: Unknown symbol ieee80211_stop_queue (err -22)
[   30.725501] b43: disagrees about version of symbol __ieee80211_get_assoc_led_name
[   30.725505] b43: Unknown symbol __ieee80211_get_assoc_led_name (err -22)
[   30.725516] b43: disagrees about version of symbol wiphy_rfkill_start_polling
[   30.725520] b43: Unknown symbol wiphy_rfkill_start_polling (err -22)
[   30.725545] b43: disagrees about version of symbol ieee80211_unregister_hw
[   30.725549] b43: Unknown symbol ieee80211_unregister_hw (err -22)
[   30.725559] b43: disagrees about version of symbol ieee80211_beacon_get_tim
[   30.725563] b43: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   30.725589] b43: disagrees about version of symbol ieee80211_rts_get
[   30.725593] b43: Unknown symbol ieee80211_rts_get (err -22)
[   30.725609] b43: disagrees about version of symbol bcma_core_pci_irq_ctl
[   30.725613] b43: Unknown symbol bcma_core_pci_irq_ctl (err -22)
[   30.725623] b43: disagrees about version of symbol ieee80211_queue_work
[   30.725627] b43: Unknown symbol ieee80211_queue_work (err -22)
[   30.861322] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   32.956403] Registered led device: brcmsmac-phy0:radio
[   32.956410] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   33.036754] Bluetooth: can't load firmware, may not work correctly
[   33.114898] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

[ATTACH=CONFIG]252039[/ATTACH][ATTACH=CONFIG]252040[/ATTACH]

---

### Post by varunendra on 2014-04-14
As the description in your router's web interface suggests, please change the encryption type to pure WPA2 with AES (CCMP). WPA uses TKIP, so avoid both. Leave the settings in Ubuntu as they currently are.

Apart from that, some suggestions based on the wireless_script report -

[indent]**1)** Turn the "Power Management" on the wifi "off", and make sure it remains off. To turn it off -
```
sudo iwconfig wlan0 power off
```
To check its state -
```
iwconfig
```
Check it a few times within 20-30 minutes to make sure it remains off. If it turns back on automatically, we may try a few additional tricks to keep it off.

**2)** Keep the ethernet cable unplugged while trying to connect to wireless. By default Network Manager may not attempt to connect wirelessly if a wired connection is detected.

**3)** The module "ssb" is loading for some reason while it shouldn't. Blacklist it to prevent from loading (with "b43" for additional precaution). The following command will do it -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

**4)** The "NetworkManager.state" file is showing "**WirelessEnabled=[COLOR="#FF0000"]false[/COLOR]**", which means the wireless is disabled in Network Manager's drop-down menu. Please make sure it is enabled there (there should be a tick mark before the "Enable Wireless" option in NM menu). Probably this is the first thing you should cross check. If it already seems enabled, check the file again with -
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Does it still show as "false" in the above output? If yes, try manually changing the value to "true". Let me know if you need help with that.[/indent]

If none of the above could help, could you please try a Live session of whichever latest ISO you have (I guess from your previous post that you should have the latest ISO of "Lubuntu")? I would be interested to know how it performs with kernel 3.11 or later. If it behaves well, we can manually upgrade your kernel and hope for the best.

---

### Post by 1DoLittle on 2014-04-14
Varun,
Changing the security settings on the router, as you requested, made the wireless system work properly. For your information, included are screen shots of the router security settings - before and after.
Thanks for your great instructions and help.

[ATTACH=CONFIG]252052[/ATTACH]

---

