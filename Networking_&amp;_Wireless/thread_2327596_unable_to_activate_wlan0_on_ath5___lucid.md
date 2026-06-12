---
title: "unable to activate wlan0 on ath5  : lucid"
date: 2016-06-12
forum: Networking &amp; Wireless
---

### Post by bunty on 2016-06-12
Hi,

I am having trouble with wlan0 on a remotely maintained system on an HP laptop.  HP G60-213EM

When I say remote I mean REMOTE. I do not have the possibility to pop over and sort this out with physical possession of the machine. Neither do I have the confidence to do a major system upgrade remotely and hope that I get control of the machine when it comes back up. That is why it is still running kubuntu lucid. 

So with the preliminaries out of the way : I have run the test script and here is the output. 


```

########## wireless info START ##########

Report from: 12 Jun 2016 18:44 IST +0100

Booted last: 12 Jun 2016 17:35 IST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:  Ubuntu 10.04.4 LTS
Release:  10.04
Codename: lucid

##### kernel ############################

Linux 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 unknown unknown GNU/Linux

, ro, quiet, splash,

##### desktop ###########################

KDE

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
  Kernel driver in use: r8169
  Kernel modules: r8169

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
  Kernel driver in use: ath5k
  Kernel modules: ath5k

##### lsusb #############################

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: no

##### lsmod #############################

ath5k                 134437  0
mac80211              238896  1 ath5k
ath                     9723  1 ath5k
cfg80211              148341  3 ath5k,mac80211,ath
led_class               3764  1 ath5k

##### interfaces ########################

auto lo
iface lo inet loopback

allow-hotplug eth0
auto eth0
iface eth0 inet static
 address 192.168.1.2
 gateway 192.168.1.254
 netmask 255.255.255.0
 network 192.168.1.0
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 metric 2

allow-hotplug wlan0
iface wlan0 inet static
 address 192.168.1.3
 gateway 192.168.1.254
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 metric 2
 pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
 post-down killall -q wpa_supplicant
 #post-down ifup eth0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3777990 (3.7 MB)  TX bytes:9841841 (9.8 MB)
          Interrupt:26 Base address:0x8000

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    2      0        0 eth0

##### resolv.conf #######################

nameserver 8.8.4.4

##### network managers ##################

Installed:

  None found.

Running:

  None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

nm-system-settings.conf (used up to Ubuntu 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/w1]] (600 root)
[connection] id=w1 | type=802-11-wireless | autoconnect=true
[ipv4] method=auto
[802-11-wireless] ssid=84;105;115;99;97;108;105;55;57;57;50;68;66; | mtu=0

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[ath5k]
filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     5A81CAB958F60B02DE47E18
depends:        mac80211,led-class,cfg80211,ath
vermagic:       2.6.32-33-generic SMP mod_unload modversions
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)

[mac80211]
filename:       /lib/modules/2.6.32-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8053D81494B2D5D18042B07
depends:        cfg80211
vermagic:       2.6.32-33-generic SMP mod_unload modversions
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath]
filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     9F3058CD7BF1A871B2C3DCD
depends:        cfg80211
vermagic:       2.6.32-33-generic SMP mod_unload modversions

[cfg80211]
filename:       /lib/modules/2.6.32-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     202104338ECB626EB55A6B7
depends:
vermagic:       2.6.32-33-generic SMP mod_unload modversions
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)

##### module parameters #################

[ath5k]
all_channels: N
nohwcrypt: N

[mac80211]
ieee80211_default_rc_algo: minstrel

[cfg80211]
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist ipv6
blacklist ath_hal
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
blacklist amd76x_edac

[/etc/modprobe.d/madwifi.conf]
blacklist ath5k

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

/sbin/modprobe ath5k

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   19.581857] type=1505 audit(1465749351.508:3):  operation="profile_load" pid=595 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.586713] type=1505 audit(1465749351.508:6):  operation="profile_replace" pid=619 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.635147] r8169: eth0: link up (repeated 2 times)
[   21.935652] type=1505 audit(1465749354.108:9):  operation="profile_replace" pid=927 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.456005] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.456020] ath5k 0000:02:00.0: setting latency timer to 64
[   23.456084] ath5k 0000:02:00.0: registered as 'phy0'
[   23.950507] ath: EEPROM regdomain: 0x67
[   23.950511] ath: EEPROM indicates we should expect a direct regpair map
[   23.950517] ath: Country alpha2 being used: 00
[   23.950519] ath: Regpair used: 0x67
[   23.959423] Registered led device: ath5k-phy0::rx
[   23.959447] Registered led device: ath5k-phy0::tx
[   23.959454] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   29.691272] eth0: no IPv6 routers present

########## wireless info END ############

```



Wired networking is fine. 
The network widget on the lower panel shows eth0 and wlan0 checked. 
The wifi LED on the machine shows blue once powered up, not red. I take it mean that this is working and configured:  an indication that wifi hardware is on. 
The router config shows wifi enabled. 

We see from the above that:
wlan0     Interface doesn't support scanning : Network is down


Now I recall that about 3y ago , the last time I had physical access, I was trying to configure something to switch the wifi connection on when etho went down and vice versa but it was too much effort and I left it with eth0 only which was satisfactory at that time. Now we need wireless. 

This may be one of those annoying hardware setups that disables wifi when the wired connection is connected. I have tried unplugging eth0 and rebooting but don't get wlan0. 

Hopefully, with the script output someone can point me to the problem. 

TIA for any advice.

---

### Post by bunty on 2016-06-12
OK, I have got somewhere:

ifconfig wlan0 up 

I now have output from iwlist scanning finding a bunch of ESSIDs including my Thomson router. ;)

I'm a little confused by NetworkManager saying :

WirelessEnabled=false


 /etc/wpa_supplicant/wpa_supplicant.conf shows a single network config 

ssid=[my router ESSID]
psk=[64char hexidecimal digits]

---

### Post by X-RED_Tech on 2016-06-12
Ubuntu 10.04 is out of support since a long time ago. I see no point in troubleshooting.

---

### Post by bunty on 2016-06-13
I would like to do a dist-upgrade but my experience is that this is risky process that invariably throws up a few things that need fixing. If one of those things affects my ability to connect remotely this will require an international flight to sort the problem since the person NEEDS this system to be functional . 

This is an unacceptable risk. So until I have physical access it will have to stay on lucid. 

If you are unable to help that's fine.

---

### Post by QLee on 2016-06-13
> **bunty said:**
> Hopefully, with the script output someone can point me to the problem. 

OK, I read through your script results.

First off, you don't have Network Manager installed, so how it is "configured" shouldn't matter.

You don't have the wireless optioned to "auto", so of course it doesn't come up automagically at boot. Your thread title isn't correct, you can "activate it", that's what you did with ifconfig wlan0 up.

As X-Red mentioned, 10.04 is no longer supported and thus a possible security risk, hope it isn't connected to the Internet. ;-)

You seem to somewhat understand what you are doing, perhaps that will be enough to get you thinking. it's all the support we should be offering for 10.04. I do wish you good luck.

---

### Post by bunty on 2016-06-13
thanks for your reply QLee. 

I have quite a lot of linux experience but not a lot with wifi. 

I think part of the problem was that I had a commented line in the network{} section . It seems that this was not parsing ( comments not allowed? ). 

Using ifup wlan0 gave some output that I was not getting when using ifconfig wlan0 up 

Having removed that line it looked to be dong something but the ssh connection broke and I'm blind now until I can get telephone connection to the other end and start dictating command lines. :(

I think bringing up the wireless shuts down the wired connection on this h/w, from what I've read. 

I remember having this jive last time I had physical access and gave up !

It may be possible to set up wireless only and leave it that way.

---

### Post by QLee on 2016-06-13
> **bunty said:**
> Having removed that line it looked to be dong something but the ssh connection broke and I'm blind now until I can get telephone connection to the other end and start dictating command lines. :(

I think bringing up the wireless shuts down the wired connection on this h/w, from what I've read. 

If that is true about the hardware (it might possibly be a BIOS option that can be set), of course you'd lose the remote connection when the wired connection goes down because you'd have a different IP address.

> **bunty said:**
> It may be possible to set up wireless only and leave it that way.

Please don't leave a system without security updates and the inability to even receive security updates attached to the Internet, especially in the hands of someone who understands so little as it appears is the case for your user.

---

### Post by X-RED_Tech on 2016-06-13
> **QLee said:**
> Please don't leave a system without security updates and the inability to even receive security updates attached to the Internet, especially in the hands of someone who understands so little as it appears is the case for your user.

+1

If I remember correctly, 10.04 server had 5 years support but desktop only 3. Either way it isn't receiving any update since a long time ago, the software repositories closed and/or moved somewhere else.

---

### Post by QIII on 2016-06-13
Hello.

Please see [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730) for the Ubuntu Forums Staff position on EOL releases.

A far more unacceptable risk to your client is an EOL release that is no longer getting security updates.  If you cannot get them upgraded without physical access, then I submit that it would be in the best interest of your client that you enlist the help of someone who can get this done.

Asking for our help with 10.04 is asking for our complicity in an irresponsible course of action.

---

