---
title: "HP pavilion dv4000 don't go wireless"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by pollorodighiero on 2010-10-14
hi, I am completely new with Ubuntu 10.04.
I have an HP Pavilion dv4365EA with an Intel PRO/wireless 2200 BG card, and I cannot connect to the internet

the cable connectio works fine

what can I do?  

thanx, pollo

---

### Post by lkraemer on 2010-10-14
**1. How do I know what Hardware my computer has?**

Open a Terminal Window (Console) and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. Copy & Paste to
prevent errors!
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

Are you sure that the Wifi is ENABLED?  Is there a Switch or Special 
Keystrokes (maybe CNTL F2) that turns it ON/OFF?


You could try to manually configure the Wifi Interface, if it is ENABLED.

**Manual Configure:**
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

lk

---

### Post by pollorodighiero on 2010-10-15
hello, I tried with iwconfig and the result is:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

so the manual configuration didn't work
what now?  thanx, pollo



QUOTE FROM THE FIRST ANSWER:
Are you sure that the Wifi is ENABLED?  Is there a Switch or Special 
Keystrokes (maybe CNTL F2) that turns it ON/OFF?


You could try to manually configure the Wifi Interface, if it is ENABLED.

**Manual Configure:**
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

```example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

lk[/QUOTE]

---

### Post by lkraemer on 2010-10-15
It appears you didn't read the posing correctly....
Copy and Paste each command in a Terminal Window (Console):
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
**If you are requesting help, post the output of each command........**

We need that information to know what your Hardware, Drivers, etc. are.

lk

---

### Post by ibizatunes on 2010-10-15
Does the dv4000 connect to the internet on window, have you turn off the wireless card itself?

---

### Post by pollorodighiero on 2010-10-20
I'm sorry, in windows the wireless card works correctly, so it's not that I turned it out.
following, the output of all the commands in terminal

thanx , pollo

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b8:0856 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:4e:b6:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:20 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:dd:df:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.4 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:3000(size=256) memory:b0109400-b01094ff


lsmod
Module                  Size  Used by
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  275008  2 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               135216  0 
sdhci_pci               5470  0 
drm_kms_helper         29297  1 i915
sbp2                   19448  0 
tifm_7xx1               3690  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
sdhci                  15462  1 sdhci_pci
libipw                 39896  1 ipw2200
intel_agp              24177  2 i915
soundcore               6620  1 snd
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
usblp                  10481  0 
tifm_core               6045  1 tifm_7xx1
video                  17375  1 i915
lib80211                5046  2 ipw2200,libipw
led_class               2864  1 sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
raid10                 20469  0 
raid456                52027  0 
async_raid6_recov       4743  1 raid456
async_pq                3026  2 raid456,async_raid6_recov
raid6_pq               80029  2 async_raid6_recov,async_pq
async_xor               2382  3 raid456,async_raid6_recov,async_pq
xor                    15028  1 async_xor
async_memcpy            1065  2 raid456,async_raid6_recov
async_tx                1996  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  19781  0 
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
usb_storage            39425  0 
raid0                   6804  0 
ieee1394               81181  2 sbp2,ohci1394
mii                     4381  2 8139too,8139cp
multipath               6041  0 
linear                  3874  0 


ndiswrapper -l
bcmwl5 : driver installed


cat /etc/modprobe.d/blacklist.conf
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


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by lkraemer on 2010-10-20
OK, it appears that you have ndiswrapper installed along with the Broadcom
bcmwl5 driver installed.  I assume you are not wanting to use the Windows
Broadcom Drivers for the Wifi hardware you have installed, because it
won't work using them.  Plus you must remove these to get the proper drivers
functional.

Let's clean up the Windows drivers by removing them along with ndiswrapper.

Open a Terminal Window (Console):

**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5

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

Once you have this corrected, and ndiswrapper -l (MINUS LOWERCASE "L") try:
```

sudo /etc/init.d/networking restart

```
or reboot. You should have the Wifi functional.  If it isn't move your mouse over
the Wifi Icon in the Top Right Toolbar, then RIGHT click and ENABLE the WIFI.
It must be ENABLED.


You're Wifi is a:
Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
and hopefully Ubuntu has selected the proper Drivers...........
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 maxlatency=24 mingnt=3

To try and Manually set up the Wifi try:

**MANUAL SETUP:**
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
```

sudo iwconfig Wlan0 essid "Airlink"

```
It shouldn't take more than about 15 minutes......


lk

---

