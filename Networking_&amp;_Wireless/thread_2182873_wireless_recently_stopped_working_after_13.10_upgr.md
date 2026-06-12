---
title: "wireless recently stopped working after 13.10 upgrade"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by pmsolfest on 2013-10-22
I recently upgraded my desktop from 13.04 to 13.10. The wireless was working in 13.04, and when I initially upgraded it worked in 13.10. 
(although the icon in the system tray failed to show up after logging in).
About 2 days ago (I believe this was just after updating packages, although I could be mistaken) my wireless stopped working altogether.

I am using an AirLink101 usb receiver (AWLL6075) and it is using the r8712u driver. Below is all the system information which I could think of as relevant to include:

```

$sudo lsusb
Bus 003 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 008 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$sudo lshw -C Network
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 06
       serial: 90:2b:34:15:46:fe
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdcf8000-fdcfbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:4
       logical name: wlan0
       serial: 00:21:2f:30:91:69
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated


$sudo iwconfig wlan0
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ sudo iwlist wlan0 scan
wlan0     No scan results


$nm-tool
NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             unmanaged
  Default:           no
  HW Address:        00:21:2F:30:91:69


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        90:2B:34:15:46:FE


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


$ iwlist wlan0 frequency
wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

```

After searching through forums for a few days I believe the problem is that for some reason my wireless usb stick has a configuration which includes 'wireless=unassociated',
but I can't figure out how to change this to a standard wifi network.
This is based upon the idea that my laptop indicates that the 'wireless=IEEE 802.11abg'

---

### Post by varunendra on 2013-10-24
Hello pmsolfest, Welcome to the forums !

The "wireless=unassociated" entry is a result, not the cause of its inability to connect. The best you can try with defaults is to try saving all the settings (SSID, BSSID (the MAC address of your access-point), security key with encryption type etc.) in Network Manager, and assign manual IP to the interface. This will work if it is a minor problem.

To get the details of the setup, and possibly find the exact problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by pmsolfest on 2013-10-28
I wasn't 100% sure how to do the first one - I tried manually creating the network profile in network manager and it didn't seem to work.
I ran the script, and the output is below:
```



*************** info trace ***************


***** uname -a *****


Linux solter-Ldesktop 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


***** lsusb *****


Bus 003 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 008 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****




***** lsmod *****


r8712u                184124  0 


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth1 -----------------------------------------------------------------
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


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback


iface wlan0 inet dhcp
  pre-up wpa_supplicant -Bw -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
  post-down killall -q wpa_supplicant


***** iwlist *****


wlan0     No scan results




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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     748939744C6AAC44D12C356
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0bda:0x8172 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:09.0/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   19.362542] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   19.363104] r8712u: Staging version
[   19.363118] r8712u: register rtl8712_netdev_ops to netdev_ops
[   19.363122] usb 3-4: r8712u: USB_SPEED_HIGH with 4 endpoints
[   19.363624] usb 3-4: r8712u: Boot from EFUSE: Autoload OK
[   20.031215] usb 3-4: r8712u: CustomerID = 0x0000
[   20.031226] usb 3-4: r8712u: MAC Address from efuse = <MAC address removed>
[   20.031231] usb 3-4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   23.246869] r8169 0000:03:00.0 eth1: link down
[   23.246912] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.247190] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   27.158509] r8712u 3-4:1.0 wlan0: 1 RCR=0x153f00e
[   27.159355] r8712u 3-4:1.0 wlan0: 2 RCR=0x553f00e
[   27.266265] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.441070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.368264] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.651141] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.034873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

Thanks

---

### Post by varunendra on 2013-10-28
> **pmsolfest said:**
> ```
***** interfaces *****

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
  pre-up wpa_supplicant -Bw -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
  post-down killall -q wpa_supplicant

```

Why are you using the /etc/network/interfaces file for your wifi? Have you done it after the upgrade or before it?

Please remove the extra lines from it so that your wifi is managed by Network Manager again. To do so -
```
sudo sed -i '/auto lo/,+2 !d' /etc/network/interfaces
```
Then check again -
```
cat /etc/network/interfaces
```
There should be only these two lines in the output -
```
auto lo
iface lo inet loopback
```

Can you connect after this? Reboot if required.

---

### Post by pmsolfest on 2013-10-29
I deleted those lines form the interfaces file (I believe they had been changed due to past attempts at making my wireless work a year ago, which eventually succeeded).
Then restarting gave I still had problems (although different this time) connecting to the wifi, described below:


First - the network I need to connect to is my school's WPA2 enterprise network.
At the log-in screen, clicking on the wireless icon and trying to connect led to failure, as it kept looping asking for a password.


Upon logging in, there is no wireless icon in the system tray.
But system settings -> network seems to indicate that it sees the wireless network. (Although this cuts out after about 5 minutes and it doesn't see anything again).
Clicking on the network leads to the network options screen with buttons labeled connect, forget, and settings.
I have gone through the settings and put them at appropriate values (wpa2 enterprise, PEAP, MSCHAPSV2, etc.).
On the network options screen I hit connect, and it doesn't seem to do anything (there is no indication that it is trying to connect and the button returns to its original unpressed stage immediately).


I have attached 2 files generated by the wireless_info.txt script. The FAIL version was produced after the network manager had attempted to connect and then fail to recognize any networks were available. Note that this is nigh identical to the previously posed wireless-info file except the nm-tool has changed from state=unmanaged to state=disconnected.


The standard wireless-info version was produced while network manager could still see the networks.

Furthermore, I am really confused as to why the nm-tool seems to see all the networks, but iwlist scan does not (this is true even if I run them as root independently of the script). If you could shed light on this discrepancy it would be much appreciated.

Thanks for the help.

---

### Post by varunendra on 2013-10-30
> **pmsolfest said:**
> Upon logging in, there is no wireless icon in the system tray.
You mean this icon ? -
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247387&d=1381682098[/IMG]

If yes, that sounds like a broken NM installation. Let's try fixing it first.

Download the required packages beforehand > purge NM > reinstall it from downloaded packages -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
sudo apt-get remove --purge network-manager-gnome network-manager
sudo apt-get install network-manager network-manager-gnome
```
Does it bring the icon back? Post back if not.

In the school, regardless of whether the above brings back the NM icon or not (and assuming NM itself is functional), try connecting to the network (let it fail if it does). When the connection is created and saved, check its 'keyfile' (it's output may contain the security key, so either don't post it here, or obscure it before posting) -
```
sudo cat /etc/NetworkManager/system-connections/*<the connection's Name>*
```
Does it show a line "system-ca-certs=true" among other details ?? If yes, change it to "false" -
```
sudo sed -i '/system-ca-certs/ s:true:false:' /etc/NetoworkManager/system-connections/*<the connection's Name>*
```
Check again with the previous command and try to connect again. Success?

> Furthermore, I am really confused as to why the nm-tool seems to see all the networks, but iwlist scan does not (this is true even if I run them as root independently of the script). If you could shed light on this discrepancy it would be much appreciated.
I'm not very sure about this but nm-tool probably shows 'cached' results, while "iwlist scan" (with sudo) shows the live scanning results.

It is still a bit discomforting that it failed to scan the available access-points after initial failure to connect, but let's try the above solution first that works for most people who need to connect to a network like that.

---

### Post by pmsolfest on 2013-10-30
I tried the re-installation of network manager and the icon still failed to show up. Just for clarification, the missing tray icon is the one associated with the dropdown image shown here (from google - not my screenshot): [IMG]http://www.bournemouth.ac.uk/wireless/local-assets/linux-connect/1.png[/IMG]

In the system-connections file I switched the system-ca-certs flag to false, and the wireless behavior was still the same, not even indicating that it was trying to connect when I hit the 'connect' button.
Also, whenever I used the GUI to adjust settings for the network, the system-ca-certs flag was flipped back to true.

Here is the contents of my system-connections file (I replaced all the local names with ?????, that's not the file being messed up):

```


[ipv6]
method=auto


[connection]
id=???????????
uuid=?????????
type=802-11-wireless


[802-11-wireless]
ssid=????????
mode=infrastructure
mac-address=???????
security=802-11-wireless-security


[802-1x]
eap=peap;
identity=??????
phase2-auth=mschapv2
password-flags=1
system-ca-certs=false


[ipv4]
method=auto


[802-11-wireless-security]
key-mgmt=wpa-eap



```

Historical note of possible relevance: a year ago (or so) I was having issues connecting to this network, and if I recall the solution which finally worked involved installing wicd and modifying some other settings. This was the reason I had previously been using the /etc/network/interfaces file.
Apparently something recently changed in an update which made this workaround fail.
I really have no clue as to whether this may have created some weird settings hidden somewhere messing this up, which is why I mention it. WICD has since been uninstalled and the interface reset as suggested above.

---

### Post by pmsolfest on 2013-11-12
I got it working ... sort of. Here are the details for those of you who are having the same issue:

First thing I did to get it to mostly work is found another wireless usb stick - this one is from cisco.
It uses the driver rt2800usb - and this seems good enough that it will connect (this doesn't work perfectly, but does work good enough to connect and stay connected usually).

as for the nm-applet disappearing from the icon tray - I just needed to add nm-applet to the startup applications.

---

