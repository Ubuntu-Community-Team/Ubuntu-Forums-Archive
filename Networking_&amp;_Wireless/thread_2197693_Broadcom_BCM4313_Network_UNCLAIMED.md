---
title: "Broadcom BCM4313: Network UNCLAIMED"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by 13718484207 on 2014-01-05
I have a problem on wireless network connection. I am using ubuntu 13.10.There are some infomation about my issue followed.
[COLOR=#a52a2a]1. sudo lshw -C network
[/COLOR]
     ```
*-network                      description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: c1
       serial: 0a:89:d3:0f:dd:3d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=10.18.28.60 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fe900000-fe93ffff ioport:d000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:15:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe800000-fe803fff2

```
  [COLOR=#800000]2.  lspci | grep Broadcom[/COLOR]
       15:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

  **Many thanks!**

---

### Post by praseodym on 2014-01-05
Hi,

install the missing firmware
```

sudo apt-get install linux-firmware-nonfree
```

---

### Post by varunendra on 2014-01-05
Welcome to the forums !

Please also check if the native driver "brcmsmac" is blacklisted (probably by a faulty installation/removal attempt of the sta driver "wl") -
```
grep -R brcm /etc/modprobe.d
```
If you see lines like "blacklist brcmsmac" or "blacklist bcma" etc., either remove those files/entries, or post back the output here if unsure.

If nothing comes up in the above output, and you are still unable to connect, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by 13718484207 on 2014-01-09
I am sorry to reply to you these late.
I have try the method.I install it but it is useless.

---

### Post by coffeecat on 2014-01-09
> **13718484207 said:**
> I am sorry to reply to you these late.
I have try the method.I install it but it is useless.

@13718484207, that is so vague that it doesn't help those trying to help you. Did you see this in varunendra's post?...

> **varunendra said:**
> If nothing comes up in the above output, and you are still unable to connect, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Run the wireless script and then post the report. It will give the information people need to be able to help you. The BCM4313 wireless device should work out of the box in 13.10 with the default brcmsmac driver, so it's possible an attempt at installing one of the other Broadcom drivers is the problem here. Please also run this terminal command that varunendra posted...

> **varunendra said:**
> ```
grep -R brcm /etc/modprobe.d
```

... and post the output, **whatever** it says, even an error message if that is what you get.

---

### Post by 13718484207 on 2014-01-09
I have ran the script posted by varunendra, The output contains "[COLOR=#000000]blacklist brcmsmac" and "blacklist bcma",then I comment these lines in the conf file and reboot my computer, but I also can not connect to the wireless.
A few days ago,I can connect to the wireless, but when I update my kernel, I can not connect to the wireless.Now I will try the wireless scripts. 
I am a freshman in ubuntu,thank you![/COLOR]

---

### Post by 13718484207 on 2014-01-09
I am sorry that I can not connect to the website [COLOR=#000000][FONT=Ubuntu Mono]http://dl.dropbox.com/u/57264241/wireless_script. can you send the script to me,thank you.[/FONT][/COLOR]

---

### Post by varunendra on 2014-01-09
> **13718484207 said:**
> I am sorry that I can not connect to the website [COLOR=#000000][FONT=Ubuntu Mono]http://dl.dropbox.com/u/57264241/wireless_script. can you send the script to me,thank you.[/FONT][/COLOR]

Attached.

Please download the attachment > copy it to your desktop > right-click > "Extract here".

Then open a terminal, and run this command to run it -
```
Desktop/wireless_script
```

It will finish with a message "Results saved in "wireless-info.txt". Post the contents of this file (created on your desktop) or attach the report in your next post.

---

### Post by 13718484207 on 2014-01-11
The content in the wireless-info show as follows:
```


*************** info trace ***************


***** uname -a *****


Linux zengping-Inspiron-M4010 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


14:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Dell Device [1028:046f]
	Kernel driver in use: atl1c
15:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]


***** lsusb *****


Bus 003 Device 003: ID 0c45:6422 Microdia 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 109b:90c8  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1bcf:0501 Sunplus Innovation Technology Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.18.28.70
    Prefix:          16 (255.255.0.0)
    Gateway:         10.18.0.254


    DNS:             8.8.8.8


  IPv6 Settings:
    Address:         2001:cc0:2026:4018:8436:65d3:b014:45e8
    Prefix:          64
    Gateway:         fe80::225:90ff:fe63:8468


    Address:         2001:cc0:2026:4018:585d:b3ff:fe1d:fb4e
    Prefix:          64
    Gateway:         fe80::225:90ff:fe63:8468


    Address:         2001:470:f822:d0:8436:65d3:b014:45e8
    Prefix:          64
    Gateway:         fe80::225:90ff:fe63:8468


    Address:         2001:470:f822:d0:585d:b3ff:fe1d:fb4e
    Prefix:          64
    Gateway:         fe80::225:90ff:fe63:8468


    Address:         fe80::585d:b3ff:fe1d:fb4e
    Prefix:          64
    Gateway:         fe80::225:90ff:fe63:8468








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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist ssb


***** modinfo *****




***** udev rules *****


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"




***** dmesg *****




****************** done ******************



```
The file is also in the attachment.
Thank you so much!

---

### Post by praseodym on 2014-01-11
Download the following file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
```
Clean up the blacklists:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Error messages are Ok. Reboot.

---

### Post by 13718484207 on 2014-01-11
Thank you very much! I can connect to the wireless now!

---

### Post by 13718484207 on 2014-05-10
Hi praseodym, I have another question, recently i change my computer which is thinkpad T440, It has the similar problem. thank you!
```

  *-network
       description: Ethernet interface
       product: Ethernet Connection I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 28:d2:44:50:bd:42
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.6-4 ip=10.201.3.207 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:59 memory:f1600000-f161ffff memory:f163e000-f163efff ioport:5080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: RTL8192EE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:f1400000-f1403fff

```

And run the script wireless_script , I get such result.
```


*************** info trace ***************
***** uname -a *****
Linux zengping-ThinkPad-T440 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
***** lsb_release *****
Distributor ID:    UbuntuDescription:    Ubuntu 14.04 LTSRelease:    14.04Codename:    trusty
***** lspci *****
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)    Subsystem: Lenovo Device [17aa:2214]    Kernel driver in use: e1000e--03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]04:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
***** lsusb *****
Bus 001 Device 002: ID 8087:8000 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 002 Device 004: ID 5986:0268 Acer, Inc Bus 002 Device 003: ID 0bda:8761 Realtek Semiconductor Corp. Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
***** PCMCIA Card Info *****

***** iwconfig *****

***** rfkill *****
0: tpacpi_bluetooth_sw: Bluetooth    Soft blocked: no    Hard blocked: no1: hci0: Bluetooth    Soft blocked: no    Hard blocked: no
***** lsmod *****

***** nm-tool *****
NetworkManager Tool
State: connected (global)
- Device: eth0  [Wired connection 1] -------------------------------------------  Type:              Wired  Driver:            e1000e  State:             connected  Default:           yes  HW Address:        <MAC address removed>
  Capabilities:    Carrier Detect:  yes    Speed:           100 Mb/s
  Wired Properties    Carrier:         on
  IPv4 Settings:    Address:         10.201.3.207    Prefix:          27 (255.255.255.224)    Gateway:         10.201.3.193
    DNS:             10.3.9.4    DNS:             10.3.9.5    DNS:             10.3.9.6    DNS:             10.3.9.7
  IPv6 Settings:    Address:         2001:da8:215:c11e:b477:89f:63e5:f1d7    Prefix:          64    Gateway:         fe80::223:89ff:fe56:d491
    Address:         2001:da8:215:c11e:2ad2:44ff:fe50:bd42    Prefix:          64    Gateway:         fe80::223:89ff:fe56:d491
    Address:         fe80::2ad2:44ff:fe50:bd42    Prefix:          64    Gateway:         fe80::223:89ff:fe56:d491



***** NetworkManager.state *****[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true
***** NetworkManager.conf *****
[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq
[ifupdown]managed=false
***** interfaces *****
# interfaces(5) file used by ifup(8) and ifdown(8)auto loiface lo inet loopback
***** iwlist *****

***** resolv.conf *****
nameserver 127.0.1.1search bupt.edu.cn
***** blacklist *****
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci
[/etc/modprobe.d/blacklist.conf]blacklist evbugblacklist usbmouseblacklist usbkbdblacklist eepro100blacklist de4x5blacklist eth1394blacklist snd_intel8x0mblacklist snd_aw2blacklist i2c_i801blacklist prism54blacklist bcm43xxblacklist garmin_gpsblacklist asus_acpiblacklist snd_pcspblacklist pcspkrblacklist amd76x_edac
[/etc/modprobe.d/fbdev-blacklist.conf]blacklist arkfbblacklist aty128fbblacklist atyfbblacklist radeonfbblacklist cirrusfbblacklist cyber2000fbblacklist gx1fbblacklist gxfbblacklist kyrofbblacklist matroxfb_baseblacklist mb862xxfbblacklist neofbblacklist nvidiafbblacklist pm2fbblacklist pm3fbblacklist s3fbblacklist savagefbblacklist sisfbblacklist tdfxfbblacklist tridentfbblacklist viafbblacklist vt8623fb
***** modinfo *****

***** udev rules *****
# PCI device 0x8086:0x1559 (e1000e)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
***** dmesg *****
[   13.737027] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
****************** done ******************

```

---

### Post by praseodym on 2014-05-11
You need this driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot. The "ee" driver is also inside.

---

