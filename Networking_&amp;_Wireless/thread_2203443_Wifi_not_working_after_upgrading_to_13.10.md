---
title: "Wifi not working after upgrading to 13.10"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by juandescals on 2014-02-03
Hello,

I upgraded to 13.10 with no problems but when I restarted I cannot connect via wifi. I can see the SSID of my wifi network listed but I can't connect with it.

As I saw in other threads I've obtained this output:

```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:cd:e3:a6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=sb ip=192.168.1.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 memory:b3000000-b300ffff
  *-network
       description: Wireless interface
       product: RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:7e:ac:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.11.0-15-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:1000(size=256) memory:b2000000-b2003fff 
```

---

### Post by varunendra on 2014-02-06
Please try -
```
sudo modprobe -rv rtl8192se
sudo modprobe -v rtl8192se swenc=Y
```
This will be a temporary change that will be lost at next boot. If it helps, we can make it permanent. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by juandescals on 2014-02-08
Thank you very much for the answer.

The code you sent me didn't work so here is the report of the "Wireless script"

```

*************** info trace ***************

***** uname -a *****

Linux juandescalsPB 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se

***** lsusb *****

Bus 002 Device 005: ID 0fce:e180 Sony Ericsson Mobile Communications AB 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
rtlwifi                63229  2 rtl_pci,rtl8192se
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              480503  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    tr13:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 22 Mb/s, Strength 10


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             217.11.96.234
    DNS:             217.11.108.234



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:off
                    ESSID:"tr13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=000000021328aaab
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000474723133
                    IE: Unknown: 010582840B162C
                    IE: Unknown: 030106


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E3576B855061FB3E2B43629
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8363D6BED4EF1CF5A92482B
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     13B5FC2521B6DC5AB3F115C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   26.438460] rtl8192se: FW Power Save off (module option)
[   26.438521] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   26.438521] Loading firmware rtlwifi/rtl8192sefw.bin
[   26.531316] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   27.400197] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040213)
[   30.250114] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.250417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1042.655792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1665.901357] Modules linked in: snd_hda_codec_hdmi parport_pc ppdev intel_powerclamp coretemp kvm_intel kvm bnep rfcomm bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev arc4 snd_hda_codec_realtek snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq radeon rtl8192se rtl_pci snd_seq_device rtlwifi snd_timer mac80211 microcode snd ttm drm_kms_helper cfg80211 psmouse serio_raw drm lpc_ich mei_me soundcore mei i2c_algo_bit binfmt_misc joydev acer_wmi sparse_keymap mxm_wmi wmi video mac_hid lp parport hid_generic usbhid hid tg3 ptp pps_core ahci libahci
[ 3501.149369] rtl8192se: FW Power Save off (module option)
[ 3501.149451] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[ 3501.149451] Loading firmware rtlwifi/rtl8192sefw.bin
[ 3501.150320] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 3501.393081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3501.393702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3511.115362] wlan0: authenticate with <MAC address removed>
[ 3511.136417] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3511.238520] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3511.342484] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3511.446437] wlan0: authentication with <MAC address removed> timed out
[ 3512.386671] wlan0: authenticate with <MAC address removed>
[ 3512.397292] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3512.498048] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3512.601951] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3512.705994] wlan0: authentication with <MAC address removed> timed out
[ 3513.662163] wlan0: authenticate with <MAC address removed>
[ 3513.672972] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3513.773567] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3513.877519] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3513.981482] wlan0: authentication with <MAC address removed> timed out
[ 3514.921702] wlan0: authenticate with <MAC address removed>
[ 3514.932546] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3515.037079] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3515.141004] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3515.244957] wlan0: authentication with <MAC address removed> timed out
[ 3516.189635] wlan0: authenticate with <MAC address removed>
[ 3516.200060] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3516.300644] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3516.404561] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3516.508521] wlan0: authentication with <MAC address removed> timed out
[ 3517.448576] wlan0: authenticate with <MAC address removed>
[ 3517.459465] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3517.560088] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3517.664077] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3517.768043] wlan0: authentication with <MAC address removed> timed out
[ 3518.716568] wlan0: authenticate with <MAC address removed>
[ 3518.727022] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3518.827697] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3518.931600] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3519.035455] wlan0: authentication with <MAC address removed> timed out
[ 3519.975894] wlan0: authenticate with <MAC address removed>
[ 3519.986634] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3520.091148] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3520.195113] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3520.299086] wlan0: authentication with <MAC address removed> timed out
[ 3521.239329] wlan0: authenticate with <MAC address removed>
[ 3521.250039] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3521.350630] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3521.454556] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3521.558559] wlan0: authentication with <MAC address removed> timed out
[ 3522.519013] wlan0: authenticate with <MAC address removed>
[ 3522.529477] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3522.630205] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3522.734173] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3522.838137] wlan0: authentication with <MAC address removed> timed out
[ 3523.778482] wlan0: authenticate with <MAC address removed>
[ 3523.789086] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3523.889794] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3523.993597] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3524.101585] wlan0: authentication with <MAC address removed> timed out
[ 3525.061863] wlan0: authenticate with <MAC address removed>
[ 3525.072578] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3525.173241] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3525.277214] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3525.381161] wlan0: authentication with <MAC address removed> timed out
[ 3526.321940] wlan0: authenticate with <MAC address removed>
[ 3526.332118] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3526.432722] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3526.536685] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3526.640630] wlan0: authentication with <MAC address removed> timed out
[ 3527.581016] wlan0: authenticate with <MAC address removed>
[ 3527.591587] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3527.692282] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3527.796145] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3527.900174] wlan0: authentication with <MAC address removed> timed out
[ 3528.844866] wlan0: authenticate with <MAC address removed>
[ 3528.855129] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3528.955742] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3529.059702] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3529.163680] wlan0: authentication with <MAC address removed> timed out
[ 3530.104139] wlan0: authenticate with <MAC address removed>
[ 3530.114751] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3530.215296] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3530.319255] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3530.423212] wlan0: authentication with <MAC address removed> timed out
[ 3531.364056] wlan0: authenticate with <MAC address removed>
[ 3531.374152] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3531.474876] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3531.578789] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3531.682721] wlan0: authentication with <MAC address removed> timed out
[ 3532.623335] wlan0: authenticate with <MAC address removed>
[ 3532.633752] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3532.734339] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3532.838333] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3532.942296] wlan0: authentication with <MAC address removed> timed out
[ 3533.882623] wlan0: authenticate with <MAC address removed>
[ 3533.893211] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3533.993860] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3534.097797] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3534.201724] wlan0: authentication with <MAC address removed> timed out

****************** done ******************


```

---

### Post by varunendra on 2014-02-09
Please try these as a few initial tweaks -

1) Change the channel in the router from channel 6 to channel 1 or 11
2) In Network Manager, make sure IPv6 is set to "Ignore". Or disable it completely following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)
3) Try these driver parameters -
```
sudo modprobe -rv rtl8192se
sudo modprobe -v rtl8192se swenc=1 ips=0 fwlps=0
```
The first command will remove the driver, the second one will reload it with the parameters. This will be a temporary change that will be lost at next boot. If it helps, we can make it permanent. If not, next we'll try a newer driver.

---

### Post by juandescals on 2014-02-11
Hello,
I've tried it and it's still not working (I changed the channel to 1 and to 11 and set "ignore" to IPv6)

---

### Post by varunendra on 2014-02-11
Okay, time try the newer driver then.

Please make sure the essential packages to build a driver are installed beforehand. While being connected to internet via cable, please do -
```
sudo apt-get install linux-headers-generic build-essential
```

Then proceed to downloading, building and installing the driver as follows :

**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > Extract here. This will create a folder with same name as the package (without .tar.xz in the last)

**3)** Open a terminal (Ctrl-Alt-T) and assuming this extracted folder is in your "Downloads" directory, run the following commands to compile and install the driver -
```
cd Downloads/backports-3.12.8-1
make defconfig-rtlwifi
make
[s]make install[/s]
sudo make install
```

**4)** Reboot and check -
```
sudo iwlist scan
```
Can you scan available networks? Can you connect to them now?

If not, please try the same process (points 1 to 4) with the latest backports package available on the linked page.

**PS:**
Oh, and please try the driver parameters with this driver as well. Some of them may be necessary sometimes.

[COLOR="#FF0000"]**EDIT:** Corrected the "make install" command above.[/COLOR]

---

### Post by juandescals on 2014-02-13
Ok
> **PS:**
Oh, and please try the driver parameters with this driver as well. Some of them may be necessary sometimes.

Using the same commands?

---

### Post by varunendra on 2014-02-14
Yes, the same commands. The backported drivers only have a different version, their names remain the same.

---

### Post by juandescals on 2014-02-14
Hello,

I've tried 3.12.8-1 and 3.13.2-1, with them the manager says "connected" but, in fact, I can't connet to the wifi.

The last command produces the next:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:80:C8:19:AA:A3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"tr13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=000000003f41950f
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000474723133
                    IE: Unknown: 010582840B162C
                    IE: Unknown: 030101


```

This net usually has no encryption but if I encrypt it then "connected" message disappears (even though I edit the connexion and provide the correct wep key).

---

### Post by varunendra on 2014-02-14
I wonder if it is a network configuration issue then. Do you get an IP? Can you ping your router when you *seem* to be connected to WiFi ? -
```
ping -c4 192.168.1.1
```

If you don't get an IP address on your WiFi interface, try manually assigning one, for example 192.168.1.100 in the Network Manager, then try pinging as above.

And does your wifi router support b-channel only? As apparent here -
> **juandescals said:**
> ```

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; **22 Mb/s**
                    Mode:Master

```
Because the g-channel supports upto 54 Mb/s speeds. So unless your router is a really ancient one, make sure the g-channel is enabled in it.

Also make sure there are no funny policies/filters are enabled in it, or are configured properly (I am thinking about MAC filters, firewall).
As always, reboot the router after saving any changes.

**[COLOR="#FF0000"]EDIT:[/COLOR]** I made a mistake in the "make install" command. It needs to be run with 'sudo'. Please use corrected command as edited in the original post above.

---

### Post by juandescals on 2014-02-17
I am suspecting that it's a problem with the network: the router only supports b-channel, and it's quite old: from 2003...

So as soon as I can I'll try with other networks...

Is possible that it will work with an old driver instead of the newest ones?

---

### Post by varunendra on 2014-02-17
Anything is possible. But much older drivers won't compile on the latest kernels and among those that will, the bunch of drivers from backports-3.12 series has been apparently working quite nicely.

We may try some other variants as well, like one from the author's github repository (usually it means the 'Bleeding edge' version), or the one from the official website of Realtek (usually much older, not sure about its success with compilation on your kernel). So we have a few other options, but I can't say anything about our chances of success with them.

But did you try pinging some of the local addresses (like gateway, DNS etc.) when it 'seemed' to be connected? Did you get a reply?

As of now, I would like to see the "wireless_script" report with the backported driver (preferably the 3.12.8-1, but no problem if the later one is already installed), when it seems to be connected.

Along with the report, please also post the output of -
```
route -n
```

---

### Post by juandescals on 2014-02-20
Ok, here you are:

```
juandescals@juandescalsPB:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


```

And the wireless script again:

```

*************** info trace ***************

***** uname -a *****

Linux juandescalsPB 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se

***** lsusb *****

Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tr13"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** lsmod *****

rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
rtlwifi                63229  2 rtl_pci,rtl8192se
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              480503  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tr13 1] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *tr13:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 22 Mb/s, Strength 78
    Wifi_Granja2:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             217.11.96.234
    DNS:             217.11.108.234


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             217.11.96.234
    DNS:             217.11.108.234



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"tr13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=00000001fe60ce06
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000474723133
                    IE: Unknown: 010582840B162C
                    IE: Unknown: 030101


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BBE7CF1C21ED0CF95992D78
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     817F63398F5E31706193BFC
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E6EB1F4DDC335E171E2711F
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   25.964937] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040213)
[   26.218857] rtl8192se: FW Power Save off (module option)
[   26.218925] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   26.218925] Loading firmware rtlwifi/rtl8192sefw.bin
[   27.174004] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   29.366906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.367261] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.132749] wlan0: authenticate with <MAC address removed>
[   31.143144] wlan0: send auth to <MAC address removed> (try 1/3)
[   31.145125] wlan0: authenticated
[   31.145248] rtl8192se 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.145252] rtl8192se 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.147890] wlan0: associate with <MAC address removed> (try 1/3)
[   31.150611] wlan0: RX AssocResp from <MAC address removed> (capab=0x41 status=0 aid=3)
[   31.153928] wlan0: associated
[   31.153938] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.159824] Modules linked in: snd_hda_codec_hdmi parport_pc uvcvideo ppdev arc4 rfcomm videobuf2_vmalloc videobuf2_memops bnep videobuf2_core bluetooth videodev intel_powerclamp coretemp kvm_intel kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec rtl8192se joydev snd_hwdep rtl_pci radeon snd_pcm rtlwifi mac80211 binfmt_misc snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi ttm drm_kms_helper drm cfg80211 snd_seq snd_seq_device mei_me snd_timer mei psmouse snd i2c_algo_bit microcode serio_raw soundcore lpc_ich acer_wmi sparse_keymap lp parport video mac_hid mxm_wmi wmi hid_generic usbhid hid tg3 ahci ptp libahci pps_core
[   31.159904]  [<ffffffffa022434d>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

****************** done ******************


```

---

### Post by varunendra on 2014-02-21
> **juandescals said:**
> 
```

***** modinfo *****

filename:       **/lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko**
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BBE7CF1C21ED0CF95992D78

```

The driver is clearly the original one from the kernel you currently have installed (3.11.0-17), not the backported one.

Please follow the post to install the backported driver again, and post back the report with that one.

Also, it seems you ran "route -n" command when the wired connection was disconnected, and the wireless script when it was connected later (or before). Please run the script with only the wireless connected this time, when the cable is unplugged.

---

### Post by juandescals on 2014-02-22
Ok 
Here's the repport: (Wifi is still not cnnecting)

```


*************** info trace ***************

***** uname -a *****

Linux juandescalsPB 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se

***** lsusb *****

Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tr13"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** lsmod *****

rtl8192se              93917  0 
rtl_pci                35460  1 rtl8192se
rtlwifi                86089  2 rtl_pci,rtl8192se
mac80211              512924  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              483474  2 mac80211,rtlwifi
compat                 13385  4 cfg80211,mac80211,rtlwifi,rtl8192se

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tr13 1] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *tr13:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 22 Mb/s, Strength 76

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             217.11.96.234
    DNS:             217.11.108.234


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"tr13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e4707e0
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000474723133
                    IE: Unknown: 010582840B162C
                    IE: Unknown: 030101


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     0D2813E706BEC7333A3D41B
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,compat,mac80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8811228D1788BF0C4F4D7B6
depends:        mac80211,rtlwifi
vermagic:       3.11.0-17-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     710FFFC52D83E7E06A71F7E
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   21.720558] rtl8192se: FW Power Save off (module option)
[   21.720614] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   21.720614] Loading firmware rtlwifi/rtl8192sefw.bin
[   22.189730] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x040213)
[   22.246352] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   25.879897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.880246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.632407] wlan0: authenticate with <MAC address removed>
[   27.642875] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.644973] wlan0: authenticated
[   27.645256] rtl8192se 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.645260] rtl8192se 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.647426] wlan0: associate with <MAC address removed> (try 1/3)
[   27.650436] wlan0: RX AssocResp from <MAC address removed> (capab=0x41 status=0 aid=6)
[   27.653547] wlan0: associated
[   27.653558] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.659412] Modules linked in: snd_hda_codec_hdmi rfcomm parport_pc bnep ppdev bluetooth snd_hda_codec_realtek radeon snd_hda_intel snd_hda_codec uvcvideo binfmt_misc arc4 intel_powerclamp videobuf2_vmalloc snd_hwdep videobuf2_memops coretemp videobuf2_core kvm_intel kvm videodev snd_pcm snd_page_alloc joydev snd_seq_midi snd_seq_midi_event rtl8192se(OF) snd_rawmidi ttm snd_seq rtl_pci(OF) rtlwifi(OF) snd_seq_device mac80211(OF) snd_timer drm_kms_helper mei_me drm snd psmouse mei cfg80211(OF) i2c_algo_bit soundcore compat(OF) microcode serio_raw lpc_ich acer_wmi sparse_keymap lp parport mxm_wmi wmi mac_hid video hid_generic usbhid hid tg3 ahci ptp libahci pps_core
[   27.659491]  [<ffffffffa02ca39d>] ? rtl_is_special_data+0x2d/0x1f0 [rtlwifi]

****************** done ******************



```

---

### Post by varunendra on 2014-02-22
Okay, you are apparently connected, but with a terrible speed of 1Mb/s -
> **juandescals said:**
> 
```

wlan0     IEEE 802.11bgn  ESSID:"tr13"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          **Bit Rate=[COLOR="#FF0000"]1 Mb/s[/COLOR] **  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

```

Since we are not expecting miracles from the router, let's try manually setting a higher speed and see if it works. Please do -
```
sudo iwconfig wlan0 rate 5.5M
```
Then check -
```
iwconfig
```
Does it show the higher speed (5.5) now? Can you start browsing now?

And can you ping your router?
```
ping -c4 192.168.1.1
```

Your DNS servers?
```
ping -c4 217.11.96.234
ping -c4 217.11.108.234
```

Google's DNS servers?
```
ping -c4 8.8.8.8
```

Please post back these reports if still having problem. And the command "route -n" has been added to the wireless_script now, so you might wish to use the newer version (same link, newer script).

---

### Post by juandescals on 2014-02-22
The change to 5.5M had worked but I still can't browse the web.

I did this: 
```

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"tr13"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:80:C8:19:AA:A3   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

juandescals@juandescalsPB:~$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3001ms



```

---

### Post by varunendra on 2014-02-24
> **juandescals said:**
> ```

juandescals@juandescalsPB:~$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, **[COLOR="#FF0000"]100% packet loss[/COLOR]**, time 3001ms

```

We can try even higher speed and it should stick, but the main problem seem to be that you are not able to even ping your Gateway.

On your Ethernet interface, have you manually configured the IP address (192.168.1.11) or is it getting that automatically? Can you browse the internet with your wired connection?

And could you post the screenshots of your router's network configuration showing the general status and the DHCP configuration? Blur out the sensitive information like your router's MAC address and WAN IP before posting the screenshots here.

---

### Post by juandescals on 2014-02-24
I've changed speed to 11M and... it's working! 

Speed was 1M before I changed it. Then I changed to 5.5M with no results, then to 11M and... bingo!

```

wlan0     IEEE 802.11bgn  ESSID:"tr13"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:80:C8:19:AA:A3   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=18/70  Signal level=-92 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0


```

Ping:
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=2.29 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 2.297/2.344/2.364/0.043 ms



```

Can I make the change permanent?

The ethernet IP adress is automatically obtained and I can browse with it nicelly.

Our network is a little tricky: first the signal arrives via radio to an Alvarion Antenna wich configuration I can't know, from here to a router who provides the IP to the network and attached to the router a Wireless Access Point. I can connect by cable directly to the router. Also by cable to a Wireless bridge placed in another building and directly via wifi if I am in range. Nothing was changed in their configuration before and after my upgrading to 13.10... But if you need it: how can I post the screenshot and what do you need exactly because there are a lot of pages of status in the router and the wireless access point?

---

### Post by varunendra on 2014-02-24
> **juandescals said:**
> I've changed speed to 11M and... it's working! 

Speed was 1M before I changed it. Then I changed to 5.5M with no results, then to 11M and... bingo!
That's awesome! Something I wasn't expecting after even a gateway ping failing at 5.5M speed! :P

Your network indeed sounds a bit tricky but not too complex. Assuming 192.168.1.1 is the router, there is only the Access-Point between it and the wireless card. So it seems the AP is not relaying the packets properly. Either it is too busy or is buggy or not configured properly. In certain cases, the connectivity may be short-lived, although I am hoping it will persist since the initial connection, which is usually the difficult part, was always established in all our attempts.

So the only possible problem that I think may arise is getting the IP via DHCP. If that problem occurs, either you can resort to manual IP configuration (modifying the DHCP range in the router accordingly, so that the manually assigned IP is not included in the DHCP range), or we may try to optimize the router/Access-Point settings. Only in the latter case shall I need the screenshots. :)

But if just forcing the speed to 11M is enough to solve the problem, it is much easier to make it permanent. Just add the command to your /etc/rc.local file, above the last line ("exit 0").

You can add it using your text editor (must be opened with root privileges), or using this single command in a terminal -
```
sudo sed -i '/^exit 0/i iwconfig wlan0 rate 11M' /etc/rc.local
```
Since next boot, you should see the speed to be already set to 11 Mbps. You may wish to try even the highest supported speed (22M) before making it permanent like this. :P

---

### Post by juandescals on 2014-02-25
Ok.
I can't switch to 22M but it's working fine at 11M... 

Thank you very much por your help. 

I'll mark this thread as solved (If you agree)

---

### Post by varunendra on 2014-02-25
> **juandescals said:**
> I'll mark this thread as solved (If you agree)

Do I agree? I love that prefix, no matter how it comes! :D

---

### Post by juandescals on 2014-02-28
Thank you very much...

---

### Post by gi0 on 2014-06-28
For me it works too! Thank you for sharing your expertise.

I would also add the following:

I came from an ubuntu 13.04 on a notebook packard bell easy note TM, the wifi adapter is driven by rtl8192se,  and everything was fine.
Then I try  ubuntu 14.04, I  connect the wifi network and I get from the router an ip  and a default gw address, so routing is ok,  but i can't ping neither the router neither the rest. 

My router has b and g channels activated, and I'm able to navigate only if I give 
 iwconfig wlan0 rate X besides the value of X ( 11 to 54M),

thus, for me,  it doesn't matter the rate but it need a value.

Thank you a lot

---

### Post by med4 on 2014-06-28
i have the same problem , but i'm good now :D

---

### Post by varunendra on 2014-06-28
Welcome both of you! :)

Glad it could help you. The only thing I doubt is stability with a 'Forced speed'. Hope no such problem occurs with your connections.

---

