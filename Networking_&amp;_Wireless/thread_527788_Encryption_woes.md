---
title: "Encryption woes"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by feffer on 2007-08-17
I'm having lots of problems getting WPA working on my new ASUS WL-107g wifi card. I used the info on:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") And this seemed to work well enough to get ndiswrapper installed and the windows drivers loaded. I could connect with encryption off. When I tried to use WPA, I could no longer connect even after following the directions a little further down in the guide. Now after struggling to get WPA going, I can't even get a connection with encryption off anymore.

This laptop already has an Intel ipw2100 wifi chip on board, but it's "b" and I was trying to upgrade to a faster "g" spec. The Intel chip works fine with WPA. Two questions: Is the faster speed of the "g" spec significant, for web surfing, etc? Second, if it is useful, how can I get WPA working on the new card?

Regards,
feffer

---

### Post by kevdog on 2007-08-17
I wouldnt worry about the b vs g thing.  I havent really noticed a difference.

As far as the WPA thing, have you install the wpasupplicant package?

Please post 
lshw -C network
iwlist scan
/etc/network/interfaces

Im sure we can get you going with WPA!!:)

---

### Post by feffer on 2007-08-17
Yes, I installed wpa-supplicant and followed the ubuntuguide info to create the conf file.```
# File created to run RT2500 wifi chipset with WPA encryption

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="my-wifi-net"
   psk="my-password"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }
```
This didn't seem to have any effect. In fact if I tried to "connect to another wifi network" the dialog that came up only offered WEP as an encryption choice. The on-board intel chip on the other hand gave both WEP and WPA choices. So I'm wondering if my ASUS card or driver is really installed/configured correctly. Not sure how to trouble-shoot this, or if I should just send the card back and just use the working "b" Intel chip.

Thanks,
Ron

---

### Post by feffer on 2007-08-17
Tried several other things, connection fine with no encrypt, but fails with WPA. Trying to "connect to other network" doesn't even offer a choice for WPA with the Ralink chip, only WEP. I've checked several sites including the Ndiswrapper WPA howto, and I'm really confused. It seems like it should be simple from here, but I can't get it. 

```
pep@pep-laptop:/etc$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:a8:a0:c0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:83:2f:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.102 latency=32 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:faffc000-faffcfff irq:5
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@03:00.0
       logical name: ra0
       version: 01
       serial: 00:1a:92:c2:bb:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:38000000-38001fff irq:11
```
```
pep@pep-laptop:/etc$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:41:57:FF
                    ESSID:"neti-net"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:88  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 192ms ago

ra0       Scan completed :
          Cell 01 - Address: 00:1C:10:41:57:FF
                    Mode:Managed
                    ESSID:"neti-net"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-35 dBm  Noise level:-192 dBm

```
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp

```

hope this shows something that will help.

Thanks,
feffer

---

### Post by kevdog on 2007-08-17
You have two wirleless cards??? Thats very unusual, I dont know if this will cause a problem.  Do you want to use the ra or eth1 interface name

Here are some generic instructions.  You will have to change wlan0 to whatever interface you want to configure -- I would try eth1 first.

Contents of the wpa_supplicant.conf file are the following:
This example is assuming WPA (not WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```

Ok then type these commands at command line (remember to use something else than wlan0) -- You might get something like process does not exist or something.  These instructions are overkill for many people, I looking only for errors at the very end or with the wpa_supplicant line: (Also assumes the above file is at /etc/wpa_supplicant.conf

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

Let me know if this works, so we can work at getting it working with network manager of wicd.

---

### Post by feffer on 2007-08-17
kevdog, thanks for the reply. Yes, I have two cards: the original on-board ipw2100 Intell chip for "b" network spec, and a new card ASUS WL-107G with ralink rt2500 chipset for "g" network spec. I think I mentioned this in the first post. I bought the new ASUS card hoping for faster speed, but I'm not sure if I'm just chasing my tail here. The existing ipw2100 card works with WPA and it's only issue might be slower file transfers to the rest of my network which is useful but not crucial. 

I changed my wpa_supplicant.conf file as noted
```
# File created to run RT2500 wifi chipset with WPA encryption

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="my-wifi-net"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="mylongpassphrase"
}
```Then I issued the commands in order: ```
pep@pep-laptop:/etc$ 

pep@pep-laptop:/etc$ sudo ifconfig ra0 down

pep@pep-laptop:/etc$ sudo ifconfig ra0 0.0.0.0

pep@pep-laptop:/etc$ sudo killall dhclient wpa_supplicant dhclient3

pep@pep-laptop:/etc$ sudo rm /var/run/dhclient.pid

rm: cannot remove `/var/run/dhclient.pid': No such file or directory

pep@pep-laptop:/etc$ sudo wpa_supplicant -w -Dwext -ra0 -c/etc/wpa_supplicant.conf -dd
wpa_supplicant: invalid option -- r
wpa_supplicant v0.5.5
Copyright (c) 2003-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit (http://www.openssl.org/)

usage:
  wpa_supplicant [-BddehLqquvwW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-b<br_ifname> [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] \
        [-p<driver_param>] [-b<br_ifname>] ...]

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
options:
  -b = optional bridge interface name
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -u = enable DBus control interface
  -v = show version
  -w = wait for interface to be added, if needed
  -W = wait for a control interface monitor before starting
  -N = start describing new interface
example:
  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
pep@pep-laptop:/etc$ sudo ip route flush dev ra0
Nothing to flush.
pep@pep-laptop:/etc$ sudo ifconfig ra0 up
pep@pep-laptop:/etc$ sudo iwconfig ra0 mode Managed
pep@pep-laptop:/etc$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:1a:92:c2:bb:99
Sending on   LPF/ra0/00:1a:92:c2:bb:99
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13

I killed it at that point as it seemed to be failing anyway.
```
My new card doesn't seem to have an option for WPA, but the on-board card does ```
pep@pep-laptop:/etc$ iwlist encryption
lo        no encryption keys information.

eth0      no encryption keys information.

eth1      2 key sizes : 40, 104bits
          4 keys available :
Error reading wireless keys (SIOCGIWENCODE): Operation not permitted
          Authentication capabilities :
                WPA
                WPA2
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0xBFC7E7E8
          Current cipher_pairwise:0xBFC7E7E8
          Current cipher_group:0xBFC7E7E8


ra0       2 key sizes : 40, 104bits
          4 keys available :
Error reading wireless keys (SIOCGIWENCODE): Operation not permitted

```I think that shows the problem. Earlier some wpa_supplicant command created the alias "wlan0" in a file in /etc, but I forgot which one. WPA was briefly working at that point, but after rebooting, the network seemed to get renamed from wlan0 to ra0, and after that it didn't work. I think there's an improper alias or something else which is looking in the wrong place for the wpa stuff. My head's about short-circuited ;) Hope we can get this.

Thanks,
feffer

---

### Post by kevdog on 2007-08-17
Lets forget the ra card for now -- b/c with ra based chipsets you need to update the old driver to the newer rt2500 serial monkey driver.  Its configured totally different than the other card.  So for now, lets just stick with the older Intel Card.

I see from your output I gave you some faulty info, (forgot you were using the ipw driver).  Do the same commands except use this line instead:

Again the interface we are using is eth1, not the ra.  If this works I can point you how to update the ra drivers.

sudo wpa_supplicant -w -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd

---

### Post by feffer on 2007-08-17
OK, yes, I'm connected using the ipw2100 card, but to be honest, I was able to do that before with WPA. I have read quite a bit about the ra2500 chipset and think it's necessary under Feisty to use ndiswrapper. I think I have the latest windows drivers, but they are dated 2004. Any further info would be appreciated.

What about the alias comment, I mentioned. As I said, I very briefly had the rt2500 working with ndiswrapper and wpa. That's why I included the iwlist encryption output.

Thanks,
Ron

---

### Post by kevdog on 2007-08-17
Look for a post called rt73 serialmonkey authored by dieprius.  It tells you how to install for rt73, but just read the post about 3 times before beginning.  Then wherever it says rt73, just put rt2500.  Dont blacklist the rt2500 driver -- since that it the one you are using.

I cant search for the post right now, but dieprius' post regarding the installation of the serial monkey drivers is the "de-facto" standard for ra chipsets and feisty.

---

