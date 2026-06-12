---
title: "Ubuntu 14.04 booting system without full network configuration"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by nitin7 on 2015-04-13
Hi...
I am using ubuntu 14.04 and on rebooting it shows "Waiting for network configuration" then it says "Waiting upto 60 more seconds for network configuration" and then "**Booting system without full network configuration"**

On starting it doesnot connect to the internet neither through wired connection nor with wifi. However there is no problem when i connect when using windows.

On giving command sudo service network-manager restart 
it connects to wifi. but still wired connection doesnt get connected.

PLZ HELP....
.

---

### Post by Bucky Ball on 2015-04-13
Not sure if it's what you're expecting, but they won't both connect at once. ;)

When you use your workaround to get wireless working, if you plug the cable in while you're online then disable the wireless, does the cable come to life?

---

### Post by nitin7 on 2015-04-13
it is not detecting eth0

when i run the command ifconfig -a
it shows only 
lo 
wlan0

it doesnt detect eth0

---

### Post by nitin7 on 2015-04-13
I want to  use wired connection but it is not getting connected

---

### Post by nitin7 on 2015-04-13
output of wireless script



```
########## wireless info START ##########


Report from: 13 Apr 2015 21:43 IST +0530


Booted last: 13 Apr 2015 20:34 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-49-generic #81-Ubuntu SMP Tue Mar 24 19:29:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6613]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 004: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a36 Importek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
wmi                    19177  1 toshiba_acpi
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


 


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/mumwifi]] (600 root)
[connection] id=mumwifi | type=802-11-wireless
[802-11-wireless] ssid=mumwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Sajeev-XOLOPlay 6X-1000]] (600 root)
[connection] id=Sajeev-XOLOPlay 6X-1000 | type=802-11-wireless
[802-11-wireless] ssid=Sajeev-XOLOPlay 6X-1000 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/multilink]] (600 root)
[connection] id=multilink | type=802-11-wireless
[802-11-wireless] ssid=multilink | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/mumwifi 1]] (600 root)
[connection] id=mumwifi 1 | type=802-11-wireless
[802-11-wireless] ssid=mumwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


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


wlan0     Interface doesn't support scanning : Network is down


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     65C14EF588BF1A68181643C
depends:        ath
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A2:F2:B9:84:B0:F0:3D:B6:0B:A1:EA:08:10:49:37:4C:1A:C3:D9:02
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0


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


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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
blacklist r8169
blacklist r8169


[/etc/modprobe.d/blacklist-ethernet.conf]
blacklist atl1c


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
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   15.901505] ath: phy0: ASPM enabled: 0x42
[   15.901510] ath: EEPROM regdomain: 0x65
[   15.901511] ath: EEPROM indicates we should expect a direct regpair map
[   15.901514] ath: Country alpha2 being used: 00
[   15.901515] ath: Regpair used: 0x65
[  362.072549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)


########## wireless info END ############
```

---

### Post by Bucky Ball on 2015-04-13
Get online with your wireless and try [this]("http://ubuntuforums.org/showthread.php?t=2260232&p=13204600&viewfull=1#post13204600"). If it doesn't work, keep following that thread and see if you get anywhere. 

PS: Please use [code] tags for terminal output. See the last link in my signature for how. ;)

---

### Post by TheFu on 2015-04-13
What troubleshooting have you done?
Did you check the logs? Anything there?

Looks like the wired adapter isn't being discovered at boot. The driver isn't in the list of output above.  That is an issue.[B]

sudo lshw -C network[/B] will let us see if anything is recognized.

---

### Post by nitin7 on 2015-04-14
*-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:4d:d8:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-49-generic firmware=N/A ip=172.16.216.137 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0400000-c040ffff
~

---

### Post by nitin7 on 2015-04-14
output for loading drivers

```

```

nitin@nitin-Satellite-C640:~$ sudo modprobe -v ath9k
[sudo] password for nitin: 
nitin@nitin-Satellite-C640:~$ sudo modprobe -v alx
insmod /lib/modules/3.13.0-49-generic/kernel/drivers/net/mdio.ko 
insmod /lib/modules/3.13.0-49-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko 
nitin@nitin-Satellite-C640:~$ sudo depmod -a
nitin@nitin-Satellite-C640:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic
nitin@nitin-Satellite-C640:~$

---

### Post by Bucky Ball on 2015-04-14
Once again, please use code tags for terminal output. See last link in my signature for how. 

Looks like you successfully installed something, but you might need to give us a bit more information about what you're doing. Is that from the link I posted? 

Shutdown, plug the ethernet cable in, boot up, run 'sudo lshw -C network' again, as this:

```
*-network UNCLAIMED
description: Ethernet controller
product: AR8152 v2.0 Fast Ethernet
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:01:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0
resources: memory:c0500000-c053ffff ioport:2000(size=128)
```

... shows the machine sees the ethernet card fine, but no driver. Note the wireless has:

```
driver=ath9k 
```

Surprised the driver for your ethernet is not part of the kernel also.

---

### Post by TheFu on 2015-04-14
> **Bucky Ball said:**
> Once again, please use code tags for terminal output. See last link in my signature for how. 

Looks like you successfully installed something, but you might need to give us a bit more information about what you're doing. Is that from the link I posted? 

Shutdown, plug the ethernet cable in, boot up, run 'sudo lshw -C network' again, as this:

```
*-network UNCLAIMED
description: Ethernet controller
product: AR8152 v2.0 Fast Ethernet
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:01:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0
resources: memory:c0500000-c053ffff ioport:2000(size=128)
```

... shows the machine sees the ethernet card fine, but no driver. Note the wireless has:

```
driver=ath9k 
```

Surprised the driver for your ethernet is not part of the kernel also.


Yep - that's the issue. No driver for the "AR8152 v2.0 Fast Ethernet" card.
+1 on the **code tags** too.
[http://ubuntuforums.org/showthread.php?t=2173582&page=2](http://ubuntuforums.org/showthread.php?t=2173582&page=2) has the same device.  It would only work with 1 or the other enabled. They had to disable wifi for the wired connection to work. It also lists the driver which is NOT "alx" for the wired ethernet.

---

### Post by nitin7 on 2015-04-17
I have tried things suggested in other threads but nothing seems to be working. I have loaded the drivers but it is of no use. On rebooting everytime it says waiting for network configuration. On rebooting I am starting the wifi using the command c```
sudo service network-manager restart
``` I am getting connected through wifi but not through wired connection

output of the command ```
ifconfig -a
``` gives only information about loopback and wlan0. It is NOT detecting eth0

I have also tried to reinstall linux-generic package as suggested in some threds but still on reboot network-manager does not start automatically.

output of the command ```
sudo lshw -C network
``` is as follows
```
*-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:4d:d8:ef
       width: 64 bits
       clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-43-generic firmware=N/A ip=172.16.233.244 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0400000-c040ffff


```

---

### Post by nitin7 on 2015-04-18
I am following the instructions given in the thread

 [http://ubuntuforums.org/showthread.php?t=2173582&page=2](http://ubuntuforums.org/showthread.php?t=2173582&page=2)

```

nitin@nitin-Satellite-C640:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


```

```
 nitin@nitin-Satellite-C640:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```
```
nitin@nitin-Satellite-C640:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
nitin@nitin-Satellite-C640:~$ 
```


```
nitin@nitin-Satellite-C640:~$ lsmod | grep ath
ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
nitin@nitin-Satellite-C640:~$ 

```

---

### Post by TheFu on 2015-04-18
To be very clear.....
until the correct driver for "AR8152 v2.0 Fast Ethernet" is loaded, NOTHING related to your wired ethernet connection will work. NetworkManager and rc.local have ZERO to do with this.

[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx) says you need the atl1c driver.

So ... as a stretch guess - disconnect from the wifi network then run **sudo modprobe atl1c**, then run **sudo lshw -C network** and let's see if that loaded the driver or not.  Don't know why this driver is in the blacklist - /etc/modprobe.d/blacklist-ethernet.conf on the first pg shows it is. You'll want to remove that line from the file.  Searching ... says that driver is known to lock up a boot sequence, so it might be smart to blacklist is and manually load the driver later.  I've seen references to using "jockey" to select specific drivers manually as needed.  Don't know anything about that.

If there are errors, please copy/paste the cmd and output back here (code-tags please).

---

### Post by nitin7 on 2015-04-18
I run the command without the wifi.
here is the output for 
```
   nitin@nitin-Satellite-C640:~$ sudo modprobe alt1c 
 modprobe: FATAL: Module alt1c not found.


```

and the output for sudo lshw -C network is
```
    *-network UNCLAIMED      
        description: Ethernet controller 
        product: AR8152 v2.0 Fast Ethernet 
        vendor: Qualcomm Atheros 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        version: c1 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress vpd bus_master cap_list 
        configuration: latency=0 
        resources: memory:c0500000-c053ffff ioport:2000(size=128) 
   *-network DISABLED 
        description: Wireless interface 
        product: AR9285 Wireless Network Adapter (PCI-Express) 
        vendor: Qualcomm Atheros 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: wlan0 
        version: 01 
        serial: 74:de:2b:4d:d8:ef 
        width: 64 bits 
        clock: 33MHz 
  capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=ath9k driverversion=3.13.0-49-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:17 memory:c0400000-c040ffff
 


```

kindly suggest further. On rebooting it is still showing waiting for network configuration

---

### Post by nitin7 on 2015-04-18
PLZ ignore my last post I made a typographic error instead of atl1c I typed alt1c
here is the correct output for the commands
```
nitin@nitin-Satellite-C640:~$ sudo modprobe atl1c
[sudo] password for nitin: 
nitin@nitin-Satellite-C640:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:dd:cc:f3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:c0500000-c053ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:4d:d8:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-49-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0400000-c040ffff
nitin@nitin-Satellite-C640:~
```

But this time My wifi got connected automatically. I did not have to  write the command ```
sudo service network-manager restart
```

---

### Post by TheFu on 2015-04-18
```
modprobe: FATAL: Module alt1c not found.
``` is the issue here.
My 14.04 box has that driver, so I don't know what is up there. Hopefully, it is on the machine and the blacklist is stopping it.  

Do you have the atl1c driver for the kernel you are running?  I do.
```
$ locate atl1c
/lib/modules/3.13.0-46-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-46-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/3.13.0-48-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-48-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/3.13.0-49-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-49-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/usr/src/linux-headers-3.13.0-46/drivers/net/ethernet/atheros/atl1c
/usr/src/linux-headers-3.13.0-46/drivers/net/ethernet/atheros/atl1c/Makefile
/usr/src/linux-headers-3.13.0-46-generic/include/config/atl1c.h
/usr/src/linux-headers-3.13.0-48/drivers/net/ethernet/atheros/atl1c
/usr/src/linux-headers-3.13.0-48/drivers/net/ethernet/atheros/atl1c/Makefile
/usr/src/linux-headers-3.13.0-48-generic/include/config/atl1c.h
/usr/src/linux-headers-3.13.0-49/drivers/net/ethernet/atheros/atl1c
/usr/src/linux-headers-3.13.0-49/drivers/net/ethernet/atheros/atl1c/Makefile
/usr/src/linux-headers-3.13.0-49-generic/include/config/atl1c.h

```

So - look in your kernel /lib/modules/.... atheros/ for the driver. I didn't do anything to put them there and don't have that NIC here, so it must be installed by default. If you don't know about **locate** - you can check the manpage, but you can look for the driver anyway you like.

---

### Post by nitin7 on 2015-04-18
Sir, I wrongly typed alt1c but when I typed atl1c i am getting no errors. As suggested here is the output of locate atl1c command
```
nitin@nitin-Satellite-C640:~$ locate atl1c
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/Makefile
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/nitin/Desktop/AAA/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/Makefile
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/nitin/compat-drivers-2013-03-04-u/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/Makefile
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/nitin/compat-drivers-3.9-rc4-2-su/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/lib/modules/3.13.0-43-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-43-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/3.13.0-48-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-48-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/3.13.0-49-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.13.0-49-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/3.2.0-61-generic/kernel/drivers/net/ethernet/atheros/atl1c
/lib/modules/3.2.0-61-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/usr/src/linux-headers-3.13.0-48/drivers/net/ethernet/atheros/atl1c
/usr/src/linux-headers-3.13.0-48/drivers/net/ethernet/atheros/atl1c/Makefile
/usr/src/linux-headers-3.13.0-48-generic/include/config/atl1c.h
/usr/src/linux-headers-3.13.0-49/drivers/net/ethernet/atheros/atl1c
/usr/src/linux-headers-3.13.0-49/drivers/net/ethernet/atheros/atl1c/Makefile
/usr/src/linux-headers-3.13.0-49-generic/include/config/atl1c.h
nitin@nitin-Satellite-C640:~$ 


```

---

### Post by Bucky Ball on 2015-04-18
What happens when you reboot with the cable plugged in?

---

### Post by nitin7 on 2015-04-23
Even if the cable is plugged in it shows "Waiting for Network configuration", on reboot. I have to give the command to start art wifi. It doesnt detect wired setting.```
sudo service network-manager restart
``` Kindly suggest.

---

