---
title: "Failed to initialize interface 'wlan0' with reaver"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by SageOfSmeg on 2014-03-20
I want to move my PC to another location in my home that cannot easily be connected to a wired connection, so I purchased a basic wireless USB adapter (just to test my WiFi connectivity). 

Now I want to test my WiFi security and vulnerability and have be reading up on reaver[COLOR=#ff0000]*[/COLOR], etc.

[RIGHT]([COLOR=#ff0000]*[/COLOR] I want to test/hack my own network, not anybody else’s cos it’s illegal, I know)
[/RIGHT]
 
 
I have managed to get the wireless USB adapter working just fine under Windows XP (so I know that the adapter works), but in Linux I am having problems and need some help please.

Adapter Details:
B-Link Wireless N USB Adapter
Model: BL-LW06-AR
(product details: [http://www.lefen.com/index.php/products/view?pid=84](http://www.lefen.com/index.php/products/view?pid=84))
MAC Address: 44:33:4C:61:5E:41
(Driver ref: Realtek RTL8191SU)
 
I have also downloaded the latest Linux driver:
   Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2
   Version: 2.6.6.0.20120403
   Updated: 2012/5/15
   File Size: 4880k
   Download Site: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU)
   Downloaded file name: RTL819xSU_usb_linux_v2.6.6.0.20120405.zip
**This has NOT been installed yet!** I will need help with the driver installation if necessary later on.

For reference...
Wireless AP: ZyXEL Model WAP3205
  - Operating Channel: Channel-09 2452MHz
  - Security Mode: WPA2-PSK 
  - 802.11 Mode: 802.11b/g
  - WPS: Configured, WPS disabled
This has SSID broadcast switched off for extra security against a typical external user.
 
 
For information, I’ve checked and have the following installed:
- linux-headers-3.5.0-47
- build-essential (installed version 11.5ubuntu2.1)

If I use the Network manager under Ubuntu I can manually enter my SSID, WPA PSK, etc. and can connect via the USB adapter, so I know that it does definitely work under Ubuntu.
```
gjd@gjdpc2:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"SageOfSmegHomeNet"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.452 GHz  Access Point: CC:5D:4E:4D:44:C4  
          Bit Rate:54 Mb/s   Sensitivity:0/0 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I can then disconnect from within Network manager.

Now, I have tried using reaver in both the "Backtrack 5 Live CD" and native Ubuntu 12.04.4.
I get the same result. Using reaver I cannot see my Wireless connection, or rather reaver cannot access it.

```
gjd@gjdpc2:~$ reaver -i wlan0 -b CC:5D:4E:4D:44:C4 -vv -t 1 -d 0 --ignore-locks
 
Reaver v1.4 WiFi Protected Setup Attack Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>
 
[-] Failed to initialize interface 'wlan0'
[-] Failed to recover WPA key
[+] Nothing done, nothing to save.
```
 
and
 
```
gjd@gjdpc2:~$ iwconfig wlan0
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I understand that I have to first put the wireless card (USB) into monitor mode using:
```
airmon-ng start wlan0   (I’ve also tried this with sudo)
and it comes up with the line
Interface          Chipset                        Driver
```
but no details shown under these headings.
 
Also, for reference...

```
gjd@gjdpc2:~$ iw wlan0 info
nl80211 not found.

``` 

```
gjd@gjdpc2:~$ iw dev wlan0 link
nl80211 not found.

``` 

```
gjd@gjdpc2:~$ iw dev wlan0 scan
nl80211 not found.

``` 

```
gjd@gjdpc2:~$ ip link set wlan0 up
RTNETLINK answers: Operation not permitted

``` 

```
gjd@gjdpc2:~$ lsusb
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` 

```
gjd@gjdpc2:~$ dmesg | grep usbcore
[    0.144157] usbcore: registered new interface driver usbfs
[    0.144182] usbcore: registered new interface driver hub
[    0.144230] usbcore: registered new device driver usb
[    0.638350] usbcore: registered new interface driver libusual
[  644.670896] usbcore: registered new interface driver r8712u

``` 

```
gjd@gjdpc2:~$ sudo lshw -c network
  *-network              
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:11:d8:f1:9b:86
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.15-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:cfee0000-cfefffff ioport:c800(size=32)
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 13
       serial: 00:11:d8:f1:9f:70
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full ip=192.168.1.10 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:cfcfc000-cfcfffff ioport:a800(size=256) memory:cfcc0000-cfcdffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 44:33:4c:61:5e:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u wireless=unassociated

``` 
 
From what I can determine, the USB adapter can be seen sometimes, but not others, or not via certain commands.
I am mystified and need guidance?


---
Hardware Specs: dual boot Ubuntu 12.04.4, Windows X SP3
Home PC
UK based

---

### Post by SageOfSmeg on 2014-03-27
Following suggestions at answers.launchpad.net, changing the wireless transmission channel to channel 5 made no  difference. I suspect it is due to the unknown/obscure chipset and/or  driver setup for this device, so I am abandoning it in favour of an  internal PCI Express card.

I don't believe it is worth spending any more of my time trying to get this USB adapter to work the way I need it. 
[COLOR=#ff0000]**Unsolved but closed.**[/COLOR]

---

