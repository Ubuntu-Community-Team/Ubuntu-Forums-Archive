---
title: "wireless problem"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by nyx14850 on 2011-09-06
[SIZE=2]Hi,  I am running 10.04 lucid lynx on my starling netbook. I am connected   the internet via wired ethernet. I would like to be able to use   wireless networks but my machine will not detect any of them. The wi-fi   LED is lit up. 

ifconfig returns this for the wlan0 :[/SIZE] [SIZE=2]

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:91:bc:71  [/SIZE] [SIZE=2]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig returns:[/SIZE]  [SIZE=2]

wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  [/SIZE] [SIZE=2]
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:eek:n   Fragment thr:eek:ff
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also, no wireless icon appears on my toolbar. Why does it not   automatically detect the wireless networks? I only have an icon with an   up and down arrow which shows the wired ethernet connection. Am I   missing drivers?[/SIZE] [SIZE=2]

Thanks,[/SIZE] [SIZE=2]
Adam[/SIZE]
                                                                                                   [SIZE=2][IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11221271")                        [/SIZE]

---

### Post by 3rdalbum on 2011-09-06
> **nyx14850 said:**
> [SIZE=2]Hi,  I am running 10.04 lucid lynx on my starling netbook. I am connected   the internet via wired ethernet. I would like to be able to use   wireless networks but my machine will not detect any of them. The wi-fi   LED is lit up. 

ifconfig returns this for the wlan0 :[/SIZE] [SIZE=2]

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:91:bc:71  [/SIZE] [SIZE=2]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig returns:[/SIZE]  [SIZE=2]

wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  [/SIZE] [SIZE=2]
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:eek:n   Fragment thr:eek:ff
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also, no wireless icon appears on my toolbar. Why does it not   automatically detect the wireless networks? I only have an icon with an   up and down arrow which shows the wired ethernet connection. Am I   missing drivers?[/SIZE] [SIZE=2]

When you click on the "wired ethernet connection" icon in the top panel, exactly what menu items appear? Please type them out precisely, even if they are greyed-out (and tell us which ones are greyed-out).

---

### Post by wildmanne39 on 2011-09-06
Hi, please run these commands and post the results here:
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

I will be out of town part of the day tomorrow but as soon as I get back I will check on you.
Thank you

---

### Post by nyx14850 on 2011-09-07
Hi, Here are the outputs from the commands

lshw -C network:

[I]*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:01:44:68
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=69.251.251.143 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:1000(size=256) memory:91010000-91010fff(prefetchable) memory:91000000-9100ffff(prefetchable) memory:91020000-9102ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:c4:91:bc:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
[/I]
lspci -nn | grep -e

*02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)*

rfkill list all

*(nothing appears)*

lsmod

[I]Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
snd                    54244  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
lp                      7028  0 
r8187b                169943  0 
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  288611  3 
drm_kms_helper         29329  1 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
video                  17375  1 i915
r8169                  34140  0 
mii                     4381  1 r8169
output                  1871  1 video
agpgart                31724  2 drm,intel_agp[/I]



Thank you.

---

### Post by nyx14850 on 2011-09-07
i only have one icon with is a while box with an up arrow and down arrow. when i click on it it open a box with the heading: Connection properties: eth0. There is a "configure" tab i can click on which then shows 4 tabs: wired, wireless, broadband, vpn, dsl. All of these are blank except the "wired" which lists eth0 and says last used "never."

This is also strange since i'm using a wired connection (works fine). I just can't get the Wi-Fi to work or even detect any of the wireless networks.

---

### Post by anewguy on 2011-09-07
Please post back the complete output of the following, as I don't see the specifics for your wireless hardware listed above:

lspci

lsusb


Thanks
Dave ;)

---

### Post by wildmanne39 on 2011-09-07
Hi, you missed part of this command please just copy and paste into the terminal, also run the commands that anewguy asked for.
```
lspci -nn | grep -e 0280 -e 0200
```
Thank you

---

### Post by nyx14850 on 2011-09-07
Hi, I did remember to type the entire command---i just didn't write rewrite it in my reply. Here are the additional outputs from lspci and lsusb :


lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 064e:a127 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks.

---

### Post by wildmanne39 on 2011-09-07
Hi, it looks like you have the wrong driver loaded it took some research but  this is the one you need RTL8187 so it should be a matter of doing this.
```
sudo su
echo "blacklist r8187b" >> /etc/modprobe.d/blacklist.conf
exit
```
Then
```
sudo modprobe rtl8187
```
disconnect your wired connection before you run the commands, if it works we will need to make it permanent.
Thank you

---

### Post by anewguy on 2011-09-08
Just a quick tip wildmanne39, this is why I always have the user do a lsusb along with everything else.  Just in case it's a USB device they plugged in or a laptop with an internal wireless connected to the internal USB.  you've done a great job on helping the OP.

Dave ;)

---

### Post by nyx14850 on 2011-09-08
hi, thanks but i ran those commands after disconnecting and i still am not able to detect any wireless networks or see any wireless icon appear.

---

### Post by wildmanne39 on 2011-09-08
Hi, yes your advice is sound, I to do it when I think it might be a usb device, I know I should ask the first time but I usually give about six commands and I am afraid I will over whelm them.
Thank you

---

### Post by wildmanne39 on 2011-09-08
Hi, post the results from these commands please: Time to roll up our sleeves and get our hands dirty.
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
```
dmesg | grep wlan0
```
```
ndiswrapper -l
```
```
dmesg | egrep 'rtl|firm'
```
Thank you

---

### Post by anewguy on 2011-09-08
> **wildmanne39 said:**
> Hi, yes your advice is sound, I to do it when I think it might be a usb device, I know I should ask the first time but I usually give about six commands and I am afraid I will over whelm them.
Thank you

Sorry about that - didn't mean to sound "preachy" or anything - I was really tired last night!

Dave ;)

---

### Post by wildmanne39 on 2011-09-08
Hi, you didn't, I appreciate your advice.

---

### Post by anewguy on 2011-09-08
OP:  Do you by chance have a web cam connected?  There are notes on the net about this adapter, 10.xx and a web cam causing the wireless not to work.  There are also old posts out there about building/loading the module that I think we can ignore for now as the support for the 8187 is supposedly "out of the box" with 10.xx, the only thing I don't know is if that applies to the USB version you have and the hardware it is (note usbid of 0bda:8189 versus 0bda:8187 - the 8189 is supposedly still the rtl8187b and is supposed to still work).

I have found a lot of posts on the net about this, so I'll spend some time trying to weed through them.  In the mean time, keep working with wildmanne39 and I'll let you both know if I find anything that looks promising if you don't already have it solved by then.

Dave ;)

---

### Post by anewguy on 2011-09-08
Just thought of 1 more thing:

Did you do a Wubi install?

---

### Post by wildmanne39 on 2011-09-08
Hi, all we can do is wait for him to post the results of the commands I gave him.

I learned that wireless connection works the same in wubi as it does in a normal install of ubuntu, only once I was not able to get one working in wubi and neither could the people I have been learning networking from.

---

### Post by anewguy on 2011-09-08
Okay, I probably shouldn't admit it, and I've been delaying doing so, but I actually run one these adapters on my desktop - a Trendnet USB adapter with the exact same usb id, etc..  I don't remember doing anything special (hence why I haven't mentioned it before - my old age is stopping me from remembering things as well - or perhaps it was the late 60'/early 70's recreational activities ;) ).

The first thing I would do, if you haven't already:

sudo apt-get update

Wait for that to finish and reboot if needed.

Post the output of:

ls /boot


I would be interested in seeing the contents of the following:

/etc/udev/rules.d/70-persistent-net.rules

Also, as wildmanne39 suggested, the r8187b module should probably be blacklisted (it doesn't show in my modules list nor do I have it blacklisted), but in addition, if you did not already reboot, you will need to do so as we did not have you remove the old module (sudo rmmod r8187b).  After the reboot you'll need to

sudo modprobe rtl8187

again to reload it since we don't have it being automatically loaded via modules yet.  Ater the reboot and loading of the module, your lsmod should show, amongst other things, something like:

rtl8187
mac80211 
led_class (I think it is needed to control the wireless led)
cfg80211 
eeprom_93cx6

If not, please let us know.

So, please reboot, then retry the wireless. 

If it does work, we just need you to do one little thing to make the changes "stick" - add to modules.

Dave ;)

---

### Post by nyx14850 on 2011-09-08
Hi guys, here are the additional command outpus. Also, I do have a webcam. It is built into my netbook. I did not not a wubi install, since the aptitude utility says there is no such package.  Thanks.



lsmod:

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
lp                      7028  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  288611  3 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 intel_agp,drm
output                  1871  1 video
r8169                  34140  0 
mii                     4381  1 r8169


cat /etc/modprobe.d/blacklist.conf :

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
blacklist r8187b


dmesg | grep wlan0
(nothing appears)



ndiswrapper -l :

Error: ndiswrapper-utils-1.9 not installed!


dmesg | egrep 'rtl|firm'

(nothing appears)

---

### Post by nyx14850 on 2011-09-08
Other outputs after i did a reboot and then sudo modprobe trl18187:


ls /boot
abi-2.6.28-17-generic         memtest86+.bin
abi-2.6.31-21-generic         System.map-2.6.28-17-generic
abi-2.6.32-22-generic         System.map-2.6.31-21-generic
abi-2.6.32-23-generic         System.map-2.6.32-22-generic
abi-2.6.32-24-generic         System.map-2.6.32-23-generic
abi-2.6.32-25-generic         System.map-2.6.32-24-generic
abi-2.6.32-26-generic         System.map-2.6.32-25-generic
abi-2.6.32-27-generic         System.map-2.6.32-26-generic
abi-2.6.32-28-generic         System.map-2.6.32-27-generic
abi-2.6.32-29-generic         System.map-2.6.32-28-generic
abi-2.6.32-30-generic         System.map-2.6.32-29-generic
abi-2.6.32-31-generic         System.map-2.6.32-30-generic
abi-2.6.32-32-generic         System.map-2.6.32-31-generic
abi-2.6.32-33-generic         System.map-2.6.32-32-generic
config-2.6.28-17-generic      System.map-2.6.32-33-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.28-17-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.31-21-generic
config-2.6.32-23-generic      vmcoreinfo-2.6.32-22-generic
config-2.6.32-24-generic      vmcoreinfo-2.6.32-23-generic
config-2.6.32-25-generic      vmcoreinfo-2.6.32-24-generic
config-2.6.32-26-generic      vmcoreinfo-2.6.32-25-generic
config-2.6.32-27-generic      vmcoreinfo-2.6.32-26-generic
config-2.6.32-28-generic      vmcoreinfo-2.6.32-27-generic
config-2.6.32-29-generic      vmcoreinfo-2.6.32-28-generic
config-2.6.32-30-generic      vmcoreinfo-2.6.32-29-generic
config-2.6.32-31-generic      vmcoreinfo-2.6.32-30-generic
config-2.6.32-32-generic      vmcoreinfo-2.6.32-31-generic
config-2.6.32-33-generic      vmcoreinfo-2.6.32-32-generic
grub                          vmcoreinfo-2.6.32-33-generic
initrd.img-2.6.28-17-generic  vmlinuz-2.6.28-17-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-23-generic  vmlinuz-2.6.32-23-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-25-generic  vmlinuz-2.6.32-25-generic
initrd.img-2.6.32-26-generic  vmlinuz-2.6.32-26-generic
initrd.img-2.6.32-27-generic  vmlinuz-2.6.32-27-generic
initrd.img-2.6.32-28-generic  vmlinuz-2.6.32-28-generic
initrd.img-2.6.32-29-generic  vmlinuz-2.6.32-29-generic
initrd.img-2.6.32-30-generic  vmlinuz-2.6.32-30-generic
initrd.img-2.6.32-31-generic  vmlinuz-2.6.32-31-generic
initrd.img-2.6.32-32-generic  vmlinuz-2.6.32-32-generic
initrd.img-2.6.32-33-generic  vmlinuz-2.6.32-33-generic



cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:9e:01:44:68", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:c4:91:bc:71", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"



0:39 PM~$ lsmod 
Module                  Size  Used by
arc4                    1153  2 
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
lp                      7028  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  288611  3 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 intel_agp,drm
output                  1871  1 video
r8169                  34140  0 
mii                     4381  1 r8169

---

### Post by anewguy on 2011-09-08
Here's what I'd like you to try:

sudo gedit /etc/udev/rules.d/80-persistent-net-8189.rules

This will bring up a blank file.  Put the following in that file:

# USB device 0x0bda:0x8189 (usb) 
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:c4:91:bc:71", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

It's possible your address is different, so you may need to substitute it above, but let's try this first.

BTW - Starting with "SUBSYSTEM" it's all 1 line to the end - it just displays as more than 1 here.

Save the file and exit the editor.

Then:

sudo gedit /etc/modules

Add the following to the end of the file:

rtl8187

Save the file, exit the editor, exit the terminal window.

Reboot.

Now right-click network manager and see it wireless is enabled - if not, enable it.

Wait a few seconds, then left-click on network manager and see if it shows any wireless networks.

Dave ;)

BTW - it might be worth updating to 10.10 and letting all the updates go through after that via update manager (probably a couple of times?).  I don't know but it's possible that since I don't remember doing anything that perhaps one of the newer kernels (I'm in 10.10 and at kernel 2.6.35-30.

---

### Post by wildmanne39 on 2011-09-09
Hi, the drivers are loaded please run these commands and post the results:
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | egrep 'rtl|firm'
```
```
lsmod | grep rtl
```
I am about done for the night I will check back tomorrow.
Thank you

---

### Post by anewguy on 2011-09-09
The udev rule wasn't looking for the usb manufacturer id and product id on the line for the 8187.  Not sure what happens with nothing in the address.  I know mine specifically has the 8189 product id, so I just had the OP add the extra rule file to hopefully ID it and assign wlan0 to it. Driver was only loaded by the manual modprobe I had them do again after the boot - decided just to have the OP load it in modules so it will load now.  The other modules are used by rtl8187 so I'm glad to see they show now after the modprobe.

Will be curious to see after the reboot so the new udev rule takes effect - if no difference then let's take a look at what you requested.

Dave ;)

---

### Post by nyx14850 on 2011-09-09
Hi guys, more outputs below. I also edited the files anewguy asked and then rebooted, but to no avail. Thanks.


nm-tool

NetworkManager Tool

State: connected

- Device: eth0 [Auto eth0] ----------------------------------------------------
Type: Wired
Driver: r8169
State: connected
Default: yes
HW Address: 00:26:9E:01:44:68

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
Address: 69.251.251.143
Prefix: 21 (255.255.248.0)
Gateway: 69.251.248.1

DNS: 68.87.73.246
DNS: 68.87.71.230


- Device: wlan1 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8187
State: disconnected
Default: no
HW Address: 00:17:C4:91:BC:70

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
jamie: Infra, 00:24:B2:E2:0E:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
Frank Sucks 2: Infra, 00:1C:10:05:31:7F, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA
PAT119: Infra, E0:91:F5:C2:0B:A3, Freq 2422 MHz, Rate 54 Mb/s, Strength 57 WPA2
DRWV2: Infra, 00:18:01:F0:50:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WEP
WATSON: Infra, 00:24:B25:E3:46, Freq 2417 MHz, Rate 54 Mb/s, Strength 68 WEP
10FX08144752: Infra, 0C5:02:13:24:9C, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WEP
kingfisher: Infra, 00:26:F3:F9:EE:A8, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
HOME-6948: Infra, 00:26:F3:F9:69:48, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
RyWorld: Infra, E0:91:F5:BD:FC:EF, Freq 2417 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
WATSON: Infra, 00:24:B25:E3:46, Freq 2417 MHz, Rate 54 Mb/s, Strength 72 WPA
camus: Infra, 00:21:29:B0:10:A7, Freq 2452 MHz, Rate 54 Mb/s, Strength 71 WPA
belkin.c42: Infra, 94:44:52:FBC:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
NETGEAR: Infra, A0:21:B7:BE:66:C4, Freq 2417 MHz, Rate 54 Mb/s, Strength 78 WPA
shanurse: Infra, A0:21:B7:A0:5B:9C, Freq 2422 MHz, Rate 54 Mb/s, Strength 75 WPA
Plato's Cave: Infra, C0:C1:C03:4E:1D, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
Dorm-NET: Infra, A0:21:B7:A0:04:80, Freq 2427 MHz, Rate 54 Mb/s, Strength 87 WPA2
Ploosh: Infra, A0:21:B7:A1:1D:A8, Freq 2417 MHz, Rate 54 Mb/s, Strength 90 WPA


iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan1 IEEE 802.11bg ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff



rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no



dmesg | grep wlan0
[ 21.114465] udev: renamed network interface wlan0 to wlan1

---

### Post by nyx14850 on 2011-09-09
sudo iwlist scan

wlan1 Scan completed :
Cell 01 - Address: A0:21:B7:A0:5B:9C
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=56/70 Signal level=-54 dBm
Encryption keyn
ESSID:"shanurse"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f17f6d80
Extra: Last beacon: 1812ms ago
IE: Unknown: 00087368616E75727365
IE: Unknown: 010882848B968C129824
IE: Unknown: 030103
IE: Unknown: 050401020000
IE: Unknown: 0706555320010B1B
IE: Unknown: 2A0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: 3204B048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C34030D0800000000000000000000000000000000000000
IE: Unknown: 3D16030D0800000000000000000000000000000000000000
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000A021B7A05B9C103C000103
Cell 02 - Address: 00:1F:5B:89:F1:0B
Channel:9
Frequency:2.452 GHz (Channel 9)
Quality=58/70 Signal level=-52 dBm
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f282c30a
Extra: Last beacon: 956ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B960C121824
IE: Unknown: 030109
IE: Unknown: 050401030000
IE: Unknown: 0706555320010B12
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1609000000000000000000000000000000000000000000
IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C332C0217FFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3409000000000000000000000000000000000000000000
IE: Unknown: DD07000393016A0021
Cell 03 - Address: 94:44:52:FBC:42
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=53/70 Signal level=-57 dBm
Encryption keyn
ESSID:"belkin.c42"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f4c03176
Extra: Last beacon: 928ms ago
IE: Unknown: 000A62656C6B696E2E633432
IE: Unknown: 010882848B960C121824
IE: Unknown: 03010B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
IE: Unknown: 3D160B070000000000000000000000000000000000000000
IE: WPA Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
IE: Unknown: DD0600E04C020160
IE: Unknown: DD0E0050F204104A0001101044000102
Cell 04 - Address: C0:C1:C03:4E:1D
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=63/70 Signal level=-47 dBm
Encryption keyn
ESSID:"Plato's Cave"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000001f38df18c
Extra: Last beacon: 556ms ago
IE: Unknown: 000C506C61746F27732043617665
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 050400010000
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D160B081500000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD0E0050F204104A0001101044000102
IE: Unknown: DD090010180201F0040000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
Cell 05 - Address: 00:26:F3:F9:69:49
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=42/70 Signal level=-68 dBm
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f1909f3d
Extra: Last beacon: 2076ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050600000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05010042127A
IE: Unknown: DD07000C4300000000
Cell 06 - Address: A0:21:B7:A0:04:80
Channel:4
Frequency:2.427 GHz (Channel 4)
Quality=62/70 Signal level=-48 dBm
Encryption keyn
ESSID:"Dorm-NET"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f148ad80
Extra: Last beacon: 1460ms ago
IE: Unknown: 0008446F726D2D4E4554
IE: Unknown: 010882848B960C121824
IE: Unknown: 030104
IE: Unknown: 050400020000
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3404080800000000000000000000000000000000000000
IE: Unknown: 3D1604080800000000000000000000000000000000000000
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD0E0050F204104A0001101044000102
Cell 07 - Address: 00:26:F3:F9:EE:A8
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=40/70 Signal level=-70 dBm
Encryption keyn
ESSID:"kingfisher"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f18be168
Extra: Last beacon: 2088ms ago
IE: Unknown: 000A6B696E67666973686572
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800026F3F9EEA8103C000101
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050000000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B0500003A127A
IE: Unknown: DD07000C4300000000
Cell 08 - Address: 00:26:F3:F9:EE:AA
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=42/70 Signal level=-68 dBm
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f18bf403
Extra: Last beacon: 2084ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050000000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B0500003A127A
IE: Unknown: DD07000C4300000000
Cell 09 - Address: 00:24:B25:E3:46
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=50/70 Signal level=-60 dBm
Encryption keyn
ESSID:"WATSON"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f188cd80
Extra: Last beacon: 1552ms ago
IE: Unknown: 0006574154534F4E
IE: Unknown: 010882848B968C129824
IE: Unknown: 030102
IE: Unknown: 050401020000
IE: Unknown: 0706555320010B1B
IE: Unknown: 2A0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: 3204B048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000
IE: Unknown: 3D16020D0800000000000000000000000000000000000000
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000000024B2D5E346103C000103
Cell 10 - Address: 00:26:F3:F9:69:48
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=45/70 Signal level=-65 dBm
Encryption keyn
ESSID:"HOME-6948"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f19094ab
Extra: Last beacon: 2080ms ago
IE: Unknown: 0009484F4D452D36393438
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: DD270050F204104A0001101044000101104700102880288028801880A8800026F3F96948103C000101
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050600000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05010040127A
IE: Unknown: DD07000C4300000000
Cell 11 - Address: 0C5:02:13:24:9C
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=45/70 Signal level=-65 dBm
Encryption keyn
ESSID:"10FX08144752"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000001f24da183
Extra: Last beacon: 1340ms ago
IE: Unknown: 000C313046583038313434373532
IE: Unknown: 010882848B962430486C
IE: Unknown: 030106
IE: Unknown: 050401030000
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: Unknown: 32040C121860
IE: Unknown: DD090010180201F0000000
Cell 12 - Address: 00:21:29:B0:10:A7
Channel:9
Frequency:2.452 GHz (Channel 9)
Quality=46/70 Signal level=-64 dBm
Encryption keyn
ESSID:"camus"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000001f479e183
Extra: Last beacon: 672ms ago
IE: Unknown: 000563616D7573
IE: Unknown: 010882848B962430486C
IE: Unknown: 030109
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: Unknown: 32040C121860
IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1609001300000000000000000000000000000000000000
IE: Unknown: 7F0101
IE: Unknown: DD0E0050F204104A0001101044000102
IE: Unknown: DD090010180203F4010000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C3409001300000000000000000000000000000000000000
Cell 13 - Address: 00:26:F3:F9:EE:A9
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=42/70 Signal level=-68 dBm
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f18beb02
Extra: Last beacon: 2088ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050000000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05000036127A
IE: Unknown: DD07000C4300000000
Cell 14 - Address: 00:26:F3:F9:EE:AB
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=40/70 Signal level=-70 dBm
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Unknown/bug
Extra:tsf=00000001f18bfd05
Extra: Last beacon: 2084ms ago
IE: Unknown: 0000
IE: Unknown: 010882848B961224486C
IE: Unknown: 030101
IE: Unknown: 32040C183060
IE: Unknown: 0706555320010B14
IE: Unknown: 33082001020304050607
IE: Unknown: 33082105060708090A0B
IE: Unknown: 050400010000
IE: Unknown: 2A0104
IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
IE: Unknown: 3D1601050000000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: 0B05000036127A
IE: Unknown: DD07000C4300000000
Cell 15 - Address: E0:91:F5:C2:0B:A3
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=41/70 Signal level=-69 dBm
Encryption keyn
ESSID:"PAT119"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f13c4d80
Extra: Last beacon: 1696ms ago
IE: Unknown: 0006504154313139
IE: Unknown: 010882848B960C121824
IE: Unknown: 030103
IE: Unknown: 050401020000
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C34030D0800000000000000000000000000000000000000
IE: Unknown: 3D16030D0800000000000000000000000000000000000000
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD0E0050F204104A0001101044000102
Cell 16 - Address: E0:91:F5:BD:FC:EF
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=47/70 Signal level=-63 dBm
Encryption keyn
ESSID:"RyWorld"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000001f18a4d80
Extra: Last beacon: 1540ms ago
IE: Unknown: 00075279576F726C64
IE: Unknown: 010882848B968C129824
IE: Unknown: 030102
IE: Unknown: 050401020000
IE: Unknown: 0706555320010B1B
IE: Unknown: 2A0100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 3204B048606C
IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000
IE: Unknown: 3D16020D0800000000000000000000000000000000000000
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010002004000
IE: Unknown: DD270050F204104A00011010440001021047001000000000000010000000E091F5BDFCEF103C000103





dmesg | egrep 'rtl|firm'
[ 21.039669] phy0: hwaddr 00:17:c4:91:bc:70, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[ 21.062337] rtl8187: Customer ID is 0x00
[ 21.062470] Registered led device: rtl8187-phy0::tx
[ 21.062539] Registered led device: rtl8187-phy0::rx
[ 21.065079] rtl8187: wireless switch is on
[ 21.065185] usbcore: registered new interface driver rtl8187



lsmod | grep rtl
rtl8187 50680 0
mac80211 205402 1 rtl8187
led_class 2864 1 rtl8187
cfg80211 126144 2 rtl8187,mac80211
eeprom_93cx6 1333 1 rtl8187

---

### Post by wildmanne39 on 2011-09-09
Hi, your wireless card is scanning for networks, what is the name of the network you want to connect too, because there are many listed.

Also set your router encryption to wpa2 not mixed or wpa or wep.
Thank you

---

### Post by anewguy on 2011-09-09
+1 - ** THIS PART OF MY ORIGINAL POST IS INCORRECT - SO I REMOVED IT **

THE REST OF THE POST IS FINE:


Looks like it at least knows of the wireless now and it is indeed picking up many networks to choose from they way it looks.  I believe that even though the driver is now loaded via modules, it still wouldn't have worked without the udev rule as nothing was assigning the id to the adapter - wlan0 (which gets overriden and changed to wlan1 by the system).

I have a bunch of stuff to do for a while, so I'm going to be gone most of the time.  I'll leave you back in the very capable hands of wildmanne39 since he's been helping you from the start.  I kinda jumped in here in the middle and want to let you go back to dealing with just 1 person again as I know it makes things much easier to follow.

wildmanne39:  sorry to have jumped in - looks like things are at least working for the wireless.  I think the rest is as you have indicated - encryption, etc., but I don't know.  I'm going to kinda gracefully bow out and let the OP go back to dealing just with 1 user again as I know that makes things easier.  Again, sorry to have just jumped in, and we'll talk to you later my friend!

Dave ;)

---

### Post by nyx14850 on 2011-09-09
hi, how do i set the router encryption? what i would like to is to choose the wireless network i want to connect to from a list. it should automatically detect them and show them in an icon. for some reason i don't have such an icon. why would this be?
thanks.

---

### Post by wildmanne39 on 2011-09-09
Hi, run this command please and it will tell us if network manager is running.
```
ps aux | grep nm-apple
```
Type 192.168.0.1 into your address bar of your browser with your wired connection connected to your router and it should allow you to change your router settings.

Once in the router under wireless change security to just wpa2 only save and exit.

I still need need to know the name of the network you want to connect to so I can see if it shows up and what the encryption settings are.
Thank you

---

### Post by nyx14850 on 2011-09-09
Here is the output from ps aux | grep nm-apple


adam      2013  0.0  0.5  54000 11468 ?        S    18:19   0:02 nm-applet --sm-disable
adam      3648  0.0  0.0   3328   808 pts/0    S+   20:43   0:00 grep nm-apple


I don't think I have a router. I have high speed cable internet with a modem that connects directly to my netbook. My friend can however bring his laptop into my apartment and detect wireless networks or in a starbucks. He is running ubuntu and it just automatically detects the networks and there is an icon showing the strength of the connection and a list of networks available and he can choose one of them. That's what i want to do. 

thanks.

---

### Post by wildmanne39 on 2011-09-09
Hi, most cable modems have a built in wireless router, did you try to enter router setup as a recommended? Not all routers are accessed with the same numbers that I gave you.

Also here is a link that explains how to connect to an encrypted network with the driver that you use and others as well you will need to scroll down the page to find your driver.
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)
Thank you

---

### Post by nm_geo on 2011-09-09
Hi guys..

I would sure contact comcast and find about about if my router could assign me and IP  other than the one you showed. In fact if I were you nyx14850 I might do some editing on this thread Check your PM (private message) I sent you..

Good Job wildmanne 

I am Out.

---

### Post by anewguy on 2011-09-10
It's very important for anyone else reading this thread to realize 3 things if you have the same situation with the same adapter:

(1) You must add rtl8187 to the /etc/modules file
(2) You must add rtl8187b to the /etc/modprobe.d/blacklist.conf file
(3) You must be sure to add the special udev rule file in order for the adapter to be recognized and the driver assigned to it.

That will get the adapter itself working.

HOWEVER, it should be noted that in the newer kernels in 10.10 and in 11.04, the adapter should work "out of the box" without anything on your part.  I run a Trendnet USB adapter with the exact same chipset, etc., and in 10.10 it worked fine and in 11.04 it is working fine - both right out of the box.

The rest is as wildmanne39 is working with the OP now:  being sure they have network-manager installed, that they know what the icon looks like, that they have right-clicked on the network-manager icon to be sure enable wireless is checked as enabled, and that they (prior to 11.04) left-click to look for available networks (in 11.04, both the enable wireless and the available networks will show whether you left or right click).

You also have to know your router - what type of encryption, the passphrase/password key, if there is MAC filtering and you've never connected with the PC you must have your MAC address added to the router, etc., etc., etc..

wildmanne39 - it looks like the network manager aaplet is there - does the OP actually know where to look for it?  Perhaps they are not seeing it as *maybe* the friend they are comparing to has something like wicd instead of network manager.

Dave ;)

---

