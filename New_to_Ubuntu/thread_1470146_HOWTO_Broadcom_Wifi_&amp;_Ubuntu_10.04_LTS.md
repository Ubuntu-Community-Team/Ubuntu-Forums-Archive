---
title: "HOWTO: Broadcom Wifi &amp; Ubuntu 10.04 LTS"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by lkraemer on 2010-05-02
This posting should help those of you with Broadcom Wifi Hardware that
are Upgrading/Installing Ubuntu 10.04 LTS.  10.04 uses the B43 Driver.

**1.  How do I know if I have Broadcom Hardware?**

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted.  Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

Your options that can be used to get the Wifi functional: (B43 is the preferred for 10.04)

**1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys**
   The correct 32/64 Bit drivers must be used to match Ubuntu 32/64 Bit.

[B]2. B43 and some Firmware that was downloaded/extracted when you
enabled the Driver.
[/B]

**#1 - NDISWRAPPER**
To install the Windows Drivers that are located on your Desktop in a
folder named broadcom (.sys & .inf files):
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```

Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

SKIP to FINISH below.......


**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

SKIP to FINISH below.......


**#2 Use DEFAULT B43 Driver in 10.04**
The Firmware is missing and you just need to have an Ethernet Connection
and ENABLE the B43 Driver, or if you don't have an Ethernet Connection,
you can just copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy.  You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working:  (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls
cd ..
cd b43legacy
ls
exit

```

Now you just have to Enable the B43 Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a B43 Driver listed a driver listed for your wireless,
if so enable it.  (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be. 

Check Network Manager (right click on the icon) to be sure the "Enable Wireless"
box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now.  If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
Post the output of lsmod.

You can check for errors with:
```

dmesg | tail

```

You may have to remove other modules depending on what lsmod shows:.... ..
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module bcm43xx and other conflicts installed you will
need to blacklist them, since you are going to be using B43.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r ndiswrapper

```
You can use sudo nano /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

**FINISH:**
Click on the Wifi Icon in the top right toolbar and select the Network.

**Manual Choice:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

It shouldn't take more than about 15 minutes......

lk

---

### Post by rldavis on 2010-05-18
Okay, I have reinstalled Ubuntu, done the necessary updates, and enabled b43 in Hardware Drivers, but still I have no wireless capability. Here is the output of lsmod:

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51914  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
b43                   157218  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
drm_kms_helper         29297  1 i915
mac80211              204922  1 b43
dell_wmi                1793  0 
drm                   162471  4 i915,drm_kms_helper
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24177  2 i915
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
psmouse                63245  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
cfg80211              126485  2 b43,mac80211
led_class               2864  2 b43,sdhci
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
lp                      7028  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
b44                    25542  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 b44
ssb                    37336  2 b43,b44

```Besides maybe b44, what should I remove, if anything?

---

### Post by lkraemer on 2010-05-18
I'd try just blacklisting b44 first.

Then, if you have downloaded the firmware, and have it copied to the proper
places, you should be able to do a:
```

sudo /etc/init.d/networking restart

```
or reboot.  You should have the Wifi functional.

This lsmod listing is different than what you posted on your other posting,
so I assume you did another fresh install.

These steps worked fine on my Compaq V5201US to make the Wifi Functional.

lk

---

### Post by Terl on 2010-05-18
I have a Broadcom wireless as well and installed the restricted driver (System>Administration>Hardware Drivers) without issue; just select it, activate it and the light goes on.  Just curious if there is a reason that that method was not mentioned to install the drivers.  It worked like a charm on my Dell Studio.

---

### Post by fredbird67 on 2010-05-24
Better yet, I personally recommend PC/OS ([http://www.pc-os.org]("http://www.pc-os.org")) instead of Ubuntu.  We have a 2005 Dell Inspiron 6000 laptop, which has a Broadcom 4311 (or is it the 4318? -- I can't remember) wireless card in it, and PC/OS properly detected it right off the bat without all the hassle involved with trying to set it up in Ubuntu (believe me, I've tried -- it's a BEAR to get that thing working in Ubuntu!).

What's more, PC/OS is based on Ubuntu, although by default, it uses Xfce for the desktop (which I personally prefer, anyway), although there is a GNOME version available for those of you that are hooked on GNOME.

Fred in St. Louis

---

### Post by anewguy on 2010-05-24
> **Terl said:**
> I have a Broadcom wireless as well and installed the restricted driver (System>Administration>Hardware Drivers) without issue; just select it, activate it and the light goes on.  Just curious if there is a reason that that method was not mentioned to install the drivers.  It worked like a charm on my Dell Studio.

Indeed, from what I've seen, you just need to hard-wire to your router (since obviously your wireless isn't working yet), open a terminal window (Applications/Accessories/Terminal), type sudo apt-get update and press enter.  Wait for that to complete then go to System/Administration/Hardware Drivers and enable the driver listed.

Also to be noted:

- if you need to install ndiswrapper in order to use your wireless, the 2 packages you must install are on the LiveCD you installed with:

/pool/main/n/ndiswrapper -> click on ndiswrapper-common first and let it install, then click on the utilities and let them install

- if you need or want to use ndiswrapper, there is another program on the LiveCD that takes away all of the command line things:  ndisgtk.

/pool/main/n/ndiswrapper/ndisgtk -> click on the package there to install it.  Once you have your Windows drivers, and ndiswrapper and ndisgtk both installed, forget the command line info and just do the following:

- go to System/Administration and click on Windows Wireless Drivers.  This will start ndisgtk (it is a GUI'd application).  Check for any existing definitions and delete them if they are present, then just click on add and point it to your Windows driver files.

Additionally, sometimes you see people make reference to the firmware cutter.  If for some reason you need it and don't have an internet connection, it is also on the LiveCD at:

/pool/main/b


Dave ;)

---

### Post by Kirkland14 on 2010-05-24
> **Terl said:**
> I have a Broadcom wireless as well and installed the restricted driver (System>Administration>Hardware Drivers) without issue; just select it, activate it and the light goes on.  Just curious if there is a reason that that method was not mentioned to install the drivers.  It worked like a charm on my Dell Studio.

I did this the same way(hard wired to my router) and it worked just great for me as well, and I just started using Linux yesterday.  I did this with my Dell 1545.

---

### Post by bcasanov on 2010-06-30
I have no B43 driver even listed in Hardware Drivers for my Broadcom BCM4312.  The only driver listed there is "Broadcom STA wireless driver" and in the description box, it says "These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware."  I have this driver activated, yet I cannot use wireless because when I left-click on the Network Manager icon in the panel, it shows that wireless is disabled. When I right-click, I can't enable wireless because the "Enable Wireless" option is grayed-out.

The results of the following command are:


sudo lshw -C network

```
 *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:02:b5:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5b:04:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

The output of lsmod is: 

```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
aes_i586                7268  814 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               191042  0 
dm_crypt               11331  0 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7596  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959630  0 
soundcore               6620  1 snd
serio_raw               3978  0 
usblp                  10481  0 
dell_wmi                1793  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
dell_laptop             6856  0 
lp                      7028  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
dcdbas                  5490  1 dell_laptop
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36174  0 
i915                  285891  3 
drm_kms_helper         29297  1 i915
hid                    67032  1 usbhid
usb_storage            39457  1 
intel_agp              24415  2 i915
drm                   163034  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31788  2 intel_agp,drm
ahci                   32200  2 
output                  1871  1 video
sky2                   41040  0 

```

Just to clarify, my computer does not have a physical wireless switch that toggles enabling/disabling wireless.

---

### Post by bcasanov on 2010-06-30
I finally got the B43 driver to display in Restricted Drivers after working with software sources and apt-get, and I have enabled it (and of course, disabled the other driver: the Broadcom STA driver).  After downloading and installing the driver and after rebooting, I still have the same problem of not being able to use my wireless.  

The output of sudo lshw -C network now is:

```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5b:04:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:02:b5:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
The output of lsmod is:

```
Module                  Size  Used by
btrfs                 458938  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
msdos                   6392  0 
jfs                   172682  0 
xfs                   515324  0 
exportfs                3437  1 xfs
reiserfs              225539  0 
usbhid                 36174  0 
hid                    67032  1 usbhid
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  2 msdos,vfat
aes_i586                7268  940 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               191042  0 
dm_crypt               11331  0 
arc4                    1153  2 
b43                   164132  0 
joydev                  8708  0 
snd_hda_codec_idt      51978  1 
snd_hda_intel          22037  2 
mac80211              205146  1 b43
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dell_wmi                1793  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  2 b43,mac80211
dell_laptop             6856  0 
dcdbas                  5490  1 dell_laptop
usblp                  10481  0 
led_class               2864  1 b43
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  285891  3 
drm_kms_helper         29297  1 i915
drm                   163034  4 i915,drm_kms_helper
usb_storage            39457  1 
intel_agp              24415  2 i915
sky2                   41040  0 
ssb                    38671  1 b43
ahci                   32200  2 
i2c_algo_bit            5028  1 i915
agpgart                31788  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video

```

I don't think I see any module conflicts or anything, but I might be wrong.  What should I do?

---

### Post by lkraemer on 2010-06-30
bcasanov,
What is the output for:
```

ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
What files are located at:
```

cd /
cd /lib
cd firmware
pwd
cd b43
ls -alt
cd ..
cd b43legacy
ls -alt

```

If the firmware files are there it should work, if not they need
to be copied as per the previous instructions.  If the firmware files 
exist, then go to Hardware Drivers and disable B43, then re-enable b43.

Then restart the networking or re-boot.

lk

---

### Post by bcasanov on 2010-06-30
After running ndiswrapper -l, the output of cat /etc/modprobe.d/blacklist.conf is:
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

```  
It should be noted that I removed "blacklist bcm43xx" in an attempt to find if this blacklisting was not allowing my wireless to work.  Removing this line did not work.

The output of iwconfig is:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

The files located at each of the directories given below are displayed through the output of the ls command:

/lib/firmware/b43
```
total 344
-rw-r--r--  1 root root  1840 2010-06-30 20:12 a0g0initvals5.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 b0g0bsinitvals5.fw
-rw-r--r--  1 root root  1840 2010-06-30 20:12 b0g0initvals5.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g0bsinitvals9.fw
-rw-r--r--  1 root root  2002 2010-06-30 20:12 a0g0initvals9.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g1bsinitvals5.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g1bsinitvals9.fw
-rw-r--r--  1 root root  2080 2010-06-30 20:12 a0g1initvals13.fw
-rw-r--r--  1 root root  1840 2010-06-30 20:12 a0g1initvals5.fw
-rw-r--r--  1 root root  2002 2010-06-30 20:12 a0g1initvals9.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 b0g0bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 b0g0bsinitvals9.fw
-rw-r--r--  1 root root  2080 2010-06-30 20:12 b0g0initvals13.fw
-rw-r--r--  1 root root  2002 2010-06-30 20:12 b0g0initvals9.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 lp0bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 lp0bsinitvals14.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 lp0bsinitvals15.fw
-rw-r--r--  1 root root  3618 2010-06-30 20:12 lp0initvals13.fw
-rw-r--r--  1 root root  2064 2010-06-30 20:12 lp0initvals14.fw
-rw-r--r--  1 root root  2052 2010-06-30 20:12 lp0initvals15.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 n0absinitvals11.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 n0bsinitvals11.fw
-rw-r--r--  1 root root  2100 2010-06-30 20:12 n0initvals11.fw
-rw-r--r--  1 root root  1320 2010-06-30 20:12 pcm5.fw
-rw-r--r--  1 root root 29864 2010-06-30 20:12 ucode11.fw
-rw-r--r--  1 root root 32232 2010-06-30 20:12 ucode13.fw
-rw-r--r--  1 root root 31384 2010-06-30 20:12 ucode14.fw
-rw-r--r--  1 root root 30488 2010-06-30 20:12 ucode15.fw
-rw-r--r--  1 root root 22384 2010-06-30 20:12 ucode5.fw
-rw-r--r--  1 root root 25160 2010-06-30 20:12 ucode9.fw
drwxr-xr-x 52 root root 16384 2010-06-30 15:52 ..
drwxr-xr-x  2 root root  4096 2010-06-15 20:55 .
-rw-r--r--  1 root root    18 2008-04-18 14:27 a0g0bsinitvals4.fw
-rw-r--r--  1 root root  2680 2008-04-18 14:27 a0g0initvals4.fw
-rw-r--r--  1 root root    18 2008-04-18 14:27 b0g0bsinitvals4.fw
-rw-r--r--  1 root root  2680 2008-04-18 14:27 b0g0initvals4.fw
-rw-r--r--  1 root root  1320 2008-04-18 14:27 pcm4.fw
-rw-r--r--  1 root root 20080 2008-04-18 14:27 ucode4.fw

```

/lib/firmware/b43legacy
```
total 152
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g0bsinitvals5.fw
-rw-r--r--  1 root root    18 2010-06-30 20:12 a0g0bsinitvals2.fw
-rw-r--r--  1 root root  2520 2010-06-30 20:12 a0g0initvals2.fw
-rw-r--r--  1 root root  1818 2010-06-30 20:12 a0g0initvals5.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 a0g1bsinitvals5.fw
-rw-r--r--  1 root root  1818 2010-06-30 20:12 a0g1initvals5.fw
-rw-r--r--  1 root root    18 2010-06-30 20:12 b0g0bsinitvals2.fw
-rw-r--r--  1 root root   158 2010-06-30 20:12 b0g0bsinitvals5.fw
-rw-r--r--  1 root root  2520 2010-06-30 20:12 b0g0initvals2.fw
-rw-r--r--  1 root root  1818 2010-06-30 20:12 b0g0initvals5.fw
-rw-r--r--  1 root root  1320 2010-06-30 20:12 pcm4.fw
-rw-r--r--  1 root root  1320 2010-06-30 20:12 pcm5.fw
-rw-r--r--  1 root root 21680 2010-06-30 20:12 ucode11.fw
-rw-r--r--  1 root root 16360 2010-06-30 20:12 ucode2.fw
-rw-r--r--  1 root root 20096 2010-06-30 20:12 ucode4.fw
-rw-r--r--  1 root root 22280 2010-06-30 20:12 ucode5.fw
drwxr-xr-x 52 root root 16384 2010-06-30 15:52 ..
drwxr-xr-x  2 root root  4096 2010-06-15 20:56 .

```

---

### Post by bcasanov on 2010-07-01
I checked the files I downloaded in each of the extracted folders and I saw that all of the same files were there in the /lib/firmware/b43 and /lib/firmware/b43legacy locations, along with some other files that I presume were downloaded when I disabled and then re-enabled the B43 driver in Restricted Drivers.  I have disabled and re-enabled the B43 driver multiple times, and still, I do not have wireless after I restart.

---

### Post by ldkraemer on 2010-07-01
What was the output, if any from ndiswrapper -l  ?????

bcm43xx isn't used and needs to be Blacklisted.  Add this driver to your Blacklist.conf
file and then restart networking and/or re-boot.

lk

---

### Post by bcasanov on 2010-07-01
There is no output for ndiswrapper -l.  I put in the "blacklist bcm43xx" line back in the blacklist.conf file, and after I restarted networking with the command "sudo /etc/init.d/networking restart" I have the following output:

```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

I still do not have wireless working.

---

### Post by bcasanov on 2010-07-01
I do not know if this is relevant or not, but my /etc/modprobe.d/blacklist-local.conf file has only one line, and it says "blacklist wl".  Is wl a Broadcom driver-related or wireless-related module?

---

### Post by lkraemer on 2010-07-01
Well, I'm at a loss now because it has always worked before.

Maybe now that bcm43xx is blacklisted, you should disable the hardware
drivers and then enable b43 again......

OR 

Maybe you can boot the LiveCD of 10.04 and then copy the *.fw files
to the proper location and then enable the hardware drivers and see
if it works from a LiveCD.  I've done it on my Compaq Laptops.

Other than that I'd suggest blacklisting the b43 driver and using 
ndiswrapper with the Windows Drivers (inf & sys).  That will work.

lk

---

### Post by bcasanov on 2010-07-02
Thank you so much for your help!  I tried the LiveCD, and during that session, I tried something I did not think to do before.  First, though, I tried all methods to attempt to get wireless through enabling the B43 driver, and I did not have success on the LiveCD, which should have worked by all accounts. On my laptop, there is a key with a wireless tower icon on it, and I basically thought that I might as well try anything, including trying out this key I was unfamiliar with, and after I had pushed the key, I had wireless.  Now I know that this key acts as a physical on/off wireless toggle switch.  After the LiveCD session, I tried this discovery out on my Ubuntu install, and it worked!

---

### Post by anewguy on 2010-07-23
I noticed one of your network adapters in your first post is listed with "vbox" in the name - are you running Ubuntu in a VirtualBox virtual machine?  If so, what is the native OS?

Dave ;)

---

