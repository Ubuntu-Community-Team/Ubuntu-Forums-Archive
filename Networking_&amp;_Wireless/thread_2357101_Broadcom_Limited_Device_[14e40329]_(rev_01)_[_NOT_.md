---
title: "Broadcom Limited Device [14e4:0329] (rev 01) [ NOT in list ]"
date: 2017-03-29
forum: Networking &amp; Wireless
---

### Post by balise on 2017-03-29
Ubuntu 14.04.  Tried "apt install firmware-b43-installer" anyway.
Which completed, but after re-booting nothing is apparent.  :confused:

---

### Post by RobGoss on 2017-03-30
Try this
```
sudo apt-get install firmware-b43-installer
```

---

### Post by chili555 on 2017-03-30
I love new devices! Let's see some diagnostics:```
lspci -nnk | grep -e 0200 -e 0280 -A2
dmesg | grep -i 14e4
```Thanks.

---

### Post by balise on 2017-03-31
'fraid not.  I've successfully installed b43, but does not work with '0329' device :(

---

### Post by RobGoss on 2017-03-31
Have you tried installing  the proprietary drivers in the Ubuntu repository

You will need to wired and have a Internet connection in order to download the necessary drivers for your machine

Go to Software & updates and click on  Additional drivers, let it search for the appropriate drivers for your machine

---

### Post by chili555 on 2017-03-31
I'd be anxious to help solve this if I had the data I requested above.

I doubt that either the proprietary STA driver or firmware are correct here.

---

### Post by balise on 2017-03-31
I had never used the 'additional drivers' thing, now I see what it's for.  It reverted me to 'bcmwl-kernel-source', but there must be another step, I think.  Or, and I'm thinking more likely (the board is large with an extra Linksys box on it, although three antennae), that it's just *really* legacy.

---

### Post by RobGoss on 2017-03-31
Please see **chili555** post **#3** also he might have a better solution to your issue as far as installing the drivers needed for the WiFi

The process of installing additional drivers are pretty straightforward

---

### Post by balise on 2017-03-31
Well the most daunting thing is that the :0329 part of the device is unknown by Broadcom or internet.  i.e. could not find Windows drivers even.

---

### Post by Hadaka on 2017-03-31
Hi Balise, please open a terminal ctrl/alt/t then Copy and past the following...
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This command will build a file in your home directory titled **wireless-info.txt** Please copy and paste the file so that we may help in providing you
with a solution to your wifi problem.
thanks

---

### Post by balise on 2017-03-31
```
########## wireless info START ##########

Report from: 31 Mar 2017 14:43 PDT -0700

Booted last: 31 Mar 2017 12:07 PDT -0700

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.4.0-71-generic #92~14.04.1-Ubuntu SMP Fri Mar 24 15:22:50 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169

06:02.0 Network controller [0280]: Broadcom Limited Device [14e4:0329] (rev 01)
    Subsystem: Linksys Device [1737:0060]

3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c61] (rev 05)

##### lsusb #############################

Bus 002 Device 008: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 006: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 007: ID 03f0:8b07 Hewlett-Packard 
Bus 002 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 002 Device 004: ID 0a16:2005 Trek Technology (S) PTE, Ltd 
Bus 002 Device 003: ID 03f0:3d17 Hewlett-Packard LaserJet P1005
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID b58e:9e84 Blue Microphones Yeti Stereo Microphone
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wl                   6365184  0 
cfg80211              561152  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback
##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17515568 (17.5 MB)  TX bytes:4306026 (4.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:346954 (346.9 KB)  TX bytes:346954 (346.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       921     1  0 12:07 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s
  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             64.59.144.90
    DNS:             64.59.150.136

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

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-71-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.4.0-71-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-71-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A7DC879B6551813C20004F1
depends:        
intree:         Y
vermagic:       4.4.0-71-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   21.548679] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.551941] wl: module verification failed: signature and/or required key missing - tainting kernel
[   27.216840] r8169 0000:02:00.0 eth0: link down
[   27.216895] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.217306] r8169 0000:02:00.0 eth0: link down
[   32.727750] r8169 0000:02:00.0 eth0: link up
[   32.727764] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2017-03-31
@Hadaka-

Please note:> 06:02.0 Network controller [0280]: Broadcom Limited Device [14e4:0329] (rev 01)
[COLOR="#FF0000"]Subsystem: Linksys Device [1737:0060][/COLOR]I see many references to 14e4:***4***329 and ***Subsystem: Linksys Device [1737:0060]*** on the various forums; here, for example: [https://ubuntuforums.org/showthread.php?t=1837779](https://ubuntuforums.org/showthread.php?t=1837779) and here: [https://forums.linuxmint.com/viewtopic.php?t=72619](https://forums.linuxmint.com/viewtopic.php?t=72619)

I suspect this is not a new device but a device with a glitch in the silicon or perhaps an experimental or pre-production piece. We see that sometimes when replacement cards are bought from dubious far east sources. I doubt that is the case here.

I suggest that we try to work out how to get this recognized as a new_id. Off to dine with Mrs. Chili or I'd start on it myself.

---

### Post by Hadaka on 2017-03-31
Hi, Thank you for posting the diagnostic wireless-info report. As Dr. Chili555 points out
it looks like you have a unique wifi card that will require some experimental tinkering to
hopefully get it going. Please post the output of..
```
iwconfig
ifconfig
cat /etc/udev/rules.d/70-persistent-net.rules
```
You currently have the "wl" wifi driver loaded per the report and it was also noted that
the country code was unset, this also has an effect on wireless. Let's put that in place
while we continue doing some research on your wifi card. please Copy and paste.
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
Also, just to see...lets purge the wl driver and load the b43
please copy and past, and also ignore any errors or file not found
do each line one at a time even if you get an error...it is expected.
From a working wired connection please do...
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
remove wired connection,boot and test wireless.
report back please
thanks.

---

### Post by balise on 2017-03-31
Done this:  (sorry for enormous length) ..

```

 c-art home/jae %     iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

 c-art home/jae %     ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:b7:09:6b  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:feb7:96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105579018 (105.5 MB)  TX bytes:16302647 (16.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:757719 (757.7 KB)  TX bytes:757719 (757.7 KB)

 c-art home/jae %     cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="bc:ae:c5:b7:09:6b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
 c-art home/jae % sudo iw reg set US
[sudo] password for jae: 
 c-art home/jae % sudo sed -i 's/=.*/=US/' /etc/default/crda
 c-art home/jae % 
 c-art home/jae % 
 c-art home/jae % sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [https://repo.skype.com](https://repo.skype.com) stable InRelease                                    
Hit [https://repo.skype.com](https://repo.skype.com) stable/main amd64 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [https://deb.nodesource.com](https://deb.nodesource.com) trusty InRelease                                
Hit [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main Sources                             
Hit [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main amd64 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main i386 Packages                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:1 [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Ign [https://deb.nodesource.com](https://deb.nodesource.com) trusty/main Translation-en                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Get:2 [https://repo.skype.com](https://repo.skype.com) stable/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages             
Ign [https://repo.skype.com](https://repo.skype.com) stable/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Ign [https://repo.skype.com](https://repo.skype.com) stable/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Reading package lists... Done                                                  
 c-art home/jae % 
 c-art home/jae % 
 c-art home/jae % sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms imagemagick-common kodi-bin libcec3 libcrossguid1 libgexiv2-2 libgif5
  liblockdev1 liblqr-1-0 libmagickcore5 libmagickcore5-extra libmagickwand5
  libmicrohttpd10 libnetpbm10 libnfs1 libpcrecpp0 libraw9 libsdl2-2.0-0
  libshairplay0 libtar0 libva-intel-vaapi-driver linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic netpbm python-bluez python-simplejson
  shotwell-common vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 8,045 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 485884 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic
 c-art home/jae % 
 c-art home/jae % 
 c-art home/jae % sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
 c-art home/jae % 
 c-art home/jae % sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms imagemagick-common kodi-bin libcec3 libcrossguid1 libgexiv2-2 libgif5
  liblockdev1 liblqr-1-0 libmagickcore5 libmagickcore5-extra libmagickwand5
  libmicrohttpd10 libnetpbm10 libnfs1 libpcrecpp0 libraw9 libsdl2-2.0-0
  libshairplay0 libtar0 libva-intel-vaapi-driver linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic netpbm python-bluez python-simplejson
  shotwell-common vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/30.4 kB of archives.
After this operation, 154 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 485807 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a018-2_amd64.deb ...
Unpacking b43-fwcutter (1:018-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a018-2_all.deb ...
Unpacking firmware-b43-installer (1:018-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up b43-fwcutter (1:018-2) ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2017-03-31 18:15:37--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com]("http://www.lwfinger.com") ([www.lwfinger.com]("http://www.lwfinger.com"))... 173.254.28.119
Connecting to [www.lwfinger.com]("http://www.lwfinger.com") ([www.lwfinger.com)|173.254.28.119|:80]("http://www.lwfinger.com)|173.254.28.119|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;

100%[==============================================>] 13,514,651   444KB/s   in 27s    

2017-03-31 18:16:04 (482 KB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
 c-art home/jae % 
 c-art home/jae % 
 c-art home/jae % sudo modprobe b43
 c-art home/jae % 
 c-art home/jae % 

```

Then, switch off computer including power, re-seated the
"0329" PCI device, and rebooted.  No change that I see, but
how do I test wireless?

-jae

---

### Post by wildmanne39 on 2017-03-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by balise on 2017-03-31
Copy & will do.  Rookie at this sort of thing ..

---

### Post by chili555 on 2017-04-01
You have presented us with an interesting problem, sir. The problem is, how do we trick the driver to get a device working that is not included by default in the driver files. 

Some background information for the benefit of you and the inevitable searchers. When the system boots and sees PCI and USB and some other devices, the vendor, product and subsytem identifiers are consulted to see if an available driver should be loaded. Here is an example from the message log on my machine:```
[    0.821381] pci 0000:03:00.0: [[COLOR="#FF0000"]8086:08b2[/COLOR]] type 00 class 0x028000
```The system sees that there is a driver matching the device:```
filename:       /lib/modules/4.9.0-040900-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-IWL6000G2B_UCODE_API_MAX.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-26.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-26.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-26.ucode
firmware:       iwlwifi-8000C--26.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--26.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--26.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--26.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--26.ucode
srcversion:     3C3F30F1C18A1B3790B3E1C
<snip>
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]08B2[/COLOR]sv*sd0000C220bc*sc*i*
<snip>
```So, it loads the driver, creates an interface, Network Manager connects, etc.```
[    5.598067] iwlwifi 0000:03:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    5.647843] [COLOR="#FF0000"]iwlwifi[/COLOR] 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.649730] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.649991] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.991533] iwlwifi 0000:03:00.0[COLOR="#FF0000"] wlp3s0[/COLOR]: renamed from wlan0

```Since your device has a glitchy identifier, the usual driver doesn't attach.

Let's see if we can trick it. This is purely experimental; it may or may not work. We haven't the device so we can't, as we usually like to do, test it for you in advance of proposing a solution.

Please open a terminal and do: ```
sudo -i
modprobe wl
echo "14e4 0329"  >  /sys/bus/pci/drivers/wl/new_id
exit
```Was an interface created?```
ifconfig
```Any clues in the log?```
dmesg | grep wl
```

---

### Post by balise on 2017-04-01
No joy I'm afraid:

 ```
 
 c-art home/jae % sudo -i
[sudo] password for jae: 
 ROOT /root # 
 ROOT /root # modprobe wl
modprobe: FATAL: Module wl not found.
 ROOT /root # echo "14e4 0329" > /sys/bus/pci/drivers/wl/new_id
-bash: /sys/bus/pci/drivers/wl/new_id: No such file or directory
 ROOT /root # 
 ROOT /root # ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:b7:09:6b  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:feb7:96b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:928197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:510432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:656822460 (656.8 MB)  TX bytes:72556055 (72.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2625429 (2.6 MB)  TX bytes:2625429 (2.6 MB)

 ROOT /root # dmesg | grep wl
[    1.428193] usb 2-1.2: Manufacturer: Hewlett-Packard
 ROOT /root #


```

---

### Post by chili555 on 2017-04-01
Have you, in all your struggles, removed bcmwl-kernel-source?

Please reinstall it:```
sudo apt-get install bcmwl-kernel-source
```Reboot and try again:```
sudo -i
modprobe wl
echo "14e4 0329"  >  /sys/bus/pci/drivers/wl/new_id
exit
```

---

### Post by balise on 2017-04-02
Reinstall:

```

 c-art home/jae % sudo apt-get install bcmwl-kernel-source
[sudo] password for jae: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  imagemagick-common kodi-bin libcec3 libcrossguid1 libgexiv2-2 libgif5
  liblockdev1 liblqr-1-0 libmagickcore5 libmagickcore5-extra libmagickwand5
  libmicrohttpd10 libnetpbm10 libnfs1 libpcrecpp0 libraw9 libsdl2-2.0-0
  libshairplay0 libtar0 libva-intel-vaapi-driver linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic netpbm python-bluez python-simplejson
  shotwell-common vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/1,511 kB of archives.
After this operation, 8,045 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 485819 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-71-generic
Building for architecture x86_64
Building initial module for 4.4.0-71-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-71-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic
 c-art home/jae % 

```

And then rebooted, and 

```
 c-art home/jae % sudo -i
[sudo] password for jae: 
 ROOT /root # modprobe wl
 ROOT /root # echo "14e4 0329" > /sys/bus/pci/drivers/wl/new_id
 ROOT /root # exit
logout
 c-art home/jae % 
 c-art home/jae % dmesg | grep wl
[    1.428186] usb 2-1.2: Manufacturer: Hewlett-Packard
[   21.245185] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.245190] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.245191] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.253208] wl: module verification failed: signature and/or required key missing - tainting kernel
 c-art home/jae % 

```

---

### Post by chili555 on 2017-04-02
> **balise said:**
> Reinstall:

```

 <snip>

And then rebooted, and 

[code] c-art home/jae % sudo -i
[sudo] password for jae: 
 ROOT /root # modprobe wl
 ROOT /root # echo "14e4 0329" > /sys/bus/pci/drivers/wl/new_id
 ROOT /root # exit
logout
 c-art home/jae % 
 c-art home/jae % dmesg | grep wl
[    1.428186] usb 2-1.2: Manufacturer: Hewlett-Packard
[   21.245185] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.245190] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.245191] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.253208] wl: module verification failed: signature and/or required key missing - tainting kernel
 c-art home/jae % 

```Look's great so far. Was a wireless interface created?```
iwconfig
```

---

### Post by balise on 2017-04-02
> **chili555 said:**
> Look's great so far. Was a wireless interface created?```
iwconfig
```
```
 
 c-art home/jae % iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

 c-art home/jae % 

```

Is that definitive?

---

### Post by chili555 on 2017-04-03
> Is that definitive?It is, actually. It is definite that I know of no way to get a new identifier added to the driver *wl.* 

I suggest that you buy some other wireless card for your computer and replace the Broadcom. You might face the problem of whitelisting. [http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/)

You might also look into a USB wireless. Several of us here use this; it works out of the box: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/)

I regret that I have no other suggestions.

---

### Post by balise on 2017-04-03
Thanks for help!  Think that USB thingy is what I'm ordering ..

---

### Post by RobGoss on 2017-04-03
I use a belkin WiFi dongle on one of my older machines and it works with out any issues

---

