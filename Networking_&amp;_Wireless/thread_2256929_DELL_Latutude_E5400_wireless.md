---
title: "DELL Latutude E5400 wireless"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by atfleg on 2014-12-15
Hi, I have a Dell laptop running lubuntu 14.04.01 and after an upgrade I got the following error on startup:
[COLOR=#000000][FONT=Verdana][TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3[/TD]
[TD="class: code"][COLOR=#000000][  557.664914] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
[  557.664919] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
[  557.664921] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[URL="http://paste.ubuntu.com/9533890/plain/"]
[/URL]
At some point I must have switched off teh wifi hardware switch (Doh) and attempted to follow these instructions.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers)

Still no wifi - then switch it back on! - still no wifi. 

Then saw this:

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) 

ran 
lspci -nn -d 14e4:

and got 

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


So tried 

sudo apt-get install bcmwl-kernel-source

and rebooted, still no wifi...now confused.

Anyone any suggestions? Output from wireless script below

   ```
########## wireless info START ########## 

Report from: 15 Dec 2014 23:29 GMT +0000 

Booted last: 15 Dec 2014 23:06 GMT +0000 

Script from: 20 Sep 2014 23:04 UTC +0000 

##### release ########################### 

Distributor ID:	Ubuntu Description:	Ubuntu 14.04.1 LTS Release:	14.04 Codename:	trusty 

##### kernel ############################ 

Linux 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12
18:02:44 UTC 2013 i686 i686 i686 GNU/Linux 

Parameters: ro, quiet, splash, vt.handoff=7 

##### desktop ########################### 

Lubuntu 

##### lspci ############################# 

09:00.0 Ethernet controller [0200]: Broadcom
Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express
[14e4:1674] 	Subsystem: Dell Device [1028:0262] 	Kernel driver in use: tg3 

0c:00.0 Network controller [0280]: Broadcom
Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b]
(rev 01) 	Subsystem: Dell Wireless 1510 Wireless-N WLAN
Mini-Card [1028:000d] 

##### lsusb ############################# 

Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 008 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 007 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub 

##### PCMCIA card info ################## 

'pccardctl' is not installed (package
"pcmciautils"). 

##### rfkill ############################ 

##### lsmod ############################# 

dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi dell_laptop            17161  0 
dcdbas                 14021  1 dell_laptop wmi                    18590  1 dell_wmi 

##### interfaces ######################## 

auto lo iface lo inet loopback 

##### ifconfig ########################## 

eth0      Link encap:Ethernet  HWaddr <MAC
'eth0' [IF]>  
          inet addr:192.168.1.65 
Bcast:192.168.1.255  Mask:255.255.255.0           inet6 addr:
fe80::223:aeff:fe11:4c8c/64 Scope:Link           UP BROADCAST RUNNING MULTICAST 
MTU:1500  Metric:1           RX packets:9254 errors:0 dropped:0
overruns:0 frame:0           TX packets:8178 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:5742754 (5.7 MB)  TX
bytes:1259751 (1.2 MB)           Interrupt:16 


##### iwconfig ########################## 

lo        no wireless extensions. 

eth0      no wireless extensions. 

##### route ############################# 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 0.0.0.0         192.168.1.254   0.0.0.0        
UG    0      0        0 eth0 192.168.1.0     0.0.0.0         255.255.255.0  
U     1      0        0 eth0 

##### resolv.conf ####################### 

nameserver 127.0.1.1 search home 

##### nm-tool ########################### 

NetworkManager Tool 

State: connected (global) 

- Device: eth0  [Wired connection 1]
-------------------------------------------   Type:              Wired   Driver:            tg3   State:             connected   Default:           yes   HW Address:        <MAC 'eth0' [IF]> 

  Capabilities:     Carrier Detect:  yes     Speed:           100 Mb/s 

  Wired Properties     Carrier:         on 

  IPv4 Settings:     Address:         192.168.1.65     Prefix:          24 (255.255.255.0)     Gateway:         192.168.1.254 

    DNS:             192.168.1.254 

##### NetworkManager.state ############## 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ############### 

[main] plugins=ifupdown,keyfile,ofono dns=dnsmasq 

[ifupdown] managed=false 

##### NetworkManager profiles ########### 

[[/etc/NetworkManager/system-connections/ph1-3-office]]
(600 root) [connection] id=ph1-3-office |
type=802-11-wireless [802-11-wireless] ssid=ph1-3-office |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/familylaptop]]
(600 root) [connection] id=familylaptop |
type=802-11-wireless [802-11-wireless] ssid=familylaptop |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/virginmedia5125668]]
(600 root) [connection] id=virginmedia5125668 |
type=802-11-wireless [802-11-wireless] ssid=virginmedia5125668 |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/PlusnetWireless38FEFD]]
(600 root) [connection] id=PlusnetWireless38FEFD |
type=802-11-wireless [802-11-wireless] ssid=PlusnetWireless38FEFD |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/HOTSPOT]]
(600 root) [connection] id=HOTSPOT | type=802-11-wireless [802-11-wireless] ssid=HOTSPOT |
mac-address=<MAC address> [ipv6] method=auto [ipv4] method=auto 

[[/etc/NetworkManager/system-connections/ph0-1-off]]
(600 root) [connection] id=ph0-1-off | type=802-11-wireless [802-11-wireless] ssid=ph0-1-off |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/virgintrainswifi]]
(600 root) [connection] id=virgintrainswifi |
type=802-11-wireless [802-11-wireless] ssid=virgintrainswifi |
mac-address=<MAC address> [ipv6] method=auto [ipv4] method=auto 

[[/etc/NetworkManager/system-connections/BTHomeHub2-N5S9]]
(600 root) [connection] id=BTHomeHub2-N5S9 |
type=802-11-wireless [802-11-wireless] ssid=BTHomeHub2-N5S9 |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/BTHomeHub2-Q7W8]]
(600 root) [connection] id=BTHomeHub2-Q7W8 |
type=802-11-wireless [802-11-wireless] ssid=BTHomeHub2-Q7W8 |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/SKY0E92C]]
(600 root) [connection] id=SKY0E92C | type=802-11-wireless [802-11-wireless] ssid=SKY0E92C |
mac-address=<MAC address> [ipv4] method=auto [ipv6] method=auto 

[[/etc/NetworkManager/system-connections/pybushomesecurity]]
(600 root) [connection] id=pybushomesecurity |
type=802-11-wireless [802-11-wireless] ssid=pybushomesecurity |
mac-address=<MAC address> [ipv6] method=auto [ipv4] method=auto 

##### iw reg get ######################## 

'iw' is not installed (package "iw"). 

##### iwlist channels ################### 

lo        no frequency information. 

eth0      no frequency information. 

##### iwlist scan ####################### 

lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

##### module infos ###################### 

##### module parameters ################# 

##### /etc/modules ###################### 

loop lp 

##### modprobe options ################## 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist-bcm43.conf] blacklist b43 blacklist b43legacy blacklist ssb blacklist bcm43xx blacklist brcm80211 blacklist brcmfmac blacklist brcmsmac blacklist bcma 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac 

[/etc/modprobe.d/blacklist-rare-network.conf] alias net-pf-3 off alias net-pf-6 off alias net-pf-9 off alias net-pf-11 off alias net-pf-12 off alias net-pf-19 off alias net-pf-21 off alias net-pf-36 off 

[/etc/modprobe.d/iwlwifi.conf] remove iwlwifi \ (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e
^iwlwifi | xargs /sbin/rmmod) \ && /sbin/modprobe -r mac80211 

[/etc/modprobe.d/libpisock9.conf] blacklist visor 

[/etc/modprobe.d/mlx4.conf] softdep mlx4_core post: mlx4_en 

##### rc.local ########################## 

exit 0 

##### pm-utils ########################## 

##### udev rules ######################## 

[/etc/udev/rules.d/70-persistent-net.rules] # PCI device
0x14e4:/sys/devices/pci0000:00/0000:00:1c.4/0000:09:00.0 (tg3) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" # PCI device
0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (wl) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth1" # PCI device 0x14e4:0x432b (b43) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="wlan*", NAME="wlan0" 

##### dmesg ############################# 

########## wireless info END ############
```

---

### Post by chili555 on 2014-12-15
With a temporary internet connection, open a terminal and run:```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Reboot. If the wireless isn't working, post:```
rfkill list all
dmesg | grep -e wlan -e wl
```

---

### Post by atfleg on 2015-01-03
when i run "sudo modprobe wl" I get
modprobe: FATAL: Module wl not found.

when i type ```
rfkill list all
dmesg | grep -e wlan -e wl
```

in terminal nothing happens!

anyone help?

---

### Post by chili555 on 2015-01-03
> **atfleg said:**
> when i run "sudo modprobe wl" I get
modprobe: FATAL: Module wl not found.

when i type ```
rfkill list all
dmesg | grep -e wlan -e wl
```

in terminal nothing happens!

anyone help?Were there any errors or warnings at:```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```Please show us.

---

### Post by atfleg on 2015-01-03
nope no errors.

i should have also said i've upgrade to 14.10 as well

wireless script output:

```
   ########## wireless info START ##########

Report from: 03 Jan 2015 16:13 GMT +0000

Booted last: 03 Jan 2015 14:01 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12 18:02:44 UTC 2013 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
	Subsystem: Dell Device [1028:0262]
	Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14021  1 dell_laptop
wmi                    18590  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe11:4c8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34026734 (34.0 MB)  TX bytes:3039291 (3.0 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ph1-3-office]] (600 root)
[connection] id=ph1-3-office | type=802-11-wireless
[802-11-wireless] ssid=ph1-3-office | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/familylaptop]] (600 root)
[connection] id=familylaptop | type=802-11-wireless
[802-11-wireless] ssid=familylaptop | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/virginmedia5125668]] (600 root)
[connection] id=virginmedia5125668 | type=802-11-wireless
[802-11-wireless] ssid=virginmedia5125668 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PlusnetWireless38FEFD]] (600 root)
[connection] id=PlusnetWireless38FEFD | type=802-11-wireless
[802-11-wireless] ssid=PlusnetWireless38FEFD | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOTSPOT]] (600 root)
[connection] id=HOTSPOT | type=802-11-wireless
[802-11-wireless] ssid=HOTSPOT | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ph0-1-off]] (600 root)
[connection] id=ph0-1-off | type=802-11-wireless
[802-11-wireless] ssid=ph0-1-off | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/virgintrainswifi]] (600 root)
[connection] id=virgintrainswifi | type=802-11-wireless
[802-11-wireless] ssid=virgintrainswifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BTHomeHub2-N5S9]] (600 root)
[connection] id=BTHomeHub2-N5S9 | type=802-11-wireless
[802-11-wireless] ssid=BTHomeHub2-N5S9 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHomeHub2-Q7W8]] (600 root)
[connection] id=BTHomeHub2-Q7W8 | type=802-11-wireless
[802-11-wireless] ssid=BTHomeHub2-Q7W8 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKY0E92C]] (600 root)
[connection] id=SKY0E92C | type=802-11-wireless
[802-11-wireless] ssid=SKY0E92C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pybushomesecurity]] (600 root)
[connection] id=pybushomesecurity | type=802-11-wireless
[802-11-wireless] ssid=pybushomesecurity | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

loop
lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.4/0000:09:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x432b (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by chili555 on 2015-01-03
> Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12 18:02:44 UTC 2013 i686 i686 i686 GNU/Linux
Whaaaaat?? How is it that you are running an old 3.8.0-xx kernel in Ubuntu 14.10? I have:```
chili@T410:~$ uname -r
3.[COLOR="#FF0000"]16[/COLOR].0-28-generic
```What would you like to confess to the Doc under strict doctor-patient confidentiality?

---

### Post by atfleg on 2015-01-03
I'm not entirely sure I understand the question, and I'm entirely unsure how I may have done it! 

I'd consider myself a bit of a noobie to lubuntu but have tried mucking about with some bits that are entirely beyond my ken! 
Any idea how I might have done it and how I might undo it?

---

### Post by chili555 on 2015-01-03
How exactly did you install 14.10? An upgrade from an earlier version, no doubt? Does 3.16.0-xx exist on your system?```
sudo updatedb
locate linux-image | grep 3.16
```Have you done all required reboots? Would you do one now and show us:```
uname -r
```

---

### Post by atfleg on 2015-01-04
user@user-Latitude-E5400:~$ uname -r
3.8.0-34-generic

---

### Post by chili555 on 2015-01-04
> **atfleg said:**
> user@user-Latitude-E5400:~$ uname -r
3.8.0-34-genericAnd how about my other questions?

---

### Post by atfleg on 2015-01-04
yup upgraded from 14.04 I guess, i think i got the lap top about a year ago an installed 13.10 then upgraded.

i ran those two commands and nothing happened.

---

### Post by chili555 on 2015-01-04
I suppose it is possible that the previous owner of the laptop placed a hold on the linux-image so it would never be updated. Crazy, I know, but I have seen worse! Let's check:```
sudo dpkg --get-selections | grep linux-image
```If any are marked 'hold,' then let's fix it:```
echo "linux-image-XXX install" | sudo dpkg --set-selections
```...where XXX is the latest 3.16 you found, ideally 3.16.0-28-generic. Then update:```
sudo apt-get update
```And reboot. Confirm you are now running the latest 14.10 kernel:```
uname -r
```Next, reinstall the Broadcom driver:```
sudo apt-get install --reinstall bcmwl-kernel-source
```If nothing is held, then we have a bigger issue to unravel!

Please show:```
sudo dpkg -s bcmwl-kernel-source | head -n9
lsb_release -d
```Thanks.

---

### Post by atfleg on 2015-01-05
here's what i get doing teh first and last commands

```
user@user-Latitude-E5400:~$ sudo dpkg --get-selections | grep linux-image
[sudo] password for user: 
linux-image-3.11.0-14-generic            deinstall
linux-image-3.8.0-19-generic            deinstall
linux-image-3.8.0-34-generic            install
linux-image-extra-3.11.0-14-generic        deinstall
linux-image-extra-3.8.0-19-generic        deinstall
linux-image-extra-3.8.0-34-generic        install
user@user-Latitude-E5400:~$ sudo dpkg -s bcmwl-kernel-source | head -n9
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 6966
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu1
user@user-Latitude-E5400:~$ lsb_release -d
Description:    Ubuntu 14.10
user@user-Latitude-E5400:~$ 


```
None are parked hold, and none are 3.16.xxx

It was me who installed lubuntu - the machine had windows XP on it when i got it. As i say I have messed about with a few things!

Thanks for all your help with this - should I just wipe the machine and start again? Or can it be uravelled.

Oh and I have two network icons on the bottom right hand corner when before upgrading to 14.10 I only had 1!

---

### Post by chili555 on 2015-01-05
The last time I installed fresh, it took just about 15 minutes. After a thorough back-up, that's what I'd do.

---

### Post by atfleg on 2015-01-10
hi again!

so a reinstall later and still no wi-fi - which is pain because I had wi-fi when i was running 14.04 previously.

 I do now have a wi-fi connection, I can see the network just can't connect to it!

wi-fi script output:

```

########## wireless info START ##########

Report from: 10 Jan 2015 20:46 GMT +0000

Booted last: 10 Jan 2015 20:37 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
    Subsystem: Dell Device [1028:0262]
    Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
wl                   3999690  0 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
wmi                    18673  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe11:4c8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2360828 (2.3 MB)  TX bytes:149693 (149.6 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::224:2bff:fe78:28ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BTHomeHub2-Q7W8: Infra, <MAC 'BTHomeHub2-Q7W8' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWiFi:          Infra, <MAC 'BTWiFi' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=BTHomeHub2-Q7w8
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BTWiFi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-11 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
          Cell 02 - Address: <MAC 'BTWiFi-with-FON' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
          Cell 03 - Address: <MAC 'BTHomeHub2-Q7W8' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-11 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-Q7W8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1674 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x432b (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.664074] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.668479] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.878183] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   18.577293] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  593.947061] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

any help greatfully received!

TIA

---

### Post by chili555 on 2015-01-10
Network Manager will, by default, prefer the faster and more secure ethernet. In your case, the ethernet is connected and has an IP address. If you detach the ethernet and wait a few moments for NM to see the change in state, can you click the NM icon and see networks?

Actually, this is a trick question; we know you see networks!> Wireless Access Points 
    BTHomeHub2-Q7W8: Infra, <MAC 'BTHomeHub2-Q7W8' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWiFi:          Infra, <MAC 'BTWiFi' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100Can you click on your preferred network, supply the password and connect? If not, what happens? Does it try and fail or smoke or spit sparks or whine like a baby??

---

### Post by atfleg on 2015-01-10
yup I can see the networks. The odd thing is i have two network manager icon an ethernet one and a wifi one. I only had one before - but when I was trying to resolve the problem I somehow ended up with two. Now after a completely fresh install I still have two....

if i click on the network it asks me for the password, i tyope it in and,,,,,......nothing happens, I still have a big red X next to the NW.

I'm about to hurl my laptop against the nearest wall!

---

### Post by chili555 on 2015-01-10
> **atfleg said:**
> I'm about to hurl my laptop against the nearest wall!Now, now! Pity the poor wall.

With the ethernet still detached, let's see what NM is doing all this time:```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n25  > wifi.txt
```Hook up the ethernet and post the text file wifi.txt here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by atfleg on 2015-01-10
OK, wall saved! 

[http://paste.ubuntu.com/9708109/](http://paste.ubuntu.com/9708109/)

---

### Post by chili555 on 2015-01-10
Almost everything we see is the ethernet. Let's take another look:```
cat /var/log/syslog | grep wlan | tail -n25  > wifi.txt
```

---

### Post by atfleg on 2015-01-11
very little:

Jan 11 13:58:55 edward-Latitude-E5400 ntpd[2743]: Listen normally on 5 wlan0 fe80::224:2bff:fe78:28ca UDP 123
Jan 11 14:00:06 edward-Latitude-E5400 ntpd[2878]: Listen normally on 5 wlan0 fe80::224:2bff:fe78:28ca UDP 123

That's it.

thanks again for the help - and apologies for the intermittent replies!

---

### Post by chili555 on 2015-01-11
Something is obviously wrong. Please detach the ethernet, reboot, see if you see networks, try to connect and then do:```
dmesg > wifi.txt
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25  >>  wifi.txt
iwconfig  >>  wifi.txt
```Find the file wifi.txt and paste it here: [http://paste.ubuntu.com](http://paste.ubuntu.com) Give us the link in your reply.

---

### Post by atfleg on 2015-01-11
[http://paste.ubuntu.com/9712576/](http://paste.ubuntu.com/9712576/)

There's a fair bit of it! 

There was also this in terminal:

```
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2015-01-11
I really don't see much wrong, that is, fixable there. Two things might be helpful to adjust:> lib80211_crypt: registered algorithm 'TKIP'I assume your router is set for WPA2-TKIP. TKIP is not as secure as AES and is often a bit troublesome for some Linux drivers.

Check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I see this:> cfg80211: World regulatory domain updated:  That big, fat blank there means no regulatory domain was set; a one-size-maybe-fits-all was used. I recommend that your regulatory domain be set explicitly. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)  Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close the text editor. Reboot.

Let's also see if we can see why NM isn't starting and running the wireless as expected.```
nm-tool
sudo dhclient wlan0
```dhclient is expected to fail if NM is installed correctly, but let's see if there are any interesting errors or other messages.

---

### Post by atfleg on 2015-01-11
thanks for the tips re router and country code. Updated where I can,

NM output - [http://paste.ubuntu.com/9714390/](http://paste.ubuntu.com/9714390/)

dhclient does nothing for a while...and then does nothing.

---

