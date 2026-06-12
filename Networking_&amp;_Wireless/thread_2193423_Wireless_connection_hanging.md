---
title: "Wireless connection hanging"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by noyanculum on 2013-12-12
Hello,

I am fairly new to Ubuntu. I use Ubuntu 12.04 LTS.

After launching Ubuntu, I can connect automatically and succesfully to the internet via my wireless lan. But a few minutes later the connection hangs and I can not connect anymore. And many functionalities of Ubuntu does not work either (console commands, file manager). Then I have to hard shut down the system.

In fact Ive had any problem until some days ago. I installed an Nvidia graphics card to my configuration. This connection problem started after that day. That's why I think there may be a problem between the graphics card and wireless donghy.

I don't know how to inspect and solve the problem. Could anyone please kindly lead me to do the necessary checks and solutions.

Thanks in advance.

---

### Post by Bucky Ball on 2013-12-13
First thing to do would be to disable the Nvidia driver, presuming you installed one, and verify that is the cause if that's when the errors started happening. Can you simply disable it in 'Additional Drivers' and reboot? Let us know.

Not sure that the physical hardware will make much difference to a USB dongle so thinking software that came for the card. Your post implies you are using a wireless USB dongle?

---

### Post by noyanculum on 2013-12-14
Hello Bucky Ball, thank you for replying.

I did completely uninstall the Nvidia drivers via Synaptic Package Manager, I removed Nvidia graphics card from the motherboard and I tried the system with my old onboard graphics card. The problem still continues. After 1-2 minutes of usage, the wireless connection hangs permanently. (Now I reinstall Nvidia card)

Yes I use a wireless USB dongle. It has been working like a charm until the day I changed the graphics card. I installed a lot of critical packages at that day: drivers, kernel, gtk3, and tons of critical packages... So probably some of them affect somethings.

What can I do to find the problem?

---

### Post by varunendra on 2013-12-14
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by noyanculum on 2013-12-14
Hello Varunendra,

I run your script. I will paste below 2 results. The first one is when the connection works. The second one is when the connection does not work. When my connection hanged (the second one), the script is stopped in ***** iwlist ***** stage.

Thanks in advance.

The script output when the connection alive:
```


*************** info trace ***************

***** uname -a *****

Linux Ubuntu1 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: Elitegroup Computer Systems Device [1019:2048]
	Kernel driver in use: atl2

***** lsusb *****

Bus 001 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan1     IEEE 802.11bg  ESSID:"CeptekiDunya"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:35  Invalid misc:30   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

rt73usb                31676  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20779  1 rt73usb
rt2x00lib              55559  2 rt73usb,rt2x00usb
mac80211              630977  2 rt2x00usb,rt2x00lib
cfg80211              525326  2 rt2x00lib,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan1  [CeptekiDunya 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
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
    CeptekiDunya:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    dmn:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Broadcom:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    *CeptekiDunya:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl2
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
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"CeptekiDunya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000276116c560
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000C43657074656B6944756E7961
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706545200010D10
                    IE: Unknown: DD9D0050F204104A0001001044000102103B00010310470010BC329E001DD811B2860110FEED5DF9721021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020004103C000100
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"CeptekiDunya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002760be5183
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 000C43657074656B6944756E7961
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1100000000000000000000000000000000000000
                    IE: Unknown: DD090010180201102C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Broadcom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ba0cb8d16
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000842726F6164636F6D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


***** resolv.conf *****

nameserver 127.0.0.1

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

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     246FEEC23EA0D5DB663C1D3
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B2734411C831D4AF35167D6
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     101F39DDF5F96BC8EA5BF21
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (atl2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x07d1:0x3c07 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x07d1:0x3c07 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   19.176957] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.177254] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.764519] wlan1: authenticate with <MAC address removed>
[   22.786356] wlan1: direct probe to <MAC address removed> (try 1/3)
[   22.988013] wlan1: direct probe to <MAC address removed> (try 2/3)
[   23.192016] wlan1: direct probe to <MAC address removed> (try 3/3)
[   23.396013] wlan1: authentication with <MAC address removed> timed out
[   23.532341] wlan1: authenticate with <MAC address removed>
[   23.535600] wlan1: send auth to <MAC address removed> (try 1/3)
[   23.736012] wlan1: send auth to <MAC address removed> (try 2/3)
[   23.940013] wlan1: send auth to <MAC address removed> (try 3/3)
[   24.144014] wlan1: authentication with <MAC address removed> timed out
[   27.788064] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[   36.732606] wlan1: authenticate with <MAC address removed>
[   36.752990] wlan1: send auth to <MAC address removed> (try 1/3)
[   36.956017] wlan1: send auth to <MAC address removed> (try 2/3)
[   37.122950] wlan1: authenticated
[   37.124033] wlan1: associate with <MAC address removed> (try 1/3)
[   37.328013] wlan1: associate with <MAC address removed> (try 2/3)
[   37.532013] wlan1: associate with <MAC address removed> (try 3/3)
[   37.736018] wlan1: association with <MAC address removed> timed out
[   37.872377] wlan1: authenticate with <MAC address removed>
[   37.874852] wlan1: send auth to <MAC address removed> (try 1/3)
[   38.076014] wlan1: send auth to <MAC address removed> (try 2/3)
[   38.280014] wlan1: send auth to <MAC address removed> (try 3/3)
[   38.484012] wlan1: authentication with <MAC address removed> timed out
[   42.877999] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[   64.804621] wlan1: authenticate with <MAC address removed>
[   64.827615] wlan1: send auth to <MAC address removed> (try 1/3)
[   64.836461] wlan1: authenticated
[   64.840037] wlan1: associate with <MAC address removed> (try 1/3)
[   65.044014] wlan1: associate with <MAC address removed> (try 2/3)
[   65.151579] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   65.162051] wlan1: associated
[   65.162100] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

****************** done ******************

```



And here is the script output when the connection hangs:
```


*************** info trace ***************

***** uname -a *****

Linux Ubuntu1 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L2 Fast Ethernet [1969:2048] (rev a0)
	Subsystem: Elitegroup Computer Systems Device [1019:2048]
	Kernel driver in use: atl2

***** lsusb *****

Bus 001 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan1     IEEE 802.11bg  ESSID:"CeptekiDunya"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:FE:ED:5D:F9:72   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:53  Invalid misc:34   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

rt73usb                31676  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20779  1 rt73usb
rt2x00lib              55559  2 rt73usb,rt2x00usb
mac80211              630977  2 rt2x00usb,rt2x00lib
cfg80211              525326  2 rt2x00lib,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan1  [CeptekiDunya 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             connected
  Default:           yes
  HW Address:        00:24:01:08:6A:4C

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CeptekiDunya:    Infra, C8:3A:35:49:D5:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    dmn:             Infra, 00:1A:2A:D1:ED:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    Broadcom:        Infra, 38:22:9D:07:E9:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    *CeptekiDunya:   Infra, 10:FE:ED:5D:F9:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl2
  State:             unavailable
  Default:           no
  HW Address:        00:25:11:00:07:42

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
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:25:11:00:07:42,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

```

---

### Post by varunendra on 2013-12-14
Looks like it just hangs on the scanning operation when the connection fails.

Based on the completed info in the first result, please try these -

[indent]**1)** Please change the encryption type in your access points to **WPA2-PSK** with **CCMP**.
Currently, one of your access points is using WPA2, but with **TKIP** (strongly discouraged). The other one is using CCMP, but with WPA (1). As per what I have gathered so far, this combination shouldn't even be possible. Since both these access-points have same SSID, I suspect it is this weird combination that may be causing the wifi to hang when trying to switch to this other AP.

Even if the change doesn't help, keep it as recommended.

**2)** If the above one doesn't help, try turning the power management off on the wifi -
```
sudo iwconfig wlan1 power off
```
Then check -
```
iwconfig
```
Does the "Power Management" appears to be turned off? It should stay off even after reboot. Does it help?

**3)** If not, try a parameter with the driver -
```
sudo modprobe -rv rt73usb
sudo modprobe -v rt73usb nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. If it helps, we can make it permanent.

**4)** Your udev rules file is a bit unusual (double entry for the same USB wifi device). I recommend deleting it -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
It will be regenerated automatically on next boot or when you replug the usb adapter, with only two entries this time. Please note that this will cause the wifi adapter's logical name to change from "wlan1" to "wlan0" again. So if you need to try the point 2 above again, make sure to use the correct logical name of the interface.
[/indent]

Try these for now and let us know which one works, if any. If none of above helps, please post the following output when it hangs again -
```
dmesg | grep rt73
```

---

### Post by noyanculum on 2013-12-14
Dear Varunendra thank you for replying,

The 3. step give me an error message

```

FATAL: Module rt37usb not found

```

 May this be the reason of the problem?

EDIT: Oops sorry it should be rt73usb :)

---

### Post by noyanculum on 2013-12-14
Dear Varunendra,

STEP 1. I couldnt make that. Because the main access point's encryption is WPA2-PSK with TKIP/AES. There is not a CCMP option. And I can not modify the other access point for instant.

But I don't think this is the reason of my problem. Because I have 2 computers on my table now, Both of them are running Ubuntu 12.04 and both having the same USB dongle. The other computer (which one I use right now to write you these lines) connects perfectly.

Plus, the computer which has problems was working like a charm as well, until 2 days ago. In this wireless LAN, with this dongle...

STEP 2-3-4: I tried these steps but nothing changed. Wireless still hanging.

STEP 5: Here is the output:
```

$ dmesg | grep rt73
[    9.557751] usbcore: registered new interface driver rt73usb

```

---

### Post by varunendra on 2013-12-15
> **noyanculum said:**
> the main access point's encryption is WPA2-PSK with TKIP/AES. There is not a CCMP option.
Sorry, I should have mentioned that AES and CCMP are the same thing. It should have the option to use AES only (anything but TKIP alone or combined). Choose that one.

> But I don't think this is the reason of my problem. Because I have 2 computers on my table now, Both of them are running Ubuntu 12.04 and both having the same USB dongle. The other computer (which one I use right now to write you these lines) connects perfectly.
I agree that the problem may be something other than the encryption. But the WPA+CCMP is a weird combination and the WPA2+TKIP is a common but poor combination (performance wise). This may be adding to the problem if not causing it. Hence it is better to keep it as recommended if you can.

When the wireless hangs, you mentioned that the "command console" hangs as well. By "command console", do you mean the terminal? If yes, how did you manage to get the output of dmesg 'After' it hung? The output you got tells nothing about a problem, it is from when the driver was initially probed.

From the symptoms and details we have shared so far, there is a fair chance that the wireless problem may be the result of some other bigger problem, not the cause of it. In that case, the log files in **/var/log** directory may shed some light on it, especially dmesg, syslog, kern.log and Xorg.0.log files. Since we have no clue what to look for and these files are usually huge, you may try to look at them yourself and report back anything that looks suspicious.

Please note that dmesg.0, syslog.1 kern.log.1 etc. usually contain the messages from the previous session (although they can also contain messages from the same session if the session is too long (a day long or more)). So if the system gets totally hung in a way that you can't even read these files, try finding relevant messages in these files instead.

---

### Post by noyanculum on 2013-12-15
Dear Varunendra,

Thank you for giving your time to that error.

 In fact, before posting this post I made all possible researches I could and I tried everything I found on similar forum threads. My main problem is, as you said, there is no clue to find the reason of the problem.

A. ACCESS POINT CONFIGURATION:
I will do the access point setups you recommend.

B. SYSTEM HANG:
When I mention "command console" hangs as well: sorry I shortened something to not take your time too much. It is happining like that:
1. I boot Ubuntu, everything start good, no problem.
2. I open Firefox and I visit 2-3 web pages, no problem. (I generated 1. wireless script at this stage)
3. Then the connection hangs, I can not visit web pages anymore.
 4. During 1-2 minutes, the file manager and the terminal work. The terminal works at this stage but it hangs when running some commands, like "iwlist". (I generated 2. wireless script at this stage)
 5. After 1-2 minutes, the file manager and the terminal become completely unresponsive. I can not launch the file manager at all. I can launch the terminal, but it stay unresponsive for any command.

 Note: During the stages 3-4-5 above, if I plug the wireless dongle out, all system starts to work normal again (with no internet connection of course).
Note 2: I also tried different usb dongles. The connection hangs always.

C. /VAR/LOG RESEARCH
I did already do that, but I couldn't find something. I am going to do it now again.

D. MAYBE ANOTHER POSSIBILITY (INAPPROPRIATE WAY):
 I found out on the forum posts that some people use a program called "Windows Wireless Drivers" (ndiswrapper). I think to give a try to it as well, if I can not find something after log research.

---

### Post by Bucky Ball on 2013-12-15
I've been following this and starting to think that this is not down to wireless but, as varunendra alluded to earlier, something other. The wireless is a clue rather than a cause. The fact that the terminal and file manager are also locking up points at something other than network problems, particularly if the wireless was problem free until recently and suddenly things went pear-shaped.

Just out of curiousity, do you have web pages already open when you open Firefox or are you opening to a completely clean, one tab open Firefox at the home page (your search engine)? I'm wondering if one of the pages you have open is sending junk and locking things up. 

Try opening Firefox, close all tabs, close Firefox and reboot. Open Firefox. Things still the same. 

Anyhow, if this was simply a wireless issue, the wireless would die and that would be it. That other things are also going awry points elsewhere perhaps ...

PS: I would take out the new graphics card (physically) for the moment just to rule that out for now.

---

### Post by varunendra on 2013-12-15
I have seen this driver for the first time and don't know how well it works (or is supposed to work). So yes, ndiswrapper may be worth a try. At least we can see if the problem remains the same or disappears (or changes) when not using the current driver.

I hope you have found a good guide on installing ndiswrapper, since my knowledge about it is not very up to date. Make sure to use windows XP driver, not win7 or vista. You may also need to find 64 bit driver, since your Ubuntu installation is 64 bit.


**EDIT:**
Sorry bb, your post wasn't there when I started typing mine ;)

@noyanculum, please follow what Bucky Ball suggested. Preferably before you try ndiswrapper which is usually our last resort.

---

### Post by Bucky Ball on 2013-12-15
Yes, ndiswrapper DEFINITELY a last resort. You could well be opening a whole other bunch of issues using that. Largely obsolete.

There are lots of reports of this USB dongle working fine without ndiswrapper. You might try using this to install the correct driver easily.

[http://www.ubuntugeek.com/gui-installer-for-rt73-ralink-devices-beta.html](http://www.ubuntugeek.com/gui-installer-for-rt73-ralink-devices-beta.html)

And here:

[https://duckduckgo.com/?q=rt73usb+ubuntu](https://duckduckgo.com/?q=rt73usb+ubuntu)

Lots of success. Which is why I'm thinking this isn't about the wireless card. My money still on the graphics card which, as I suggested in my last post, should be removed so you are back to square one and, hardware-wise, in the same state as before the problems started.

---

### Post by noyanculum on 2013-12-15
Bucky Ball and Varunendra,

Thank you for replies and suggestions. Yes I will try ndiswrapper as a last choice, because I want my system works on its original way.
@Bucky Ball: I tried all of the start page combinations: clean page, google, other websites... The issue is always same. (Thanks to unlimited different tries, I read all of the news on newspapers today lol)

Before trying to remove graphics card again, etc.. I made some researches on the syslog file. I will give you first a list of my steps -so you can understand syslog records better-, then I will give you the syslog records. It would be really great if you can have a look at it, my production is really suspended because of this problem.

These are step by step what I did:
1. [11:34:50] I turned Ubuntu on.
2. [11:39:30] I launched Firefox via terminal command, I visited some newspaper pages
3. [11:40:00] The wireless connection hanged
4. [11:42:41] I closed Firefox and terminal
5. [11:44:41] I made Alt+F2 and I fired "Gksudo Nautilus" (No response)
6. [11:45:11] I plugged the usb wireless dongle out
7. Then I checked /var/log/syslog.


Now I want to give you my syslog records. Please especeially see this line (when the connection was hanged):
```

[11:40:43] Ubuntu1 kernel: [  362.820255] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.

```
Is this error code -110 generic or does it show something?


Ok here is my complete syslog after network manager started:
```

Dec 15 11:34:57 Ubuntu1 NetworkManager[1091]: <info> NetworkManager (version 0.9.4.0) is starting...
Dec 15 11:34:57 Ubuntu1 NetworkManager[1091]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 15 11:34:57 Ubuntu1 modem-manager[935]: <info>  Loaded plugin Linktop
Dec 15 11:34:57 Ubuntu1 modem-manager[935]: <info>  Loaded plugin SimTech
Dec 15 11:34:57 Ubuntu1 modem-manager[935]: <info>  Loaded plugin Sierra
Dec 15 11:34:57 Ubuntu1 modem-manager[935]: <info>  Loaded plugin X22X
Dec 15 11:34:58 Ubuntu1 NetworkManager[1091]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 15 11:34:58 Ubuntu1 NetworkManager[1091]: <info> DNS: loaded plugin dnsmasq
Dec 15 11:34:58 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 15 11:34:58 Ubuntu1 acpid: 37 rules loaded
Dec 15 11:34:58 Ubuntu1 acpid: waiting for events: event logging is off
Dec 15 11:34:58 Ubuntu1 anacron[1128]: Anacron 2.3 started on 2013-12-15
Dec 15 11:34:58 Ubuntu1 anacron[1128]: Normal exit (0 jobs run)
Dec 15 11:34:58 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec 15 11:34:59 Ubuntu1 polkitd[1121]: started daemon version 0.104 using authority implementation `local' version `0.104'
Dec 15 11:34:59 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: init!
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: update_system_hostname
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPluginIfupdown: management mode: unmanaged
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlan1, iface: wlan1)
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: end _init.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    Ifupdown: get unmanaged devices count: 0
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: (25357104) ... get_connections.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: (25357104) ... get_connections (managed=false): return empty list.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    keyfile: parsing CeptekiDunya 1 ... 
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    keyfile:     read connection 'CeptekiDunya 1'
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    keyfile: parsing CeptekiDunya ... 
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320705] vesafb: mode is 640x480x32, linelength=2560, pages=0
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320709] vesafb: scrolling: redraw
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320711] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320719] mtrr: type mismatch for fb000000,200000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320722] mtrr: type mismatch for fb000000,100000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320724] mtrr: type mismatch for fb000000,80000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320726] mtrr: type mismatch for fb000000,40000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320729] mtrr: type mismatch for fb000000,20000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320731] mtrr: type mismatch for fb000000,10000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320733] mtrr: type mismatch for fb000000,8000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320735] mtrr: type mismatch for fb000000,4000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320738] mtrr: type mismatch for fb000000,2000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320740] mtrr: type mismatch for fb000000,1000 old: write-back new: write-combining
Dec 15 11:34:59 Ubuntu1 kernel: [   18.320883] vesafb: framebuffer at 0xfb000000, mapped to 0xffffc90010b80000, using 1216k, total 1216k
Dec 15 11:34:59 Ubuntu1 kernel: [   18.321154] Console: switching to colour frame buffer device 80x30
Dec 15 11:34:59 Ubuntu1 kernel: [   18.321876] fb0: VESA VGA frame buffer device
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    keyfile:     read connection 'CeptekiDunya'
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]:    Ifupdown: get unmanaged devices count: 0
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> modem-manager is now available
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill0) (driver (unknown))
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> Networking is enabled by state file
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): carrier is OFF
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): new Ethernet device (driver: 'atl2' ifindex: 2)
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): now managed
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): bringing up device.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): preparing device.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): using nl80211 for WiFi device control
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <warn> (wlan1): driver supports Access Point (AP) mode
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): new 802.11 WiFi device (driver: 'rt73usb' ifindex: 3)
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): now managed
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): bringing up device.
Dec 15 11:34:59 Ubuntu1 kernel: [   18.556609] atl2 0000:02:00.0: irq 43 for MSI/MSI-X
Dec 15 11:34:59 Ubuntu1 kernel: [   18.556681] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 11:34:59 Ubuntu1 kernel: [   18.556910] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 15 11:34:59 Ubuntu1 kernel: [   18.703987] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): preparing device.
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): deactivating device (reason 'managed') [2]
Dec 15 11:34:59 Ubuntu1 dbus[920]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 15 11:34:59 Ubuntu1 kernel: [   18.704342] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Dec 15 11:34:59 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec 15 11:34:59 Ubuntu1 dbus[920]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> wpa_supplicant started
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: starting -> ready
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: ready -> inactive
Dec 15 11:34:59 Ubuntu1 NetworkManager[1091]: <warn> Trying to remove a non-existant call id.
Dec 15 11:35:01 Ubuntu1 acpid: client connected from 1262[0:0]
Dec 15 11:35:01 Ubuntu1 acpid: 1 client rule loaded
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Auto-activating connection 'CeptekiDunya 1'.
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) starting connection 'CeptekiDunya 1'
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1/wireless): connection 'CeptekiDunya 1' has security, and secrets exist.  No new secrets needed.
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Config: added 'ssid' value 'CeptekiDunya'
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Config: added 'scan_ssid' value '1'
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Config: added 'psk' value '<omitted>'
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> Config: set interface ap_scan to 1
Dec 15 11:35:01 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: inactive -> scanning
Dec 15 11:35:02 Ubuntu1 kernel: [   21.643332] nvidia 0000:01:00.0: irq 44 for MSI/MSI-X
Dec 15 11:35:03 Ubuntu1 wpa_supplicant[1259]: Trying to authenticate with 10:fe:ed:5d:f9:72 (SSID='CeptekiDunya' freq=2412 MHz)
Dec 15 11:35:03 Ubuntu1 kernel: [   22.180646] wlan1: authenticate with 10:fe:ed:5d:f9:72
Dec 15 11:35:03 Ubuntu1 kernel: [   22.239638] wlan1: send auth to 10:fe:ed:5d:f9:72 (try 1/3)
Dec 15 11:35:03 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Dec 15 11:35:03 Ubuntu1 kernel: [   22.278900] NVRM: Your system is not currently configured to drive a VGA console
Dec 15 11:35:03 Ubuntu1 kernel: [   22.278905] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Dec 15 11:35:03 Ubuntu1 kernel: [   22.278907] NVRM: requires the use of a text-mode VGA console. Use of other console
Dec 15 11:35:03 Ubuntu1 kernel: [   22.278908] NVRM: drivers including, but not limited to, vesafb, may result in
Dec 15 11:35:03 Ubuntu1 kernel: [   22.278910] NVRM: corruption and stability problems, and is not supported.
Dec 15 11:35:03 Ubuntu1 acpid: client connected from 1262[0:0]
Dec 15 11:35:03 Ubuntu1 acpid: 1 client rule loaded
Dec 15 11:35:03 Ubuntu1 kernel: [   22.419864] wlan1: authenticated
Dec 15 11:35:03 Ubuntu1 wpa_supplicant[1259]: Trying to associate with 10:fe:ed:5d:f9:72 (SSID='CeptekiDunya' freq=2412 MHz)
Dec 15 11:35:03 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: authenticating -> associating
Dec 15 11:35:03 Ubuntu1 kernel: [   22.424044] wlan1: associate with 10:fe:ed:5d:f9:72 (try 1/3)
Dec 15 11:35:03 Ubuntu1 kernel: [   22.628025] wlan1: associate with 10:fe:ed:5d:f9:72 (try 2/3)
Dec 15 11:35:03 Ubuntu1 kernel: [   22.743227] wlan1: RX AssocResp from 10:fe:ed:5d:f9:72 (capab=0x411 status=0 aid=2)
Dec 15 11:35:03 Ubuntu1 wpa_supplicant[1259]: Associated with 10:fe:ed:5d:f9:72
Dec 15 11:35:03 Ubuntu1 kernel: [   22.753190] wlan1: associated
Dec 15 11:35:03 Ubuntu1 kernel: [   22.753244] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Dec 15 11:35:03 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: associating -> associated
Dec 15 11:35:03 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec 15 11:35:03 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Dec 15 11:35:03 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec 15 11:35:04 Ubuntu1 accounts-daemon[1272]: started daemon version 0.6.15
Dec 15 11:35:04 Ubuntu1 wpa_supplicant[1259]: WPA: Key negotiation completed with 10:fe:ed:5d:f9:72 [PTK=CCMP GTK=TKIP]
Dec 15 11:35:04 Ubuntu1 wpa_supplicant[1259]: CTRL-EVENT-CONNECTED - Connection to 10:fe:ed:5d:f9:72 completed (auth) [id=0 id_str=]
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'CeptekiDunya'.
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> dhclient started with pid 1274
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Beginning IP6 addrconf.
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Dec 15 11:35:04 Ubuntu1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 15 11:35:04 Ubuntu1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 15 11:35:04 Ubuntu1 dhclient: All rights reserved.
Dec 15 11:35:04 Ubuntu1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 15 11:35:04 Ubuntu1 dhclient: 
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Dec 15 11:35:04 Ubuntu1 dhclient: Listening on LPF/wlan1/00:24:01:08:6a:4c
Dec 15 11:35:04 Ubuntu1 dhclient: Sending on   LPF/wlan1/00:24:01:08:6a:4c
Dec 15 11:35:04 Ubuntu1 dhclient: Sending on   Socket/fallback
Dec 15 11:35:04 Ubuntu1 dhclient: DHCPREQUEST of 192.168.1.102 on wlan1 to 255.255.255.255 port 67
Dec 15 11:35:04 Ubuntu1 dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Dec 15 11:35:04 Ubuntu1 dhclient: bound to 192.168.1.102 -- renewal in 116368 seconds.
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info>   address 192.168.1.102
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info>   prefix 24 (255.255.255.0)
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info>   gateway 192.168.1.1
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info>   hostname 'dhcppc2'
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info>   nameserver '192.168.1.1'
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 15 11:35:04 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
Dec 15 11:35:04 Ubuntu1 avahi-daemon[1003]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.102.
Dec 15 11:35:04 Ubuntu1 avahi-daemon[1003]: New relevant interface wlan1.IPv4 for mDNS.
Dec 15 11:35:04 Ubuntu1 avahi-daemon[1003]: Registering new address record for 192.168.1.102 on wlan1.IPv4.
Dec 15 11:35:05 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec 15 11:35:05 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> DNS: starting dnsmasq...
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <error> [1387100105.522694] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <error> [1387100105.522724] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <warn> DNS: plugin dnsmasq update failed
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: started, version 2.59 cache disabled
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: DBus support enabled: connected to system bus
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: warning: no upstream servers configured
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> Policy set 'CeptekiDunya 1' (wlan1) as default for IPv4 routing and DNS.
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) successful, device activated.
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Dec 15 11:35:05 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <warn> dnsmasq appeared on DBus: :1.20
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: setting upstream servers from DBus
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: using nameserver 208.67.220.220#53
Dec 15 11:35:05 Ubuntu1 dnsmasq[1369]: using nameserver 208.67.222.222#53
Dec 15 11:35:05 Ubuntu1 NetworkManager[1091]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
Dec 15 11:35:05 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 15 11:35:06 Ubuntu1 avahi-daemon[1003]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::224:1ff:fe08:6a4c.
Dec 15 11:35:06 Ubuntu1 avahi-daemon[1003]: New relevant interface wlan1.IPv6 for mDNS.
Dec 15 11:35:06 Ubuntu1 avahi-daemon[1003]: Registering new address record for fe80::224:1ff:fe08:6a4c on wlan1.*.
Dec 15 11:35:08 Ubuntu1 gnome-session[1354]: WARNING: Could not parse desktop file /home/noyan/.config/autostart/indicator-weather.desktop: No such file or directory
Dec 15 11:35:08 Ubuntu1 gnome-session[1354]: WARNING: could not read /home/noyan/.config/autostart/indicator-weather.desktop
Dec 15 11:35:09 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec 15 11:35:09 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec 15 11:35:09 Ubuntu1 anacron[1591]: Anacron 2.3 started on 2013-12-15
Dec 15 11:35:09 Ubuntu1 anacron[1591]: Normal exit (0 jobs run)
Dec 15 11:35:11 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec 15 11:35:11 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Successfully called chroot.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Successfully dropped privileges.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Successfully limited resources.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Running.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Canary thread running.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Watchdog thread running.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Successfully made thread 1679 of process 1679 (n/a) owned by '1000' high priority at nice level -11.
Dec 15 11:35:11 Ubuntu1 rtkit-daemon[1681]: Supervising 1 threads of 1 processes of 1 users.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Successfully made thread 1690 of process 1679 (n/a) owned by '1000' RT at priority 5.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Supervising 2 threads of 1 processes of 1 users.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Successfully made thread 1696 of process 1679 (n/a) owned by '1000' RT at priority 5.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Supervising 3 threads of 1 processes of 1 users.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Successfully made thread 1698 of process 1679 (n/a) owned by '1000' RT at priority 5.
Dec 15 11:35:13 Ubuntu1 rtkit-daemon[1681]: Supervising 4 threads of 1 processes of 1 users.
Dec 15 11:35:14 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec 15 11:35:14 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec 15 11:35:20 Ubuntu1 ntpdate[1470]: adjust time server 91.189.89.199 offset 0.166802 sec
Dec 15 11:35:23 Ubuntu1 NetworkManager[1091]: <info> (wlan1): IP6 addrconf timed out or failed.
Dec 15 11:35:23 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec 15 11:35:23 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec 15 11:35:23 Ubuntu1 NetworkManager[1091]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec 15 11:35:29 Ubuntu1 goa[1860]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Dec 15 11:36:27 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Dec 15 11:36:28 Ubuntu1 AptDaemon: INFO: Initializing daemon
Dec 15 11:36:28 Ubuntu1 AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Dec 15 11:36:28 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Dec 15 11:36:28 Ubuntu1 AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Dec 15 11:36:28 Ubuntu1 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/8fcbf6223f34408980bcd914a3719c62
Dec 15 11:36:28 Ubuntu1 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/8fcbf6223f34408980bcd914a3719c62
Dec 15 11:36:32 Ubuntu1 AptDaemon.PackageKit: INFO: Get updates()
Dec 15 11:36:33 Ubuntu1 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/8fcbf6223f34408980bcd914a3719c62
Dec 15 11:40:43 Ubuntu1 kernel: [  362.820255] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
Dec 15 11:41:33 Ubuntu1 kernel: [  412.820258] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
Dec 15 11:42:23 Ubuntu1 kernel: [  462.820260] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x302c with error -110.
Dec 15 11:42:29 Ubuntu1 AptDaemon: INFO: Quitting due to inactivity
Dec 15 11:42:29 Ubuntu1 AptDaemon: INFO: Quitting was requested
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452038] INFO: task irqbalance:1051 blocked for more than 120 seconds.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452045] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452048] irqbalance      D ffff880115cb24e0     0  1051      1 0x00000000
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452056]  ffff88010fc13d28 0000000000000082 0000000000000161 ffff88011fc93ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452063]  ffff88010fc13fd8 ffff88010fc13fd8 ffff88010fc13fd8 0000000000013ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452068]  ffff880119b31740 ffff880118280000 0000000000000000 ffffffff81cbc700
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452075] Call Trace:
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452087]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452092]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452097]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452104]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452111]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452116]  [<ffffffff815e7101>] dev_ioctl+0x1a1/0x2f0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452122]  [<ffffffff815cadbd>] sock_do_ioctl+0x5d/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452127]  [<ffffffff815cbb59>] sock_ioctl+0x79/0x2f0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452135]  [<ffffffff8119d0c8>] ? get_empty_filp+0x88/0x180
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452140]  [<ffffffff811ad72a>] do_vfs_ioctl+0x8a/0x340
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452146]  [<ffffffff816f437e>] ? _raw_spin_lock+0xe/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452151]  [<ffffffff811b9135>] ? __fd_install+0x55/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452156]  [<ffffffff811ada71>] sys_ioctl+0x91/0xb0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452161]  [<ffffffff815cd504>] ? sys_socket+0x74/0xb0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452168]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452173] INFO: task NetworkManager:1091 blocked for more than 120 seconds.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452175] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452178] NetworkManager  D ffff880115cb24e0     0  1091      1 0x00000000
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452184]  ffff88010fdcfa18 0000000000000086 ffff880119b31740 ffff88011fc93ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452190]  ffff88010fdcffd8 ffff88010fdcffd8 ffff88010fdcffd8 0000000000013ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452195]  ffff880119b31740 ffff880118980000 ffff88010fdcf9f8 ffffffff81cbe5e0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452201] Call Trace:
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452207]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452212]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452217]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452222]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452228]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452235]  [<ffffffff8160ea95>] genl_lock+0x15/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452240]  [<ffffffff8160eab6>] genl_rcv+0x16/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452245]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452251]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452256]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452262]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452267]  [<ffffffff815d9c96>] ? verify_iovec+0x56/0xd0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452273]  [<ffffffff815cc95c>] ___sys_sendmsg+0x38c/0x3a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452278]  [<ffffffff811ae650>] ? __pollwait+0xf0/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452284]  [<ffffffff81092130>] ? try_to_wake_up+0x190/0x200
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452290]  [<ffffffff810921a0>] ? try_to_wake_up+0x200/0x200
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452296]  [<ffffffff8101bac9>] ? read_tsc+0x9/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452302]  [<ffffffff815ce469>] __sys_sendmsg+0x49/0x90
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452307]  [<ffffffff815ce4c9>] sys_sendmsg+0x19/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452312]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452317] INFO: task whoopsie:1095 blocked for more than 120 seconds.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452320] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452322] whoopsie        D ffff880115cb24e0     0  1095      1 0x00000000
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452328]  ffff880116411b08 0000000000000086 ffff880116411ab8 ffff88011fc13ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452334]  ffff880116411fd8 ffff880116411fd8 ffff880116411fd8 0000000000013ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452339]  ffff8800cb8045c0 ffff88010fc6ae80 ffff880116411b68 ffffffff81cbc700
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452345] Call Trace:
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452350]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452355]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452360]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452365]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452371]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452377]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452383]  [<ffffffff815f2806>] rtnetlink_rcv+0x16/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452388]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452394]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452399]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452406]  [<ffffffff815cdfcd>] sys_sendto+0x13d/0x190
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452412]  [<ffffffff8119bbfd>] ? vfs_read+0x10d/0x180
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452418]  [<ffffffff8119bcdb>] ? sys_read+0x6b/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452424]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452430] INFO: task wpa_supplicant:1259 blocked for more than 120 seconds.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452432] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452435] wpa_supplicant  D ffff880115cb24e0     0  1259      1 0x00000000
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452440]  ffff88010fdb5688 0000000000000086 ffff88010fdb5628 ffff88011fc13ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452446]  ffff88010fdb5fd8 ffff88010fdb5fd8 ffff88010fdb5fd8 0000000000013ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452452]  ffff8801167c45c0 ffff88011895dd00 ffff8801167c45c0 7fffffffffffffff
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452457] Call Trace:
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452463]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452469]  [<ffffffff816f1bc5>] schedule_timeout+0x1e5/0x250
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452474]  [<ffffffff8108fa36>] ? ttwu_do_activate.constprop.84+0x66/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452479]  [<ffffffff8108fb16>] ? ttwu_queue+0xd6/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452485]  [<ffffffff816f329f>] wait_for_common+0xdf/0x180
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452490]  [<ffffffff810921a0>] ? try_to_wake_up+0x200/0x200
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452495]  [<ffffffff816f341d>] wait_for_completion+0x1d/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452501]  [<ffffffff8107a669>] flush_work+0x29/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452507]  [<ffffffff810768a0>] ? insert_work+0xa0/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452512]  [<ffffffff8107a760>] __cancel_work_timer+0x70/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452517]  [<ffffffff8107a7c0>] cancel_work_sync+0x10/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452547]  [<ffffffffa022826f>] ieee80211_offchannel_ps_enable+0x4f/0xa0 [mac80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452567]  [<ffffffffa022841a>] ieee80211_offchannel_stop_vifs+0x15a/0x1a0 [mac80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452587]  [<ffffffffa0226e64>] __ieee80211_start_scan+0x2f4/0x530 [mac80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452593]  [<ffffffff8108f62d>] ? ttwu_do_wakeup+0x3d/0x120
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452599]  [<ffffffff816f1f7d>] ? mutex_lock+0x1d/0x50
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452618]  [<ffffffffa02278a9>] ieee80211_request_scan+0x39/0x60 [mac80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452642]  [<ffffffffa0235489>] ieee80211_scan+0x89/0x90 [mac80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452670]  [<ffffffffa016171b>] nl80211_trigger_scan+0x4fb/0x700 [cfg80211]
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452677]  [<ffffffff8160ed0d>] genl_rcv_msg+0x22d/0x2b0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452683]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452688]  [<ffffffff8160eae0>] ? genl_rcv+0x40/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452694]  [<ffffffff8160e4b9>] netlink_rcv_skb+0xa9/0xd0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452699]  [<ffffffff8160eac5>] genl_rcv+0x25/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452705]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452710]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452715]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452722]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452727]  [<ffffffff815d9c96>] ? verify_iovec+0x56/0xd0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452732]  [<ffffffff815cc95c>] ___sys_sendmsg+0x38c/0x3a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452738]  [<ffffffff81070672>] ? __set_current_blocked+0x52/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452744]  [<ffffffff8101dda2>] ? fpu_finit+0x22/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452749]  [<ffffffff8101e0c6>] ? init_fpu+0x56/0xc0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452754]  [<ffffffff8101f0ad>] ? __restore_xstate_sig+0x20d/0x520
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452761]  [<ffffffff81014d06>] ? do_signal+0xc6/0x130
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452766]  [<ffffffff8106d84f>] ? recalc_sigpending+0x1f/0x60
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452772]  [<ffffffff8106e0f7>] ? __set_task_blocked+0x37/0x80
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452777]  [<ffffffff815ce469>] __sys_sendmsg+0x49/0x90
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452782]  [<ffffffff815ce4c9>] sys_sendmsg+0x19/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452788]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452819] INFO: task DNS Resolver #7:2283 blocked for more than 120 seconds.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452822] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452824] DNS Resolver #7 D ffff880115cb24e0     0  2283      1 0x00000004
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452830]  ffff8800bf31fb08 0000000000000086 000102d01fffcb00 ffff88011fc13ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452836]  ffff8800bf31ffd8 ffff8800bf31ffd8 ffff8800bf31ffd8 0000000000013ec0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452842]  ffffffff81c15440 ffff880119582e80 0000000000000000 ffffffff81cbc700
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452847] Call Trace:
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452853]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452858]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452863]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452868]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452874]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452880]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452885]  [<ffffffff815f2806>] rtnetlink_rcv+0x16/0x40
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452891]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452897]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452902]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452908]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452913]  [<ffffffff815cdfcd>] sys_sendto+0x13d/0x190
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452919]  [<ffffffff816f437e>] ? _raw_spin_lock+0xe/0x20
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452924]  [<ffffffff811b9135>] ? __fd_install+0x55/0x70
Dec 15 11:42:41 Ubuntu1 kernel: [  480.452930]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:43:13 Ubuntu1 kernel: [  512.828285] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x302c with error -110.
Dec 15 11:44:03 Ubuntu1 kernel: [  562.828304] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x302c with error -110.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452031] INFO: task irqbalance:1051 blocked for more than 120 seconds.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452038] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452042] irqbalance      D ffff880115cb24e0     0  1051      1 0x00000000
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452049]  ffff88010fc13d28 0000000000000082 0000000000000161 ffff88011fc93ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452056]  ffff88010fc13fd8 ffff88010fc13fd8 ffff88010fc13fd8 0000000000013ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452062]  ffff880119b31740 ffff880118280000 0000000000000000 ffffffff81cbc700
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452068] Call Trace:
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452080]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452085]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452091]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452097]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452104]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452109]  [<ffffffff815e7101>] dev_ioctl+0x1a1/0x2f0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452115]  [<ffffffff815cadbd>] sock_do_ioctl+0x5d/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452120]  [<ffffffff815cbb59>] sock_ioctl+0x79/0x2f0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452128]  [<ffffffff8119d0c8>] ? get_empty_filp+0x88/0x180
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452134]  [<ffffffff811ad72a>] do_vfs_ioctl+0x8a/0x340
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452139]  [<ffffffff816f437e>] ? _raw_spin_lock+0xe/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452144]  [<ffffffff811b9135>] ? __fd_install+0x55/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452149]  [<ffffffff811ada71>] sys_ioctl+0x91/0xb0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452154]  [<ffffffff815cd504>] ? sys_socket+0x74/0xb0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452161]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452166] INFO: task NetworkManager:1091 blocked for more than 120 seconds.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452168] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452171] NetworkManager  D ffff880115cb24e0     0  1091      1 0x00000000
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452176]  ffff88010fdcfa18 0000000000000086 ffff880119b31740 ffff88011fc93ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452182]  ffff88010fdcffd8 ffff88010fdcffd8 ffff88010fdcffd8 0000000000013ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452188]  ffff880119b31740 ffff880118980000 ffff88010fdcf9f8 ffffffff81cbe5e0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452194] Call Trace:
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452199]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452205]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452209]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452215]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452221]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452228]  [<ffffffff8160ea95>] genl_lock+0x15/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452233]  [<ffffffff8160eab6>] genl_rcv+0x16/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452238]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452244]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452249]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452255]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452261]  [<ffffffff815d9c96>] ? verify_iovec+0x56/0xd0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452266]  [<ffffffff815cc95c>] ___sys_sendmsg+0x38c/0x3a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452271]  [<ffffffff811ae650>] ? __pollwait+0xf0/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452278]  [<ffffffff81092130>] ? try_to_wake_up+0x190/0x200
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452283]  [<ffffffff810921a0>] ? try_to_wake_up+0x200/0x200
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452289]  [<ffffffff8101bac9>] ? read_tsc+0x9/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452295]  [<ffffffff815ce469>] __sys_sendmsg+0x49/0x90
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452301]  [<ffffffff815ce4c9>] sys_sendmsg+0x19/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452306]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452311] INFO: task whoopsie:1095 blocked for more than 120 seconds.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452313] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452316] whoopsie        D ffff880115cb24e0     0  1095      1 0x00000000
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452321]  ffff880116411b08 0000000000000086 ffff880116411ab8 ffff88011fc13ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452327]  ffff880116411fd8 ffff880116411fd8 ffff880116411fd8 0000000000013ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452333]  ffff8800cb8045c0 ffff88010fc6ae80 ffff880116411b68 ffffffff81cbc700
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452339] Call Trace:
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452344]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452349]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452354]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452359]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452365]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452370]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452376]  [<ffffffff815f2806>] rtnetlink_rcv+0x16/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452381]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452387]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452392]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452399]  [<ffffffff815cdfcd>] sys_sendto+0x13d/0x190
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452405]  [<ffffffff8119bbfd>] ? vfs_read+0x10d/0x180
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452411]  [<ffffffff8119bcdb>] ? sys_read+0x6b/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452416]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452423] INFO: task wpa_supplicant:1259 blocked for more than 120 seconds.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452425] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452428] wpa_supplicant  D ffff880115cb24e0     0  1259      1 0x00000000
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452433]  ffff88010fdb5688 0000000000000086 ffff88010fdb5628 ffff88011fc13ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452439]  ffff88010fdb5fd8 ffff88010fdb5fd8 ffff88010fdb5fd8 0000000000013ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452445]  ffff8801167c45c0 ffff88011895dd00 ffff8801167c45c0 7fffffffffffffff
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452450] Call Trace:
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452456]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452462]  [<ffffffff816f1bc5>] schedule_timeout+0x1e5/0x250
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452467]  [<ffffffff8108fa36>] ? ttwu_do_activate.constprop.84+0x66/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452472]  [<ffffffff8108fb16>] ? ttwu_queue+0xd6/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452477]  [<ffffffff816f329f>] wait_for_common+0xdf/0x180
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452483]  [<ffffffff810921a0>] ? try_to_wake_up+0x200/0x200
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452488]  [<ffffffff816f341d>] wait_for_completion+0x1d/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452494]  [<ffffffff8107a669>] flush_work+0x29/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452500]  [<ffffffff810768a0>] ? insert_work+0xa0/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452505]  [<ffffffff8107a760>] __cancel_work_timer+0x70/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452510]  [<ffffffff8107a7c0>] cancel_work_sync+0x10/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452540]  [<ffffffffa022826f>] ieee80211_offchannel_ps_enable+0x4f/0xa0 [mac80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452560]  [<ffffffffa022841a>] ieee80211_offchannel_stop_vifs+0x15a/0x1a0 [mac80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452580]  [<ffffffffa0226e64>] __ieee80211_start_scan+0x2f4/0x530 [mac80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452585]  [<ffffffff8108f62d>] ? ttwu_do_wakeup+0x3d/0x120
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452591]  [<ffffffff816f1f7d>] ? mutex_lock+0x1d/0x50
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452611]  [<ffffffffa02278a9>] ieee80211_request_scan+0x39/0x60 [mac80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452635]  [<ffffffffa0235489>] ieee80211_scan+0x89/0x90 [mac80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452663]  [<ffffffffa016171b>] nl80211_trigger_scan+0x4fb/0x700 [cfg80211]
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452670]  [<ffffffff8160ed0d>] genl_rcv_msg+0x22d/0x2b0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452676]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452682]  [<ffffffff8160eae0>] ? genl_rcv+0x40/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452687]  [<ffffffff8160e4b9>] netlink_rcv_skb+0xa9/0xd0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452693]  [<ffffffff8160eac5>] genl_rcv+0x25/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452698]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452704]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452709]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452715]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452720]  [<ffffffff815d9c96>] ? verify_iovec+0x56/0xd0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452726]  [<ffffffff815cc95c>] ___sys_sendmsg+0x38c/0x3a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452731]  [<ffffffff81070672>] ? __set_current_blocked+0x52/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452737]  [<ffffffff8101dda2>] ? fpu_finit+0x22/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452742]  [<ffffffff8101e0c6>] ? init_fpu+0x56/0xc0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452748]  [<ffffffff8101f0ad>] ? __restore_xstate_sig+0x20d/0x520
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452755]  [<ffffffff81014d06>] ? do_signal+0xc6/0x130
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452760]  [<ffffffff8106d84f>] ? recalc_sigpending+0x1f/0x60
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452766]  [<ffffffff8106e0f7>] ? __set_task_blocked+0x37/0x80
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452771]  [<ffffffff815ce469>] __sys_sendmsg+0x49/0x90
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452776]  [<ffffffff815ce4c9>] sys_sendmsg+0x19/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452781]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452814] INFO: task DNS Resolver #7:2283 blocked for more than 120 seconds.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452817] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452819] DNS Resolver #7 D ffff880115cb24e0     0  2283      1 0x00000004
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452825]  ffff8800bf31fb08 0000000000000086 000102d01fffcb00 ffff88011fc13ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452831]  ffff8800bf31ffd8 ffff8800bf31ffd8 ffff8800bf31ffd8 0000000000013ec0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452836]  ffffffff81c15440 ffff880119582e80 0000000000000000 ffffffff81cbc700
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452842] Call Trace:
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452848]  [<ffffffff816f3449>] schedule+0x29/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452853]  [<ffffffff816f36fe>] schedule_preempt_disabled+0xe/0x10
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452858]  [<ffffffff816f2377>] __mutex_lock_slowpath+0xd7/0x150
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452863]  [<ffffffff815d7bab>] ? __alloc_skb+0x8b/0x2a0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452869]  [<ffffffff816f1f8a>] mutex_lock+0x2a/0x50
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452874]  [<ffffffff815f27e5>] rtnl_lock+0x15/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452880]  [<ffffffff815f2806>] rtnetlink_rcv+0x16/0x40
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452886]  [<ffffffff8160de01>] netlink_unicast+0x1b1/0x230
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452891]  [<ffffffff8160e17e>] netlink_sendmsg+0x2fe/0x3b0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452897]  [<ffffffff815cabc2>] sock_sendmsg+0xd2/0xf0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452903]  [<ffffffff815cd44a>] ? move_addr_to_kernel+0x5a/0xa0
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452908]  [<ffffffff815cdfcd>] sys_sendto+0x13d/0x190
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452913]  [<ffffffff816f437e>] ? _raw_spin_lock+0xe/0x20
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452919]  [<ffffffff811b9135>] ? __fd_install+0x55/0x70
Dec 15 11:44:41 Ubuntu1 kernel: [  600.452925]  [<ffffffff816fd1dd>] system_call_fastpath+0x1a/0x1f
Dec 15 11:44:53 Ubuntu1 kernel: [  612.828192] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
Dec 15 11:45:11 Ubuntu1 kernel: [  630.040234] usb 1-2: USB disconnect, device number 2
Dec 15 11:45:11 Ubuntu1 kernel: [  630.044093] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -19.
Dec 15 11:45:11 Ubuntu1 NetworkManager[1091]: <warn> Could not get scan request result: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Dec 15 11:45:12 Ubuntu1 kernel: [  631.644017] phy0 -> rt73usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 15 11:45:12 Ubuntu1 kernel: [  631.644026] phy0 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 15 11:45:12 Ubuntu1 kernel: [  631.644287] wlan1: deauthenticating from 10:fe:ed:5d:f9:72 by local choice (reason=3)
Dec 15 11:45:12 Ubuntu1 wpa_supplicant[1259]: CTRL-EVENT-DISCONNECTED bssid=10:fe:ed:5d:f9:72 reason=3
Dec 15 11:45:12 Ubuntu1 kernel: [  631.652287] cfg80211: Calling CRDA for country: TR
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Interface wlan1.IPv6 no longer relevant for mDNS.
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::224:1ff:fe08:6a4c.
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Interface wlan1.IPv4 no longer relevant for mDNS.
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.102.
Dec 15 11:45:12 Ubuntu1 dhclient: receive_packet failed on wlan1: Network is down
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Withdrawing address record for fe80::224:1ff:fe08:6a4c on wlan1.
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Withdrawing address record for 192.168.1.102 on wlan1.
Dec 15 11:45:12 Ubuntu1 avahi-daemon[1003]: Withdrawing workstation service for wlan1.
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/net/wlan1, iface: wlan1)
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): now unmanaged
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Dec 15 11:45:12 Ubuntu1 wpa_supplicant[1259]: Failed to initialize the driver after interface was added.
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): deactivating device (reason 'removed') [36]
Dec 15 11:45:12 Ubuntu1 wpa_supplicant[1259]: Failed to initiate AP scan.
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 1274
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <warn> (3) failed to find interface name for index
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <warn> (3) failed to find interface name for index
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <warn> DNS: plugin dnsmasq update failed
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): removing resolv.conf from /sbin/resolvconf
Dec 15 11:45:12 Ubuntu1 dnsmasq[1369]: setting upstream servers from DBus
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> (wlan1): cleaning up...
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <warn> (3) failed to find interface name for index
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <error> [1387100712.931992] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Dec 15 11:45:12 Ubuntu1 NetworkManager[1091]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill0 disappeared
Dec 15 11:45:12 Ubuntu1 dbus[920]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 15 11:45:12 Ubuntu1 dbus[920]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 15 11:45:12 Ubuntu1 wpa_supplicant[1259]: Could not read interface wlan1 flags: No such device
Dec 15 11:49:27 Ubuntu1 kernel: [  886.697827] audit_printk_skb: 48 callbacks suppressed
Dec 15 11:49:27 Ubuntu1 kernel: [  886.697834] type=1400 audit(1387100967.679:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=957 comm="cupsd" pid=957 comm="cupsd" capability=36  capname="block_suspend"


```

 I hope this is not too much thing to check for you. I really appreciate your help. Thank you very much guys from now.

---

### Post by noyanculum on 2013-12-15
I found 2 bug reports similar to my problem with error -110.
The first one with the same dongle and the second one with the same driver.
But no one looks like solved:

1. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/999129](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/999129)
2. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599)

EDIT: Anyway, I doubt their problem is same as mine. Because my dongle was working like a charm until 3 days ago. And it is still working like a charm on my other computer in the same version of Ubuntu.

---

### Post by varunendra on 2013-12-15
In the meanwhile, I also found a number of similar bug reports and related posts, although none actually solved like you found out.
So yeah, it does look like the old bug to me.
> **noyanculum said:**
> ....my dongle was working like a charm until 3 days ago. And it is still working like a charm on my other computer in the same version of Ubuntu.

Are the driver versions also the same? Please check (and show us) the outputs of -
```
uname -mr
modinfo rt73usb rt2x00usb | egrep 'file|version'
```

We can try a newer (backported) driver, but that would cause permanent changes without any guaranty to fix it. So if trying with the graphics card removed like BB suggested is not a problem for you, I'd encourage to try that first.

Let's try things that are 'easy to revert' first, before trying things that would be relatively difficult to revert.

---

### Post by noyanculum on 2013-12-15
WORKING DONGLE:
```

$ uname -mr
3.8.0-33-generic x86_64

$ modinfo rt73usb | egrep 'file|version'
filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
version:        2.3.0
srcversion:     246FEEC23EA0D5DB663C1D3
vermagic:       3.8.0-33-generic SMP mod_unload modversions

```

NOT WORKING DONGLE:
```

$ uname -mr
3.8.0-34-generic x86_64

$ modinfo rt73usb | egrep 'file|version'
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
version:        2.3.0
srcversion:     246FEEC23EA0D5DB663C1D3
vermagic:       3.8.0-34-generic SMP mod_unload modversions

```

 Is this 3.8.0.34 Kernel version? I remember I installed this package the same day I installed the graphics card.


Note 1: I found some suggestions on some other forums, that the reason of the problem may be the firmware.
 
  Note 2: @Bucky Ball I tested the problem 1 time with removing the graphics card. It is same, the wireless connection hangs. Then I reinstalled the card. I don't want to remove the graphics card again. Because I had some different problems in that try. The graphical interface did completely stop. I worked 30 minutes on the console. Then I did fortunately find something to make it working again. But I may not be lucky next time. That's why, I don't want to try it again. I want to find a solution within the current configuration.

---

### Post by Bucky Ball on 2013-12-15
Well, on the face of it, it appears the card works in this kernel:

3.8.0-33-generic x86_64

But not this one:

3.8.0-34-generic x86_64

Use kernel 3.8.0-33-generic x86_64. Is everything stable?

You could boot to 3.8.0-34-generic x86_64 and immediately:

```
sudo apt-get update
sudo apt-get upgrade
```

Then reboot. If you've only just upgraded to the .34 kernel your problems could be related to that and should improve within a few updates. Hopefully.

---

### Post by varunendra on 2013-12-15
> **Bucky Ball said:**
> Use kernel 3.8.0-33-generic x86_64. Is everything stable?
..and you can choose to boot with that older kernel from grub menu.

If you don't get grub menu at boot time by default, press 'Shift' (or 'Esc' in some computers) key on the purple splash screen at boot time to bring it up.

---

### Post by noyanculum on 2013-12-15
Not working dongle meant -> my ubuntu computer which has connection problem (Computer1)
Working dongle meant -> my other ubuntu computer which has any connection problem (Computer2)

Both computers have the same model of usb wireless dongle.
:)

I upgraded the Computer2 to Kernel 3.8.0-34. It still works like a charm. Its wireless connection is still perfect.

---

### Post by noyanculum on 2013-12-15
Both computers have now the same driver versions:
```

$ uname -mr
3.8.0-34-generic x86_64

$ modinfo rt73usb | egrep 'file|version'
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
version:        2.3.0
srcversion:     246FEEC23EA0D5DB663C1D3
vermagic:       3.8.0-34-generic SMP mod_unload modversions 

```

With the same Ubuntu version, the same driver version and the same USB wireless dongle device; Computer1 can not connect, Computer2 connect perfectly.

---

### Post by varunendra on 2013-12-15
Silly question, and probably unnecessary too, but I can't think better with my sleepy head now -

Is the rt2x00 driver version also the same? (my original command was "modinfo rt73usb **rt2x00usb** | egrep 'file|version' ")

Installing and trying a backported driver is easy, but trying an already installed older kernel is easier ! :)

---

### Post by noyanculum on 2013-12-15
Yes they are same:
```

$ modinfo rt73usb rt2x00usb | egrep 'file|version'
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
version:        2.3.0
srcversion:     246FEEC23EA0D5DB663C1D3
vermagic:       3.8.0-34-generic SMP mod_unload modversions 
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     B2734411C831D4AF35167D6
vermagic:       3.8.0-34-generic SMP mod_unload modversions

```


 A few minutes ago, I uninstalled Kernel 3.8.0-34 from Computer1 and I rebooted. Then it couldn't start and it went to low graphics mode. In this mode, there was no connection problem. It was never hanged. Then I reinstalled kernel 3.8.0-34 and Nvidia driver. Then I rebooted the computer and again connection hanging.

Maybe kernel and driver downgrade, maybe low graphics mode. Something make the malfunction stopping.

 May the reason of malfunction of the connection be these Xorg packages?

---

### Post by varunendra on 2013-12-15
> **noyanculum said:**
>  May the reason of malfunction of the connection be these Xorg packages?

Most likely.

Could you try installing the kernel, but not the NVidia driver again? You can always boot into low graphics mode from recovery menu or by manually adding "nomodeset" option : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Like I said, installing and trying a backported driver for the wireless is as easy as downloading a 9-10 MB package and running 3-4 commands, but I doubt that would help.

---

### Post by noyanculum on 2013-12-15
Ok, I deactivated Nvidia-driver via jockey-gtk and rebooted the computer. Ubuntu started in low graphics mode (full screen console, no graphical interface).

During 15 minutes, I did some network operations like;
- ping 192.168.1.1
- ping google.com
- ping <myownwebsite>.com
- traceroute -nn google.com
- traceroute -nn <myownwebsite>.com
- sudo apt-get update

The wireless connection works good in this mode. It does not hang.

 Then I reinstalled Nvidia driver. I rebooted Ubuntu. I launched Firefox. I visited google and a few pages of newspaper websites. 1 minute later the wireless connection hanged.

---

### Post by noyanculum on 2013-12-16
Another test
I put my livecd (which I used to install this Ubuntu) to the cd driver.
I booted Ubuntu via `Try Ubuntu without installing` option of the livecd menu.
The wireless connection works very well, I write these lines now within this connection.


EDIT>
After all; I see Nvidia driver installation process installs tons of files. It is very fast I can not see them one by one; but it put some files into lib directories, some files into lib32 directories. some files for kernel, some files for xserver-xorg, and many additional files.. One or some of these files stops somehow my connection working. But which one?

The only clue I can see is:
If I uninstall Nvidia drivers, I remove the Nvidia card physically and I start Ubuntu again with my old onboard graphics card; the connection still hangs.
If I uninstall Nvidia drivers and I start Ubuntu in low graphics mode, the connection does not hang.

So it looks like there is a problem in some files of graphical interface, installed by Nvidia installation process. I can not think of something more.

---

### Post by noyanculum on 2013-12-16
Ok another simple test, that I didnt mind until today.
I launched Ubuntu (normal boot with Nvidia drivers). I launched a terminal window. During 15 minutes I did some network operations like ping, traceroute, apt-get update.
The wireless connection didn`t hang.

Then I launched Firefox, I visited a few webpages. 1 minute later the wireless connection hanged.
I tried that also with Chrome and Opera. The connection always hangs.

---

### Post by varunendra on 2013-12-16
Clearly an X config issue now, which means I'll have to bail out. :(

Sorry, my knowledge and experience with graphics and Xorg issues is almost zero, so can't offer any help with that, other than pointing you to this NVidia wiki : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Hope you can get something worth there. If you find someone on the forums who seems to be able to help with such issues, I'm sure they won't mind a PM from you asking to take a look at your thread.

I'd be interested in seeing a solution to this, but sorry for not being able to be of anymore help on this.

---

### Post by noyanculum on 2013-12-16
Hey Varunendra,

Thank you for pointing where to search the source of the problem, X server.
I was in the darkness after the last simple test I made.
At least I have a start point now. I am going to work on its configuration.

---

### Post by varunendra on 2013-12-17
One more thing that I should have added earlier is that both the title and section of this thread are irrelevant to the problem you actually need to troubleshoot. Therefore it makes sense to post a new thread with a relevant title, in a relevant section of the forums. That will have much more chance of catching attention of experts who can help with this kind of issues.

I think a title like "GUI hangs After installing NVidia driver" in "[Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334")" section should be good enough. Using the word "browsing" and/or "networking" may cause some of the potential helpers think "this one is for networking guys..", so avoid using them in the title. :P

But of course include the full details as in your posts 25, 26, 27 above in your original post in that thread, and even post a link to this page as a reference to show what you have tried so far and why you think it is an Xorg issue.

Similarly, please post the link to your new thread here so that us curious creatures can follow it and hopefully see it getting solved.

Best of luck !

---

### Post by noyanculum on 2013-12-19
Yes if I try first via terminal when everything working, my connection does not hang.
But if I connect first via a browser and my connection hangs, then I can not connect via the terminal either.
Is this a GUI hang or connection hang?

I uninstalled some radeon xorg libraries. The connected time is a bit longer now. I can stay connected during 6-7 minutes.
The only radeon library I didn't uninstalled is libdrm-radeon1. As the behaviour changed after uninstalling other radeon libraries, I want to uninstall this one as well. But Synaptic warns me that it will delete tons of packages with that, including nearly everything essential. So I can not delete it.

The problem continues since 1 week. I can not connect properly yet.

---

### Post by varunendra on 2013-12-19
> **noyanculum said:**
> Is this a GUI hang or connection hang?

Could be a kernel/driver or services crash due to a misbehaving driver or setting. This driver can be anythin, including wireless. But since the same driver works nicely before changing X configuration, I believe it is almost certainly related to an Xorg or Nvidia driver bug. I believe a misconfigured Xorg can cause troubles beyond imagination.

Just start a thread as suggested and let us see what the graphics guys have to tell us. We can proceed accordingly with the leads they may give us.

---

### Post by noyanculum on 2013-12-21
I started a new thread on the Multimedia&Video section of the forums. Here is the link of the new thread: [http://ubuntuforums.org/showthread.php?t=2194847](http://ubuntuforums.org/showthread.php?t=2194847)

---

### Post by varunendra on 2013-12-21
Being quoted feels so nice ! But sometimes embarrassing too :P

Let's hope someone there can shed more light on this.

---

### Post by noyanculum on 2013-12-23
Your sentences were the best words to express the conclusion of the current situation.
Anyway, i have still problems in connecting :)))

---

