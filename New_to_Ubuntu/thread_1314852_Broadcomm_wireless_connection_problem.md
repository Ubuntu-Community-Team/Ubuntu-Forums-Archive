---
title: "Broadcomm wireless connection problem"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by pilchbo on 2009-11-04
I've looked at threads for three days and although I see similar problems, none of the solutions works.  I've got a Broadcomm 4306.  I think it's installed correctly because when I click the Network icon, I see a Wireless Networks heading--but no networks.  When I followed instructions to use ndiswrapper, I wasn't sure I had the right driver files and the option of Wireless Networks disappeared so I went back to using the Ubuntu supplied driver.  I have added my wireless network in several different ways, but it is never seen by ubuntu.  I'm using 9.10.  Here are some logs:

ken@ken-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

When I looked at Hardware Drivers, it says No proprietary drivers are in use on this system at the top.  In the next small window down it says Broadcom B43 wireless driver.  Then in the big window it says Broadcom B43 wireless driver, then Testedby the Ubuntu developers, then License:  Free.  Under that it has a definition for fwcutter.  I have clicked the Activate button several times.  Also beside the Activate button it states A different version of this driver is in use.

I'm totally new to Linux in general.

---

### Post by Michael.Palone on 2009-11-04
I've had the same issue every time I've updated Ubuntu. Comforting, huh?
Okay. You've installed the bcm-fwcutter package, I'm assuming?
Try installing the bcmwl-kernel-source package and activating the drivers again.

---

### Post by lkraemer on 2009-11-04
pilchbo,
I just booted Ubuntu 9.10 Livecd with my Wifi PCMCIA card (Broadcom) and got it working in a few minutes.
 
Pick one method and stick with it.  Don't mix-n-match.

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.  ( I used #2 above)

It appears that you started with ndiswrapper, and if you change methods,
you will have to remove the previous modules and un-install or reverse
all the changes you have made thus far.  So, it is a good idea to keep
track of what method you used so you have a list of the commands.
(You can open a terminal window and type the following to get a list
of the terminal commands)
```

history > mycmds.txt

```

For #2 above you just have to download the Firmware, or have your
computer connected to the internet via ethernet when you enable
the Hardware Drivers.  The Firmware is installed at /lib/firmware
as folders /b43 and /b43legacy.  Open a Terminal window and do the
following commands (cut and paste one at a time):
```

cd /
cd /lib
cd /firmware
ls -alt

```
(You are looking for any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the
Hardware Drivers with a LAN connection there should have been folders
created and files inserted for the Restricted Drivers to work.)

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 and above use:
                                  cat /etc/modprobe.d/blacklist.conf
iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

It will be your decision on what to use.

For #2 above:
If you just need the Broadcom firmware for b43xx it can be found on
the internet.  ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)
Extract the files, copy them to /lib/firmware and then enable
the Hardware Drivers.

You can search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue.

#2 ONLY - (The following is NOT for Ubuntu 9.10 as it uses b43.)
If lsmod shows module b43, ndiswrapper, and others installed you
will need to blacklist them, since you are going to be using b43xx.
Be sure to insert a # at the beginning of the line if any of the
existing driver modules are blacklisted, and you will be using them.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb    #DO NOT BLACKLIST

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist, or the updated location
for 9.04 & 9.10.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
And wait a few minutes......

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below, if you want to do it manually:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

Post the output of iwconfig above.

#3 ONLY - (The following is for Ubuntu 9.10 as it uses b43.)
If you just need the Broadcom firmware for b43 it can be found on
the internet.  ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)
Extract the files, copy them to /lib/firmware and then enable
the Hardware Drivers.

If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to remove them and blacklist them, since you are going to
be using b43.  Be sure to insert a # at the beginning of the line if
any of the existing driver modules are blacklisted, and you will be
using them. You may have to remove the following depending on what lsmod
shows:  (DON'T BLACKLIST SSB)
```

modprobe -r b44
modprobe -r b43legacy

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist, or the updated location
for 9.04 & 9.10

lk

---

### Post by linux6994 on 2009-11-04
Try installing b43-fwcutter, look at the attachment.

sudo apt-get install b43-fwcutter

---

### Post by lkraemer on 2009-11-05
If you are still having problems:
[http://ubuntuforums.org/showthread.php?p=8248919#post8248919](http://ubuntuforums.org/showthread.php?p=8248919#post8248919)
Posting #8 will help you finish up.

lk

---

### Post by pilchbo on 2009-11-05
I guess I didn't write well.  I didn't start with ndiswrapper.  I installed the B43 driver using the Hardware Driver app--at least I think it is installed.  Then, following a thread with responses from anewguy, I used ndiswrapper and blacklisted the Broadcomm stuff, but that didn't work so I backtracked and undid it.

I'll give the rest a try in a little bit.

---

### Post by lkraemer on 2009-11-05
Well, I know for a fact that if you extract the firmware to
/lib/firmware/b43 and /lib/firmware/b43legacy and then ENABLE
the Restricted Hardware Drivers, you will be up and running
in a few minutes with Ubuntu 9.10 because I've done it from
LiveCD.

That assumes a Fresh install with the proper drivers loaded.
In your case you may have to blacklist some drivers, or remove
them from the blacklist file if you will be using them.

lk

---

### Post by sadaruwan12 on 2009-11-05
Try using the ndsiwrapper it works and once you install the drivers you've to reboot the network service and load the new drivers. ndsiwrapper worked for me who had the same kind of a problem.

---

### Post by lkraemer on 2009-11-05
RE-READ my postings as I have corrected them for 9.10.

I have booted from Floppy, and finished booting from LiveCD 9.10
and VERIFIED that it all works using Broadcom Firmware and b43
module.

REF:
[http://ubuntuforums.org/showthread.php?t=1314327&page=2](http://ubuntuforums.org/showthread.php?t=1314327&page=2)

lk

---

### Post by pilchbo on 2009-11-06
Haven't done anything yet.  I was looking at other linux OS's because I had two work out of the box a week ago but I didn't like them.  That was Puppy and Knoppix.  Now that Windows is gone from the hard drive, however, they don't work with the wireless either.

In the process I have installed a different linux on my laptop.  Therefore I will have to put a clean installl of Ubuntu on, which may be for the best.  However, I am looking at Xubuntu in a few minutes because my laptop has only 256Mb of RAM.  Ubuntu seemed to run fine and was pretty quick, but if Xubuntu runs better, it's probably a better flavor of Ubuntu for me.

I imagine the problem will be the same, Xubuntu or Ubuntu.  I am a REAL beginner with linux, although I'm pretty good with Windows and Visual Basic.  I don't even understand the terms you're using most of the time.  I figured out ipwconfig means Internet Protocol Wireless Configuration, but I could really use a dictionary of commands.  

Give me a day.  When I come back, I will need to know how to do the stuff above, step by painfully obvious step (to you guys).  ;)

Ken

---

### Post by pilchbo on 2009-11-06
> **lkraemer said:**
> 
If you just need the Broadcom firmware for b43xx it can be found on
the internet.  ie. [www.omattos.com/broadcom]("http://www.omattos.com/broadcom")
Extract the files, copy them to /lib/firmware and then enable
the Hardware Drivers.

lk

I am not allowed to unzip or paste anything into the firmware folder.  I am not asked for my password or anything.  The unzipping attempt tells me I don't have permission to do so.  When I unzipped the download in place and then attempted to copy it in, the Paste command was grayed out.  BTW, the unzipping produced a folder called b43.  I assume I want to get that entire folder in /lib/firmware?

When I shut down a LiveCD session of Ubuntu I was able to read a complete web address for getting the b43 driver.  The link above is better, but the wireless.kernel.org site helped me understand what you folks are talking about.

Ken

---

### Post by lkraemer on 2009-11-06
You should be able to extract the files just by double left clicking
on the zip file on your desktop.  Then tag each one and extract.
To copy them use the sudo command as follows in a Terminal Window:
```

sudo cp -r /Desktop/b43* /lib/firmware

```
That should do it.  Then to verify that the folders exist you can do this:
```

cd /
cd /lib/firmware/b43
ls -alt

```
That will move to the b43 folder and display all files there.

lk

---

### Post by lkraemer on 2009-11-06
For smaller Distro's you might want to look at:
(iIn order of my preference)

1. Crunchbang
2. Tinyme Acorn
3. PCLinuxOS MiniME 2009.1 (or the latest version)
4. Damn Small Linux
5. Puppy
6. Slitaz
7. Tinycore

lk

---

### Post by pilchbo on 2009-11-06
OK, so far so good.  I re-installed Ubuntu.  A little slower than Xubuntu, but not bad.  I downloaded the driver files from omattos.  I extracted--Firefox automatically put them in the downloads folder.  I modified your terminal commands and managed to copy them to the /lib/firmware directory.  Still don't see why I can't paste them directly--I tried because I'm stubborn--but what the heck.  

Now how do I enable them?  I started the Hardware Drivers app and I see nothing except a message **No proprietary drivers are in use on this system.**  In my previous installation I saw the b43 driver listed, but now the listing box is blank.

---

### Post by lkraemer on 2009-11-07
Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci -vvnn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     #(OR for 9.04 and above use:
                                  #cat /etc/modprobe.d/blacklist.conf)
iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

lk

---

### Post by pilchbo on 2009-11-07
> **lkraemer said:**
> iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

lk

Thanks.  I'm using a clean install of 9.10.  The only thing I've done since installing Ubuntu is download, extract, and copy the drivers as in the previous posts.  Wireless should be wlan0.  Let's see.

```

ken@ken-laptop:/$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

``````

ken@ken-laptop:/$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

ken@ken-laptop:/$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:50:5e:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.106 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:3000(size=256) memory:e0202000-e02020ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0200000-e0201fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:97:59:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

``````


ken@ken-laptop:/$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1660  2 
ecb                     2524  2 
b43                   122136  0 
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181236  1 b43
yenta_socket           24200  1 
joydev                 10272  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 b43,mac80211
rsrc_nonstatic         11644  1 yenta_socket
led_class               4096  1 b43
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
soundcore               7264  1 snd
shpchp                 32272  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
psmouse                56180  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ssb                    35300  1 b43
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

``````


ken@ken-laptop:/$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
ndiswrapper: command not found

``````


ken@ken-laptop:/$ cat /etc/modprobe.d/blacklist.conf
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

``````


ken@ken-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:

``````


ken@ken-laptop:/lib/firmware$ ls -alt
total 9932
drwxr-xr-x  2 root root    4096 2009-11-06 14:44 b43legacy
drwxr-xr-x  7 root root    4096 2009-11-06 14:44 .
-rw-r--r--  1 root root  109476 2009-11-06 14:44 b43-all-fw.zip
drwxr-xr-x  2 root root    4096 2009-11-06 14:44 b43
drwxr-xr-x 18 root root   12288 2009-11-06 02:53 ..
lrwxrwxrwx  1 root root      14 2009-11-06 02:34 NPE-B -> NPE-B.01020201
lrwxrwxrwx  1 root root      14 2009-11-06 02:34 NPE-C -> NPE-C.02020201
drwxr-xr-x 13 root root    4096 2009-10-28 16:59 acx
drwxr-xr-x  2 root root    4096 2009-10-28 16:59 zd1211
drwxr-xr-x 29 root root    4096 2009-10-28 16:57 2.6.31-14-generic
-rw-r--r--  1 root root   22622 2009-10-17 18:55 aic94xx-seq.fw
-rw-r--r--  1 root root   83968 2009-10-17 18:55 ar9170-1.fw
-rw-r--r--  1 root root    3508 2009-10-17 18:55 ar9170-2.fw
-rw-r--r--  1 root root   15960 2009-10-17 18:55 ar9170.fw
-rw-r--r--  1 root root   30348 2009-10-17 18:55 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   35184 2009-10-17 18:55 atmel_at76c502_3com-wpa.bin
-rw-r--r--  1 root root   31764 2009-10-17 18:55 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 2009-10-17 18:55 atmel_at76c502d.bin
-rw-r--r--  1 root root   35276 2009-10-17 18:55 atmel_at76c502d-wpa.bin
-rw-r--r--  1 root root   31776 2009-10-17 18:55 atmel_at76c502e.bin
-rw-r--r--  1 root root   35272 2009-10-17 18:55 atmel_at76c502e-wpa.bin
-rw-r--r--  1 root root   35276 2009-10-17 18:55 atmel_at76c502-wpa.bin
-rw-r--r--  1 root root   28156 2009-10-17 18:55 atmel_at76c503-i3861.bin
-rw-r--r--  1 root root   28032 2009-10-17 18:55 atmel_at76c503-i3863.bin
-rw-r--r--  1 root root   35372 2009-10-17 18:55 atmel_at76c503-rfmd-0.90.2-140.bin
-rw-r--r--  1 root root   37800 2009-10-17 18:55 atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root   37956 2009-10-17 18:55 atmel_at76c503-rfmd.bin
-rw-r--r--  1 root root   35180 2009-10-17 18:55 atmel_at76c504_2958-wpa.bin
-rw-r--r--  1 root root   39928 2009-10-17 18:55 atmel_at76c504a_2958-wpa.bin
-rw-r--r--  1 root root   31748 2009-10-17 18:55 atmel_at76c504.bin
-rw-r--r--  1 root root   35196 2009-10-17 18:55 atmel_at76c504c-wpa.bin
-rw-r--r--  1 root root   37005 2009-10-17 18:55 atmel_at76c505a-rfmd2958.bin
-rw-r--r--  1 root root   36992 2009-10-17 18:55 atmel_at76c505-rfmd2958.bin
-rw-r--r--  1 root root   35528 2009-10-17 18:55 atmel_at76c505-rfmd.bin
-rw-r--r--  1 root root   31824 2009-10-17 18:55 atmel_at76c506.bin
-rw-r--r--  1 root root   35228 2009-10-17 18:55 atmel_at76c506-wpa.bin
-rw-r--r--  1 root root  114688 2009-10-17 18:55 BCM2033-FW.BIN
-rw-r--r--  1 root root    3245 2009-10-17 18:55 BCM2033-MD.BIN
-rw-r--r--  1 root root   12401 2009-10-17 18:55 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 2009-10-17 18:55 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root 1142480 2009-10-17 18:55 i2400m-fw-usb-1.3.sbcf
-rw-r--r--  1 root root 1251036 2009-10-17 18:55 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root  209190 2009-10-17 18:55 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2009-10-17 18:55 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2009-10-17 18:55 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2009-10-17 18:55 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2009-10-17 18:55 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2009-10-17 18:55 ipw2200-sniffer.fw
-rw-r--r--  1 root root  112128 2009-10-17 18:55 isl3877
-rw-r--r--  1 root root   29036 2009-10-17 18:55 isl3886pci
-rw-r--r--  1 root root   29500 2009-10-17 18:55 isl3886usb
-rw-r--r--  1 root root   29736 2009-10-17 18:55 isl3887usb
-rw-r--r--  1 root root   93996 2009-10-17 18:55 isl3890
-rw-r--r--  1 root root  335056 2009-10-17 18:55 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  149652 2009-10-17 18:55 iwlwifi-3945-1.ucode
-rwxr-xr-x  1 root root  150100 2009-10-17 18:55 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187608 2009-10-17 18:55 iwlwifi-4965-1.ucode
-rwxr-xr-x  1 root root  187972 2009-10-17 18:55 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2009-10-17 18:55 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2009-10-17 18:55 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2009-10-17 18:55 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  459992 2009-10-17 18:55 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  118884 2009-10-17 18:55 lbtf_usb.bin
-rw-r--r--  1 root root   76802 2009-10-17 18:55 ql2100_fw.bin
-rw-r--r--  1 root root   84566 2009-10-17 18:55 ql2200_fw.bin
-rw-r--r--  1 root root  123170 2009-10-17 18:55 ql2300_fw.bin
-rw-r--r--  1 root root  132978 2009-10-17 18:55 ql2322_fw.bin
-rw-r--r--  1 root root  206500 2009-10-17 18:55 ql2400_fw.bin
-rw-r--r--  1 root root    8192 2009-10-17 18:55 rt2561.bin
-rw-r--r--  1 root root    8192 2009-10-17 18:55 rt2561s.bin
-rw-r--r--  1 root root    8192 2009-10-17 18:55 rt2661.bin
-rw-r--r--  1 root root    8192 2009-10-17 18:55 rt2860.bin
-rw-r--r--  1 root root    4096 2009-10-17 18:55 rt2870.bin
-rw-r--r--  1 root root    2048 2009-10-17 18:55 rt73.bin
-rw-r--r--  1 root root  141200 2009-10-17 18:55 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 2009-10-17 18:55 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 2009-10-17 18:55 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 2009-10-17 18:55 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 2009-10-17 18:55 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 2009-10-17 18:55 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 2009-10-17 18:55 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root  376836 2009-10-17 18:55 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 2009-10-17 18:55 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 2009-10-17 18:55 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 2009-10-17 18:55 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root   62484 2009-10-17 18:55 zd1201-ap.fw
-rw-r--r--  1 root root   70612 2009-10-17 18:55 zd1201.fw
-rw-r--r--  1 root root   15664 2009-10-13 15:41 NPE-B.01020201
-rw-r--r--  1 root root   15664 2009-10-13 15:41 NPE-C.02020201

``````


ken@ken-laptop:/lib/firmware$ cd /b43
bash: cd: /b43: No such file or directory
ken@ken-laptop:/lib/firmware$ cd /lib/firmware/b43
ken@ken-laptop:/lib/firmware/b43$ ls -alt
total 176
drwxr-xr-x 7 root root  4096 2009-11-06 14:44 ..
drwxr-xr-x 2 root root  4096 2009-11-06 14:44 .
-rw-r--r-- 1 root root  2680 2009-11-06 14:44 a0g0initvals4.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 b0g0bsinitvals13.fw
-rw-r--r-- 1 root root  2680 2009-11-06 14:44 b0g0initvals4.fw
-rw-r--r-- 1 root root  1858 2009-11-06 14:44 a0g0initvals5.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 b0g0bsinitvals5.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 lp0bsinitvals13.fw
-rw-r--r-- 1 root root 20080 2009-11-06 14:44 ucode4.fw
-rw-r--r-- 1 root root  2056 2009-11-06 14:44 a0g1initvals13.fw
-rw-r--r-- 1 root root  1320 2009-11-06 14:44 pcm4.fw
-rw-r--r-- 1 root root 24424 2009-11-06 14:44 ucode13.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 a0g1bsinitvals13.fw
-rw-r--r-- 1 root root    18 2009-11-06 14:44 b0g0bsinitvals4.fw
-rw-r--r-- 1 root root  1858 2009-11-06 14:44 b0g0initvals5.fw
-rw-r--r-- 1 root root  2052 2009-11-06 14:44 lp0initvals13.fw
-rw-r--r-- 1 root root    18 2009-11-06 14:44 a0g0bsinitvals4.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 a0g0bsinitvals5.fw
-rw-r--r-- 1 root root 22088 2009-11-06 14:44 ucode5.fw
-rw-r--r-- 1 root root   158 2009-11-06 14:44 a0g1bsinitvals5.fw
-rw-r--r-- 1 root root  2056 2009-11-06 14:44 b0g0initvals13.fw
-rw-r--r-- 1 root root  1320 2009-11-06 14:44 pcm5.fw
-rw-r--r-- 1 root root 26600 2009-11-06 14:44 ucode11.fw
-rw-r--r-- 1 root root  1858 2009-11-06 14:44 a0g1initvals5.fw


```As you can see, I also copied in the b43legacy stuff although I shouldn't need it with version 3 of the 4306.  I have not attempted adding my wireless or anything.  We're right at the beginning.  I appreciate you sticking with this.

:D

---

### Post by lkraemer on 2009-11-07
OK, everything appears as it should.  One quick suggestion is to remove the
b43-all-fw.zip file in /lib/firmware.  I should have told you to delete it.

Now if you go to the top right section of your toolbar you should see an icon
for enabling the restricted drivers.  Just click on it and let it work.
After that, in a few minutes, you should be able to left click on the networking
icon and select your router.

Here is what you should see:
[http://ubuntuforums.org/showthread.php?t=1314327&page=2](http://ubuntuforums.org/showthread.php?t=1314327&page=2)
Posting #12

If you want to connect manually you can do this:
```

iwconfig

```
should display something like the following (minus you routers name,
but you should know that name already):
```

ath0      IEEE 802.11g  ESSID:"Airlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:A3:91:B0:B2   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:57687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
At this point you know your Router's ESSID, that ath0 (in my case) is the
router, and you should be able to bring it up manually.
Replace the <interface> below with your actual interface which is wlan0.
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo iwconfig ath0 essid "Airlink"
sudo iwconfig ath0 mode Managed
sudo ifconfig ath0 up
sudo dhclient ath0
iwconfig

```
Post the output of iwconfig

lk

---

### Post by pilchbo on 2009-11-07
> **lkraemer said:**
> OK, everything appears as it should.  One quick suggestion is to remove the
b43-all-fw.zip file in /lib/firmware.  I should have told you to delete it.

Now if you go to the top right section of your toolbar you should see an icon
for enabling the restricted drivers.  Just click on it and let it work.
After that, in a few minutes, you should be able to left click on the networking
icon and select your router.

Here is what you should see:
[http://ubuntuforums.org/showthread.php?t=1314327&page=2](http://ubuntuforums.org/showthread.php?t=1314327&page=2)
Posting #12


There is no icon on the toolbar.  I know the one you mean, because I saw it/used it when fooling around with LiveCD version on my desktop.  So I went to System/Administration/Hardware Drivers and thought I could do it that way.  You know that gray dot to the left of the driver name, the one I should be able to click and make it blue and then click Activate?  I can't click it.  So before I try the terminal window, I'm wondering if there is something else wrong.

---

### Post by lkraemer on 2009-11-07
That is a possibility.........It could be a corrupt install.
I wonder if you insert the LiveCD and boot from that if you could
repeat the same previous steps and see if you can get wireless working.
Might be worth a try.

lk

---

### Post by pilchbo on 2009-11-07
> **lkraemer said:**
> That is a possibility.........It could be a corrupt install.
I wonder if you insert the LiveCD and boot from that if you could
repeat the same previous steps and see if you can get wireless working.
Might be worth a try.

lk


Ugh.  OK, I've started the laptop on its merry way.  This will take quite awhile, I think.  I'll report back.

kp

---

### Post by pilchbo on 2009-11-07
The LiveCD just finished loading up.  At the end there was an error message:

**The Panel encountered a problem while loading:  OAFIID GNOME_IndicatorApplet**

I chose Don't Delete.  I was then notified that new Hardware Drivers were available--both a balloon message and the icon on the toolbar.  Clicked icon.  Hardware Drivers dialog comes up.  Same problem.  When I attempt to select the Broadcom B43 wireless driver, I can't get the radio button to indicate it is selected.  However I clicked the Activate button anyway and it now says it is downloading and installing the driver.  (Wait for it....man, I thought it had hung up.  It took nearly ten minutes just for the download part.)  

After downloading and installing, the Hardware Drivers applet says the driver is activated and currently in use.  The button in the dialog no longer says Install, it says Remove.  The Network button on the toolbar, when clicked does not offer any wireless networks to connect to.  I don't hide my network.  When I alt-click and choose Edit Connections, I see no networks under Wireless.

I rebooted using the hard drive Ubuntu installation.  The Broadcom B43 driver now does not appear as activated, so I repeated the above--even though I couldn't select it, it appears to be downloading and activating, and incredibly faster than when it was managed by the LiveCD.  Okay, I'm going to switch over to the laptop to post the rest.


Now on the laptop.  Everything is the same.  The router doesn't appear on the Network choices, either by clicking the icon on the toolbar or clicking Edit Connections and getting the Network Connections applet.  Here is iwconfig:
```

ken@ken-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and here is the network picture

```

ken@ken-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:50:5e:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.106 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:3000(size=256) memory:e0202000-e02020ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0200000-e0201fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:97:59:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
ken@ken-laptop:~$ 

```

Looks to me like we've got an enabled wlan0 anyway.  Do I now add the home wireless network manually?

---

### Post by pilchbo on 2009-11-07
Maybe spoke too quickly.  The Hardware Drivers applet says the driver is free and tested by Ubuntu developers.  I just installed the wrong thing, didn't I?  The other ones never appeared in the Hardware Drivers window.

---

### Post by lkraemer on 2009-11-07
Post the output of:
```

lsmod

```
Then view the contents making sure b43 is installed.

lk

---

### Post by pilchbo on 2009-11-07
As requested...
```

ken@ken-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
snd_seq_midi            6432  0 
ecb                     2524  2 
ppdev                   6688  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
b43                   122136  0 
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  1 b43
yenta_socket           24200  1 
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               93052  2 b43,mac80211
rsrc_nonstatic         11644  1 yenta_socket
snd_timer              22276  2 snd_pcm,snd_seq
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  1 b43
joydev                 10272  0 
lp                      8964  0 
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
parport                35340  2 ppdev,lp
psmouse                56180  0 
serio_raw               5280  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ssb                    35300  1 b43
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```If I'm reading this correctly, b43 is a module and is used by a module.  Isn't that what it's supposed to be?

kp

---

### Post by dm6257 on 2009-11-07
I just installed 9.10 and my package manager can't find b43-fwcutter.  Ditto sudo apt-get install.

---

### Post by lkraemer on 2009-11-07
Looks to me as if the only thing you need is the Access Point associated.

If you want to connect manually you can do this:
```

iwconfig

```
should display something like the following (minus you routers name,
but you should know that name already):
```


ath0      IEEE 802.11g  ESSID:"Airlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:A3:91:B0:B2   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:57687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
At this point you know your Router's ESSID, that ath0 (in my case) is the
router, and you should be able to bring it up manually. Just insert your
routers name where you see "Airlink":   (copy & paste all commands)
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "Airlink"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0
iwconfig

```
Post the output of iwconfig

If this doesn't work I am at a loss as what to do next.  It has always worked.

lk

---

### Post by dm6257 on 2009-11-07
I noticed that when I ran 9.10 live cd it told me I needed firmware.  When I installed 9.10 on my hard drive it said no proprietary drivers  were
used.  I went ahead and added b43 and b43leagacy folders to the /lib/firmware folder and when I restarted, my broadcom wireless came right up.  As I mentioned elsewhere, my package manager can't find b43-fwcutter.

It is all very confusing as I am not a Linux techie.

---

### Post by pilchbo on 2009-11-08
Well, lk, no dice.  Here is some relevant code:

```

ken@ken-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PondLink1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```You can see the name of the network is there, but it could not be found.  Take a look at this:

```

ken@ken-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:97:59:1b
Sending on   LPF/wlan0/00:90:4b:97:59:1b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```I am going to reboot to see if that has any effect.  Then I will try one more time to add the network through the Edit Connections interface that you get when you alt-click the network icon in the tray.  If that doesn't work, I figure I've got only a few choices left:  


[LIST=1]
[*]Try Xubuntu again, even though it did a couple of squirrelly things right out of the box (such as it refused to set the system clock to local time and started at 00:00 instead);
[*]Buy a USB wireless adapter and make sure to get a generic one so that Ubuntu will recognize it;
[*]Reformat with Windows XP and continue to curse at the glacial effect it has on the laptop;
[*]Take a big hammer to the laptop, tell my wife that the "computer's broken" and that I will need to buy a new laptop.
[/LIST]
The whole purpose of going to Linux in general was that it would revitalize an old laptop.  I keep thinking it is something so simple that I will slap my forehead and say "duh" when I/we finally figure it out.

cheers,  kp

---

### Post by pilchbo on 2009-11-08
Rebooting did not do the trick.  I then clicked the network icon in the tray and chose an option at the bottom which said **Connect to Hidden Wireless Network...**  even though my router is not hidden.  I had forgotten that this reveals another little problem.  After putting in the name and the WEP Key, I am asked to provide a password to unlock the keyring.  I am sure that I put in the same password as my admin password for the whole Ubuntu system, but it refuses to recognize it.  Finally I clicked Deny.  Now when I try to connect to the hidden wireless, my network name (PondLink1) is shown as a connection in the drop down box.  When I choose it, everything below it grays out including the connect button.

I'm giving up.  This is ridiculous.  Much as I hate Windows, it at least recognizes the wireless signals around it.  My whole neighborhood is filled with networks.  I should see at least 4, maybe 6.

kp

---

### Post by tony1212 on 2009-11-08
Hi if your looking for help with command line stuff have a look here:

[https://help.ubuntu.com/community/AdvancedCommandlineHowto](https://help.ubuntu.com/community/AdvancedCommandlineHowto)

Also you could try the XFCE version of Mint 7 (Xubuntu 9.04 with a few extras) I've sometimes found that Mint will work for me when one of the *buntus does not as they come to the plate a little down the line and have often sorted out some of the initial bugs for you.

---

### Post by lkraemer on 2009-11-08
Well, there must have been something skipped.  You should have done:
1.  Fresh install
2.  EXTRACT, then copy the Firmware you downloaded from the website to
    /lib/firmware and those folders should have been the folders 
    b43 & b43 legacy
3.  Unhook Ethernet, Enable the restricted drivers (icon in top right toolbar)
4.  Wait a bit, then left click on the two little networking computers in
    the top right of menu tool bar.  (if you right click you can enable/
    disable the Wireless)
5.  Select your router.
6.  Open Browser
7.  Surf

Don't be so fast to jump ship.  We only tried Item #3 and there are two
other ways.  Ndiswrapper, and by using the b43xx drivers.

Another thing you can try is to purchase a Belkin F5D9010 PCMCIA for
$7.99.  Shipping is $10.00.  But they plug and play because I just purchased
two of them.   PM me for the business if you're interested.

Another thing you can do is to boot try Crunchbang, and see what drivers
are loaded and if the Wifi comes up working.  Maybe that Broadcom card
doesn't work with b43 and needs b43xx.  That would be an easy fix.

Lets at least try another way.
You can always use the drivers for your card and ndiswrapper.

Or if you have wired ethernet connection try using fwcutter to extract the firmware.


lk

---

### Post by pilchbo on 2009-11-08
Thanks, tony1212.  At this point I have nothing to lose--I purposefully haven't done any setup with Ubuntu this time around.  

kp

UPDATE:  No big surprise, but Mint works just like the rest of the Ubuntu family.  LK, Somehow I missed your last post, but I need a rest for a few days.  I wrote a bunch of other stuff, but deleted it because I shouldn't make comments when I'm really @#$%#-ed off.

kp

---

### Post by pilchbo on 2009-11-10
I just can't stay away from it.  More news from the front:


[LIST]
[*]LK, I _did_ do exactly what your list above says.
[*]I tried CrunchBang which is pretty cool but didn't work either.
[*]Based on search results that said Dream Linux works with the B43 out of the box, I booted that OS up from LiveCD.  I followed instructions found on forum there and still no wireless networks appear.  Also, during boot-up Dream Linux reports an active b43 but not an active wlan0.
[*]Based on several comments seen on various forums, I have checked, rechecked, triple-checked that the wireless light is on.  I've punched the wireless button several times when frustrated to see if it makes any difference.  It doesn't.
[*]I ran into this on the buglog pages for Karmic Koala posted around the same day as release of KK:  > Go to pool/restricted/b/bcmwl on Ubuntu CD or Ubuntu Live USB. Double click into the .deb file in there, and REINSTALL that package. Now you can activate Broadcom STA driver in Hardware Drivers.  I tried that and got nothing.
[*]I came across this and thought I might try it, but haven't yet:   [URL="http://ubuntu.cafuego.net/dists/jaunty-cafuego/broadcom/"]http://ubuntu.cafuego.net/dists/jaunty-cafuego/broadcom/
[/URL]
[*]I'm really beginning to think this is some kind of a hardware problem.  My computer is an HP Pavilion ze4907wm, in case I haven't listed that before.  I'm actually contemplating reinstalling Windows XP to see if the wi-fi works there like it did before the Linux experiment began.  Assuming it works, I would then reinstall something that would _share_ the hard drive instead of taking all of it.  It's only 40 Gb so I don't have a lot to share, but then I only plan to surf the 'Net with this thing for the most part.
[/LIST]
pilchbo

---

### Post by lkraemer on 2009-11-10
Do you by chance have an ethernet (wired) connection on that computer where you can try using the b43-fwcutter software?  If you do, and are willing to do another clean install, then connect to the internet and install the b43-fwcutter package from Synaptic. The problem of not
doing a clean install is I can't assume I know everything you have tried,
or that you have removed all the modules you should have.  A FRESH
install gets us calibrated.  I think you have a HP Laptop.  (The one
I am using tonight is a HP Pavillion ze4315us Laptop with 1Gig and
a new 160 Gig Western Digitial drive that is only using 127 Gig.)

(Make sure you boot into Windows, Enable the Wifi, and DON'T turn it off.
Just don't ever turn t off.  Some systems require a boot to Windows
to ENABLE it again.  What a PAIN! Just forget that button exists, and forget about the LED.  It may or maynot work.  It's not really needed.)

That should extract the firmware, and install the drivers to get it working.  If that doesn't work, we will just disable the b43 driver and use ndiswrapper.  To do that you are going to need to get your hands on the drivers (inf & sys files) for your Wifi card.  You should be able to find those from within your windows software, and then search for those names.

One way, or another it will work.  The problem is the developers change
things, and they need to, but we as users don't have a clue as to what
works for each version because it is a moving target.  And just one module
can keep it from working.  Unless someone posts a good HOWTO: it is up
to trial and error. 

lk

---

### Post by pilchbo on 2009-11-11
> **lkraemer said:**
> 

(Make sure you boot into Windows, Enable the Wifi, and DON'T turn it off.
Just don't ever turn t off.  Some systems require a boot to Windows
to ENABLE it again.  What a PAIN! Just forget that button exists, and forget about the LED.  It may or maynot work.  It's not really needed.)

lk

This supports what I was thinking.  I had already planned to reinstall Windows tonight.  (Remember, there is no Windows on the HDD now.)  Then I'm going to make sure that Windows can see a working wi-fi.  Then I am going to pick an Ubuntu-based OS and this time I'm leaving a small partition for Windows.  When I've got that done, I'll post again.  I've tried so many things that I think I know how to use the cutter, but better that you guide me through it.

pilchbo

EXTRA:  My HP has significantly less memory and HD space.  256MB for RAM, 40GB for HDD.

---

### Post by pilchbo on 2009-11-12
Re-installed Windows XP and all drivers from OEM disk that came with HP Pavilion.  Pushed the "on" button for wireless, brought up the wireless connections interface and told it to look for wireless networks and there was my home network.  Connect!  All I had time for last night.

pilchbo

---

### Post by lkraemer on 2009-11-12
OK, just do an orderly shutdown in Windows, leaving the Wifi in the
running state.  Then create a Dual Boot machine. Windows typically needs
about 6 Gig after it is completely installed.  If you make the Windows
Partition much smaller you won't have any room to install much software.

There is a good website for Dual Booting.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

lk

---

### Post by pilchbo on 2009-11-13
Now that I'm back working, haven't as much time to work on this.  I want to settle on my Linux of choice before installing yet again.  I counted it up and I installed six different Linuxes eight or nine times last week.  That's in addition to the 8 to 10 that I ran off of LiveCD.  I have these criteria:


[LIST=1]
[*]I'm partial to staying with Ubuntu or something based on it.  It has better support than some I've looked at.
[*]I want to maximize the resources of this 256MB of RAM laptop.
[*]I want an OS with a desktop that has real program names.  I liked CrunchBang, but I'm put off by cryptic program names that look like this "xgedit".  I think I've figured out that down the road I could configure the desktop interface any way I like, but that is past the first learning curve--I want it clear to start off with, which is one of the reasons I like Ubuntu.
[/LIST]
So I'm taking a look again at Xubuntu and Linux Mint on Xcfe desktop.  And I'm going to search the Net a little tonight.

pilchbo

---

### Post by lkraemer on 2009-11-13
Well, with the 256 RAM size that is going to limit your choices.
I've read on the forum that Xubuntu, Puppy, and my choice of Crunchbang
are about the best choices.  You could also try TinyME Acorn, MiniME, or
Damn Small Linux, TinyCore, or Slitaz.  Those are about the only ones that
will run and be fast enough with the limit of 256 RAM.  I tried most of them
on my old Compaq Presario 1672 K6-2 350 MHZ with 192 Meg RAM and 80 Gig Drive.

So, burn some LiveCD's on CDRW's, and test out your system to see what
works and what doesn't.  Pick the one that fits your fancy/needs.  Once again
I think my choice would be Crunchbang (Ubuntu based, with a good forum).

lk

---

### Post by pilchbo on 2009-11-13
Thanks again for the suggestions. I would like to not have to learn esoteric names of things like in CrunchBang.  That's what I like about Ubuntu/Xubuntu--the nice menu-driven stuff and commonsense names of programs.  We'll see.  Hard to gauge performance without installing them.  I know that performance-wise, CrunchBang was dynamite.  I'll look into the others.  I'm kind of surprised that Mint Xcfe isn't on the list, being Ubuntu based.  It would seem to rival Xubuntu.  I hope to be back with an installed program no later than Sunday.

pilchbo

---

### Post by DapperMe17 on 2009-11-13
Pilchbo,

I'm typing now from the Broadcom 4306. 

Here's my tutorial....[http://ubuntuforums.org/showthread.php?t=939658](http://ubuntuforums.org/showthread.php?t=939658)

I would also recommend Linux Mint XFCE. It ships with WICD by default.


:popcorn:

---

### Post by pilchbo on 2009-11-15
I settle on Xubuntu. Seemed to be slightly more responsive than Mint Xcfe. (Hard to tell from Live CD on my underpowered laptop--many app's refused to load.)  Didn't get further than that. When I try a method, I was thinking of running through the tutorial steps that DapperMe17 posted above.  Comments, lk?

pilchbo

---

### Post by DapperMe17 on 2009-11-16
You shouldn't have to follow "all" of those steps anymore. 

First, simply download & install WICD. Then, open it & see if your network automatically appears. If it does, you should only have to enter your network details in the "advanced settings" 

Second, if your network does not automatically appear, then you'll likely have to complete ONLY steps 21-25 of my tutorial.

That should be the extent, if your using Karmic 9.10. That's all it took me, with Karmic & the Broadcom 4306.


Now, if for some reason, that all fails...go ahead & follow all the steps listed, 1-25. 

I've had no problem connecting with either method.

---

### Post by pilchbo on 2009-11-19
Obviously I haven't had time to do anything.  Thanks for the update.  It will have to be the weekend.

pilchbo

---

### Post by pilchbo on 2009-11-21
> **DapperMe17 said:**
> You shouldn't have to follow "all" of those steps anymore. 

First, simply download & install WICD. Then, open it & see if your network automatically appears. If it does, you should only have to enter your network details in the "advanced settings" 

Second, if your network does not automatically appear, then you'll likely have to complete ONLY steps 21-25 of my tutorial.

That should be the extent, if your using Karmic 9.10. That's all it took me, with Karmic & the Broadcom 4306.


Now, if for some reason, that all fails...go ahead & follow all the steps listed, 1-25. 

I've had no problem connecting with either method.

I could not install WICD because Xubuntu reports that it conflicts with installed software. I assumed the installed applet called Network Manager is the software being referred to so I uninstalled it, but that wasn't the conflict.  Using Synaptic Package Manager, I removed Netowrk Manager and installed WICD (which also required a Python dependent package, python-urwid). Wireless network did not appear. Proceeding to try steps 21-25.

Also of note: the wireless light is not on, hasn't been since installing Xubuntu. During the previous go-round, the wireless light came on after installing a 4306 driver.  Of course, I never got connected, but the light being on or not would seem to indicate if the computer recognizes that it has a driver installed.

pilchbo

---

### Post by pilchbo on 2009-11-21
I am unable to begin creating the file described in tutorial step 21, dapper.  I get a "command not found" for sudo gedit. 

pilchbo

UPDATE:  I did a sudo apt-get for gedit and I'm installing it now.

---

### Post by pilchbo on 2009-11-21
> Best of luck, it works perfect with my BCM4306 v02. Don't be turned off by the length of the tread...that's what it took! :smile:

"THEE" key for me was script toward the end & especially the "network restart" line & the final terminal command to "run-the-script-at-boot." 

All the other threads that I researched failed to mention those two, which I've found essential to make it work.

The only other thing I suggest, is to manually set your network interface file. Neither network-manager, Wicd or wifi-radar would do the trick. However, they will act as a nice monitor of your internet connection.The above is from your other thread, dapper.  I followed steps 21 through the end.  No luck. Wicd shows only the wired network. I don't understand why the instructions exist to install Wicd--it seems to be the same thing as Network Manager.

I'm now going to read the preliminary steps in your tutorial and the stuff above that lk has posted to see if there is something that will work.  I'm going to start by installing the proprietary driver that lists under the Hardware Drivers app.

pilchbo

---

### Post by pilchbo on 2009-11-21
Well, it worked--but it doesn't work.  I used Hardware Drivers applet to install the B43 driver and the blue indicator light on the laptop came on. Wicd immediately showed me all of the wireless networks in my area.

Problem is, I cannot get Wicd to connect through my wireless. It authenticates and then says it cannot obtain an IP address. In the Properties box for the wireless network I get a section for Static IPs, a section for Static DNS, and then the encryption information section below that. I never had to fill that out when connecting in Windows. (CLARIFICATION: I never had to enter IP addresses. I did have to enter the WEP key.)

If I check the box to Use Static IPs, I can type in IP address from the information supplied by the router's administration software. It gives a specific IP address for this laptop. But if I check the Use Static IPs box, it automatically checks the Use Static DNS box and wants me to fill in the DNS domain, the Search domain, and DNS 1, 2, and 3.  (or at least 1--I never got a message to put in 2 or 3)  I have no idea what to put in there. I tried a guess, and put in the IP address for the router, but that didn't work.  I put it in for all three.  I'm going to poke around in Windows to see if I can figure this out, but help would be appreciated...I'm [B]so close!
:D

UPDATE:[/B]  I am getting different error messages when I try to connect.  It has not given me a message again that it can't obtain an IP address. It seems to be alternating between "bad password" and "could not contact the wireless access point."  I am using a best guess for the DNS settings mentioned above.  I found the advanced settings for the router and I'm pretty sure the DNS 1, 2, and 3 addresses are 0.0.0.0, but I still don't know what to put into the DNS domain name and the search domain name fields.  I've tried the starting IP address for the router, I've tried leaving them blank...nada.

---

### Post by pilot4pay on 2009-11-21
I am also having a terrible time with getting my wireless broadcomm radio working with 9.10 netbook remix. I'm running from a 4Gb live SD on an HP 110. I can connect via ethernet wired connection, activate the proprietary driver, I then get the message I need to reboot for the driver to work. I reboot, and the driver is not installed and no broadcomm modem. Shouldn't an SD live drive save the settings, and changes to the system? Do I need a degree in computer science to run linux?

---

### Post by pilchbo on 2009-11-21
I feel your pain, Pilot. It sounds like you have some different hardware than I do.  Perhaps you should start a new thread?

---

### Post by pilchbo on 2009-11-28
Well, it all became moot this past week when the wireless ceased working with my laptop under _**Windows**_!  The ultimate test was that it wouldn't work with three independent laptops, either, including my work laptop that has automatically connected to the wireless ever since ever.

So if you've read this thread through to the end and it helps you, good luck.  In my opinion you're going to need it.  I'm a reasonably savvy geek who  has built VBA apps for businesses, built computers from scratch, and I'm the go-to guy for many people around me.  If I can't work Linux out of the box to just get it hooked up to a wireless network, how is my buddy going to do it?  That would be my buddy who still thinks that he can only get his email on his computer "because it isn't there on your computer."  

I'll mark this thread solved because I did finally get the wireless network recognized.

---

