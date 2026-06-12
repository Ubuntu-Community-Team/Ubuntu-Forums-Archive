---
title: "No wired or wireless network after upgrade to 12.04LTS from 10.04LTS"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by Old_Brewer on 2014-02-03
Today I upgraded to 12.04LTS from 10.04LTS.  Wired and wireless was working with 10.04.  I had to install ndiswrapper to get the wireless working on 10.04LTS.  I have not installed/reinstalled ndiswrapper.
Here is some info, I have to retype so output is abbreviated:
lshw -C network
Network:0 UNCLAIMED
     description: Ethernet Controller
     Product: BCM4401-B0 100Base-TX
Network:1 UNCLAIMED
     Description: Network Controller
     product; BCM4318 [AirForce One 54g] 802.11 Wireless LAN Controller

lsmod |grep ndiswrapper
FATAL Module ndiswrapper not found

nddiswrapper -l
b44win : driver installed
      device 14e4:170c present alternate driver b44
bcmwl : driver installed
      device 14e4:4318 present alternate driver ssb

I read in the sticky that ndiswrapper might not be needed, so I have not tried to install/reinstall.  Last time with 10.04 I went back and forth with a live bootable CD to get the wired connection.  I'll do whatever it takes, I definitely need help!  Also I used Wicd, but have not tried that, yet.
If someone helps me I can take a picture of the output of commands & post them.
Thanks in advance

PS  I just tried copy & paste with a usb stick.  Here is the output:

root@joebelle-laptop:~# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
b44win : driver installed
    device (14E4:170C) present (alternate driver: b44)
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
root@joebelle-laptop:~# 
root@joebelle-laptop:~# 
root@joebelle-laptop:~# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
b44win : driver installed
    device (14E4:170C) present (alternate driver: b44)
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
root@joebelle-laptop:~# 
root@joebelle-laptop:~# lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:dfbfc000-dfbfdfff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:dfbfe000-dfbfffff
root@joebelle-laptop:~# 
root@joebelle-laptop:~# 
root@joebelle-laptop:~# lsmod |grep ndis
root@joebelle-laptop:~# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
root@joebelle-laptop:~# 
root@joebelle-laptop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by chili555 on 2014-02-03
We have a very technical term here at HQ: Holee Molee!!! You have a little mess there,don't you?? Please hook up the ethernet and open a terminal and do:```
sudo modprobe b44
```Does your ethernet come to life? If so, we'll undo a blacklist and make it persistent. To find the blacklist, we need to see:```
ls /etc/modprobe.d
```You needn't take a picture; just tell us what you see that has something to do with bcmxx or brcmxx or some such.

Then we'll whip the wireless.

We also need to see:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/bluez
```

---

### Post by Old_Brewer on 2014-02-03
Thanks for helping me. 
modprobe b44 worked

Here is the output you requested:

root@joebelle-laptop:~# modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@joebelle-laptop:~# 
root@joebelle-laptop:~# 
root@joebelle-laptop:~# ls /etc/modprobe.d
alsa-base.conf          blacklist.conf              blacklist-modem.orig         blacklist-watchdog.conf  ndiswrapper
alsa-base.orig          blacklist.conf.orig         blacklist.orig               bluez                    ndiswrapper.conf
blacklist               blacklist-firewire.conf     blacklist-oss.conf           bluez.orig               nvidia-kernel-nkc.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-oss.dpkg-bak       dkms.conf                oss-compat.conf
blacklist-bcm43.conf    blacklist-modem.conf        blacklist-rare-network.conf  libpisock9.conf          vmwgfx-fbdev.conf
root@joebelle-laptop:~# 
root@joebelle-laptop:~# 
root@joebelle-laptop:~# cat /etc/modprobe.d/blacklist
blacklist bcm43xx\nblacklist wl
root@joebelle-laptop:~# 
root@joebelle-laptop:~# cat /etc/modprobe.d/ndiswrapper
alias pci:v000014E4d0000170Csv0000017Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000188sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000189sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000018Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000196sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000198sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000199sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Esd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Fsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001A2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001A4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001ABsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001AFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001B5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001BDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001C9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CAsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CBsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D7sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D8sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001E5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001E9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EEsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F1sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F3sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F6sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001FCsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001FDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000008B0sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001004sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001014sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001016sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001019sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000123Bsd000010CFbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003095sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003098sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003099sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000082C4sd00001033bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001363sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001364sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001365sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001374sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001375sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001376sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001377sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv0000135Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001360sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001361sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001362sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001370sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001371sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001372sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001373sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001355sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001356sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001357sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001358sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001359sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv0000135Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000000E7sd00000E11bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F4sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F8sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FAsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FBsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012F9sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012FCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001366sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001367sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001368sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001369sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000001sd00001179bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000159sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000017Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000188sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000189sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000018Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000196sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000198sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000199sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Esd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Fsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001A2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001A4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001ABsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001AFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001B5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001BDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001C9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CAsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CBsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D7sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D8sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000008B0sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000008BCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000585Csd00001462bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000590Csd00001462bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000080A8sd00001043bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00008401sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv*sd*bc*sc*i* ndiswrapper
root@joebelle-laptop:~# 
root@joebelle-laptop:~# 
root@joebelle-laptop:~# cat /etc/modprobe.d/bluez
# BlueZ modules

# These are all in the default aliases file.  Uncomment them only
# if for some reason you need them.
#alias net-pf-31 bluetooth
#alias bt-proto-0 l2cap
#alias bt-proto-2 sco
#alias bt-proto-3 rfcomm
#alias bt-proto-4 bnep
#alias bt-proto-5 cmtp
#alias tty-ldisc-15 hci_uart

# HIDP is not yet in the standard aliases file.
alias bt-proto-6 hidp

# Uncomment this if you wish to use VHCI
# Unfortunately no minor has been assigned.
# alias char-major-10-250 hci_vhci
root@joebelle-laptop:~# 

Looks like we need to blacklist.
Thanks for the help & anticipated instructions.

---

### Post by chili555 on 2014-02-03
Let's start here:```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```Find where it says:```
blacklist b44
```Comment it out like this:```
**#**blacklist b44
```Proofread, save and close gedit.

This file is useless; we'll eliminate it:```
sudo rm /etc/modprobe.d/blacklist 
```I'm not sure what this one does, but let's clean it up:```
sudo mv  /etc/modprobe.d/bluez   /etc/modprobe.d/bluez.conf
```Since the module doesn't even load correctly, I'm fairly sure we're going to get rid of ndiswrapper, so until we decide for sure, let's leave /etc/modprobe.d/ndiswrapper alone for now.

Let's see if we can coax the wireless to life. Please do:```
sudo modprobe wl
```Any errors or warnings? If not, check:```
iwconfig
```Do you have a wireless interface, ideally eth1? Does it scan?```
sudo iwlist eth1 scan
```If it scans, it should connect after you detach the ethernet.

We'll do a little clean-up if all goes as I expect, and you'll be all set!

---

### Post by Old_Brewer on 2014-02-03
I tried iwlist eth1 scan, iwlist eth scan, and iwlist lo scan.  The results were all the same, Interface dosen't support scanning. 

Everything you said up to that point worked, with no errors.

---

### Post by chili555 on 2014-02-03
Let's see:```
rfkill list all
iwconfig
```We're getting really close!

---

### Post by Old_Brewer on 2014-02-03
I'm back from supper.  I can reply a little faster now that I have been been fed, along with the chickens & cats :)
Here is the output:
root@joebelle-laptop:/etc/modprobe.d# rfkill list all
root@joebelle-laptop:/etc/modprobe.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@joebelle-laptop:/etc/modprobe.d#

---

### Post by chili555 on 2014-02-03
Let's try again:```
sudo modprobe wl
dmesg | grep -e wl -e eth1
iwconfig
```Please post any errors, messages, etc.

---

### Post by Old_Brewer on 2014-02-03
root@joebelle-laptop:/etc/modprobe.d# rfkill list all
root@joebelle-laptop:/etc/modprobe.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@joebelle-laptop:/etc/modprobe.d#

---

### Post by chili555 on 2014-02-03
> **Old_Brewer said:**
> root@joebelle-laptop:/etc/modprobe.d# rfkill list all
root@joebelle-laptop:/etc/modprobe.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@joebelle-laptop:/etc/modprobe.d#Please check my reply again.

---

### Post by Old_Brewer on 2014-02-03
joebelle@joebelle-laptop:~$ sudo modprobe wl
[sudo] password for joebelle: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
joebelle@joebelle-laptop:~$ dmesg | grep -e wl -e eth1
[11238.153450] wl: module license 'MIXED/Proprietary' taints kernel.
joebelle@joebelle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

joebelle@joebelle-laptop:~$ 

Sorry about the last post.  I think I pasted the wrong info.

---

### Post by chili555 on 2014-02-03
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Didn't we remove that file?> This file is useless; we'll eliminate it:
Code:

sudo rm /etc/modprobe.d/blacklist

Something is very awry here. Let's also see:```
cat /etc/modprobe.d/blacklist.conf | tail -n10
lsmod
```

---

### Post by Old_Brewer on 2014-02-03
I remember #ing out something before.  Here is the output you requested and a little extra.  Thanks for staying with me on this problem.

joebelle@joebelle-laptop:/$ su -
Password: 
root@joebelle-laptop:~# cd /
root@joebelle-laptop:/# pwd
/
root@joebelle-laptop:/# 
root@joebelle-laptop:/# cd /etc/modprobe.d
root@joebelle-laptop:/etc/modprobe.d# ls -l
total 96
-rw-r--r-- 1 root root 2507 Feb 27  2013 alsa-base.conf
-rw-r--r-- 1 root root 2180 Apr 14  2011 alsa-base.orig
-rw-r--r-- 1 root root   32 Apr 18  2011 blacklist
-rw-r--r-- 1 root root  325 Apr 13  2010 blacklist-ath_pci.conf
-rw-r--r-- 1 root root  227 Feb  3 17:58 blacklist-bcm43.conf
-rw-r--r-- 1 root root  226 Feb  3 17:56 blacklist-bcm43.conf.orig
-rw-r--r-- 1 root root 1827 Apr 18  2011 blacklist.conf
-rw-r--r-- 1 root root 1585 Apr 18  2011 blacklist.conf.orig
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Jan 28  2010 blacklist-modem.conf
-rw-r--r-- 1 root root  156 Apr 14  2011 blacklist-modem.orig
-rw-r--r-- 1 root root   37 Apr 18  2011 blacklist.orig
lrwxrwxrwx 1 root root   41 Feb  3 12:45 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
lrwxrwxrwx 1 root root   41 Apr 29  2008 blacklist-oss.dpkg-bak -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Apr 13  2010 blacklist-watchdog.conf
-rw-r--r-- 1 root root  484 Oct  3  2007 bluez.orig
-rw-r--r-- 1 root root  127 Jan 28 04:13 dkms.conf
-rw-r--r-- 1 root root   16 Jan  6  2010 libpisock9.conf
-rw-r--r-- 1 root root 8016 Apr 18  2011 ndiswrapper
-rw-r--r-- 1 root root   24 Apr 14  2011 ndiswrapper.conf
-rw-r--r-- 1 root root  115 Mar  5  2009 nvidia-kernel-nkc.conf
-rw-r--r-- 1 root root  356 Feb  3 13:12 oss-compat.conf
-rw-r--r-- 1 root root   30 May 18  2012 vmwgfx-fbdev.conf
root@joebelle-laptop:/etc/modprobe.d# cat blacklist
blacklist bcm43xx\nblacklist wl
root@joebelle-laptop:/etc/modprobe.d# 
root@joebelle-laptop:/etc/modprobe.d# rm blacklist
root@joebelle-laptop:/etc/modprobe.d# 
root@joebelle-laptop:/etc/modprobe.d# cat blacklist.conf |tail -n10
# really needed.
blacklist amd76x_edac


# Also, according to Ubuntu ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) there are a bunch of drivers which should not be running. They are:
blacklist b44
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
root@joebelle-laptop:/etc/modprobe.d#

---

### Post by chili555 on 2014-02-03
Please get a temporary wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge ndiswrapper*
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo apt-get install firmware-b43-installer
gksudo gedit /etc/modprobe.d/blacklist.conf 
```Remove all of these lines:```
# Also, according to Ubuntu (https://help.ubuntu.com/community/Wi...er/Ndiswrapper) there are a bunch of drivers which should not be running. They are:
blacklist b44
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```Proofread, save and close gedit.```
sudo -i
echo b43 >> /etc/modules
echo b44 >> /etc/modules
exit
```Reboot and let us hear your report.

---

### Post by Old_Brewer on 2014-02-03
Thank you very much!
All is working. First the wired, then the wireless, all I had to do was put in the security key.
Thanks for staying with me.  I really appreciate the help.
Consider the problem solved. Do you close the thread, or do I?

---

### Post by chili555 on 2014-02-03
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

