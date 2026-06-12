---
title: "Problems with WIFI connection"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by mantecas21 on 2013-12-07
Since last week I noticed that my computer was going offline, however the icon appeared as connected. I tried to restart the network manager and try to connect again with no success, even I uninstalled the Firefox and reinstall it, no success. Now I dont have any access to the internet. I have been looking for some information about this issue, and tried some of the suggestions, but no success, still not having access to the internet.

I am using Sony VAIO with an atheron 9285 adapter. Tried to reinstall the controllers but I could not.
In one of the latest thread that I found I typed the commands suggested in the terminal and I found something interesting that may be the cause of the adapter to be going offline. Following is the outcome of that command:
[ 1240.135889] wlan0: AP f4:3e:61:28:e2:c8 changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 1240.135897] wlan0: AP f4:3e:61:28:e2:c8 changed bandwidth in a way we can't support - disconnect
[ 1241.052910] wlan0: authenticate with f4:3e:61:28:e2:c8
[ 1241.068695] wlan0: send auth to f4:3e:61:28:e2:c8 (try 1/3)
[ 1241.070761] wlan0: authenticated
[ 1241.076074] wlan0: associate with f4:3e:61:28:e2:c8 (try 1/3)
[ 1241.079875] wlan0: RX AssocResp from f4:3e:61:28:e2:c8 (capab=0x401 status=0 aid=4)
[ 1241.079925] wlan0: associated
[ 1241.083503] ath: regdomain 0x8348 updated by CountryIE
[ 1241.083508] ath: EEPROM regdomain: 0x8348
[ 1241.083510] ath: EEPROM indicates we should expect a country code
[ 1241.083512] ath: doing EEPROM country->regdmn map search
[ 1241.083514] ath: country maps to regdmn code: 0x3a
[ 1241.083515] ath: Country alpha2 being used: US
[ 1241.083517] ath: Regpair used: 0x3a
[ 1241.159902] wlan0: AP f4:3e:61:28:e2:c8 changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 1241.159909] wlan0: AP f4:3e:61:28:e2:c8 changed bandwidth in a way we can't support - disconnect

Do you know what can be the problem??

Thanks

---

### Post by mantecas21 on 2013-12-07
In my case i dont have an asus laptop, mine is Sony VAIO. I am attaching the file after running the script, can you help me with it.

Regards

---

### Post by Iowan on 2013-12-07
Threads merged.

---

### Post by varunendra on 2013-12-07
Thanks for the prompt move Iowan, didn't expect the report to be addressed this fast. :)

@mantecas21,
First of all, Welcome to the forums ! :)

You may be right about this causing the problem -> **mantecas21 said:**
> 
[ 1240.135889] wlan0: AP f4:3e:61:28:e2:c8 changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 1240.135897] wlan0: [COLOR="#FF0000"]AP f4:3e:61:28:e2:c8 changed bandwidth in a way we can't support - disconnect[/COLOR]

Are you in US? Is you router set to use the same settings (regulatory domain settings)?

---

### Post by mantecas21 on 2013-12-13
Varun:
Thanks a lot, no I am not in US, originally I installed Ubuntu in Trinidad and Tobago, there pretty much uses internet providers from US and Canada, or at least local settings (from Trinidad and Tobago) are like those countries. The thing is when I was there in Trinidad it worked fine, but now that I am in Venezuela, after two weeks it started to behave like this, to the point that I can't get connected to the internet, not even intermittent connection. The router I am trying to connect is the one from the hotel I am staying at, so I can't edit any setting, the funny thing is that it was working fine and suddenly it stopped. Is there a way that I can reset the whole network settings with the terminal? Now I am using another computer running windows 7 and trying to fix the problem in Ubuntu.
Regards
mantecas21

---

### Post by mantecas21 on 2013-12-13
Varun, good news:
Just 10 minutes after my last post,  i found one post you put before:
As per the script output, you seem to be connected. Is the report from  when it was working? Maybe one from the non-working state could give us  some more clues.

"For now, please try these -

1) Try disabling the firewall. If this helps, maybe your firewall configuration is causing troubles. To disable it -
 	Code:

 	sudo ufw disable

2) Try these parameters (one at a time) -


 	Code:

 	sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1 enable_diversity=1

This will be a temporary change and will be lost at next boot. If it seems to help, we can make it permanent. Also, try only one of the 
parameters first (either "nohwcrypt=1" or "enable_diversity=1"). Both together if trying them separately doesn't seem to help (although none 
of them is guaranteed to help)." 
I should say that I run both separated, one at a time, and I got connected, can you figure out what is going on?

Regards
mantecas21

---

### Post by varunendra on 2013-12-14
> **mantecas21 said:**
> can you figure out what is going on?

I can't even guess with the amount of info we currently have here. I'd suggest to try only one parameter at a time and see if any one of them alone can help. You can then write a .conf file to make the parameter permanent.

For example, if it turns out to be the "nohwcrypt=1" parameter, you can make it permanent with -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

This will create a file "ath9k.conf" in the /etc/modprobe.d/ directory with just one line (options ath9k nohwcrypt=1) in it, which makes the parameter load automatically since next boot.

**PS:**
If the problem re-appears, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mantecas21 on 2013-12-17
Varun attached the results of the latest script run.
Regards
mantecas21
```
 
*************** info trace ***************

***** uname -a *****

Linux chicos 3.13.0-031300rc2-generic #201311291635 SMP Fri Nov 29 21:36:49 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller [11ab:4380] (rev 10)
    Subsystem: Sony Corporation Device [104d:906b]
    Kernel driver in use: sky2
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b14e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"MAXELL"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC address removed>   
          Bit Rate=135 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0


***** rfkill *****

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 166504  0 
ath9k_common           13551  1 ath9k
ath9k_hw              462889  2 ath9k_common,ath9k
ath                    29145  3 ath9k_common,ath9k,ath9k_hw
mac80211              654078  1 ath9k
cfg80211              509407  3 ath,ath9k,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [MAXELL] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           135 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Red Wi-Fi de Filip: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2
    401:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    HEBERTICO_NETWORk : Infra, <MAC address removed>, Freq 2412 MHz, Rate 11 Mb/s, Strength 20
    *MAXELL:         Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 84
    AlexRed-Wifi *0414-6594314*: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2

  IPv4 Settings:
    Address:         192.168.254.22
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.254.1

    DNS:             192.168.254.1


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
                    Channel:13
                    Frequency:2.472 GHz
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:"MAXELL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000055b36d2cca
                    Extra: Last beacon: 639480ms ago
                    IE: Unknown: 00064D4158454C4C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030029127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D070500000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Conexion2_60bfs 0414.6594314"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a8223180
                    Extra: Last beacon: 1088ms ago
                    IE: Unknown: 001C436F6E6578696F6E325F363062667320303431342E36353934333134
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F202010185000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405001D00000000000000000000000000000000000000
                    IE: Unknown: 3D1605001D00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E00156D000000010202E202021200
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Red Wi-Fi de Filip"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000469171e00f
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00125265642057692D46692064652046696C6970
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021900
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301770320
                    IE: Unknown: DD0E0017F207000101069072400F8AE3
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 04 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Conexion1_60bfs*0414.6594314*"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb970fd662
                    Extra: Last beacon: 408ms ago
                    IE: Unknown: 001D436F6E6578696F6E315F36306266732A303431342E363539343331342A
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010020FF7F


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

filename:       /lib/modules/3.13.0-031300rc2-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     13569A40BBE6FC9041B15A4
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-031300rc2-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)

filename:       /lib/modules/3.13.0-031300rc2-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-031300rc2-generic SMP mod_unload modversions 

filename:       /lib/modules/3.13.0-031300rc2-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A6171FCD7FD36C65AC545
depends:        ath
intree:         Y
vermagic:       3.13.0-031300rc2-generic SMP mod_unload modversions 

filename:       /lib/modules/3.13.0-031300rc2-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-031300rc2-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[ 2725.236864] wlan0: authenticate with <MAC address removed>
[ 2725.252670] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2725.254702] wlan0: authenticated
[ 2725.260039] wlan0: associate with <MAC address removed> (try 1/3)
[ 2725.264362] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2725.264412] wlan0: associated
[ 2725.268748] ath: EEPROM regdomain: 0x8348
[ 2725.268755] ath: EEPROM indicates we should expect a country code
[ 2725.268759] ath: doing EEPROM country->regdmn map search
[ 2725.268762] ath: country maps to regdmn code: 0x3a
[ 2725.268765] ath: Country alpha2 being used: US
[ 2725.268767] ath: Regpair used: 0x3a
[ 2725.268771] ath: regdomain 0x8348 dynamically updated by country IE
[ 2725.348928] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2725.348936] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2726.313131] wlan0: authenticate with <MAC address removed>
[ 2726.329004] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2726.332060] wlan0: authenticated
[ 2726.340117] wlan0: associate with <MAC address removed> (try 1/3)
[ 2726.344217] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2726.344294] wlan0: associated
[ 2726.350302] ath: EEPROM regdomain: 0x8348
[ 2726.350311] ath: EEPROM indicates we should expect a country code
[ 2726.350315] ath: doing EEPROM country->regdmn map search
[ 2726.350318] ath: country maps to regdmn code: 0x3a
[ 2726.350321] ath: Country alpha2 being used: US
[ 2726.350324] ath: Regpair used: 0x3a
[ 2726.350327] ath: regdomain 0x8348 dynamically updated by country IE
[ 2726.372858] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2726.372865] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2727.332861] wlan0: authenticate with <MAC address removed>
[ 2727.348679] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2727.350737] wlan0: authenticated
[ 2727.356062] wlan0: associate with <MAC address removed> (try 1/3)
[ 2727.359953] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2727.360056] wlan0: associated
[ 2727.366089] ath: EEPROM regdomain: 0x8348
[ 2727.366097] ath: EEPROM indicates we should expect a country code
[ 2727.366101] ath: doing EEPROM country->regdmn map search
[ 2727.366104] ath: country maps to regdmn code: 0x3a
[ 2727.366108] ath: Country alpha2 being used: US
[ 2727.366110] ath: Regpair used: 0x3a
[ 2727.366114] ath: regdomain 0x8348 dynamically updated by country IE
[ 2727.396839] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2727.396845] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2728.304879] wlan0: authenticate with <MAC address removed>
[ 2728.320718] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2728.323057] wlan0: authenticated
[ 2728.324096] wlan0: associate with <MAC address removed> (try 1/3)
[ 2728.327925] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2728.327975] wlan0: associated
[ 2728.334220] ath: EEPROM regdomain: 0x8348
[ 2728.334227] ath: EEPROM indicates we should expect a country code
[ 2728.334231] ath: doing EEPROM country->regdmn map search
[ 2728.334234] ath: country maps to regdmn code: 0x3a
[ 2728.334237] ath: Country alpha2 being used: US
[ 2728.334240] ath: Regpair used: 0x3a
[ 2728.334243] ath: regdomain 0x8348 dynamically updated by country IE
[ 2728.420864] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2728.420872] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2729.337053] wlan0: authenticate with <MAC address removed>
[ 2729.352983] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2729.354909] wlan0: authenticated
[ 2729.356065] wlan0: associate with <MAC address removed> (try 1/3)
[ 2729.359910] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2729.359963] wlan0: associated
[ 2729.364441] ath: EEPROM regdomain: 0x8348
[ 2729.364447] ath: EEPROM indicates we should expect a country code
[ 2729.364449] ath: doing EEPROM country->regdmn map search
[ 2729.364451] ath: country maps to regdmn code: 0x3a
[ 2729.364452] ath: Country alpha2 being used: US
[ 2729.364454] ath: Regpair used: 0x3a
[ 2729.364456] ath: regdomain 0x8348 dynamically updated by country IE
[ 2729.444788] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2729.444793] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2730.356892] wlan0: authenticate with <MAC address removed>
[ 2730.372738] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2730.374766] wlan0: authenticated
[ 2730.376098] wlan0: associate with <MAC address removed> (try 1/3)
[ 2730.379947] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2730.380000] wlan0: associated
[ 2730.386161] ath: EEPROM regdomain: 0x8348
[ 2730.386170] ath: EEPROM indicates we should expect a country code
[ 2730.386173] ath: doing EEPROM country->regdmn map search
[ 2730.386177] ath: country maps to regdmn code: 0x3a
[ 2730.386180] ath: Country alpha2 being used: US
[ 2730.386182] ath: Regpair used: 0x3a
[ 2730.386186] ath: regdomain 0x8348 dynamically updated by country IE
[ 2730.468807] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2730.468813] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2731.384883] wlan0: authenticate with <MAC address removed>
[ 2731.400652] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2731.402663] wlan0: authenticated
[ 2731.404096] wlan0: associate with <MAC address removed> (try 1/3)
[ 2731.407980] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2731.408050] wlan0: associated
[ 2731.412369] ath: EEPROM regdomain: 0x8348
[ 2731.412377] ath: EEPROM indicates we should expect a country code
[ 2731.412380] ath: doing EEPROM country->regdmn map search
[ 2731.412384] ath: country maps to regdmn code: 0x3a
[ 2731.412387] ath: Country alpha2 being used: US
[ 2731.412389] ath: Regpair used: 0x3a
[ 2731.412393] ath: regdomain 0x8348 dynamically updated by country IE
[ 2731.492839] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2731.492847] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2732.405032] wlan0: authenticate with <MAC address removed>
[ 2732.420891] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2732.422913] wlan0: authenticated
[ 2732.424108] wlan0: associate with <MAC address removed> (try 1/3)
[ 2732.427956] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2732.428020] wlan0: associated
[ 2732.432800] ath: EEPROM regdomain: 0x8348
[ 2732.432807] ath: EEPROM indicates we should expect a country code
[ 2732.432810] ath: doing EEPROM country->regdmn map search
[ 2732.432814] ath: country maps to regdmn code: 0x3a
[ 2732.432817] ath: Country alpha2 being used: US
[ 2732.432819] ath: Regpair used: 0x3a
[ 2732.432823] ath: regdomain 0x8348 dynamically updated by country IE
[ 2732.516845] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2732.516852] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2733.481296] wlan0: authenticate with <MAC address removed>
[ 2733.497517] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2733.499504] wlan0: authenticated
[ 2733.500133] wlan0: associate with <MAC address removed> (try 1/3)
[ 2733.503932] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2733.503979] wlan0: associated
[ 2733.508318] ath: EEPROM regdomain: 0x8348
[ 2733.508322] ath: EEPROM indicates we should expect a country code
[ 2733.508325] ath: doing EEPROM country->regdmn map search
[ 2733.508326] ath: country maps to regdmn code: 0x3a
[ 2733.508328] ath: Country alpha2 being used: US
[ 2733.508330] ath: Regpair used: 0x3a
[ 2733.508332] ath: regdomain 0x8348 dynamically updated by country IE
[ 2733.540856] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2733.540864] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2734.448872] wlan0: authenticate with <MAC address removed>
[ 2734.464782] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2734.466705] wlan0: authenticated
[ 2734.468070] wlan0: associate with <MAC address removed> (try 1/3)
[ 2734.472263] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2734.472336] wlan0: associated
[ 2734.478257] ath: EEPROM regdomain: 0x8348
[ 2734.478262] ath: EEPROM indicates we should expect a country code
[ 2734.478264] ath: doing EEPROM country->regdmn map search
[ 2734.478266] ath: country maps to regdmn code: 0x3a
[ 2734.478268] ath: Country alpha2 being used: US
[ 2734.478269] ath: Regpair used: 0x3a
[ 2734.478271] ath: regdomain 0x8348 dynamically updated by country IE
[ 2734.564855] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2734.564865] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2735.477190] wlan0: authenticate with <MAC address removed>
[ 2735.493127] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2735.495159] wlan0: authenticated
[ 2735.500079] wlan0: associate with <MAC address removed> (try 1/3)
[ 2735.504182] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2735.504256] wlan0: associated
[ 2735.510411] ath: EEPROM regdomain: 0x8348
[ 2735.510419] ath: EEPROM indicates we should expect a country code
[ 2735.510422] ath: doing EEPROM country->regdmn map search
[ 2735.510426] ath: country maps to regdmn code: 0x3a
[ 2735.510429] ath: Country alpha2 being used: US
[ 2735.510431] ath: Regpair used: 0x3a
[ 2735.510439] ath: regdomain 0x8348 dynamically updated by country IE
[ 2735.588821] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2735.588828] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2736.553208] wlan0: authenticate with <MAC address removed>
[ 2736.568965] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2736.571178] wlan0: authenticated
[ 2736.576102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2736.579965] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2736.580047] wlan0: associated
[ 2736.585086] ath: EEPROM regdomain: 0x8348
[ 2736.585092] ath: EEPROM indicates we should expect a country code
[ 2736.585094] ath: doing EEPROM country->regdmn map search
[ 2736.585097] ath: country maps to regdmn code: 0x3a
[ 2736.585099] ath: Country alpha2 being used: US
[ 2736.585101] ath: Regpair used: 0x3a
[ 2736.585104] ath: regdomain 0x8348 dynamically updated by country IE
[ 2736.612809] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2736.612815] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2737.576879] wlan0: authenticate with <MAC address removed>
[ 2737.592724] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2737.595612] wlan0: authenticated
[ 2737.600102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2737.603958] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2737.604055] wlan0: associated
[ 2737.611912] ath: EEPROM regdomain: 0x8348
[ 2737.611921] ath: EEPROM indicates we should expect a country code
[ 2737.611924] ath: doing EEPROM country->regdmn map search
[ 2737.611928] ath: country maps to regdmn code: 0x3a
[ 2737.611931] ath: Country alpha2 being used: US
[ 2737.611934] ath: Regpair used: 0x3a
[ 2737.611937] ath: regdomain 0x8348 dynamically updated by country IE
[ 2737.636801] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2737.636807] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2738.545509] wlan0: authenticate with <MAC address removed>
[ 2738.561302] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2738.563332] wlan0: authenticated
[ 2738.564106] wlan0: associate with <MAC address removed> (try 1/3)
[ 2738.567864] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2738.567912] wlan0: associated
[ 2738.572087] ath: EEPROM regdomain: 0x8348
[ 2738.572092] ath: EEPROM indicates we should expect a country code
[ 2738.572094] ath: doing EEPROM country->regdmn map search
[ 2738.572096] ath: country maps to regdmn code: 0x3a
[ 2738.572098] ath: Country alpha2 being used: US
[ 2738.572099] ath: Regpair used: 0x3a
[ 2738.572101] ath: regdomain 0x8348 dynamically updated by country IE
[ 2738.660830] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2738.660837] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2739.577537] wlan0: authenticate with <MAC address removed>
[ 2739.593409] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2739.595386] wlan0: authenticated
[ 2739.596106] wlan0: associate with <MAC address removed> (try 1/3)
[ 2739.599943] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2739.599994] wlan0: associated
[ 2739.604211] ath: EEPROM regdomain: 0x8348
[ 2739.604217] ath: EEPROM indicates we should expect a country code
[ 2739.604219] ath: doing EEPROM country->regdmn map search
[ 2739.604221] ath: country maps to regdmn code: 0x3a
[ 2739.604223] ath: Country alpha2 being used: US
[ 2739.604224] ath: Regpair used: 0x3a
[ 2739.604226] ath: regdomain 0x8348 dynamically updated by country IE
[ 2739.684822] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2739.684827] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2740.657152] wlan0: authenticate with <MAC address removed>
[ 2740.673077] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2740.675054] wlan0: authenticated
[ 2740.676108] wlan0: associate with <MAC address removed> (try 1/3)
[ 2740.679979] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2740.680049] wlan0: associated
[ 2740.684519] ath: EEPROM regdomain: 0x8348
[ 2740.684524] ath: EEPROM indicates we should expect a country code
[ 2740.684526] ath: doing EEPROM country->regdmn map search
[ 2740.684528] ath: country maps to regdmn code: 0x3a
[ 2740.684530] ath: Country alpha2 being used: US
[ 2740.684531] ath: Regpair used: 0x3a
[ 2740.684533] ath: regdomain 0x8348 dynamically updated by country IE
[ 2740.708858] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2740.708865] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2741.676892] wlan0: authenticate with <MAC address removed>
[ 2741.692653] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2741.694729] wlan0: authenticated
[ 2741.696114] wlan0: associate with <MAC address removed> (try 1/3)
[ 2741.699940] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2741.699992] wlan0: associated
[ 2741.704832] ath: EEPROM regdomain: 0x8348
[ 2741.704837] ath: EEPROM indicates we should expect a country code
[ 2741.704839] ath: doing EEPROM country->regdmn map search
[ 2741.704841] ath: country maps to regdmn code: 0x3a
[ 2741.704842] ath: Country alpha2 being used: US
[ 2741.704844] ath: Regpair used: 0x3a
[ 2741.704846] ath: regdomain 0x8348 dynamically updated by country IE
[ 2741.732856] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2741.732864] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2742.640911] wlan0: authenticate with <MAC address removed>
[ 2742.656633] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2742.658585] wlan0: authenticated
[ 2742.660109] wlan0: associate with <MAC address removed> (try 1/3)
[ 2742.663877] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2742.663936] wlan0: associated
[ 2742.668342] ath: EEPROM regdomain: 0x8348
[ 2742.668348] ath: EEPROM indicates we should expect a country code
[ 2742.668352] ath: doing EEPROM country->regdmn map search
[ 2742.668355] ath: country maps to regdmn code: 0x3a
[ 2742.668358] ath: Country alpha2 being used: US
[ 2742.668361] ath: Regpair used: 0x3a
[ 2742.668366] ath: regdomain 0x8348 dynamically updated by country IE
[ 2742.756792] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2742.756797] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2743.664886] wlan0: authenticate with <MAC address removed>
[ 2743.680761] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2743.682705] wlan0: authenticated
[ 2743.684102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2743.687946] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2743.688021] wlan0: associated
[ 2743.695481] ath: EEPROM regdomain: 0x8348
[ 2743.695490] ath: EEPROM indicates we should expect a country code
[ 2743.695493] ath: doing EEPROM country->regdmn map search
[ 2743.695497] ath: country maps to regdmn code: 0x3a
[ 2743.695501] ath: Country alpha2 being used: US
[ 2743.695503] ath: Regpair used: 0x3a
[ 2743.695507] ath: regdomain 0x8348 dynamically updated by country IE
[ 2743.780811] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2743.780819] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2744.748881] wlan0: authenticate with <MAC address removed>
[ 2744.764702] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2744.767709] wlan0: authenticated
[ 2744.768060] wlan0: associate with <MAC address removed> (try 1/3)
[ 2744.773509] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2744.773574] wlan0: associated
[ 2744.777562] ath: EEPROM regdomain: 0x8348
[ 2744.777567] ath: EEPROM indicates we should expect a country code
[ 2744.777569] ath: doing EEPROM country->regdmn map search
[ 2744.777571] ath: country maps to regdmn code: 0x3a
[ 2744.777573] ath: Country alpha2 being used: US
[ 2744.777574] ath: Regpair used: 0x3a
[ 2744.777576] ath: regdomain 0x8348 dynamically updated by country IE
[ 2744.804800] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2744.804805] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2745.716890] wlan0: authenticate with <MAC address removed>
[ 2745.732768] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2745.734786] wlan0: authenticated
[ 2745.740099] wlan0: associate with <MAC address removed> (try 1/3)
[ 2745.743910] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2745.743977] wlan0: associated
[ 2745.749896] ath: EEPROM regdomain: 0x8348
[ 2745.749903] ath: EEPROM indicates we should expect a country code
[ 2745.749907] ath: doing EEPROM country->regdmn map search
[ 2745.749910] ath: country maps to regdmn code: 0x3a
[ 2745.749913] ath: Country alpha2 being used: US
[ 2745.749916] ath: Regpair used: 0x3a
[ 2745.749919] ath: regdomain 0x8348 dynamically updated by country IE
[ 2745.828832] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2745.828840] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2746.745159] wlan0: authenticate with <MAC address removed>
[ 2746.761145] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2746.763191] wlan0: authenticated
[ 2746.764103] wlan0: associate with <MAC address removed> (try 1/3)
[ 2746.767876] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2746.767927] wlan0: associated
[ 2746.771797] ath: EEPROM regdomain: 0x8348
[ 2746.771803] ath: EEPROM indicates we should expect a country code
[ 2746.771805] ath: doing EEPROM country->regdmn map search
[ 2746.771807] ath: country maps to regdmn code: 0x3a
[ 2746.771809] ath: Country alpha2 being used: US
[ 2746.771810] ath: Regpair used: 0x3a
[ 2746.771813] ath: regdomain 0x8348 dynamically updated by country IE
[ 2746.852843] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2746.852851] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2747.817136] wlan0: authenticate with <MAC address removed>
[ 2747.832988] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2747.835430] wlan0: authenticated
[ 2747.840090] wlan0: associate with <MAC address removed> (try 1/3)
[ 2747.843915] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2747.843968] wlan0: associated
[ 2747.851014] ath: EEPROM regdomain: 0x8348
[ 2747.851022] ath: EEPROM indicates we should expect a country code
[ 2747.851026] ath: doing EEPROM country->regdmn map search
[ 2747.851029] ath: country maps to regdmn code: 0x3a
[ 2747.851032] ath: Country alpha2 being used: US
[ 2747.851035] ath: Regpair used: 0x3a
[ 2747.851039] ath: regdomain 0x8348 dynamically updated by country IE
[ 2747.876860] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2747.876868] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2748.837159] wlan0: authenticate with <MAC address removed>
[ 2748.853049] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2748.855113] wlan0: authenticated
[ 2748.856104] wlan0: associate with <MAC address removed> (try 1/3)
[ 2748.861702] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2748.861756] wlan0: associated
[ 2748.866578] ath: EEPROM regdomain: 0x8348
[ 2748.866585] ath: EEPROM indicates we should expect a country code
[ 2748.866589] ath: doing EEPROM country->regdmn map search
[ 2748.866592] ath: country maps to regdmn code: 0x3a
[ 2748.866595] ath: Country alpha2 being used: US
[ 2748.866598] ath: Regpair used: 0x3a
[ 2748.866601] ath: regdomain 0x8348 dynamically updated by country IE
[ 2748.900790] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2748.900796] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2749.812869] wlan0: authenticate with <MAC address removed>
[ 2749.828611] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2749.832666] wlan0: authenticated
[ 2749.836091] wlan0: associate with <MAC address removed> (try 1/3)
[ 2749.840138] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2749.840203] wlan0: associated
[ 2749.844063] ath: EEPROM regdomain: 0x8348
[ 2749.844068] ath: EEPROM indicates we should expect a country code
[ 2749.844070] ath: doing EEPROM country->regdmn map search
[ 2749.844072] ath: country maps to regdmn code: 0x3a
[ 2749.844073] ath: Country alpha2 being used: US
[ 2749.844075] ath: Regpair used: 0x3a
[ 2749.844077] ath: regdomain 0x8348 dynamically updated by country IE
[ 2749.927192] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2749.927197] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2750.888871] wlan0: authenticate with <MAC address removed>
[ 2750.904741] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2750.907985] wlan0: authenticated
[ 2750.912128] wlan0: associate with <MAC address removed> (try 1/3)
[ 2750.915980] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2750.916081] wlan0: associated
[ 2750.921724] ath: EEPROM regdomain: 0x8348
[ 2750.921731] ath: EEPROM indicates we should expect a country code
[ 2750.921735] ath: doing EEPROM country->regdmn map search
[ 2750.921738] ath: country maps to regdmn code: 0x3a
[ 2750.921741] ath: Country alpha2 being used: US
[ 2750.921744] ath: Regpair used: 0x3a
[ 2750.921747] ath: regdomain 0x8348 dynamically updated by country IE
[ 2750.948793] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2750.948799] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2751.860925] wlan0: authenticate with <MAC address removed>
[ 2751.876784] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2751.878851] wlan0: authenticated
[ 2751.880097] wlan0: associate with <MAC address removed> (try 1/3)
[ 2751.883857] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2751.883907] wlan0: associated
[ 2751.889706] ath: EEPROM regdomain: 0x8348
[ 2751.889713] ath: EEPROM indicates we should expect a country code
[ 2751.889717] ath: doing EEPROM country->regdmn map search
[ 2751.889720] ath: country maps to regdmn code: 0x3a
[ 2751.889723] ath: Country alpha2 being used: US
[ 2751.889726] ath: Regpair used: 0x3a
[ 2751.889729] ath: regdomain 0x8348 dynamically updated by country IE
[ 2751.973988] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2751.973996] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2752.893087] wlan0: authenticate with <MAC address removed>
[ 2752.908971] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2752.912076] wlan0: authenticated
[ 2752.916112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2752.920038] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2752.920113] wlan0: associated
[ 2752.926568] ath: EEPROM regdomain: 0x8348
[ 2752.926575] ath: EEPROM indicates we should expect a country code
[ 2752.926579] ath: doing EEPROM country->regdmn map search
[ 2752.926582] ath: country maps to regdmn code: 0x3a
[ 2752.926586] ath: Country alpha2 being used: US
[ 2752.926588] ath: Regpair used: 0x3a
[ 2752.926592] ath: regdomain 0x8348 dynamically updated by country IE
[ 2752.997726] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2752.997734] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2753.913086] wlan0: authenticate with <MAC address removed>
[ 2753.928962] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2753.930936] wlan0: authenticated
[ 2753.932096] wlan0: associate with <MAC address removed> (try 1/3)
[ 2753.936369] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2753.936439] wlan0: associated
[ 2753.942475] ath: EEPROM regdomain: 0x8348
[ 2753.942482] ath: EEPROM indicates we should expect a country code
[ 2753.942486] ath: doing EEPROM country->regdmn map search
[ 2753.942489] ath: country maps to regdmn code: 0x3a
[ 2753.942492] ath: Country alpha2 being used: US
[ 2753.942495] ath: Regpair used: 0x3a
[ 2753.942498] ath: regdomain 0x8348 dynamically updated by country IE
[ 2754.020830] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2754.020836] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2754.941036] wlan0: authenticate with <MAC address removed>
[ 2754.956908] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2754.958907] wlan0: authenticated
[ 2754.960061] wlan0: associate with <MAC address removed> (try 1/3)
[ 2754.963922] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2754.963971] wlan0: associated
[ 2754.968402] ath: EEPROM regdomain: 0x8348
[ 2754.968406] ath: EEPROM indicates we should expect a country code
[ 2754.968408] ath: doing EEPROM country->regdmn map search
[ 2754.968410] ath: country maps to regdmn code: 0x3a
[ 2754.968412] ath: Country alpha2 being used: US
[ 2754.968414] ath: Regpair used: 0x3a
[ 2754.968416] ath: regdomain 0x8348 dynamically updated by country IE
[ 2755.044773] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2755.044778] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2755.965190] wlan0: authenticate with <MAC address removed>
[ 2755.981075] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2755.983077] wlan0: authenticated
[ 2755.984095] wlan0: associate with <MAC address removed> (try 1/3)
[ 2755.987858] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2755.987908] wlan0: associated
[ 2755.995563] ath: EEPROM regdomain: 0x8348
[ 2755.995570] ath: EEPROM indicates we should expect a country code
[ 2755.995574] ath: doing EEPROM country->regdmn map search
[ 2755.995577] ath: country maps to regdmn code: 0x3a
[ 2755.995580] ath: Country alpha2 being used: US
[ 2755.995583] ath: Regpair used: 0x3a
[ 2755.995586] ath: regdomain 0x8348 dynamically updated by country IE
[ 2756.068793] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2756.068801] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2756.993050] wlan0: authenticate with <MAC address removed>
[ 2757.008772] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2757.010788] wlan0: authenticated
[ 2757.012096] wlan0: associate with <MAC address removed> (try 1/3)
[ 2757.016120] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2757.016172] wlan0: associated
[ 2757.020414] ath: EEPROM regdomain: 0x8348
[ 2757.020421] ath: EEPROM indicates we should expect a country code
[ 2757.020424] ath: doing EEPROM country->regdmn map search
[ 2757.020428] ath: country maps to regdmn code: 0x3a
[ 2757.020431] ath: Country alpha2 being used: US
[ 2757.020433] ath: Regpair used: 0x3a
[ 2757.020437] ath: regdomain 0x8348 dynamically updated by country IE
[ 2757.092807] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2757.092815] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2758.005121] wlan0: authenticate with <MAC address removed>
[ 2758.020955] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2758.023021] wlan0: authenticated
[ 2758.024108] wlan0: associate with <MAC address removed> (try 1/3)
[ 2758.027954] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2758.028019] wlan0: associated
[ 2758.036813] ath: EEPROM regdomain: 0x8348
[ 2758.036820] ath: EEPROM indicates we should expect a country code
[ 2758.036824] ath: doing EEPROM country->regdmn map search
[ 2758.036827] ath: country maps to regdmn code: 0x3a
[ 2758.036830] ath: Country alpha2 being used: US
[ 2758.036833] ath: Regpair used: 0x3a
[ 2758.036840] ath: regdomain 0x8348 dynamically updated by country IE
[ 2758.116818] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2758.116826] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2759.029112] wlan0: authenticate with <MAC address removed>
[ 2759.045060] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2759.047310] wlan0: authenticated
[ 2759.048111] wlan0: associate with <MAC address removed> (try 1/3)
[ 2759.051880] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2759.051930] wlan0: associated
[ 2759.057886] ath: EEPROM regdomain: 0x8348
[ 2759.057891] ath: EEPROM indicates we should expect a country code
[ 2759.057893] ath: doing EEPROM country->regdmn map search
[ 2759.057895] ath: country maps to regdmn code: 0x3a
[ 2759.057897] ath: Country alpha2 being used: US
[ 2759.057898] ath: Regpair used: 0x3a
[ 2759.057900] ath: regdomain 0x8348 dynamically updated by country IE
[ 2759.140838] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2759.140846] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2760.057097] wlan0: authenticate with <MAC address removed>
[ 2760.073014] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2760.074972] wlan0: authenticated
[ 2760.076062] wlan0: associate with <MAC address removed> (try 1/3)
[ 2760.079922] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2760.079971] wlan0: associated
[ 2760.084101] ath: EEPROM regdomain: 0x8348
[ 2760.084106] ath: EEPROM indicates we should expect a country code
[ 2760.084109] ath: doing EEPROM country->regdmn map search
[ 2760.084111] ath: country maps to regdmn code: 0x3a
[ 2760.084113] ath: Country alpha2 being used: US
[ 2760.084114] ath: Regpair used: 0x3a
[ 2760.084116] ath: regdomain 0x8348 dynamically updated by country IE
[ 2760.164811] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2760.164816] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2761.133182] wlan0: authenticate with <MAC address removed>
[ 2761.149202] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2761.151136] wlan0: authenticated
[ 2761.156080] wlan0: associate with <MAC address removed> (try 1/3)
[ 2761.159891] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2761.159944] wlan0: associated
[ 2761.166723] ath: EEPROM regdomain: 0x8348
[ 2761.166730] ath: EEPROM indicates we should expect a country code
[ 2761.166733] ath: doing EEPROM country->regdmn map search
[ 2761.166737] ath: country maps to regdmn code: 0x3a
[ 2761.166740] ath: Country alpha2 being used: US
[ 2761.166742] ath: Regpair used: 0x3a
[ 2761.166746] ath: regdomain 0x8348 dynamically updated by country IE
[ 2761.188849] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2761.188857] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2762.101487] wlan0: authenticate with <MAC address removed>
[ 2762.117318] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2762.119278] wlan0: authenticated
[ 2762.120106] wlan0: associate with <MAC address removed> (try 1/3)
[ 2762.123971] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2762.124043] wlan0: associated
[ 2762.128093] ath: EEPROM regdomain: 0x8348
[ 2762.128097] ath: EEPROM indicates we should expect a country code
[ 2762.128099] ath: doing EEPROM country->regdmn map search
[ 2762.128101] ath: country maps to regdmn code: 0x3a
[ 2762.128103] ath: Country alpha2 being used: US
[ 2762.128104] ath: Regpair used: 0x3a
[ 2762.128107] ath: regdomain 0x8348 dynamically updated by country IE
[ 2762.212771] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2762.212777] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2763.177219] wlan0: authenticate with <MAC address removed>
[ 2763.193046] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2763.194997] wlan0: authenticated
[ 2763.196123] wlan0: associate with <MAC address removed> (try 1/3)
[ 2763.199964] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2763.200030] wlan0: associated
[ 2763.206179] ath: EEPROM regdomain: 0x8348
[ 2763.206191] ath: EEPROM indicates we should expect a country code
[ 2763.206195] ath: doing EEPROM country->regdmn map search
[ 2763.206198] ath: country maps to regdmn code: 0x3a
[ 2763.206201] ath: Country alpha2 being used: US
[ 2763.206204] ath: Regpair used: 0x3a
[ 2763.206207] ath: regdomain 0x8348 dynamically updated by country IE
[ 2763.236799] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2763.236807] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2764.145085] wlan0: authenticate with <MAC address removed>
[ 2764.160966] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2764.163036] wlan0: authenticated
[ 2764.164111] wlan0: associate with <MAC address removed> (try 1/3)
[ 2764.167880] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2764.167927] wlan0: associated
[ 2764.172093] ath: EEPROM regdomain: 0x8348
[ 2764.172106] ath: EEPROM indicates we should expect a country code
[ 2764.172110] ath: doing EEPROM country->regdmn map search
[ 2764.172113] ath: country maps to regdmn code: 0x3a
[ 2764.172116] ath: Country alpha2 being used: US
[ 2764.172119] ath: Regpair used: 0x3a
[ 2764.172122] ath: regdomain 0x8348 dynamically updated by country IE
[ 2764.260803] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2764.260815] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2765.228886] wlan0: authenticate with <MAC address removed>
[ 2765.244821] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2765.246792] wlan0: authenticated
[ 2765.248066] wlan0: associate with <MAC address removed> (try 1/3)
[ 2765.251898] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2765.251946] wlan0: associated
[ 2765.256817] ath: EEPROM regdomain: 0x8348
[ 2765.256823] ath: EEPROM indicates we should expect a country code
[ 2765.256825] ath: doing EEPROM country->regdmn map search
[ 2765.256827] ath: country maps to regdmn code: 0x3a
[ 2765.256829] ath: Country alpha2 being used: US
[ 2765.256830] ath: Regpair used: 0x3a
[ 2765.256832] ath: regdomain 0x8348 dynamically updated by country IE
[ 2765.284797] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2765.284803] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2766.244893] wlan0: authenticate with <MAC address removed>
[ 2766.260701] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2766.262693] wlan0: authenticated
[ 2766.268041] wlan0: associate with <MAC address removed> (try 1/3)
[ 2766.271908] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2766.271961] wlan0: associated
[ 2766.277900] ath: EEPROM regdomain: 0x8348
[ 2766.277907] ath: EEPROM indicates we should expect a country code
[ 2766.277911] ath: doing EEPROM country->regdmn map search
[ 2766.277914] ath: country maps to regdmn code: 0x3a
[ 2766.277917] ath: Country alpha2 being used: US
[ 2766.277919] ath: Regpair used: 0x3a
[ 2766.277923] ath: regdomain 0x8348 dynamically updated by country IE
[ 2766.308825] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2766.308837] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2767.220920] wlan0: authenticate with <MAC address removed>
[ 2767.236843] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2767.238918] wlan0: authenticated
[ 2767.240102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2767.243859] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2767.243909] wlan0: associated
[ 2767.250314] ath: EEPROM regdomain: 0x8348
[ 2767.250321] ath: EEPROM indicates we should expect a country code
[ 2767.250325] ath: doing EEPROM country->regdmn map search
[ 2767.250328] ath: country maps to regdmn code: 0x3a
[ 2767.250331] ath: Country alpha2 being used: US
[ 2767.250334] ath: Regpair used: 0x3a
[ 2767.250337] ath: regdomain 0x8348 dynamically updated by country IE
[ 2767.332834] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2767.332842] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2768.244935] wlan0: authenticate with <MAC address removed>
[ 2768.260608] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2768.262556] wlan0: authenticated
[ 2768.264111] wlan0: associate with <MAC address removed> (try 1/3)
[ 2768.267915] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2768.267970] wlan0: associated
[ 2768.271902] ath: EEPROM regdomain: 0x8348
[ 2768.271907] ath: EEPROM indicates we should expect a country code
[ 2768.271910] ath: doing EEPROM country->regdmn map search
[ 2768.271912] ath: country maps to regdmn code: 0x3a
[ 2768.271913] ath: Country alpha2 being used: US
[ 2768.271915] ath: Regpair used: 0x3a
[ 2768.271917] ath: regdomain 0x8348 dynamically updated by country IE
[ 2768.356787] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2768.356795] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2769.265177] wlan0: authenticate with <MAC address removed>
[ 2769.280965] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2769.283023] wlan0: authenticated
[ 2769.284109] wlan0: associate with <MAC address removed> (try 1/3)
[ 2769.287988] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2769.288054] wlan0: associated
[ 2769.292420] ath: EEPROM regdomain: 0x8348
[ 2769.292424] ath: EEPROM indicates we should expect a country code
[ 2769.292427] ath: doing EEPROM country->regdmn map search
[ 2769.292428] ath: country maps to regdmn code: 0x3a
[ 2769.292430] ath: Country alpha2 being used: US
[ 2769.292432] ath: Regpair used: 0x3a
[ 2769.292434] ath: regdomain 0x8348 dynamically updated by country IE
[ 2769.380768] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2769.380777] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2770.293084] wlan0: authenticate with <MAC address removed>
[ 2770.308984] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2770.310898] wlan0: authenticated
[ 2770.312062] wlan0: associate with <MAC address removed> (try 1/3)
[ 2770.315924] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2770.315978] wlan0: associated
[ 2770.319696] ath: EEPROM regdomain: 0x8348
[ 2770.319701] ath: EEPROM indicates we should expect a country code
[ 2770.319703] ath: doing EEPROM country->regdmn map search
[ 2770.319705] ath: country maps to regdmn code: 0x3a
[ 2770.319707] ath: Country alpha2 being used: US
[ 2770.319708] ath: Regpair used: 0x3a
[ 2770.319710] ath: regdomain 0x8348 dynamically updated by country IE
[ 2770.404778] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2770.404783] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2771.372941] wlan0: authenticate with <MAC address removed>
[ 2771.388779] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2771.390774] wlan0: authenticated
[ 2771.392103] wlan0: associate with <MAC address removed> (try 1/3)
[ 2771.395913] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2771.395963] wlan0: associated
[ 2771.402185] ath: EEPROM regdomain: 0x8348
[ 2771.402192] ath: EEPROM indicates we should expect a country code
[ 2771.402196] ath: doing EEPROM country->regdmn map search
[ 2771.402199] ath: country maps to regdmn code: 0x3a
[ 2771.402202] ath: Country alpha2 being used: US
[ 2771.402205] ath: Regpair used: 0x3a
[ 2771.402209] ath: regdomain 0x8348 dynamically updated by country IE
[ 2771.428801] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2771.428809] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2772.337069] wlan0: authenticate with <MAC address removed>
[ 2772.352966] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2772.354927] wlan0: authenticated
[ 2772.356120] wlan0: associate with <MAC address removed> (try 1/3)
[ 2772.359925] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2772.359975] wlan0: associated
[ 2772.364610] ath: EEPROM regdomain: 0x8348
[ 2772.364615] ath: EEPROM indicates we should expect a country code
[ 2772.364617] ath: doing EEPROM country->regdmn map search
[ 2772.364619] ath: country maps to regdmn code: 0x3a
[ 2772.364621] ath: Country alpha2 being used: US
[ 2772.364622] ath: Regpair used: 0x3a
[ 2772.364624] ath: regdomain 0x8348 dynamically updated by country IE
[ 2772.452821] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2772.452829] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2773.365234] wlan0: authenticate with <MAC address removed>
[ 2773.381143] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2773.383108] wlan0: authenticated
[ 2773.388105] wlan0: associate with <MAC address removed> (try 1/3)
[ 2773.391960] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2773.392058] wlan0: associated
[ 2773.397611] ath: EEPROM regdomain: 0x8348
[ 2773.397620] ath: EEPROM indicates we should expect a country code
[ 2773.397624] ath: doing EEPROM country->regdmn map search
[ 2773.397627] ath: country maps to regdmn code: 0x3a
[ 2773.397630] ath: Country alpha2 being used: US
[ 2773.397633] ath: Regpair used: 0x3a
[ 2773.397636] ath: regdomain 0x8348 dynamically updated by country IE
[ 2773.476810] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2773.476816] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2774.393077] wlan0: authenticate with <MAC address removed>
[ 2774.408951] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2774.411003] wlan0: authenticated
[ 2774.412114] wlan0: associate with <MAC address removed> (try 1/3)
[ 2774.416217] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2774.416277] wlan0: associated
[ 2774.420523] ath: EEPROM regdomain: 0x8348
[ 2774.420530] ath: EEPROM indicates we should expect a country code
[ 2774.420533] ath: doing EEPROM country->regdmn map search
[ 2774.420537] ath: country maps to regdmn code: 0x3a
[ 2774.420540] ath: Country alpha2 being used: US
[ 2774.420542] ath: Regpair used: 0x3a
[ 2774.420546] ath: regdomain 0x8348 dynamically updated by country IE
[ 2774.500838] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2774.500846] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2775.412904] wlan0: authenticate with <MAC address removed>
[ 2775.428737] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2775.430678] wlan0: authenticated
[ 2775.432059] wlan0: associate with <MAC address removed> (try 1/3)
[ 2775.435910] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2775.435964] wlan0: associated
[ 2775.440069] ath: EEPROM regdomain: 0x8348
[ 2775.440075] ath: EEPROM indicates we should expect a country code
[ 2775.440077] ath: doing EEPROM country->regdmn map search
[ 2775.440079] ath: country maps to regdmn code: 0x3a
[ 2775.440081] ath: Country alpha2 being used: US
[ 2775.440083] ath: Regpair used: 0x3a
[ 2775.440085] ath: regdomain 0x8348 dynamically updated by country IE
[ 2775.524982] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2775.524987] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2776.496852] wlan0: authenticate with <MAC address removed>
[ 2776.512704] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2776.514668] wlan0: authenticated
[ 2776.520051] wlan0: associate with <MAC address removed> (try 1/3)
[ 2776.523901] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2776.523954] wlan0: associated
[ 2776.530047] ath: EEPROM regdomain: 0x8348
[ 2776.530054] ath: EEPROM indicates we should expect a country code
[ 2776.530058] ath: doing EEPROM country->regdmn map search
[ 2776.530061] ath: country maps to regdmn code: 0x3a
[ 2776.530064] ath: Country alpha2 being used: US
[ 2776.530067] ath: Regpair used: 0x3a
[ 2776.530070] ath: regdomain 0x8348 dynamically updated by country IE
[ 2776.549135] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2776.549141] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2777.457061] wlan0: authenticate with <MAC address removed>
[ 2777.472959] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2777.475923] wlan0: authenticated
[ 2777.480113] wlan0: associate with <MAC address removed> (try 1/3)
[ 2777.484001] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2777.484112] wlan0: associated
[ 2777.490169] ath: EEPROM regdomain: 0x8348
[ 2777.490178] ath: EEPROM indicates we should expect a country code
[ 2777.490182] ath: doing EEPROM country->regdmn map search
[ 2777.490185] ath: country maps to regdmn code: 0x3a
[ 2777.490189] ath: Country alpha2 being used: US
[ 2777.490191] ath: Regpair used: 0x3a
[ 2777.490195] ath: regdomain 0x8348 dynamically updated by country IE
[ 2777.572828] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2777.572836] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2778.484913] wlan0: authenticate with <MAC address removed>
[ 2778.500634] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2778.502830] wlan0: authenticated
[ 2778.508095] wlan0: associate with <MAC address removed> (try 1/3)
[ 2778.511995] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2778.512073] wlan0: associated
[ 2778.517659] ath: EEPROM regdomain: 0x8348
[ 2778.517667] ath: EEPROM indicates we should expect a country code
[ 2778.517670] ath: doing EEPROM country->regdmn map search
[ 2778.517674] ath: country maps to regdmn code: 0x3a
[ 2778.517677] ath: Country alpha2 being used: US
[ 2778.517679] ath: Regpair used: 0x3a
[ 2778.517683] ath: regdomain 0x8348 dynamically updated by country IE
[ 2778.597324] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2778.597334] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2779.517081] wlan0: authenticate with <MAC address removed>
[ 2779.532961] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2779.534961] wlan0: authenticated
[ 2779.536099] wlan0: associate with <MAC address removed> (try 1/3)
[ 2779.539860] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2779.539911] wlan0: associated
[ 2779.545785] ath: EEPROM regdomain: 0x8348
[ 2779.545792] ath: EEPROM indicates we should expect a country code
[ 2779.545796] ath: doing EEPROM country->regdmn map search
[ 2779.545799] ath: country maps to regdmn code: 0x3a
[ 2779.545802] ath: Country alpha2 being used: US
[ 2779.545804] ath: Regpair used: 0x3a
[ 2779.545808] ath: regdomain 0x8348 dynamically updated by country IE
[ 2779.620823] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2779.620831] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2780.532868] wlan0: authenticate with <MAC address removed>
[ 2780.548614] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2780.550540] wlan0: authenticated
[ 2780.552081] wlan0: associate with <MAC address removed> (try 1/3)
[ 2780.555885] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2780.555940] wlan0: associated
[ 2780.560052] ath: EEPROM regdomain: 0x8348
[ 2780.560057] ath: EEPROM indicates we should expect a country code
[ 2780.560059] ath: doing EEPROM country->regdmn map search
[ 2780.560061] ath: country maps to regdmn code: 0x3a
[ 2780.560063] ath: Country alpha2 being used: US
[ 2780.560064] ath: Regpair used: 0x3a
[ 2780.560066] ath: regdomain 0x8348 dynamically updated by country IE
[ 2780.645329] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2780.645337] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2781.612858] wlan0: authenticate with <MAC address removed>
[ 2781.628659] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2781.630730] wlan0: authenticated
[ 2781.632117] wlan0: associate with <MAC address removed> (try 1/3)
[ 2781.635950] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2781.636000] wlan0: associated
[ 2781.640063] ath: EEPROM regdomain: 0x8348
[ 2781.640069] ath: EEPROM indicates we should expect a country code
[ 2781.640073] ath: doing EEPROM country->regdmn map search
[ 2781.640077] ath: country maps to regdmn code: 0x3a
[ 2781.640080] ath: Country alpha2 being used: US
[ 2781.640082] ath: Regpair used: 0x3a
[ 2781.640084] ath: regdomain 0x8348 dynamically updated by country IE
[ 2781.669096] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2781.669104] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2782.632846] wlan0: authenticate with <MAC address removed>
[ 2782.648564] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2782.651304] wlan0: authenticated
[ 2782.652116] wlan0: associate with <MAC address removed> (try 1/3)
[ 2782.655905] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 2782.655956] wlan0: associated
[ 2782.660683] ath: EEPROM regdomain: 0x8348
[ 2782.660688] ath: EEPROM indicates we should expect a country code
[ 2782.660690] ath: doing EEPROM country->regdmn map search
[ 2782.660692] ath: country maps to regdmn code: 0x3a
[ 2782.660693] ath: Country alpha2 being used: US
[ 2782.660695] ath: Regpair used: 0x3a
[ 2782.660697] ath: regdomain 0x8348 dynamically updated by country IE
[ 2782.692775] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2782.692783] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2783.600883] wlan0: authenticate with <MAC address removed>
[ 2783.616729] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2783.618494] wlan0: authenticated
[ 2783.620103] wlan0: associate with <MAC address removed> (try 1/3)
[ 2783.623944] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 2783.623998] wlan0: associated
[ 2783.630474] ath: EEPROM regdomain: 0x8348
[ 2783.630482] ath: EEPROM indicates we should expect a country code
[ 2783.630486] ath: doing EEPROM country->regdmn map search
[ 2783.630489] ath: country maps to regdmn code: 0x3a
[ 2783.630493] ath: Country alpha2 being used: US
[ 2783.630495] ath: Regpair used: 0x3a
[ 2783.630499] ath: regdomain 0x8348 dynamically updated by country IE
[ 2783.716779] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2783.716787] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2784.629072] wlan0: authenticate with <MAC address removed>
[ 2784.644983] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2784.646975] wlan0: authenticated
[ 2784.652082] wlan0: associate with <MAC address removed> (try 1/3)
[ 2784.655926] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2784.655978] wlan0: associated
[ 2784.662264] ath: EEPROM regdomain: 0x8348
[ 2784.662272] ath: EEPROM indicates we should expect a country code
[ 2784.662275] ath: doing EEPROM country->regdmn map search
[ 2784.662279] ath: country maps to regdmn code: 0x3a
[ 2784.662282] ath: Country alpha2 being used: US
[ 2784.662284] ath: Regpair used: 0x3a
[ 2784.662288] ath: regdomain 0x8348 dynamically updated by country IE
[ 2784.740783] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2784.740791] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2785.652913] wlan0: authenticate with <MAC address removed>
[ 2785.668763] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2785.670849] wlan0: authenticated
[ 2785.672071] wlan0: associate with <MAC address removed> (try 1/3)
[ 2785.675853] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2785.675902] wlan0: associated
[ 2785.681270] ath: EEPROM regdomain: 0x8348
[ 2785.681275] ath: EEPROM indicates we should expect a country code
[ 2785.681277] ath: doing EEPROM country->regdmn map search
[ 2785.681279] ath: country maps to regdmn code: 0x3a
[ 2785.681281] ath: Country alpha2 being used: US
[ 2785.681283] ath: Regpair used: 0x3a
[ 2785.681285] ath: regdomain 0x8348 dynamically updated by country IE
[ 2785.764768] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2785.764774] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2786.676852] wlan0: authenticate with <MAC address removed>
[ 2786.692638] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2786.694634] wlan0: authenticated
[ 2786.696112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2786.699929] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2786.699984] wlan0: associated
[ 2786.704589] ath: EEPROM regdomain: 0x8348
[ 2786.704594] ath: EEPROM indicates we should expect a country code
[ 2786.704596] ath: doing EEPROM country->regdmn map search
[ 2786.704598] ath: country maps to regdmn code: 0x3a
[ 2786.704600] ath: Country alpha2 being used: US
[ 2786.704601] ath: Regpair used: 0x3a
[ 2786.704603] ath: regdomain 0x8348 dynamically updated by country IE
[ 2786.788809] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2786.788817] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2787.697077] wlan0: authenticate with <MAC address removed>
[ 2787.712944] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2787.715015] wlan0: authenticated
[ 2787.716133] wlan0: associate with <MAC address removed> (try 1/3)
[ 2787.720017] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2787.720070] wlan0: associated
[ 2787.724960] ath: EEPROM regdomain: 0x8348
[ 2787.724965] ath: EEPROM indicates we should expect a country code
[ 2787.724967] ath: doing EEPROM country->regdmn map search
[ 2787.724969] ath: country maps to regdmn code: 0x3a
[ 2787.724970] ath: Country alpha2 being used: US
[ 2787.724972] ath: Regpair used: 0x3a
[ 2787.724974] ath: regdomain 0x8348 dynamically updated by country IE
[ 2787.813413] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2787.813419] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2788.781265] wlan0: authenticate with <MAC address removed>
[ 2788.797068] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2788.799009] wlan0: authenticated
[ 2788.804089] wlan0: associate with <MAC address removed> (try 1/3)
[ 2788.807940] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2788.807992] wlan0: associated
[ 2788.814425] ath: EEPROM regdomain: 0x8348
[ 2788.814432] ath: EEPROM indicates we should expect a country code
[ 2788.814436] ath: doing EEPROM country->regdmn map search
[ 2788.814439] ath: country maps to regdmn code: 0x3a
[ 2788.814442] ath: Country alpha2 being used: US
[ 2788.814445] ath: Regpair used: 0x3a
[ 2788.814448] ath: regdomain 0x8348 dynamically updated by country IE
[ 2788.836770] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2788.836778] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2789.744888] wlan0: authenticate with <MAC address removed>
[ 2789.760767] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2789.762849] wlan0: authenticated
[ 2789.764110] wlan0: associate with <MAC address removed> (try 1/3)
[ 2789.767969] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2789.768041] wlan0: associated
[ 2789.774589] ath: EEPROM regdomain: 0x8348
[ 2789.774596] ath: EEPROM indicates we should expect a country code
[ 2789.774600] ath: doing EEPROM country->regdmn map search
[ 2789.774603] ath: country maps to regdmn code: 0x3a
[ 2789.774606] ath: Country alpha2 being used: US
[ 2789.774609] ath: Regpair used: 0x3a
[ 2789.774612] ath: regdomain 0x8348 dynamically updated by country IE
[ 2789.860776] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2789.860784] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2790.772876] wlan0: authenticate with <MAC address removed>
[ 2790.788705] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2790.790670] wlan0: authenticated
[ 2790.792071] wlan0: associate with <MAC address removed> (try 1/3)
[ 2790.795807] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2790.795859] wlan0: associated
[ 2790.800682] ath: EEPROM regdomain: 0x8348
[ 2790.800689] ath: EEPROM indicates we should expect a country code
[ 2790.800693] ath: doing EEPROM country->regdmn map search
[ 2790.800696] ath: country maps to regdmn code: 0x3a
[ 2790.800699] ath: Country alpha2 being used: US
[ 2790.800702] ath: Regpair used: 0x3a
[ 2790.800705] ath: regdomain 0x8348 dynamically updated by country IE
[ 2790.885399] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2790.885404] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2791.796889] wlan0: authenticate with <MAC address removed>
[ 2791.812686] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2791.814639] wlan0: authenticated
[ 2791.816100] wlan0: associate with <MAC address removed> (try 1/3)
[ 2791.819925] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2791.819980] wlan0: associated
[ 2791.826481] ath: EEPROM regdomain: 0x8348
[ 2791.826490] ath: EEPROM indicates we should expect a country code
[ 2791.826493] ath: doing EEPROM country->regdmn map search
[ 2791.826497] ath: country maps to regdmn code: 0x3a
[ 2791.826500] ath: Country alpha2 being used: US
[ 2791.826502] ath: Regpair used: 0x3a
[ 2791.826506] ath: regdomain 0x8348 dynamically updated by country IE
[ 2791.908771] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2791.908776] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2792.824872] wlan0: authenticate with <MAC address removed>
[ 2792.840690] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2792.843290] wlan0: authenticated
[ 2792.844102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2792.848176] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2792.848229] wlan0: associated
[ 2792.852744] ath: EEPROM regdomain: 0x8348
[ 2792.852751] ath: EEPROM indicates we should expect a country code
[ 2792.852754] ath: doing EEPROM country->regdmn map search
[ 2792.852758] ath: country maps to regdmn code: 0x3a
[ 2792.852761] ath: Country alpha2 being used: US
[ 2792.852763] ath: Regpair used: 0x3a
[ 2792.852767] ath: regdomain 0x8348 dynamically updated by country IE
[ 2792.932980] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2792.932988] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2793.845084] wlan0: authenticate with <MAC address removed>
[ 2793.860992] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2793.863018] wlan0: authenticated
[ 2793.864103] wlan0: associate with <MAC address removed> (try 1/3)
[ 2793.867952] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2793.868017] wlan0: associated
[ 2793.872104] ath: EEPROM regdomain: 0x8348
[ 2793.872110] ath: EEPROM indicates we should expect a country code
[ 2793.872112] ath: doing EEPROM country->regdmn map search
[ 2793.872114] ath: country maps to regdmn code: 0x3a
[ 2793.872115] ath: Country alpha2 being used: US
[ 2793.872117] ath: Regpair used: 0x3a
[ 2793.872119] ath: regdomain 0x8348 dynamically updated by country IE
[ 2793.956815] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2793.956823] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2794.869014] wlan0: authenticate with <MAC address removed>
[ 2794.885005] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2794.886970] wlan0: authenticated
[ 2794.888112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2794.894273] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2794.894342] wlan0: associated
[ 2794.899974] ath: EEPROM regdomain: 0x8348
[ 2794.899983] ath: EEPROM indicates we should expect a country code
[ 2794.899987] ath: doing EEPROM country->regdmn map search
[ 2794.899990] ath: country maps to regdmn code: 0x3a
[ 2794.899993] ath: Country alpha2 being used: US
[ 2794.899996] ath: Regpair used: 0x3a
[ 2794.899999] ath: regdomain 0x8348 dynamically updated by country IE
[ 2794.980750] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2794.980756] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2795.896888] wlan0: authenticate with <MAC address removed>
[ 2795.912639] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2795.914641] wlan0: authenticated
[ 2795.916110] wlan0: associate with <MAC address removed> (try 1/3)
[ 2795.920022] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2795.920083] wlan0: associated
[ 2795.924741] ath: EEPROM regdomain: 0x8348
[ 2795.924748] ath: EEPROM indicates we should expect a country code
[ 2795.924751] ath: doing EEPROM country->regdmn map search
[ 2795.924755] ath: country maps to regdmn code: 0x3a
[ 2795.924758] ath: Country alpha2 being used: US
[ 2795.924760] ath: Regpair used: 0x3a
[ 2795.924764] ath: regdomain 0x8348 dynamically updated by country IE
[ 2796.004768] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2796.004776] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2796.916863] wlan0: authenticate with <MAC address removed>
[ 2796.932697] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2796.935013] wlan0: authenticated
[ 2796.936122] wlan0: associate with <MAC address removed> (try 1/3)
[ 2796.940172] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2796.940237] wlan0: associated
[ 2796.947326] ath: EEPROM regdomain: 0x8348
[ 2796.947333] ath: EEPROM indicates we should expect a country code
[ 2796.947337] ath: doing EEPROM country->regdmn map search
[ 2796.947340] ath: country maps to regdmn code: 0x3a
[ 2796.947344] ath: Country alpha2 being used: US
[ 2796.947346] ath: Regpair used: 0x3a
[ 2796.947350] ath: regdomain 0x8348 dynamically updated by country IE
[ 2797.028777] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2797.028785] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2797.944910] wlan0: authenticate with <MAC address removed>
[ 2797.960668] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2797.962667] wlan0: authenticated
[ 2797.964121] wlan0: associate with <MAC address removed> (try 1/3)
[ 2797.968034] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2797.968100] wlan0: associated
[ 2797.973634] ath: EEPROM regdomain: 0x8348
[ 2797.973642] ath: EEPROM indicates we should expect a country code
[ 2797.973644] ath: doing EEPROM country->regdmn map search
[ 2797.973647] ath: country maps to regdmn code: 0x3a
[ 2797.973649] ath: Country alpha2 being used: US
[ 2797.973651] ath: Regpair used: 0x3a
[ 2797.973654] ath: regdomain 0x8348 dynamically updated by country IE
[ 2798.052771] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2798.052777] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2798.973174] wlan0: authenticate with <MAC address removed>
[ 2798.989090] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2798.991135] wlan0: authenticated
[ 2798.992158] wlan0: associate with <MAC address removed> (try 1/3)
[ 2798.998701] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2798.998772] wlan0: associated
[ 2799.005262] ath: EEPROM regdomain: 0x8348
[ 2799.005270] ath: EEPROM indicates we should expect a country code
[ 2799.005274] ath: doing EEPROM country->regdmn map search
[ 2799.005277] ath: country maps to regdmn code: 0x3a
[ 2799.005280] ath: Country alpha2 being used: US
[ 2799.005283] ath: Regpair used: 0x3a
[ 2799.005286] ath: regdomain 0x8348 dynamically updated by country IE
[ 2799.076804] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2799.076812] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2799.985495] wlan0: authenticate with <MAC address removed>
[ 2800.001267] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2800.003258] wlan0: authenticated
[ 2800.008090] wlan0: associate with <MAC address removed> (try 1/3)
[ 2800.011872] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2800.011927] wlan0: associated
[ 2800.016255] ath: EEPROM regdomain: 0x8348
[ 2800.016261] ath: EEPROM indicates we should expect a country code
[ 2800.016265] ath: doing EEPROM country->regdmn map search
[ 2800.016268] ath: country maps to regdmn code: 0x3a
[ 2800.016271] ath: Country alpha2 being used: US
[ 2800.016274] ath: Regpair used: 0x3a
[ 2800.016277] ath: regdomain 0x8348 dynamically updated by country IE
[ 2800.100807] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2800.100814] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2801.020889] wlan0: authenticate with <MAC address removed>
[ 2801.036749] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2801.038772] wlan0: authenticated
[ 2801.040067] wlan0: associate with <MAC address removed> (try 1/3)
[ 2801.043889] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2801.043936] wlan0: associated
[ 2801.048135] ath: EEPROM regdomain: 0x8348
[ 2801.048141] ath: EEPROM indicates we should expect a country code
[ 2801.048145] ath: doing EEPROM country->regdmn map search
[ 2801.048148] ath: country maps to regdmn code: 0x3a
[ 2801.048151] ath: Country alpha2 being used: US
[ 2801.048154] ath: Regpair used: 0x3a
[ 2801.048158] ath: regdomain 0x8348 dynamically updated by country IE
[ 2801.124736] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2801.124740] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2802.041052] wlan0: authenticate with <MAC address removed>
[ 2802.056949] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2802.058960] wlan0: authenticated
[ 2802.060111] wlan0: associate with <MAC address removed> (try 1/3)
[ 2802.063910] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2802.063959] wlan0: associated
[ 2802.068924] ath: EEPROM regdomain: 0x8348
[ 2802.068931] ath: EEPROM indicates we should expect a country code
[ 2802.068935] ath: doing EEPROM country->regdmn map search
[ 2802.068938] ath: country maps to regdmn code: 0x3a
[ 2802.068942] ath: Country alpha2 being used: US
[ 2802.068944] ath: Regpair used: 0x3a
[ 2802.068948] ath: regdomain 0x8348 dynamically updated by country IE
[ 2802.148767] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2802.148775] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2803.108851] wlan0: authenticate with <MAC address removed>
[ 2803.124606] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2803.126612] wlan0: authenticated
[ 2803.128105] wlan0: associate with <MAC address removed> (try 1/3)
[ 2803.133231] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2803.133285] wlan0: associated
[ 2803.138038] ath: EEPROM regdomain: 0x8348
[ 2803.138045] ath: EEPROM indicates we should expect a country code
[ 2803.138049] ath: doing EEPROM country->regdmn map search
[ 2803.138052] ath: country maps to regdmn code: 0x3a
[ 2803.138055] ath: Country alpha2 being used: US
[ 2803.138058] ath: Regpair used: 0x3a
[ 2803.138061] ath: regdomain 0x8348 dynamically updated by country IE
[ 2803.172769] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2803.172776] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2804.081148] wlan0: authenticate with <MAC address removed>
[ 2804.097050] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2804.099004] wlan0: authenticated
[ 2804.100116] wlan0: associate with <MAC address removed> (try 1/3)
[ 2804.103974] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2804.104041] wlan0: associated
[ 2804.108383] ath: EEPROM regdomain: 0x8348
[ 2804.108390] ath: EEPROM indicates we should expect a country code
[ 2804.108394] ath: doing EEPROM country->regdmn map search
[ 2804.108397] ath: country maps to regdmn code: 0x3a
[ 2804.108400] ath: Country alpha2 being used: US
[ 2804.108402] ath: Regpair used: 0x3a
[ 2804.108406] ath: regdomain 0x8348 dynamically updated by country IE
[ 2804.196779] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2804.196786] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2805.117480] wlan0: authenticate with <MAC address removed>
[ 2805.133421] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2805.135436] wlan0: authenticated
[ 2805.136100] wlan0: associate with <MAC address removed> (try 1/3)
[ 2805.139891] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2805.139941] wlan0: associated
[ 2805.146649] ath: EEPROM regdomain: 0x8348
[ 2805.146656] ath: EEPROM indicates we should expect a country code
[ 2805.146660] ath: doing EEPROM country->regdmn map search
[ 2805.146663] ath: country maps to regdmn code: 0x3a
[ 2805.146667] ath: Country alpha2 being used: US
[ 2805.146670] ath: Regpair used: 0x3a
[ 2805.146673] ath: regdomain 0x8348 dynamically updated by country IE
[ 2805.220788] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2805.220797] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2806.136892] wlan0: authenticate with <MAC address removed>
[ 2806.152755] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2806.154699] wlan0: authenticated
[ 2806.156079] wlan0: associate with <MAC address removed> (try 1/3)
[ 2806.159817] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2806.159869] wlan0: associated
[ 2806.165301] ath: EEPROM regdomain: 0x8348
[ 2806.165306] ath: EEPROM indicates we should expect a country code
[ 2806.165308] ath: doing EEPROM country->regdmn map search
[ 2806.165310] ath: country maps to regdmn code: 0x3a
[ 2806.165312] ath: Country alpha2 being used: US
[ 2806.165313] ath: Regpair used: 0x3a
[ 2806.165315] ath: regdomain 0x8348 dynamically updated by country IE
[ 2806.244774] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2806.244779] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2807.220883] wlan0: authenticate with <MAC address removed>
[ 2807.236653] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2807.239531] wlan0: authenticated
[ 2807.244098] wlan0: associate with <MAC address removed> (try 1/3)
[ 2807.248158] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2807.248241] wlan0: associated
[ 2807.254480] ath: EEPROM regdomain: 0x8348
[ 2807.254488] ath: EEPROM indicates we should expect a country code
[ 2807.254491] ath: doing EEPROM country->regdmn map search
[ 2807.254495] ath: country maps to regdmn code: 0x3a
[ 2807.254498] ath: Country alpha2 being used: US
[ 2807.254501] ath: Regpair used: 0x3a
[ 2807.254504] ath: regdomain 0x8348 dynamically updated by country IE
[ 2807.268961] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2807.268969] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2808.173064] wlan0: authenticate with <MAC address removed>
[ 2808.188956] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2808.192407] wlan0: authenticated
[ 2808.196090] wlan0: associate with <MAC address removed> (try 1/3)
[ 2808.199966] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2808.200045] wlan0: associated
[ 2808.205772] ath: EEPROM regdomain: 0x8348
[ 2808.205779] ath: EEPROM indicates we should expect a country code
[ 2808.205783] ath: doing EEPROM country->regdmn map search
[ 2808.205786] ath: country maps to regdmn code: 0x3a
[ 2808.205789] ath: Country alpha2 being used: US
[ 2808.205792] ath: Regpair used: 0x3a
[ 2808.205795] ath: regdomain 0x8348 dynamically updated by country IE
[ 2808.292729] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2808.292735] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2809.205065] wlan0: authenticate with <MAC address removed>
[ 2809.220922] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2809.222965] wlan0: authenticated
[ 2809.224102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2809.227905] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2809.227965] wlan0: associated
[ 2809.233699] ath: EEPROM regdomain: 0x8348
[ 2809.233706] ath: EEPROM indicates we should expect a country code
[ 2809.233710] ath: doing EEPROM country->regdmn map search
[ 2809.233714] ath: country maps to regdmn code: 0x3a
[ 2809.233717] ath: Country alpha2 being used: US
[ 2809.233719] ath: Regpair used: 0x3a
[ 2809.233723] ath: regdomain 0x8348 dynamically updated by country IE
[ 2809.316760] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2809.316768] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2810.225168] wlan0: authenticate with <MAC address removed>
[ 2810.240967] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2810.243211] wlan0: authenticated
[ 2810.244113] wlan0: associate with <MAC address removed> (try 1/3)
[ 2810.249401] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2810.249457] wlan0: associated
[ 2810.255634] ath: EEPROM regdomain: 0x8348
[ 2810.255641] ath: EEPROM indicates we should expect a country code
[ 2810.255645] ath: doing EEPROM country->regdmn map search
[ 2810.255648] ath: country maps to regdmn code: 0x3a
[ 2810.255652] ath: Country alpha2 being used: US
[ 2810.255654] ath: Regpair used: 0x3a
[ 2810.255658] ath: regdomain 0x8348 dynamically updated by country IE
[ 2810.340757] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2810.340766] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2811.301223] wlan0: authenticate with <MAC address removed>
[ 2811.317178] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2811.319093] wlan0: authenticated
[ 2811.320076] wlan0: associate with <MAC address removed> (try 1/3)
[ 2811.325295] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2811.325349] wlan0: associated
[ 2811.329445] ath: EEPROM regdomain: 0x8348
[ 2811.329450] ath: EEPROM indicates we should expect a country code
[ 2811.329452] ath: doing EEPROM country->regdmn map search
[ 2811.329454] ath: country maps to regdmn code: 0x3a
[ 2811.329456] ath: Country alpha2 being used: US
[ 2811.329457] ath: Regpair used: 0x3a
[ 2811.329459] ath: regdomain 0x8348 dynamically updated by country IE
[ 2811.364760] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2811.364766] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2812.269014] wlan0: authenticate with <MAC address removed>
[ 2812.284831] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2812.288450] wlan0: authenticated
[ 2812.292114] wlan0: associate with <MAC address removed> (try 1/3)
[ 2812.295969] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2812.296066] wlan0: associated
[ 2812.302117] ath: EEPROM regdomain: 0x8348
[ 2812.302126] ath: EEPROM indicates we should expect a country code
[ 2812.302129] ath: doing EEPROM country->regdmn map search
[ 2812.302133] ath: country maps to regdmn code: 0x3a
[ 2812.302136] ath: Country alpha2 being used: US
[ 2812.302138] ath: Regpair used: 0x3a
[ 2812.302142] ath: regdomain 0x8348 dynamically updated by country IE
[ 2812.388770] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2812.388777] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2813.301119] wlan0: authenticate with <MAC address removed>
[ 2813.316984] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2813.318973] wlan0: authenticated
[ 2813.320105] wlan0: associate with <MAC address removed> (try 1/3)
[ 2813.324882] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2813.324953] wlan0: associated
[ 2813.331092] ath: EEPROM regdomain: 0x8348
[ 2813.331099] ath: EEPROM indicates we should expect a country code
[ 2813.331103] ath: doing EEPROM country->regdmn map search
[ 2813.331106] ath: country maps to regdmn code: 0x3a
[ 2813.331109] ath: Country alpha2 being used: US
[ 2813.331112] ath: Regpair used: 0x3a
[ 2813.331115] ath: regdomain 0x8348 dynamically updated by country IE
[ 2813.413150] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2813.413158] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2814.372949] wlan0: authenticate with <MAC address removed>
[ 2814.388699] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2814.390851] wlan0: authenticated
[ 2814.392100] wlan0: associate with <MAC address removed> (try 1/3)
[ 2814.397164] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2814.397231] wlan0: associated
[ 2814.402574] ath: EEPROM regdomain: 0x8348
[ 2814.402580] ath: EEPROM indicates we should expect a country code
[ 2814.402583] ath: doing EEPROM country->regdmn map search
[ 2814.402585] ath: country maps to regdmn code: 0x3a
[ 2814.402588] ath: Country alpha2 being used: US
[ 2814.402590] ath: Regpair used: 0x3a
[ 2814.402592] ath: regdomain 0x8348 dynamically updated by country IE
[ 2814.436739] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2814.436747] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2815.340919] wlan0: authenticate with <MAC address removed>
[ 2815.356829] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2815.361269] wlan0: authenticated
[ 2815.364096] wlan0: associate with <MAC address removed> (try 1/3)
[ 2815.367741] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2815.367812] wlan0: associated
[ 2815.373926] ath: EEPROM regdomain: 0x8348
[ 2815.373933] ath: EEPROM indicates we should expect a country code
[ 2815.373936] ath: doing EEPROM country->regdmn map search
[ 2815.373939] ath: country maps to regdmn code: 0x3a
[ 2815.373943] ath: Country alpha2 being used: US
[ 2815.373945] ath: Regpair used: 0x3a
[ 2815.373949] ath: regdomain 0x8348 dynamically updated by country IE
[ 2815.465570] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2815.465576] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2816.429202] wlan0: authenticate with <MAC address removed>
[ 2816.445064] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2816.447017] wlan0: authenticated
[ 2816.452050] wlan0: associate with <MAC address removed> (try 1/3)
[ 2816.455855] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2816.455907] wlan0: associated
[ 2816.460349] ath: EEPROM regdomain: 0x8348
[ 2816.460354] ath: EEPROM indicates we should expect a country code
[ 2816.460356] ath: doing EEPROM country->regdmn map search
[ 2816.460358] ath: country maps to regdmn code: 0x3a
[ 2816.460360] ath: Country alpha2 being used: US
[ 2816.460361] ath: Regpair used: 0x3a
[ 2816.460363] ath: regdomain 0x8348 dynamically updated by country IE
[ 2816.485389] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2816.485397] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2817.445190] wlan0: authenticate with <MAC address removed>
[ 2817.460957] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2817.464074] wlan0: authenticated
[ 2817.468100] wlan0: associate with <MAC address removed> (try 1/3)
[ 2817.471887] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2817.471940] wlan0: associated
[ 2817.475945] ath: EEPROM regdomain: 0x8348
[ 2817.475950] ath: EEPROM indicates we should expect a country code
[ 2817.475952] ath: doing EEPROM country->regdmn map search
[ 2817.475954] ath: country maps to regdmn code: 0x3a
[ 2817.475956] ath: Country alpha2 being used: US
[ 2817.475957] ath: Regpair used: 0x3a
[ 2817.475959] ath: regdomain 0x8348 dynamically updated by country IE
[ 2817.508819] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2817.508827] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2818.413262] wlan0: authenticate with <MAC address removed>
[ 2818.429130] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2818.432668] wlan0: authenticated
[ 2818.436129] wlan0: associate with <MAC address removed> (try 1/3)
[ 2818.440086] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2818.440158] wlan0: associated
[ 2818.446341] ath: EEPROM regdomain: 0x8348
[ 2818.446348] ath: EEPROM indicates we should expect a country code
[ 2818.446352] ath: doing EEPROM country->regdmn map search
[ 2818.446355] ath: country maps to regdmn code: 0x3a
[ 2818.446358] ath: Country alpha2 being used: US
[ 2818.446361] ath: Regpair used: 0x3a
[ 2818.446364] ath: regdomain 0x8348 dynamically updated by country IE
[ 2818.532773] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2818.532781] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2819.445118] wlan0: authenticate with <MAC address removed>
[ 2819.461007] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2819.463069] wlan0: authenticated
[ 2819.464106] wlan0: associate with <MAC address removed> (try 1/3)
[ 2819.468001] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2819.468074] wlan0: associated
[ 2819.472144] ath: EEPROM regdomain: 0x8348
[ 2819.472150] ath: EEPROM indicates we should expect a country code
[ 2819.472152] ath: doing EEPROM country->regdmn map search
[ 2819.472154] ath: country maps to regdmn code: 0x3a
[ 2819.472156] ath: Country alpha2 being used: US
[ 2819.472157] ath: Regpair used: 0x3a
[ 2819.472160] ath: regdomain 0x8348 dynamically updated by country IE
[ 2819.556756] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2819.556765] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2820.476959] wlan0: authenticate with <MAC address removed>
[ 2820.492799] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2820.494823] wlan0: authenticated
[ 2820.500112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2820.503999] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2820.504104] wlan0: associated
[ 2820.509852] ath: EEPROM regdomain: 0x8348
[ 2820.509860] ath: EEPROM indicates we should expect a country code
[ 2820.509864] ath: doing EEPROM country->regdmn map search
[ 2820.509867] ath: country maps to regdmn code: 0x3a
[ 2820.509871] ath: Country alpha2 being used: US
[ 2820.509873] ath: Regpair used: 0x3a
[ 2820.509877] ath: regdomain 0x8348 dynamically updated by country IE
[ 2820.580724] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2820.580730] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2821.540876] wlan0: authenticate with <MAC address removed>
[ 2821.556639] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2821.558596] wlan0: authenticated
[ 2821.560066] wlan0: associate with <MAC address removed> (try 1/3)
[ 2821.564809] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2821.564862] wlan0: associated
[ 2821.569574] ath: EEPROM regdomain: 0x8348
[ 2821.569579] ath: EEPROM indicates we should expect a country code
[ 2821.569581] ath: doing EEPROM country->regdmn map search
[ 2821.569583] ath: country maps to regdmn code: 0x3a
[ 2821.569585] ath: Country alpha2 being used: US
[ 2821.569586] ath: Regpair used: 0x3a
[ 2821.569589] ath: regdomain 0x8348 dynamically updated by country IE
[ 2821.604725] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2821.604731] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2822.509110] wlan0: authenticate with <MAC address removed>
[ 2822.525011] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2822.528945] wlan0: authenticated
[ 2822.532102] wlan0: associate with <MAC address removed> (try 1/3)
[ 2822.535658] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2822.535712] wlan0: associated
[ 2822.539787] ath: EEPROM regdomain: 0x8348
[ 2822.539792] ath: EEPROM indicates we should expect a country code
[ 2822.539795] ath: doing EEPROM country->regdmn map search
[ 2822.539796] ath: country maps to regdmn code: 0x3a
[ 2822.539798] ath: Country alpha2 being used: US
[ 2822.539800] ath: Regpair used: 0x3a
[ 2822.539802] ath: regdomain 0x8348 dynamically updated by country IE
[ 2822.628748] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2822.628756] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2823.589150] wlan0: authenticate with <MAC address removed>
[ 2823.604930] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2823.606884] wlan0: authenticated
[ 2823.608112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2823.612743] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[ 2823.612809] wlan0: associated
[ 2823.617081] ath: EEPROM regdomain: 0x8348
[ 2823.617086] ath: EEPROM indicates we should expect a country code
[ 2823.617088] ath: doing EEPROM country->regdmn map search
[ 2823.617090] ath: country maps to regdmn code: 0x3a
[ 2823.617091] ath: Country alpha2 being used: US
[ 2823.617093] ath: Regpair used: 0x3a
[ 2823.617095] ath: regdomain 0x8348 dynamically updated by country IE
[ 2823.652759] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2823.652766] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2824.556907] wlan0: authenticate with <MAC address removed>
[ 2824.572789] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2824.576838] wlan0: authenticated
[ 2824.580111] wlan0: associate with <MAC address removed> (try 1/3)
[ 2824.584050] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2824.584126] wlan0: associated
[ 2824.589816] ath: EEPROM regdomain: 0x8348
[ 2824.589824] ath: EEPROM indicates we should expect a country code
[ 2824.589827] ath: doing EEPROM country->regdmn map search
[ 2824.589831] ath: country maps to regdmn code: 0x3a
[ 2824.589834] ath: Country alpha2 being used: US
[ 2824.589836] ath: Regpair used: 0x3a
[ 2824.589840] ath: regdomain 0x8348 dynamically updated by country IE
[ 2824.676759] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2824.676766] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2825.585516] wlan0: authenticate with <MAC address removed>
[ 2825.601331] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2825.632051] wlan0: authenticated
[ 2825.636138] wlan0: associate with <MAC address removed> (try 1/3)
[ 2825.640177] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2825.640251] wlan0: associated
[ 2825.647167] ath: EEPROM regdomain: 0x8348
[ 2825.647176] ath: EEPROM indicates we should expect a country code
[ 2825.647180] ath: doing EEPROM country->regdmn map search
[ 2825.647183] ath: country maps to regdmn code: 0x3a
[ 2825.647186] ath: Country alpha2 being used: US
[ 2825.647189] ath: Regpair used: 0x3a
[ 2825.647192] ath: regdomain 0x8348 dynamically updated by country IE
[ 2825.700786] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2825.700794] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2826.660877] wlan0: authenticate with <MAC address removed>
[ 2826.676687] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2826.678695] wlan0: authenticated
[ 2826.680100] wlan0: associate with <MAC address removed> (try 1/3)
[ 2826.685150] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2826.685209] wlan0: associated
[ 2826.690075] ath: EEPROM regdomain: 0x8348
[ 2826.690080] ath: EEPROM indicates we should expect a country code
[ 2826.690083] ath: doing EEPROM country->regdmn map search
[ 2826.690086] ath: country maps to regdmn code: 0x3a
[ 2826.690088] ath: Country alpha2 being used: US
[ 2826.690090] ath: Regpair used: 0x3a
[ 2826.690093] ath: regdomain 0x8348 dynamically updated by country IE
[ 2826.728532] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2826.728540] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2827.632890] wlan0: authenticate with <MAC address removed>
[ 2827.648729] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2827.651625] wlan0: authenticated
[ 2827.652109] wlan0: associate with <MAC address removed> (try 1/3)
[ 2827.655984] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2827.656052] wlan0: associated
[ 2827.660855] ath: EEPROM regdomain: 0x8348
[ 2827.660859] ath: EEPROM indicates we should expect a country code
[ 2827.660861] ath: doing EEPROM country->regdmn map search
[ 2827.660863] ath: country maps to regdmn code: 0x3a
[ 2827.660865] ath: Country alpha2 being used: US
[ 2827.660866] ath: Regpair used: 0x3a
[ 2827.660868] ath: regdomain 0x8348 dynamically updated by country IE
[ 2827.749556] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2827.749564] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2828.657073] wlan0: authenticate with <MAC address removed>
[ 2828.672972] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2828.776103] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2828.833471] wlan0: authenticated
[ 2828.836125] wlan0: associate with <MAC address removed> (try 1/3)
[ 2828.841189] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2828.841259] wlan0: associated
[ 2828.847244] ath: EEPROM regdomain: 0x8348
[ 2828.847251] ath: EEPROM indicates we should expect a country code
[ 2828.847255] ath: doing EEPROM country->regdmn map search
[ 2828.847259] ath: country maps to regdmn code: 0x3a
[ 2828.847262] ath: Country alpha2 being used: US
[ 2828.847264] ath: Regpair used: 0x3a
[ 2828.847268] ath: regdomain 0x8348 dynamically updated by country IE
[ 2828.875131] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2828.875140] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2829.833029] wlan0: authenticate with <MAC address removed>
[ 2829.848807] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2829.850803] wlan0: authenticated
[ 2829.852098] wlan0: associate with <MAC address removed> (try 1/3)
[ 2829.857439] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2829.857492] wlan0: associated
[ 2829.862365] ath: EEPROM regdomain: 0x8348
[ 2829.862372] ath: EEPROM indicates we should expect a country code
[ 2829.862376] ath: doing EEPROM country->regdmn map search
[ 2829.862379] ath: country maps to regdmn code: 0x3a
[ 2829.862382] ath: Country alpha2 being used: US
[ 2829.862385] ath: Regpair used: 0x3a
[ 2829.862389] ath: regdomain 0x8348 dynamically updated by country IE
[ 2829.899154] wlan0: AP <MAC address removed> changed bandwidth, new config is 2472 MHz, width 1 (2472/0 MHz)
[ 2829.899163] wlan0: AP <MAC address removed> changed bandwidth in a way we can't support - disconnect
[ 2830.804904] wlan0: authenticate with <MAC address removed>
[ 2830.820701] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2830.924111] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2831.015861] wlan0: authenticated
[ 2831.020092] wlan0: associate with <MAC address removed> (try 1/3)
[ 2831.023945] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 2831.024039] wlan0: associated
[ 2831.030272] ath: EEPROM regdomain: 0x8348
[ 2831.030279] ath: EEPROM indicates we should expect a country code
[ 2831.030283] ath: doing EEPROM country->regdmn map search
[ 2831.030286] ath: country maps to regdmn code: 0x3a
[ 2831.030289] ath: Country alpha2 being used: US
[ 2831.030291] ath: Regpair used: 0x3a
[ 2831.030295] ath: regdomain 0x8348 dynamically updated by country IE

****************** done ******************


```

---

### Post by varunendra on 2013-12-18
mantecas21, so is there a problem again? The huge dmesg part suggests there is.

Have you changed your location (country)? Default regulatory settings are for US in your setup, but it looks like the regdomain settings of Ireland are being forced which the adapter is unable to deal with.

---

