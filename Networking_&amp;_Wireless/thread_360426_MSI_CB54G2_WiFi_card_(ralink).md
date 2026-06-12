---
title: "MSI CB54G2 WiFi card (ralink)"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by sliwowitz on 2007-02-13
My brother bought a MSI CB54G2 PCMCIA WiFi card, but can't get it to work under linux (no troubles under Windows). It seems, that it should run with the ralink rt2500 drivers.
To make things worse, he is about 700km from home, so I can't tell you exactly what happens overe there, but I will try my best:
- lspci sees the card, iwconfig outputs ra0 RT2500 Wireless along the lines, the card is configurable via system->administration->networking
- It is able to detect an AP and get its ESSID, but always shows 0 signal level
- No networks are by default not visible under the standard network icon in the notification area. They appear only after running the network manager icon from the gnome-nettool package and selecting ra0 there

---

### Post by ukripper on 2007-02-13
Ask him to paste output of iwconfig  here by running **$ sudo iwconfig ** and also ask him to paste contents of the file by typing **$ sudo gedit /etc/network/interfaces**

---

### Post by mozetti on 2007-02-13
Is he using a **smp** kernel? A few months back when I started to get my Ralink 2500 Linksys WiFi card working, the driver developers noted that it didn't work with a **smp** kernel.

For me, it hung the system during boot. They were hoping to overcome this, but I haven't checked back about it.

---

### Post by ukripper on 2007-02-13
There are plenty of factors related to wifi not working. Well If it detects the card and configured alright, it shouldn't have any problems. Still I need to  see iwconfig and /etc/network/interfaces lspci to help him.

still you can ask him to run following:



$ sudo ifdown wlan0
$ sudo ifup wlan0

then using wlassistant or wifiradar configure the available network which should show up in available connections list personally I would use wlassistant.

---

### Post by sliwowitz on 2007-02-18
Here it is:
```
waclar@waclar-laptop:~$ lspci
Password:
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```
```

waclar@waclar-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

waclar@waclar-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface dsl-provider inet ppp
provider dsl-provider

auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```
The ppp section is a remaint of their university network configuration. Actually I see no ra0 there. Should he change the config file, or would it be better, if he made a symlink /dev/wlan0 -> /dev/ra0?

---

### Post by ukripper on 2007-02-19
> **sliwowitz said:**
> Here it is:
```
waclar@waclar-laptop:~$ lspci
Password:
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```
```

waclar@waclar-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

waclar@waclar-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface dsl-provider inet ppp
provider dsl-provider

auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```
The ppp section is a remaint of their university network configuration. Actually I see no ra0 there. Should he change the config file, or would it be better, if he made a symlink /dev/wlan0 -> /dev/ra0?



You can ask him to go in network settings and configure ra0 from there using ESSID and WEP KEY or else ask him to use interfaces files to configure ra0.

After enabling ra0, ask him to download wlassistant to see available networks and configure them from there

---

### Post by sliwowitz on 2007-02-22
Even if he does configure the interface to ra0 in network settings, all APs always show 0 signal level. He didn't try with the alternative gui tools yet, because it's difficult to install without direct access to internet (and he's no tech-type). I hope, he will manage to install wifi-radar.
Meanwhile, do you know about any tools which should be already installed and could help us to find what's going on?

---

### Post by sliwowitz on 2007-03-06
Last weekend, I visited my brother in Italy, we got a great time skiing and wine drinking and by the way, I fixed his Ubuntu laptop.
From what I've learned in Ubuntu forums and bugzilla, rt2500 drivers with this particular card don't work in Edgy and probably won't work in Fiesty, so I gave ndiswrapper (with XP drivers from the MSI website) a try and it worked great. Altough I personally prefer native opensource drivers, I was almost impressed by the simplicity of the installation and the fact that windows drivers can really make that thing work in Linux. The only trouble is, that the computer hangs on boot if the card is inserted. Fortunately it's a PCMCIA, so there's a simple workaround - you can insert it after Ubuntu has finished the boot process.
I also installed wifi-radar on the machine, for it has no big dependencies (kdelibs...) and the machine is short on disk space. Its ability to run a command after connecting is great, for it simplifies the weird "ppp over wireless" network setup they have at the University of Trento.

---

