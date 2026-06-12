---
title: "Wifi connection too slow"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by vitaoma on 2013-10-05
Hello,

I've recently installed Ubuntu, but it was running too slow on my computer and I installed the lubuntu-core package through the Synaptic Manager. So now I'm using Lubuntu (sorry but I am a complete newbie and don't know how to check its version).

Anyway, my wifi connection speed is much slower now than it was on Windows. On Windows it was around 10 Mbps, now it is 1 Mbps -- I've noticed because of slow download and then tried an internet connection speed test that confirmed this. I can still connect to my default connection, but it is slower.

I've checked around the forums and internet for a solution, but as the repliers always ask for technical information, I think it varies from system to system, so here I am to ask you what sould be done.

Thank you very much.

---

### Post by vitaoma on 2013-10-05
up

---

### Post by vitaoma on 2013-10-06
Up! Please people, I'm really enjoying Lubuntu, the only issue is the slow connection...

---

### Post by varunendra on 2013-10-06
Welcome to the forums vitaoma ! :)

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lspci -nnk | grep -iA2 net
ifconfig
iwconfig
nm-tool
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

**PS:**
Please avoid bumping multiple times within 24 hrs unless you have something to add to the information you have already provided.

---

### Post by vitaoma on 2013-10-06
Thank you very much, varunendra. Sorry for bumping and sorry for my inexperience.

The outputs were:[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
vitaoma@victor:~$ lspci -nnk | grep -iA2 net
04:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8225]
    Kernel driver in use: rtl8180
--
04:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167]
    Kernel driver in use: r8169
    Kernel modules: r8169

```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
vitaoma@victor:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:1a:92:93:6d:82  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:7127 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:7127 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:1198005 (1.1 MB) TX bytes:1198005 (1.1 MB)


wlan0     Link encap:Ethernet  Endereço de HW 08:10:74:2f:d4:c9  
          inet end.: 192.168.1.102  Bcast:192.168.1.255  Masc:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:201452 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:169913 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:195182888 (195.1 MB) TX bytes:28235065 (28.2 MB)

```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
vitaoma@victor:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:10:74:5F:3F:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/100  Signal level=49/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:986  Invalid misc:1505   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:93:6D:82


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [default] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             connected
  Default:           yes
  HW Address:        08:10:74:2F:D4:C9


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Rocha:           Infra, 00:1A:3F:91:B6:0A, Freq 2462 MHz, Rate 54 Mb/s, Strength 16 WPA WPA2
    *default:        Infra, 08:10:74:5F:3F:22, Freq 2437 MHz, Rate 54 Mb/s, Strength 67
    Multilaser_WS01: Infra, C8:3A:35:03:48:68, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Familia Souza:   Infra, 00:24:01:94:70:78, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2


  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             201.6.2.24
    DNS:             201.6.2.144

```[COLOR=#000000][FONT=Ubuntu Mono]

Now I see there is some information in Portuguese in the output. In case it is necessary, please comment so I can try to translate it into English, or change the system language (I don't know how to do this yet).[/FONT][/COLOR]

---

### Post by varunendra on 2013-10-06
Everything seems normal in the outputs, except signal strength -
```
vitaoma@victor:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:10:74:5F:3F:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=**[COLOR="#FF0000"]49[/COLOR]/100**  Signal level=49/100 
```
Do you get similar signal strength in Widows too? If so, it *maybe* a driver fault.

To see if we can try something with the native driver, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

**PS:**
It's okay with the bump. Just thought you should know before a mod has to post the same thing. Since it is a busy forum, older posts quickly go off the search results. So bumping multiple times within 24 hours becomes somewhat unfair to those other threads that deserve and could otherwise get equal attention and help. :)

---

### Post by vitaoma on 2013-10-06
Yeah, the signal strength is unusually low, I would normally have around 80-100 % on Windows.

Following your instructions, the content of wireless-info.txt is:

```



*************** info trace ***************


***** uname -a *****


Linux victor 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:10:28 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal


***** lspci *****


04:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8225]
	Kernel driver in use: rtl8180
--
04:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167]
	Kernel driver in use: r8169
	Kernel modules: r8169


***** lsusb *****


Bus 001 Device 004: ID 1c4f:3002 SiGma Micro 
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 003 Device 002: ID 04ca:0022 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=52/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:991  Invalid misc:1547   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8180                35545  0 
mac80211              461261  1 rtl8180
eeprom_93cx6           13169  1 rtl8180
cfg80211              175574  2 rtl8180,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [default] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
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
    Rocha:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 16 WPA WPA2
    *default:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 73
    Multilaser_WS01: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Familia Souza:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2


  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             201.6.2.24
    DNS:             201.6.2.144






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


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=75/100  Signal level=75/100  
                    Encryption key:off
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a18ba36177
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/100  Signal level=15/100  
                    Encryption key:on
                    ESSID:"Rocha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b6e7389cc
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 0005526F636861
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1
search private


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


filename:       /lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     A7C4D1801D827D6037261EB
alias:          pci:v00001186d00003300sv*sd*bc*sc*i*
alias:          pci:v00001799d00006020sv*sd*bc*sc*i*
alias:          pci:v00001799d00006001sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008180sv*sd*bc*sc*i*
alias:          pci:v00001799d0000701Fsv*sd*bc*sc*i*
alias:          pci:v00001799d0000700Fsv*sd*bc*sc*i*
alias:          pci:v000010ECd00008185sv*sd*bc*sc*i*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.5.0-37-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:13.1/0000:04:07.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:13.1/0000:04:03.0 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****




****************** done ******************

```

---

### Post by varunendra on 2013-10-06
There seems to be only one thing you can try here - changing the channel from "6" to "1" or "11" in your access-point. If that does not help, we may try either the proprietary driver, or a backported one first.

---

### Post by vitaoma on 2013-10-06
Woah! Changed to channel 11 and it's ~10 times faster now! Thank you very much varunendra!

---

### Post by varunendra on 2013-10-06
You're welcome !

Didn't know myself it can make so much difference !! :D

---

