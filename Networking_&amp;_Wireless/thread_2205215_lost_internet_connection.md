---
title: "lost internet connection"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by meanmrmustard on 2014-02-12
I believe I've added all the relevant info here and listed everything I've tried, though I'm not sure everything I tried was done correctly.
I don't know what else to look at or try and hope someone can point me in the right direction.
It may be one problem or more I suppose. It's been a while since the Linksys has been used - so it's possible that the wireless function is
having some problem but that's just a guess.

I recently added my personal router (Linksys WRT 54GL running Tomato v1.28) behind my IPS's modem after switching the modem to bridged mode.
I have verified that Open DNS is setup and functional on the router (it updates with no problem).
Wireless is enabled in the router with WPA2 Personal TPIK. I tried the WiFi connections with security off and still it would not connect.

All devices recognize the router's ethernet and/or the wireless connections (shows them as active) but I am only able to get connected to the internet on *some*, **not all**, of the devices that 
are connected with ethernet and none of my devices will connect wirelessly.

Previous to adding the Linksys router all devices were able to connect to the internet, my smart phone, my Nook, my ThinkPad laptop (dual booting Ubuntu 10.04 and 
Win XP), the Sony TV and the Win 7 install via WiFi and all machines using ethernet, Two Win 7 boxes and one Win XP install and three separate machines
running Ubuntu installations.


My UbuntuGnome 12.04 box (ethernet only) and the Ubuntu install on the laptop now will not connect and one Windows box (Desktop 2 - wireless only) refuses to get online, it does however connect
using ethernet.

The smart phone, Nook, the laptop and TV will not connect via WiFi.
Another Win 7 (wireless not installed on this one) box connects via ethernet. This machine dual boots Ubuntu (again, only ethernet available) but it (Ubuntu) will not connect.

The Win XP installation on the laptop (dual booting Win XP and Ubuntu) only connects via ethernet but not WiFi and the Ubuntu install will not connect with either method.

Ubuntu Live discs also show the eth0 interface as "connected" (Active, I guess) but do not connect to the internet via ethernet or WiFi.


To summarize:

1. (will connect)
All Windows boxes but only via ethernet
2. (will not connect)
All Windows devices using WiFi only and all Ubuntu installations using  WiFi and/or ethernet and Live Ubuntu discs.

All devices show the router's ethernet and/or WiFi connections as available.

I can ping the router (192.168.2.0) on the Windows machines, when I try it on the Ubuntu installations it returns:
"Do you want to ping broadcast? Then -b"
This makes no sense to me as Connection Information shows broadcast address as 192.168.2.255. and also shows the correct
IP address, gateway and subnet mask. When I do use the -b option it shows 100% packet loss.

I also have DNS entries for OpenDNS on each machine.
I've tried configuring one Ubuntu machine's ethernet manually with an available IP address within the 192.168.2.0 -192.168.2.149
subnet - still no internet.
I've tried both DHCP and DHCP (addresses only) settings in edit connections for eth0 to no avail.

Checking the network info on the UbuntuGnome machine I found no entry for eth0 in /etc/network/interfaces I found only:

auto  lo
iface lo inet loopback

and so I added:

auto eth0

which didn't help so I tried making the address static entering:

iface eth0 inet static
address 192.168.2.20
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.0
dns-nameservers 192.168.2.0

then ran:
restart network

it returned:
restart: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory.
At this point I notice the network manager icon has disappeared.

I reboot the machine, the icon is back and relevant lines in dmesg say:

r8169 000:06:00.0: eth0: link up

and further down:

eth0: no IPv6 routers present.

syslog reports:

```
NetworkManager [1071] info. (etho) IP6 addr conf timed out or failed.
         NetworkManager [1071] Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) schedule...
         NetworkManager [1071] Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) start... 
         NetworkManager [1071] Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

No mention of Ipv4??

auth.log shows a message from an attempt to restart networking: (this was all one line)

dbus[949] [system] Rejected send message, 2 matched rules; type="method_call" , sender=":1.40"  
(uid=1000 pid=1926 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface-"org.freedesktop.DBus.Properties" 
member="GetAll" error name="(unset)" requested_reply="0" destination-":1.15" (uid=0 pid=1434 comm="/usr/sbin/console-kit-daemon --no-daemon ")

I'm not aware of any other logs that might have a hint.

---

### Post by meanmrmustard on 2014-02-12
Continuing my search I just found a script that collects info to troubleshoot wireless connection issues.
Thanks to varunendra for the help.

Below is the txt created by the script.
Maybe it will help.


[code]*************** info trace ***************

***** uname -a *****

Linux paduak 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

***** lspci *****

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
	Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 10d5:5000 Uni Class Technology Co., Ltd 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 009 Device 002: ID 0bc2:50a5 Seagate RSS LLC 
Bus 009 Device 003: ID 0bc2:50a5 Seagate RSS LLC 
Bus 002 Device 003: ID 04b8:081e Seiko Epson Corp. MFP Composite Device

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.0

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             205.171.3.26



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

# This file describes the network interfaces available on your system
#and how to activate them. For further information, see interfaces(5).

# The looopback interface
auto lo
iface lo inet loopback

# Primary network interface
auto eth0 
#iface eth0 inet  
# address 192.168.2.20
# netmask 255.255.255.0
# broadcast 192.168.2.255
# gateway 192.168.2.0	
# dns-nameservers 192.168.2.0 



	

***** iwlist *****


***** resolv.conf *****

nameserver 208.67.222.222
nameserver 208.67.220.220


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


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****


****************** done ******************[/code

---

### Post by varunendra on 2014-02-13
Actually the script is a 'Thanks to Wild Man' who created it, I am only using it as is Wild Man :)

But the computer on which you ran it clearly has no wireless interface, so the script is not much useful for that although it still does show quite some relevant info that would be required in troubleshooting of both wireless and ethernet interfaces.

Maybe I didn't read your first post as carefully as I should have, but are you trying to troubleshoot the whole network or just a/few particular machine(s)?

The Gateway (router) address 192.168.2.0 is a bit awkward. Usually it is a "1" in the last.

Also, if you are using Network Manager to establish connections, it is best to leave the /etc/network/interfaces file alone unless you have very specific needs and using both is a well thought reasonable choice.

So.. could you please summarize again what you want to achive, regarding my questions above?

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by meanmrmustard on 2014-02-13
After adding the last post I realized that the machine I ran the script on has no wireless interface but was too tired to carry on and thought I'd do it this morning.
So this morning, on a whim, I changed the router's IP to 192.168.1.1 and suddenly everything's fine.
I don't see why that should make a difference but... they ya' go.

As for /etc/network/interfaces, shouldn't it have more than just the loopback in it?
Should I remove auto eth0?
It seem like the best idea is to leave well enough alone.

Thanks so much for your reply

---

### Post by varunendra on 2014-02-13
> **meanmrmustard said:**
> As for /etc/network/interfaces, shouldn't it have more than just the loopback in it?
Should I remove auto eth0?

Yup, IF you are using Network Manager to control the interfaces, then the '/etc/network/interfaces' file should only contain those two lines -
```
auto lo
iface lo inet loopback
```

Any interface that is mentioned in that file is, by default, ignored by the Network Manager. If you need static IP, you can do so in NM as well (although there is a bug in NM that you can't configure Static Interface without defining a Gateway. But most people do need to define a Gateway anyway, so it doesn't matter for most people).

---

### Post by meanmrmustard on 2014-02-13
Got it!
Thanks again.

---

