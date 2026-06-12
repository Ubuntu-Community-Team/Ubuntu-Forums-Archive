---
title: "Wi-fi stopped working"
date: 2018-02-04
forum: Networking &amp; Wireless
---

### Post by jorge9992 on 2018-02-04
Hello,

I have the same problem as joecitizien, who posted some hours ago:

I am unable to connect to the Internet using WiFi on my desktop . There's no option to "enable wifi" in the drop-down menu. I haven't tried a wired connection, as my computer is too far away from the router.

I have never had this problem on this PC before - WiFi has always worked in the past. I haven't recently upgraded to a new version of Ubuntu or anything.  It worked fine for six months until it suddenly stopped doing it yesterday. 

I have been connecting through an USB device called Netgear WPS.

I run the "wireless-info" script and this is the result :



```
########## wireless info START ##########

Report from: 04 Feb 2018 09:59 CET +0100

Booted last: 04 Feb 2018 00:00 CET +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0846:9021 NetGear, Inc. WNA3100M(v1) Wireless-N 300 [Realtek RTL8192CU]
Bus 003 Device 004: ID 09da:000a A4Tech Co., Ltd. Optical Mouse Opto 510D / OP-620D
Bus 003 Device 003: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 003 Device 002: ID 0bc2:3300 Seagate RSS LLC 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mac80211              782336  0
cfg80211              614400  1 mac80211

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:27716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2053968 (2.0 MB)  TX bytes:2053968 (2.0 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root       708     1  0 08:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many))
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/freebox_VQZFRE]] (600 root)
[connection] id=freebox_VQZFRE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=freebox_VQZFRE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | autoconnect=false | permissions=user:jorge:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/freebox_VQZFRE_2GEXT]] (600 root)
[connection] id=freebox_VQZFRE_2GEXT | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=freebox_VQZFRE_2GEXT
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-32-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

8192cu

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   18.174457] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   18.422618] r8169 0000:02:00.0 enp2s0: link down
[   18.422690] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready

########## wireless info END ############
```

Thanks for any clues !

---

### Post by jeremy31 on 2018-02-04
I would try
```
sudo rm /etc/modprobe.d/blacklist-native-rtl8192.conf
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl819cu.conf
```
Reboot and if it doesn't work run the script again and post new results

---

### Post by jorge9992 on 2018-02-04
Thanks for your answer. I tried but apparently there is nothing to remove called etc/modprobe.d/blacklist ... (and so on)

---

### Post by praseodym on 2018-02-04
Lets check
```

lsmod
egrep 'rtl|8192' /etc/modprobe.d/*
```

---

### Post by jorge9992 on 2018-02-04
praseodym: I get this:
```

/etc/modprobe.d/rtl8192cu.conf:blacklist rtl8192cu

```

---

### Post by praseodym on 2018-02-04
Lets see
```

sudo modprobe -v rtl8xxxu
dmesg | grep rtl
```

---

### Post by jorge9992 on 2018-02-04
I did and now my wi-fi is working again!!!

After the first command, I got this: 
```

insmod /lib/modules/4.13.0-32-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko 
```

After the second one (dmesg):

```

[29208.595130] usb 3-9: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[29208.595159] usb 3-9: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[29209.093929] usbcore: registered new interface driver rtl8xxxu
[29209.180643] rtl8xxxu 3-9:1.0 wlx4494fc18ce9f: renamed from wlan0
[29240.549228] usb 3-9: rtl8xxxu_bss_info_changed: HT supported

```

---

### Post by jorge9992 on 2018-02-04
Lots of thanks, praseodym and jeremy31 !!!

If you ever have the time, could you tell me what the trouble was ?

Thanks again !

---

### Post by jeremy31 on 2018-02-04
You had two possible drivers blacklisted likely from installing pvaret's github source, the /etc/modprobe.d/blacklist-native-rtl8192.conf file is part of that.  The 4.13 kernel has 2 drivers to support that wifi and they can conflict so we blacklisted the rtl8192cu module and let rtl8xxxu do the job.  I am not sure why you had to manually modprobe it, if it happens again after a reboot try
```
sudo depmod -a
```

---

### Post by jorge9992 on 2018-02-04
Great. You saved my day (or my week).

---

### Post by joecitizien on 2018-02-04
Hmm, I have a similar problem as Jorge, but this hasn't worked for me (my wired connection is functioning, but my wireless is not). 

I enter the command 
lsmod
egrlsmod
egrep 'rtl|8192' /etc/modprobe.d/*ep 'rtl|8192' /etc/modprobe.d/*And get this 
>  /etc/modprobe.d/rtl819cu.conf:blacklist rtl8192cu 

I then enter 

sudo modprobe -v rtl8xxxu

And get 

> insmod /lib/modules/4.4.0-89-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-89-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.4.0-89-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko 

And then enter dmesg | grep rtl and get...
  
> [  400.875731] usbcore: registered new interface driver rtl8xxxu


---

### Post by wildmanne39 on 2018-02-04
Hello joecitizien, please do not hijack someone else's thread it is always better to start your own thread so both of you can get the help you need. 

Run the wireless script in my signature and post it in your own thread so someone can help you.

Thanks

---

### Post by the.fallen.one on 2018-02-06
Hey jeremy31, i am a complete noob to linux and know nothing but want to learn everything. I had installed mint cinnamon 18.3 but it had this very slow wi fi connection( was getting 0.30mbps down speed on speed test) but had exact speed on ethernet(25MBps) so i shifted to ubuntu which i wanted to do eventually after learning mint which i reserched as the basics. but the problem still persists and after searching through forums a was able to get some sort of solution by running clone from github of the realtek driver. Before i run that script wi fi was very slow but now its completely not even detecting the network. i ran the above scrpits too but to no avail. If you could help me and teach me whats is wrong that i'm doing, i'd be really grateful to you sir.

---

### Post by wildmanne39 on 2018-02-06
Hello and welcome to the forum the.fallen.one please do not hijack someone else's thread or create more then one post on the same topic, it is considered rude and you will get the best help by creating your own thread, click on the wireless script in my signature and post the results so we can help you.

Thanks

---

### Post by the.fallen.one on 2018-02-08
i am very sorry. its embarrassing ,i didnt know how to create a new thread.(Learnt it now)
I clicked on somethings and made mistakes.
again i apologize.

---

### Post by wildmanne39 on 2018-02-08
No worries!

---

