---
title: "BCM4311 No Wifi 14.04.3"
date: 2016-03-04
forum: Networking &amp; Wireless
---

### Post by Luke_Johnson on 2016-03-04
Hi Everyone, 

I have been trying to get my card working for the past two days, I have tried just about everything I could find on the internet and these forums to resolve my wifi issues. Ive read the guides which normally work but for some reason this time nothing can get it working.

The card is there but I cant get it to work at all. 

Im new to ubuntu and id appreciate any help you may be able to provide. 

Kind regards, 
Luke Johnson

```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.77 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
```

---

### Post by chili555 on 2016-03-04
Did you read this?  [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Luke_Johnson on 2016-03-04
Hi Chili, 

I have tried that one, it got my ethernet working when I did the purge section but then installing the b43 firmware didnt help get the wifi card up and running. I have tried purging and then reinstalling them too.

---

### Post by coldraven on 2016-03-04
It's working for me, I just enabled it in "Additional Drivers".

---

### Post by chili555 on 2016-03-04
> **coldraven said:**
> It's working for me, I just enabled it in "Additional Drivers".Additional Drivers installs the _wrong_ driver for his 4311. Please do not try this, Luke.

---

### Post by chili555 on 2016-03-04
> **Luke_Johnson said:**
> Hi Chili, 

I have tried that one, it got my ethernet working when I did the purge section but then installing the b43 firmware didnt help get the wifi card up and running. I have tried purging and then reinstalling them too.Let's see what's going on under the hood. Please run and post:```
rfkill list all
lsmod | grep -e wl -e b43
dmesg | grep b43
```

---

### Post by Luke_Johnson on 2016-03-04
Too late I tried the other suggestion do I now need to do some purging again?

When I run your commands nothing appears. Am I doing something wrong?

---

### Post by chili555 on 2016-03-04
> Too late I tried the other suggestion do I now need to do some purging again?Yes, please. Then reboot and try my diagnostics again.

---

### Post by Luke_Johnson on 2016-03-07
Hi Chili, 

For each of those commands nothing is displayed.

Hi Chili, 

I did the sudo apt-get purge bcmwl-kernel-source

and then tried to run your commands again but nothing appeared after each one.

---

### Post by chili555 on 2016-03-07
Please try:```
sudo modprobe b43
dmesg | grep b43
```Something is still very wrong and we'll need to fix it.

As was said in another thread:> I won't bore you with the multitude of things that I did (following all sorts of [SOLVED] forum thread guides) because none of them worked, almost certainly because when you try too many things you completely c*ck up your configuration with too many "tips and tricks" fighting for supremacy. As has been published many times over, the correct driver for your 14e4:4311 device is *NOT* bcmwl-kernel-source, also known as Additional Drivers. It is b43 and firmware. Please do not try anything else as we will have to undo it before we can get your device working properly.

---

### Post by Luke_Johnson on 2016-03-07
sudo modprobe b43:

libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 1: ignoring bad line starting with 'sudo'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 2: ignoring bad line starting with 'apt-get'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 3: ignoring bad line starting with 'apt-get'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 4: ignoring bad line starting with 'svn'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 5: ignoring bad line starting with 'cat'
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.2.0-16-generic/modules.dep.bin'

dmesg | grep b43 resulted in nothing.

---

### Post by chili555 on 2016-03-07
Wow. Just wow.

Please show me:```
cat /etc/modprobe.d/blacklist.conf
```I am quite sure it is damaged. We will probably need to rebuild it.

---

### Post by Luke_Johnson on 2016-03-07
sudo -i
apt-get update && apt-get upgrade
apt-get install build-essential libssl-dev linux-headers-4.2.0-16-generic subve$
svn checkout [http://svn.madwifi-project.org/madwifi/trunk/](http://svn.madwifi-project.org/madwifi/trunk/) madwifi-ng
cat >> /etc/modprobe.d/blacklist.conf << END

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k
blacklist b43
blacklist ssb

---

### Post by chili555 on 2016-03-07
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

Remove *everything* that is in there now; replace it with the default file:```
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

```Proofread carefully, save and close the text editor.

Reboot and let me see:```
lsmod | grep b43
iwconfig
dmesg | grep b43
```

---

### Post by Luke_Johnson on 2016-03-07
lsmod | grep b43 returns nothing.

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

dmesg | grep b43 also returns nothing.

---

### Post by chili555 on 2016-03-07
> **Luke_Johnson said:**
> lsmod | grep b43 returns nothing.

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

dmesg | grep b43 also returns nothing.I suspect a few *more *things are broken here. Please provide the wireless script from here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Luke_Johnson on 2016-03-07
```
########## wireless info START ##########

Report from: 07 Mar 2016 16:15 GMT +0000

Booted last: 07 Mar 2016 16:08 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 14:46:51 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

ssb                    57344  1 b44
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.77  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1005318 (1.0 MB)  TX bytes:250857 (250.8 KB)
          Interrupt:17 

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
search dscallards.local

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       925     1  0 16:08 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.17

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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=test
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

libkmod: ERROR ../libkmod/libkmod.c:556 kmod_search_moddep: could not open moddep file '/lib/modules/4.2.0-16-generic/modules.dep.bin'
modinfo: ERROR: Module alias ssb not found.
[ssb]

##### module parameters #################

##### /etc/modules ######################

lp
ath_hal
ath_pci
ath_hal
ath_pci

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
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
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    3.481414] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC 'eth0' [IF]>
[   27.618524] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.816243] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   30.816256] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[   30.816377] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2016-03-07
> ##### network managers ##################

Installed:

NetworkManager
Wicd
You needn't have both. Please do:```
sudo apt-get purge wicd
```You haven't an Atheros card, so please do:```
sudo rm /etc/modprobe.d/ath9k.conf
sudo gedit /etc/modules
```Remove the lines I've highlighted:```
lp
[COLOR="#FF0000"]ath_hal
ath_pci
ath_hal
ath_pci[/COLOR]
```Proofread carefully, save and close the text editor. Reboot and run:```
sudo apt-get update
sudo apt-get upgrade
```Any errors? Problems? If not, next run:```
sudo modprobe b43 && dmesg | grep -e ssb -e b43
```

---

### Post by Luke_Johnson on 2016-03-07
sudo apt-get update:
W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

sudo apt-get upgrade:

The following packages were automatically installed and are no longer required:
  dkms gksu libgksu2-0 libmbim-glib0 libqmi-glib0 python-wicd usb-modeswitch
  usb-modeswitch-data wicd-daemon wicd-gtk
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Not sure if any of these are related.

Should I continue with the: 
sudo modprobe b43 && dmesg | grep -e ssb -e b43


I must apologise im not sure how to put the code bits into one of those boxes.

---

### Post by chili555 on 2016-03-07
> W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 It is trying to update from the CD. Please open Software and Updates and delete the CD (DVD, actually) as a source and be sure that main, universe, restricted and multiverse are selected and try again:```
sudo apt-get update
sudo apt-get upgrade
sudo modprobe b43 && dmesg | grep -e ssb -e b43


```

---

### Post by Luke_Johnson on 2016-03-07
$ sudo modprobe b43 && dmesg | grep -e ssb -e b43
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.2.0-16-generic/modules.dep.bin'

---

### Post by chili555 on 2016-03-07
Let's try one more thing:```
sudo apt-get install linux-generic
```Reboot and show us:```
uname -r
sudo modprobe b43
```If this can't fix it, then I suggest a reinstall from scratch.

---

### Post by Luke_Johnson on 2016-03-08
```
luke@luke-MM7:~$ uname -r
4.2.0-16-generic
luke@luke-MM7:~$ sudo modprobe b43
[sudo] password for luke: 
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.2.0-16-generic/modules.dep.bin'
```

---

### Post by Luke_Johnson on 2016-03-08
This is the third time I have reinstalled the OS and each time wifi and internet work during the install but not afterwards.

---

### Post by Luke_Johnson on 2016-03-08
Is there anything else I can try to fix it?

---

### Post by chili555 on 2016-03-08
Is this a message from a fresh, new install where nothing, *nothing* has been done about the wireless?> luke@luke-MM7:~$ uname -r
4.2.0-16-generic
luke@luke-MM7:~$ sudo modprobe b43
[sudo] password for luke: 
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.2.0-16-generic/modules.dep.bin'If not, then I suggest you reinstall again. Do NOT activate Additional Drivers, do NOT connect to the internet and do NOT download updates as you go.

After you boot into the fresh install, hook up the ethernet and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Reboot.

---

### Post by Luke_Johnson on 2016-03-08
Ill give that a go. Thanks for your help, I will report back soon :)

---

### Post by Luke_Johnson on 2016-03-08
AMAZING!! Thankyou so much for your time. I really appreciate it. After reinstall, purged existing drivers, restarted, plugged network cable in, updated, then installed [COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer and another reboot. Fixed!!![/FONT][/COLOR]

---

