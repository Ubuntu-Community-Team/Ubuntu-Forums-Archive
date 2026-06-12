---
title: "Wireless connection not working after installing ubuntu 14.04"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by kashif3 on 2014-06-07
Hi, I installed new version of ubuntu 14.04 on my Dell vostro 1500 laptop. The wired internet connection is working but can't setup the wirless connection. 

Just in case I am using Broadcom pci card number BCM4401-BO.

Any help would be appriciated. Thanks

---

### Post by Hadaka on 2014-06-07
hi, please open a terminal  ctrl/alt/t  then COPY
and paste the following...
 ```
 lspci -n | egrep '0200|0280' | awk '{print$3}'
``` 
post the output
thanks

---

### Post by kashif3 on 2014-06-07
Hi, 

11ab:4354
14e4:4315

thanks

---

### Post by Hadaka on 2014-06-07
Hi, with the ethernet cable connected to the internet
please do.```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot
then do
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
disconnect the cable and test wireless
thanks

---

### Post by kashif3 on 2014-06-09
Hi, I still couldn't able to connect to wireless connection. 
After coding
sudo apt-get remove --purge bcmwl-kernel-source

I get the following output

Reading package lists... Done
Building state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade

And after reboot and then coded


sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

Got the following output:

Reading package lists... Done
Building state information... Done
linux-firmware-nonfree is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade
......nothing happened with sudo modprobe b43.

then taken out the cable tested the wireless connection by going into edit connections as couldn't find the auto detection of wireless connections.

Thanks

---

### Post by Hadaka on 2014-06-09
Hi, with the ethernet cable connected and connected to the internet
please do.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by kashif3 on 2014-06-10
Hi, Still the same after I executed the above commands in terminal window one after the other by connecting to cable, mean internet is working when connected through cable.

But no wireless connection. I edited the connections and put all the wireless internet connection details manually but not show up any sign of wireless connection.

Thanks

---

### Post by kc1di on 2014-06-10
would you post the output of ```
rf kill list all 
``` Thanks

---

### Post by Hadaka on 2014-06-10
Hi, Let's run Varun's handy dandy wireless diagnostic
script. go here ->[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)
read carefully...follow the simple directions and post
back the data from the ->   wireless-info.txt <-

---

### Post by kashif3 on 2014-06-11
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux javaria-Vostro-1500 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44

0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

No way to aquire root rights found.

##### iwlist channel #####

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### lsmod #####

iwl3945                73259  0 
iwlegacy              100569  1 iwl3945
mac80211              626557  2 iwl3945,iwlegacy
cfg80211              484040  3 iwl3945,iwlegacy,mac80211
ssb                    62379  1 b44

##### modinfo #####

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     C93C31FCEBBAE1F376E495F
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    3.458150] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    3.458175] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    3.458193] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    3.458213] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    3.496347] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.517456] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   18.015195] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.015207] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.015373] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.144897] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.144907] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.145038] iwl3945 0000:0c:00.0: irq 44 for MSI/MSI-X
[   18.289043] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   24.182231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.812248] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   27.812268] b44 ssb0:0 eth0: Flow control is off for TX and off for RX

########## wireless info END ############

```

---

### Post by Hadaka on 2014-06-11
Hi, when i first asked you to show me your network cards,,you reported
11ab:4354 Marvell ethernet card
14e4:4315 Broadcom wireless card 

i next asked you to run a wireless script and you post..
[14e4:170c] Broadcom ethernet card
[8086:4222] Intel wireless card

Exactly how am i suppose to find the trouble if you are changeing out your cards ??????

you also now have a hardblock in your rfkill list

hold down the FN key and press the F2 key  ONE  time
boot
if it does not clear the block, i can think of nothing else i can do for you
good luck.

---

### Post by kashif3 on 2014-06-11
Hi, What I did is copy the wireless_script from other computer as a text file and then emailed to myself.

Then downloaded the file from the troubled computer (by ethernet cable connected internet) and then ran the script on this troubled computer whose wireless card is not working.

I don't know why the Ethernet card names been changed. I haven't changed the the cards.

Also the command
rf kill list all 
doesnt work it says, rf: command not found

I also did the last step which you told me but no luck.(i.e hold down the FN key and press the F2 key  ONE  time
boot)

Anyway thanks for your help, no problem I will try to see what else I can do to enable the wireless.

---

### Post by kc1di on 2014-06-11
Hi Again,
that script show among other thing that you have a hard block on your wireless. 

> ##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Which means there is a switch somewhere to turn the wireless on your machine on and off.  
On my Dell it's the FN F2 Combination.  You'll have to look at the manual or help on your machine to find where it is. but you need to turn it 
back on in order for Wireless to be recognized. 
Good Luck

---

### Post by jeremy31 on 2014-06-11
> **kashif3 said:**
> Hi, What I did is copy the wireless_script from other computer as a text file and then emailed to myself.

Then downloaded the file from the troubled computer (by ethernet cable connected internet) and then ran the script on this troubled computer whose wireless card is not working.

I don't know why the Ethernet card names been changed. I haven't changed the the cards.

Also the command
rf kill list all 
doesnt work it says, rf: command not found

I also did the last step which you told me but no luck.(i.e hold down the FN key and press the F2 key  ONE  time
boot)

Anyway thanks for your help, no problem I will try to see what else I can do to enable the wireless.

```
rfkill list all
```  the wireless script will have to done different.  On computer with internet run ```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script 
```
Send it to the problem computer and put it in home directory and ```
chmod +x wireless_script && ./wireless_script
```
Then send the results back to the computer that works

---

### Post by kashif3 on 2014-06-12
Thanks [URL="http://ubuntuforums.org/member.php?u=1839"][COLOR=#000000]kc1di

[/COLOR]That exactly was the case....wifi switch was off.[/URL]
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1839")
problem solved ... sign of relief:lolflag:

---

### Post by kc1di on 2014-06-12
Your Welcome, Enjoy ;)

---

