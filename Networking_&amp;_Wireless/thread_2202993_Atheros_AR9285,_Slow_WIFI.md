---
title: "Atheros AR9285, Slow WIFI"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by chris155 on 2014-01-31
Hi!

I recently dual booted my Sony Vaio VPCEA3EG to Win7 x64 and Ubuntu 12.04 LTS x64.
Was fine till I noticed my Ubuntu net speed is incredibly slower than Win 7. It's at 0.7mbps!

I'm new to Ubuntu and have not the slightest clue how to fix this. Pls help.

I did try solutions #2 and #4 on this page:
[http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

#2 came up with an error saying the method wasn't found and #3 increased my page loading by a meer 2 to 5 seconds.

---

### Post by newb85 on 2014-01-31
My gut reaction is that you probably have a special wireless card that would run better on special drivers.  That would mean Wildman is probably the best qualified to help.

---

### Post by chris155 on 2014-01-31
Oh great Wild Man, I summon thee!

Yeah, hopefully this problem gets fixed, cause loading this page just took 4 minutes :(

---

### Post by chris155 on 2014-02-01
Just so I get more assistance, I shall copy this thread to the Networking & Wireless section.

---

### Post by chris155 on 2014-02-01
Hi!

I recently dual booted my Sony Vaio VPCEA3EG to Win7 x64 and Ubuntu 12.04 LTS x64.
Was fine till I noticed my Ubuntu net speed is incredibly slower than Win 7. It's at 0.7mbps!

I'm new to Ubuntu and have not the slightest clue how to fix this. Pls help.

I did try solutions #2 and #4 on this page:
[http://itsfoss.com/speed-up-slow-wif...ection-ubuntu/]("http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/")

#2 came up with an error saying the method wasn't found and #3 increased my page loading by a meer 2 to 5 seconds.

This was also originally posted @: [http://ubuntuforums.org/showthread.php?t=2202782](http://ubuntuforums.org/showthread.php?t=2202782)

---

### Post by howefield on 2014-02-01
> **chris155 said:**
> Just so I get more assistance, I shall copy this thread to the Networking & Wireless section.

No, duplicate threads aren't a good idea but I'll move it to the "*Networking & Wireless*" forum. You can use the report button to request moves.

---

### Post by varunendra on 2014-02-01
> **chris155 said:**
> Oh great Wild Man, I summon thee!

I believe Wild Man or anyone else would first like to know a little about your wifi card, the driver it uses and some other related info, and I also believe Wild Man's favourite method to get these details is to run his "wireless_script" which you can find in the "Wireless Script" link in my signature below. :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mörgæs on 2014-02-01
As posted above, please stop multiposting. You get plenty of help here already.
Merged your threads.

---

### Post by chris155 on 2014-02-01
Sorry for the forum mess up, and thanks!
Will take note.

So here's the the result I got from the script in wireless-info.txt:

```


*************** info trace ***************

***** uname -a *****

Linux chris-VPCEA43EG 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: Sony Corporation Device [104d:9071]
    Kernel driver in use: sky2

***** lsusb *****

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6464 Microdia 
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"promethei_pi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=52 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:120  Invalid misc:435   Missed beacon:0


***** rfkill *****

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 152184  0 
mac80211              631450  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422564  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              526422  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [promethei_pi] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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
    dlink:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    promethei_pi-guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    *promethei_pi:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2
    Belkin.3582:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    elsatp:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2

  IPv4 Settings:
    Address:         192.168.1.139
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.254.1



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

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"promethei_pi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4cc931505
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000C70726F6D65746865695F7069
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B00010310470010FEF9268E0ACB259269E3CBB72515247210210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180209F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4cc5e2350
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010ECBEF4C227BCA80BD49AFC7516A6222710210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"promethei_pi-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4cc933a71
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 001270726F6D65746865695F70692D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180209F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Belkin.3582"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ccf6fa141
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 000B42656C6B696E2E33353832
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: DD1E00904C336E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000


***** resolv.conf *****

nameserver 127.0.0.1
search domain.name

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

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4E9F0D89FF4F3CF07CD5105
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0078E2DDCA5F8B073A36467
depends:        ath
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.902419] ath: phy0: ASPM enabled: 0x42
[   12.902425] ath: EEPROM regdomain: 0x65
[   12.902426] ath: EEPROM indicates we should expect a direct regpair map
[   12.902428] ath: Country alpha2 being used: 00
[   12.902429] ath: Regpair used: 0x65
[   16.960849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.953308] wlan0: authenticate with <MAC address removed>
[   19.965958] wlan0: send auth to <MAC address removed> (try 1/3)
[   19.967986] wlan0: authenticated
[   19.968582] wlan0: associate with <MAC address removed> (try 1/3)
[   19.972220] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   19.972290] wlan0: associated
[   19.972306] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************



```

I don't understand a thing :lol:

---

### Post by newb85 on 2014-02-01
Well, I don't have any experience with your chipset (or any that doesn't work out-of-box), but here's what I found with a little searching...

Your wifi chipset's driver (kernel module) is already installed; however it isn't operating optimally.  You can tweak it to improve performance with the following commands and then reboot:

```
[FONT=Ubuntu Mono]echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf[/FONT]
sudo modprobe -rfv ath9k

sudo modprobe -v ath9k
```

I got this answer from [http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver](http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver), where it was posted by Wild Man.  ;)

---

### Post by chris155 on 2014-02-01
> **newb85 said:**
> Well, I don't have any experience with your chipset (or any that doesn't work out-of-box), but here's what I found with a little searching...

Your wifi chipset's driver (kernel module) is already installed; however it isn't operating optimally.  You can tweak it to improve performance with the following commands and then reboot:

```
[FONT=Ubuntu Mono]echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf[/FONT]
sudo modprobe -rfv ath9k

sudo modprobe -v ath9k
```

I got this answer from [http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver](http://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver), where it was posted by Wild Man.  ;)

Oh wow, this actually has seemed to work. I went from 0.7 mbps and below to 1.77 mbps, which is actually pretty good for where I live (We got routers going an average of 2mpbs).

Will keep a text file of this code, thanks! ;)

---

### Post by varunendra on 2014-02-02
> **chris155 said:**
> I went from 0.7 mbps and below to **1.77 mbps**, which is actually pretty good for where I live (We got routers going an average of 2mpbs).

I believe this is the Internet speed. What is the speed in Windows?
Can you also check the local network speed? Because that would be the real performance test of the driver.

Your report earlier showed a signal strength of 35/70, which is pretty weak. Are you too far away from the access-point? If not, it maybe due to a couple other reasons, including the driver's own issues.

The ath9k driver in kernel 3.8 series was reported quite many times for not performing well. Judging by the number of reports, apparently it was significantly improved in kernel 3.11 series (and I *believe* it should have been further improved in later kernels). As such, if the local network speed, or that in comparison to Windows is still much slower, you may get better performance with a newer version of the driver.

For that you may either upgrade your kernel, upgrade the whole OS (to 13.10) or just compile a newer driver (which will only change that particular driver, leaving the rest of the system at its current state). For compiling a newer driver, you may follow the instructions in this post (ignore the "power off" part, not applicable to you) : [http://ubuntuforums.org/showthread.php?t=2199584&p=12903760#post12903760](http://ubuntuforums.org/showthread.php?t=2199584&p=12903760#post12903760)

There is one more thing in your router that we network guys here don't like to see. That is, the WPA/WPA2 mixed mode -
```
  Wireless Access Points (* = current AP)
....
    ***promethei_pi:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 46 [COLOR="#FF0000"]WPA WPA2[/COLOR]**
```
This encryption type requires TKIP which is not only outdated and less secure, but is also a very inefficient encryption algorithm. We highly recommend to change it (in your router) to pure WPA2-PSK with AES. No mixed mode, no TKIP. Change the setting > Save it > Reboot both the router and laptop and see if there is further performance improvement.

Having said all of the above, of course you don't need to follow any of the above if you are satisfied with its current performance. You will automatically get the newer driver when you upgrade to 14.04 in April-March (or 13.10 right now). :)

---

