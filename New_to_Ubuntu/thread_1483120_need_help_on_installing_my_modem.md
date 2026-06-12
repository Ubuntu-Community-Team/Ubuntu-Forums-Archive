---
title: "need help on installing my modem"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by rratnasara on 2010-05-14
Hello every one and I need some help on installing my modem. I'm from Sri-Lanka(asia, the small island underneath India) and over here we don't have advanced technologies to connect to Internet. I recently received a copy of UBUNTU 10.04 from canonical and I'm faced with a big problem. My modem is a USB modem and the driver only supports windows XP. This is the best modem delivered from the
one and only major internet service provider in Sri-Lanka. I asked the ISP whether they have support to ubuntu and the reply was "no". So I looked in the manufactures website and they didn't have any other versions beyond windows xp. I also did an extensive google search for modem drivers for ubuntu or any other linux distributions and couldn't find any thing. Since I'm dual booting xp and ubuntu on my computer I would like to get updates on my ubuntu. So I badly want to use internet inside UBUNTU and work with it. Therefore I need to know is there any possibility installing my xp driver on UBUNTU 10.04 with a third party software or some other way. Please let me know if there is a way to solve this problem. Thank you. 

MY LEVEL OF COMPUTER LITTERECY: I'm new to Ubuntu but, I'm a third year computer science student.

---

### Post by Bertus_Nel on 2010-05-14
Im new to Ubuntu aswell and I got mine to work by going to System - Network Connections then I click on the Mobile Broadband Tab. Then add your device, I assume you are talking about a Huawei?

---

### Post by rratnasara on 2010-05-14
> **Bertus_Nel said:**
> Im new to Ubuntu aswell and I got mine to work by going to System - Network Connections then I click on the Mobile Broadband Tab. Then add your device, I assume you are talking about a Huawei?
I've heard about this brand but mine is PROLINK and it's an ADSL USB MODEM. Also is not a mobile broadband router. Anyway thank you for the information Bertus_Nel.

---

### Post by rratnasara on 2010-05-14
This is the link to my modem [http://www.fida.com/products/H8600.htm]("http://www.fida.com/products/H8600.htm") .

Also one more thing that I should mention is that when I plug in the modem the power indicator doesn't light up. Basically when I plug in the modem to Ubuntu 10.04 the modem doesn't show that it's powered on. Is there any option inside Ubuntu 10.04 that I need to turn on so that power goes to the Modem so that at least I know Ubuntu recognizes my modem. So that I can go to next step finding proper drivers for Ubuntu if there is any way thanks to the community. Thank you.

---

### Post by lkraemer on 2010-05-14
Boot into Ubuntu, without the USB Modem installed.  Open a Terminal
Window and Copy & Paste the following commands.  Then post the output here.
```

lsusb

```
Copy the output to a text file opened with gedit. Then plug in the USB
Modem, and wait a minute or two.  Repeat the command in the Terminal
Window.
```

lsusb

```
Hopefully, Ubuntu will find the USB Modem.
Post that output.

We'll go from there.  There should be a difference in the outputs
if the USB Modem is found.

Are you going to be using Dialup?   If so, you may need to download
wvdial and the dependencies.  I'll check on that.

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy to USB Flash Drive & then to Ubuntu.

But you say it is ADSL, so maybe this will get you going:
[http://www.linuxquestions.org/questions/linux-hardware-18/how-to-install-prolink-h9601-adsl-usb-modem-in-ubuntu-724373/](http://www.linuxquestions.org/questions/linux-hardware-18/how-to-install-prolink-h9601-adsl-usb-modem-in-ubuntu-724373/)
or
[http://ubuntuforums.org/showthread.php?t=47910](http://ubuntuforums.org/showthread.php?t=47910)

Ubuntu 10.04, but ...... 32 Bit or 64 Bit??

lk

---

### Post by rratnasara on 2010-05-14
First of all thanks to lkraemer for your support.  

I did follow your steps with lsusb command and these are the output and yes it did show a variation.

before

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ramiboi@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

After
ramiboi@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0483:0137 SGS Thomson Microelectronics BeWAN ADSL USB ST (blue or green)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ramiboi@ubuntu:~$ 

So i think Ubuntu understood the modem although it doesn't physically show it. By the way the Chicony Electronics Co., Ltd is my webcam. 

Although the speeds are ADSL , sadly the technology still used is dial up. I'm not using any Ethernet cable to connect to the computer in order to receive ADSL connection as other developed countries do so.  

Also it's Ubuntu 10.04 32 bit version.(My fault, I should have mentioned this in my first post, sorry! by the way this is my first ever forum post online. Please excuse my faults.)

I understand the things in the two forum links that you have posted and I should mention that, in windows once I install the driver the specific ISP dependent values should be entered. Such as VCI value ,VPI value and selection between PPPoA VCMUX and PPPoE LLC. So there is specific profile for Sri-Lankan users to install so that we are able to connect to the internet. I also have link to the manual of my modem [http://www.prolink2u.com/downloads/pdf/manuals/manual_h8700.pdf]("http://www.prolink2u.com/downloads/pdf/manuals/manual_h8700.pdf")

Once again thank you lkraemer and to the community for the help.

---

### Post by rratnasara on 2010-05-14
One more thing lkraemer,
Since it's dial up it is I believe I should download wvdial and it's dependencies. But when I went to the webpage of wvdial it lists more dependencies than you listed. 

> "wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base"

And when I went to those dependency web pages and they had sub dependencies. I'm bit confused whether to download all of them or does some of them all ready included in Ubuntu 10.04. Also how am I suppose to know that relevant dependencies are already installed or not?

I think I should wait for a reply from you before I start downloading the wvdial and it's dependencies. Thank you again.

---

### Post by lkraemer on 2010-05-15
I checked my installed Ubuntu 10.04 for what would be needed to install
wvdial.  So, if the others wern't marked, I assumed they were already installed.
You can use Synaptics to verify each one, but it's probably
going to be easier to just download these to start with and go from there.
After wvdial in installed and working we will install Gnome-ppp and set it
up and you can use it from the Desktop GUI, which will make life easy.

I'll read the modem manual tomorrow morning and start posting more details
on what will be needed next.

You will need the Windows XP 32 Bit drivers for the Modem.  You should have a CDR
with the unit, or be able to download the latest ones from an online
site.  That will give you something to do until I get back tomorrow morning.

Go ahead and copy the wvdial files to the ubuntu machine, and well move them also
so Synaptic can locate them and install.



Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. You MUST use the
Proper Windows drivers for 32 or 64 Bit to match the 32 or 64 Bit
Version of Ubuntu. You need the .inf and .sys files.......

Use copy & paste to prevent typos!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf 

```
Post the output of each command listed above ........

Your options that can be used:
1. Ndiswrapper and a Windows Driver....????.inf & sys

STOP here until we have more information.......


More later after you post the output from the above.

lk

---

### Post by lkraemer on 2010-05-15
Information merged with later posting.

---

### Post by pdc on 2010-05-15
hi rratnasara;  lkraemer is doing a great job of guiding your through this;

you commented 

> So i think Ubuntu understood the modem **although it doesn't physically show it**.

I would suggest your lsusb command DID show it

> Bus 003 Device 004: ID 0483:0137 SGS Thomson Microelectronics BeWAN ADSL USB ST (blue or green)

and if you google on that ID 

> ubuntu 0483:0137

you get some posts

including this one

[http://translate.google.co.nz/translate?hl=en&sl=it&u=http://wiki.ubuntu-it.org/Hardware/Modem/Adsl/FastrateUsb100&ei=8yPuS7KHI5Lo7APjnImYBg&sa=X&oi=translate&ct=result&resnum=6&ved=0CDAQ7gEwBQ&prev=/search%3Fq%3Dubuntu%2B0483:0137%26hl%3Den](http://translate.google.co.nz/translate?hl=en&sl=it&u=http://wiki.ubuntu-it.org/Hardware/Modem/Adsl/FastrateUsb100&ei=8yPuS7KHI5Lo7APjnImYBg&sa=X&oi=translate&ct=result&resnum=6&ved=0CDAQ7gEwBQ&prev=/search%3Fq%3Dubuntu%2B0483:0137%26hl%3Den)

this, admittedly old, guide says

> Download and save to ~ / the latest drivers available by clicking here .

> A1012-A1006-A904-A888-A983-0.9.3.tgz

this seemed to be the .tgz that was recommended; I am not sure if it is still relevant to the installation of this device

some guides

[http://huw.org.uk/pages/misc/bewan-adsl-pcist.php](http://huw.org.uk/pages/misc/bewan-adsl-pcist.php)

but they talk of older kernels

lkraemer will guide you

---

### Post by rratnasara on 2010-05-15
Yes you were absolutely right I needed just exactly what you mentioned and I installed wvdial successfully. Also I have the modem driver for the 32 bit Windows XP. I slowly understand what synaptic package manager does and it's quite awesome compared to windows systems. Also it's quite awesome how you guided me looking at your computer and I know why you asked me to install wvdial before moving to gnome ppp. As I'm also trying to be computer science graduate Linux has impressed me a lot compared to the versatility given from Microsoft. So I'll try to install gnome ppp and we might be able to start at least one step ahead by the time you are up tomorrow(which will cause you less trouble at least). Once again thank you lkraemer for your immense help and do really appreciate your guidance.

---

### Post by rratnasara on 2010-05-15
> **lkraemer said:**
> I checked my installed Ubuntu 10.04 for what would be needed to install
wvdial.  So, if the others wern't marked, I assumed they were already installed.
You can use Synaptics to verify each one, but it's probably
going to be easier to just download these to start with and go from there.
After wvdial in installed and working we will install Gnome-ppp and set it
up and you can use it from the Desktop GUI, which will make life easy.

I'll read the modem manual tomorrow morning and start posting more details
on what will be needed next.

You will need the Windows XP 32 Bit drivers for the Modem.  You should have a CDR
with the unit, or be able to download the latest ones from an online
site.  That will give you something to do until I get back tomorrow morning.

Go ahead and copy the wvdial files to the ubuntu machine, and well move them also
so Synaptic can locate them and install.



Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. You MUST use the
Proper Windows drivers for 32 or 64 Bit to match the 32 or 64 Bit
Version of Ubuntu. You need the .inf and .sys files.......

Use copy & paste to prevent typos!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf 

```
Post the output of each command listed above ........

Your options that can be used:
1. Ndiswrapper and a Windows Driver....????.inf & sys

STOP here until we have more information.......


More later after you post the output from the above.

lk
As you requested here are the outputs of the code that you requested. 

ramiboi@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

ramiboi@ubuntu:~$ lsusb
Bus 006 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:0137 SGS Thomson Microelectronics BeWAN ADSL USB ST (blue or green)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ramiboi@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:68:b5:19:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:b3:c2:d9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f0400000-f0403fff ioport:a000(size=256)


ramiboi@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
usb_storage            39425  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_conexant    22577  1 
arc4                    1153  2 
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
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
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121792  0 
radeon                674135  3 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
ttm                    49943  1 radeon
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126485  3 ath5k,mac80211,ath
drm_kms_helper         29297  1 radeon
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162471  5 radeon,ttm,drm_kms_helper
i2c_piix4               8335  0 
led_class               2864  2 ath5k,sdhci
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
psmouse                63245  0 
serio_raw               3978  0 
shpchp                 28820  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  1 lp
usbhid                 36110  0 
ohci1394               26950  0 
hid                    67032  1 usbhid
ieee1394               81181  1 ohci1394
pata_atiixp             3148  1 
ahci                   32008  1 
sky2                   40775  0


although ndiswrapper wasn't installed I was quickly able to install it using the package search and synaptic package manager.

but the ndiswrapper -l did not produce any output and then I went to the last step and outputs are here.  

ramiboi@ubuntu:~$ ndiswrapper -l
ramiboi@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
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
ramiboi@ubuntu:~$

---

### Post by rratnasara on 2010-05-15
> **lkraemer said:**
> I checked my installed Ubuntu 10.04 for what would be needed to install
wvdial.  So, if the others wern't marked, I assumed they were already installed.
You can use Synaptics to verify each one, but it's probably
going to be easier to just download these to start with and go from there.
After wvdial in installed and working we will install Gnome-ppp and set it
up and you can use it from the Desktop GUI, which will make life easy.

I'll read the modem manual tomorrow morning and start posting more details
on what will be needed next.

You will need the Windows XP 32 Bit drivers for the Modem.  You should have a CDR
with the unit, or be able to download the latest ones from an online
site.  That will give you something to do until I get back tomorrow morning.

Go ahead and copy the wvdial files to the ubuntu machine, and well move them also
so Synaptic can locate them and install.



Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. You MUST use the
Proper Windows drivers for 32 or 64 Bit to match the 32 or 64 Bit
Version of Ubuntu. You need the .inf and .sys files.......

Use copy & paste to prevent typos!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf 

```
Post the output of each command listed above ........

Your options that can be used:
1. Ndiswrapper and a Windows Driver....????.inf & sys

STOP here until we have more information.......


More later after you post the output from the above.

lk
You mentioned that 
> You need the .inf and .sys files.......

The windows driver contains a lot of files and bit confused what exactly I need as a .inf file or a .sys file. If you don't mind you can take a look at the files available in the driver for Hurricane 8600 in this webpage [http://www.fida.com/download-dc.htm]("http://www.fida.com/download-dc.htm"). This zip file is 10 Mb and If you feel like you can take a look inside and see what files I need during the installation. 

I will try to give you a preview of the files inside the driver for Hurricane 8600 if you don't feel like downloading.

[IMG]http://www.glowfoto.com/static_image/15-003233L/1648/jpg/05/2010/img6/glowfoto[/IMG]

[IMG]http://www.glowfoto.com/static_image/15-020754L/3406/jpg/05/2010/img4/glowfoto[/IMG]


just in case if the photos cannot be viewed these are the direct links 

pic1[http://www.glowfoto.com/viewimage.php?img=15-003233L&rand=1648&t=jpg&m=05&y=2010&srv=img6]("http://www.glowfoto.com/viewimage.php?img=15-003233L&rand=1648&t=jpg&m=05&y=2010&srv=img6")

pic2[http://www.glowfoto.com/viewimage.php?img=15-020754L&rand=3406&t=jpg&m=05&y=2010&srv=img4]("http://www.glowfoto.com/viewimage.php?img=15-020754L&rand=3406&t=jpg&m=05&y=2010&srv=img4")


Also I'm not sure what you mean over here

> Your options that can be used:
1. Ndiswrapper and a Windows Driver....????.inf & sys

Please try to explain. I don't know how to thank you for all the support and for the valuable time that you are spending for my task. Thanks again.

---

### Post by ssj6akshat on 2010-05-15
I found Linux Drivers for your device

[http://driverscollection.com/?H=ADSL%20PCI%20%26%20USB%20ST&By=BeWAN&SS=Linux](http://driverscollection.com/?H=ADSL%20PCI%20%26%20USB%20ST&By=BeWAN&SS=Linux)

It says kernel 2.6.14 or newer.The kernel in Lucid is 2.6.32 I believe

---

### Post by rratnasara on 2010-05-15
> **ssj6akshat said:**
> I found Linux Drivers for your device

[http://driverscollection.com/?H=ADSL%20PCI%20%26%20USB%20ST&By=BeWAN&SS=Linux](http://driverscollection.com/?H=ADSL%20PCI%20%26%20USB%20ST&By=BeWAN&SS=Linux)

It says kernel 2.6.14 or newer.The kernel in Lucid is 2.6.32 I believe
Thank You for the info ssj6akshat, But do you have any idea of installing it in Ubuntu because I'm new to this. 

Also many thanks to pdc's valuable info.

---

### Post by lkraemer on 2010-05-15
OK, A couple of answers and information for you before we proceed.

Your loaded modules shows that you have the Atheros Wifi Hardware
and that the ath5k module is already loaded.  You aren't going to
be using it right now, but when you are in an area where there are
Wifi Wireless Networks, you should be able to see them and connect
if they are not protected with WEP or WPA.  The Atheros Wifi drivers
will work correctly with Ubuntu 10.04 installs.  So, that is good
information to know for the future.

For ndiswrapper and ndiswrapper -l, those commands were included in my
set of GENERIC commands so I get information on your system, and some
things might or might not be installed or loaded, but I have no way of
knowing what you have or have not done before posting on the forum.
So, with that data you post I can have a preview if you have already
loaded some driver with ndiswrapper and didn't say anything about it,
or just forgot.  So, there is also less chance of conflicts, which
would cause things to not work properly.

As for the:
Your options that can be used:
1. Ndiswrapper and a Windows Driver....????.inf & sys

This was just some text of a previous post where I was helping folks
install B43 and BCM43xx where there were three options.  It was to be
their choice of what drivers to use.  I probably should have also cut
those lines out of the post to make it less confusing....but I didn't.

Also, from the things already Blacklisted, I think we are OK there and
can skip that part, unless we find something as we proceed 

**SET UP PAP/CHAP**
 
Locate your userlogin, password, Dialup Provider Info, Phone Number,
and what your ISP uses (PAP or CHAP)

Open a Terminal Window and run the following:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically, you just answer the questions
that are presented. You can delete a configuration and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password
"yourusername" provider "yourpassword"

```
And the file is located at:
```

/etc/ppp/pap-secrets

```
Use pppconfig to create a modified file or edit the file with:
```

sudo nano /etc/ppp/pap-secrets

```


[B]Install the Latest Drivers with ndiswrapper:
[/B]

You are going to have to go into XP and locate the Drivers name
by going to Control Panel >> System >> Hardware >> Device Manager >> Network Adapter
and selecting Prolink H8600 ADSL USB.  You are going to need the
xxxx.sys and xxxx.inf files.  Once you find the name search your
hard drive for those files until you locate them.  I have no
way to locate the drivers because I need the ADSL Modem to
plug into my computer to finish the driver install........

Create a Folder/subdirectory at your /home/user named Prolink
Copy the files you located in XP there.  (You can try update driver
in XP to see if there are any later versions available.)

To install the Windows Drivers you will do something like this:
```

cd ~/Prolink
sudo ndiswrapper -i xxxx.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod

```
The lsmod listing will make 100% sure ndiswrapper is installed.

To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
[B]
REMOVE WINDOWS DRIVERS & NDISWRAPPER .......IF NEEDED:[/B]

If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. If memory serves me correctly the command is:
```

sudo ndiswrapper -e xxxx

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

Open a Terminal & Check for errors:
```

dmesg tail
lsmod

```
[B]
YOU SHOULD BE GOOD HERE:  SKIP TO SETUP WVDIAL BELOW:[/B]
[B]
REMOVE MODULES or BLACKLIST MODULES:[/B]
You may have to remove other modules depending on what lsmod shows:......example only.....
What you will REMOVE depends on what you post as output from your commands.

**EXAMPLE ONLY:**
If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using ndiswrapper.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo nano /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.


**SETUP WVDIAL:**

Now ppp is setup and the Drivers are loaded, you will need to set up wvdial. 

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file that is something like this,
but your modem and some of your parameters may be slightly different
depending on what wvdial detects.
Your PhoneNumber, LoginName, and PassWord will be what you use.
The Modem type ....as in Modem = /dev/ttyACM0 should be determined
by wvdial......hopefully.....
```

sudo nano /etc/wvdial.conf (you may need to edit/add/modify a few things...)

```
wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings, and the 
information provided by pradeepthundiyil in a later posting may apply.
You will need to adjust these as per your testing, then from your feedback
I'll update this guide, so others have good information.
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
If wvdial gives you an error try:
```

sudo wvdial /etc/wvdial.conf

``` 
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny
characters) and then you should stay connected. [B](you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN.....just minimize it)  You may have to uncheck
the box marked OFFLINE when you open your browser to make it online.[/B]
Surf, then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

If your configuration is wrong, it will disconnect in a few seconds because
it won't be able to authenticate properly......

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)

MORE REF's:
[http://www.ubuntugeek.com/setting-up...in-ubuntu.html](http://www.ubuntugeek.com/setting-up...in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/Di...to/SetUpDialer](https://help.ubuntu.com/community/Di...to/SetUpDialer)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

wvdial info:
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5](http://www.squarebox.co.uk/cgi-squar.../wvdial.conf.5)

Finally, when wvdial is working you can Download & Install
Gnome-PPP and then configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

Attached are my three Setup snapshots of Gnome-PPP....if they are of
any help. 

lk

---

### Post by rratnasara on 2010-05-15
Good Morning lkraemer

I have a quick question should I install gnomeppp before we proceed?

---

### Post by rratnasara on 2010-05-15
okay now I'm bit confused with pppconfig because it requests some information that I don't know.

To be honest the ISP doesn't give us any of the info. In windows xp once we install the adsl modem we have to reinstall the Sri-lankan profile on top of the generic profile to set the proper values related to our ISP. There fore much of this information is not visible. On the other hand it setup creates the dialup connection and all we need to enter the username and password provided from the ISP.

The computer literacy is so low that when I ask a question like that from the customer service they go nuts. So what should I do to figure out the required info to enter in the pppconfig.

Also I think i should mention that I have a fresh copy of 10.04 installed and I only installed wvdial and ndiswrapper so far.

---

### Post by lkraemer on 2010-05-15
Well, if you can install Gnome-PPP, I'd say yes.  There isn't any reason not to.

I'm kinda stuck, because I now need the name of your driver that is
installed in XP.  So, next step is for you to try and locate that name.
The only way I have to locate it is to run VirtualBox, run XP inside
VirtualBox, Install the Drivers, and then search for it.  But you
already have them installed and you should be able to locate the
proper one.  Once you find the name search your hard drive for the
sys & inf file locations.  Then copy them to a USB Flash Drive and
copy them to a Prolink folder/subdirectory under your /home/username
in Ubuntu.

I'm still refining my posting.......but, I'm about finished as far as I
know.

Next step is for you to start down the procedure and see how it goes.
If you have questions post.

I looked over the modem manual, and looked at the Driver file.

[B]For pppconfig, if you aren't sure just leave the default, but try PAP
first.  Insert Phone Number, Username, and Password.  Save the file and exit.[/B]

lk

---

### Post by pradeepthundiyil on 2010-05-15
hi,

To all those who have problems with connecting datacard.. I had issues  in connecting my datacard. I could solve it through the suggestions in  forum.. I dont use Windows anymore.. I love ubuntu..

Follow the steps and reboot..


The on going saga of the Network Manager failing to return the NS1 and  NS2
IE the modem connects but the Browser and updates etc fail to connect

Here I have change the IPCP configure-NAKs returned before starting ,  remove the # and set the number to 30 ( or any thing above the default  value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP)  instead of Setting the NM to IPv4 settings to Automatic (PPP) address  only and having to enter the numerical addresses in the DNS servers text  box.

I will be monitoring the outcome of this change.


Also try this from a recent post / but also has roots from the past /  please read the thread


[http://ubuntuforums.org/showthread.php?t=1426409](http://ubuntuforums.org/showthread.php?t=1426409)




Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute

if this is done then replace the # in front of the

replace the # in front of the " ipcp-max-failure 30 " do not use both  lines


also the replacedefaulte has failed a few times after a fresh boot , but  has proved quite successful


#reboot
 		                   		  		  		  		  		 		 			 				 				* 					 						 					 				*

---

