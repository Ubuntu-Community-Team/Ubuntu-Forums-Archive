---
title: "And yet, another Ubuntu noob trying to get his Atheros AR242x 802.11 card to work"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by qjmoss on 2008-10-06
I have an Atheros AR242x 802.11 wireless card on ubuntu 8.04. I'm new to Ubuntu/Linux all together. Got sick of vista and wanted to try something new on my Sony Vaio laptop.

I'm sorry for being "that guy" posting an over posted thread, but none of them seemed to help.

Thanks

---

### Post by willca on 2008-10-07
Click on the Ubuntu start button 
Go to system and click on the “Hardware Drivers Manager” 
This is where you will find all proprietary drivers. But we’re looking for everything that has Atheros in it. Tick the box in behind of “Atheros Hardware Access Layer(HAL)” and “Support for Atheros 802.11 wireless LAN cards” and restart the computer.

After that do the following.

Open up a terminal.
mkdir atheros
cd atheros
wget -c [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar xvf madwifi*.tar.gz
cd madwifi*r3862*
sudo apt-get update
sudo apt-get install build-essential
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

Reboot and check if it works by running.

sudo iwlist ath0 scan

---

### Post by qjmoss on 2008-10-07
Ok, from what I understand Kubuntu is the same OS, just uses KDE instead of Gnome. So does this mean I can use the script above for Kubuntu?

---

### Post by nomind111 on 2008-10-07
did you mean enable the a
theros drivers by ticking or disable? 

vichara@sage:~$ mkdir atheros
mkdir: cannot create directory `atheros': File exists
vichara@sage:~$ cd atheros
vichara@sage:~/atheros$ wget -c [http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz)
--15:56:12--  [http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz)
           => `madwifi...current.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:56:13 ERROR 404: Not Found.

---

### Post by willca on 2008-10-08
> **qjmoss said:**
> Ok, from what I understand Kubuntu is the same OS, just uses KDE instead of Gnome. So does this mean I can use the script above for Kubuntu?

Yes you can.

---

### Post by willca on 2008-10-08
> **nomind111 said:**
> did you mean enable the a
theros drivers by ticking or disable? 

vichara@sage:~$ mkdir atheros
mkdir: cannot create directory `atheros': File exists
vichara@sage:~$ cd atheros
vichara@sage:~/atheros$ wget -c [http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz)
--15:56:12--  [http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz)
           => `madwifi...current.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:56:13 ERROR 404: Not Found.


You want to disable it. Dont know however it needs to be tick'd or click'd in that GUI you see ;)

---

### Post by nomind111 on 2008-10-08
what i posted above is the progress i got, with it disabled(atheros).  any ideas? thanks.:)

---

### Post by Commodore64 on 2008-10-08
hello guys,

willcas advice worked perfect for me with just a little change 

HTTP request sent, awaiting response... 404 Not Found
15:56:13 ERROR 404: Not Found.

I believe this is an internet error whereby either the page does not exist or has changed place 

follow the steps that willca posted but in the line

 wget -c http//snapshots.madwifi.org etc..... substitute this line...

 madwifi-hal-0.10.5.6-current.tar.gz         for what comes after the 

[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

ie your http:// should read      snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

 be sure that the atheros drivers in hardware drivers are in use ie have the tick mark showing and note that for me the line 

sudo modprobe wlan_scan_sta

brought up and error.This however I believe can be overlooked as it had no bearing on the result for me 

hope this helps.

---

### Post by spiderterp on 2008-10-09
I am also a new user with this same problem. I was following the directions which worked to the point of the "make" command. Here is all the output if someone can help me! Thanks in advance.

dawn@deanna-laptop:~$ cd atheros
dawn@deanna-laptop:~/atheros$ cd madwifi*r3862*
bash: cd: madwifi*r3862*: No such file or directory
dawn@deanna-laptop:~/atheros$ sudo apt-get update
[sudo] password for dawn: 
Sorry, try again.
[sudo] password for dawn: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
dawn@deanna-laptop:~/atheros$ sudo apt-get install build essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build
dawn@deanna-laptop:~/atheros$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dawn@deanna-laptop:~/atheros$ make
make: *** No targets specified and no makefile found.  Stop.
dawn@deanna-laptop:~/atheros$ sudo make install
make: *** No rule to make target `install'.  Stop.
dawn@deanna-laptop:~/atheros$ sudo modprobe ath_pci
dawn@deanna-laptop:~/atheros$

---

### Post by TheSmokingGNU on 2008-10-09
Need help installing Atheros AR2413 card
lspci -nn
lshw -C network

i was told to include these in my post by a very helpful person here. I did the lspci -nn and got that my belking g desktop card is being viewed as an Atheros AR2413 card. I am running a dual boot, and windows has internet, so the going will be slow. every time i have to do anything in the terminal i have to restart.
I am running ubuntu, and i have an intel core 2 duo e8400 processor for what it's worth.

anyone, I need help with this. I am using my neighbor's wireless, but I don't know the configuration for it.

---

### Post by nomind111 on 2008-10-10
spiderterb:

i also got the same thing, everything worked up to where you posted.  have any luck resolving it yet? boy, this is week 2 trying to get this to work!!

---

### Post by robrink on 2008-10-10
Hi guys,
I'm another absolute noob to Ubuntu(2 days) and I tried for over 8 hours to get mine to work. Used Willca's guide along with the new link that Commodore64 supplied and got it nailed! I guess it goes without saying, but you must be hooked up to the net to get this to work. You'll know it's going to work when all the code comes flying by with no errors reported. Thanks a Bunch guys!

---

### Post by qjmoss on 2008-10-10
Guys, still can't get it. sorry for the late response

quentin@quentin-laptop:~$ mkdir atheros
mkdir: cannot create directory `atheros': File exists
quentin@quentin-laptop:~$ cd atheros
quentin@quentin-laptop:~/atheros$ wget -c [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
--20:00:02--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
           => `madwifi-hal-0.10.5.6-current.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

quentin@quentin-laptop:~/atheros$ tar xvf madwifi*.tar.gz
madwifi-hal-0.10.5.6-r3861-20080903/
madwifi-hal-0.10.5.6-r3861-20080903/THANKS
madwifi-hal-0.10.5.6-r3861-20080903/scripts/
madwifi-hal-0.10.5.6-r3861-20080903/scripts/hal_unmangle.sed
madwifi-hal-0.10.5.6-r3861-20080903/scripts/hal_unmangle.objcopy
madwifi-hal-0.10.5.6-r3861-20080903/scripts/madwifi-unload
madwifi-hal-0.10.5.6-r3861-20080903/scripts/if_ath_hal_generator.pl
madwifi-hal-0.10.5.6-r3861-20080903/scripts/get_arch.mk
madwifi-hal-0.10.5.6-r3861-20080903/scripts/find-madwifi-modules.sh
madwifi-hal-0.10.5.6-r3861-20080903/scripts/make-release.bash
madwifi-hal-0.10.5.6-r3861-20080903/scripts/hal_unmangle_log
madwifi-hal-0.10.5.6-r3861-20080903/scripts/madwifi-indent
madwifi-hal-0.10.5.6-r3861-20080903/scripts/update_hal_unmangle
madwifi-hal-0.10.5.6-r3861-20080903/regression/
madwifi-hal-0.10.5.6-r3861-20080903/regression/ccmp/
madwifi-hal-0.10.5.6-r3861-20080903/regression/ccmp/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/regression/ccmp/test_ccmp.c
madwifi-hal-0.10.5.6-r3861-20080903/regression/tkip/
madwifi-hal-0.10.5.6-r3861-20080903/regression/tkip/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/regression/tkip/test_tkip.c
madwifi-hal-0.10.5.6-r3861-20080903/regression/wep/
madwifi-hal-0.10.5.6-r3861-20080903/regression/wep/test_wep.c
madwifi-hal-0.10.5.6-r3861-20080903/regression/wep/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/regression/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/BuildCaps.inc
madwifi-hal-0.10.5.6-r3861-20080903/ath/
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal_extensions.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_athvar.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal_macros.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal_extensions.c
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_radar.c
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal_wrappers.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_pci.c
madwifi-hal-0.10.5.6-r3861-20080903/ath/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_radar.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_athioctl.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_pci.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_ahb.c
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_debug.h
madwifi-hal-0.10.5.6-r3861-20080903/ath/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath.c
madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_ahb.h
madwifi-hal-0.10.5.6-r3861-20080903/tools/
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/wlanconfig.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/athkey.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/athctrl.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/80211debug.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/athdebug.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/athchans.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/athstats.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/man/80211stats.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/athctrl.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/athdebug.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/80211stats.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/wlanconfig.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/athstats.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info/
madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info/README
madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info/ath_info.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info/ath_info.8
madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/tools/wpakey.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/wireless_copy.h
madwifi-hal-0.10.5.6-r3861-20080903/tools/athchans.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/athkey.c
madwifi-hal-0.10.5.6-r3861-20080903/tools/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/tools/80211debug.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/ah_osdep.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/ah_os.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/ah_target.inc
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/ah_os.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/Config.in
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/README
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/Kconfig
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/install.sh
madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel/Configure.help.patch
madwifi-hal-0.10.5.6-r3861-20080903/net80211/
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_rate.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_var.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_linux.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/if_media.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/if_media.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/if_ethersubr.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_scan.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_rate.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/if_llc.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_wireless.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_radiotap.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_node.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto_tkip.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_input.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_scan.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_output.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto_ccmp.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_power.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_debug.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_monitor.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_scan_ap.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto_none.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_ioctl.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_beacon.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_linux.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/if_athproto.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_skb.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_node.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_xauth.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_monitor.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_power.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_acl.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_crypto_wep.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_scan_sta.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/_ieee80211.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_proto.h
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_proto.c
madwifi-hal-0.10.5.6-r3861-20080903/net80211/ieee80211_skb.c
madwifi-hal-0.10.5.6-r3861-20080903/COPYRIGHT
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe/
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe/onoe.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe/onoe.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/minstrel.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/minstrel.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/minstrel.txt
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample/
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample/sample.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample/sample.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr/
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr/amrr.c
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr/amrr.h
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/include/
madwifi-hal-0.10.5.6-r3861-20080903/include/compat.h
madwifi-hal-0.10.5.6-r3861-20080903/include/sys/
madwifi-hal-0.10.5.6-r3861-20080903/include/sys/queue.h
madwifi-hal-0.10.5.6-r3861-20080903/Makefile.inc
madwifi-hal-0.10.5.6-r3861-20080903/kernelversion.c
madwifi-hal-0.10.5.6-r3861-20080903/README
madwifi-hal-0.10.5.6-r3861-20080903/Makefile.kernel
madwifi-hal-0.10.5.6-r3861-20080903/INSTALL
madwifi-hal-0.10.5.6-r3861-20080903/SNAPSHOT
madwifi-hal-0.10.5.6-r3861-20080903/contrib/
madwifi-hal-0.10.5.6-r3861-20080903/contrib/madwifi.spec.in
madwifi-hal-0.10.5.6-r3861-20080903/contrib/madwifi.spec
madwifi-hal-0.10.5.6-r3861-20080903/README.dfs
madwifi-hal-0.10.5.6-r3861-20080903/Makefile
madwifi-hal-0.10.5.6-r3861-20080903/hal/
madwifi-hal-0.10.5.6-r3861-20080903/hal/ah_devid.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/COPYRIGHT
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap30.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/i386-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap30.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/i386-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap51.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/wisoc.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/alpha-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/wackelf.c
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap43.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc64-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap30.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/alpha-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap61.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc64-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sh4-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/arm9-le-thumb-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-eabi.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-eabi.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-eabi.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/wisoc.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sh4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-le-eabi.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-le-eabi.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/x86_64-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sh4-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/arm9-le-thumb-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/alpha-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/arm9-le-thumb-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-le-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap43.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap51.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap61.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/i386-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips1-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/x86_64-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap51.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/armv4-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mips-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/mipsisa32-le-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc-be-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/wisoc.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/powerpc-le-eabi.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-be-elf.inc
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap61.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/x86_64-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/ap43.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/sparc64-be-elf.hal.o.uu
madwifi-hal-0.10.5.6-r3861-20080903/hal/public/xscale-le-elf.opt_ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/ah_soc.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/README
madwifi-hal-0.10.5.6-r3861-20080903/hal/version.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/ah.h
madwifi-hal-0.10.5.6-r3861-20080903/hal/ah_desc.h
madwifi-hal-0.10.5.6-r3861-20080903/release.h
quentin@quentin-laptop:~/atheros$ cd madwifi*r3862*
bash: cd: madwifi*r3862*: No such file or directory
quentin@quentin-laptop:~/atheros$ sudo apt-get update
[sudo] password for quentin: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
quentin@quentin-laptop:~/athero





Thats what i got.

A couple errors. 

help if ya can =/

---

### Post by Commodore64 on 2008-10-11
hey guys

 your problem is the directory name.

if you still have all the downloaded files in place in the file  atheros then follow these steps 

open terminal
cd atheros
cd madwifi*r386*  
sudo apt-get update
sudo apt-get install build-essential
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

everything should work fine after that

---

### Post by nomind111 on 2008-10-11
everything worked, up until the last command:
sudo modprobe wlan_scan_sta - this is what i came up with.

vichara@sage:~/atheros/madwifi-hal-0.10.5.6-r3861-20080903$ sudo modprobe wlan_scan_sta
FATAL: Error inserting wlan_scan_sta (/lib/modules/2.6.24-19-generic/net/wlan_scan_sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

here's the out when i typed in dmesg


[    0.000000] ACPI: BOOT 6FF64FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454994
[    0.000000] Kernel command line: root=UUID=0d7d073e-27bc-481e-90f7-08ef0bd3889f ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1800.299 MHz processor.
[   16.229417] spurious 8259A interrupt: IRQ7.
[   16.233108] Console: colour VGA+ 80x25
[   16.233111] console [tty0] enabled
[   16.233383] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.233758] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.306352] Memory: 1806480k/1834304k available (2177k kernel code, 26644k reserved, 1006k data, 368k init, 916800k highmem)
[   16.306361] virtual kernel memory layout:
[   16.306362]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.306363]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.306364]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.306365]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.306367]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.306368]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   16.306369]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   16.306372] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.306406] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.306550] hpet clockevent registered
[   16.386440] Calibrating delay using timer specific routine.. 3604.28 BogoMIPS (lpj=7208575)
[   16.386461] Security Framework initialized
[   16.386466] SELinux:  Disabled at boot.
[   16.386479] AppArmor: AppArmor initialized
[   16.386483] Failure registering capabilities with primary security module.
[   16.386491] Mount-cache hash table entries: 512
[   16.386595] Initializing cgroup subsys ns
[   16.386598] Initializing cgroup subsys cpuacct
[   16.386607] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   16.386615] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.386618] CPU: L2 Cache: 512K (64 bytes/line)
[   16.386620] CPU 0(2) -> Core 0
[   16.386622] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   16.386633] Compat vDSO mapped to ffffe000.
[   16.386642] Checking 'hlt' instruction... OK.
[   16.402682] SMP alternatives: switching to UP code
[   16.403842] Early unpacking initramfs... done
[   16.740377] ACPI: Core revision 20070126
[   16.740439] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.151039] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   17.151056] SMP alternatives: switching to SMP code
[   17.151512] Booting processor 1/1 eip 3000
[   17.161692] Initializing CPU#1
[   17.241404] Calibrating delay using timer specific routine.. 3600.51 BogoMIPS (lpj=7201037)
[   17.241411] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   17.241418] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.241420] CPU: L2 Cache: 512K (64 bytes/line)
[   17.241422] CPU 1(2) -> Core 1
[   17.241424] AMD C1E detected late. 	Force timer broadcast.
[   17.241425] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   17.241426] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   17.241443] Total of 2 processors activated (7204.80 BogoMIPS).
[   17.241682] ENABLING IO-APIC IRQs
[   17.241915] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.281699] Brought up 2 CPUs
[   17.281745] CPU0 attaching sched-domain:
[   17.281747]  domain 0: span 03
[   17.281749]   groups: 01 02
[   17.281752] CPU1 attaching sched-domain:
[   17.281754]  domain 0: span 03
[   17.281755]   groups: 02 01
[   17.281947] net_namespace: 64 bytes
[   17.281953] Booting paravirtualized kernel on bare hardware
[   17.282421] Time: 14:25:07  Date: 10/11/08
[   17.282444] NET: Registered protocol family 16
[   17.282627] EISA bus registered
[   17.282631] ACPI: bus type pci registered
[   17.303605] PCI: PCI BIOS revision 3.00 entry at 0xfda7d, last bus=5
[   17.303607] PCI: Using configuration type 1
[   17.303616] Setting up standard PCI resources
[   17.305432] ACPI: EC: Look up EC in DSDT
[   17.308047] ACPI: Interpreter enabled
[   17.308050] ACPI: (supports S0 S3 S4 S5)
[   17.308061] ACPI: Using IOAPIC for interrupt routing
[   17.313517] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.381412] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   17.381415] ACPI: EC: driver started in interrupt mode
[   17.381462] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.382380] PCI: Transparent bridge - 0000:00:08.0
[   17.382565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.382646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   17.382664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   17.382691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   17.413389] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 11) *10
[   17.413599] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *11)
[   17.413814] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 11) *0, disabled.
[   17.414021] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 11) *0, disabled.
[   17.414228] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   17.414435] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   17.414641] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   17.414847] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   17.415052] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[   17.415259] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *11
[   17.415466] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *7
[   17.415678] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[   17.415886] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[   17.416093] ACPI: PCI Interrupt Link [LGPU] (IRQs 17) *10
[   17.416299] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
[   17.416507] ACPI: PCI Interrupt Link [LSI0] (IRQs 20 21 22 23) *5
[   17.416719] ACPI: PCI Interrupt Link [Z00N] (IRQs 20 21 22 23) *10
[   17.416930] ACPI: PCI Interrupt Link [Z00O] (IRQs 20 21 22 23) *11
[   17.417137] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[   17.417279] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.417310] pnp: PnP ACPI init
[   17.417317] ACPI: bus type pnp registered
[   17.455483] pnp: PnP ACPI: found 13 devices
[   17.455485] ACPI: ACPI bus type pnp unregistered
[   17.455488] PnPBIOS: Disabled by ACPI PNP
[   17.455711] PCI: Using ACPI for IRQ routing
[   17.455714] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.485516] NET: Registered protocol family 8
[   17.485518] NET: Registered protocol family 20
[   17.485551] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   17.485555] hpet0: 3 32-bit timers, 25000000 Hz
[   17.486596] AppArmor: AppArmor Filesystem Enabled
[   17.489308] Time: hpet clocksource has been installed.
[   17.489312] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.489315] Could not switch to high resolution mode on CPU 0
[   17.493500] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.493504] Could not switch to high resolution mode on CPU 1
[   17.501523] system 00:01: ioport range 0x360-0x361 has been reserved
[   17.501526] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   17.501534] system 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.501541] system 00:0a: ioport range 0x1000-0x107f has been reserved
[   17.501544] system 00:0a: ioport range 0x1080-0x10ff has been reserved
[   17.501547] system 00:0a: ioport range 0x1400-0x147f has been reserved
[   17.501550] system 00:0a: ioport range 0x1480-0x14ff has been reserved
[   17.501552] system 00:0a: ioport range 0x1800-0x187f has been reserved
[   17.501555] system 00:0a: ioport range 0x1880-0x18ff has been reserved
[   17.501561] system 00:0c: iomem range 0xffc00000-0xffffffff could not be reserved
[   17.501565] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.501568] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   17.501571] system 00:0c: iomem range 0xfed00000-0xfed00fff has been reserved
[   17.501574] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   17.501577] system 00:0c: iomem range 0xfef00000-0xfef00fff has been reserved
[   17.531958] PCI: Bridge: 0000:00:08.0
[   17.531960]   IO window: disabled.
[   17.531964]   MEM window: d0500000-d05fffff
[   17.531966]   PREFETCH window: disabled.
[   17.531969] PCI: Bridge: 0000:00:0c.0
[   17.531971]   IO window: 4000-4fff
[   17.531974]   MEM window: d0200000-d03fffff
[   17.531976]   PREFETCH window: d0000000-d01fffff
[   17.531979] PCI: Bridge: 0000:00:0d.0
[   17.531981]   IO window: disabled.
[   17.531983]   MEM window: d0400000-d04fffff
[   17.531985]   PREFETCH window: disabled.
[   17.531996] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.532005] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.532012] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.532023] NET: Registered protocol family 2
[   17.573453] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.573726] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.574377] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.574707] TCP: Hash tables configured (established 131072 bind 65536)
[   17.574709] TCP reno registered
[   17.589501] checking if image is initramfs... it is
[   18.241080] Freeing initrd memory: 7322k freed
[   18.241176] Simple Boot Flag at 0x36 set to 0x1
[   18.241808] audit: initializing netlink socket (disabled)
[   18.241819] audit(1223735107.532:1): initialized
[   18.241990] highmem bounce pool size: 64 pages
[   18.243858] VFS: Disk quotas dquot_6.5.1
[   18.243935] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.244052] io scheduler noop registered
[   18.244054] io scheduler anticipatory registered
[   18.244056] io scheduler deadline registered
[   18.244066] io scheduler cfq registered (default)
[   18.244097] pci 0000:00:00.0: Enabling HT MSI Mapping
[   18.244233] pci 0000:00:07.0: Enabling HT MSI Mapping
[   18.244247] pci 0000:00:08.0: Enabling HT MSI Mapping
[   18.244262] pci 0000:00:09.0: Enabling HT MSI Mapping
[   18.244278] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   18.244292] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   18.244306] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   18.244320] Boot video device is 0000:00:12.0
[   18.244437] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.244460] assign_interrupt_mode Found MSI capability
[   18.244480] Allocate Port Service[0000:00:0c.0:pcie00]
[   18.244543] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.244565] assign_interrupt_mode Found MSI capability
[   18.244581] Allocate Port Service[0000:00:0d.0:pcie00]
[   18.244797] isapnp: Scanning for PnP cards...
[   18.596878] isapnp: No Plug & Play device found
[   18.624586] Real Time Clock Driver v1.12ac
[   18.624779] hpet_resources: 0xfed00000 is busy
[   18.624803] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.625913] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.625977] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.626069] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.660797] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.660802] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.671865] mice: PS/2 mouse device common for all mice
[   18.671984] EISA: Probing bus 0 at eisa.0
[   18.671989] Cannot allocate resource for EISA slot 1
[   18.671994] Cannot allocate resource for EISA slot 3
[   18.671997] Cannot allocate resource for EISA slot 4
[   18.672009] EISA: Detected 0 cards.
[   18.672012] cpuidle: using governor ladder
[   18.672014] cpuidle: using governor menu
[   18.672093] NET: Registered protocol family 1
[   18.672116] Using IPI No-Shortcut mode
[   18.672146] registered taskstats version 1
[   18.672267]   Magic number: 12:708:434
[   18.672401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.672403] EDD information not available.
[   18.672612] Freeing unused kernel memory: 368k freed
[   18.693421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.944704] fuse init (API version 7.9)
[   19.965756] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.965763] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.965788] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.965799] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.998840] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   20.012947] ACPI: Thermal Zone [THRM] (32 C)
[   20.219458] usbcore: registered new interface driver usbfs
[   20.219481] usbcore: registered new interface driver hub
[   20.220080] usbcore: registered new device driver usb
[   20.221652] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.222044] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   20.222053] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 23 (level, low) -> IRQ 16
[   20.222065] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.222069] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   20.222337] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   20.222354] ohci_hcd 0000:00:02.0: irq 16, io mem 0xd0886000
[   20.283574] usb usb1: configuration #1 chosen from 1 choice
[   20.283599] hub 1-0:1.0: USB hub found
[   20.283606] hub 1-0:1.0: 5 ports detected
[   20.389760] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 22
[   20.389771] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z00N] -> GSI 22 (level, low) -> IRQ 17
[   20.389784] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.389788] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   20.389811] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   20.389826] ohci_hcd 0000:00:04.0: irq 17, io mem 0xd0887000
[   20.451311] usb usb2: configuration #1 chosen from 1 choice
[   20.451338] hub 2-0:1.0: USB hub found
[   20.451346] hub 2-0:1.0: 5 ports detected
[   20.550740] SCSI subsystem initialized
[   20.557391] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[   20.557401] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 21 (level, low) -> IRQ 18
[   20.557413] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.557417] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   20.557441] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   20.557470] ehci_hcd 0000:00:02.1: debug port 1
[   20.557474] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   20.557485] ehci_hcd 0000:00:02.1: irq 18, io mem 0xd0889000
[   20.558462] libata version 3.00 loaded.
[   20.700866] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   20.712834] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.712956] usb usb3: configuration #1 chosen from 1 choice
[   20.712979] hub 3-0:1.0: USB hub found
[   20.712985] hub 3-0:1.0: 5 ports detected
[   20.821096] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 20
[   20.821107] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z00O] -> GSI 20 (level, low) -> IRQ 19
[   20.821120] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   20.821123] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   20.821148] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   20.821176] ehci_hcd 0000:00:04.1: debug port 1
[   20.821180] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   20.821190] ehci_hcd 0000:00:04.1: irq 19, io mem 0xd0889400
[   20.832665] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.832752] usb usb4: configuration #1 chosen from 1 choice
[   20.832773] hub 4-0:1.0: USB hub found
[   20.832779] hub 4-0:1.0: 5 ports detected
[   20.936845] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   20.936859] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   20.988566] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[d0500000-d05007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.993947] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   20.994275] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   20.994278] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 16
[   20.994283] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.363893] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   21.509355] usb 3-3: configuration #1 chosen from 1 choice
[   21.512236] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:38:d0:14:b7
[   21.512242] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   21.526040] ahci 0000:00:09.0: version 3.0
[   21.526390] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 22
[   21.526394] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 22 (level, low) -> IRQ 17
[   22.022938] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   22.240745] usb 2-2: configuration #1 chosen from 1 choice
[   22.260239] usbcore: registered new interface driver hiddev
[   22.262515] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f81ba40d0d9]
[   22.266804] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input2
[   22.286618] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.0-2
[   22.286634] usbcore: registered new interface driver usbhid
[   22.286638] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.526223] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.526228] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   22.526233] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.526542] scsi0 : ahci
[   22.526799] scsi1 : ahci
[   22.526935] scsi2 : ahci
[   22.527070] scsi3 : ahci
[   22.527147] ata1: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884100 irq 221
[   22.527151] ata2: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884180 irq 221
[   22.527154] ata3: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884200 irq 221
[   22.527157] ata4: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884280 irq 221
[   23.173281] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.224761] ata1.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[   23.224765] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.225576] ata1.00: configured for UDMA/133
[   23.548740] ata2: SATA link down (SStatus 0 SControl 300)
[   23.876267] ata3: SATA link down (SStatus 0 SControl 300)
[   24.203794] ata4: SATA link down (SStatus 0 SControl 300)
[   24.203889] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[   24.203790] pata_amd 0000:00:06.0: version 0.3.10
[   24.203844] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.204082] scsi4 : pata_amd
[   24.204234] scsi5 : pata_amd
[   24.204579] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   24.204582] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   24.527683] ata5.00: ATAPI: Optiarc DVD RW AD-7530B, NX09, max UDMA/33
[   24.699296] ata5.00: configured for UDMA/33
[   24.699327] ata6: port disabled. ignoring.
[   24.700598] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX09 PQ: 0 ANSI: 5
[   24.714962] Driver 'sd' needs updating - please use bus_type methods
[   24.715659] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   24.715672] sd 0:0:0:0: [sda] Write Protect is off
[   24.715674] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.715690] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.715736] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   24.715745] sd 0:0:0:0: [sda] Write Protect is off
[   24.715747] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.715764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.715767]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.768450]  sda1 sda2 < sda5 >
[   24.792863] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.798091] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.798112] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   24.809030] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.809035] Uniform CD-ROM driver Revision: 3.20
[   24.809090] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   25.110005] Attempting manual resume
[   25.110009] swsusp: Resume From Partition 8:5
[   25.110011] PM: Checking swsusp image.
[   25.110183] PM: Resume from disk failed.
[   25.165348] kjournald starting.  Commit interval 5 seconds
[   25.165536] EXT3-fs: mounted filesystem with ordered data mode.
[   31.904812] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.995590] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.152433] Linux agpgart interface v0.102
[   32.307873] input: Power Button (FF) as /devices/virtual/input/input3
[   32.320134] ACPI: Power Button (FF) [PWRF]
[   32.320239] input: Lid Switch as /devices/virtual/input/input4
[   32.330396] ACPI: Lid Switch [LID]
[   32.330477] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.352048] ACPI: Sleep Button (CM) [SLPB]
[   32.352161] input: Power Button (CM) as /devices/virtual/input/input6
[   32.389543] nvidia: module license 'NVIDIA' taints kernel.
[   32.400062] ACPI: Power Button (CM) [PWRB]
[   32.831745] ACPI: WMI-Acer: Mapper loaded
[   33.351636] ACPI: AC Adapter [ACAD] (on-line)
[   33.513060] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   33.513066] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 18
[   33.513085] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   33.623604] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 17
[   33.623616] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 17 (level, low) -> IRQ 20
[   33.623624] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   33.623844] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   33.828933] ACPI: Battery Slot [BAT1] (battery present)
[   33.878745] ricoh-mmc: Ricoh MMC Controller disabling driver
[   33.878750] ricoh-mmc: Copyright(c) Philip Langdale
[   33.878815] ricoh-mmc: Ricoh MMC controller found at 0000:01:04.2 [1180:0843] (rev 12)
[   33.878824] ricoh-mmc: Controller is now disabled.
[   33.962254] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.025094] sdhci: Secure Digital Host Controller Interface driver
[   34.025099] sdhci: Copyright(c) Pierre Ossman
[   34.025143] sdhci: SDHCI controller found at 0000:01:04.1 [1180:0822] (rev 22)
[   34.025482] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   34.025485] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   34.025500] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   34.025547] mmc0: SDHCI at 0xd0500800 irq 11 DMA
[   34.161536] wlan: 0.9.4
[   34.225443] ath_pci: 0.9.4
[   34.225834] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   34.225844] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 21
[   34.225854] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   34.253656] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   34.253676] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   34.334843] Linux video capture interface: v2.00
[   34.438590] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   34.485947] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   34.487613] usbcore: registered new interface driver uvcvideo
[   34.487619] USB Video Class driver (v0.1.0)
[   34.579272] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   34.579278] acer_acpi: Detected Acer WMID interface
[   35.023675] input: PS/2 Mouse as /devices/virtual/input/input8
[   35.098966] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   35.893083] lp: driver loaded but no devices found
[   36.026641] Adding 5309440k swap on /dev/sda5.  Priority:-1 extents:1 across:5309440k
[   36.585972] EXT3 FS on sda1, internal journal
[   37.924393] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.443811] No dock devices found.
[   38.930475] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   38.930389] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   38.930394] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   38.930397] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   39.872781] apm: BIOS not found.
[   40.007001] ppdev: user-space parallel port driver
[   40.125279] audit(1223735130.382:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5263 profile="/usr/sbin/cupsd" namespace="default"
[   40.579630] Clocksource tsc unstable (delta = -124473918 ns)
[   41.325471] Bluetooth: Core ver 2.11
[   41.325934] NET: Registered protocol family 31
[   41.325939] Bluetooth: HCI device and connection manager initialized
[   41.325944] Bluetooth: HCI socket layer initialized
[   41.369578] Bluetooth: L2CAP ver 2.9
[   41.369583] Bluetooth: L2CAP socket layer initialized
[   41.455838] Bluetooth: RFCOMM socket layer initialized
[   41.455851] Bluetooth: RFCOMM TTY layer initialized
[   41.455853] Bluetooth: RFCOMM ver 1.8
[   43.166700] NET: Registered protocol family 17
[   47.351300] NET: Registered protocol family 10
[   47.351514] lo: Disabled Privacy Extensions
[   52.586927] eth0: no IPv6 routers present
[   94.255418] CPU0 attaching NULL sched-domain.
[   94.255423] CPU1 attaching NULL sched-domain.
[   94.272528] CPU0 attaching sched-domain:
[   94.272535]  domain 0: span 03
[   94.272537]   groups: 01 02
[   94.272540] CPU1 attaching sched-domain:
[   94.272542]  domain 0: span 03
[   94.272544]   groups: 02 01
[ 6922.541695] wlan_scan_sta: disagrees about version of symbol ieee80211_find_channel
[ 6922.541710] wlan_scan_sta: Unknown symbol ieee80211_find_channel
[ 6922.541764] wlan_scan_sta: disagrees about version of symbol ieee80211_scan_dump_channels
[ 6922.541768] wlan_scan_sta: Unknown symbol ieee80211_scan_dump_channels
[ 6922.541807] wlan_scan_sta: disagrees about version of symbol ieee80211_create_ibss
[ 6922.541811] wlan_scan_sta: Unknown symbol ieee80211_create_ibss
[ 6922.541847] wlan_scan_sta: disagrees about version of symbol ieee80211_note
[ 6922.541850] wlan_scan_sta: Unknown symbol ieee80211_note
[ 6922.541899] wlan_scan_sta: disagrees about version of symbol ieee80211_start_scan
[ 6922.541902] wlan_scan_sta: Unknown symbol ieee80211_start_scan
[ 6922.541948] wlan_scan_sta: disagrees about version of symbol ieee80211_sta_join
[ 6922.541952] wlan_scan_sta: Unknown symbol ieee80211_sta_join
[ 6922.541987] wlan_scan_sta: disagrees about version of symbol ieee80211_note_mac
[ 6922.541991] wlan_scan_sta: Unknown symbol ieee80211_note_mac
[ 6922.542030] wlan_scan_sta: disagrees about version of symbol ieee80211_bg_scan
[ 6922.542034] wlan_scan_sta: Unknown symbol ieee80211_bg_scan
[ 6922.542076] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_register
[ 6922.542079] wlan_scan_sta: Unknown symbol ieee80211_scanner_register
[ 6922.542113] wlan_scan_sta: disagrees about version of symbol ieee80211_chan2ieee
[ 6922.542117] wlan_scan_sta: Unknown symbol ieee80211_chan2ieee
[ 6922.542192] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_unregister_all
[ 6922.542195] wlan_scan_sta: Unknown symbol ieee80211_scanner_unregister_all
[ 6977.829447] wlan_scan_sta: disagrees about version of symbol ieee80211_find_channel
[ 6977.829458] wlan_scan_sta: Unknown symbol ieee80211_find_channel
[ 6977.829514] wlan_scan_sta: disagrees about version of symbol ieee80211_scan_dump_channels
[ 6977.829518] wlan_scan_sta: Unknown symbol ieee80211_scan_dump_channels
[ 6977.829557] wlan_scan_sta: disagrees about version of symbol ieee80211_create_ibss
[ 6977.829561] wlan_scan_sta: Unknown symbol ieee80211_create_ibss
[ 6977.829596] wlan_scan_sta: disagrees about version of symbol ieee80211_note
[ 6977.829600] wlan_scan_sta: Unknown symbol ieee80211_note
[ 6977.829649] wlan_scan_sta: disagrees about version of symbol ieee80211_start_scan
[ 6977.829653] wlan_scan_sta: Unknown symbol ieee80211_start_scan
[ 6977.829699] wlan_scan_sta: disagrees about version of symbol ieee80211_sta_join
[ 6977.829702] wlan_scan_sta: Unknown symbol ieee80211_sta_join
[ 6977.829738] wlan_scan_sta: disagrees about version of symbol ieee80211_note_mac
[ 6977.829741] wlan_scan_sta: Unknown symbol ieee80211_note_mac
[ 6977.829781] wlan_scan_sta: disagrees about version of symbol ieee80211_bg_scan
[ 6977.829784] wlan_scan_sta: Unknown symbol ieee80211_bg_scan
[ 6977.829826] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_register
[ 6977.829830] wlan_scan_sta: Unknown symbol ieee80211_scanner_register
[ 6977.829864] wlan_scan_sta: disagrees about version of symbol ieee80211_chan2ieee
[ 6977.829867] wlan_scan_sta: Unknown symbol ieee80211_chan2ieee
[ 6977.829942] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_unregister_all
[ 6977.829946] wlan_scan_sta: Unknown symbol ieee80211_scanner_unregister_all

---

### Post by Commodore64 on 2008-10-11
hey there nomind111,

that particular command did not work for me either but had no direct bearing on the result, go ahead and restart your computer and see if your wireless is working, dont forget to enable wireless networking in network manager and all should be ok.

---

