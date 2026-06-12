---
title: "How do you use WPA with laptop broadcom 4306?"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by iceman0304 on 2008-01-16
Using Gutsy 7.10 Ubuntu 32bit the wireless was working, but doesn't with the WPA or WPA2 security

> **stchman said:**
> What I believe you are referring to is the installation of Network Manager.  NM is installed by default on Feisty and later.  What Ubuntu are you running.

Whatever version of Ubuntu you are running then follow the instructions.

For Feisty follow the instructions I have on my page for getting the ndiswrapper up and running.  For Gutsy follow these instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

I wish that Broadcom would make Linux drivers for their cards.

Remember, Network Manager is installed by default on Feisty and later and NM is capable of connecting to WEP/WPA/WPA2 points.



here is what I got with this when I tried it, any suggestions?



matt@matt-laptop:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
matt@matt-laptop:~$ gksu gedit /etc/apt/sources.list


This is what opens: gedit

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


matt@matt-laptop:~$ deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) gutsy-cafuego bcm43xx
bash: deb: command not found
matt@matt-laptop:~$

---

### Post by csat on 2008-01-17
My notebook Dell 131-L, running Broadcom 43xx, works fine under WPA-TKIP-PSK.  All my configuration was based on [=>this<=](http://ubuntuforums.org/showthread.php?t=297092) link, nothing more.  After having my wireless card up and running just went to network setup and clicked on my wireless identification.  Then it opens up a window in order to place there my WPA key.  That's all.

---

### Post by iceman0304 on 2008-01-17
using a compaq, laptop

just need to know how to get connected, can I do this thru the menus or do I have to do it thru terminal? How? 

I know I see the router--

matt@matt-laptop:~$ sudo iwlist scanning
[sudo] password for matt:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:49:EE:97
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

matt@matt-laptop:~$

Can anyone confirm "CSAT" link with a Compaq laptop  Broadcom 4306

Thanks

---

### Post by csat on 2008-01-17
Well, whenever wireless board can identify router and another signal from the neighborhood indicates that you only need to configure network.

For instance if you type sudo iwlist eth1 scan <enter> and your router/AP is shown to your screen seems it is almost done and there is no need to go to my suggested link.

---

### Post by iceman0304 on 2008-01-18
Here is the output:

matt@matt-laptop:~$ sudo iwlist eth1 scan
[sudo] password for matt:
eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:49:EE:97
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

matt@matt-laptop:~$ 

I just have no luck getting it connected from here........

:confused:

---

### Post by csat on 2008-01-18
Which wireless driver are you using?

How did you loaded it?  Are you using ndiswrapper?

What do you have at the end of the file /etc/modprobe.d/blacklist  ??  The tutorial gives direction to blacklist bcm43xx because original XP driver has a conflict with restricted driver that comes along Ubuntu distribution.

The previous assigned tutorial made a clean statement about a possible "chaos" that a computer could be when trying to make wireless to work but have no success.  See step 1 of the tutorial.

---

### Post by iceman0304 on 2008-01-18
Here is a link to the commands that I followed:

[http://ubuntuforums.org/showpost.php...7&postcount=46](http://ubuntuforums.org/showpost.php...7&postcount=46)

/etc/modprobe.d/blacklist:

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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
blacklist bcm43xx1[QUOTE]

# drivers wireless ACX
blacklist acx

:confused:

---

### Post by iceman0304 on 2008-01-18
:confused:

---

### Post by kevdog on 2008-01-18
Can you summarize your problem briefly and give any relevant terminal output that shows the problem (if you can?)

---

### Post by iceman0304 on 2008-01-18
Do I need wpa supplicant, do I even have it, how would I know and where would I look? I don't think its setup if I even have it.  I did a search for the config file and came up with nothin.. 

Here is what I did so far, it atleast got me running without security WPA or WPA2:

> **Digger78 said:**
> ```
sudo rmmod ndiswrapper
```
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
```
```
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
```
```
sudo ndiswrapper -m
```
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Now, REBOOT.

**I would recommend disabling security temporarily on your router it will make it easier to verify that you can connect to the router**

After rebooting, you should be able to click the network manager icon. (In Gnome, it looks like two black monitors overlapping each other on the top panel.) Hopefully, you'll see the available wireless access points under "Wireless Networks" and your machine ought to try to connect to one of them if you remove your network cable (or if you select one of them with a mouse click).

What else do you need to to show you to give you an idea where I'm at?  Sorry I was using XP when I wrote this post.

---

### Post by kevdog on 2008-01-19
You definitely need the wpasupplicant package.  You should install this either with apt/aptitude or using synaptic.  You need this package if you want to use wpa.

---

### Post by iceman0304 on 2008-01-19
I'd be using synaptic. Is the WPA Supplicant already on the computer, I've only open the synaptic once.  So I'm not real familiar with it.

---

### Post by kevdog on 2008-01-19
To my knowledge wpasupplicant is not installed by default.  To verify you can do the following:

sudo updatedb

(Wait for a few minutes for the command to complete)

locate wpa

See if the results show any file by the name of wpasupplicant or wpa_supplicant.

I would get very familiar with either synaptic or aptitude (apt-get), since you are going to be using this utility millions of times to update your packages and install new software. :)

---

### Post by iceman0304 on 2008-01-19
Ok I reinstalled WPA supplicant, with the synaptic. I think? unless it was already there.  I also did the sudo updatedb  nothing happened if it was supposed to you'll see here and only took maybe 2 sec's to the normal prompt..

matt@matt-laptop:~$ sudo updatedb
[sudo] password for matt:
matt@matt-laptop:~$ locate wpa
/usr/bin/wpa_passphrase
/usr/share/doc/wpasupplicant
/usr/share/doc/wpasupplicant/README.Debian
/usr/share/doc/wpasupplicant/copyright
/usr/share/doc/wpasupplicant/NEWS.Debian.gz
/usr/share/doc/wpasupplicant/README.modes.gz
/usr/share/doc/wpasupplicant/eap_testing.txt.gz
/usr/share/doc/wpasupplicant/README.gz
/usr/share/doc/wpasupplicant/changelog.Debian.gz
/usr/share/doc/wpasupplicant/examples
/usr/share/doc/wpasupplicant/examples/wpa_supplicant.init-daemon
/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.template
/usr/share/doc/wpasupplicant/examples/wpa2-eap-ccmp.conf
/usr/share/doc/wpasupplicant/examples/ieee8021x.conf
/usr/share/doc/wpasupplicant/examples/wpa-psk-tkip.conf
/usr/share/doc/wpasupplicant/examples/README.wpa_supplicant.conf.gz
/usr/share/doc/wpasupplicant/examples/wep.conf
/usr/share/doc/wpasupplicant/examples/plaintext.conf
/usr/share/doc/wpasupplicant/changelog.gz
/usr/share/man/man5/wpa_supplicant.conf.5.gz
/usr/share/man/man8/wpa_cli.8.gz
/usr/share/man/man8/wpa_background.8.gz
/usr/share/man/man8/wpa_action.8.gz
/usr/share/man/man8/wpa_passphrase.8.gz
/usr/share/man/man8/wpa_supplicant.8.gz
/usr/share/ghostscript/8.61/lib/showpage.ps
/lib/firmware/2.6.22-14-generic/atmel_at76c506-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c502-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c504a_2958-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c502d-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c504c-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c502_3com-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c504_2958-wpa.bin
/lib/firmware/2.6.22-14-generic/atmel_at76c502e-wpa.bin
/etc/logrotate.d/wpa_action
/etc/default/wpasupplicant
/etc/init.d/wpa-ifupdown
/etc/rc6.d/S15wpa-ifupdown
/etc/wpa_supplicant
/etc/wpa_supplicant/functions.sh
/etc/wpa_supplicant/ifupdown.sh
/etc/network/if-pre-up.d/wpasupplicant
/etc/network/if-post-down.d/wpasupplicant
/etc/network/if-down.d/wpasupplicant
/etc/network/if-up.d/wpasupplicant
/etc/rc0.d/S15wpa-ifupdown
/sbin/wpa_action
/sbin/wpa_cli
/sbin/wpa_supplicant
/var/lib/dpkg/info/wpasupplicant.postrm
/var/lib/dpkg/info/wpasupplicant.postinst
/var/lib/dpkg/info/wpasupplicant.preinst
/var/lib/dpkg/info/wpasupplicant.md5sums
/var/lib/dpkg/info/wpasupplicant.list
/var/lib/dpkg/info/wpasupplicant.conffiles
/var/cache/apt/archives/wpasupplicant_0.6.0+0.5.8-0ubuntu1_i386.deb
matt@matt-laptop:~$ 

I'll try to some different things, I'm just hoping I don't mess anything up.  

:confused:

---

### Post by kevdog on 2008-01-19
Ok you got the package installed.  If you want to know how to manually configure for wpa try my tutorial in my signature about connecting from the command line.

---

### Post by iceman0304 on 2008-01-19
have a look at Dark Noobs thread
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

and Weiman01's tutorial

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

they might help



I did both of the sites and haven't had any luck

matt@matt-laptop:~$ sudo gedit /etc/network/interfaces
[sudo] password for matt:


auto lo
iface lo inet loopback

auto eth1 _<--------- I lost my wired lan with this in had to remove_
iface eth1 inet dhcp _it to get connected via wired lan._
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid linksys

auto eth1


matt@matt-laptop:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:1C:10:49:EE:97
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managedmatt@matt-laptop:~$ sudo gedit /etc/network/interfaces
[sudo] password for matt:

Frequency:2.437 GHz (Channel 6)
Quality:78/100 Signal level:-46 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK


iface eth0 inet dhcp _<--------is this OK_

auto eth0 [U]<-------is this OK
[/U]


matt@matt-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:32 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

:confused:

---

### Post by iceman0304 on 2008-01-20
Trying the troubleshooting not sure which driver I am supposed to use.  I'll mark my questions with :KS  ...  

Another question I use a spaces in my passphrase do I use " _ " in it's place or does that pose a problem? 


matt@matt-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:47:14:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 :KS   driverversion=1.45+Broadcom,03/23/2006, 4.40.1 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:81:0e:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.100 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

matt@matt-laptop:~$ sudo aptitude install wpasupplicant
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
matt@matt-laptop:~$ gksu gedit /etc/wpa_supplicant.conf
matt@matt-laptop:~$ sudo ifconfig eth1 down
matt@matt-laptop:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:47:14:25
Sending on   LPF/eth1/00:90:4b:47:14:25
Sending on   Socket/fallback
matt@matt-laptop:~$ sudo wpa_supplicant -w -Dndiswrapper+bcmwl5 -ieth1 -c/etc/wpa_supplicant.conf    :KS
Unsupported driver 'ndiswrapper+bcmwl5'.

matt@matt-laptop:~$ sudo wpa_supplicant -w -Dndiswrapper=wext -ieth1 -c/etc/wpa_supplicant.conf   :KS
Unsupported driver 'ndiswrapper=wext'.

---

### Post by kevdog on 2008-01-20
```
sudo wpa_supplicant -w -Dndiswrapper=wext -ieth1 -c/etc/wpa_supplicant.conf 
```

That statement is wrong. It should be:
```
sudo wpa_supplicant -w -D wext -ieth1 -c/etc/wpa_supplicant.conf 
```

Dont use any spaces in your passphrase -- thats a definite no-no

---

### Post by iceman0304 on 2008-01-20
no no for what reason?, security lowered?...  I'm using it with XP's currently.  but I can go and fix that.

---

### Post by iceman0304 on 2008-01-20
Does the security need to be set to "TKIP"   currently it is "AES"

matt@matt-laptop:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf
Line 5: failed to parse ssid 'linksys'.
Line 5: failed to parse ssid 'linksys'.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
matt@matt-laptop:~$

---

### Post by kevdog on 2008-01-20
You either use TKIP or AES depending on the settings in your router -- you just want to match the router settings.  Usually (rule of thumb) WPA is TKIP and WPA2 is AES -- however sometimes this rule of thumb is incorrect.

Can you post your wpa_supplicant.conf file?  Seems like something is choking on the essid statement!

Also can you repost iwlist scan?

---

### Post by iceman0304 on 2008-01-20
When I started your troubleshooting and opened this file for the first time it was empty.

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid=linksys
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk=i erased this
        pairwise=TKIP
        group=TKIP
}


matt@matt-laptop:~$ iwlist scanlo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:49:EE:97
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by kevdog on 2008-01-20
Are you putting your password in quotes?  Also put the ssid in quotes.

What output are you getting??

---

### Post by iceman0304 on 2008-01-20
Line 9: Invalid passphrase length 64 (expected: 8..63) 'this has been erased"'.
Line 9: failed to parse psk '"this has been erased"'.
Line 12: WPA-PSK accepted for key management, but no PSK configured.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
matt@matt-laptop:~$

---

### Post by kevdog on 2008-01-20
So there is a problem with your password it looks like.

Ok for right now you want your ascii password.  Make sure it has no spaces in the password, or weird symbols.  Just make it numbers and letters.

you want your password line to be like the following:
psk="password123"

Again try to work through it, and if in a jam, just post your password here.  You can always change it later if you want.

---

### Post by iceman0304 on 2008-01-20
matt@matt-laptop:~$ wpa_passphrase linksys password123
network={
        ssid="linksys"
        #psk="password123"
        psk=c99b32de2a76787758e3162826699365b105810d1b8a835c00445e04399fd27b
}
matt@matt-laptop:~$ 


ok which one would I use the :"c99b32de2a76787758e3162826699365b105810d1b8a835c00445e04399fd27b"

or "password123"

---

### Post by kevdog on 2008-01-20
If you want to use the ascii form, you put it in quotes.  If you want to use the hex equivalent (as instructed here, dont put the resultant hex in quotes.  Again it doesnt matter:

Courtesy of Wieman01

VERY IMPORTANT:
Now convert your WPA ASCII password using the following command:
```
wpa_passphrase <your_essid> <your_ascii_key>
```
Resulting in an output like...

```
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
```

---

### Post by iceman0304 on 2008-01-20
matt@matt-laptop:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.


this is what I have now


ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="linksys"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="password123"
pairwise=TKIP
group=TKIP
}

---

### Post by kevdog on 2008-01-20
Either reboot

or

sudo ps -ef | grep wpa

Find the process number associated with the wpasupplicant

sudo kill <process_number>

If any problems, just reboot.

---

### Post by iceman0304 on 2008-01-20
ok I'm done rebooting

---

### Post by kevdog on 2008-01-20
Ok great, what happens when you type:

sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

---

### Post by iceman0304 on 2008-01-20
matt@matt-laptop:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     6c 69 6e 6b 73 79 73                              linksys         
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='linksys'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:90:4b:47:14:25
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
matt@matt-laptop:~$ 





matt@matt-laptop:~$ sudo dhclient eth1
[sudo] password for matt:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:47:14:25
Sending on   LPF/eth1/00:90:4b:47:14:25
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
matt@matt-laptop:~$

---

### Post by kevdog on 2008-01-20
You are certain eth1 is the interface?

Also try

sudo rm /var/run/wpa_supplicant'

---

### Post by iceman0304 on 2008-01-20
matt@matt-laptop:~$ sudo rm /var/run/wpa_supplicant'
> 




matt@matt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:49:EE:97
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

---

### Post by kevdog on 2008-01-20
Im not sure what this means:

Group Cipher : WEP-40
Pairwise Ciphers (1) : WEP-40

It should be TKIP here!

---

### Post by iceman0304 on 2008-01-20
I opened the WPA supplicant and it had TKIP in both places

---

### Post by kevdog on 2008-01-20
You're making no sense:  Look at your output:

```
eth1 Scan completed :
Cell 01 - Address: 00:1C:10:49:EE:97
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:78/100 Signal level:-46 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
[COLOR="Red"][B]Group Cipher : WEP-40
Pairwise Ciphers (1) : WEP-40[/B][/COLOR]
Authentication Suites (1) : PSK
```

---

### Post by iceman0304 on 2008-01-20
matt@matt-laptop:~$ gksu gedit /etc/wpa_supplicant.conf



ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="linksys"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="password123"
        pairwise=TKIP
        group=TKIP
}

---

### Post by kevdog on 2008-01-20
My recommendations is instead of reposting things, take a look and reread this thread.  I cant help you since you are not answering my questions or providing any explanation.  Im not sitting in front of your computer.  Im trusting the output you provide me.  Your provided output is conflicting.  It doesnt make a lot of sense.  Also review the settings on your router.

---

### Post by iceman0304 on 2008-01-20
sorry, I'm trying to answer the best I can, I've been copying and pasting all my outputs.

Is there another version of Ubuntu, or other linux distros that might setup easier than Gutsy 7.10

What about laptops themselves any preferred brands or preferred wireless chipsets

---

### Post by bascherz on 2008-01-24
Hello fellow Ubuntans...

I am a relative noob with Ubuntu... been using it about 5 months now on various different computers in as many different configurations, including with VMware. I have gotten comfortable enough with it to finally do the following.
 
I just replaced my HP ze4400 laptop with a new dv6000 and the old one is getting a divorce from XP and remarried to Ubuntu Gutsy. I had a few issues with the installation of Ubuntu on this computer, but the one that is on-topic here is getting the Broadcom driver to work. 

Starting with the included 43xx firmware and driver, I was able to see both of my WAPs but could not connect to them. It seems the  WEP passphrase key negotiation just wasn't working. After trying many, many different combinations, I decided using ndiswrapper with the Windows driver that came with the machine was probably the best route. All the different configurations I tried resulted in the same outcome, but this one is the easiest to setup and control because using it requires no command line stuff.

So today brought the machine to work where we have open WiFi access in certain buildings primarily so our customers can use the Internet here during meetings. I am able to connect just fine without having to authenticate, so the driver is working properly in this configuration. I am using the machine right now at work.

So my question is, has anyone else experienced this problem? Could it be a problem only with WEP encryption? Has anyone gotten WAP to work? I can (and probably should) change my home network over to WPA, especially if it works around this problem.

Thanks to everyone who has already contributed to these threads discussing this series of devices. It has been very educational.

Cheers,
Bruce

---

### Post by iceman0304 on 2008-01-24
I finally got my internet to work with the wireless broadcom 4306 without any additional drivers needed...

I switched over to using PCLinux  Gnome lastest version from there website,it took awhile to figure out but actually it was really simple, no command line needed.

1) I'm able to connect with no security

2) turned on mac filter (Router) lost connection. If I would've rebooted it probably would've worked.

3) Turned on WPA TKIP Security (Router) lost connection.  don't recall if I rebooted to check or not.

4) Turned on WPA AES Security (Router) lost connection.  Huh BUT I rebooted this time and  Grin I'M CONNECTED!!!!!

5) turned on mac filter (Router) lost connection.   BUT I rebooted and  I'M CONNECTED!!!!!

---

