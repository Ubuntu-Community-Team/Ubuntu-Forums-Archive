---
title: "Lubuntu 13.04 - AR242x / AR542x Wireless not working"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by pinolo on 2013-10-12
I run lubuntu 13.04, kernel 3.8.0-19-generic, on a compaq presario CQ60-301SL, and my wifi is not working...
with the command **lshw** i get:

```

...
        *-network
             description: Wireless interface
             product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:24:2b:82:1a:0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff
...

```


after a search on google i gave these commands:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
(rebooting)
ifconfig wlan0 up
iwlist wlan0 scan


```


i get:

```
wlan0     No scan results

```

and the network manager enabling option for wifi is uncheckable...

How can I solve this?
Thank you!

---

### Post by varunendra on 2013-10-13
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us almost all the info required to locate the problem and possibly solve it.

---

### Post by pinolo on 2013-10-14
Thank you, here is the script output:

```



*************** info trace ***************


***** uname -a *****


Linux user-Compaq-Presario-CQ60-Notebook-PC 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Kernel driver in use: ath5k


***** lsusb *****


Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


***** rfkill *****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


ath5k                 149933  0 
ath                    23827  1 ath5k
mac80211              606457  1 ath5k
cfg80211              511019  3 ath,ath5k,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254






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




***** resolv.conf *****


nameserver 127.0.1.1
search Digicom-ADSL


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     0B3CF1DF2C984E30CCA3C9E
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:14.0/0000:07:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   21.434924] ath5k 0000:07:00.0: registered as 'phy0'
[   24.854760] ath: EEPROM regdomain: 0x67
[   24.854766] ath: EEPROM indicates we should expect a direct regpair map
[   24.854771] ath: Country alpha2 being used: 00
[   24.854773] ath: Regpair used: 0x67
[   24.939761] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   27.864250] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

---

### Post by pinolo on 2013-10-14
ok, I see that it was hard blocked (and nothing happened if I pressed the wifi hard button)

if I give the command "sudo rfkill unblock all" it works!

---

### Post by varunendra on 2013-10-14
> **pinolo said:**
> if I give the command "sudo rfkill unblock all" it works!

So can we consider it solved? If yes, please mark it [SOLVED] using the "Thread Tools" link above the top post. :)

If not, and because you always have to do that, you may try this (not sure, looks like it may help) -

Check the value of a parameter -
```
cat /sys/module/ath5k/parameters/no_hw_rfkill_switch
```
If it is set to "N", try this -
```
echo "options ath5k no_hw_rfkill_switch=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
This will create a conf file for ath5k driver, which apparently tells the driver to "Ignore" the hardware switch's rfkill state. Enable the wifi with rfkill command and reboot to see if it remains on. If it (the conf file) causes the opposite effect, simply delete the file -
```
sudo rm /etc/modprobe.d/ath5k.conf
```
..and reboot to return to current state.

..And let me know the result.

---

### Post by pinolo on 2013-10-17
solved, all right :)

---

### Post by Naturally-Simple on 2014-04-07
Hello Varun,
I came across your helpful posts through a search for my wireless card, and wanted to see what your opinion is on my wireless issue I've had for a few years now. Here is the output of your script I ran:

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux deep-thought 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:32 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.168.122.1    0.0.0.0         UG    0      0        0 eth0
10.168.122.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search wp.shawcable.net

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         10.168.122.2
    Prefix:          24 (255.255.255.0)
    Gateway:         10.168.122.1

    DNS:             64.59.176.13
    DNS:             64.59.177.226

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

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

##### lsmod #####

ath5k                 135055  0 
ath                    19187  1 ath5k
mac80211              517444  1 ath5k
cfg80211              401762  3 ath,ath5k,mac80211

##### modinfo #####

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     68167C5D7C0F1F5FF5D8D62
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 

##### modules #####

lp
ath_pci
ath_pci

##### blacklist #####

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
blacklist hp-wmi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x050d:0x705e (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x168c:0x001c (ath_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ath*", NAME="ath0"

##### dmesg #####

[   20.502995] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.503131] ath5k 0000:02:00.0: registered as 'phy0'
[   21.222230] ath: EEPROM regdomain: 0x64
[   21.222233] ath: EEPROM indicates we should expect a direct regpair map
[   21.222237] ath: Country alpha2 being used: 00
[   21.222238] ath: Regpair used: 0x64
[   21.236244] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   26.200965] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.201316] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

Could you please help me? This wireless issue has been nagging me for a  couple years now, and it seems like no one has been able to completely resolve it. Every version upgrade I make I cross my fingers hoping it will be solved,  but so far no such luck.

Thanks,
-Kevin
ps. ignore the part of my username "Dell1100" as I started this account before I my laptop of a Compaq Presario CQ60.

---

### Post by varunendra on 2014-04-08
Hello Kevin,

As replied to your PM, I am not a very useful guy these days. My current routine hardly allows any time to keep up with my forum contributions.

I haven't looked through your previous posts very thoroughly, so not sure what all have you tried so far. For now, these are my suggestions -

[INDENT]**1)** Please delete the 'ath_pci' entries from your '/etc/modules' file.

**2)** If blacklisting 'hp_wmi' helps removing the wifi 'hard block', keep it. Otherwise remove it from the blacklist too.

**3)** Delete your current udev rules file -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
It will be automatically regenerated when required, with only relevant entries this time.

**4)** While testing wifi, keep the Ethernet cable unplugged. Network Manager, as well as some BIOS may not allow to use wifi when a wired connection is detected.

**5)** If the above suggestions don'e seem to help, try installing a backported driver as suggested in this post (replace "**[COLOR="#FF0000"]defconfig-ath9k[/COLOR]**" with "**[COLOR="#0000CD"]defconfig-ath5k[/COLOR]**" in the commands) : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)[/INDENT]

If none of these could solve the problem, please start a new thread and give me its link (but don't put much hope on 'my' suggestions or responsiveness).

---

