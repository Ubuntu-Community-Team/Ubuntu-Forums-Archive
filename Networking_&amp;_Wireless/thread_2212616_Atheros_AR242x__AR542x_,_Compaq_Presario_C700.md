---
title: "Atheros AR242x / AR542x , Compaq Presario C700"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by StealthMode on 2014-03-22
Hello, I'm hoping that this thread is still active. I've been having a heck of a time trying to get the Atheros wireless card to turn on. I ran the script and here is my output. 
EDIT: sorry it's not an Asus laptop, but still uses the Atheros card, so I guess I should be up front about that. My machine is a Compaq Presario C700.

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux megatron-notebook 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

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

# interfaces(5) file used by ifup(8) and ifdown(8)
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
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search Home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.2.25

  IPv6 Settings:
    Address:         fd00::21b:38ff:fec5:586e
    Prefix:          64
    Gateway:         ::

    Address:         fe80::21b:38ff:fec5:586e
    Prefix:          64
    Gateway:         ::

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

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

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

ath5k                 150026  0 
ath                    23827  1 ath5k
mac80211              597268  1 ath5k
cfg80211              480503  3 ath,ath5k,mac80211

##### modinfo #####

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
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
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

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

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   11.521932] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.522121] ath5k 0000:01:00.0: registered as 'phy0'
[   12.170355] ath: EEPROM regdomain: 0x64
[   12.170356] ath: EEPROM indicates we should expect a direct regpair map
[   12.170359] ath: Country alpha2 being used: 00
[   12.170360] ath: Regpair used: 0x64
[   12.221733] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.765345] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.766042] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2091.338416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

Thank you for taking a look!

---

### Post by lisati on 2014-03-22
I've moved your post to its own thread. Sometimes you might get lucky and find that what works on one machine works on another by different manufacturer. On the other hand, even machines from the same manufacturer often have different hardware.....

---

### Post by varunendra on 2014-03-22
Have you tried the wireless with the Ethernet cable unplugged?

Some laptops, especially HPs have a setting to automatically disable wireless if a wired connection is detected. Yours doesn't seem to be 'disabled', but Network Manager may also prefer the wired connection and not try the wireless connection when the wired one is being used.

So.. please make sure the Ethernet cable is unplugged, then try -
```
sudo iwlist scan
```
Do you get any scan results? Try it after a reboot (with cable unplugged) if you can't. Also check the BIOS to make sure wireless is enabled there. This would probably just a sanity check since your only available interface (phy0) already seems to be enabled in "rfkill list" command.

How old is this laptop by the way? Is there any evidence that the card itself is working, just not in Ubuntu?

---

### Post by praseodym on 2014-03-22
Deactivate the hardware encryption of the driver via
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by StealthMode on 2014-03-25
I followed this write-up [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and it seemed to work, but all I managed to do is disable the hardware switch! So now network manager doesn't detect wireless AT ALL, and pushing the button doesn't do anything anymore. I will post my results below. 

sudo iwlist scan 
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.


```
echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
```

options ath5k nohwcrypt=1

```
sudo modprobe -v ath5k
```
insmod /lib/modules/3.11.0-18-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1 

```

---

### Post by StealthMode on 2014-03-25
After entering those commands, I now have SOME kind of recognition via Network Manager for wireless. It tells me "Wifi is disabled by hardware switch" but the "enable Wifi" option is not selectable. It is dark gray, along with the previous comment about hardware switch. I'm going to check the BIOS and see if it is enabled. 

As far as I know, the computer is a couple (a "few" probably) years old. As far as I understand, Compaq laptops are no longer being manufactured.

I couldn't find anything in the BIOS for enabling wifi. I'll attach some pictures I took.
** I don't think I uploaded them in the correct order, but I'm sure you know what you're looking at better than I do.

---

### Post by varunendra on 2014-03-25
Ndiswrapper is rarely needed and is usually an added problem rather than a fix. We keep it as a last resort and that too only for a very few cards. I don't think yours is one of those 'very few'.

Please purge it, and try only what is suggested 'here' (not anywhere else) on a clean system. To purge ndiswrapper -
```
sudo modprobe -rv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper
```

Post back a fresh report of "wireless_script" so that we can be sure there is no more ndiswrapper factor involved. You may try it again if everything we suggest here fails. But if it is present in the system, whatever we would suggest would certainly fail.

Nothing interesting in the screenshots you posted.

---

### Post by StealthMode on 2014-03-25
I have another question regarding this wireless issue on my machine. All the searching I did on this subject pointed me in the direction of "blacklisting" certain drivers using Gedit. I have done some of that but I am not completely confident that I did things correctly. Should I do a fresh install of Ubuntu 13.10 as sort of a "reset" button for the damage I might have done to the file system? This is a fresh install on a new-to-me computer, and I don't have anything important saved. I did partition my drive with a separate home directory, but if I needed to re-do that as well, I don't mind. 

I ran those commands, but I will need to wait some time today to either return home after work for an internet connection, or find an available ethernet connection here at work, with a few minutes free to run the script.

EDIT: script output below
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux megatron-notebook 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search Home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             205.171.2.25

  IPv6 Settings:
    Address:         fd00::21b:38ff:fec5:586e
    Prefix:          64
    Gateway:         ::

    Address:         fe80::21b:38ff:fec5:586e
    Prefix:          64
    Gateway:         ::

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist ath_pci
blacklist ath_hal
blacklist ath9k
blacklist ath5k

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

########## wireless info END ############
```

---

### Post by varunendra on 2014-03-25
> **StealthMode said:**
> Should I do a fresh install of Ubuntu 13.10 as sort of a "reset" button for the damage I might have done to the file system?

Shouldn't be necessary, but a fresh installation takes just 15-30 minutes depending upon system's overall speed. So if there are no other concerns, I'd suggest go ahead with a fresh install so that there are no doubts about any 'remnant' problems from previous attempts.

If you wish to try your luck with the current setup before a fresh install, please remove the blacklisting first that you did with the following command -
```
sudo sed -i '/^blacklist ath/ d' /etc/modprobe.d/blacklist.conf
```

Then either reboot, or load the driver manually -
```
sudo modprobe -v ath5k
```

Check if you can scan available networks now -
```
sudo iwlist scan
```
If it shows available networks, including yours, can you connect to it now? If not, then our next step would be to try a newer driver. The steps would be almost the same as suggested in this post, ONLY the command **"make defconfig-ath9k"** would be replaced **"make defconfig-ath5k"** in **step 3** : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)

If you prefer to try these on a fresh installation, try ONLY the "nohwcrypt=1" parameter that praseodym suggested first. If that doesn't seem to help, only then try the newer driver suggested above.

---

### Post by StealthMode on 2014-03-26
Ok, first I tried to repair it before blowing away my OS, using Varunendra's suggestions. No luck. So I re-installed 13.10 and tried the parameter by Praseodym. No luck. I then tried updating the driver, following the link at the end of Varunendra's post, making sure to change the command to "make defconfig-ath5k". It installed, there were no errors. I rebooted, and when I click on Network Manager, it shows "wireless networks" and "disconnected" in gray, unable to be clicked. "Enable Wi-Fi" has been checked. My hardware switch LED is blue (rather than orange when it's not working) but when I push the button, nothing changes when I have the drop down menu for Network Manager expanded. I clicked on "enable wifi" to disable it, and then re-enabled it. Still nothing. 

Any other ideas gents? Thank you again for helping to walk me through this.

I tried "sudo iwlist scan" 
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results


```

---

### Post by varunendra on 2014-03-26
> **StealthMode said:**
> Any other ideas gents? Thank you again for helping to walk me through this.

Please show us a fresh report of the wireless_script.

---

### Post by StealthMode on 2014-03-26
Updated wireless_script
```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux megatron-notebook 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
	Kernel driver in use: ath5k
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Kernel driver in use: 8139too


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eth0
10.0.1.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.0.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1


    DNS:             10.0.1.155
    DNS:             67.122.32.71


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


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


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


ath5k                 149775  0 
ath                    28698  1 ath5k
mac80211              530286  1 ath5k
cfg80211              483366  3 ath,ath5k,mac80211
compat                 13893  3 cfg80211,ath5k,mac80211


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
srcversion:     E3AAE20365450BBB996B8D5
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
depends:        mac80211,compat,cfg80211,ath
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0BE5FC7C1EAF38AFA84BEDB
depends:        cfg80211
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


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


##### udev rules #####


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   10.445838] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.446031] ath5k 0000:01:00.0: registered as 'phy0'
[   11.162380] ath: EEPROM regdomain: 0x64
[   11.162386] ath: EEPROM indicates we should expect a direct regpair map
[   11.162391] ath: Country alpha2 being used: 00
[   11.162393] ath: Regpair used: 0x64
[   11.269493] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.662030] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.714464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############
```

---

### Post by varunendra on 2014-03-26
Your wifi is currently disabled by 'Hardware switch' -
> **StealthMode said:**
> ```
##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	**Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
```

Accordingly, please make sure the hardware switch, if any, is turned "on". This may be a physical dedicated switch or a Fn+ key combination etc. depending on laptop's model. Also refer to the instructions in post #3.

We need to see "Hard blocked" as "no" in the output of command "rfkill list".

_ONLY If_ the hardware switch or the instructions in post #3 don't help enabling the card, try this -
```
echo "options ath5k no_hw_rfkill_switch=Y nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
Reboot, and check the output of command "rfkill list" again. If it still shows as "Hard blocked : yes", and the previous suggestions above don't help, please post back the outputs of -
```
rfkill list
lsmod
dmesg | egrep 'ath|phy|firm'
grep [[:alnum:]] /sys/module/ath*/parameters/*
```

---

### Post by StealthMode on 2014-03-27
Ok, maybe we are on the right track. I followed the first half of your post, Varun, and when I rebooted I ran "rfkill list" and got this:
```
0: phy0: Wireless LAN	Soft blocked: no
	Hard blocked: no

```

However, when I unplug Ethernet and even give it 15-30 minutes of sitting there to scan for available wireless networks, I still get nothing. 

My "enable wifi" is checked in Network Manager, the hardware switch in the top left hand corner of the keyboard area is blue (rather than orange when not working). So all seems to be turned on, but still no detection of wireless networks.

---

### Post by varunendra on 2014-03-27
Sorry, I'm currently travelling with low battery and almost no signal. May not be able to dig deeper and reply back for a little more time (could be a few hours to a day or two!)

Any of the wireless gurus, if you notice this thread, please jump in!

---

### Post by StealthMode on 2014-03-28
Thanks Varun. I will keep my eyes peeled for a reply. I appreciate your willingness to help!

---

### Post by varunendra on 2014-03-30
Looks like I getting more busy as the time is passing by, and I'm afraid it may be too late before I can get the opportunity to look into it again and reply back.

I have asked someone to take a look at your thread. So I hope you'll certainly get an answer soon if there is one.

---

### Post by chili555 on 2014-03-30
Now that the LED is blue and rfkill reports not blocked, does it scan?```
sudo iwlist wlan0 scan
```If it scans, we generally can get it to connect.

---

### Post by StealthMode on 2014-04-01
Thank you Chili for taking the reins on this issue. 

sudo iwlist wlan0 scan
```
wlan0     No scan results
```

---

### Post by chili555 on 2014-04-01
Weird is too kind a word for this little problem! Let's have a look at:```
dmesg | grep -e ath -e 01:00
```In this case, 01:00 is the bus number for your wireless card. We hope there is no hardware or ACPI issue here.

---

### Post by StealthMode on 2014-04-01
Ok here are the results:
```
[    0.556861] pci 0000:01:00.0: [168c:001c] type 00 class 0x020000[    0.556899] pci 0000:01:00.0: reg 0x10: [mem 0x91300000-0x9130ffff 64bit]
[    0.557150] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.638873] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9d94dc8d073854d044b3fa3652786ac75597c2f5'
[   12.707723] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.772770] ath5k 0000:01:00.0: registered as 'phy0'
[   13.502088] ath: EEPROM regdomain: 0x64
[   13.502089] ath: EEPROM indicates we should expect a direct regpair map
[   13.502093] ath: Country alpha2 being used: 00
[   13.502094] ath: Regpair used: 0x64
[   13.509789] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

---

### Post by chili555 on 2014-04-01
Hmmm. We don't see anything wrong; that is, fixable here. I suggest you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

---

### Post by StealthMode on 2014-04-01
How do I make those changes with the router? Are they just switches that I need to make sure are activated. It is a Qwest (Century Link) Motorola Q1000 I believe. Or do I need to connect it to my computer somehow to make the changes? I am not able to see wireless networks both at home AND at work, so I am not sure it's a router issue. I would not be able to make any changes to the router at work either. 

I'll get started on these commands and edit this reply with the results.

Ok I set it permanently to "US" for United States. Do I need to reboot or anything?

---

### Post by chili555 on 2014-04-01
Please see: [http://internethelp.centurylink.com/internethelp/modem-q1000-wireless-wpa.html](http://internethelp.centurylink.com/internethelp/modem-q1000-wireless-wpa.html)

This is the stage of troubleshooting I like to call "kitchen sink." We are trying any and everything.

---

### Post by StealthMode on 2014-04-01
Do I need to go to the Century Link configuration page from my HOME? (In order for it to change any settings affecting my personal router?) Just curious because I am currently at work, and might have to modify home internet settings when I get home this afternoon/evening.

---

### Post by chili555 on 2014-04-01
> **StealthMode said:**
> Do I need to go to the Century Link configuration page from my HOME? (In order for it to change any settings affecting my personal router?) Just curious because I am currently at work, and might have to modify home internet settings when I get home this afternoon/evening.Yes, from home. I suggest you hook up to the router with ethernet and open Firefox. Unless you've changed it, and it sounds like you haven't, type in the address bar:```
192.168.0.1
```The configuration pages should appear.

In particular, the page I linked suggests both WPA and WPA2; I think that WPA2 _only_ is preferred. 

I would also look at 'Radio Setup' and try with 802.11B and G only; that is, without N. [http://internethelp.centurylink.com/internethelp/modem-q1000-wireless-radio.html](http://internethelp.centurylink.com/internethelp/modem-q1000-wireless-radio.html)

I also notice that these devices use a default authentication key. In this context, 'default' means everyone in the world knows it or can Google it!!! I suggest you set your own authentication key and use something that doesn't include your address, name or other commonly knowable data. Of course, if you change it, every connected device will get kicked off until you tell everyone the new secret key.

---

### Post by StealthMode on 2014-04-01
Ok thank you Chili. I will give it a go tonight when I get home and I'll reply back, letting you know the results.

---

### Post by StealthMode on 2014-04-01
Ok, I made your suggested changes to the router configuration, selecting Channel 1 for now. The rest, I followed your advice. I didn't touch the other config settings like MAC Authentication, WPS, WMM, WDS, or 802.1x. I just left those as they were. I am about to reboot the router and we'll see what happens. I will disconnect from ethernet for a few and see what the results are.

EDIT: Router rebooted, no detection of wireless networks from this computer still.

---

### Post by chili555 on 2014-04-02
Frankly, we can see no reason whatever that this device doesn't start and run. The only, admittedly crazy thought I have is to check to see if the wireless card is seated in its slot and that the antenna wires haven't become dislodged. Many laptops have a door on the bottom that can be used to access the wireless card. Here is an example: [http://paulov.ru/files/2011/11/replacing-laptop-keyboard-11.jpg](http://paulov.ru/files/2011/11/replacing-laptop-keyboard-11.jpg)

Before you proceed, find the hardware repair manual on line and check and follow all the usual precautions.

I notice that there may also be a hardware switch that has its own little board; it may be intermittent, if not altogether defective. [http://www.itsurplusliquidators.com/media/catalog/product/cache/1/image/400x360/9df78eab33525d08d6e5fb8d27136e95/d/s/dsc05149.jpg](http://www.itsurplusliquidators.com/media/catalog/product/cache/1/image/400x360/9df78eab33525d08d6e5fb8d27136e95/d/s/dsc05149.jpg) That would help to explain why your rfkill drifts from blocked:yes to blocked:no. 

I have no further suggestions.

Notice that the smart and fast guys have already left the thread!

---

### Post by StealthMode on 2014-04-02
I opened the case, checked the card, and found that one of the wires' connection point was loose. So I pushed it back down to re-seat it. While I was in there I couldn't break the screws loose to check the connection of the card itself. I wish it was that easy to re-seat the wire and voila! But sadly no... 

My next question is: Is there perhaps a completely different driver that I can try rather than the ath5k? Maybe some kind of work-around? Or are you thinking this is more of a hardware issue, rather than software? I can try to get a completely different card and install it, if that might work. Or I can try to find an external usb card....?

What about something like this [http://www.amazon.com/Bolse%C2%AE-300Mbps-Wireless-N-Micro-Adapter/dp/B00DTZYHX4/ref=sr_1_11?s=pc&ie=UTF8&qid=1396460610&sr=1-11&keywords=usb+wireless+card](http://www.amazon.com/Bolse%C2%AE-300Mbps-Wireless-N-Micro-Adapter/dp/B00DTZYHX4/ref=sr_1_11?s=pc&ie=UTF8&qid=1396460610&sr=1-11&keywords=usb+wireless+card)

or this [http://www.amazon.com/300Mbps-Wireless-Network-802-11n-Adapter/dp/B00CNZW328/ref=sr_1_29?s=pc&ie=UTF8&qid=1396460699&sr=1-29&keywords=usb+wireless+card](http://www.amazon.com/300Mbps-Wireless-Network-802-11n-Adapter/dp/B00CNZW328/ref=sr_1_29?s=pc&ie=UTF8&qid=1396460699&sr=1-29&keywords=usb+wireless+card)

Are the chipsets of these adapters supported by Ubuntu? Particularly 13.10 and then 14.04 when it's released? (I'd like to be able to upgrade to the new LTS this month.)

---

### Post by chili555 on 2014-04-02
I am not sure about either of the devices you linked. However, there is a thread going here about devices that are known to work out of the box. I suggest you check there.

I am thinking it is a hardware issue. You are already using an updated driver:> filename:       /lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
version:        [COLOR="#FF0000"]backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc[/COLOR]If and when you get a new device, I suggest you blacklist ath5k so there is no conflict. Post back if you need guidance.

[http://ubuntuforums.org/showthread.php?t=2166676](http://ubuntuforums.org/showthread.php?t=2166676) What works in 13.04 will work in 13.10 and following.

---

### Post by StealthMode on 2014-04-24
I'll mark this thread Solved, but it was because the dongle I bought from Amazon is what got wireless working. Thanks Chili for your time. The Compaq's fan went kapooey, so that machine is currently un-usable anyway. Got 14.04 installed in the HP, and just made a new thread about something different, haha.

---

### Post by StealthMode on 2014-04-24
solved

---

### Post by varunendra on 2014-04-25
The correct way to mark a thread as [SOLVED] is -

Click on "Thread Tools" link above the top post > click "Mark this thread as solved.."

The "see how" link in my signature below links to a wiki page that shows it with screenshots. :)

---

### Post by StealthMode on 2014-04-25
Thanks Varun.

---

