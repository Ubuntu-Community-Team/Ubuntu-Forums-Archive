---
title: "Ralink RT5390"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by bryce2 on 2013-09-11
So, I am brand new to Ubuntu, and have just installed Ubuntu 13.04. For some reason my wireless is half way working, It can detect routers and somewhat connect to them. But when I connect to my router and type in the password it will start connecting and then stop, and ask for the pw again. IT seems it won't let me connect.

my router has a WPA/WPA2 security, and my network controller is a :  Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe

THanks in advance!

---

### Post by rencemc on 2013-09-12
Have you tried it with no encryption/security set ? Temporarily disable encryption on the router and see if you can
connect. That way you can narrow it down to the WPA/WPA2 security.

---

### Post by manoriax on 2013-09-12
Also, additional information would be nice. Please run the following commands in a terminal and post the output here.
```

lspci -nnk 
ifconfig wlan0
iwconfig wlan0 

```
(of course, you should replace "wlan0" with your network adapter, though it should be working if you only have one wireless adapter installed)

---

### Post by bryce2 on 2013-09-12
Here is what code appeared in the terminal when i put in the above code


Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

---

### Post by manoriax on 2013-09-13
I suspect that you copied the code I posted? Try enter each command separately, this should work. So first the "lspci -nnk" (without the "), then the other two.

---

### Post by varunendra on 2013-09-13
To keep the output short -
```
lspci -nnk | grep -iA2 net
```
You should copy-paste above to avoid typo. The pipe (|) symbol is on the same key as backslash (\) on my US-104 type keyboard.

And Welcome to the forums bryce2 ! :)

**PS:**
While posting the output, please use 'Code' box. To see how to use it - please follow the "Using Code Tags" link in my signature. Thanks!

---

### Post by bryce2 on 2013-09-13
Thanks varunendra! Sorry, Like I said I am brand new to ubuntu and am a total noob lol. Ok, ill be sure to re enter the code seperatley instead of all together. Ill post back when i've finished!

---

### Post by bryce2 on 2013-09-13
I have entered the code into terminal, this was the output:

```
05:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. Device [1814:f051]
    Kernel driver in use: rt2800pci
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2ab5]
    Kernel driver in use: r8169


```

---

### Post by varunendra on 2013-09-13
Let's try a few things available.

Please open a terminal and do -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
Do not reboot after this since it is a temporary change and will be lost at next boot. If it helps, we can make it permanent.

If it doesn't help, then without rebooting, try saving your network's name (SSID) and security key in Network Manager settings. Also save your access-point/router's MAC address in the BSSID field of NM settings. Make sure "Available to all" checkbox is checked. Does this help connecting?

If not, please post the outputs of -
```
nm-tool
dmesg | grep rt2
```

---

### Post by bryce2 on 2013-09-14
Ok I entered the first codes in seperatley and then tried connecting, same thing: it started to connect, asked me for the router password, then started connecting, then asked for the PW again.

The SSID, PW, and MAC addresses were already saved and "available to all" (Or in my case "All users may connect to this network") was also checked.

I entered nm-tool and this code came up:

```
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        74:DE:2B:DE:DD:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    myqwest4842:     Infra, 20:76:00:04:31:3C, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    myqwest3085:     Infra, 40:4A:03:DD:6E:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Bergs:           Infra, 00:25:9C:45:D8:1B, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    CenturyLink8095: Infra, 40:8B:07:C8:9D:24, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    stefanij9:       Infra, 00:22:75:E2:D7:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        38:60:77:A8:62:17

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

In my case "CenturyLink8095" is my router. I also tried the other code dmsg | grep rt2, but when i entered it in the console nothing happened.

---

### Post by varunendra on 2013-09-14
> **bryce2 said:**
> I also tried the other code **[COLOR="#FF0000"]dmsg[/COLOR] | grep rt2,** but when i entered it in the console nothing happened.
Because it is "dm**[COLOR="#FF0000"]e[/COLOR]**sg", not dmsg. Wrong code = error instead of expected output = nothing to grep.

Anyway, nevermind with that now. There are a couple more things I want to try before resorting to the proprietary one -
```

  Wireless Access Points 
    myqwest4842:     Infra, 20:76:00:04:31:3C, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    myqwest3085:     Infra, 40:4A:03:DD:6E:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Bergs:           Infra, 00:25:9C:45:D8:1B, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    **CenturyLink8095: Infra, 40:8B:07:C8:9D:24, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 [COLOR="#FF0000"]WPA WPA2[/COLOR]**
    stefanij9:       Infra, 00:22:75:E2:D7:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

```
Your router is currently set to use WPA/WPA2 mixed mode. It generally doesn't work well with Linux. Please change it to pure WPA2-PSK, with AES encryption. No mixed mode, no TKIP.

Besides that, there can also be problem with N-channel sometimes. So if your router supports it and is enabled, please try disabling it by changing the channel to b/g mode only.

After doing these changes, please try the two modprobe commands again. If you still can't connect, please follow the "Wireless Script" link in my signature, follow the instructions to run it, and post back the result here. It'll give me everything to decide our further action, hopefully, just one or two more posts.

---

### Post by bryce2 on 2013-09-15
Ok I have set the router settings to WPA2 with AES encryption and ran the 2 modprobe commands in terminal, same exact thing: the router kept asking for the password and wouldnt connect.

I followed the instructions for the wireless script and this was the output:

```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

05:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. Device [1814:f051]
    Kernel driver in use: rt2800pci
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2ab5]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 192f:0416 Avago Technologies, Pte. 
Bus 001 Device 004: ID 0461:4dd7 Primax Electronics, Ltd 
Bus 001 Device 007: ID 0781:556c SanDisk Corp. 
Bus 002 Device 003: ID 046d:082c Logitech, Inc. 
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Bergs:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    myqwest4842:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    CenturyLink8095: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    myqwest3085:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2


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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

No way to aquire root rights found.

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

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A40A95D1558A66562B223A2
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     8C466FA66D830BEA5BE8597
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4C55FBC01E873875F9583CA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F3B7F97865D53E7B0E71194
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.4/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.581879] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.582085] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.549999] wlan0: authenticate with <MAC address removed>
[  138.566061] wlan0: send auth to <MAC address removed> (try 1/3)
[  138.567565] wlan0: authenticated
[  138.569430] wlan0: associate with <MAC address removed> (try 1/3)
[  138.574242] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  138.574311] wlan0: associated
[  138.574340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  138.660333] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  146.514485] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  152.077664] wlan0: authenticate with <MAC address removed>
[  152.093446] wlan0: send auth to <MAC address removed> (try 1/3)
[  152.094933] wlan0: authenticated
[  152.097124] wlan0: associate with <MAC address removed> (try 1/3)
[  152.100531] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  152.100600] wlan0: associated
[  152.172866] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  160.030838] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  460.699759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  460.700093] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  516.833810] wlan0: authenticate with <MAC address removed>
[  516.849937] wlan0: send auth to <MAC address removed> (try 1/3)
[  516.851430] wlan0: authenticated
[  516.853306] wlan0: associate with <MAC address removed> (try 1/3)
[  516.857047] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  516.857119] wlan0: associated
[  516.857128] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  516.907803] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  524.791059] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  561.219727] wlan0: authenticate with <MAC address removed>
[  561.235851] wlan0: send auth to <MAC address removed> (try 1/3)
[  561.237355] wlan0: authenticated
[  561.239243] wlan0: associate with <MAC address removed> (try 1/3)
[  561.243197] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  561.243271] wlan0: associated
[  561.335277] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  569.176326] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  588.515225] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  588.515556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  608.628822] wlan0: authenticate with <MAC address removed>
[  608.644890] wlan0: send auth to <MAC address removed> (try 1/3)
[  608.648310] wlan0: authenticated
[  608.652147] wlan0: associate with <MAC address removed> (try 1/3)
[  608.655715] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  608.655773] wlan0: associated
[  608.655779] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  608.731395] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  616.587911] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  621.256546] wlan0: authenticate with <MAC address removed>
[  621.272780] wlan0: send auth to <MAC address removed> (try 1/3)
[  621.274485] wlan0: authenticated
[  621.276175] wlan0: associate with <MAC address removed> (try 1/3)
[  621.279413] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  621.279482] wlan0: associated
[  621.322561] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  629.211986] wlan0: deauthenticated from <MAC address removed> (Reason: 15)

****************** done ******************


```

---

### Post by varunendra on 2013-09-16
Okay, time to try the proprietary driver, tested successfully on kernel 3.8.0-26-generic, 64 bit, with a required patch ([post=12732190]reference post[/post]) -

Before compiling, make sure the essential components required to build a package are installed -
```
sudo apt-get install linux-headers-generic build-essential
```

Now download, patch and compile the driver as follows :

[INDENT]**1)** Download the proprietary driver (2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2) from mediatek's official site [here]("http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001").
(If you don't want to supply your actual name & email, just use any dummy one). Copy this file to your Desktop.

**2)** Rename this file so that the name ends with "**[COLOR="#006400"].tar[/COLOR].bz2**" instead of ".bz2.bz2".

**3)** Right-click the renamed file > click "Extract Here". This will extract a folder named "**2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO**" on your Desktop.

**4)** Download a patch for this driver (right-click the link > "Save as") : [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch) .
Copy this .patch file (rt5592sta_fix_64bit_3.8.patch) inside the folder you just extracted above.

**5)** Open the file **os/linux/config.mk** from the extracted directory. Edit its line no.31 to change "**n**" to "**y**". It should now read -
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#006400"]y[/COLOR]**
```

**6)** Open a terminal (Ctrl-Alt-T) and enter the following commands *(one at a time > let it finish > next command. Hint: just type a few initial characters, then press "Tab" key to auto-complete long names)* :
```
cd Desktop/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
patch -p1 <rt5592sta_fix_64bit_3.8.patch
make
sudo make install
```
Watch out for errors. Exactly one error (regarding "/tftpboot") during 'make' is normal and can be safely ignored. Report here if there are more.[/INDENT]

Now remove the native driver and load the compiled one -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt5390sta
```

To avoid conflict, blacklist the native one -
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

If everything went fine, please let us all know about its performance. Thanks.

---

### Post by bryce2 on 2013-09-19
I have followed all the instructions accordingly and only 2 errors appeared during the process , 

When i entered

```
sudo apt-get install linux-headers-generic build-essential
```

It said it could not find that build.

And when i entered 

```
sudo modprobe -v modprobe rt5390sta
```

This appeared

```
FATAL: Module modprobe not found.
```

Please reply as soon as you can, i've been having major issues with my computer and need to get ubuntu working functionally ASAP. :D

---

### Post by varunendra on 2013-09-20
> **bryce2 said:**
> 
```
sudo modprobe -v modprobe rt5390sta
```

Oops ! Sorry, that's a mistake on my part, a stupid one :redface:

It should be just -
```
sudo modprobe -v rt5390sta
```
Going to correct that in my original post too..

But if the 'make' command didn't return any errors (except maybe the /tftpboot one), the sta module should load automatically at next boot. So did the 'make' command finish smoothly?

Please post the outputs of -
```
lsmod | egrep 'rt2|rt5'
dmesg | egrep 'rt2|rt5'
```

And can you post the exact error message that you get while trying -
```
sudo apt-get install linux-headers-generic build-essential
``` ?

---

### Post by bryce2 on 2013-09-24
My computer's wireless seems to be working perfectly now, although i haven't tried downloading etc. but searching the internet is working fine.


Will I have to go through this process everytime there is an ubuntu update? 

This was the out put of the lsmod and the dmesg commands:

```
rt5390sta            1460542  1 
 dmesg | egrep 'rt2|rt5'
[   11.228037] rt5390sta: module license 'unspecified' taints kernel.
[   11.246523] register rt2860
[   12.841372] Modules linked in: parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_usb_audio snd_usbmidi_lib joydev(F) rt5390sta(POF) coretemp kvm ghash_clmulni_intel(F) aesni_intel(F) aes_x86_64(F) xts(F) lrw(F) gf128mul(F) ablk_helper(F) cryptd(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) gpio_ich snd_hda_codec_idt snd_hda_intel(+) microcode(F) snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq(F) snd_seq_device(F) snd_timer(F) psmouse(F) serio_raw(F) lpc_ich snd(F) nouveau mxm_wmi soundcore(F) wmi video(F) ttm drm_kms_helper drm mei i2c_algo_bit mac_hid lp(F) parport(F) usb_storage(F) hid_generic usbhid hid r8169 ahci(F) libahci(F)
[   12.841426]  [<ffffffffa04a66bb>] RtmpAsicSendCommandToMcu+0x77b/0x8b0 [rt5390sta]
[   12.841436]  [<ffffffffa04269e9>] AsicSendCommandToMcuBBP+0x29/0x30 [rt5390sta]
[   12.841443]  [<ffffffffa03fa453>] NICInitBBP+0x1353/0x2bb0 [rt5390sta]
[   12.841452]  [<ffffffffa03fc35b>] NICInitializeAsic+0x2fb/0x5a0 [rt5390sta]
[   12.841458]  [<ffffffffa03fc791>] NICInitializeAdapter+0x191/0x6b0 [rt5390sta]
[   12.841465]  [<ffffffffa0403af4>] rt28xx_init+0x2a4/0x710 [rt5390sta]
[   12.841474]  [<ffffffffa04824a5>] rt28xx_open+0x95/0x100 [rt5390sta]
[   12.841482]  [<ffffffffa0413d6e>] RTMP_COM_IoctlHandle+0x53e/0x5a0 [rt5390sta]
[   12.841490]  [<ffffffffa0481ec7>] MainVirtualIF_open+0x47/0xe0 [rt5390sta]
[   12.841498]  [<ffffffffa0482410>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   12.841505]  [<ffffffffa0481df0>] ? MainVirtualIF_close+0xb0/0xb0 [rt5390sta]
[   12.915442] <==== rt28xx_init, Status=0
[   12.939742] <==== rt28xx_init, Status=0
[   12.962874] <==== rt28xx_init, Status=0
[  375.739018] <==== rt28xx_init, Status=0
[  375.762561] <==== rt28xx_init, Status=0




```

Thanks for your help Varun!

---

### Post by varunendra on 2013-09-24
Congratulations ! Thanks for the feedback. :)
> **bryce2 said:**
> Will I have to go through this process everytime there is an ubuntu update?
There is a '*dkms*' installation which can do it automatically, but unfortunately, I don't know yet how to implement it. So with the procedure given here, yes, you will have to do this everytime a kernel upgrade happens.

Keep the folder where you ran 'make' command (so that the renaming > extracting > editing > patching is already done). Then whenever a newer kernel installs, you will just need to go into that directory > run 'make clean' > 'make' > 'sudo make install' :
```
cd *<the directory where you have previously run 'make' from>*
make clean
make
sudo make install
```

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post on the page. It helps others by indicating that this thread contains a possible solution to their problem. :)

---

### Post by bryce2 on 2013-09-25
Thanks again Varun!!

---

