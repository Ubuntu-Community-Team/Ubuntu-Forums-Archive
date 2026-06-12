---
title: "RTL8185 Recognized But Not Used Headless Ubuntu 14.04"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by nuttboxer2 on 2016-01-10
I have a Realtek RTL8185 NIC I tried adding to my headless server(14.04).  While the various identifying commands show it to be recognized, it is not functioning.  I tried compiling the driver from the Realtek website, which lists a much older kernel under support (2.6.x), and received a number of errors.  I also tried the fix listed here:
[http://ubuntuforums.org/showthread.php?p=9580984](http://ubuntuforums.org/showthread.php?p=9580984)

Didn't help.  Not really sure what to do next.  Here's the output of my wireless-info file:

```

########## wireless info START ##########

Report from: 10 Jan 2016 10:20 PST -0800

Booted last: 09 Jan 2016 14:25 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/adrian/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a5b]
    Kernel driver in use: forcedeth

01:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8225]
    Kernel driver in use: rtl8180

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

rtl8180                40280  0 
mac80211              630728  1 rtl8180
cfg80211              484040  2 mac80211,rtl8180
eeprom_93cx6           13344  1 rtl8180
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:35fd:5720:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2602:306:35fd:5720:cd6b:10ce:5b18:5144/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68049718 (68.0 MB)  TX bytes:1906612730 (1.9 GB)

tun0      Link encap:UNSPEC  HWaddr <MAC 'tun0' [IF]>  
          inet addr:10.175.1.6  P-t-P:10.175.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:27204 (27.2 KB)  TX bytes:3105 (3.1 KB)

##### iwconfig ##########################

tun0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.175.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
10.175.1.1      10.175.1.5      255.255.255.255 UGH   0      0        0 tun0
10.175.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.175.1.5      128.0.0.0       UG    0      0        0 tun0
169.57.0.199    192.168.1.254   255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 192.168.1.254
search attlocal.net

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

No NetworkManager profiles found.

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

tun0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

tun0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8180]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     55981B6920CC72BDE7D0933
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C8432FAB97804E8F7A8FB0F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

loop
lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   34.731027] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.072867] forcedeth 0000:00:07.0 eth0: MSI enabled
[   36.943034] rtl8180 0000:01:09.0: enabling device (0000 -> 0003)
[   36.943381] 0000:01:09.0 (rtl8180): Unknown chip! (0x7)

########## wireless info END ############

```

Found some additional info in dmesg
```

[   61.012039] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   61.012040] realtek: Enable default setup for auto mode as fallback
[   61.059891] forcedeth 0000:00:07.0: irq 46 for MSI/MSI-X
[   61.059933] forcedeth 0000:00:07.0 eth0: MSI enabled
[   61.081261] cfg80211: Calling CRDA to update world regulatory domain
[   61.670947] cfg80211: World regulatory domain updated:
[   61.670954] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   61.670957] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   61.670959] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   61.670961] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   61.670964] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   61.670967] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   61.688308] rtl8180 0000:01:09.0: enabling device (0000 -> 0003)
[   61.688622] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   61.795719] 0000:01:09.0 (rtl8180): Invalid hwaddr! Using randomly generated MAC addr
[   61.920501] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   61.920783] ieee80211 phy0: hwaddr 92c6f704fbbb, RTL8185vD + rtl8225
[   62.228027] ieee80211 phy0: reset timeout!

```

---

### Post by chili555 on 2016-01-11
> ##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcpThis will never do. Wireless interfaces require a declaration of the SSID (network name) you wish to connect to and, hopefully, the WPA2 password. Moreover, if you expect to connect to the server by SSH or FTP later, you probably want a static IP address.

I suggest you set up /etc/network/interfaces something like:

```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_router>
wpa-psk <your_wpa_key>
dns-nameservers 8.8.8.8 192.168.1.1
```
Be sure to select a static address outside the range used by the DHCP server in the router, switch or other access point. Of course, substitute your details here.

Get the system to read and use the changes:

```
sudo ifdown wlan0 && sudo ifup -v wlan0
```
Did you connect?

```
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by nuttboxer2 on 2016-01-12
Thanks Chili!  I had this card working in the past on other PC's, don't remember having to do this much config work.  Haven't had a chance to get back to this, I'll be sure to post as soon as I do.

Ran the command to get the system to read the changes.  Didn't get the response I was hoping for:
```

Cannot find device "wlan0"
Error getting hardware address for "wlan0": No such device
Failed to bring up wlan0.

```

Some additional info, this server is already connected to the ISP wireless router/modem using working ethernet.  I need the card to setup a virtual router w/vpn that most of my devices will run through.

---

### Post by chili555 on 2016-01-13
> I need the card to setup a virtual router w/vpn that most of my devices will run through.You have exceeded my limited level of expertise. May I assume this is a virtual machine? I have no experience in such things.

I see that you haven't a wlan0 in ifconfig, so my answer is probably inapplicable.> I had this card working in the past on other PC's, don't remember having to do this much config work. In an ordinary computer with a desktop environment, Network Manager usually does all the work for us. Headless means no NM and so manual methods are needed.

---

### Post by nuttboxer2 on 2016-01-13
> **chili555 said:**
> In an ordinary computer with a desktop environment, Network Manager usually does all the work for us. Headless means no NM and so manual methods are needed.

Makes sense.

The card is on a physical headless server.  I am in the process of setting up a virtualbox, but I need to bridge two NIC's for the VB before installing an OS, and later route traffic through this card for some devices as a VPN router, which is why I'm trying to get it working.

In the output I provided it shows a kernal driver for this NIC.  The issue I keep seeing seems to indicate a driver is not being used, hence no recognition of my NIC as a WiFi card.  As I mentioned, the Realtek alternative seems very outdated, and doesn't compile.  I think I need to know if I can get a driver working for this card, or if I should move on to other alternatives.  I have a USB WiFi adapter, and a physical router I can fall back to.  But I would really like to know I've exhausted my options with the PCI card first.

---

### Post by chili555 on 2016-01-13
In a virtual environment, you are probably *not* going to get the PCI device working as you expect.

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by nuttboxer2 on 2016-01-13
I see from the article that only IPV4 is supported.  I believe some of the output I posted at the top has it trying to connect using IPV6, which would be a problem.  Still I would like to try and get the card driver installed just to confirm.  Any help along those lines would be very much appreciated.

---

### Post by chili555 on 2016-01-13
> [COLOR="#FF0000"]rtl8180[/COLOR] 0000:01:09.0: enabling device (0000 -> 0003)I believe the driver is already present. Does it appear?```
lsmod | grep rtl
```

---

### Post by nuttboxer2 on 2016-01-14
> **chili555 said:**
> I believe the driver is already present. Does it appear?```
lsmod | grep rtl
```

Right after enabling device it says unknown chip, from what I've gathered in other posts, this seems to be an indicator the driver is not working.

The lsmod command doesn't display anything, just reloads the command prompt.

---

### Post by chili555 on 2016-01-14
> **nuttboxer2 said:**
> Right after enabling device it says unknown chip, from what I've gathered in other posts, this seems to be an indicator the driver is not working.

The lsmod command doesn't display anything, just reloads the command prompt.Let's see for ourselves, please:```
sudo modprobe rtl8180 && dmesg | grep rtl
```

---

### Post by nuttboxer2 on 2016-01-14
```

sudo modprobe rtl8180 && dmesg | grep rtl
[   61.688308] rtl8180 0000:01:09.0: enabling device (0000 -> 0003)
[   61.795719] 0000:01:09.0 (rtl8180): Invalid hwaddr! Using randomly generated MAC addr
[   61.920783] ieee80211 phy0: hwaddr 92c6f704fbbb, RTL8185vD + rtl8225
[ 2488.555718] 0000:01:09.0 (rtl8180): Invalid hwaddr! Using randomly generated MAC addr
[ 2488.567228] ieee80211 phy1: hwaddr 0260ff99a00c, RTL8185vD + rtl8225
[353814.375788] 0000:01:09.0 (rtl8180): Invalid hwaddr! Using randomly generated MAC addr
[353814.387982] ieee80211 phy2: hwaddr 3e880d766794, RTL8185vD + rtl8225

```

```

lsmod | grep rtl
rtl8180                40280  0 
mac80211              630728  1 rtl8180
cfg80211              484040  2 mac80211,rtl8180
eeprom_93cx6           13344  1 rtl8180

```

Looks like progress, but still no wlan0 when I run ifconfig, and networking restart gives pretty much the same dmesg output.

BUT... Looking at my virtualbox configuration, I now have an available wlan0 to choose, which will hopefully enable me to install pfsense.  I'll post back to confirm if this fixed my networking issue.

---

