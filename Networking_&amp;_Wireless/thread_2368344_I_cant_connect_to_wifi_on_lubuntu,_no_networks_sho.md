---
title: "I cant connect to wifi on lubuntu, no networks show up."
date: 2017-08-09
forum: Networking &amp; Wireless
---

### Post by thatonecoderkid on 2017-08-09
I am running lubuntu 16.04, and I can't connect to wifi. It is fine when I plug it in with an ethernet cable, but no wireless networks show up. I have already tried downloading some of the .txt files that have been suggested, I used Rfkill to list the network devices and it says Soft blocked: no, and hard blocked: no. I have a realtek wifi card on a gateway laptop. I couldn't find the driver for my card though, but it said in lshw that one is already working. HELP!!!

---

### Post by chili555 on 2017-08-09
Please see: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by johndough2 on 2017-08-10
Hi

If it is working then one of these should show that (or give NO details)...

sudo ifconfig -a
sudo hwinfo --network
sudo iwlist wlan0 channel   The wlan0 would be your device listing name, wifi1, wifi2 wlan3 or whatever.

Then from the "*script*"  the finer details should move us to the next level.

---

### Post by thatonecoderkid on 2017-08-10
Chili555 I tried that already, to no avail.

---

### Post by jeremy31 on 2017-08-10
You need to post the results from the script, the wireless-info.txt file contents as that will give us important info to diagnose the problem

---

### Post by chili555 on 2017-08-10
> **thatonecoderkid said:**
> Chili555 I tried that already, to no avail.It is not supposed to FIX the wireless. It is suppose to gather and allow you to post the details we need to diagnose the problem and propose a fix.

---

### Post by thatonecoderkid on 2017-08-11
Ohhh, how do you run it, just by doing the wget command?

---

### Post by chili555 on 2017-08-11
I can't explain it any better than in the link.> Once that's done, download and run the wireless info script, which will gather information to help diagnose your system. You can run it using this command:

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.


---

### Post by thatonecoderkid on 2017-08-12
I see, I believe this is what you want to see:


```
########## wireless info START ##########

Report from: 12 Aug 2017 11:27 MDT -0600

Booted last: 12 Aug 2017 00:00 MDT -0600

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-89-generic #112-Ubuntu SMP Mon Jul 31 19:37:10 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, acpi=off, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
    Subsystem: Gateway, Inc. 88E8038 PCI-E Fast Ethernet Controller [107b:0318]
    Kernel driver in use: sky2

08:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8225]
    Kernel driver in use: rtl818x_pci

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl818x_pci            49152  0
mac80211              659456  1 rtl818x_pci
cfg80211              499712  2 mac80211,rtl818x_pci
eeprom_93cx6           16384  1 rtl818x_pci

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:37264 (37.2 KB)  TX bytes:37264 (37.2 KB)

wlp8s9    Link encap:Ethernet  HWaddr <MAC 'wlp8s9' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp8s9    IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thrff   Fragment thrff
          Power Managementff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       673     1  0 11:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp8s9
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
GENERAL.DRIVER:                         rtl818x_pci
GENERAL.DRIVER-VERSION:                 4.4.0-89-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp8s9' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:08:09.0/net/wlp8s9
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8038 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
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

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

##### iw reg get ########################

Region: America/Denver (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

wlp8s9    11 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp8s9    No scan results

##### module infos ######################

[rtl818x_pci]
filename:       /lib/modules/4.4.0-89-generic/kernel/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
license:        GPL
description:    RTL8180 / RTL8185 / RTL8187SE PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     718CDE48D1F626F7851C577
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       4.4.0-89-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-89-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     066D9B501A63401DBFCBF56
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-89-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-89-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-89-generic SMP mod_unload modversions 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

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
blacklist b43
blacklist ssb

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
options iwlwifi 11n_disable=8

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   10.147843] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   11.585732] systemd[1]: Reached target Network (Pre).
[   22.993999] rtl818x_pci 0000:08:09.0: using bridge 0000:00:14.4 INT B to get IRQ 16
[   22.994008] rtl818x_pci 0000:08:09.0: PCI->APIC IRQ transform: INT B -> IRQ 16
[   26.586946] rtl818x_pci 0000:08:09.0 wlp8s9: renamed from wlan0
[   48.605496] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   48.608023] sky2 0000:02:00.0 enp2s0: enabling interface
[   48.608797] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   48.709829] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready (repeated 3 times)

########## wireless info END ############
```

---

### Post by praseodym on 2017-08-12
Please try

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by thatonecoderkid on 2017-08-26
Sorry I haven't been able to reply, school just started, and I am using a different laptop, but stil want to get this one working. Praseodym, when I try to do that, it says :no such file or directory

---

### Post by thatonecoderkid on 2017-08-27
Now in lshw it says UNCLAIMED, and has no driver attached. I am beginning to think the driver is the issue, but I can't find the right one for Linux, and ndiswrapper isn't working

---

### Post by chili555 on 2017-08-27
ndiswrapper is almost never helpful. I suggest that you purge it:```
sudo apt-get purge ndiswrapper*
```The driver is rtl818x_pci. Let's load it and see if the wireless springs to life:```
sudo modprobe rtl818x_pci
```In your efforts to get the tricky ndiswrapper working, did you blacklist the native driver?

---

### Post by thatonecoderkid on 2017-08-27
The wireless is now back, but it shows no networks

---

### Post by chili555 on 2017-08-27
Let's try to see why. Please run and post:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
ls /etc/modprobe.d
dmesg | grep -e rtl -e wlp
```

---

### Post by thatonecoderkid on 2017-08-27
Here you go

[code]christian@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf | tail -n5
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb
christian@ubuntu:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-oss.conf              iwlwifi.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf     libpisock9.conf
blacklist.conf              blacklist-watchdog.conf         mlx4.conf
blacklist-firewire.conf     dkms.conf                       vmwgfx-fbdev.conf
blacklist-framebuffer.conf  fbdev-blacklist.conf
blacklist-modem.conf        intel-microcode-blacklist.conf
christian@ubuntu:~$ dmesg | grep -e rtl -e wlp
[  369.335364] rtl818x_pci 0000:08:09.0: using bridge 0000:00:14.4 INT B to get IRQ 16
[  369.335372] rtl818x_pci 0000:08:09.0: PCI->APIC IRQ transform: INT B -> IRQ 16
[  369.539304] ieee80211 phy0: hwaddr 00c0a8f7ad0b, RTL8185vD + rtl8225
[  377.403145] rtl818x_pci 0000:08:09.0 wlp8s9: renamed from wlan0
[  378.282897] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready
[  381.644999] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready
[  381.780061] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready
[  739.814654] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready
[  739.848288] IPv6: ADDRCONF(NETDEV_UP): wlp8s9: link is not ready
christian@ubuntu:~$ 

[code]

---

### Post by chili555 on 2017-08-28
We see nothing unusual; that is, fixable here. We do see this:> ##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp8s9    No scan resultsIf there were some driver or hardware problem, we'd expect to see some other error or warnings; not just 'No scan results.' 

I assume this is a PCI-E wireless card in a desktop computer and that the card is something like this: [http://ca.dlink.com/wp-content/uploads/2014/03/DWA548front1664x936.png](http://ca.dlink.com/wp-content/uploads/2014/03/DWA548front1664x936.png) Can you please confirm that the antennae are present and firmly attached? Then try again:```
sudo iwlist scan
```

---

### Post by thatonecoderkid on 2017-08-28
everything seems to check out, I cheched the antennae connections, still getting the same results

---

### Post by thatonecoderkid on 2017-08-29
could it be a problem with the ipv6?

---

### Post by thatonecoderkid on 2017-09-02
Can anybody help?

---

### Post by praseodym on 2017-09-02
Deactivate IPv6 in the network profile ("Ignore") and reconnect

---

### Post by thatonecoderkid on 2017-09-02
I tried doing "connect to hidden wifi" and turned off ipv6, that didnt work

---

### Post by praseodym on 2017-09-03
Why hiding and not broadcasting? It is not a security feature!

---

### Post by thatonecoderkid on 2017-09-03
My problem is no wifi networks are showing up in the first place.

---

