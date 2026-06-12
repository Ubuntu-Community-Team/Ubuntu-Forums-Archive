---
title: "strong wifi-signal but very slow browsing"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by berthold-t on 2014-02-18
Using 2 yagi antennas and a usb-wireless adapter with RTL8187 inside I recently established a wifi connection over 500m in rural environment  (no other wifi networks for miles). Signal strength is ok and torrents  download as fast as with cable connection. Browsing is almost  impossible. Almost all the connections time out.
Below the result of the wireless script ubuntu member varunendra recommended to another user.
I tried all variations of encryption, including no encryption and now  Access Control by MAC Address. Also tried wicd - no improvement so back  to gnome network manager. Even removed the two other machines from the  lan that are connected by wire. Any suggestions anybody?
The same hardware worked ok with previous ubuntu 11.04 but in another environment (boat/shore) two years ago.
Here is the wireless text

```
 

*************** info trace ***************

***** uname -a *****

Linux b-Lenovo-IdeaPad-S10-2 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
    Subsystem: Lenovo Device [17aa:389e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 019: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0241 Acer, Inc BisonCam, NB Pro
Bus 001 Device 020: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 021: ID 1d57:0016  

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:79   Missed beacon:0


***** rfkill *****

0: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** lsmod *****

rtl8187                56323  0 
mac80211              436493  1 rtl8187
cfg80211              178877  2 rtl8187,mac80211
eeprom_93cx6           12687  1 rtl8187

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [xxxxxx] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *PLDTMyDSL:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1



- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

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
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000aa5e1173
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 0009504C44544D7944534C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607051300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407051300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160


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

***** modinfo *****

filename:       /lib/modules/3.2.0-58-generic-pae/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     3FC4C17E287B57D0CA62625
alias:          usb:v1737p0073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6232d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v114Bp0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p010Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p11F2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.2.0-58-generic-pae SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   15.741417] ieee80211 phy0: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   15.762693] rtl8187: Customer ID is 0x00
[   15.764646] Registered led device: rtl8187-phy0::radio
[   15.767248] Registered led device: rtl8187-phy0::tx
[   15.769849] Registered led device: rtl8187-phy0::rx
[   15.770673] rtl8187: wireless switch is on
[   25.218301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.337299] wlan0: authenticate with <MAC address removed> (try 1)
[   30.345298] wlan0: authenticated
[   30.573420] wlan0: associate with <MAC address removed> (try 1)
[   30.772096] wlan0: associate with <MAC address removed> (try 2)
[   30.774924] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   30.774937] wlan0: associated
[   30.779690] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  590.017372] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  594.157032] ieee80211 phy1: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  594.181940] rtl8187: Customer ID is 0x00
[  594.182363] Registered led device: rtl8187-phy1::radio
[  594.182687] Registered led device: rtl8187-phy1::tx
[  594.183005] Registered led device: rtl8187-phy1::rx
[  594.183785] rtl8187: wireless switch is on
[  596.694489] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  601.945418] wlan0: direct probe to <MAC address removed> (try 1/3)
[  602.144274] wlan0: direct probe to <MAC address removed> (try 2/3)
[  602.148416] wlan0: direct probe responded
[  602.148531] wlan0: authenticate with <MAC address removed> (try 1)
[  602.348123] wlan0: authenticate with <MAC address removed> (try 2)
[  602.349694] wlan0: authenticated
[  602.593454] wlan0: associate with <MAC address removed> (try 1)
[  602.597155] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  602.597175] wlan0: associated
[  602.602457] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  876.935007] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4880.447866] ieee80211 phy2: hwaddr <MAC address removed>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 4880.479788] rtl8187: Customer ID is 0x00
[ 4880.479948] Registered led device: rtl8187-phy2::radio
[ 4880.480095] Registered led device: rtl8187-phy2::tx
[ 4880.480186] Registered led device: rtl8187-phy2::rx
[ 4880.481282] rtl8187: wireless switch is on
[ 4885.334198] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4890.737385] wlan0: authenticate with <MAC address removed> (try 1)
[ 4890.742024] wlan0: authenticated
[ 4890.993395] wlan0: associate with <MAC address removed> (try 1)
[ 4890.995829] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4890.995843] wlan0: associated
[ 4891.000322] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

```

---

### Post by steeldriver on 2014-02-18
Have you tried reducing the MTU?

---

### Post by fdrake on 2014-02-18
your /etc/resolv.conf is empty should you have your name server there.

go to your roter settings and search for your Domain Name(under "Status")
make sure that your /etc/resolv.conf these these 2 lines
```

nameserver 127.0.0.1
search your.domain.name.here

```

do not edit directly the file, but follow this instructions (the first suggestion): [http://askubuntu.com/questions/201603/how-do-i-edit-my-resolv-conf-file](http://askubuntu.com/questions/201603/how-do-i-edit-my-resolv-conf-file)

---

### Post by varunendra on 2014-02-18
> **fdrake said:**
> your /etc/resolv.conf is empty should you have your name server there.
Yup, I'm also stumped to see no DNS in the nm-tool part.

@berthold-t, how have you configured your DNS. Manually, or is it supplied via DHCP?

> **berthold-t said:**
> I tried all variations of encryption, including no encryption.... 
..but the current variation is what we can probably call the worst -
> **berthold-t said:**
> ```

  Wireless Access Points (* = current AP)
    *PLDTMyDSL:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 56 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**

```
Please change it to pure WPA2-AES(CCMP). No mixed mode, no TKIP.

I'm also a little confused with this part -
> **berthold-t said:**
> torrents download as fast as with cable connection. Browsing is almost impossible
So can we assume that the download/transfer speed is good? Only opening of pages is slow?

If so, then it is almost certainly a DNS issue, which should be easily fixable.

---

### Post by berthold-t on 2014-02-18
yes, I have tried that earlier: no luck

---

### Post by berthold-t on 2014-02-18
> **fdrake said:**
> your /etc/resolv.conf is empty should you have your name server there.

go to your roter settings and search for your Domain Name(under "Status")
make sure that your /etc/resolv.conf these these 2 lines
```

nameserver 127.0.0.1
search your.domain.name.here

```

do not edit directly the file, but follow this instructions (the first suggestion): [http://askubuntu.com/questions/201603/how-do-i-edit-my-resolv-conf-file](http://askubuntu.com/questions/201603/how-do-i-edit-my-resolv-conf-file)

THANKS ALOT! I followed the procedure given in that link and it works fine now!

---

### Post by fdrake on 2014-02-18
u r welcome. 
Make sure to mark the thread as "Solved" please for future reference.

---

