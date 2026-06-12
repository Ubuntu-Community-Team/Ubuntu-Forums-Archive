---
title: "Ubuntu 14.04.3 - Qualcomm Atheros - Lenovo z51 - wireless not working"
date: 2015-09-23
forum: Networking &amp; Wireless
---

### Post by saptarshi2 on 2015-09-23
I am new to ubuntu and have installed Ubuntu 14.04.3 on my new Lenovo z51-70 and the wireless is not working. 



```
########## wireless info START ##########


Report from: 23 Sep 2015 14:36 IST +0530


Booted last: 23 Sep 2015 14:18 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo Device [17aa:3826]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]


04:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] [1002:6820] (rev ff)


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57267308 (57.2 MB)  TX bytes:2358463 (2.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       751     1  0 14:18 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############

```

---

### Post by jeremy31 on 2015-09-23
I found a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940) and patched backports, the instructions
```
sudo apt-get install build-essential linux-headers-$(uname -r)
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget https://www.dropbox.com/s/gyuvdlhzx5ho277/backports-20150731.tar.gz
tar -zxvf backports-20150731.tar.gz
cd backports-20150731
make defconfig-ath10k
make
sudo make install
git clone https://github.com/atondwal/ath10k-firmware.git
sudo cp -r /ath10k-firmware/ath10k/ /lib/firmware/
```


Reboot and test, if ```
lspci -nnk | grep -iA2 net
``` shows nothing for kernel driver in use try ```
sudo modprobe ath10k_pci
```

---

### Post by saptarshi2 on 2015-09-23
lspci -nnk | grep -iA2 net
threw this

```
:~$ lspci -nnk | grep -iA2 net02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo Device [17aa:3826]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]
	Kernel driver in use: ath10k_pci

```

---

### Post by jeremy31 on 2015-09-23
Edited code in other post to fix command ```
make defconfig-ath10k
```

---

### Post by saptarshi2 on 2015-09-23
Thanks for your help, Jeremy.

but, I followed ll the steps carefully and have posted the output of 

[COLOR=#000000]lspci -nnk | grep -iA2 net

in the post above.

After sudo modprobe ath10k_pci I rebooted the system and it still doesnt work.[/COLOR]

---

### Post by jeremy31 on 2015-09-23
Run the wireless script again and post the new results

---

### Post by saptarshi2 on 2015-09-25
Ran the script again

```



########## wireless info START ##########


Report from: 25 Sep 2015 22:25 IST +0530


Booted last: 25 Sep 2015 21:25 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo Device [17aa:3826]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
ath10k_pci             45056  0 
ath10k_core           278528  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              643072  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:593776 (593.7 KB)  TX bytes:124591 (124.5 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       797     1  0 21:25 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
srcversion:     546811EFF3C7A8D4FB20A07
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     B8B903F0D843C312F7FCB10
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
srcversion:     94D2A0276F31273C6A42278
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6BE4ED42578C9DFBE16CE50
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    4.126977] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    4.316256] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    4.316584] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    4.316586] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[    4.316591] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board.bin failed with error -2
[    4.316592] ath10k_pci 0000:03:00.0: failed to fetch generic board data: -2
[    4.316593] ath10k_pci 0000:03:00.0: failed to fetch board file: -2
[    4.316594] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    4.316596] ath10k_pci 0000:03:00.0: could not probe fw (-2)


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-09-25
I noticed the newest backports has the correct patch, so I will show you how to uninstall my patched version and install the new backports
```
cd backports-20150731
```
```
sudo make uninstall
```
Reboot
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz
tar -zxvf backports-20150903.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
```

Reboot

---

### Post by saptarshi2 on 2015-09-25
Still isnt working

Re-ran the same script.

```


########## wireless info START ##########


Report from: 26 Sep 2015 02:45 IST +0530


Booted last: 26 Sep 2015 02:43 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo Device [17aa:3826]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1009 errors:0 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942807 (942.8 KB)  TX bytes:157383 (157.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       721     1  0 02:43 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    4.338934] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    4.344858] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    4.344861] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[    4.344878] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board.bin failed with error -2
[    4.344880] ath10k_pci 0000:03:00.0: failed to fetch generic board data: -2
[    4.344882] ath10k_pci 0000:03:00.0: failed to fetch board file: -2
[    4.344884] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    4.344886] ath10k_pci 0000:03:00.0: could not probe fw (-2)


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-09-25
Ok, lets change the firmware
```
rm -r ath10k-firmware
```
```
git clone https://github.com/kvalo/ath10k-firmware.git
```
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp -r /ath10k-firmware/ /lib/firmware/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

Reboot[/FONT][/COLOR]

---

### Post by saptarshi2 on 2015-09-25
Where am I removing the '[COLOR=#000000][FONT=Ubuntu Mono]ath10k-firmware' from?[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-09-25
Home directory, if any questions about write protected files show up, press y then enter

---

### Post by saptarshi2 on 2015-09-25
There was no ath10k-firmware folder on my system, used 'locate' command.

I downloaded the new one from git and placed it in /lib/firmware/ directly and rebooted the system. 

If this helps,
```



########## wireless info START ##########


Report from: 26 Sep 2015 03:40 IST +0530


Booted last: 26 Sep 2015 03:36 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3826]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:499 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168976 (168.9 KB)  TX bytes:139219 (139.2 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       809     1  0 03:36 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    4.217493] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    4.219201] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    4.219207] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[    4.219217] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board.bin failed with error -2
[    4.219219] ath10k_pci 0000:03:00.0: failed to fetch generic board data: -2
[    4.219222] ath10k_pci 0000:03:00.0: failed to fetch board file: -2
[    4.219224] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    4.219226] ath10k_pci 0000:03:00.0: could not probe fw (-2)


########## wireless info END ############



```

It still isnt working, I might have not done what you intended in this step, the folder I could not find and have placed the new one directly under /lib/firmware/

Is this what you intended?

---

### Post by jeremy31 on 2015-09-25
Noticed something in the latest script results post ```
ls /lib/firmware/ath10k/QCA6174
``` and ```
ls /lib/firmware/ath10k/QCA6164
```

---

### Post by saptarshi2 on 2015-09-25
```

ls /lib/firmware/ath10k/QCA6174
hw3.0

```

```

ls /lib/firmware/ath10k/QCA6164
hw2.1

```

---

### Post by jeremy31 on 2015-09-25
```
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
```
reboot and post a new wireless script report if it doesn't work

---

### Post by saptarshi2 on 2015-09-25
Annnnnnd it worked!!! Thanks!

Any detail i need to keep in mind as a noob?
Any parting word of advice?

---

### Post by jeremy31 on 2015-09-25
Don't delete the backports-20150903 folder, if Ubuntu installs a kernel update you will lose wireless unless the kernel update contains the fix.
If you lose wireless after an update
```

cd backports-20150903
make clean
make defconfig-ath10k
make
sudo make install
```

Then you should be able to reboot to working wireless

Thank you so much for putting up with this and can you post a wireless script result with it working as there might be errors that can be ignored and use the 'thread tools' menu at the top of the page to 'mark as solved' if you are happy with the result

---

### Post by awcjack on 2015-09-26
I have the same problem of this topic
Can you help?
The same system(Ubuntu 14.04)
But different laptop (Qualcomm Atheros - Lenovo U41)
But I found that the Lan card is the same.
So that I did the same thing, after it , I found that it haven't /lib/firmware/ath10k/QCA6164 but have [/FONT][FONT=Ubuntu Mono]/lib/firmware/ath10k/QCA899A
So I tried to use QCA899A instead of QCA6164
hw2.0 instead of hw2.1
But failed to use wireless.
So I want to ask about any other method to do the same thing?
Thank you~;)
If reply in this post is no allowed to ask this question, please tell me and open a new topic.


```
########## wireless info START ##########

Report from: 26 Sep 2015 20:13 HKT +0800

Booted last: 26 Sep 2015 20:07 HKT +0800

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:381e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
wmi                    20480  0 
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64514 (64.5 KB)  TX bytes:14522 (14.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       908     1  0 20:07 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [&#26377;&#32218;&#32178;&#32097;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: Asia/Hong_Kong (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)

[ath]
filename:       /lib/modules/3.19.0-25-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-25-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-25-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N

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

[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist ideapad-laptop
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
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

[/etc/modprobe.d/broadcom.conf]
blacklist ssb

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   12.612274] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   13.276395] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.297368] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   13.297371] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[   14.649823] ath10k_pci 0000:02:00.0: firmware crashed! (uuid f4953f54-b27d-4472-b818-1cd3d218ccb9)
[   14.649834] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   14.649836] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   14.652168] ath10k_pci 0000:02:00.0: firmware register dump:
[   14.652171] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   14.652173] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x88685006
[   14.652175] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   14.652178] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   14.652180] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[   14.652182] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   14.652184] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A508BF8 0xC00A012D
[   14.652186] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   14.652188] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   14.652190] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   14.652192] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   14.652194] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   14.652196] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   14.652198] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   14.652201] ath10k_pci 0000:02:00.0: [56]: 0xFD384A00 0x273263A5 0xB7CD1D5F 0x5FD878D6
[   15.647588] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   16.648544] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   16.648549] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   16.725208] ath10k_pci 0000:02:00.0: could not init core (-110)
[   16.725229] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   16.732726] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started

########## wireless info END ############

```

---

### Post by jeremy31 on 2015-09-26
```
[COLOR=#000000][FONT=Ubuntu Mono]git clone https://github.com/atondwal/ath10k-firmware.git
[/FONT][/COLOR]sudo cp -r ath10k-firmware/ /lib/firmware/
rm -r ath10k-firmware/

git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/QCA6174/
```
Reboot
I am not sure why it is defined as a QCA6164 device in the source code and looks for firmware in the QCA6174 directory

---

### Post by awcjack on 2015-09-26
Thx for replying
but result is like that
meaning of &#26222;&#36890;&#27284;&#26696; i think is similar to something haven't blocked. And I can delete in manually so that I delete it manually and git clone from [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)

```
chan@chan-Lenovo-U41-70:~$ git clone https://github.com/atondwal/ath10k-firmware.gitCloning into 'ath10k-firmware'...
remote: Counting objects: 209, done.
remote: Total 209 (delta 0), reused 0 (delta 0), pack-reused 209
Receiving objects: 100% (209/209), 4.27 MiB | 1.30 MiB/s, done.
Resolving deltas: 100% (68/68), done.
Checking connectivity... done.
chan@chan-Lenovo-U41-70:~$ sudo cp -r ath10k-firmware/ /lib/firmware/
[sudo] password for chan: 
chan@chan-Lenovo-U41-70:~$ rm -r ath10k-firmware/
rm: remove write-protected &#26222;&#36890;&#27284;&#26696; ‘ath10k-firmware/.git/objects/pack/pack-682a34d5b9d5757117b8200e7999f75f757d0cbf.pack’? 
rm: remove write-protected &#26222;&#36890;&#27284;&#26696; ‘ath10k-firmware/.git/objects/pack/pack-682a34d5b9d5757117b8200e7999f75f757d0cbf.idx’? 
rm: cannot remove ‘ath10k-firmware/.git/objects/pack’: Directory not empty
chan@chan-Lenovo-U41-70:~$ git clone https://github.com/kvalo/ath10k-firmware.git
fatal: destination path 'ath10k-firmware' already exists and is not an empty directory.
chan@chan-Lenovo-U41-70:~$ git clone https://github.com/kvalo/ath10k-firmware.git
Cloning into 'ath10k-firmware'...
remote: Counting objects: 220, done.
remote: Total 220 (delta 0), reused 0 (delta 0), pack-reused 220
Receiving objects: 100% (220/220), 4.46 MiB | 981.00 KiB/s, done.
Resolving deltas: 100% (76/76), done.
^[[3~Checking connectivity... done.
chan@chan-Lenovo-U41-70:~$ sudo cp -r ath10k-firmware/ /lib/firmware/
chan@chan-Lenovo-U41-70:~$ cd /lib/firmware/ath10k/QCA6164
bash: cd: /lib/firmware/ath10k/QCA6164: No such file or directory



```

---

### Post by jeremy31 on 2015-09-26
Messed up the command somehow
But when it displays ```
[COLOR=#000000][FONT=Ubuntu Mono]rm: remove write-protected &#26222;&#36890;&#27284;&#26696; &#8216;ath10k-firmware/.git/objects/pack/pack-682a34d5b9d5757117b8200e7999f75f757d0cbf.pack&#8217;? [/FONT][/COLOR]rm: remove write-protected &#26222;&#36890;&#27284;&#26696; &#8216;ath10k-firmware/.git/objects/pack/pack-682a34d5b9d5757117b8200e7999f75f757d0cbf.idx&#8217;? 
``` Press y then enter

[code]rm -r ath10k-firmware

[COLOR=#000000][FONT=Ubuntu Mono]git clone https://github.com/atondwal/ath10k-firmware.git
[/FONT][/COLOR]sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
rm -r ath10k-firmware/

git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/QCA6174/

---

### Post by awcjack on 2015-09-26
[INDENT]This time copy correctly but not functioned :(
this is the new information
[/INDENT]
```


########## wireless info START ##########


Report from: 26 Sep 2015 21:25 HKT +0800


Booted last: 26 Sep 2015 21:22 HKT +0800


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:381e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12605 (12.6 KB)  TX bytes:21038 (21.0 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       908     1  0 21:22 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [&#26377;&#32218;&#32178;&#32097;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Hong_Kong (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist ideapad-laptop
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
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


[/etc/modprobe.d/broadcom.conf]
blacklist ssb


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   14.140207] Bluetooth: hci0: don't support firmware rome 0x200


########## wireless info END ############


```[INDENT]
[/INDENT]

---

### Post by jeremy31 on 2015-09-26
You had a kernel update the latest script report shows 3.19.0-28 and your original report shows 3.19.0-25, so
```
[COLOR=#000000][FONT=Ubuntu Mono]cd backports-20150903
[/FONT][/COLOR]make clean
make defconfig-ath10k
make
sudo make install
```
Reboot

---

### Post by awcjack on 2015-09-26
This is the output during type that command
```
chan@chan-Lenovo-U41-70:~$ cd backpots-20150903bash: cd: backpots-20150903: No such file or directory
chan@chan-Lenovo-U41-70:~$ cd backports-20150903
chan@chan-Lenovo-U41-70:~/backports-20150903$ make clean
Generating local configuration database from kernel ... done.
chan@chan-Lenovo-U41-70:~/backports-20150903$ make defconfig-ath10k
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
chan@chan-Lenovo-U41-70:~/backports-20150903$ make
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/chan/backports-20150903/compat/main.o
  CC [M]  /home/chan/backports-20150903/compat/backport-4.0.o
  CC [M]  /home/chan/backports-20150903/compat/backport-4.1.o
  CC [M]  /home/chan/backports-20150903/compat/backport-4.2.o
  CC [M]  /home/chan/backports-20150903/compat/backport-4.3.o
  CC [M]  /home/chan/backports-20150903/compat/lib-rhashtable.o
  LD [M]  /home/chan/backports-20150903/compat/compat.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/main.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/regd.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/hw.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/key.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/dfs_pattern_detector.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/dfs_pri_detector.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/mac.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/debug.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/core.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/htc.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/htt.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/htt_rx.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/htt_tx.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/txrx.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/wmi.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/wmi-tlv.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/bmi.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/hw.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/p2p.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/swap.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/spectral.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/thermal.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/wow.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_core.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/pci.o
  CC [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ce.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_pci.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/main.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/status.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/driver-ops.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/sta_info.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/wep.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/wpa.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/scan.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/offchannel.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/ht.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/agg-tx.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/agg-rx.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/vht.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/ibss.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/iface.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/rate.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/michael.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/tkip.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/aes_ccm.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/aes_gcm.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/aes_cmac.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/aes_gmac.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/cfg.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/ethtool.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/rx.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/spectmgmt.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/tx.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/key.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/util.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/wme.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/event.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/chan.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/trace.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mlme.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/tdls.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/ocb.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/led.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh_plink.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh_hwmp.o
/home/chan/backports-20150903/net/mac80211/mesh_hwmp.c: In function &#8216;mesh_rx_path_sel_frame&#8217;:
/home/chan/backports-20150903/net/mac80211/mesh_hwmp.c:603:26: warning: &#8216;target_metric&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]
    mesh_path_sel_frame_tx(MPATH_PREP, 0, orig_addr,
                          ^
/home/chan/backports-20150903/net/mac80211/mesh_hwmp.c:533:36: note: &#8216;target_metric&#8217; was declared here
  u32 orig_sn, target_sn, lifetime, target_metric;
                                    ^
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh_sync.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/mesh_ps.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/pm.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/chan/backports-20150903/net/mac80211/rc80211_minstrel_ht.o
  LD [M]  /home/chan/backports-20150903/net/mac80211/mac80211.o
  CC [M]  /home/chan/backports-20150903/net/wireless/core.o
  CC [M]  /home/chan/backports-20150903/net/wireless/sysfs.o
  CC [M]  /home/chan/backports-20150903/net/wireless/radiotap.o
  CC [M]  /home/chan/backports-20150903/net/wireless/util.o
  CC [M]  /home/chan/backports-20150903/net/wireless/reg.o
  CC [M]  /home/chan/backports-20150903/net/wireless/scan.o
  CC [M]  /home/chan/backports-20150903/net/wireless/nl80211.o
  CC [M]  /home/chan/backports-20150903/net/wireless/mlme.o
  CC [M]  /home/chan/backports-20150903/net/wireless/ibss.o
  CC [M]  /home/chan/backports-20150903/net/wireless/sme.o
  CC [M]  /home/chan/backports-20150903/net/wireless/chan.o
  CC [M]  /home/chan/backports-20150903/net/wireless/ethtool.o
  CC [M]  /home/chan/backports-20150903/net/wireless/mesh.o
  CC [M]  /home/chan/backports-20150903/net/wireless/ap.o
  CC [M]  /home/chan/backports-20150903/net/wireless/trace.o
  CC [M]  /home/chan/backports-20150903/net/wireless/ocb.o
  CC [M]  /home/chan/backports-20150903/net/wireless/wext-compat.o
  CC [M]  /home/chan/backports-20150903/net/wireless/wext-sme.o
  LD [M]  /home/chan/backports-20150903/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 6 modules
  CC      /home/chan/backports-20150903/compat/compat.mod.o
  LD [M]  /home/chan/backports-20150903/compat/compat.ko
  CC      /home/chan/backports-20150903/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath.ko
  CC      /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_core.mod.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_core.ko
  CC      /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_pci.mod.o
  LD [M]  /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
  CC      /home/chan/backports-20150903/net/mac80211/mac80211.mod.o
  LD [M]  /home/chan/backports-20150903/net/mac80211/mac80211.ko
  CC      /home/chan/backports-20150903/net/wireless/cfg80211.mod.o
  LD [M]  /home/chan/backports-20150903/net/wireless/cfg80211.ko
chan@chan-Lenovo-U41-70:~/backports-20150903$ sudo make install
[sudo] password for chan: 
  Building modules, stage 2.
  MODPOST 6 modules
  INSTALL /home/chan/backports-20150903/compat/compat.ko
Can't read private key
  INSTALL /home/chan/backports-20150903/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_core.ko
Can't read private key
  INSTALL /home/chan/backports-20150903/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
Can't read private key
  INSTALL /home/chan/backports-20150903/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/chan/backports-20150903/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.19.0-28-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.


Your backported driver modules should be installed now.
Reboot.


chan@chan-Lenovo-U41-70:~/backports-20150903$ 



```




This is new info

```


########## wireless info START ##########


Report from: 26 Sep 2015 22:09 HKT +0800


Booted last: 26 Sep 2015 22:08 HKT +0800


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:381e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         94208  0 
ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3080 (3.0 KB)  TX bytes:10444 (10.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       839     1  0 22:08 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [&#26377;&#32218;&#32178;&#32097;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Hong_Kong (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist ideapad-laptop
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
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


[/etc/modprobe.d/broadcom.conf]
blacklist ssb


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   15.215324] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   15.340839] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   15.340845] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[   16.753711] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 78869a82-4251-4c14-bf0f-c5e30b4d0482)
[   16.753718] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   16.753720] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   16.756040] ath10k_pci 0000:02:00.0: firmware register dump:
[   16.756043] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   16.756045] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x88685006
[   16.756047] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   16.756048] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   16.756050] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[   16.756051] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   16.756052] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A508BF8 0xC00A012D
[   16.756054] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   16.756055] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   16.756056] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   16.756058] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.756059] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   16.756060] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   16.756062] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.756063] ath10k_pci 0000:02:00.0: [56]: 0xFD384A00 0x273263A5 0xB7CD1D5F 0x5FD878D6
[   17.753214] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   18.754253] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   18.754258] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   18.832406] ath10k_pci 0000:02:00.0: could not init core (-110)
[   18.832439] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   18.858411] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


########## wireless info END ############



```



But still cannot use the wifi :(

---

### Post by jeremy31 on 2015-09-26
I wonder if the firmware copy did work correctly ```
md5sum /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin; ls /lib/firmware/ath10k/QCA6174/hw2.1/
```

---

### Post by awcjack on 2015-09-26
```
8f5303e4b1afc818798425a700139133 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
board.bin firmware-5.bin
```

---

### Post by jeremy31 on 2015-09-26
Found a bug report with similar issue ```
echo "options ath10k_pci irq_mode=1" | sudo tee /etc/modprobe.d/ath10k_pci.conf
```
Reboot

---

### Post by awcjack on 2015-09-26
eth0      no wireless extensions.


lo        no wireless extensions.

Still keeping this result.....:cry:

```


########## wireless info START ##########


Report from: 26 Sep 2015 22:56 HKT +0800


Booted last: 26 Sep 2015 22:54 HKT +0800


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]
	Kernel driver in use: ath10k_pci


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:381e]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4384 (4.3 KB)  TX bytes:10611 (10.6 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       875     1  0 22:54 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [&#26377;&#32218;&#32178;&#32097;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Hong_Kong (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 1
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/ath10k_pci.conf]
options ath10k_pci irq_mode=1


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist ideapad-laptop
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
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


[/etc/modprobe.d/broadcom.conf]
blacklist ssb


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   15.091815] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   15.175657] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   15.175662] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[   16.454482] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 86cbe864-1802-4280-a697-4243b2a7a125)
[   16.454490] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   16.454492] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   16.456813] ath10k_pci 0000:02:00.0: firmware register dump:
[   16.456815] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   16.456816] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x88685006
[   16.456817] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   16.456819] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   16.456820] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[   16.456821] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   16.456823] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A508BF8 0xC00A012D
[   16.456824] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   16.456825] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   16.456827] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   16.456828] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.456829] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   16.456831] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   16.456832] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.456833] ath10k_pci 0000:02:00.0: [56]: 0xFD384A00 0x273263A5 0xB7CD1D5F 0x5FD878D6
[   17.452845] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   18.453909] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   18.453914] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   18.542868] ath10k_pci 0000:02:00.0: could not init core (-110)
[   18.542889] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   18.546044] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


########## wireless info END ############



```

---

### Post by saptarshi2 on 2015-09-26
Jeremy thanks again, here is the script output again, have a look. Will mark as 'SOLVED' once you have reviewed this output.

```



########## wireless info START ##########


Report from: 26 Sep 2015 21:47 IST +0530


Booted last: 26 Sep 2015 20:45 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo Device [17aa:3826]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
	Subsystem: Lenovo Device [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  6 snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95798779 (95.7 MB)  TX bytes:5333272 (5.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"PSR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'PSR' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain.name


##### network managers ##################


Installed:


	NetworkManager


Running:


root       742     1  0 20:45 ?        00:00:02 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [PSR] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Bombay:          Infra, <MAC 'Bombay' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Wifi_111:        Infra, <MAC 'Wifi_111' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA2
    DIRECT-sg-BRAVIA:Infra, <MAC 'DIRECT-sg-BRAVIA' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Amoli Tia Khus-khus: Infra, <MAC 'Amoli Tia Khus-khus' [AC8]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    VEDANT:          Infra, <MAC 'VEDANT' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA
    dlink:           Infra, <MAC 'dlink' [AC14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    pine wood 405:   Infra, <MAC 'pine wood 405' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    *PSR:            Infra, <MAC 'PSR' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Omega_Guest:     Infra, <MAC 'Omega_Guest' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Dean:            Infra, <MAC 'Dean' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Omega_WL:        Infra, <MAC 'Omega_WL' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    NETGEAR88:       Infra, <MAC 'NETGEAR88' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Omega_WL:        Infra, <MAC 'Omega_WL' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Netcafe:         Infra, <MAC 'Netcafe' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    shiran:          Infra, <MAC 'shiran' [AC10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA
    N SINGH...:      Infra, <MAC 'N SINGH...' [AN16]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA2
    dom406mp:        Infra, <MAC 'dom406mp' [AC9]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA2
    CRACK_HIM:       Infra, <MAC 'CRACK_HIM' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Omega_Guest:     Infra, <MAC 'Omega_Guest' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             202.83.21.24
    DNS:             202.83.21.28


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[[/etc/NetworkManager/system-connections/lemons2]] (600 root)
[connection] id=lemons2 | type=802-11-wireless
[802-11-wireless] ssid=lemons2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PSR]] (600 root)
[connection] id=PSR | type=802-11-wireless
[802-11-wireless] ssid=PSR | mac-address=<MAC 'wlan0' [IF]>
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


eth0      no frequency information.


lo        no frequency information.


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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'PSR' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"PSR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000041bf280e3
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Dean' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Dean"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1d491dc7
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Wifi_111' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Wifi_111"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02a18b3e
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Bombay' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Bombay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02df9e96
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'pine wood 405' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"pine wood 405"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f023763cc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Omega_WL' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Omega_WL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cc1efca180
                    Extra: Last beacon: 21168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VEDANT' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"VEDANT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f016f00e0
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Amoli Tia Khus-khus' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Amoli Tia Khus-khus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02df401f
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'dom406mp' [AC9]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"dom406mp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000f168181
                    Extra: Last beacon: 6044ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'shiran' [AC10]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"shiran"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d3894166192
                    Extra: Last beacon: 20868ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'DIRECT-sg-BRAVIA' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-sg-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b24bb020
                    Extra: Last beacon: 6040ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'NETGEAR88' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dd309176
                    Extra: Last beacon: 20756ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Omega_Guest' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Omega_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cc1fdc117f
                    Extra: Last beacon: 6568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'dlink' [AC14]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d18ec18e
                    Extra: Last beacon: 6260ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '' [AC15]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d3894f769a4
                    Extra: Last beacon: 6120ms ago
          Cell 16 - Address: <MAC 'Netcafe' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Netcafe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c677a173
                    Extra: Last beacon: 6064ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0041 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    9.816432] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.053030] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   10.053329] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   10.053331] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[   11.220821] ath10k_pci 0000:03:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   11.220825] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   11.289137] ath: EEPROM regdomain: 0x6c
[   11.289140] ath: EEPROM indicates we should expect a direct regpair map
[   11.289142] ath: Country alpha2 being used: 00
[   11.289143] ath: Regpair used: 0x6c
[   12.615931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.756019] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)! (repeated 2 times)
[   36.725530] wlan0: authenticate with <MAC 'PSR' [AC1]>
[   36.759383] wlan0: send auth to <MAC 'PSR' [AC1]> (try 1/3)
[   36.761044] wlan0: authenticated
[   36.764642] wlan0: associate with <MAC 'PSR' [AC1]> (try 1/3)
[   36.769104] wlan0: RX AssocResp from <MAC 'PSR' [AC1]> (capab=0x411 status=0 aid=1)
[   36.771766] wlan0: associated
[   36.771785] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   84.988986] wlan0: AP <MAC 'PSR' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-09-26
> **saptarshi2 said:**
> Jeremy thanks again, here is the script output again, have a look. Will mark as 'SOLVED' once you have reviewed this output.

```



########## wireless info START ##########


Report from: 26 Sep 2015 21:47 IST +0530


Booted last: 26 Sep 2015 20:45 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3826]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04f2:b50f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
snd_pcm               106496  6 snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95798779 (95.7 MB)  TX bytes:5333272 (5.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"PSR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'PSR' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search domain.name


##### network managers ##################


Installed:


    NetworkManager


Running:


root       742     1  0 20:45 ?        00:00:02 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [PSR] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Bombay:          Infra, <MAC 'Bombay' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    Wifi_111:        Infra, <MAC 'Wifi_111' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA2
    DIRECT-sg-BRAVIA:Infra, <MAC 'DIRECT-sg-BRAVIA' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Amoli Tia Khus-khus: Infra, <MAC 'Amoli Tia Khus-khus' [AC8]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    VEDANT:          Infra, <MAC 'VEDANT' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA
    dlink:           Infra, <MAC 'dlink' [AC14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    pine wood 405:   Infra, <MAC 'pine wood 405' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    *PSR:            Infra, <MAC 'PSR' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Omega_Guest:     Infra, <MAC 'Omega_Guest' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Dean:            Infra, <MAC 'Dean' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Omega_WL:        Infra, <MAC 'Omega_WL' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    NETGEAR88:       Infra, <MAC 'NETGEAR88' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Omega_WL:        Infra, <MAC 'Omega_WL' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Netcafe:         Infra, <MAC 'Netcafe' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    shiran:          Infra, <MAC 'shiran' [AC10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA
    N SINGH...:      Infra, <MAC 'N SINGH...' [AN16]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA2
    dom406mp:        Infra, <MAC 'dom406mp' [AC9]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA2
    CRACK_HIM:       Infra, <MAC 'CRACK_HIM' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Omega_Guest:     Infra, <MAC 'Omega_Guest' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             202.83.21.24
    DNS:             202.83.21.28


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[[/etc/NetworkManager/system-connections/lemons2]] (600 root)
[connection] id=lemons2 | type=802-11-wireless
[802-11-wireless] ssid=lemons2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PSR]] (600 root)
[connection] id=PSR | type=802-11-wireless
[802-11-wireless] ssid=PSR | mac-address=<MAC 'wlan0' [IF]>
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


eth0      no frequency information.


lo        no frequency information.


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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'PSR' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"PSR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000041bf280e3
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Dean' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Dean"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1d491dc7
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Wifi_111' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Wifi_111"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02a18b3e
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Bombay' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Bombay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02df9e96
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'pine wood 405' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"pine wood 405"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f023763cc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Omega_WL' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Omega_WL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cc1efca180
                    Extra: Last beacon: 21168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VEDANT' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"VEDANT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f016f00e0
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Amoli Tia Khus-khus' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Amoli Tia Khus-khus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f02df401f
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'dom406mp' [AC9]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"dom406mp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000f168181
                    Extra: Last beacon: 6044ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'shiran' [AC10]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"shiran"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d3894166192
                    Extra: Last beacon: 20868ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'DIRECT-sg-BRAVIA' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-sg-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b24bb020
                    Extra: Last beacon: 6040ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'NETGEAR88' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007dd309176
                    Extra: Last beacon: 20756ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Omega_Guest' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Omega_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cc1fdc117f
                    Extra: Last beacon: 6568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'dlink' [AC14]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d18ec18e
                    Extra: Last beacon: 6260ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '' [AC15]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d3894f769a4
                    Extra: Last beacon: 6120ms ago
          Cell 16 - Address: <MAC 'Netcafe' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Netcafe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003c677a173
                    Extra: Last beacon: 6064ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


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
blacklist ideapad-laptop


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0041 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    9.816432] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.053030] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   10.053329] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   10.053331] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[   11.220821] ath10k_pci 0000:03:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   11.220825] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   11.289137] ath: EEPROM regdomain: 0x6c
[   11.289140] ath: EEPROM indicates we should expect a direct regpair map
[   11.289142] ath: Country alpha2 being used: 00
[   11.289143] ath: Regpair used: 0x6c
[   12.615931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.756019] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)! (repeated 2 times)
[   36.725530] wlan0: authenticate with <MAC 'PSR' [AC1]>
[   36.759383] wlan0: send auth to <MAC 'PSR' [AC1]> (try 1/3)
[   36.761044] wlan0: authenticated
[   36.764642] wlan0: associate with <MAC 'PSR' [AC1]> (try 1/3)
[   36.769104] wlan0: RX AssocResp from <MAC 'PSR' [AC1]> (capab=0x411 status=0 aid=1)
[   36.771766] wlan0: associated
[   36.771785] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   84.988986] wlan0: AP <MAC 'PSR' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)


########## wireless info END ############



```

Thanks for posting that, if you have issues with disconnect or slow wifi, change the wifi routers encryption to WPA2 only, it might be called WPA2-AES or WPA2-PSK in the router settings.  Right now it is showing TKIP as group cipher for your connection

---

### Post by jeremy31 on 2015-09-26
> **awcjack said:**
> eth0      no wireless extensions.


lo        no wireless extensions.

Still keeping this result.....:cry:

```


########## wireless info START ##########


Report from: 26 Sep 2015 22:56 HKT +0800


Booted last: 26 Sep 2015 22:54 HKT +0800


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:381e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 5986:0670 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
ath10k_pci             45056  0 
ath10k_core           290816  1 ath10k_pci
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 28672  4 cfg80211,mac80211,ath10k_pci,ath10k_core
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4384 (4.3 KB)  TX bytes:10611 (10.6 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       875     1  0 22:54 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [&#26377;&#32218;&#32178;&#32097;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


##### iw reg get ########################


Region: Asia/Hong_Kong (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,compat,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)


[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 1
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
skip_otp: Y
uart_print: N


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


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/ath10k_pci.conf]
options ath10k_pci irq_mode=1


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist ideapad-laptop
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
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


[/etc/modprobe.d/broadcom.conf]
blacklist ssb


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   15.091815] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   15.175657] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   15.175662] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[   16.454482] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 86cbe864-1802-4280-a697-4243b2a7a125)
[   16.454490] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   16.454492] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   16.456813] ath10k_pci 0000:02:00.0: firmware register dump:
[   16.456815] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   16.456816] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x88685006
[   16.456817] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   16.456819] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   16.456820] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[   16.456821] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   16.456823] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A508BF8 0xC00A012D
[   16.456824] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   16.456825] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   16.456827] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   16.456828] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.456829] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   16.456831] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   16.456832] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   16.456833] ath10k_pci 0000:02:00.0: [56]: 0xFD384A00 0x273263A5 0xB7CD1D5F 0x5FD878D6
[   17.452845] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   18.453909] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   18.453914] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   18.542868] ath10k_pci 0000:02:00.0: could not init core (-110)
[   18.542889] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   18.546044] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


########## wireless info END ############



```

I must have gotten the commands mixed and you have the wrong firmware
```
rm -r ath10k-firmware
git clone https://github.com/atondwal/ath10k-firmware.git
cd ath10k-firmware/ath10k/QCA6164
sudo rm -r /lib/firmware/ath10k/QCA6174/hw2.1
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
```

I hope that finally fixes it and we can remove one thing before a reboot
```
sudo rm /etc/modprobe.d/ath10k_pci.conf
```

Reboot and cross fingers

---

### Post by awcjack on 2015-09-26
I tried re-copy the QCX6164 to QCX6174  again yesterday 
It work correctly now.
Thanks for your help;)

---

### Post by jeremy31 on 2015-09-26
Good to hear finally

---

### Post by sarthak3 on 2015-10-02
hey im new to linux ..
i read and tried to fix the wlan issue for mine but cant
can you please give exact steps ive to follow

QCA6164,lenovo Z51-70
directly installed gnome15.04 and updates via software updater

---

### Post by QIII on 2015-10-02
@sarthak3:

Please do not hijack threads.  Please start your own.  Feel free to refer to this thread as a reference.

---

### Post by sarthak3 on 2015-10-03
> **QIII said:**
> @sarthak3:

Please do not hijack threads.  Please start your own.  Feel free to refer to this thread as a reference.
sry about that.. totally a new user unaware of rules  :)

---

