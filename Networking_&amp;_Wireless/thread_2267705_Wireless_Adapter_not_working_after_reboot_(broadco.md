---
title: "Wireless Adapter not working after reboot (broadcom)"
date: 2015-03-03
forum: Networking &amp; Wireless
---

### Post by Jack_Pytel on 2015-03-03
Good morning,

I've been using Ubuntu for about a week now. Still a newbie. One reoccurring issue that's been happening is that my broadcom wireless adapter has been loosing(?) a driver, if that makes sense. I end up having to either use Ethernet cable, or using a lovely Linksys adapter in order to get the driver back. I usually either use the system update menu to restore the wireless card back to normal, or the command line to download the bcmwl-kernel-source. Being a newbie it's hard to resolve such an issue. I've looked around the internet and didn't find a definitive answer. I'm hoping one of you can help me out.


Thanks,

Jack

PS:

Here's the wireless script output:

```
 
########## wireless info START ##########
 
Report from: 03 Mar 2015 09:34 CST -0600
 
Booted last: 03 Mar 2015 09:15 CST -0600
 
Script from: 20 Sep 2014 23:04 UTC +0000
 
##### release ###########################
 
Distributor ID:    Ubuntu
Description:        Ubuntu 14.04.1 LTS
Release:               14.04
Codename:        trusty
 
##### kernel ############################
 
Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=7
 
##### desktop ###########################
 
sed: can't read /root/.dmrc: No such file or directory
Could not be determined.
 
##### lspci #############################
 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
                Subsystem: Lite-On Communications Inc Device [11ad:6605]
                Kernel driver in use: bcma-pci-bridge
 
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
                Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
                Kernel driver in use: r8169
 
##### lsusb #############################
 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57b4 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 04ca:2006 Lite-On Technology Corp.
Bus 001 Device 004: ID 154b:0095 PNY
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
##### PCMCIA card info ##################
 
##### rfkill ############################
 
0: asus-wlan: Wireless LAN
                Soft blocked: no
                Hard blocked: no
1: asus-bluetooth: Bluetooth
                Soft blocked: no
                Hard blocked: no
 
##### lsmod #############################
 
bcma                   52096  0
asus_nb_wmi            16990  0
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
video                  19476  3 i915,nouveau,asus_wmi
 
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
 
##### iwconfig ##########################
 
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
##### route #############################
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 
##### resolv.conf #######################
 
##### nm-tool ###########################
 
NetworkManager Tool
 
State: disconnected
 
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
 
[[/etc/NetworkManager/system-connections/21805Access]] (600 root)
[connection] id=21805Access | type=802-11-wireless
[802-11-wireless] ssid=21805Access | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto
 
[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto
 
[[/etc/NetworkManager/system-connections/21805Access 1]] (600 root)
[connection] id=21805Access 1 | type=802-11-wireless
[802-11-wireless] ssid=21805Access | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto
 
##### iw reg get ########################
 
Region: America/Chicago (based on set time zone)
 
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
 
[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:       
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
 
##### module parameters #################
 
##### /etc/modules ######################
 
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
 
##### rc.local ##########################
 
exit 0
 
##### pm-utils ##########################
 
##### udev rules ########################
 
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
 
##### dmesg #############################
 
########## wireless info END ############
 

```

---

### Post by chili555 on 2015-03-03
Please open a terminal, hook up the ethernet temporarily and do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Please note and post any errors. If none, reboot and let us hear the result.

---

### Post by Jack_Pytel on 2015-03-03
As stated before, I have "sudo apt-get update" and "sudo apt-get install bcmwl-kernel-source" before to get my driver; however, after a few restarts the wireless adapter goes back to not working. I've seen threads online that it happens to people, it's just that everybody provides a different solution which doesn't really solve anything. My solution so far was just to carry around a wireless adapter and just execute the above commands. Any other ideas?

---

### Post by chili555 on 2015-03-03
While I appeciate what you are saying, I am not interested in what other people suggest that's different from above. Clearly, bcmwl-kernel-source was either not installed or installed but blacklisted in your diagnostics above:> Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
                Subsystem: Lite-On Communications Inc Device [11ad:6605]
                [COLOR="#FF0000"]Kernel driver in use: bcma-pci-bridge[/COLOR]So, can you please confirm that *right now * you followed the steps I requested above, rebooted and it doesn't work? Once you can confirm, we can move to the next step in the process.

---

