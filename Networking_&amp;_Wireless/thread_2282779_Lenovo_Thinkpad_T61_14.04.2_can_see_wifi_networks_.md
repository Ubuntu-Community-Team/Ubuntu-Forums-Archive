---
title: "Lenovo Thinkpad T61 14.04.2 can see wifi networks but won't accept passwords"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by mp-y on 2015-06-16
Hello.  I have played around with Ubuntu for a few years on servers, but this is the first time I have installed on a laptop.  I downloaded the latest desktop iso (64 bit) and installed.  No problems on docking station with cable, but trying to use wifi it just refuses to connect using the password.

Access Point is Netgear WG102 set with WPA2-PSK (though have also tried with no security and with WPA).
I could connect with laptop when it had Windows 7 on
I can connect using same password with tablet and smart phone (copied and pasted from KeePass)
It can see all the networks it just doesn't accept the passwords
Device is a Intel Pro Wireless 4965 AG or AGN [Kedron]

```
PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:d2:cf:8b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.3-0 ip=192.168.0.43 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:7c:e0:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.16.0-41-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:df3fe000-df3fffff

```

I have hunted through dozens of similar articles and tried all of the suggestions but to no avail.

Any ideas why the wifi isn't working?
Thanks

---

### Post by wildmanne39 on 2015-06-16
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by tgalati4 on 2015-06-17
I presume that you have this card.  [http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_4965AGN_Mini-PCI_Express_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_4965AGN_Mini-PCI_Express_Adapter)

You can remove the bottom panel and verify that it is the correct card and that it is seated correctly, they can loosen up over time.

There are a lot of switches to try with the open Intel driver iwlwifi:

> parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


Try turning off bluetooth and testing.  Sometimes bluetooth will interfere with wireless connection, since they use the same antennae.

That's an older wireless card (2007 vintage).  Try setting your AP to "A" band (5 GHz) only--for testing purposes and try to connect.  There are a lot wireless devices on "G" band (2.4 GHz) and that interference can cause connections to fail.  So either your card is worn out, or you need to set interference robustness (20 MHz instead of 40 MHz bandwidth) or use "A" band exclusively.  That has been my experience on my T43p which has a similar Intel wireless card.

In the meantime, run the WildMan's wireless script so we can get more diagnostic information.

---

### Post by mp-y on 2015-06-19
[ATTACH]262699[/ATTACH]

Thank you for your prompt responses.  Here is the wireless-info file.

Galilee, GuestNet14 and Netgear-2 are mine.  Galilee is the one I normally use, GuestNet14 is a guest network cut off from my PCs and network drives and the Netgear was when I was trying different settings to see if the type of encryption made a difference.

---

### Post by tgalati4 on 2015-06-19
You are using a different driver, one with less switches:

> tgalati4@Mint17 ~ $ modinfo iwl4965
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     52A3B1E68D22B0078326AC5
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)


Sometimes turning of "N" capability can help.  Are you running the latest firmware on the Netgear [WG102]("http://support.netgear.com/product/wg102")? It looks like 5.0.3 is the latest.  Your router only supports "G" band with a large (+5 dB) antenna, so I would use a smart phone with WiFi Analyzer to see the 2.4 GHz congestion in your location.  Change channels if necessary.  Try to connect with the Thinkpad from 20 to 50' away, since the laptop has a dual-antenna and that can result in too strong a signal to communicate.

Although it is counter-intuitive, sometimes turning down the AP power can help, especially when using a business-grade AP in a residence.  Also, your Thinkpad's wireless card is set to Europe--that gives you Channel 13.  I presume that the region is correct?

Also, your troubleshooting output shows that you have a USB Ralink2800 Wireless Dongle attached.  Try removing that and work with one wireless device at a time.  The internal Intel Wireless card should work just fine.

---

### Post by mp-y on 2015-06-19
Thank you for your further reply

I disabled N by adding 
options iwl4965 11n_disable=1 

to 

/etc/modprobe.d/iwl4965.conf

The router is on the latest firmware (5.0.3).  I have turned the power down to half and shifted the channels to avoid as much as possible the neighbours' wifi.  
My laptop is currently in my study, which is a thick brick wall away from the AP which is in the lounge.  That said, I never had any problems when I was running Windows 7 accessing the wifi in the lounge.

I have disconnected the other - I tried with that to see if it was the hardware.

I am based in the UK and my AP is set to UK.  Do I need to change this in ubuntu?  If so, where do I find this setting? 

Thanks

---

### Post by wildmanne39 on 2015-06-19
What network are you trying to connect too?

---

### Post by mp-y on 2015-06-19
Trying to connect to the Galilee wireless network - this is my private home network as opposed to the Guest network.

I have also tried the guest network (GuestNet14) but same result.

The laptop can see the network - it tries to connect but keeps prompting for the password again.

---

### Post by tgalati4 on 2015-06-19
As long as you can see Channel 13 in your scan list, then you are OK.  Windows uses a proprietary driver that works out-of-the-box.  Linux uses an open source driver that may not be as good as the Windows driver, or, more likely, it needs some tweaking to work correctly.

What does:

```
iwlist wlan0 scan
```

Turn off your bluetooth.  There may be either a physical switch or a Fn (blue key) switch.  

Then check your frequencies and power management:

> tgalati4@Mint17 ~ $ iwlist wlan0 power
wlan0     Current mode:off

tgalati4@Mint17 ~ $ man iwlist
tgalati4@Mint17 ~ $ iwlist wlan0 frequency
wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.427 GHz (Channel 4)


I'm in the US, so we don't have Channels 12 or 13.  I have to use Channel 4 because of so many 2.4 GHz AP's in my area.

You can turn off bluetooth multiplexing using a switch:

```
modinfo iwlegacy
```

---

### Post by wildmanne39 on 2015-06-19
Please do on line at a time:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
Does it connect know?
You need to have your usb adaptor unlugged first.
Thanks

---

### Post by mp-y on 2015-06-19
```
modinfo iwlegacy
```

Gives the following result. My laptop doesn't have bluetooth. Never saw any settings in Win7 and in hardware manager it says there are no bluetooth devices present

```
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     1FA10C0B834AAF4AE219899
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        42:AE:B7:DF:54:E6:D9:1C:A0:F4:01:21:E2:2F:EA:E6:B2:30:88:16
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


```

```
iwlist wlan0 scan
```

returns the following

```
wlan0     Scan completed :
          Cell 01 - Address: C0:3E:0F:6E:0A:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SKY690CC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015195913cd
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 0008534B593639304343
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0504004F0000
                    IE: Unknown: 2D1AAC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010606924A14751782796CEC58B68EA77571021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180204000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 06:1B:2F:96:2B:41
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"GuestNet14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000402a906e3
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000A47756573744E65743134
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-CJ9M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff3c418
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000B4254487562352D434A394D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B0001031047001018950A26B5FF5AE0AE8E4C19E22B6DE510210002425410230005487562203510240009425420487562203541104200122B3036383534332B4E5134353133323834381054000800060050F204000110110010425420486F6D652048756220352E3041100800020084103C000101
          Cell 04 - Address: 12:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff4fdca
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: 32:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff4a257
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: 12:1E:78:2B:84:CC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ce57b785
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 32:1E:78:2B:84:CC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ce577686
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 08 - Address: 06:1F:33:73:44:38
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"GuestNet14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c3387f80
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000A47756573744E65743134
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:1F:33:73:44:38
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Galilee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c3388802
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000747616C696C6565
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


```

```
iwlist wlan0 power
```

returns the following, even when I disconnect the ethernet and force it to try and connect to Galilee

```
wlan0 Current mode:off
```

```
iwlist wlan0 frequency
```

returns the followng, and this is after following Wildman's instructions that should have disabled N

```
wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz


```

Thank you

---

### Post by mp-y on 2015-06-19
```
modinfo iwlegacy
```

Gives the following result. My  laptop doesn't have bluetooth. Never saw any settings in Win7 and in  hardware manager it says there are no bluetooth devices present

```
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     1FA10C0B834AAF4AE219899
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        42:AE:B7:DF:54:E6:D9:1C:A0:F4:01:21:E2:2F:EA:E6:B2:30:88:16
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


```

```
iwlist wlan0 scan
```

returns the following

```
wlan0     Scan completed :
          Cell 01 - Address: C0:3E:0F:6E:0A:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SKY690CC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015195913cd
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 0008534B593639304343
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0504004F0000
                    IE: Unknown: 2D1AAC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                     IE: Unknown:  DD800050F204104A0001101044000102103B00010310470010606924A14751782796CEC58B68EA77571021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180204000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 06:1B:2F:96:2B:41
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"GuestNet14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000402a906e3
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000A47756573744E65743134
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-CJ9M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff3c418
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000B4254487562352D434A394D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                     IE: Unknown:  DD8E0050F204104A000110104400010210570001001041000100103B0001031047001018950A26B5FF5AE0AE8E4C19E22B6DE510210002425410230005487562203510240009425420487562203541104200122B3036383534332B4E5134353133323834381054000800060050F204000110110010425420486F6D652048756220352E3041100800020084103C000101
          Cell 04 - Address: 12:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff4fdca
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: 32:1E:78:2F:F3:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001ff4a257
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: 12:1E:78:2B:84:CC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ce57b785
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 32:1E:78:2B:84:CC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ce577686
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 00084254576966692D58
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 08 - Address: 06:1F:33:73:44:38
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"GuestNet14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c3387f80
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000A47756573744E65743134
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:1F:33:73:44:38
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Galilee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c3388802
                    Extra: Last beacon: 6872ms ago
                    IE: Unknown: 000747616C696C6565
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


```

```
iwlist wlan0 power
```

returns the following, even when I disconnect the ethernet and force it to try and connect to Galilee

```
wlan0 Current mode:off
```

```
iwlist wlan0 frequency
```

returns the followng, and this is after following Wildman's instructions that should have disabled N

```
wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz


```

Thank you

---

### Post by tgalati4 on 2015-06-19
You can turn off your 5 GHz band, since you only need 2.4 GHz, and that is all your AP supports.  You are getting a weak signal for "Galilee", 30 out of 70.  You want 55 or better.  So move around until you get better than 55, then try to connect.  Your power-saving mode is turned off, and that is OK.  Sometimes when the wireless goes into power-saving mode, it is more difficult to maintain a connection in a crowded wifi area.

Also, it appears that your AP is using [TKIP]("http://www.howtogeek.com/204697/wi-fi-security-should-you-use-wpa2-aes-wpa2-tkip-or-both/") which is an older encryption protocol.  You want AES and your router should support it with the latest firmware.  So set your router to use AES only (not BOTH, and not DEFAULT) and then reboot the router and try to connect again.

---

### Post by wildmanne39 on 2015-06-19
Let's remove the last parameter we tried then we will add it and another one that hopefully will make it work.
```
sudo sed -i '/11n_disable/ d' /etc/modprobe.d/iwl4965.conf
```
Then do: 
```
sudo -i
echo "options iwl4965 swcrypto=1 11n_disable=1" >> /etc/modprobe.d/iwl4965.conf
```
make sure the usb adaptor is unplugged if it does not connect run and post a fresh report from the wireless script. 

We may have to set your country code as well right now it is showing for the U.S. and I believe you are in Europe.
Thanks

---

### Post by mp-y on 2015-06-19
Thanks again both of you.

I have set AP to WPA2 using AES.  No joy

I have followed your (Wildman) instructions to change the settings again, rebooted but still nothing.

I tried something else - I set my mobile phone as a hotspot and was able to connect to that, just no joy with the home wifi.

[ATTACH]262716[/ATTACH]

Couldn't work out where the country code is set.

Looking at the silver lining - getting to learn some useful commands and understanding the command line even better.:p

---

### Post by tgalati4 on 2015-06-19
Looking through your output:  What is a Logitech Unifying Receiver?  Is that a wireless keyboard and mouse?  Does it operate at 2.4 GHz?  If so remove it.

Also, are you sure you don't have bluetooth?  Most Thinkpads do.  Check your build sheet on the Lenovo/IBM website using your model number. The* rfkill list* is showing no bluetooth.   It's possible that the bluetooth switch needs to turned off in the driver:

> [iwlegacy]
**bt_coex_active: Y**
led_mode: 0

Also what are the BTWiFi devices?  They are taking up a lot of channels.

You can see channel 13 which means your wireless card is OK, but the intermediate wireless driver thinks it is regulatory domain 00, which is possibly US.

> [cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

The other switch is for 20 MHz bands vs 40 MHz bands.  Tighter bands can help in noisy, crowded wifi areas, but with less range.  I believe you are currently using 40 MHz bands.

Perhaps remove the wireless card with the laptop shut down, and yourself well-grounded, then try the USB dongle and see if it connects.  There may be a subtle hardware problem with this wireless card.  They normally work out-of-the box.  Put your finger on the card chip while in use.  If it is really hot, then it's time to replace it.

---

### Post by wildmanne39 on 2015-06-19
I recommend that your regulatory domain be set to your country. 

Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set US
```Of course, substitute your country code if not United States. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=US
```Proofread carefully, save and close the text editor.
Thanks

---

### Post by mp-y on 2015-06-19
I have set the country code to GB (I am in the United Kingdom), rebooted but still no joy.

I really don't think there is a problem with the wifi card hardware - it worked fine for windows 7, it will connect to my mobile hotspot, and when forcing the usb connection, it still doesn't work.  It's quite an involved task getting to the innards, so i'd rather avoid that unless I'm convinced it's the issue.

---

### Post by tgalati4 on 2015-06-19
On my T43p the wireless card is easily accessed through a small door on the backside.  You need a small torx driver.  Is yours different?

You are going to hate this suggestion:  Burn a disk of 10.04 32-bit and boot from that.  In the Live Session, see if your wireless works.  If so, then there is a regression in the Intel wireless driver.  Your hardware works, but there is some issue with the configuration because your log files show it takes 3 tries to authenticate and then fail.  It should authenticate immediately.  

Is your router set to "open" key or "shared" key?  You want "shared" or "pre-shared key" PSK.

The fact that your USB wireless dongle is also not working points to your AP and it's configuration.

---

### Post by wildmanne39 on 2015-06-19
I believe the second command in post 14 failed please do:
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```
and post the contents of that file.
Thanks

---

### Post by mp-y on 2015-06-20
> **Wild Man said:**
> I believe the second command in post 14 failed please do:
```
gksudo gedit /etc/modprobe.d/iwl4965.conf
```
and post the contents of that file.
Thanks

Hi Wildman
The contents of the file
```
options iwl4965 swcrypto=1 11n_disable=1
```
Thanks


> On my T43p the wireless card is easily accessed through a small door on  the backside.  You need a small torx driver.  Is yours different?

Yes - I have to take about about a half dozen screws and lift the keyboard

> You are going to hate this suggestion:  Burn a disk of 10.04 32-bit and  boot from that.  In the Live Session, see if your wireless works.  If  so, then there is a regression in the Intel wireless driver.  Your  hardware works, but there is some issue with the configuration because  your log files show it takes 3 tries to authenticate and then fail.  It  should authenticate immediately.  

I'll give that a shot

> Is your router set to "open" key or "shared" key?  You want "shared" or "pre-shared key" PSK.
WPA2-PSK - I had tried "WPA-PSK and WPA2-PSK" before as ubuntu network manager offers "WPA and WPA2 - Personal" when configuring a wireless network from scratch, rather than separate settings, though it was on WPA2-PSK at all times before that.

> The fact that your USB wireless dongle is also not working points to your AP and it's configuration. 
Surely, the fact that the same laptop worked with the AP, together with another laptop, a desktop PC, a Nintendo Wii, 5 android devices and a Kindle, points to Ubuntu and its configuration of the hardware?

Thanks

---

### Post by mp-y on 2015-06-20
Tried 10.04 - wireless works fine
Tried 12.04 - same issue with the wireless as my current installation

---

### Post by mp-y on 2015-06-26
Out of interest, I tried Linux Mint 17.1 but exactly the same.  Not too surprising as based on 14.04 but thought it was worth a shot.

Any other ideas?

---

### Post by tgalati4 on 2015-06-26
As I recall, the Intel wireless driver consisted of a binary blob attached to an open source wedge that linked to the kernel.  Over time (perhaps between 10.04 and 12.04) it was written as an entirely open source driver.  So I would explore the history of the driver and what specifically changed.  The reason for reseating the wireless card is so that you can verify the make and model of the wifi card and make sure it is the original card.  It's possible that the 14.04 Intel Wireless driver is choosing the wrong configuration because the card is slightly different (perhaps a Rev change or a later replacement) and the driver doesn't handle it properly.

Using 10.04 proves that the card works under linux, but 12.04 and later points to a driver problem.  Compare *lsmod* between 10.04 and 12.04.

---

### Post by mp-y on 2015-06-27
Hmmm, sounds complex.  I have bought a new access point to replace the netgears, and it now works fine.

Thanks for all your assistance tgalati4 and wildman

---

### Post by tgalati4 on 2015-06-27
You can mark this thread as SOLVED by using Thread Tools.

---

