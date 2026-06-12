---
title: "No Wired or Wireless connection on Ubuntu 14.04"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by Creatorr on 2014-09-28
```

 
########## wireless info START ##########
 
Report from: 29 Sep 2014 01:38 IST +0530
 
Booted last: 29 Sep 2014 01:02 IST +0530
 
Script from: 20 Sep 2014 23:04 UTC +0000
 
##### release ###########################
 
Distributor ID:    Ubuntu
Description:        Ubuntu 14.04.1 LTS
Release:               14.04
Codename:        trusty
 
##### kernel ############################
 
Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=7
 
##### desktop ###########################
 
Ubuntu
 
##### lspci #############################
 
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
                Subsystem: Dell Device [1028:04b0]
 
09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
                Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD] [1028:0205]
 
0b:00.0 USB controller [0c03]: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller [104c:8241] (rev 02)
 
##### lsusb #############################
 
Bus 002 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 002 Device 003: ID 8564:1000 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2188:0ae1 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc.
Bus 001 Device 003: ID 0cf3:3002 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
##### PCMCIA card info ##################
 
##### rfkill ############################
 
##### lsmod #############################
 
##### interfaces ########################
 
auto lo
iface lo inet loopback
 
##### ifconfig ##########################
 
##### iwconfig ##########################
 
lo        no wireless extensions.
 
##### route #############################
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 
##### resolv.conf #######################
 
##### nm-tool ###########################
 
NetworkManager Tool
 
State: disconnected
 
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
 
[[/etc/NetworkManager/system-connections/Kaveri]] (600 root)
[connection] id=Kaveri | type=802-11-wireless
[802-11-wireless] ssid=Kaveri | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto
 
##### iw reg get ########################
 
nl80211 not found.
 
##### iwlist channels ###################
 
lo        no frequency information.
 
##### iwlist scan #######################
 
lo        Interface doesn't support scanning.
 
##### module infos ######################
 
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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
 
##### dmesg #############################
 
########## wireless info END ############

```  I'm completely new user of ubuntu.
As per your "No- Internet GUI  Method" gave me above [COLOR=#000000]"[/COLOR]**wireless-info.txt"  file .**  

Please help...Thanks in advance!!!!

---

### Post by Creatorr on 2014-09-28
```
[COLOR=#000000][FONT=Ubuntu Mono]########## wireless info START ##########[/FONT][/COLOR][COLOR=#000000] 
Report from: 29 Sep 2014 01:38 IST +0530
 
Booted last: 29 Sep 2014 01:02 IST +0530
 
Script from: 20 Sep 2014 23:04 UTC +0000
 
##### release ###########################
 
Distributor ID:    Ubuntu
Description:        Ubuntu 14.04.1 LTS
Release:               14.04
Codename:        trusty
 
##### kernel ############################
 
Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=7
 
##### desktop ###########################
 
Ubuntu
 
##### lspci #############################
 
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
                Subsystem: Dell Device [1028:04b0]
 
09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
                Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD] [1028:0205]
 
0b:00.0 USB controller [0c03]: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller [104c:8241] (rev 02)
 
##### lsusb #############################
 
Bus 002 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 002 Device 003: ID 8564:1000 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2188:0ae1 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc.
Bus 001 Device 003: ID 0cf3:3002 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
##### PCMCIA card info ##################
 
##### rfkill ############################
 
##### lsmod #############################
 
##### interfaces ########################
 
auto lo
iface lo inet loopback
 
##### ifconfig ##########################
 
##### iwconfig ##########################
 
lo        no wireless extensions.
 
##### route #############################
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 
##### resolv.conf #######################
 
##### nm-tool ###########################
 
NetworkManager Tool
 
State: disconnected
 
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
 
[[/etc/NetworkManager/system-connections/Kaveri]] (600 root)
[connection] id=Kaveri | type=802-11-wireless
[802-11-wireless] ssid=Kaveri | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto
 
##### iw reg get ########################
 
nl80211 not found.
 
##### iwlist channels ###################
 
lo        no frequency information.
 
##### iwlist scan #######################
 
lo        Interface doesn't support scanning.
 
##### module infos ######################
 
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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
 
##### dmesg #############################
 
########## wireless info END ############
[FONT=Verdana]
```[/FONT][/COLOR]
[COLOR=#000000]I'm completely new user of ubuntu.[/COLOR]
[COLOR=#000000]As per your "No- Internet GUI Method" gave me above [/COLOR][COLOR=#000000][COLOR=#000000]"[/COLOR][/COLOR][B]wireless-info.txt" file . 

Please help...Thanks in advance!!!![/B]

---

### Post by coffeecat on 2014-09-29
@Creatorr, I've moved your two posts to their own thread. Please do not post your questions to others' threads - this simply confuses things. In the case of the Asus thread it appears that you are probably not running an Asus anyway. And please do not post duplicates in different parts of the forum. This dilutes community effort.

---

### Post by varunendra on 2014-09-29
Thank you for the move coffeecat! I was just waiting for it. :)

Creatorr, first of all, Welcome to the forums!

What coffeecat suggested above is the best way to get help.

Regarding the problem - Is this installation of 14.04.1 an upgrade from a previous version? The udev rules file section suggests that this installation did have both wired and wireless connections detected and possibly working earlier. Please confirm whether they did or not, and whether it is a clean installation or an upgrade.

In any case, it seems to be a seriously broken kernel issue. If it is a clean installation, check your installation media for defects : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is an upgrade, or broke after a simple update, try reinstalling your kernel. Try this first -
```
sudo apt-get install --reinstall linux-image-$(uname -r)
```
Watch the output closely and report back if you see any errors. If not, reboot and hopefully you'll have your networking (and other broken stuff) back.

If it returns any errors, further steps would depend upon the error message you get. Please try to quote them exactly in your next post. If it is NOT about lack of free space, you can manually download the kernel *(linux-image-3.13.0-36-generic_3.13.0-36.63_amd64.deb)* from [here]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/"), then install it with either double-click, or with the command -
```
sudo dpkg -i **Desktop/**linux-image*.deb
```
..assuming you have copied the downloaded .deb file onto your Desktop. You will then need to reboot.

---

### Post by Creatorr on 2014-09-29
[ATTACH=CONFIG]256814[/ATTACH][ATTACH=CONFIG]256815[/ATTACH]Dear Varun,
Thanks for answering to my thread but problem isn't yet solved.

Both wired and wireless connections  were working earlier
And neither I got any Error while executing any of both command. I'm attaching snapshots for each.
```
sudo apt-get install --reinstall linux-image-$(uname -r)


```

```
  sudo dpkg -i **Desktop/**linux-image*.deb
```
[ATTACH=CONFIG]256816[/ATTACH][ATTACH=CONFIG]256817[/ATTACH][ATTACH=CONFIG]256818[/ATTACH][ATTACH=CONFIG]256819[/ATTACH]


While executing above command I was not having Internet Connection.Is that required????


Yesterday I had upgraded and updated my Ubuntu 14.04.01 LTS.  "Booting fom the DVD" method was followed to install it.
Even I had edited .bashrc file to add PATH for installing NS2. Is that the cause of problem???

---

### Post by varunendra on 2014-09-29
Not sure about the .bashrc change, but the screenshots show everything went okay. Now after a reboot, do you still not get either wifi or ethernet? If so, please post a fresh report of the wireless_script.

The attachment links in your post don't work by the way. What were they?

---

