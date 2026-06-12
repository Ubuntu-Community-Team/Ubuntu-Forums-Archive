---
title: "Help! Wireless on Gateway M-6750 Laptop"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by indrewjones0870 on 2010-02-17
Hello, I own a Gateway m-6750 laptop. I recently dual booted vista 32 bit and Ubuntu 9.1 on my P.C. Everything seems to be working fine except on the top bar, where your network information is. When ever i right click, it only gives me an option  to enable networking. How can i get the enable wireless to be there? And if not, is there any way to get my wireless internet working. I can connect to the internet fine with an Ethernet cable, but no wireless.I have tried several things with no luck. Please, i cant stand vista.
Thanks

---

### Post by gordintoronto on 2010-02-17
If you right-click on the icon and select "edit connections," is there a wireless tab?

---

### Post by lkraemer on 2010-02-17
First you need to find out more about the Hardware installed in your 
Gateway Laptop.

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lspci -nn | grep Marvell
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig
tail /var/log/messages

```
Post the results.

Here is a Guide I wrote on my Gateway:
[http://ubuntuforums.org/showthread.php?t=650637&highlight=Gateway](http://ubuntuforums.org/showthread.php?t=650637&highlight=Gateway)

lk

---

### Post by indrewjones0870 on 2010-02-17
indrewjones@indrewjones-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
indrewjones@indrewjones-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c525 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
indrewjones@indrewjones-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f600ffff memory:f4000000-f400ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e6:e5:32
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.10 latency=0 multicast=yes
       resources: irq:29 ioport:4000(size=256) memory:fa200000-fa200fff memory:c0000000-c001ffff(prefetchable)
indrewjones@indrewjones-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_idt      59844  1 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
uinput                  7836  2 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56500  0 
serio_raw               5280  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
usb_storage            52576  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
indrewjones@indrewjones-laptop:~$ ndiswrapper -l
indrewjones@indrewjones-laptop:~$ cat /etc/modprobe.d/blacklist.conf
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
indrewjones@indrewjones-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

indrewjones@indrewjones-laptop:~$

---

### Post by indrewjones0870 on 2010-02-17
> **gordintoronto said:**
> If you right-click on the icon and select "edit connections," is there a wireless tab?

Yes, the wireless tab is still there. But when i right click, theres no enable wireless, just enable networking.

---

### Post by lkraemer on 2010-02-17
I don't see any references to any Wifi Hardware.

If you boot Windows, and turn on the Wifi, with Function F2 does
it work properly?  Try to Toggle it OFF, then back ON in Windows
to verify that the Keystrokes are in fact FUNCTION F2.  If it is,
leave it ENABLED, and boot Ubuntu.

You can also cruise around in Windows and see if you can find any
reference to the Wifi Hardware and Drivers that are loaded.  
ie. Control Panel -> Hardware

Then run the lshw -C network and iwconfig again.

There should be a reference to Wifi somewhere, if it is enabled via hardware.

lk

---

### Post by indrewjones0870 on 2010-02-18
The manual wifi switch, and the function f2 both work in windows, but no luck in ubuntu.

---

### Post by lkraemer on 2010-02-18
Try the following command to determine the PCI ID of your wireless
device under linux:
```

lspci -nn

```
Then search for that PCI ID with Google.

The only thing I can now suggest is for you to download LiveCD's for,
Sidux, PCLinuxOS, or Fedora and try one of them to see what hardware
is detected.  You might also want to try the latest release candidate
for Ubuntu 10.04 Alpha 2 as first choice.  I'd bet Sidux or PCLinuxOS
locates the hardware.  If any of these gets the Wifi working from
LiveCD, then run the above commands to see what was detected.

[http://distrowatch.com](http://distrowatch.com) will help you find these distro's.

lk

---

### Post by bkratz on 2010-02-18
Found this if it is any help, it speaks about the Gateway "M" series and missing wireless.

[http://ubuntuforums.org/archive/index.php/t-1236637.html](http://ubuntuforums.org/archive/index.php/t-1236637.html)

---

### Post by indrewjones0870 on 2010-02-18
> **bkratz said:**
> Found this if it is any help, it speaks about the Gateway "M" series and missing wireless.

[http://ubuntuforums.org/archive/index.php/t-1236637.html](http://ubuntuforums.org/archive/index.php/t-1236637.html)

I do the first step, everything seems fine, at the end of the download this appears.E: Sub-process /usr/bin/dpkg returned an error code (1)

i download the setup fine and copy it into the tmp folder.
i unzip the file
i downloaded cabextract
Im fine until step 9, nothing works after that.
where can i get a .inf driver? if i can get one, i think i can install it.
thanks

---

### Post by lkraemer on 2010-02-18
So, if you open a Terminal Window and type:
```

cd .wi

```
and then the TAB Key you should be at the .wine subdirectory.
Does this work?  If so keep going down until you find the
NETGEAR subdirectory.  ie. cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/
Then do a ls to list the files.

Typically, after wine is installed you run winecfg from a terminal which
creates the .wine subdirectory, and allows you to set up more details.

The remaining steps should work for you.  What is your exact error?
Your first line speaks of an error message from the initial download
of ndiswrapper.  Is this correct?  Why not open Synaptic and search
for ndisgtk.  If it is installed there should be a GREEN Box to the left
that is Highlighted.
  
lk

---

### Post by lkraemer on 2010-02-18
Now you won't have to worry about all the Wine install and extracting.

Here are ALL the netmw*.sys and NetMW14x.inf files that you were looking for
from the WN511T Version 3.0 Software.

I had to locate the zip, download it and extract, boot VirtualBox, make a
snapshot of XP, install the drivers, copy them to Ubuntu, and sort out just
files you needed.  Then RESTORE my XP to before the driver install.

You should be good to go, as I don't think you will need any of the
other files.  I'll save them for a bit just in case.

You should be able to start at item 10, just be sure to change your 
directory to the subdirectory where you copy and extract the files.

If you should need additional files PM me with your Email address.

lk

You're on your way to having a GATEWAY into the UNIVERSE........
INSTEAD of a Window into the Virus Pit.......

---

### Post by indrewjones0870 on 2010-02-19
WOW! Thanks SOOO much! ill try this and get back to you, thanks a ton!

---

### Post by indrewjones0870 on 2010-02-20
OH, MY, GOD!. It still wont work! I have no idea what is going wrong,  thanks a ton for the files though. im sure ill find a way to get it  working. Do you think if i downgraded to 8.10 or something that it might  work? 
thanks for your time

---

### Post by lkraemer on 2010-02-20
Well, imagine being on this end, and not knowing what you typed, 
what response you got from each command, and not being able to
see the display or touch the keyboard..........A little helpful
information goes a long way, versus it still doesn't work.....

Did you install 32 Bit or 64 Bit Ubuntu, and what Version?
I don't think ndiswrapper and the driver works with 64 Bit installs.
You may need the 64 Bit Driver from Gateway.
[http://support.gateway.com/support/drivers/getFile.asp?id=21850&dscr=Marvell%20Wireless%20LAN%20Driver&uid=260834268](http://support.gateway.com/support/drivers/getFile.asp?id=21850&dscr=Marvell%20Wireless%20LAN%20Driver&uid=260834268)


Run the commands I posted in Posting #3, and post the output here.
Also, Please post the output of:
```

lspci -nn | grep Marvell

```

You should have copied the zip to a folder named maybe /home/user/WN511T
and then extracted the files.  Then open a Terminal window and do:
```

cd WN511T
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```

To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```

Did you get any errors in the five steps?

You should have seen something like this:
```

$sudo ndiswrapper -i NetMW14x.inf
installing netmw14x &#8230;
$sudo ndiswrapper -a 11ab:2a08 netmw14x
WARNING: Driver &#8216;netmw14x&#8217; will be used for &#8216;11AB:2A08&#8242;
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08
$sudo ndiswrapper -l
netmw14x : driver installed
device (11AB:2A08) present

```

It is possible that your ID could be different than the one you actually used.
I found them listed somewhere a few days back, but haven't located them again.

If you got an error, you should see something like this:
```

$ sudo ndiswrapper -i NetMW14x.inf
driver netmw14x is already installed
$ sudo ndiswrapper -a 11ab:2a08 netmw14x
driver 'netmw14x' is not installed (properly)!
$ sudo ndiswrapper -l
netmw14x : invalid driver!

```

If this is what you saw try copying NetMW145.sys, and then paste and rename it to NetMW146.sys
The problem is that the .inf file has a section that calls a driver called NetMW146, but on
the pack only 143 and 145 are included... Windows ignores this and goes directly to the driver
that works, but ndiswrapper don't, it expects it to be there.  Your mileage may vary.


When you run the command iwconfig this will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.
assuming everything was setup correctly, and was detected properly.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below. Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi. Insert your
essid (UPPERCASE or lowercase specific)
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```
You should be able to surf.


EXTRA INFO!
[http://forums.driverguide.com/showthread.php?t=37046&page=2&vforum=0c2329d12](http://forums.driverguide.com/showthread.php?t=37046&page=2&vforum=0c2329d12)

MARVEL TOP DOG CARD RUNNING UNDER XP.

Hope you haven't given up all hope on getting the Marvell TopDog 802.11n
mini PCI wireless adapter in the Gateway MT6458 Laptop to work correctly.

MARVELL TOPDOG INSTALL INSTRUCTIONS:
1. Open this link in a new tab of your web browser: [http://kbserver.netgear.com/release_notes/d103154.asp](http://kbserver.netgear.com/release_notes/d103154.asp).

2. Download the 'WN311T Driver and Utility Version 4.1' driver package to your 'desktop' or 'software' folder
of your choice.

3. Double-click on the 'wn311t_setup_4_1.exe' install file to install the driver package. (***IF WINDOWS
TELLS YOU THE DRIVERS DON'T HAVE SIGNATURES AND ASKS IF YOU REALLY WANT TO INSTALL THEM, TELL THE OS 'YES'!)

4. After install, please reboot your laptop.

5. Navigate down into the Netgear folder in the Programs folder on the root of hard drive and you should be able
to find a file in there called 'NetMW14x.inf'. Right click on this file and choose 'Install'.

6. Now go into the 'Device Manager' and double-click on the '?' adapter with the yellow question mark showing the
hardware you've been pulling your hair out over. Choose to update the driver and take total control by demanding
to choose the driver yourself Choose 'NetGear' for the maufacturer and 'WNT311 Wireless PCI adapter' as the device.
Once again, XP will ask if it's OK to install the driver because it doesn't have a signature; tell Windows 'yes'.

7.Your wireless connection should work perfectly. You should have a good and solid wireless connection through the
TopDog mini PCI 802.11n adapter.


lk

---

