---
title: "Ubuntu 14.04: Atheros Wireless card not detected"
date: 2014-10-18
forum: Networking &amp; Wireless
---

### Post by alexandre19 on 2014-10-18
Hello,
I just bought an MSI GS60 and installed Ubuntu 14.04.1.
I have an issue with the WiFi : the card is not detected.
It works fine with Windows after installing the drivers.
The wired network interface works with windows and Ubuntu.

Here is the result of the wireless script :

```

########## wireless info START ##########

Report from: 18 Oct 2014 06:23 EDT -0400

Booted last: 18 Oct 2014 06:20 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1102]
    Kernel driver in use: alx

05:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1525]

##### lsusb #############################

Bus 002 Device 003: ID 1770:ff00  
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:055c Acer, Inc 
Bus 001 Device 003: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

msi_wmi                13354  0 
sparse_keymap          13948  1 msi_wmi
ath3k                  13318  0 
bluetooth             391136  12 bnep,ath3k,btusb,rfcomm
mxm_wmi                13021  1 nouveau
wmi                    19177  3 msi_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:8420:4bb6:7800:468a:5bff:fe6e:c261/64 Scope:Global
          inet6 addr: 2a02:8420:4bb6:7800:c199:864f:f219:81ee/64 Scope:Global
          inet6 addr: fe80::468a:5bff:fe6e:c261/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

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

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.99
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         2a02:8420:4bb6:7800:c199:864f:f219:81ee
    Prefix:          64
    Gateway:         fe80::327e:cbff:fe74:3818

    Address:         2a02:8420:4bb6:7800:468a:5bff:fe6e:c261
    Prefix:          64
    Gateway:         fe80::327e:cbff:fe74:3818

    Address:         fe80::468a:5bff:fe6e:c261
    Prefix:          64
    Gateway:         fe80::327e:cbff:fe74:3818

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

Region: America/New_York (based on set time zone)

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

[ath3k]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     661F5D1CDD236CFF7BE3FA5
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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
# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   17.847686] usb 1-1.3: Direct firmware load failed with error -2
[   17.904572] ath3k: probe of 1-1.3:1.0 failed with error -2

########## wireless info END ############


```

Here is also the information regarding my wireless card from Windows :
```
Killer Wireless-n/a/ac 1525 Wireless network adapter
```

Hope someone can help :)

---

### Post by jeremy31 on 2014-10-18
It might be as easy as ```
sudo modprobe ath9k
```

But I doubt it as I can't find much info on that card

---

### Post by chili555 on 2014-10-18
Just as a tool for Jeremy and the searchers to use, you can check the modalias tables for any driver to see if it covers any device:> Network controller [0280]: Qualcomm Atheros Device [[COLOR="#FF0000"]168c:003e[/COLOR]] (rev 20)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1525]So we check using the last four digits of the pci.id:```
modinfo ath9k | grep 003E
```In this case, it comes out blank. That means that ath9k does not yet cover the device in question.

As to whether it can or should drive your device, we turn to Google. As far as I can see, yours is the first seen in the universe! I see no mention of it anywhere. So far, I have no idea what the driver may be.

If you are intrepid and an experimenter, we could try amending the c code and compiling ath9k or, if you have the option to use the ethernet, you might check again in six months to see if any progress has been made.

If you have any driver disk that came with the device, we might examine the Windows driver for any clues.

---

### Post by jeremy31 on 2014-10-18
> **chili555 said:**
> Just as a tool for Jeremy and the searchers to use, you can check the modalias tables for any driver to see if it covers any device:So we check using the last four digits of the pci.id:```
modinfo ath9k | grep 003E
```In this case, it comes out blank. That means that ath9k does not yet cover the device in question.

As to whether it can or should drive your device, we turn to Google. As far as I can see, yours is the first seen in the universe! I see no mention of it anywhere. So far, I have no idea what the driver may be.

If you are intrepid and an experimenter, we could try amending the c code and compiling ath9k or, if you have the option to use the ethernet, you might check again in six months to see if any progress has been made.

If you have any driver disk that came with the device, we might examine the Windows driver for any clues.

I haven't found anything on that card and linux

ath10k might be the module that will be used when the card is supported

---

### Post by Noelson on 2014-10-18
Hello there.

Found this thread via Google. I also just bought an MSI GT72 2QE gaming notebook. As I am going to use this for work too, I went ahead and dual booted Ubuntu on it (it's on a Raid0 SSD array, which wasn't easy at all).

Everything is working fine except for the wifi as the OP suggests. I thought it would be the case, considering the card is really new but I hoped a workaround would be found...

In case anyone wants to try to help us, the exact model of the card is Qualcomm Killer N1525 Wireless-AC and the windows driver can be found here: [http://www.qca.qualcomm.com/resources/driverdownloads/](http://www.qca.qualcomm.com/resources/driverdownloads/)

---

### Post by chili555 on 2014-10-18
>  the exact model of the card is Qualcomm Killer N1525 Wireless-AC and the windows driver can be found here: [http://www.qca.qualcomm.com/resources/driverdownloads/](http://www.qca.qualcomm.com/resources/driverdownloads/)I have tried every tool at my disposal and have, so far, been unable to extract the Windows XP driver .inf file. If you have it on a Windows partition, it may be helpful. If you are able, paste it here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

It should be readable with any text editor.

---

### Post by Noelson on 2014-10-18
Hello there and thank you for your effort. I am unsure where that winXP .inf file would be, however I did manage to to find a .inf file on my Windows 8.1 x64 system that the driver is running.

Here goes:

[http://paste.ubuntu.com/8587525/](http://paste.ubuntu.com/8587525/)

EDIT1: I think the above is the inf file of the e2200 ethernet card after all...

EDIT2: After further investigation I think I've found the correct .inf file for the network adapter.

[http://paste.ubuntu.com/8587542/](http://paste.ubuntu.com/8587542/)

I'm not sure if this helps since it's WinXP you asked for but I hope it can be of some use!

---

### Post by jeremy31 on 2014-10-18
The one work around I can think of is to install an Intel 7260 AC card and wait for your Killer Atheros card to have Linux suport

---

### Post by chili555 on 2014-10-18
> After further investigation I think I've found the correct .inf file for the network adapter.Yes, indeed. We see the device listed:> %ATHR.DeviceDesc.2582%     = ATHR_DEV_OS63_988x_NFA344.ndi,     PCI\VEN_[COLOR="#FF0000"]168C[/COLOR]&DEV_[COLOR="#FF0000"]003E[/COLOR]&[COLOR="#FF0000"]SUBSYS_1525[/COLOR]1A56&REV_20 ;for Killer QCA2582However, we see nothing that would help us know what native driver to try to trick to drive the device.

ndiswrapper uses Win XP driver files which are apparently not available here.

I suggest you both file a bug report: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Noelson on 2014-10-19
Thanks for the try anyway...

Unfortunately I am completely overwhelmed by that bug reporting guide... I don't know where to start with that

---

### Post by chili555 on 2014-10-19
First, you will need to register with Launchpad. Second, since it is a hardware issue, file the bug against 'linux' here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

I suggest you title the bug something like: Atheros Qualcomm Killer N1525 Wireless-AC [168c:003e] not supported

Give the exact card detail in the body of the report: Qualcomm Atheros Device [168c:003e] (rev 20)
Subsystem: Bigfoot Networks, Inc. Device [1a56:1525]. Mention that you are running a fully updated Ubuntu 14.04. After filing the bug, you will undoubtedly be asked for additional details. Provide as requested. That's really all there is to it.

---

### Post by Noelson on 2014-10-19
Thank you once again, Chili.

---

### Post by Noelson on 2014-10-20
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

Here it is. I hope this is done correctly, its my first bug report on Launchpad :)

---

### Post by chili555 on 2014-10-20
> **Noelson said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

Here it is. I hope this is done correctly, its my first bug report on Launchpad :)Looks fine to me! It may take weeks or it may take years for a driver to appear. I suggest you have a backup plan at the ready; for example, ethernet or a cheap USB wireless.

---

### Post by Noelson on 2014-10-20
Thankfully I am dual booting Windows, so I can use that if there's no Ethernet around. The cheap usb wifi is not a bad idea though. I might actually look into the prices of those.

---

### Post by alexandre19 on 2014-10-20
Thanks everyone for your answers.

Thank you Noelson for the bug report, glad  to see I am not alone :)


Let's hope a driver will soon appear...

> **chili555 said:**
> Looks fine to me! It may take weeks or it may take years for a driver to appear. I suggest you have a backup plan at the ready; for example, ethernet or a cheap USB wireless.

Any suggestions for a usb wifi with linux compatibility ?
I have a D-link G122 IIRC that is also not recognized...

---

### Post by chili555 on 2014-10-20
There is a thread a week, or so it seems, here and also here: [http://askubuntu.com/questions](http://askubuntu.com/questions)

For example: [http://ubuntuforums.org/showthread.php?t=2233349](http://ubuntuforums.org/showthread.php?t=2233349)

Research carefully before you buy.

---

### Post by Noelson on 2014-10-20
Someone replied on the bug report, asking me to try the latest upstream kernel.

I did install it and tried but unfortunately it looks like that still has the same issue.

The journey continues!

---

### Post by R0blucci on 2014-11-05
Hi all, 
I found this thread and I had to join in because I got the same issue with my brand new MSI GS70 2QE gaming notebook.
I have managed to install Ubuntu 14.04.1 in dual boot along side windonw 8.1 with UEFI and secure boot enabled.
To switch between OS I got 2 ways, is either go to the BIOS and chnge the BBS HDD drive order form windows to ubuntu or I let the notebook boot normaly till GRUB comes up and choose from there if i want windows or ubuntu to boot, for that matter i use GRUB method.
Now when I am in Ubuntu every works fine but my wi-fi, if I use an RJ45 cable i do get internet though.

The issuing of the comand "ifconfig -a" is as follow:

eth0      Link encap:Ethernet  HWaddr 44:8a:5b:6e:ec:2c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::468a:5bff:fe6e:ec2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17066393 (17.0 MB)  TX bytes:1266194 (1.2 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:327314 (327.3 KB)  TX bytes:327314 (327.3 KB)

as you can see no wlan or wlan0 showing up.

The "lspci" command gives me this:

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation Device 13d8 (rev a1)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5249 (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Qualcomm Atheros Device 003e (rev 20)

therefore I cannot figure out how to get my wi-fi working, I installed the lastest kernel 3.18.0-031800rc3-generic and run apt-get update and upgrade but with no result.

Is sad that i cannot get wi-fi in ubuntu since i use it quite a lot in ssh, SFTP and the like since i do code in it.

Lastly if can be of any help when i boot ubuntu before the user screen password appears i do get this message:

2.065748 Bluetooth: Patch file not found ar3k/AthrBT_0x000002000.dfu
2.065781 Bluetooth: Loading path file failed

EDIT: Just to add anoter issue when in Ububtu the integrated GPU does not kick in and my lapton uses the dscrate GPU card (GTX 970M) instead, i can see that because whenever time the power bottom is red means that the notebook is using the Nvidia card.
Is not a big deal but If you guys now why i cannot use the HD 4600 integrated card would be nice, so i can save some battery power.

Thanks for the help, if you need more information just ask I will do anything i can to help you figure out the problem

---

### Post by jeremy31 on 2014-11-05
I guess you could file your own bug report
[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

The people dealing with bug reports would rather have each one seperate and they will decide if it is a duplicate

Edit: according to a post on the ath9k developers site, the ath10k developers are working on support for these cards

---

### Post by Noelson on 2014-11-06
Good to see there are more people interested in fixing this. You can add a comment on my bug report as well if you like.

Regarding your GPU issue, my GT72 has a button to switch from Nvidia to Intel HD GPU. Unfortunately, right now that is only possible in Windows through the SCM from MSI. Whenever I want to use the Intel GPU on Ubuntu, I log on windows, switch, then reboot into Ubuntu.

I have made a suggestion to MSI to include this GPU switching functionality in the BIOS, just so we can skip the booting into Windows part.

---

### Post by Scott_Gray on 2014-11-06
When you switch to the intel GPU is the nvidia gpu still active or is it totally disabled?  It would be nice if were still active so it could be used purely for cuda development.

---

### Post by Noelson on 2014-11-07
Considering there is no Optimus support in this system, I guess it completely gets turned off when you switch to Intel HD graphics. I'm guessing there is some kind of hardware switch that defines which one will be used at boot.

---

### Post by Scott_Gray on 2014-11-07
Well I have a GT72 sitting next to me here.  The first thing I did when getting it was to wipe windows and install ubuntu.  So I never played around with GPU selection functionality.   What's the best way to lobby MSI to convince them to add support to have either or both enabled in the bios?

I just ordered a cheapo usb wifi dongle to use while waiting for linux Atheros support.

---

### Post by Noelson on 2014-11-08
It shouldn't be difficult for them to add a bios switch for the GPUs. I'm not how having them both running would work but to choose between them is a really easy addition to them. I guess you'd have to call them or email them with a feature suggestion. I would never completely remove windows from this machine as it performs excellently in it, especially in games, for which it is designed in the first place. I do like however how I managed to add Ubuntu on the raid array, as I need it for work.

---

### Post by inventor2 on 2015-01-20
Noelson, are you completely sure your GS60 does not have Optimus support? From what I understand, all GS series laptops are optimus.
I have the GS60 066 with the GTX970m, with a fully working optimus setup.

```
Linux kernel [COLOR=#333333][FONT=Consolas]3.13
Bumblebee 3.2.1
nvidia-346 + 346-prime

[/FONT][/COLOR]sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:xorg-edgers/ppa


sudo apt-get install bumblebee-nvidia primus
sudo apt-get install nvidia-346 nvidia-346-uvm
```

As the rest, I am also waiting for my wifi driver support...

---

### Post by Noelson on 2015-01-24
> **inventor2 said:**
> Noelson, are you completely sure your GS60 does not have Optimus support? From what I understand, all GS series laptops are optimus.
I have the GS60 066 with the GTX970m, with a fully working optimus setup.

```
Linux kernel [COLOR=#333333][FONT=Consolas]3.13
Bumblebee 3.2.1
nvidia-346 + 346-prime

[/FONT][/COLOR]sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:xorg-edgers/ppa


sudo apt-get install bumblebee-nvidia primus
sudo apt-get install nvidia-346 nvidia-346-uvm
```

As the rest, I am also waiting for my wifi driver support...

I'm sorry buddy, I am on a GT72 not on a GS60.

---

### Post by MiLLeN on 2015-02-07
I am in your own way with one GS70 Q2E. Currently, I'm with one TP Link wifi usb until one driver gets up to linux.

Please, lest anyone forget this thread, if someone gets more info than let us know.

---

### Post by sandeep_ghosh on 2015-05-02
Any further update on this thread? I have run into a similar problem with MSI Z971 MB which has Qualcomm Killer N1525 Wireless-AC module. Not very happy not able to use wifi with Ubuntu. I end up spending more time on windows which I hate.

Thanks

---

### Post by chili555 on 2015-05-02
> **sandeep_ghosh said:**
> Any further update on this thread? I have run into a similar problem with MSI Z971 MB which has Qualcomm Killer N1525 Wireless-AC module. Not very happy not able to use wifi with Ubuntu. I end up spending more time on windows which I hate.

Thanks*YES!!!* I have upgraded my laptop to Ubuntu 15.04 and am running a mainline kernel version 4.0: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-vivid/) I am delighted to report that the module ath10k_pci covers the subject device:```
chili@T410:~$ modinfo ath10k_pci
filename:       /lib/modules/4.0.1-040001-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     837C8B320227AB6A933D58D
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]003E[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core
intree:         Y
vermagic:       4.0.1-040001-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        58:EF:1B:E8:6F:69:F6:97:25:C1:20:58:C9:00:5C:68:4C:A0:4C:FB
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```As you can see, the driver requires firmware. My default 15.04 install includes most of it:```
/lib/firmware/ath10k/QCA988X/hw2.0/board.bin
/lib/firmware/ath10k/QCA988X/hw2.0/firmware.bin
/lib/firmware/ath10k/QCA988X/hw2.0/otp.bin

```I will look forward to a report from one of you posters as to whether the device finally works as expected.

EDIT: If firmware is an issue, according to *dmesg*, check here: [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware) Note that the driver is quite specific about where it expects to see the files.

---

### Post by antoine-dacrem on 2015-05-13
I've followed the developpements on this thread about the N1525.

Like chili555, i'm running a 4.0 mainline Kernel with Ubuntu 15.04 (on a MSI GS60 2QE) and the modinfo command gives me the same results. But the card is still undetected. 
I've checked the ath10k folder and compared with the file on github and i've found that the folder labelled QCA6174 is missing.
According to this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184) comment #30 and this site [https://wikidevi.com/wiki/Qualcomm_Atheros_Killer_Wireless-AC_1525](https://wikidevi.com/wiki/Qualcomm_Atheros_Killer_Wireless-AC_1525) the label QCA6174 might refer to our module.

How could we add missing files and test them ?

---

### Post by chili555 on 2015-05-13
> **antoine-dacrem said:**
> How could we add missing files and test them ?What does the system report that it's missing? There are several versions out there.```
dmesg | grep ath
```

Reference: [http://askubuntu.com/questions/621345/lenovo-z70-wifi-with-14-04-2-and-kernel-3-16-not-working/621491#621491](http://askubuntu.com/questions/621345/lenovo-z70-wifi-with-14-04-2-and-kernel-3-16-not-working/621491#621491)

---

### Post by misiunt on 2015-05-31
> **chili555 said:**
> What does the system report that it's missing? There are several versions out there.```
dmesg | grep ath
```

Reference: [http://askubuntu.com/questions/621345/lenovo-z70-wifi-with-14-04-2-and-kernel-3-16-not-working/621491#621491](http://askubuntu.com/questions/621345/lenovo-z70-wifi-with-14-04-2-and-kernel-3-16-not-working/621491#621491)

I followed the instructions on my Acer Aspire V 15 Nitro VN7-571G-5050 but dmesg reports the following error:
ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2.

lspci describes my  wi-fi with :
03:00.0 Network controller: Qualcomm Atheros Device 003e (rev 20)
        Subsystem: Foxconn International, Inc. Device e08e
        Flags: bus master, fast devsel, latency 0, IRQ 51
        Memory at c4000000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=8/8 Maskable+ 64bit-
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [148] Virtual Channel
        Capabilities: [168] Device Serial Number 00-00-00-00-00-00-00-00
        Capabilities: [178] Latency Tolerance Reporting
        Capabilities: [180] L1 PM Substates
        Kernel driver in use: ath10k_pci



I currently use a usb wi-fi stick but the performance is very poor, so I hope there will be soon a solution for the Qualcomm Atheros Device.

---

### Post by chili555 on 2015-05-31
Please see the referenced thread where I said: > It looks like until we can find or bypass cal-pci-0000:03:00.0.bin, we are stuck. I will keep searching and suggest you do also. The various bug reports suggest that the fix is close. Here, for example: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

---

### Post by misiunt on 2015-06-06
> **chili555 said:**
> Please see the referenced thread where I said: The various bug reports suggest that the fix is close. Here, for example: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

the solution described in the bug report (#150) works perfectly for me. Wi-fi performs well and stable and the 4.1.0-rc6-wl-ath
 kernel doesn't cause any issues , so I hope , this solution will be merged to the mainstream kernel very soon.

---

### Post by santiago87 on 2015-07-02
I am glad I found this thread, I have had the same problems in ubuntu 15.04.

I have been fighting for days and googling everywhere how to install the wifi drivers for my Killer Wireless-n/a/ac 1525 Wireless Network Adapter.
Mine is a Schenker A505 laptop.

So, if I understand correctly the discussion here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

Then the ath10k drivers will be soon merged into the mainline kernel, right? 

For the moment, the correct solution is what is posted in #150?

I will try it today or tomorrow and report if I have any success.

---

