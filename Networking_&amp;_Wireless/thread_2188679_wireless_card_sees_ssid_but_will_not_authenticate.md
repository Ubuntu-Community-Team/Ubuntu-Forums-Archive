---
title: "wireless card sees ssid but will not authenticate"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by Dave_Norvell on 2013-11-18
Issue=Wireless nic sees ssid but I am unable authenticate from Dell/Ubuntu laptop.  When I try to connect wirelessly, Wi-Fi Network Authentication Required window pops up, I verify password and click Connect, the window closes then re-opens immediately requesting authentication.
When I plugged the USB nic into WinXP desktop PC it authenticates with network OK.  

Hardware=Dell Inspiron 2200 laptop, LB-Link 150mbps usb wireless card, Linksys wrt160nl wireless router (MAC address filtering disabled)
OS=Ubuntu 13.10

Below is output from lsusb, lshw, & iwlist.
Please let me know if more info is required.
thanks



~$ lsusb
Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter


~$ sudo lshw -C network
[sudo] password for owner: 
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:ef:70:9e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.0.109 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfdff000-dfdfffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan0
       serial: 48:02:2a:c4:2e:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.12.0-031200-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn


~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:D6:76:49
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:on
                    ESSID:"SerenityNow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001736e96
                    Extra: Last beacon: 20020ms ago
                    IE: Unknown: 000B536572656E6974794E6F77
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD770050F204104A0001101044000102103B000103104700100656C66666760656C666667626A61676102100104C696E6B73797320627920436973636F102300085752543136304E4C1024000876312E30302E30311042000231371054000800060050F2040001101100085752543136304E4C100800020084
                    IE: Unknown: DD0A00037F04010000000000

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2013-11-19
Try pure WPA2-AES (CCMP) encryption, check the router manual

---

### Post by Dave_Norvell on 2013-11-19
Thanks for the suggestion.  Unfortunately, after adjusting the encryption on the router from "AES or TKIP" to "AES", I am still getting the Wi-Fi Network Authentication Required window and it's not connecting.

---

### Post by praseodym on 2013-11-19
Why is kernel 3.12 in use? 13.10 ships kernel 3.11 per default. Driver update for 3.11 via
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.7
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. I dont know if this driver works with 3.12. Feel free to try it.

---

### Post by Dave_Norvell on 2013-11-22
This laptop was a gift so I don't know why the kernel is 3.12.  I loaded the 13.10 demo and lshw -C network indicates that the 3.11 kernel was used.  I got the same results from the usb wireless card (i.e. it keeps asking for authentication).  I'm thinking that since this is somewhat of an offbrand NIC I want to go to the HCL and pick a listed card from it to purchase.  Any recomendations for a known working USB network card would be greatly appreciated.

---

### Post by praseodym on 2013-11-22
Check if other kernels are installed:
```

dpkg -l linux-image-* | grep ii
```

---

### Post by Dave_Norvell on 2013-11-22
~$ dpkg -l linux-image-* | grep ii
dpkg-query: no packages found matching linux-image-3.11.4-031104-generic_3.11.4-031104.201310081221_i386.deb
dpkg-query: no packages found matching linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_i386.deb
dpkg-query: no packages found matching linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_i386.deb.1

---

### Post by praseodym on 2013-11-22
Reboot and press the SHIFT button during boot-up. In the GRUB bootloader choose "previous ubuntu versions" and there kernel 3.11. With this one you can install the driver named above

---

### Post by Dave_Norvell on 2013-11-22
output from driver installation:

~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-3.11.4-031104-generic is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic
  linux-image-extra-3.11.0-12-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 13 not upgraded.
Need to get 0 B/7,873 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 267421 files and directories currently installed.)
Preparing to replace build-essential 11.6ubuntu5 (using .../build-essential_11.6ubuntu5_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1.1ubuntu4 (using .../dkms_2.2.0.3-1.1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace git 1:1.8.3.2-1 (using .../git_1%3a1.8.3.2-1_i386.deb) ...
Unpacking replacement git ...
Preparing to replace linux-headers-generic 3.11.0.13.14 (using .../linux-headers-generic_3.11.0.13.14_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.6ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu4) ...
Setting up git (1:1.8.3.2-1) ...
Setting up linux-headers-generic (3.11.0.13.14) ...


:~$ sudo dkms add ./rtl8192cu-fixes
Error! Could not find module source directory.
Directory: /usr/src/.-rtl8192cu-fixes does not exist.


~$ sudo dkms install 8192cu/1.7
Error! Could not find module source directory.
Directory: /usr/src/8192cu-1.7 does not exist.

---

### Post by Dave_Norvell on 2013-11-22
output from lshw:

~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:ef:70:9e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.0.109 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfdff000-dfdfffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan0
       serial: 48:02:2a:c4:2e:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.12.0-031200-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

---

### Post by praseodym on 2013-11-23
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.7
```
?!

---

### Post by kurt18947 on 2013-11-23
Dave

I too have had good success with the fix praseodym recommends.  If you do not, I can recommend a couple 'plug -n- play adapters/chipsets. One is Netgear WNA1100 using an Atheros 9271 (I think) chipset.  I plug it into a new install and it just works.  Another alternative is an Ebay generic adapter using a Ralink/Mediatek RT5370 chipset.  It has been plug 'n' play since about 12.10.  The downside to the 5370 using the built-in driver is that range/signal strength are not very strong in my experience.  I have the nano adapter, a 5370 device using an external antenna might be much better, don't know.

---

### Post by Dave_Norvell on 2013-11-23
WOOHOO! SUCCESS!

Here's the resolution for future generations:

changed kernel from 3.12 to 3.11 (not sure if this is necessary)
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | tee -a /etc/modprobe.d/blacklist.conf
reboot


MANY THANKS TO PRASEODYM for PATIENCE and PERSEVERENCE!!!

---

