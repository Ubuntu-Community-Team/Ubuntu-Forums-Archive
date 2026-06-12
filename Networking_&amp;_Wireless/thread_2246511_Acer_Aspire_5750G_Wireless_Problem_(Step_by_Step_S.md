---
title: "Acer Aspire 5750G Wireless Problem (Step by Step Solution)"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by Ilgazman on 2014-10-01
Hi Dear Ubuntu Users! 
In this post, I am going to explain solution with **varunendra**'s help. And you can view my original post below this explaining.


[LIST=1]
[*]Firstly, You must supply your** connection** with** ethernet cable**
*(Do not look up with different computer because of solution)*.
[*]You must figure out your **net** informations with the code:
```
 lspci -nnk | grep -iA2 net 
```
[*]Now we must have a result of problem on your computer.  To detect what is your problem, we will use Wireless Script. 
You can find the **Wireless Script** of **varunendra** from [**here**]("http://ubuntuforums.org/showthread.php?p=12350385#post12350385").
[*]Your system must be updated, so you must update it with the code:
```
 sudo apt-get update 
```
[*]Then you must know that what is your wifii adaptor's name and model.
*(This is really important, and if you don't know, you'll learn it from **2nd step**. or Ask it to [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") of **ubuntuforums.org**)*
[*]Here we go! Now we have to update our wireless driver with the code [I](that is learnt from 2nd step):
[/I]```
 sudo apt-get install bcmwl-kernel-source 
```

(**PS:** this is my model's kernel source code, so be sure what is yours and typed your model's code.)
[/LIST]

Now you can use your WiFii :)

Thanks to **varunendra** for everything.



// Original post begins here...


Hi there, 

My system: Acer Aspire 5750g, Intel Core i5 @ 2.50GHz, 4 GB ram.

I installed **Ubuntu 14.4** but I can't activate my Wireless connection. 

I got results by the script of **varunendra**,

These are my results:

```
cry@cry-Aspire-5750G:~$ lspci -nnk | grep -iA2 net
02:00.0

 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    
Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    
Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    
Subsystem: Foxconn International, Inc. Device [105b:e040]
    
Kernel driver in use: bcma-pci-bridge


```


and your script's result is...

```
########## wireless info START ##########

Report from: 01 Oct 2014 19:00 EEST +0300

Booted last: 01 Oct 2014 18:42 EEST +0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288a Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  1 nouveau
bcma                   52096  0 
wmi                    19177  3 acer_wmi,mxm_wmi,nouveau
video                  19476  3 i915,acer_wmi,nouveau

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
          Interrupt:16 

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
  Driver:            tg3
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

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

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
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"

##### dmesg #############################

########## wireless info END ############
```


Please help me :/

---

### Post by varunendra on 2014-10-01
Hi abdullah6, Welcome to the forums!

With your Ethernet connection, please install the proprietary "wl" driver -
```
sudo apt-get install bcmwl-kernel-source
```
Reboot if required.

**PS:**
Instead of 'Quote' tags that you have used to post the outputs, please use 'Code' tags to preserve the formatting and make the post look cleaner and compact. Please follow the "Using Code Tags" link in my signature to see how. :)

---

### Post by slickymaster on 2014-10-01
*Moved to the ***Networking & Wireless*** sub-forum.*

Hi abdullah6, welcome to the forums.
I edited your post, replacing the 'Quote' tags with ['Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"), which are the proper tags to use when posting code output.

---

### Post by Ilgazman on 2014-10-01
> **varunendra said:**
> Hi abdullah6, Welcome to the forums!

With your Ethernet connection, please install the proprietary "wl" driver -
```
sudo apt-get install bcmwl-kernel-source
```
Reboot if required.

**PS:**
Instead of 'Quote' tags that you have used to post the outputs, please  use 'Code' tags to preserve the formatting and make the post look  cleaner and compact. Please follow the "Using Code Tags" link in my  signature to see how. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

```

cry@cry-Aspire-5750G:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for cry:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source

```

Should I connect my computer to Internet? (I'm posting now from different computer)

**PS:**
After my problem is solved, I will mark it as Solved, by the way thank you so much [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by Ilgazman on 2014-10-01
> **slickymaster said:**
> *Moved to the ***Networking & Wireless*** sub-forum.*

Hi abdullah6, welcome to the forums.
I edited your post, replacing the 'Quote' tags with ['Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"), which are the proper tags to use when posting code output.


Hi slickymaster, thank you.
I'll do it my future posts, thanks again.

**PS:**
I'll mark it as solved after I'm done with my wireless.

---

### Post by varunendra on 2014-10-01
> **abdullah6 said:**
> Should I connect my computer to Internet?

Yes, you do need to connect it to internet using an alternative connection. Your Ethernet card has an appropriate driver, so should work if you can get an ethernet cable from your modem/router to the laptop.

There are ways to install it offline too, but installing from internet is easiest.

You may have to run -
```
sudo apt-get update
```
..once after connecting to internet.

---

### Post by Ilgazman on 2014-10-01
> **varunendra said:**
> Yes, you do need to connect it to internet using an alternative connection. Your Ethernet card has an appropriate driver, so should work if you can get an ethernet cable from your modem/router to the laptop.

There are ways to install it offline too, but installing from internet is easiest.

You may have to run -
```
sudo apt-get update
```
..once after connecting to internet.

I got the connection with cable and now it's updated. What should I do now?

**PS:**
Now its updating Ubuntu's new version but Terminal is waiting your next call :)

This is my terminal now:

```

cry@cry-Aspire-5750G:~$ sudo apt-get update
[sudo] password for cry: 
Ign http://tr.archive.ubuntu.com trusty InRelease
Ign http://tr.archive.ubuntu.com trusty-updates InRelease                      
Ign http://tr.archive.ubuntu.com trusty-backports InRelease                    
Get:1 http://tr.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:2 http://tr.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:3 http://tr.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Get:4 http://tr.archive.ubuntu.com trusty Release [58,5 kB]                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:5 http://tr.archive.ubuntu.com trusty-updates Release [59,7 kB]            
Get:6 http://extras.ubuntu.com trusty Release.gpg [72 B]
Get:7 http://tr.archive.ubuntu.com trusty-backports Release [59,7 kB]          
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:8 http://extras.ubuntu.com trusty Release [11,9 kB]                        
Get:9 http://tr.archive.ubuntu.com trusty/main Sources [1.064 kB]              
Get:10 http://extras.ubuntu.com trusty/main Sources [14 B]                     
Get:11 http://security.ubuntu.com trusty-security Release.gpg [933 B]          
Get:12 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]              
Get:13 http://security.ubuntu.com trusty-security Release [59,7 kB]            
Get:14 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:15 http://tr.archive.ubuntu.com trusty/restricted Sources [5.433 B]        
Get:16 http://tr.archive.ubuntu.com trusty/universe Sources [6.399 kB]         
Get:17 http://security.ubuntu.com trusty-security/main Sources [46,3 kB]       
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:18 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Get:19 http://security.ubuntu.com trusty-security/universe Sources [10,8 kB]   
Get:20 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]   
Get:21 http://tr.archive.ubuntu.com trusty/multiverse Sources [174 kB]         
Get:22 http://security.ubuntu.com trusty-security/main amd64 Packages [146 kB] 
Get:23 http://tr.archive.ubuntu.com trusty/main amd64 Packages [1.350 kB]      
Get:24 http://tr.archive.ubuntu.com trusty/restricted amd64 Packages [13,0 kB] 
Get:25 http://tr.archive.ubuntu.com trusty/universe amd64 Packages [5.859 kB]  
Get:26 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:27 http://security.ubuntu.com trusty-security/universe amd64 Packages [49,0 kB]
Get:28 http://tr.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:29 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1.148 B]
Get:30 http://tr.archive.ubuntu.com trusty/main i386 Packages [1.348 kB]       
Get:31 http://security.ubuntu.com trusty-security/main i386 Packages [139 kB]  
Get:32 http://tr.archive.ubuntu.com trusty/restricted i386 Packages [13,4 kB]  
Get:33 http://tr.archive.ubuntu.com trusty/universe i386 Packages [5.866 kB]   
Get:34 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:35 http://security.ubuntu.com trusty-security/universe i386 Packages [49,0 kB]
Get:36 http://tr.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Get:37 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1.398 B]
Get:38 http://security.ubuntu.com trusty-security/main Translation-en [70,7 kB]
Get:39 http://tr.archive.ubuntu.com trusty/main Translation-en [762 kB]        
Get:40 http://tr.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]  
Get:41 http://tr.archive.ubuntu.com trusty/restricted Translation-en [3.457 B] 
Get:42 http://tr.archive.ubuntu.com trusty/universe Translation-en [4.089 kB]  
Get:43 http://security.ubuntu.com trusty-security/multiverse Translation-en [587 B]
Get:44 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]
Get:45 http://security.ubuntu.com trusty-security/universe Translation-en [28,7 kB]
Get:46 http://tr.archive.ubuntu.com trusty-updates/main Sources [125 kB]       
Get:47 http://tr.archive.ubuntu.com trusty-updates/restricted Sources [1.408 B]
Get:48 http://tr.archive.ubuntu.com trusty-updates/universe Sources [86,2 kB]  
Get:49 http://tr.archive.ubuntu.com trusty-updates/multiverse Sources [3.531 B]
Get:50 http://tr.archive.ubuntu.com trusty-updates/main amd64 Packages [337 kB]
Get:51 http://tr.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5.820 B]
Get:52 http://tr.archive.ubuntu.com trusty-updates/universe amd64 Packages [209 kB]
Get:53 http://tr.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9.397 B]
Get:54 http://tr.archive.ubuntu.com trusty-updates/main i386 Packages [331 kB] 
Get:55 http://tr.archive.ubuntu.com trusty-updates/restricted i386 Packages [5.820 B]
Get:56 http://tr.archive.ubuntu.com trusty-updates/universe i386 Packages [209 kB]
Get:57 http://tr.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9.564 B]
Get:58 http://tr.archive.ubuntu.com trusty-updates/main Translation-en [150 kB]
Get:59 http://tr.archive.ubuntu.com trusty-updates/multiverse Translation-en [4.719 B]
Get:60 http://tr.archive.ubuntu.com trusty-updates/restricted Translation-en [1.736 B]
Get:61 http://tr.archive.ubuntu.com trusty-updates/universe Translation-en [105 kB]
Get:62 http://tr.archive.ubuntu.com trusty-backports/main Sources [4.760 B]    
Get:63 http://tr.archive.ubuntu.com trusty-backports/restricted Sources [14 B] 
Get:64 http://tr.archive.ubuntu.com trusty-backports/universe Sources [13,7 kB]
Get:65 http://tr.archive.ubuntu.com trusty-backports/multiverse Sources [1.315 B]
Get:66 http://tr.archive.ubuntu.com trusty-backports/main amd64 Packages [6.356 B]
Get:67 http://tr.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:68 http://tr.archive.ubuntu.com trusty-backports/universe amd64 Packages [16,8 kB]
Get:69 http://tr.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [943 B]
Get:70 http://tr.archive.ubuntu.com trusty-backports/main i386 Packages [6.379 B]
Get:71 http://tr.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:72 http://tr.archive.ubuntu.com trusty-backports/universe i386 Packages [16,8 kB]
Get:73 http://tr.archive.ubuntu.com trusty-backports/multiverse i386 Packages [945 B]
Get:74 http://tr.archive.ubuntu.com trusty-backports/main Translation-en [4.216 B]
Get:75 http://tr.archive.ubuntu.com trusty-backports/multiverse Translation-en [613 B]
Get:76 http://tr.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:77 http://tr.archive.ubuntu.com trusty-backports/universe Translation-en [14,3 kB]
Ign http://tr.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://tr.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://tr.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://tr.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 29,8 MB in 11s (2.532 kB/s)                                            
Reading package lists... Done


```

---

### Post by varunendra on 2014-10-01
```
sudo apt-get install bcmwl-kernel-source
```
..and a reboot.

---

### Post by Ilgazman on 2014-10-01
> **varunendra said:**
> ```
sudo apt-get install bcmwl-kernel-source
```
..and a reboot.

Now, I'm using my **Wireless connection** and posting this with it :) Thank you so much!

---

### Post by varunendra on 2014-10-01
You're welcome!

Some of these cards still make us hold our breath until an "It works" confirmation is posted. ;)

Regarding the explanation you wrote in the 'Edit' of your first post - a good "**General**" guide about broadcom issues has already been written a while ago by our senior-most wireless guru chili555, and is now one of the two Stickys of the 'Networking & Wireless' section : [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

The word "General" is all the problem here, as wireless issues are usually very subjective, and broadcoms are particularly confusing. It is easy for us troubleshooters who are dedicated to 'Wireless' troubleshooting in particular, but really confusing for those who are not in constant touch with wireless stuff. There are four different drivers for various broadcom chips, and which one is suitable for which card is not always crystal clear.

For example, the driver you are using used to be the perfect driver for one of the variants - BCM4313 (ID being 14e4:4727), but not anymore. The *current* best is 'brcmsmac' for it, while the earlier *best* is now *often problematic*. To add to such confusions, the native driver, b43, needs proprietary firmware, the 'perfect' way to install which used to be installing the package "linux-firmware-nonfree", but now installing that actually has the potential to *remove the firmware* if it already exists. :shock:

As if it were not enough, there are plenty of ways to reach the four basic solutions, and then there are somewhat 'misleading' solutions which make it exponentially confusing. Take your *current* explanation for example - everything is well and good upto step 5, but step 6 really goes 'off-the-rails' :p

The name 'bcmwl-kernel-source' is a uniqe-style name for the driver you require - the "wl" driver (yeah, another confusion - "wl" is the name of driver, "STA" is its type, and "bcmwl-kernel-source" is the package that compiles-installs-and-configures it - three different names for the same thing. Oh, actually four - "the proprietary broadcom driver" is yet another one ;) ).

The other drivers are the native 'b43', or brcmsmac, or brcmfmac (variant of brcmsmac for USB devices) and don't have funny words like 'kernel' or 'source' in their names at all. Now the 'b43' needs 'Proprietary Firmware', and as if the terminology and the recurrence of the word 'proprietary' was not enough, the ways to install it have radically changed recently, and are still non-unique.

With this and much more of such details, we consider it to be the best to keep a *General Guide for Broadcoms* to the [wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), and keep a short version of it as the sticky. We intentionally omit many such details to avoid possible confusion to the user we are helping.

[INDENT][LIST]
[*]For those users, who are not afraid of a detailed guide, the **[wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")** is the best resource.
[*]For those users, who are interested in a 'Short-And-Quick' *General* guide, the **[sticky]("http://ubuntuforums.org/showthread.php?t=2214110")** is the best resource.
[*]For those users, who are not technically inclined at all, and need quick/clear/and simple solution, posting a thread and asking for help is the best approach.
[/LIST][/INDENT]

One of the most useful resource for us troubleshooters, regarding the broadcom chips, is this reference table : [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

Hope this post is as clear as it can possibly be :lolflag:

**PS:**
I think you should consider rephrasing step 6 of your explanation part in the first post. You can simply link it to the sticky thread, mentioning to look at the table in it to determine who needs what.

**PPS:**
The credits go to all those who help us know what we know, and that means multiple things, multiple people. We troubleshooters rely on each other's experience and posts as much as the wiki pages, and most importantly - the feedbacks from users like you which helps us know what works, what doesn't and what just broke. :p

---

