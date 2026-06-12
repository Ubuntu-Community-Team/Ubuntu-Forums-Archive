---
title: "Wireless not working on Acer aspire E1-571 (i3 ver)"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by davedub on 2014-04-20
Hi all,

Tearing my hair out here, trying to get my Dad's laptop wireless connection working again. The wifi was working when the computer was new (early Feb) and then stopped shortly afterwards. Back then, I booted off an installation cd (we're running 12.04 LTS) and the wifi worked fine. So I booted back into the installed version and all was fine, up until today.

So today I tried the same thing (booted off the installation cd and tried to connect) but that didn't work this time. So I checked and re-installed the drivers as per this page: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

This had no effect either. 
[COLOR=#000000][FONT=Ubuntu Mono]
lspci -nn -d 14e4: [/FONT][/COLOR]gives:

<code>
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
02:00.2 System peripheral [0880]: Broadcom Corporation BCM57765/57785 MS Card Reader [14e4:16be] (rev 10)
02:00.3 System peripheral [0880]: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader [14e4:16bf] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
</code>

Notes:

There's no problem with the router, all other devices work fine.
If the wifi is disabled using the hardware switch, it cannot be turned on again until after a reboot.
Wireless is shown as enabled in the network-manager icon dropdown, but the actual wifi network is not listed.
If I try to connect to the wifi network using 'connect to hidden wifi network' the network-manager icon throbs but never connects (the network is remembered from when it was all up and running). It will sometimes ask for a password after a while, but entering the password leads to a 'network disconnected' popup or it asks for the password again. This process usually takes a minute or two.

It's starting to feel like a dodgy hardware issue, but I'm still a complete Ubuntu noob, so I thought I'd try posting here before I start looking at replacing the wifi card. 

I have to go abroad in a few days, and my Dad really needs his machine up and running before I go - please help!

:-Davedub.co.uk

---

### Post by kc1di on 2014-04-20
Hi davedub 

You need the b43 driver for you card sta/wl does not work well with it.  
do the following from a terminal after connecting to a ethernet cable. 

```
 sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Then reboot it should work.
if it does go to a terminal and
enter
```
rfkill list 
```
and post the output here.

---

### Post by davedub on 2014-04-20
Thanks for the very quick reply!

That didn't work for me, no changes to the situation.
rfkill list output here:

```

:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Hadaka on 2014-04-20
Hi davedub, i am surprised the sticky didnt work for you.
lets take a look at some stuff..
please post the output of..
```
uname -a
lspci -nn | egrep '0200|0280'
lsmod
```
thanks

---

### Post by kc1di on 2014-04-20
list the output of ```
lsmod
```

---

### Post by davedub on 2014-04-20
All three here:
```

@Ubuntu-E1-203:~$ uname -a 
 Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
 @Ubuntu-E1-203:~$ lspci -nn | egrep '0200|0280' 
 02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10) 
 03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01) 
 @Ubuntu-E1-203:~$ lsmod 
 Module                  Size  Used by 
 snd_hda_codec_hdmi     32530  1  
 snd_hda_codec_realtek   224173  1  
 joydev                 17693  0  
 rfcomm                 47604  0  
 bnep                   18281  2  
 bluetooth             180113  10 rfcomm,bnep 
 parport_pc             32866  0  
 ppdev                  17113  0  
 bcma                   26696  0  
 arc4                   12529  2  
 snd_hda_intel          33719  3  
 snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              17764  1 snd_hda_codec 
 snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13324  0  
 snd_rawmidi            30748  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29990  2 snd_pcm,snd_seq 
 psmouse                97519  0  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 uvcvideo               72627  0  
 videodev               98259  1 uvcvideo 
 v4l2_compat_ioctl32    17128  1 videodev 
 brcmsmac              570930  0  
 mac80211              506862  1 brcmsmac 
 brcmutil               15139  1 brcmsmac 
 serio_raw              13211  0  
 soundcore              15091  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 i915                  478556  3  
 drm_kms_helper         46978  1 i915 
 cfg80211              205774  2 brcmsmac,mac80211 
 crc8                   12893  1 brcmsmac 
 cordic                 12574  1 brcmsmac 
 drm                   241971  4 i915,drm_kms_helper 
 i2c_algo_bit           13423  1 i915 
 mei                    41616  0  
 acer_wmi               28418  0  
 sparse_keymap          13890  1 acer_wmi 
 video                  19651  1 i915 
 wmi                    19256  1 acer_wmi 
 mac_hid                13253  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 tg3                   152144  0  
 sdhci_pci              18826  0  
 sdhci                  33205  1 sdhci_pci 0

```

---

### Post by kc1di on 2014-04-20
Go to /etc/modprob.d/blacklist/bcm43-blacklist.conf see if b43 in the list. if it is open gedit as root ```
gksu gedit
``` and place a # sign in front of the line b43 or delete it.
then run these commands again ```
sudo modprobe -rv b43
sudo modprobe -v b43
```
wait a minute or so and see if wireless comes up. 

you may have to reboot.

---

### Post by davedub on 2014-04-21
Hi Dave,

/etc/modprobe.d/blacklist/bcm43-blacklist.conf did not exist. I checked /etc/modprobe.d/blacklist.conf which did have the line, so I tried commenting it out there, but after running the modprobes and restarting nothing changed.

I have un-commented the line 'blacklist b43' in /etc/modprobe.d/blacklist.conf so it's back as it was and re-run the modprobes.

Cheers,

Davedub

---

### Post by Hadaka on 2014-04-21
Hi, give this a go..
```
sudo apt-get update
sudo apt-get upgrade
```
once finished..then do..
```
sudo su
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
 echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit 0
```then do..
```
sudo modprobe -rf bcma
sudo modprobe -v bcma
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac 
```
BOOT

---

### Post by davedub on 2014-04-21
Hi Hadaka,

Done - no change... 

Cheers,

Dave

---

### Post by Hadaka on 2014-04-21
hi , please post the output of..
```
cat /etc/modprobe.d/blacklist.conf | egrep 'ssb|b43|brcmsmac'
```
```
cat /etc/modules
lsmod
```
thanks.

---

### Post by davedub on 2014-04-21
Hi Hadaka,

```

   @Ubuntu-E1-203:~$ cat /etc/modprobe.d/blacklist.conf | egrep 'ssb|b43|brcmsmac' 
 # replaced by b43 and ssb. 
 blacklist b43 
 blacklist ssb 
 blacklist b43 
 blacklist ssb 
 @Ubuntu-E1-203:~$ cat /etc/modules 
 # /etc/modules: kernel modules to load at boot time. 
 # 
 # This file contains the names of kernel modules that should be loaded 
 # at boot time, one per line. Lines beginning with "#" are ignored. 
  
 lp 
 rtc 
 @Ubuntu-E1-203:~$ lsmod 
 Module                  Size  Used by 
 snd_hda_codec_hdmi     32530  1  
 snd_hda_codec_realtek   224173  1  
 joydev                 17693  0  
 bnep                   18281  2  
 rfcomm                 47604  0  
 bluetooth             180113  10 bnep,rfcomm 
 parport_pc             32866  0  
 ppdev                  17113  0  
 bcma                   26696  0  
 arc4                   12529  2  
 snd_hda_intel          33719  3  
 snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              17764  1 snd_hda_codec 
 snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 uvcvideo               72627  0  
 psmouse                97519  0  
 videodev               98259  1 uvcvideo 
 snd_seq_midi           13324  0  
 v4l2_compat_ioctl32    17128  1 videodev 
 serio_raw              13211  0  
 snd_rawmidi            30748  1 snd_seq_midi 
 brcmsmac              570930  0  
 snd_seq_midi_event     14899  1 snd_seq_midi 
 mac80211              506862  1 brcmsmac 
 i915                  478556  3  
 snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event 
 brcmutil               15139  1 brcmsmac 
 snd_timer              29990  2 snd_pcm,snd_seq 
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
 cfg80211              205774  2 brcmsmac,mac80211 
 drm_kms_helper         46978  1 i915 
 crc8                   12893  1 brcmsmac 
 cordic                 12574  1 brcmsmac 
 drm                   241971  4 i915,drm_kms_helper 
 snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              15091  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 i2c_algo_bit           13423  1 i915 
 mei                    41616  0  
 acer_wmi               28418  0  
 sparse_keymap          13890  1 acer_wmi 
 video                  19651  1 i915 
 wmi                    19256  1 acer_wmi 
 mac_hid                13253  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 sdhci_pci              18826  0  
 sdhci                  33205  1 sdhci_pci 
 tg3                   152144  0  
 @Ubuntu-E1-203:~$

```

cheers,

Davedub

---

### Post by Hadaka on 2014-04-21
Hi, please run Varun's script per the instructions here
[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)
thanks.

---

### Post by kc1di on 2014-04-21
Ok, Lets go back to the start.

Do the following, 
Make sure b43 is not blacklisted, Make sure ssb is blacklisted. install b43 fwcutter if not already installed for now uninstall all other broadcom drivers, blacklist the following modules wl or sta. 
reboot see what happens.

---

### Post by davedub on 2014-04-21
Hi all,

Starting with Dave's suggestions, /etc/modprobe.d/blacklist.conf now reads

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
# blacklist b43
blacklist ssb
blacklist wl
blacklist sta

```

not sure on the syntax for installing b43 fwcutter - none of these worked:

```

sudo apt-get install b43 fwcutter
sudo apt-get install b43
sudo apt-get install fwcutter

```


 Not sure how to identify 'other broadcom drivers' either... apologies for noobness!

 

 No change after the /etc/modprobe.d/blacklist.conf changes...


Hadaku's request:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: brcmsmac

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### lsmod #####

bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

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
blacklist ssb
blacklist wl
blacklist sta

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   14.613401] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 11
[   14.613449] brcmsmac 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.613458] brcmsmac 0000:03:00.0: setting latency timer to 64
[   15.564565] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   15.564569] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   15.565675] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   15.565947] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.566101] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

Many thanks for continuing help...

 - Davedub

---

### Post by Hadaka on 2014-04-21
hi , please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
thanks.

---

### Post by Hadaka on 2014-04-21
bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac[COLOR=#ff0000]<--[/COLOR]

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko[COLOR=#ff0000][/COLOR][COLOR=#ff0000]<--[/COLOR]
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v0000[COLOR=#ff0000]14E4[/COLOR]d0000[COLOR=#ff0000]4727[/COLOR]sv*sd*bc*sc*i*[COLOR=#ff0000]<---[/COLOR]
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*

---

### Post by davedub on 2014-04-21
Hi Hadaka,

Tried, but no change. Script output below:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: brcmsmac

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Tile Cottage WiFi] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Tile Cottage WiFi: Infra, <MAC address removed>, Freq 0 MHz, Rate 0 Mb/s, Strength 0 WPA WPA2

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### lsmod #####

bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

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
blacklist ssb
blacklist wl
blacklist sta

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   15.908881] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 11
[   15.908938] brcmsmac 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.908948] brcmsmac 0000:03:00.0: setting latency timer to 64
[   16.691171] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   16.691175] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   16.692259] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   16.692575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.692801] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

### Post by chili555 on 2014-04-21
People!! We have two posters here giving *conflicting* methods to get poor davedub going. First, let's dispose of one myth;  b43 and ssb and firmware are incorrect for this device. The modaliases for b43 and ssb are in ssb. Check here:```
modinfo ssb | grep 4727
```Nothing, nada, zippo. Please abandon b43.

The sticky says bcmwl-kernel-source is correct for kernel versions less than 3.8, which davedub has:> Linux Ubuntu-E1-203 [COLOR="#FF0000"]3.2.0-60[/COLOR]-genericI suggest you download this: [http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)  Be sure to get the 64-bit (amd64) version. Drag and drop it to your desktop.

Since you previously had a version of bcmwl-kernel-source installed, I assume all the prerequisites are also installed.

Install with:```
cd ~/Desktop
sudo dpkg -i bcmwl*.deb
```After it finishes, reboot and let us hear your report. Include:```
nm-tool
```

---

### Post by davedub on 2014-04-21
Hi Chilli555,

Installed:

```

   @Ubuntu-E1-203:~$ cd ~/Desktop  
 @Ubuntu-E1-203:~/Desktop$ sudo dpkg -i bcmwl*.deb  
 [sudo] password for :  
 Selecting previously unselected package bcmwl-kernel-source.  
 (Reading database ... 186131 files and directories currently installed.)  
 Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...  
 Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...  
 Loading new bcmwl-5.100.82.38+bdcom DKMS files...  
 First Installation: checking all kernels...  
 Building only for 3.2.0-60-generic  
 Building for architecture x86_64  
 Building initial module for 3.2.0-60-generic  
 Done.  
 

 wl:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/3.2.0-60-generic/updates/dkms/  
 

 depmod.........  
 

 DKMS: install completed.  
 update-initramfs: deferring update (trigger activated)  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic  
 @Ubuntu-E1-203:~/Desktop$ 

```

wireless info script output

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: brcmsmac

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### lsmod #####

bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist ssb
blacklist wl
blacklist sta

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   14.882600] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 11
[   14.882648] brcmsmac 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.882657] brcmsmac 0000:03:00.0: setting latency timer to 64
[   16.336341] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   16.336346] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   16.337437] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   16.337733] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.337943] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```


nm-tool output

```




@Ubuntu-E1-203:~$ nm-tool 
  
 NetworkManager Tool 
  
 State: connected (global) 
  
 - Device: wlan0 ---------------------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            brcmsmac 
   State:             disconnected 
   Default:           no 
   HW Address:        B<removed>4 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  
  
  
 - Device: eth0  [Auto Ethernet] ------------------------------------------------ 
   Type:              Wired 
   Driver:            tg3 
   State:             connected 
   Default:           yes 
   HW Address:        2<removed>0 
  
   Capabilities: 
     Carrier Detect:  yes 
     Speed:           100 Mb/s 
  
   Wired Properties 
     Carrier:         on 
  
   IPv4 Settings: 
     Address:         192.168.1.77 
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.1.254 
  
     DNS:             192.168.1.254 
  
  
```

Cheers,

Davedub

---

### Post by kc1di on 2014-04-21
> not sure on the syntax for installing b43 fwcutter - none of these worked:

Code:
sudo apt-get install b43 fwcutter
sudo apt-get install b43
sudo apt-get install fwcutter

it's b43-fwcutter 
But Chilli 555 seems to say that the WL driver should work with your card.
so try his suggestion first.

---

### Post by chili555 on 2014-04-21
Poor davedub. You have, I suspect, many conflicting load and blacklist entries that your system is confused. Let's see:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```We may do some surgery here.

---

### Post by davedub on 2014-04-21
Hi Chili,

cat /etc/modprobe.d/blacklist.conf

```

@Ubuntu-E1-203:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
# blacklist b43
blacklist ssb
blacklist wl
blacklist sta

```

cat /etc/modules

```

@Ubuntu-E1-203:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


```

Cheers to all,

 - davedub

---

### Post by chili555 on 2014-04-21
Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Please change the last several lines to read:```
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb
#blacklist wl
blacklist bcma
blacklist brcmsmac
```Proofread carefully, save and close gedit. Reboot with the ethernet detached and let us see again:```
nm-tool
```

---

### Post by davedub on 2014-04-21
Hi Chili

nm-tool out - edited, as I didn't do it with the ethernet cable disconnected first time...

```

@Ubuntu-E1-203:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        B8:76:3F:83:C4:24

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        20:89:84:83:59:10

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```


blacklist.conf included, just in case

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb
#blacklist wl
blacklist bcma
blacklist brcmsmac


```

Cheers!

 - davedub

---

### Post by davedub on 2014-04-21
bump - please?

:-Davedub

---

### Post by Hadaka on 2014-04-21
Hi Dave, please run the script file while we wait for chili555 
 to look at this.  also please do after the script
printout ..
```
grep blacklist /etc/modprobe.d/blacklist.conf
```

---

### Post by davedub on 2014-04-21
Hi Hadaka,

Thanks for getting back to me. Script output:

```

 

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

eth1      No scan results

##### iwlist channel #####

##### lsmod #####

wl                   2568249  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     D9C86A9C5C3D22E103EF402
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   15.205287] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.208726] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.208736] wl 0000:03:00.0: setting latency timer to 64
[   15.545831] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38

########## wireless info END ############
```

blacklist grep:

```

@Ubuntu-E1-203:~$ grep blacklist /etc/modprobe.d/blacklist.conf
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
#blacklist wl
blacklist bcma
blacklist brcmsmac


```

:-Davedub

---

### Post by chili555 on 2014-04-21
Let's try another package, young Dave. With a working ethernet:```
sudo apt-get purge bcmwl-kernel-source
wget http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
sudo dpkg -i bcmwl*.deb
```Detach the ethernet, reboot and cross your fingers!!

---

### Post by Hadaka on 2014-04-21
please also do...
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot
thanks.

---

### Post by davedub on 2014-04-21
Hi All,

I ran Chili's commands and rebooted. All references to the wireless network disappeared from the network-manager icon dropdown.

I then ran Hadaka's command and re-booted. No change.

wireless_script
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel modules: bcma, brcmsmac

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

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
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

########## wireless info END ############

```

cheers,

 - davedub

---

### Post by chili555 on 2014-04-21
Please let us see:```
sudo modprobe wl
sudo dpkg -s bcmwl-kernel-source
iwconfig
```

---

### Post by davedub on 2014-04-21
Sure:

```

   @Ubuntu-E1-203:~$ sudo modprobe wl 
 FATAL: Module wl not found. 
 @Ubuntu-E1-203:~$ sudo dpkg -s bcmwl-kernel-source 
 Package `bcmwl-kernel-source' is not installed and no info is available. 
 Use dpkg --info (= dpkg-deb --info) to examine archive files, 
 and dpkg --contents (= dpkg-deb --contents) to list their contents. 
 @Ubuntu-E1-203:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 

```

---

### Post by Hadaka on 2014-04-21
please redo post #29

---

### Post by davedub on 2014-04-22
Oops, I crashed out...

Post 29 repreated. References to wireless network have returned to the netowrk-manager dropdown, but the SSID is still not listed, and cannot connect via 'connect via hidden network'

wireless_script out:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

eth1      No scan results

##### iwlist channel #####

##### lsmod #####

wl                   2573607  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     1C6A0B8B0000A8D58131D83
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   14.793941] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.797431] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.797440] wl 0000:03:00.0: setting latency timer to 64
[   15.130628] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112

########## wireless info END ############

```

---

### Post by davedub on 2014-04-22
Hi Guys,

Time is really running out for me here - I am leaving the country in a couple of days, and my Dad really, really needs his computer working before I go.

Please, please help!

Kind Regards,

davedub

---

### Post by chili555 on 2014-04-22
Obviously, the 5.100.82.112 version is not working for us. Let's try the very latest version and see if we have better luck. ```
sudo apt-get purge bcmwl-kernel-source
rm bcmwl*.deb
wget http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb
sudo dpkg -i bcmwl*.deb

```If there is an error when installing, note it and post it here.

Detach the ethernet, reboot and cross your fingers!!

---

### Post by davedub on 2014-04-22
Hi Chili,

good to see you. I ran your script:

```
 
   @Ubuntu-E1-203:~$ sudo apt-get purge bcmwl-kernel-source  
 [sudo] password for :  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following package was automatically installed and is no longer required:  
   dkms  
 Use 'apt-get autoremove' to remove them.  
 The following packages will be REMOVED  
   bcmwl-kernel-source*  
 0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.  
 After this operation, 3,609 kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 186185 files and directories currently installed.)  
 Removing bcmwl-kernel-source ...  
 Removing all DKMS Modules  
 Done.  
 update-initramfs: deferring update (trigger activated)  
 Purging configuration files for bcmwl-kernel-source ...  
 update-initramfs: deferring update (trigger activated)  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic  
 @Ubuntu-E1-203:~$

```

the wireless showed up an SSID i've not seen before, but after a reboot all references to wireless were missing from the network-manager icon dropdown. 

I ran:

```


wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script

```

which produced

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel modules: bcma, brcmsmac

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####


##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####


##### interfaces #####

auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        20:89:84:83:59:10

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=20:89:84:83:59:10,

[ifupdown]
managed=false

##### iwlist #####

```

Cheers,

davedub

---

### Post by chili555 on 2014-04-22
You purged the old one but have not yet proceeded with the next three steps. Please do so.

---

### Post by davedub on 2014-04-22
oops - weird. ok - ran from rm bcmwl*.deb:

```

   @Ubuntu-E1-203:~$ rm bcmwl*.deb  

 @Ubuntu-E1-203:~$ wget http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb 
 --2014-04-22 21:51:46--  http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb 
 Resolving mirrors.kernel.org (mirrors.kernel.org)... 149.20.20.135, 149.20.4.71, 2001:4f8:1:10:0:1994:3:14, ...  
 Connecting to mirrors.kernel.org (mirrors.kernel.org)|149.20.20.135|:80... connected.  
 HTTP request sent, awaiting response... 200 OK  
 Length: 1790420 (1.7M) [text/plain]  
 Saving to: `bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb'  
 

 100%[======================================================================================================>] 1,790,420    665K/s   in 2.6s     
 

 2014-04-22 21:51:49 (665 KB/s) - `bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb' saved [1790420/1790420]  
 

 @Ubuntu-E1-203:~$ ^C  
 @Ubuntu-E1-203:~$ sudo dpkg -i bcmwl*.deb  
 Selecting previously unselected package bcmwl-kernel-source.  
 (Reading database ... 186131 files and directories currently installed.)  
 Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb) ...  
 Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu1) ...  
 Loading new bcmwl-6.30.223.141+bdcom DKMS files...  
 First Installation: checking all kernels...  
 Building only for 3.2.0-60-generic  
 Building for architecture x86_64  
 Building initial module for 3.2.0-60-generic  
 Done.  
 

 wl:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/3.2.0-60-generic/updates/dkms/  
 

 depmod.........  
 

 DKMS: install completed.  
 update-initramfs: deferring update (trigger activated)  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic  
 @Ubuntu-E1-203:~$

```


references to wireless reappeared in nm dropdown, but still cannot see any SSIDs

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

eth1      No scan results

##### iwlist channel #####

eth1      26 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### lsmod #####

wl                   4207808  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   14.847829] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.854993] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.855002] wl 0000:03:00.0: setting latency timer to 64
[   14.887912] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   15.146306] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  333.356735] ERROR @wl_dev_intvar_get : error (-1)
[  333.356747] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############

```

cheers!

 - davedub

---

### Post by chili555 on 2014-04-22
Unfortunately, young Dave, you have one of the most difficult, tricky and stubborn wireless devices there is; sort of reminds me of an ex-girlfriend. Sometimes, logic and science doesn't work and we throw the kitchen sink at it!```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-backports-modules-cw-3.10-precise-generic
```Then do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Change the last several lines to:```
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb
#blacklist wl
**#**blacklist bcma
**#**blacklist brcmsmac
```Proofread, save and close gedit.

Reboot. Hope and Pray.

---

### Post by davedub on 2014-04-22
lol - I always get the tricky ones!

ran:

```

   @Ubuntu-E1-203:~$ sudo apt-get purge bcmwl-kernel-source  
 [sudo] password for :  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following package was automatically installed and is no longer required:  
   dkms  
 Use 'apt-get autoremove' to remove them.  
 The following packages will be REMOVED  
   bcmwl-kernel-source*  
 0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.  
 After this operation, 5,798 kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 186195 files and directories currently installed.)  
 Removing bcmwl-kernel-source ...  
 Removing all DKMS Modules  
 Done.  
 update-initramfs: deferring update (trigger activated)  
 Purging configuration files for bcmwl-kernel-source ...  
 update-initramfs: deferring update (trigger activated)  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic  
 @Ubuntu-E1-203:~$ sudo apt-get install linux-backports-modules-cw-3.10-precise-generic  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following package was automatically installed and is no longer required:  
   dkms  
 Use 'apt-get autoremove' to remove them.  
 The following extra packages will be installed:  
   linux-backports-modules-cw-3.10-3.2.0-60-generic  
 The following NEW packages will be installed  
   linux-backports-modules-cw-3.10-3.2.0-60-generic linux-backports-modules-cw-3.10-precise-generic  
 0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.  
 Need to get 2,910 kB of archives.  
 After this operation, 11.0 MB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.10-3.2.0-60-generic amd64 3.2.0-60.50 [2,908 kB]  
 Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.10-precise-generic amd64 3.2.0.60.71 [2,468 B]  
 Fetched 2,910 kB in 3s (837 kB/s)                                          
 Selecting previously unselected package linux-backports-modules-cw-3.10-3.2.0-60-generic.  
 (Reading database ... 186131 files and directories currently installed.)  
 Unpacking linux-backports-modules-cw-3.10-3.2.0-60-generic (from .../linux-backports-modules-cw-3.10-3.2.0-60-generic_3.2.0-60.50_amd64.deb) ...  
 Selecting previously unselected package linux-backports-modules-cw-3.10-precise-generic.  
 Unpacking linux-backports-modules-cw-3.10-precise-generic (from .../linux-backports-modules-cw-3.10-precise-generic_3.2.0.60.71_amd64.deb) ...  
 Setting up linux-backports-modules-cw-3.10-3.2.0-60-generic (3.2.0-60.50) ...  
 update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic  
 Setting up linux-backports-modules-cw-3.10-precise-generic (3.2.0.60.71) ...  
 @Ubuntu-E1-203:~$ gksudo gedit /etc/modprobe.d/blacklist.conf  
 @Ubuntu-E1-203:~$  

```

 wireless references missing from nm icon dropdown, 

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

brcmutil               15618  0 
bcma                   26696  0 

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/cw-3.10/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

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
blacklist b43
blacklist ssb

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   14.865150] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.865164] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   14.865230] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   14.865286] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   14.865351] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   14.898567] bcma: Bus registered
[   15.206126] brcmsmac: Unknown symbol bcma_core_pci_extend_L1timer (err 0)
[   15.206134] brcmsmac: Unknown symbol bcma_chipco_get_alp_clock (err 0)
[   15.206168] brcmsmac: Unknown symbol bcma_chipco_gpio_outen (err 0)
[   15.206204] brcmsmac: Unknown symbol bcma_chipco_gpio_out (err 0)
[   15.206324] brcmsmac: Unknown symbol bcma_pmu_spuravoid_pllupdate (err 0)

########## wireless info END ############

```

hardware fault?


cheers!

davedub

---

### Post by chili555 on 2014-04-22
Before I give up Linux and take up something a whole lot easier like inventing time travel so I can buy GOOG at 80, just confirm that you have the firmware:```
ls /lib/firmware/brcm
```If you have bcm43xx_hdr-0.fw and bcm43xx-0.fw, then I concede that it's either a hardware fault or that there is no known way to get it working. 

Before you give up, I'd try the live DVD or USB for Ubuntu 14.04. If it works, install.

---

### Post by davedub on 2014-04-22
I do seem to have the right firmware:

```

bcm4329-fullmac-4.bin  bcm43xx_hdr-0.fw    brcmfmac4329.bin
bcm43xx-0.fw           brcmfmac43236b.bin  brcmfmac4330.bin

```

It looks like my quickest option is a USB wireless dongle for now - have we left the config in a state whereby it will accept a standard usb dongle?

Thank you so much for your help, I really appreciate your putting in the time and I've learnt quite a bit on the way :-)

Cheers!

 - davedub

---

### Post by chili555 on 2014-04-22
Before you install the USB, adjust the blacklist file to blacklist them all; something like:```
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb
blacklist wl
blacklist bcma
blacklist brcmsmac
```Be sure to research the USB carefully before you buy. There are several treads here about working out of the box USB wireless devices.

---

### Post by davedub on 2014-04-22
Cool, thanks for that, will do.

Thanks to everyone.

 - davedub

---

### Post by davedub on 2014-04-24
Well what do you know - I have a lot of progress to report, and one remaining question:

I ordered a USB wifi dongle. This initially didn't work. I then noticed the WiFi on a totally serparate printer was also failing to see the SSID. So my attention turned to the BT HomeHub 4, which it turns out had recently done some sort of merging of it's 2.4GHz and 5GHz network SSIDs, and was only actually offering a 5GHz network - which the printer and the USB WiFi dongle couldn't see. So I reconfigured the homehub 4 to use separate SSIDs for the 2.4GHz network and the 5GHz networks and changed the channel for the 2.4GHz network. Hey presto!

 ~ the printer connected to the wireless network
 ~ the Acer (with it's USB WiFi dongle) connected to the wireless network

:-D happy days!

BUT, the built in WiFi card on the Acer is still not working.

So, I booted up from both the 12.04 and 14.04 disks and what do you know - BOTH wireless cards show up and can connect on BOTH installations - so there's no problem with the built in wireless card. 

/progress

So, one last remaining issue - when I boot into the installed version of Ubuntu, only the USB WiFi dongle is shown in the network-manager icon dropdown. Having seen the built in wiress card AND the USB dongle both listed when booting from the CDs, I can only conclude that I need to put my built in wireless card settings and config back to how it was before the BT homehub 4 decided to do that weird channel merging thing.

Please could someone guide me through doings, so, I've had a go but am still too much of an Ubuntu noob!

I have run this:

```


 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script

```

Which produced the output below. It looks to me like I'm running the wl and bcma, but I don't know if they are the correct drivers, 
and I'm very unsure as how to remove all others.

```

########## wireless info START ##########
##### release #####
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
##### kernel #####
Linux Ubuntu-E1-203 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
##### lspci #####
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel modules: wl, bcma
##### lsusb #####
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b337 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
##### PCMCIA Card Info #####
##### rfkill #####
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
##### iw reg get #####
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
##### interfaces #####
auto lo
iface lo inet loopback
##### iwconfig #####
wlan0     IEEE 802.11bgn  ESSID:"Tile Cottage WiFi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:35   Missed beacon:0
##### route #####
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
##### resolv.conf #####
nameserver 127.0.0.1
search home
##### nm-tool #####
NetworkManager Tool
State: connected (global)
- Device: wlan0  [Tile Cottage WiFi] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>
  Capabilities:
    Speed:           65 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = current AP)
    *Tile Cottage WiFi: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
  IPv4 Settings:
    Address:         192.168.1.78
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
##### NetworkManager.state #####
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
##### NetworkManager.conf #####
[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=<MAC address removed>,
[ifupdown]
managed=false
##### iwlist #####
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Tile Cottage WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000010d96d9d2
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 001154696C6520436F74746167652057694669
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B000103104700103FB86AF4DACE50ACAFDF651D3A47E3F810210002425410230005487562203410240009425420487562203441104200122B3036383334302B4E5133333430373437361054000800060050F204000110110010425420486F6D652048756220342E3041100800020084103C000101
##### iwlist channel #####
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
          Current Frequency:2.462 GHz (Channel 11)
##### lsmod #####
rt2800usb              23087  0 
rt2800lib              79613  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20742  1 rt2800usb
rt2x00lib              55080  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              561944  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              558268  2 rt2x00lib,mac80211
compat                 38485  4 rt2800usb,mac80211,cfg80211,lib80211
##### modinfo #####
filename:       /lib/modules/3.2.0-60-generic/updates/cw-3.10/rt2800usb.ko
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1F0D585085E17031A775C92
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb,compat
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
filename:       /lib/modules/3.2.0-60-generic/updates/cw-3.10/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     D3AC2AC24AED805407CDAF3
depends:        rt2x00lib,mac80211,crc-ccitt
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-60-generic/updates/cw-3.10/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     6282C58E149271F6F00B763
depends:        rt2x00lib,mac80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-60-generic/updates/cw-3.10/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7B82423F0480988F128BBA8
depends:        mac80211,cfg80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
##### modules #####
lp
rtc
##### blacklist #####
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
blacklist b43
blacklist ssb
blacklist bcma
blacklist brcmsmac
##### udev rules #####
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x148f:0x3070 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
##### dmesg #####
[   15.017204] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.018259] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.018263] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[   39.035479] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   39.051266] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   39.054283] Registered led device: rt2800usb-phy0::radio
[   39.054306] Registered led device: rt2800usb-phy0::assoc
[   39.054327] Registered led device: rt2800usb-phy0::quality
[   39.159601] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   39.195060] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   39.528160] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.528653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.994561] wlan0: authenticate with <MAC address removed>
[   43.069816] wlan0: send auth to <MAC address removed> (try 1/3)
[   43.071320] wlan0: authenticated
[   43.074025] wlan0: associate with <MAC address removed> (try 1/3)
[   43.077171] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[   43.083931] wlan0: associated
[   43.084301] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.224806] wlan0: no IPv6 routers present
########## wireless info END ############

```

Please help me fix this!

Kind Regards,

davedub

---

### Post by chili555 on 2014-04-24
By the time the system is booted up, you aren't running any of the Broadcom drivers because the drivers conflict with the Realtek and bail out:> [   15.018259] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.018263] wl: Unknown symbol lib80211_get_crypto_ops (err -22)> BOTH wireless cards show up and can connect on BOTH installations How do you know which one connects? When you run:```
ifconfig
```...do both have separate IP addresses??? I'm not saying it doesn't happen; I'm saying please help me understand *HOW* it happens.

When you run the live DVD or USB, which driver is in place for the internal, brcmsmac or wl?```
lsmod
```

---

### Post by davedub on 2014-04-24
Hey Chili,

Apologies, I wasn't clear - I should have said _either_ card can connect, not _both_ - wasn't too clear...

here's ifconfig whilst connected using the internal card on 14.04 running off CD:

```

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:89:84:83:59:10  
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
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8353 (8.3 KB)  TX bytes:8353 (8.3 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c8:fa:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr b8:76:3f:83:c4:24  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba76:3fff:fe83:c424/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:1 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16824 (16.8 KB)  TX bytes:10876 (10.8 KB)


```

Here's the same thing when connecting using the USB wifi dongle:

```

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:89:84:83:59:10  
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
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47124 (47.1 KB)  TX bytes:47124 (47.1 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c8:fa:03  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec8:fa03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6646 (6.6 KB)  TX bytes:18460 (18.4 KB)

wlan1     Link encap:Ethernet  HWaddr b8:76:3f:83:c4:24  
          inet6 addr: fe80::ba76:3fff:fe83:c424/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5035 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5871282 (5.8 MB)  TX bytes:542053 (542.0 KB)



```

Here's the lsmod output:

```

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
arc4                   12608  4 
b43                   387371  0 
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
snd_hda_codec_hdmi     46207  1 
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
snd_hda_codec_realtek    61438  1 
mac80211              626489  5 b43,brcmsmac,rt2x00lib,rt2x00usb,rt2800lib
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo               80885  0 
intel_rapl             18773  0 
snd_hwdep              13602  1 snd_hda_codec
x86_pkg_temp_thermal    14205  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_vmalloc      13216  1 uvcvideo
dm_crypt               23177  0 
intel_powerclamp       14705  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
cfg80211              484040  4 b43,brcmsmac,mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
videodev              134688  2 uvcvideo,videobuf2_core
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
kvm_intel             143060  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   451511  1 kvm_intel
ssb                    62379  1 b43
joydev                 17381  0 
acer_wmi               32522  0 
snd_timer              29482  2 snd_pcm,snd_seq
sparse_keymap          13948  1 acer_wmi
dm_multipath           22873  0 
mei_me                 18627  0 
scsi_dh                14882  1 dm_multipath
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
lpc_ich                21080  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82274  1 mei_me
bcma                   52096  3 b43,brcmsmac
ghash_clmulni_intel    13259  0 
psmouse               102222  0 
soundcore              12680  1 snd
bnep                   19624  2 
serio_raw              13462  0 
cryptd                 20359  1 ghash_clmulni_intel
parport_pc             32701  0 
rfcomm                 69160  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
bluetooth             395423  10 bnep,rfcomm
parport                42348  3 lp,ppdev,parport_pc
squashfs               48362  1 
overlayfs              27916  1 
nls_utf8               12557  1 
isofs                  39835  1 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
i915                  783485  3 
ahci                   25819  2 
sdhci_pci              23172  0 
libahci                32168  1 ahci
i2c_algo_bit           13413  1 i915
sdhci                  43015  1 sdhci_pci
drm_kms_helper         52758  1 i915
tg3                   166442  0 
drm                   302817  4 i915,drm_kms_helper
ptp                    18933  1 tg3
pps_core               19382  1 ptp
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi

```

Cheers!

davedub

---

### Post by chili555 on 2014-04-24
Isn't your course of action clear? Install 14.04 LTS, _decline_ the invitation to install Additional Drivers (read: bcmwl-kernel-source which doesn't drive your Broadcom correctly) and enjoy. Yes??

Take the USB back to the store and use the refund to by a celebratory beverage or three!

---

### Post by davedub on 2014-04-25
Hi Chili,

Yep, that worked, 14.04 LTS sucessfully installed - there was a bit of fiddling about to get the printer up and running again, but managed to install the drivers from the command line myself :-)

All done, thank you very much!

 ~ davedub

---

### Post by chili555 on 2014-04-25
Awesome! I'm very glad it's working. Sometimes, newer is indeed better.

---

