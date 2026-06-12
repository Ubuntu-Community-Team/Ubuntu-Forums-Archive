---
title: "Atheros AR9285 / Lenovo G560 wireless not working after installing 13.04"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by teyi on 2013-11-02
Hello everyone,

I had Ubuntu 12.04 initially installed on my laptop. I upgraded to 12.10 then 13.04. 
Everything worked fine, including wireless.
After adding a new memory card ( I only had 2 gb and one memory slot free) my wireess stopped working.
I backed up all my data and reinstallled Ubuntu 13.04.
Everything works fine except wireess.
I bought this laptop in 2010 from Japan.
It has Intel Core i5 CPU M 450 @2.40 Ghz * 4
3,7 Gb RAM
os type 64 bit
The output of iwconfig:

```
eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 
```


The output of rfkill list all:

```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

The output of lshw -C network:

```
*-network                      description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:7d:fe:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d6400000-d640ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 88:ae:1d:2b:36:ac
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:d2410000-d2410fff memory:d2400000-d240ffff memory:d2420000-d243ffff



```

the wi-fi network appears as disconnected ( it's greyed out) Strangely enough I see a wifi network ( not mine) but not mine or the rest. That network doesn't require a password . I click on it, try to connect and i get an error message: failed to connect to xxxxx ... 32) The access point /org/freedesktop/NetworkManager/AccessPoint/0 was not in the scan list.
Someone help please :)

---

### Post by teyi on 2013-11-13
Apparently nobody knows the answer :( Tried every solution i found on the internet  but nothing is working. Still no wi fi :(

---

### Post by teyi on 2013-11-22
Went back to Ubuntu 12.04, the wireless still not working. I really don't know what else I can do.

---

### Post by teyi on 2013-11-22
:popcorn:
:guitar::KS

---

### Post by teyi on 2013-11-22
My complete wireless info:

```



*************** info trace ***************


***** uname -a *****


Linux snowdrop 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


05:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lenovo Device [17aa:30a1]
	Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Lenovo Device [17aa:392e]
	Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 090c:37b3 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 005: ID 125f:a11a A-DATA Technology Co., Ltd. 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


ath9k                 151796  0 
mac80211              630977  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422432  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              525326  3 ath9k,mac80211,ath


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






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


filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DD97D617F7C24BA9D111D21
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
vermagic:       3.8.0-33-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)


filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0078E2DDCA5F8B073A36467
depends:        ath
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   13.089499] ath: phy0: ASPM enabled: 0x43
[   13.089505] ath: EEPROM regdomain: 0x6a
[   13.089506] ath: EEPROM indicates we should expect a direct regpair map
[   13.089508] ath: Country alpha2 being used: 00
[   13.089509] ath: Regpair used: 0x6a
[   22.912658] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.915692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

---

### Post by chili555 on 2013-11-23
Network Manager will prefer wired over wireless. Please detach the ethernet cable, reboot and run:```
nm-tool
dmesg | grep -e ath -e wlan
sudo iwlist wlan0 scan
```Re-attach the ethernet, connect and give us the results here.

---

### Post by teyi on 2013-11-24
Ok, did this and this is the result:


```

matirdutza@snowdrop:~$ nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:2B:36:AC


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        78:E4:00:7D:FE:FA


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


matirdutza@snowdrop:~$ dmesg | grep -e ath -e wlan
[    1.507800] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: f18b7991d2384529679d61befc4fb536686c75e2'
[   13.256036] ath: phy0: ASPM enabled: 0x43
[   13.256038] ath: EEPROM regdomain: 0x6a
[   13.256039] ath: EEPROM indicates we should expect a direct regpair map
[   13.256041] ath: Country alpha2 being used: 00
[   13.256041] ath: Regpair used: 0x6a
[   21.848017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.851407] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.307925] type=1400 audit(1385277714.322:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1000 comm="apparmor_parser"
[   22.308334] type=1400 audit(1385277714.322:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1000 comm="apparmor_parser"


matirdutza@snowdrop:~$ sudo iwlist wlan0 scan
[sudo] password for matirdutza: 
wlan0     No scan results



```

---

### Post by chili555 on 2013-11-24
Let's try a driver parameter:```
sudo -i
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
modprobe -r ath9k
modprobe ath9k
exit
```Any improvement? It may take a reboot.

---

### Post by teyi on 2013-11-24
None...

---

### Post by chili555 on 2013-11-24
Let's try to compile a later and, hopefully, better version of the driver. Please download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2)  Right-click it and select 'Extract Here.' Now get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop/backports-3.11-rc3-1
make defconfig-ath9k
make
sudo make install
sudo rm /etc/modprobe.d/ath9k.conf
```Reboot and let me have a (good) report!

---

### Post by teyi on 2013-11-25
Nothing changed :)
I start thinking I have ghosts in my laptop :)
Here, a screenshot:

[IMG]http://rapcea.ro/testing/Menu_002.png[/IMG]

---

### Post by teyi on 2013-11-25
I forgot to tell you I tried this solution beforeon November 16, before downgrading to Ubuntu 12.04 (thought it might have been some low level problem, as somebody suggested on askubuntu:
```
a. Power down and REMOVE BATTERY
b. HOLD POWER SWITCH for 30 SEC (attempts to power-up so empties internal capacitors)
c. Power on, interrupt boot with BIOS Setup access and choose RESTORE DEFAULTS
d. Reboot 
``` and did the rest this guy suggested but nothing changed.
[http://askubuntu.com/questions/377948/partially-solved-info-about-wireless-being-greyed-out-on-lubuntu-13-04-af](http://askubuntu.com/questions/377948/partially-solved-info-about-wireless-being-greyed-out-on-lubuntu-13-04-af)

So, I don't know :)
It's weird how this happened right after adding the new RAM.
Everything was fine before. Yes I had some weird wireless interruptions, when no SSIDs were recognized but this was temporary and not very often.

---

### Post by chili555 on 2013-11-25
> It's weird how this happened right after adding the new RAM.Weird indeed. Will you please remove the new RAM stick(s), reboot and tell us the result?

---

### Post by teyi on 2013-11-25
Damn!!!
I opened it and one wire was disconnected!
I put it back and ...that was it. 
Let the RAM there, untouched.
Thank you for suggesting me to open it :)
And thank you for your time!
I will mark this as SOLVED.
:KS

This is the disconnected wire:

[IMG]http://rapcea.ro/testing/bad.jpg[/IMG]

...And back as it should be:

[IMG]http://rapcea.ro/testing/good.jpg[/IMG]

---

### Post by chili555 on 2013-11-25
Antenna wires on the wireless card it appears. Easy to miss. I am glad it is fixed.

---

### Post by teyi on 2013-11-25
:) Thank you again

---

