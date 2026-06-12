---
title: "DELL E6430 upgrade to 13.10 from 13.04 and 12.10 (64 Bit) Wireless not working"
date: 2013-11-03
forum: Networking &amp; Wireless
---

### Post by RikardSvenningsen on 2013-11-03
Hi
I started out with my new E6430. Using Ubuntu 12.10 (64 bit) From the start I got trouble with the WIFI card. It worked but I have issue when using Virtualbox, when a guest should use bridge networking to the WIFI. no problem if I used Wiered connection. Even when I used ZyXEL NWD271N, it was working fine.
An upgrade to 13.04 didn't change a thing. everything was working just fine except for the virtualbox bridging function.
An upgrade to 13.10 was a bad choice. Now my WIFI is not working.
It connect to the network, it get's an ip from the network, I can ping it's self and localhost but nothing elses.
If I connect the wired connection, then I can work again.

What is going on with my computer?

Best regards
Rikard Svenningsen

Please somebody help me. :(

---

### Post by varunendra on 2013-11-06
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Preferably run it when the wired connection is disconnected and the wireless 'seems' to be connected as you say.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Irihapeti on 2013-11-06
*Thread moved to **Networking & Wireless**.*

---

### Post by RikardSvenningsen on 2013-11-06
Ok.
This is what I get:
```

*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: wl

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 007: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:"tcbqw53951fgk"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

wl                   4207474  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              479757  1 wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [tcbqw53951fgk 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Fiber:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Tilgin-7y5Axz7K8hZK: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    *tcbqw53951fgk:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2

    DNS:             192.168.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

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

auto lo
iface lo inet loopback


***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00054669626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"tcbqw53951fgk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000D7463627177353339353166676B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA90050F204104A00011010440001021057000101103B0001031047001063041253101920061228744401825A001021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0586:0x3417 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[    5.222935] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.287335] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    5.296772] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[    5.340034] Bluetooth: can't load firmware, may not work correctly
[    6.466865] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   52.820500] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   53.820667] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 4876.280225] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 5356.716870] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[ 8772.764048] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[10260.116484] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[11410.451806] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11459.148446] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11460.149699] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11461.151502] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11462.153402] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11463.154316] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11464.156130] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[11465.157958] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[16774.110401] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[16775.111636] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[16776.112917] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18014.285517] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18015.285430] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18016.286269] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18017.286169] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18018.287010] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18019.287702] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18738.165110] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18917.121994] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18918.123024] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18919.124847] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18920.126688] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18921.127620] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18922.128518] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18923.130345] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[18948.855536] Bluetooth: can't load firmware, may not work correctly
[43186.702843] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[43187.703398] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[44887.325045] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[61539.726284] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[61540.727005] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[61541.727483] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[61542.728879] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[61543.730250] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[63115.389326] Bluetooth: can't load firmware, may not work correctly
[95899.400584] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[99283.399100] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[99284.399703] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[99285.401001] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[99286.402027] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[99287.403359] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[99288.404682] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113238.731340] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113239.732544] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113240.733757] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113241.734839] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113242.736096] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[113243.737437] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[114229.253249] Bluetooth: can't load firmware, may not work correctly
[140817.400867] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
[142627.417442] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[146885.518562] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[146973.112507] ERROR @wl_dev_intvar_get : error (-1)
[146973.112511] ERROR @wl_cfg80211_get_tx_power : error (-1)
[147067.507773] ERROR @wl_dev_intvar_get : error (-1)
[147067.507777] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************

```

---

### Post by varunendra on 2013-11-06
> **RikardSvenningsen said:**
> ```

Linux E6430-2Linux** 3.11.0-12-generic** #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
....
....
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter **[14e4:4727]** (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: **wl**

```

Please try this -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and see if it works again.

If not, try changing the encryption in the router to pure WPA2-PSK (AES/CCMP). No WPA/WPA2 mixed mode, no TKIP. The pure WPA2-PSK (AES/CCMP) is highly recommended anyway.

If still having problems, please run the script again and post back the fresh report.

---

### Post by mrcameronnewton on 2013-11-06
[FONT=arial][SIZE=3]It looks to me that you have a Driver Issue
[SIZE=2]For your PC, they should be a Linux Download in the form of a .tar.gz or something On the lines of that...
OR
If there isnt a Ubuntu Edition, Use a Emulator like WINE to install the Wireless Drivers.
Also, Concult the Software & Updates Program as you may be using incorrect drivers

By the way, Did your computer come with Ubuntu ready Installed or did it have Windows Already Installed?
[/SIZE][/SIZE][/FONT]
-- MrCameronnewton

(P.S Also change your encryption on your router, sometimes this can be a Issue with ubuntu not understanding the Encryption Protocols)

---

### Post by varunendra on 2013-11-06
> **mrcameronnewton said:**
> For your PC, they should be a Linux Download in the form of a .tar.gz or something On the lines of that...
OR
If there isnt a Ubuntu Edition, Use a Emulator like WINE to install the Wireless Drivers.

tar.gz packages are rarely needed on Ubuntu, and the driver this card requires certainly doesn't need that.

Also, the only way to install 'Windows wireless drivers' on Ubuntu is **ndiswrapper**, and that also is not needed for this card. Wine (or any 'Emulator' or 'compatibility layer' software) only works for applications, not drivers.

---

### Post by RikardSvenningsen on 2013-11-07
Hi again.
done:
sudo apt-get purge bcmwl-kernel-source
Now the wireless don't even connect to the router.


```

*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
0c:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8221] (rev 05)

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****


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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

***** modinfo *****


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0586:0x3417 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[    5.373361] Bluetooth: can't load firmware, may not work correctly

****************** done ******************

```

Before I run the command, I checked the Wireless on my work, and my Sony Xperia U hotspot.
That worked without any trouble.. :-)
But still not at home :(
Change the router as discriped, didn't work ether.
I have to mention, this problem is new, never got that problem before.
No problems with Ubuntu 13.04 nor 12.10 nor 12.04 all 64Bit.

---

### Post by wildmanne39 on 2013-11-07
Please do:
```
sudo modprobe -v brcmsmac
```
Thanks

---

### Post by varunendra on 2013-11-08
Some explanations to clear your doubts -

Keep the change of the router encryption (pure WPA2-PSK (AES/CCMP)), it is more secure and more compatible with Linux drivers. It also has the potential to offer better speeds than TKIP (TKIP is limited to 54 Mb/s).

The problem didn't exist before because the proprietary driver you were using is also a suitable one for your card, only the native one (the one we are trying to use now) is better in the newer kernels.

Also, a lot of changes have been made to the latest version of the proprietary "sta" driver that you were originally using. It is possible that one or more of these changes may be buggy, causing it to not work properly with some cards now. Since the native one is proven to work better in latest kernels, it makes even more sense to try it, which requires the proprietary one be purged first - exactly what I suggested.

However, it seems it wasn't purged correctly for some reason, because the blacklist file it creates still exists (it should have been purged too, but is not) -
> **RikardSvenningsen said:**
> ```

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
[B][COLOR="#FF0000"]blacklist bcma
blacklist brcm80211
blacklist brcmsmac[/COLOR][/B]
blacklist ssb

```
Please purge it manually, so that the driver (brcmsmac) can load automatically on next boot -
```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```
Additionally, also remove the udev rules file which still contains traces of the sta driver -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
It will be automatically regenerated on next boot, with only the desired entries this time.

Reboot and check -
```
lsmod | grep brcm
```
Do you see "brcmsmac" in the output? If yes, you should have a working wifi.

What Wild Man suggested is a way to manually load the same driver, so you can verify if it indeed works. You can always use that command to manually load the driver, in case it doesn't load automatically for some weird reason (as evident in your "wireless-info.txt" file).

As always, we are ready to dig deeper if required. :)

---

### Post by RikardSvenningsen on 2013-11-08
Thanks :-) :-) :-) :-)

This is GREAT.
1.
sudo apt-get purge bcmwl-kernel-source
2.
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
3.
sudo rm /etc/udev/rules.d/70-persistent-net.rules
4.
sudo modprobe -v brcmsmac

This did the trick, but not just that!!!

rs@E6430-2Linux:~$ sudo lsmod | grep brcm
```

[sudo] password for rs: 
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
bcma                   46670  3 b43,brcmsmac
rs@E6430-2Linux:~$ 

```

I had trouble with my Wireless before, in that way I coudn't make the bridge function avalible when I use VirtualBox. Now that works too..

This link is solved too:
[http://ubuntuforums.org/showthread.php?t=2113760](http://ubuntuforums.org/showthread.php?t=2113760)

The only downside is, it not as fast as before... on the 13.04 and lower versions.

---

### Post by varunendra on 2013-11-08
Erm.. a bit hesitating to say "Great!", cuz actually when I said it is "better", I meant (and expected) a better speed too.

If you wish to try your luck with some more tweaking, please post another fresh wireless_script report so we can see if everything is at optimal settings now.

I may not be able to reply quickly for a few days (not sure if I'll get an opportunity to), but Wild Man is already on your thread, who is much-much better than me on these issues.

---

### Post by RikardSvenningsen on 2013-11-09
Of course I want to figth... The trouble..
This is a new Wireless Script log.
```


*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tcbqw53951fgk"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:98  Invalid misc:51   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

carl9170               86949  0 
ath                    23827  1 carl9170
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  3 b43,brcmsmac,carl9170
cfg80211              479757  5 b43,ath,brcmsmac,mac80211,carl9170
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tcbqw53951fgk 1] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
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
    Waoo:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Tilgin-FPya96KcSkT9: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    Tilgin-7y5Axz7K8hZK: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
    Fiber:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA2
    TDC-07AC:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *tcbqw53951fgk:  Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Tilgin-z7Qry7UZYDb1: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    HomeBox-941C:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2

    DNS:             192.168.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"tcbqw53951fgk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ea621182b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D7463627177353339353166676B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA90050F204104A00011010440001021057000101103B0001031047001063041253101920061228744401825A001021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HomeBox-941C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000958b8725563
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000C486F6D65426F782D39343143
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2D001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331A2D001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 341601080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAB0050F204104A0001101044000102103B0001031047001080FC0F8992285312947BDA0F790796D210210008536167656D636F6D10230015536167656D436F6D46617374333936335F4847573310240009532E352E302D312E301042000F4C4B313330373844503132303337321054000800060050F20400011011001A536167656D436F6D46617374333936335F484757332D4C4B3133100800020002103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002ae15adf
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00054669626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 04 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Waoo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009295ed14
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000457616F6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TDC-07AC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000234ac7cdf1
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00085444432D30374143
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084661737433357878102400043132333410420004353637381054000800060050F20400011011001146617374333578782D536167656D204150100800020084103C000101
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-7y5Axz7K8hZK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000626b8f350d
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 001354696C67696E2D37793541787A374B38685A4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B00010310470010A755B6B7082B5E1F9BD54864476E03621021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303535393035321054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-FPya96KcSkT9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000062680ca3f2
                    Extra: Last beacon: 20ms ago


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

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     B583902FE5ABA8FEE119CD2
alias:          usb:v1B75p9170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p02B4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0249d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0026d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3417d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0326d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0804d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0ACEp1221d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vCACEp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B797CFD1C70935B62C35EE
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
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
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0586:0x3417 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[    5.389942] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    5.389973] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    5.389999] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    5.390046] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    5.401526] bcma: bus0: Bus registered
[    5.425101] Bluetooth: can't load firmware, may not work correctly
[    5.567124] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[    5.567133] b43: probe of bcma0:0 failed with error -524
[    5.589821] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    5.598454] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    6.278939] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    6.278953] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    6.279562] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.283664] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.085655] wlan0: authenticate with <MAC address removed>
[    8.089440] wlan0: send auth to <MAC address removed> (try 1/3)
[    8.090859] wlan0: authenticated
[    8.093032] wlan0: associate with <MAC address removed> (try 1/3)
[    8.097026] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[    8.099183] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[    8.099187] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[    8.099195] wlan0: associated
[    8.099205] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.953759] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  591.556464] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  591.559864] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  591.559877] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  591.559881] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  599.057652] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  599.057660] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  599.058252] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  600.798927] wlan0: authenticate with <MAC address removed>
[  600.800202] wlan0: send auth to <MAC address removed> (try 1/3)
[  600.801718] wlan0: authenticated
[  600.805873] wlan0: associate with <MAC address removed> (try 1/3)
[  600.810027] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  600.812126] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  600.812132] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  600.812149] wlan0: associated
[  600.812163] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  603.592181] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1029.702453] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 1029.725340] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1029.725351] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1029.725354] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1036.489568] wlan0: authenticate with <MAC address removed>
[ 1036.493447] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1036.532198] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1036.620854] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1036.713781] wlan0: authentication with <MAC address removed> timed out
[ 1043.509413] wlan0: authenticate with <MAC address removed>
[ 1043.513001] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1043.514736] wlan0: authenticated
[ 1043.516558] wlan0: associate with <MAC address removed> (try 1/3)
[ 1043.520707] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1043.522781] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1043.522791] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1043.522795] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1043.522809] wlan0: associated
[ 1070.136975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1070.138315] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1070.138326] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1070.138330] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1075.349496] wlan0: authenticate with <MAC address removed>
[ 1075.351001] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1075.352530] wlan0: authenticated
[ 1075.356694] wlan0: associate with <MAC address removed> (try 1/3)
[ 1075.361037] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1075.361526] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1075.361532] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1075.361545] wlan0: associated
[ 1078.033082] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1100.848985] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[ 1100.857108] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1100.857122] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1100.857126] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1101.789154] wlan0: authenticate with <MAC address removed>
[ 1101.790583] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1101.810912] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1101.940880] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1102.026014] wlan0: authentication with <MAC address removed> timed out
[ 1108.796418] wlan0: authenticate with <MAC address removed>
[ 1108.800177] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1108.839751] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1108.944710] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1109.051955] wlan0: authentication with <MAC address removed> timed out
[ 1109.991788] wlan0: authenticate with <MAC address removed>
[ 1109.995427] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1109.996977] wlan0: authenticated
[ 1109.999120] wlan0: associate with <MAC address removed> (try 1/3)
[ 1110.003645] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1110.005744] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1110.005751] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1110.005755] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1110.005769] wlan0: associated
[ 1132.617356] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1132.622708] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1132.622722] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1132.622727] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1137.598739] wlan0: authenticate with <MAC address removed>
[ 1137.600180] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1137.601738] wlan0: authenticated
[ 1137.605901] wlan0: associate with <MAC address removed> (try 1/3)
[ 1137.610094] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1137.612202] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1137.612214] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1137.612234] wlan0: associated
[ 1141.311484] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1169.050858] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 1169.396225] ath: EEPROM regdomain: 0x30
[ 1169.396231] ath: EEPROM indicates we should expect a direct regpair map
[ 1169.396234] ath: Country alpha2 being used: AM
[ 1169.396236] ath: Regpair used: 0x30
[ 1169.604890] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1169.605440] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1173.178986] wlan1: authenticate with <MAC address removed>
[ 1173.253822] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1173.255403] wlan1: authenticated
[ 1173.259682] wlan1: associate with <MAC address removed> (try 1/3)
[ 1173.263956] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1173.267839] wlan1: associated
[ 1173.267896] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1192.316230] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1192.318497] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1192.318509] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1192.318513] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1304.506047] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1327.839957] wlan0: authenticate with <MAC address removed>
[ 1327.841586] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1327.843047] wlan0: authenticated
[ 1327.843352] wlan0: associate with <MAC address removed> (try 1/3)
[ 1327.847494] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1327.847991] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1327.847999] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1327.848010] wlan0: associated
[ 1330.605047] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1605.201574] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1605.204221] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1605.204239] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1605.204245] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1611.656049] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1611.656056] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1611.656663] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1613.392430] wlan0: authenticate with <MAC address removed>
[ 1613.393579] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1613.396269] wlan0: authenticated
[ 1613.399154] wlan0: associate with <MAC address removed> (try 1/3)
[ 1613.403382] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1613.403883] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1613.403889] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1613.403900] wlan0: associated
[ 1613.403912] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1617.140336] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 3492.199043] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3492.207420] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3492.207431] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 3492.207434] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3498.341305] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3498.341313] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 3498.341924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3500.082395] wlan0: authenticate with <MAC address removed>
[ 3500.083702] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3500.085174] wlan0: authenticated
[ 3500.089293] wlan0: associate with <MAC address removed> (try 1/3)
[ 3500.093476] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3500.095587] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3500.095594] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3500.095610] wlan0: associated
[ 3500.095624] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3503.298964] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 4062.548513] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4062.561910] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 4062.561922] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 4062.561926] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4069.172645] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 4069.172652] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 4069.173260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4070.921593] wlan0: authenticate with <MAC address removed>
[ 4070.923147] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4070.924596] wlan0: authenticated
[ 4070.928769] wlan0: associate with <MAC address removed> (try 1/3)
[ 4070.932845] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4070.934933] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 4070.934938] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 4070.934952] wlan0: associated
[ 4070.934965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4074.500216] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 6467.768579] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6467.769944] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 6467.769958] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 6467.769963] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 6474.054370] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 6474.054377] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 6474.054972] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6475.795774] wlan0: authenticate with <MAC address removed>
[ 6475.796849] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6475.798386] wlan0: authenticated
[ 6475.802562] wlan0: associate with <MAC address removed> (try 1/3)
[ 6475.806695] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 6475.808772] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 6475.808778] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 6475.808792] wlan0: associated
[ 6475.808806] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6478.416315] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 7204.715094] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7204.718042] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 7204.718057] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 7204.718063] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 7211.133633] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 7211.133640] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 7211.134234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7212.866513] wlan0: authenticate with <MAC address removed>
[ 7212.869616] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7212.871090] wlan0: authenticated
[ 7212.873607] wlan0: associate with <MAC address removed> (try 1/3)
[ 7212.877851] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 7212.879992] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 7212.880002] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 7212.880017] wlan0: associated
[ 7212.880033] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7216.686792] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[10032.913712] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[10032.918114] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[10032.918128] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[10032.918132] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[10039.962940] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[10039.962955] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[10039.963564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10041.717558] wlan0: authenticate with <MAC address removed>
[10041.718570] wlan0: send auth to <MAC address removed> (try 1/3)
[10041.720033] wlan0: authenticated
[10041.724208] wlan0: associate with <MAC address removed> (try 1/3)
[10041.728383] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[10041.730444] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[10041.730450] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[10041.730464] wlan0: associated
[10041.730477] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10044.887634] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[11602.142034] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[11602.144205] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[11602.144216] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[11602.144220] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[11609.206702] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[11609.206716] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[11609.207338] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11611.009482] wlan0: authenticate with <MAC address removed>
[11611.010989] wlan0: send auth to <MAC address removed> (try 1/3)
[11611.012442] wlan0: authenticated
[11611.016548] wlan0: associate with <MAC address removed> (try 1/3)
[11611.020718] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[11611.021205] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[11611.021211] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[11611.021222] wlan0: associated
[11611.021234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11613.983144] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[12523.256913] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[12523.262455] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[12523.262469] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[12523.262472] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[12530.073260] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[12530.073275] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[12530.073880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12531.856655] wlan0: authenticate with <MAC address removed>
[12531.858243] wlan0: send auth to <MAC address removed> (try 1/3)
[12531.859693] wlan0: authenticated
[12531.863825] wlan0: associate with <MAC address removed> (try 1/3)
[12531.868702] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[12531.869194] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[12531.869200] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[12531.869215] wlan0: associated
[12531.869264] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12534.838966] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

****************** done ******************


```

I can see the speed is 1Mhz, but it goes from 1 - 29 more or less all the time, but it dosn't feel that anoing as it's supposed to.

---

### Post by varunendra on 2013-11-09
The lsmod part is quite amusing :P
> **RikardSvenningsen said:**
> 
```

***** lsmod *****

**[COLOR="#800000"]carl9170[/COLOR]**               86949  0 
ath                    23827  1 carl9170
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
**[COLOR="#FF0000"]b43[/COLOR]**                   387185  0 
mac80211              596969  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,**[COLOR="#800000"]carl9170[/COLOR]**
cfg80211              479757  5 **[COLOR="#FF0000"]b43[/COLOR],[COLOR="#800000"]ath[/COLOR]**,brcmsmac,mac80211,**[COLOR="#800000"]carl9170[/COLOR]**
**[COLOR="#FF0000"]ssb[/COLOR]**                    57932  1 b43
bcma                   46670  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (**[COLOR="#800000"]Channel 7[/COLOR]**)

```
The carl9170 driver was loaded for your usb wireless adapter (whichever you used), but b43 shouldn't have been loaded at all. I wonder if you tried something other than what has been recommended in this thread so far.

Please post the outputs of -
```
grep -v ^# /etc/modules
grep -v ^# /etc/rc.local
```

---

### Post by RikardSvenningsen on 2013-11-10
Not on purpose.
I did what you told me to do, then I found that it worked but on 28Mhz, then I tried my USB Zyxel NWD271N witch didn't work before ether... That worked just fine and faster.... That's all. Then I did run the Wireless script again, but probably not after a restart.
I have made a restart of my computer now and this is what come out:
```

rs@E6430-2Linux:~/tmp$ grep -v ^# /etc/modules 

lp
rtc
lp
rtc
rs@E6430-2Linux:~/tmp$ grep -v ^# /etc/rc.local 

exit 0
rs@E6430-2Linux:~/tmp$ 

```

And this is a new wireless script dump also after reboot.
```


*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tcbqw53951fgk"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:36   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387185  0 
mac80211              596969  2 b43,brcmsmac
cfg80211              479757  3 b43,brcmsmac,mac80211
ssb                    57932  1 b43
bcma                   46670  3 b43,brcmsmac

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tcbqw53951fgk 1] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           26 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Fiber:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Waoo:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA2
    TDC-07AC:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Tilgin-7y5Axz7K8hZK: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    Tilgin-FPya96KcSkT9: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    *tcbqw53951fgk:  Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 68 WPA2
    HomeBox-941C:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2

    DNS:             192.168.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"tcbqw53951fgk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000207421b307
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D7463627177353339353166676B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA90050F204104A00011010440001021057000101103B0001031047001063041253101920061228744401825A001021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000012fa32679
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00054669626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 03 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Waoo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e3b7735c
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000457616F6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TDC-07AC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c29e1d5b5
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00085444432D30374143
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084661737433357878102400043132333410420004353637381054000800060050F20400011011001146617374333578782D536167656D204150100800020084103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-FPya96KcSkT9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007434e77020
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 001354696C67696E2D4650796139364B63536B5439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B000103104700106581B9C4FA605DBBB91B31FFC69194711021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303832333839331054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101


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

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B797CFD1C70935B62C35EE
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
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
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0586:0x3417 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[    3.698111] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    3.698145] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    3.698171] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    3.698233] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    3.710485] bcma: bus0: Bus registered
[    3.724867] Bluetooth: can't load firmware, may not work correctly
[    3.764225] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[    3.764230] b43: probe of bcma0:0 failed with error -524
[    3.774842] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    3.780666] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    4.414333] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    4.414342] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    4.414915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.415098] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.202019] wlan0: authenticate with <MAC address removed>
[    6.205765] wlan0: send auth to <MAC address removed> (try 1/3)
[    6.207149] wlan0: authenticated
[    6.209444] wlan0: associate with <MAC address removed> (try 1/3)
[    6.213930] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[    6.216018] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[    6.216021] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[    6.216026] wlan0: associated
[    6.216033] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   10.221743] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

****************** done ******************

```
I am sorry if I did something wrong. :(

---

### Post by varunendra on 2013-11-10
There's nothing to be sorry about, as there is probably nothing a simple user like you could do any better about the wifi. These are coding confusions/conflicts of which you are just a victim for the moment.

Fortunately, it's not a serious one. I still don't understand why the b43 module is loading, the usual suspects (/etc/modules and rc.local files) came out clean.

Try this now -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Then reboot and check -
```
lsmod | egrep 'bcma|b43'
```
Does b43 still show up in lsmod? Or just brcmsmac?

If just brcmsmac, is there any improvement in the speed?

---

### Post by RikardSvenningsen on 2013-11-10
Hi
This is the result:
```

rs@E6430-2Linux:~$ lsmod | egrep 'bcma|b43'
bcma                   46670  2 brcmsmac

```

But it goes from 1Mhz to 56Mhz, but it is unstable and mostly not working.
This is a new wireless script output:
```


*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tcbqw53951fgk"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:49   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tcbqw53951fgk 1] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
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
    Fiber:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Waoo:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA2
    TDC-07AC:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Tilgin-FPya96KcSkT9: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    Tilgin-7y5Axz7K8hZK: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    *tcbqw53951fgk:  Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 37 WPA2
    linksysD206:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2

    DNS:             192.168.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"tcbqw53951fgk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025850a7a2e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000D7463627177353339353166676B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA90050F204104A00011010440001021057000101103B0001031047001063041253101920061228744401825A001021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Waoo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000de88e2a8
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000457616F6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TDC-07AC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b24cc172
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00085444432D30374143
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084661737433357878102400043132333410420004353637381054000800060050F20400011011001146617374333578782D536167656D204150100800020084103C000101
          Cell 04 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005a3e452e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 00054669626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-FPya96KcSkT9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000079457c994e
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 001354696C67696E2D4650796139364B63536B5439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B000103104700106581B9C4FA605DBBB91B31FFC69194711021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303832333839331054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-7y5Axz7K8hZK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000794a64f5bc
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 001354696C67696E2D37793541787A374B38685A4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B00010310470010A755B6B7082B5E1F9BD54864476E03621021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303535393035321054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101
          Cell 07 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"linksysD206"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026c2cbf1c3
                    Extra: Last beacon: 2180ms ago
                    IE: Unknown: 000B6C696E6B73797344323036
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 0406000100000000
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0E0050F204104A0001101044000101


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
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    5.322706] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    5.322736] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    5.322761] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    5.322807] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    5.335895] bcma: bus0: Bus registered
[    5.428139] Bluetooth: can't load firmware, may not work correctly
[    5.483778] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    5.492899] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    6.675988] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    6.676001] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    6.676608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.677067] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.452604] wlan0: authenticate with <MAC address removed>
[    8.456385] wlan0: send auth to <MAC address removed> (try 1/3)
[    8.457802] wlan0: authenticated
[    8.459972] wlan0: associate with <MAC address removed> (try 1/3)
[    8.464133] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[    8.466278] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[    8.466283] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[    8.466291] wlan0: associated
[    8.466300] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.675208] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

****************** done ******************

```

The result of the last change, is more unstable, but it seems to be able to connect with faster speed, not that it perform better.. :(

Just made a speed test:
Download = 29490 Kbits
Upload = 9850Kbit

I should be able to get 90/90 Mbit on wire speed.

---

### Post by varunendra on 2013-11-10
Now everything looks as it should be by default (except the blacklist entries for b43 and ssb, which appear to have been entered twice somehow but it doesn't hurt). Anything beyond this is going to be 'additional' tweaking for performance which shouldn't have been needed but looks like it is in our case.

You can start with optimizing the channel. Linux drivers usually work better with channels 1 or 11, so please try changing the channel in the router to either of them (channel 1 seems to be best choice from the perspective of "least interference"). Save the change in the router and reboot. See if you get any better speed (try both 1 and 11 and compare the performance).

If that alone doesn't help, also try a few 'fixed' speeds. For example, to fix the speed at 48 Mb/s -
```
sudo iwconfig wlan0 rate 48M
```
The other supported speeds appear to be 24 Mb/s; 36 Mb/s; 54 Mb/s as per "iwlist scan" results. But of course you can try higher (multiples of them) speeds if N-band (b/g/**n**) support is enabled in the router, and these lower speeds seem to be stable enough to try higher ones.

If fixing the speed seems to have negative effect, reset it with "auto" -
```
sudo iwconfig wlan0 rate auto
```
Let me know how it goes.

**PS:**
Oh, by the way, preventing b43 from loading shouldn't make it "more unstable" in any way. If anything, it should only help by 'Not' conflicting with the correct driver over resources.

---

### Post by RikardSvenningsen on 2013-11-12
Hi
I have more trouble now than "before the first fix". Now I have tried the last to commands, but it didn't get more stable.
Then I run all the previous commands again. I don't have any reason to suspect that it should help, but I find it a little more stable now.
But it's still not as great as you told me to expect, it's running from 1Mhz to 72Mhz but mostly around 1Mhz.
But now it connect more or less instant, witch it didn't do before I run all the previous command again.

My wireless router is a Netgear N300 (JWNR2000V2). On my Work I use Apple Airport Extreme (not the latest version). I got the same issue... 
Her is a fresh cut from my wireless output.
```


*************** info trace ***************

***** uname -a *****

Linux E6430-2Linux 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0534]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0015]
	Kernel driver in use: bcma-pci-bridge

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:643f Microdia 
Bus 001 Device 005: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"tcbqw53951fgk"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC address removed>   
          Bit Rate=28.9 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:217  Invalid misc:7   Missed beacon:0


***** rfkill *****

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              596969  1 brcmsmac
cfg80211              479757  2 brcmsmac,mac80211
bcma                   46670  2 brcmsmac

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [tcbqw53951fgk 1] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           28 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Fiber:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 62 WPA2
    TDC-07AC:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Waoo:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Tilgin-FPya96KcSkT9: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    *tcbqw53951fgk:  Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 71 WPA2
    Tilgin-7y5Axz7K8hZK: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA

  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2

    DNS:             192.168.1.2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"tcbqw53951fgk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000025158f262c
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D7463627177353339353166676B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA90050F204104A00011010440001021057000101103B0001031047001063041253101920061228744401825A001021000D4E4554474541522C20496E632E102300174A574E5232303030763228576972656C657373204150291024000A4A574E523230303076321042000830303030303030301054000800060050F2040001101100174A574E5232303030763228576972656C657373204150291008000220081049000600372A000120
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Waoo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000010344981b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000457616F6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e2278de7
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00054669626572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1604000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TDC-07AC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b78876536
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00085444432D30374143
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210005536167656D102300084661737433357878102400043132333410420004353637381054000800060050F20400011011001146617374333578782D536167656D204150100800020084103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-FPya96KcSkT9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dc86957ce
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 001354696C67696E2D4650796139364B63536B5439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B000103104700106581B9C4FA605DBBB91B31FFC69194711021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303832333839331054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Tilgin-7y5Axz7K8hZK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000021a5dc9fd8
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 001354696C67696E2D37793541787A374B38685A4B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444B20010D14
                    IE: Unknown: DD8A0050F204104A00011010440001021057000101103B00010310470010A755B6B7082B5E1F9BD54864476E03621021000954696C67696E20414210230006484731333131102400012D104200175636303230303030303030302D303031303535393035321054000800060050F20400011011000C486F6D652047617465776179100800020000103C000101


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
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-13-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    5.073645] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    5.073687] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    5.073813] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    5.073878] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    5.086889] bcma: bus0: Bus registered
[    5.190353] Bluetooth: can't load firmware, may not work correctly
[    5.261631] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    5.268071] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    6.409034] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    6.409046] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    6.409646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.410129] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.201656] wlan0: authenticate with <MAC address removed>
[    8.205421] wlan0: send auth to <MAC address removed> (try 1/3)
[    8.206852] wlan0: authenticated
[    8.208955] wlan0: associate with <MAC address removed> (try 1/3)
[    8.213051] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[    8.215193] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[    8.215199] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[    8.215208] wlan0: associated
[    8.215217] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   12.385814] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  102.881324] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  102.891429] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  102.891442] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  102.891446] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  110.434696] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  110.434712] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  110.435333] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  112.209327] wlan0: authenticate with <MAC address removed>
[  112.212757] wlan0: send auth to <MAC address removed> (try 1/3)
[  112.214177] wlan0: authenticated
[  112.216415] wlan0: associate with <MAC address removed> (try 1/3)
[  112.224148] wlan0: RX AssocResp from <MAC address removed> (capab=0x1431 status=0 aid=2)
[  112.226108] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  112.226118] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  112.226133] wlan0: associated
[  112.226149] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  112.291477] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  112.324247] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  239.481721] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  239.483038] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  239.483054] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  239.483061] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  239.684768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  641.676612] Bluetooth: can't load firmware, may not work correctly
[28551.185400] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[28551.185416] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[28551.186006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28553.108770] wlan0: authenticate with <MAC address removed>
[28553.111876] wlan0: send auth to <MAC address removed> (try 1/3)
[28553.113355] wlan0: authenticated
[28553.115327] wlan0: associate with <MAC address removed> (try 1/3)
[28553.119368] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[28553.121480] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[28553.121487] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[28553.121499] wlan0: associated
[28553.121512] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28556.399747] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[28591.007622] wlan0: disassociated from <MAC address removed> (Reason: 15)
[28591.050836] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[28591.050851] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[28591.050854] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[28591.066802] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[28591.998706] wlan0: authenticate with <MAC address removed>
[28592.000195] wlan0: send auth to <MAC address removed> (try 1/3)
[28592.004270] wlan0: authenticated
[28592.005911] wlan0: associate with <MAC address removed> (try 1/3)
[28592.010010] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[28592.012119] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[28592.012126] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[28592.012130] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[28592.012141] wlan0: associated
[28764.215592] brcmsmac bcma0:0: phyerr 0x20, rate 0xa

****************** done ******************

```

---

