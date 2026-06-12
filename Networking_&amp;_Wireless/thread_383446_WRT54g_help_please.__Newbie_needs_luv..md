---
title: "WRT54g help please.  Newbie needs luv."
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by MrDetermination on 2007-03-13
Hi,

Still very new to Ubuntu but trying it out on a computer I built specifically for Ubuntu now.  Yesterday I got fed up and took a Belkin card back for a "generic Linksys card" as per the advice of some random guy on a message board somewhere.  I've gotten the Network Administration tool to see the new card as two cards (much farther than I got with belkin).  It sees it as "wlan0" and "wmaster0".  I've been fanangling with modprobing of drivers and all kinds of stuff all morning, no telling what I broke in the process :)

I don't know what I'm missing now.  I can enable/disable those connections in the Network Admin panel but it doesn't do any good.  There is no additional system tray tool network manager thingy that comes up and I can't select a wireless network from the network icon where the Ethernet connection shows up.

Here are some pertinent console queries.  I don't know what else to provide to get to the bottom of this.  Last thing, I need to connect to a WPA-PSK network when this is all said and done.  I'm almost there, right?

```
chip@chip-desktop:~$ uname -r
2.6.17-11-386
chip@chip-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0b.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
chip@chip-desktop:~$ iwconfig

chip@chip-desktop:~$ 

chip@chip-desktop:~$ 
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"thisismyhouse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

```

EDIT: Here is an lspci -v chunk that mentions RaLink:
```
00:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys Unknown device 0055
        Flags: bus master, slow devsel, latency 32, IRQ 11
        Memory at ee100000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
```

---

### Post by chili555 on 2007-03-13
Please let us see the output of these two commands:```
sudo dhclient wlan0
iwlist wlan0 scan
```

Thanks. You are mostly there. We'll get her going!

---

### Post by MrDetermination on 2007-03-13
```
root@chip-desktop:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2d:fa:01
Sending on   LPF/wlan0/00:18:f8:2d:fa:01
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@chip-desktop:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:A3:D1:E4
                    ESSID:"thisismyhouse"
                    Mode:Master
                    Frequency:2.412 GHz
                    Encryption key:on
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra:tsf=0000005c01ecb181
```

---

### Post by chili555 on 2007-03-13
Now you need to set up WPA on your computer so it will associate with your router which has WPA encryption running. You will find many posts here if you search for WPA.

This HOWTO looks excellent: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

---

### Post by Matt Yun on 2007-03-13
> **chili555 said:**
> Now you need to set up WPA on your computer so it will associate with your router which has WPA encryption running. You will find many posts here if you search for WPA.

This HOWTO looks excellent: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

That WPA How-To is an excellent reference, but it's pretty newbie-intimidating.

Using WPA is quite easy with network-manager-gnome.  I'm still using Dapper 6.06, so to get it, just do as sudo 'apt-get install network-manager-gnome', or use the Add/Remove option from the Applications menu and search for 'Network-Manager'.

This gives you a system-tray WiFi widget similar to the one in WindowsXP.  You simply click it, and it displays all of the nearby wireless networks.  Select the "Connect to Other Wireless Network" option, and enter your WRT54g SSID name and WPA key.

I also have a WRT54g and I connect to it flawlessly with my notebook (Intel ipw2100 wifi card), and desktop (C-Net CWP-854 RaLink rt25xx pci card).  

P.S. #1:  I use Sidux (Debian Sid) on the desktop; it autodetected and configured the RaLink wifi card, so I didn't need to install anything like network-manager-gnome.  Sidux comes with the RaLink utilities already packaged; I used the RT25xx utility to enter my network's SSID and WPA values.

P.S. #2: RaLink open-sourced their drivers, which is why their wifi cards are the best for Linux distros.  **RaLink wifi cards also support WPA natively, and do not require wpa_supplicant.**

---

### Post by Chris Johnson on 2007-03-23
I've got a very similar problem - but my network is unencrypted. Some relevant system information:

```

[B]alice@alice-laptop:~$ uname -r
[/B]2.6.17-10-generic
[B]alice@alice-laptop:~$ lspci
[/B]...
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI[B]
alice@alice-laptop:~$ iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

[B]alice@alice-laptop:~$ sudo dhclient wlan0
[/B]Password:
There is already a pid file /var/run/dhclient.pid with pid 8674
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:2e:8a:b1:8d
Sending on   LPF/wlan0/00:0e:2e:8a:b1:8d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[B]alice@alice-laptop:~$ sudo iwlist wlan0 scan
[/B]wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:9F:BC:58
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz
                    Encryption key:off
                    Extra:tsf=000000000d838149
[B]
alice@alice-laptop:~$ lspci -v[/B]
...
02:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: RaLink Unknown device 2561
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 2c000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

```

I'm not sure what's wrong - it seems to be seeing the wireless router, but not connecting to it properly. Any ideas?

---

### Post by MeeMaw on 2007-03-23
I have a card with the RaLink rt61 driver.....(running Edgy)   I used this post

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

So for those of you with the RaLink driver, it may work for you too   (I'm a newb as well.)

Good luck!

---

### Post by Austin_KW on 2007-03-23
I have had problems with the ralink drivers included with the distribution. You need to get the rt61 drivers direct from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) and build them yourself.
If you search the forums for "rt61" you should find details on building the new drivers and blacklisting/removing the old drivers

---

