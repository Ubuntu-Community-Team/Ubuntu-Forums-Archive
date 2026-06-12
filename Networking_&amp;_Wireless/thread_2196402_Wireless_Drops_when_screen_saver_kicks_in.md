---
title: "Wireless Drops when screen saver kicks in"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by paxo.spud on 2013-12-29
I have a strange problem that after quite a bit of searching can't find the answer to.

I'm using a Dell D610 with a newly installed copy of Ubuntu 13.10. I'm not an expert user but know my way around a computer.

The problem is that if I'm downloading a large file and leave the machine running, as soon as the screen switches to screensaver the network connection drops. I've made sure that the options are set not to do anything when the lid is closed and that it should never suspend but I still get this issue.

I have set the screen not to lock.

It's a bit frustrating that it does this as I keep having to restart the download at the beginning.

Does anyone have any ideas how I can stop the Wi-Fi from stopping?

---

### Post by varunendra on 2014-01-02
Welcome to the forums paxo.spud!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by paxo.spud on 2014-01-02
Here you are Varun
```

*************** info trace ***************

***** uname -a *****

Linux delboy-Latitude-D610 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:104  Invalid misc:978   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   356285  0 
bcma                   40966  1 b43
mac80211              513247  1 b43
cfg80211              401436  2 b43,mac80211
ssb                    51596  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ASUS 1] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA2
    O2wireless701679:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    O2wireless_EXT:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    virginmedia5023329: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    TNCAP06D57E:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2

  IPv4 Settings:
    Address:         192.168.1.126
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


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
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4454ed31b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0505001E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"TNCAP06D57E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000B544E434150303644353745
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B00010310470010E29841D4B449595B9535FA82FD2BE9C21021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E10420009313331395A463635521054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"virginmedia9553152"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014d06d2a150
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001276697267696E6D6564696139353533313532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010C7B524FB104B621550B920DFC9E860C8102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"virginmedia5023329"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aed52a4c64
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 001276697267696E6D6564696135303233333239
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B000103104700107085B7D791CE146819EE4AA7ACD54220102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"O2wireless_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ecca3306
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E4F32776972656C6573735F455854
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700108F08D5037C8A0C75E86323F04BB8C6CA1021000D4E4554474541522C20496E632E10230008574E33303030525010240008574E3330303052501042000230311054000800060050F204000110110008574E333030305250100800020084103C000101
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


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

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 
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

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4318 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    1.584081] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.584093] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.584101] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.584108] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.584116] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.624125] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[   15.421733] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.469743] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   19.844043] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.912642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.916832] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.364853] wlan0: authenticate with <MAC address removed>
[   45.376655] wlan0: send auth to <MAC address removed> (try 1/3)
[   45.380676] wlan0: authenticated
[   45.384039] wlan0: associate with <MAC address removed> (try 1/3)
[   45.386478] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[   45.386966] wlan0: associated
[   45.386995] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9430.500051] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 9431.694496] wlan0: authenticate with <MAC address removed>
[ 9431.694757] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9431.700538] wlan0: authenticated
[ 9431.704223] wlan0: associate with <MAC address removed> (try 1/3)
[ 9431.706515] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=3)
[ 9431.707239] wlan0: associated
[27555.973559] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[27564.136199] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[27564.195827] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27590.341778] wlan0: authenticate with <MAC address removed>
[27590.344559] wlan0: send auth to <MAC address removed> (try 1/3)
[27590.352071] wlan0: authenticated
[27590.357640] wlan0: associate with <MAC address removed> (try 1/3)
[27590.359936] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=1)
[27590.360423] wlan0: associated
[27590.360458] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

```

---

### Post by varunendra on 2014-01-02
The device and the driver are known to me and they are okay, but the problem you mentioned is somewhat new to me for this combination.

Let's try an available parameter first. Please open a terminal and do -
```
sudo modprobe -rv b43
sudo modprobe -v b43 qos=0
```
Then reconnect and see if it survives the screensaver. The above change is temporary and will be lost at next boot. If it helps, we can make it permanent. If not, try a blind shot -
```
sudo touch /etc/pm/power.d/wireless
```
This will create a blank file "wireless" in /etc/pm/power.d directory which will disable the default power management script on wireless interface. This may help if the power management policy imposed by the script is causing the trouble.

If none of these help, please remove the above experimental file first -
```
sudo rm /etc/pm/power.d/wireless
```
Then connect normally, let the screensaver kick-in, and as soon as the wifi disconnects, run the following commands -
```
dmesg | tail -20
cat /var/log/syslog | tail -60
cat /var/log/pm-powersave.log | tail -40
```
..and post back the entire output here in your next post.

---

### Post by paxo.spud on 2014-01-03
Thanks for that Varun.

I'll give it a whirl over the weekend.

---

