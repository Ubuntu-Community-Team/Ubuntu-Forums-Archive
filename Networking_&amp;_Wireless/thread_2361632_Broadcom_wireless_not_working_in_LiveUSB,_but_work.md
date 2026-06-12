---
title: "Broadcom wireless not working in LiveUSB, but works in Windows XP"
date: 2017-05-18
forum: Networking &amp; Wireless
---

### Post by ardouronerous on 2017-05-18
I'm attempting to use a Lubuntu 16.04 LiveUSB with my old Windows XP laptop, a Dell Inspiron E1505.

In the Additional Drivers section, Broadcom wireless, it says device is not working and when I attempt to use the proprietary driver, it fails, but when I log on to Windows XP, the device is working.

Any chance I can fix this issue so I can use the Internet in my LiveUSB?

Unfortunately, I have no access to a physical connection at the moment.

---

### Post by QIII on 2017-05-18
Hello!

Just as a side note ... were you aware that you can actually *install* Lubuntu on a USB device?

---

### Post by ardouronerous on 2017-05-18
Hello, thanks for the reply. I heard creating a persistent USB will break the USB, is that true?

---

### Post by QIII on 2017-05-18
Where did you hear that?

I'm not even talking about a "persistent" USB.  I'm talking about a full-blown, real-deal installation.

If you have your LiveUSB and a spare USB thumb drive (8GB at least -- which is barely enough, 32GB+ is better), you can even temporarily take the Windows drive out of the computer and install Lubuntu without worrying about messing up your Windows installation.  You can install necessary drivers and all.

This pre-supposes that your laptop allows booting from USB.

---

### Post by ardouronerous on 2017-05-18
I do have two 8GB USBs, one I'm using as a LiveUSB for Lubuntu and one I'm keeping as a spare. My laptop did boot from the LiveUSB.

---

### Post by QIII on 2017-05-18
OK.  8GB is barely, barely enough for an installation and leaves you very little for any breathing room.

I'm assuming this laptop has USB 2.0, not USB 3.0, correct?  A 32GB USB2 thumb drive can be had for $15.  I don't want to spend your money, but is that something you might afford?  USB 2.0 will not make your machine a speed demon, but it will definitely work suitably with Lubuntu.

I have run several "single board computers" on USB drives with great success.   I actually used one as a web development platform and server for a few years.

---

### Post by wildmanne39 on 2017-05-18
I can help with the wifi but on a live install every time you reboot you will have to install the drivers again. So install ubuntu to your usb drive then we can get the wifi going most likely.

---

### Post by ardouronerous on 2017-05-18
> **QIII said:**
> OK.  8GB is barely, barely enough for an installation and leaves you very little for any breathing room.

I'm assuming this laptop has USB 2.0, not USB 3.0, correct?  A 32GB USB2 thumb drive can be had for $15.  I don't want to spend your money, but is that something you might afford?  USB 2.0 will not make your machine a speed demon, but it will definitely work suitably with Lubuntu.

I have run several "single board computers" on USB drives with great success.   I actually used one as a web development platform and server for a few years.

Thanks for the info. But for now, I want to stick to using LiveUSB first.

> **wildmanne39 said:**
> I can help with the wifi but on a live  install every time you reboot you will have to install the drivers  again. So install ubuntu to your usb drive then we can get the wifi  going most likely.

How do I install the drivers on LiveUSB? I'm willing to start from scratch on reboot.

---

### Post by wildmanne39 on 2017-05-18
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by ardouronerous on 2017-05-18
Here you go:

```
lsmodlubuntu@lubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
Linux lubuntu 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:41 UTC 2017 i686 i686 i686 GNU/Linux
lubuntu@lubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
lubuntu@lubuntu:~$ lsusb
Bus 001 Device 003: ID 0950:1664  
Bus 001 Device 004: ID 0950:1664  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0101:0007  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lubuntu@lubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

lubuntu@lubuntu:~$ rfkill list all
lubuntu@lubuntu:~$ lsmod
Module                  Size  Used by
dell_laptop            20480  0
b43                   397312  0
dell_smbios            16384  1 dell_laptop
gpio_ich               16384  0
dcdbas                 16384  1 dell_smbios
dell_smm_hwmon         16384  0
bcma                   53248  1 b43
snd_hda_codec_hdmi     45056  1
r852                   20480  0
mac80211              679936  1 b43
snd_hda_codec_idt      53248  1
sm_common              16384  1 r852
zram                   24576  2
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_intel          32768  1
joydev                 20480  0
input_leds             16384  0
nand                   57344  2 r852,sm_common
coretemp               16384  0
nand_ecc               16384  1 nand
r592                   20480  0
nand_bch               16384  1 nand
bch                    20480  1 nand_bch
snd_hda_codec         118784  4 snd_hda_intel,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
serio_raw              16384  0
nand_ids               12288  1 nand
snd_hda_core           69632  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
mtd                    61440  3 nand_bch,sm_common,nand
lpc_ich                20480  0
memstick               16384  1 r592
cfg80211              512000  2 b43,mac80211
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
ssb_hcd                16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    69632  13 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm
soundcore              16384  1 snd
mac_hid                16384  0
shpchp                 32768  0
autofs4                40960  2
aufs                  212992  2068
nls_utf8               16384  1
isofs                  40960  1
nls_iso8859_1          16384  1
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
hid_generic            16384  0
i915                 1245184  4
b44                    36864  0
uas                    20480  0
firewire_ohci          36864  0
usb_storage            57344  3 uas
psmouse               122880  0
i2c_algo_bit           16384  1 i915
sdhci_pci              24576  0
firewire_core          65536  1 firewire_ohci
drm_kms_helper        151552  1 i915
sdhci                  45056  1 sdhci_pci
pata_acpi              16384  0
crc_itu_t              16384  1 firewire_core
syscopyarea            16384  1 drm_kms_helper
mii                    16384  1 b44
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  6 i915,drm_kms_helper
video                  36864  2 dell_laptop,i915
ssb                    57344  3 b43,ssb_hcd,b44
usbhid                 49152  0
hid                    98304  2 hid_generic,usbhid
```

---

### Post by wildmanne39 on 2017-05-18
Download the b43 zip file using a computer with internet to an usb drive then drag and drop the file to your lubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:

Please copy and paste for accuracy.
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -rv b43
sudo modprobe -rv ssb
sudo modprobe -v b43

```
if you encounter any errors continue to the next step until all is complete.

Sometimes a reboot is required but not usually, lets hope not in your case.

---

### Post by ardouronerous on 2017-05-18
Didn't work.

Here's the results:

```
lubuntu@lubuntu:~$ sudo mkdir /lib/firmware/b43
lubuntu@lubuntu:~$ sudo cp Desktop/b43/* /lib/firmware/b43
lubuntu@lubuntu:~$ sudo modprobe -rv b43
rmmod b43
rmmod mac80211
rmmod cfg80211
rmmod bcma
lubuntu@lubuntu:~$ sudo modprobe -rv ssb
modprobe: FATAL: Module ssb is in use.
lubuntu@lubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko 
```

---

### Post by wildmanne39 on 2017-05-19
All went well, this:
> sudo modprobe -rv ssb
modprobe: FATAL: Module ssb is in use.
happens a lot and in your case is caused be the fact that your ethernet connection uses it as well as your wifi device, which is pretty rare these days, but we are dealing with an old computer.

You sure your ethernet connection is not working? it should be.

This old computer also has one other issue and lets see if that is causing the problem, please do:
```
sudo modprobe -rv dell_laptop
```
It should come on, make sure the physical switch is on.
Thanks

---

### Post by ardouronerous on 2017-05-19
Didn't work, maybe it does need a reboot.
Here's the results:
```
lubuntu@lubuntu:~$ sudo mkdir /lib/firmware/b43
lubuntu@lubuntu:~$ sudo cp Desktop/b43/* /lib/firmware/b43
lubuntu@lubuntu:~$ sudo modprobe -rv b43
rmmod b43
rmmod mac80211
rmmod cfg80211
rmmod bcma
lubuntu@lubuntu:~$ sudo modprobe -rv ssb
modprobe: FATAL: Module ssb is in use.
lubuntu@lubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko 
lubuntu@lubuntu:~$ sudo modprobe -rv dell_laptop
rmmod dell_laptop
rmmod dell_smbios
rmmod dcdbas
```

Yes, the ethernet does work on the laptop, however, the modem and router is on the third floor of the house, so it's kinda of a hassle to carry the laptop all the way to the 3rd floor.

---

### Post by wildmanne39 on 2017-05-19
Post the output of:
```
ls -al /lib/firmware/b43
sudo cat /var/log/syslog | grep -e b43 -e firmware | tail -n25
```
Thanks

---

### Post by wildmanne39 on 2017-05-19
*Thread moved to **Networking & Wireless**.*

---

### Post by ardouronerous on 2017-05-19
Here you go:
```
lubuntu@lubuntu:~$ sudo mkdir /lib/firmware/b43
lubuntu@lubuntu:~$ sudo cp Desktop/b43/* /lib/firmware/b43
lubuntu@lubuntu:~$ sudo modprobe -rv b43
rmmod b43
rmmod mac80211
rmmod cfg80211
rmmod bcma
lubuntu@lubuntu:~$ sudo modprobe -rv ssb
modprobe: FATAL: Module ssb is in use.
lubuntu@lubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko 
lubuntu@lubuntu:~$ ls -al /lib/firmware/b43
total 284
drwxr-xr-x  2 root root   680 May 19 13:16 .
drwxr-xr-x 72 root root    60 May 19 13:16 ..
-rw-r--r--  1 root root   158 May 19 13:16 a0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 May 19 13:16 a0g0bsinitvals9.fw
-rw-r--r--  1 root root  1840 May 19 13:16 a0g0initvals5.fw
-rw-r--r--  1 root root  2002 May 19 13:16 a0g0initvals9.fw
-rw-r--r--  1 root root   158 May 19 13:16 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 May 19 13:16 a0g1bsinitvals5.fw
-rw-r--r--  1 root root   158 May 19 13:16 a0g1bsinitvals9.fw
-rw-r--r--  1 root root  2080 May 19 13:16 a0g1initvals13.fw
-rw-r--r--  1 root root  1840 May 19 13:16 a0g1initvals5.fw
-rw-r--r--  1 root root  2002 May 19 13:16 a0g1initvals9.fw
-rw-r--r--  1 root root   158 May 19 13:16 b0g0bsinitvals13.fw
-rw-r--r--  1 root root   158 May 19 13:16 b0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 May 19 13:16 b0g0bsinitvals9.fw
-rw-r--r--  1 root root  2080 May 19 13:16 b0g0initvals13.fw
-rw-r--r--  1 root root  1840 May 19 13:16 b0g0initvals5.fw
-rw-r--r--  1 root root  2002 May 19 13:16 b0g0initvals9.fw
-rw-r--r--  1 root root   158 May 19 13:16 lp0bsinitvals13.fw
-rw-r--r--  1 root root   158 May 19 13:16 lp0bsinitvals14.fw
-rw-r--r--  1 root root   158 May 19 13:16 lp0bsinitvals15.fw
-rw-r--r--  1 root root  3618 May 19 13:16 lp0initvals13.fw
-rw-r--r--  1 root root  2064 May 19 13:16 lp0initvals14.fw
-rw-r--r--  1 root root  2052 May 19 13:16 lp0initvals15.fw
-rw-r--r--  1 root root   158 May 19 13:16 n0absinitvals11.fw
-rw-r--r--  1 root root   158 May 19 13:16 n0bsinitvals11.fw
-rw-r--r--  1 root root  2100 May 19 13:16 n0initvals11.fw
-rw-r--r--  1 root root  1320 May 19 13:16 pcm5.fw
-rw-r--r--  1 root root 29864 May 19 13:16 ucode11.fw
-rw-r--r--  1 root root 32232 May 19 13:16 ucode13.fw
-rw-r--r--  1 root root 31384 May 19 13:16 ucode14.fw
-rw-r--r--  1 root root 30488 May 19 13:16 ucode15.fw
-rw-r--r--  1 root root 22384 May 19 13:16 ucode5.fw
-rw-r--r--  1 root root 25160 May 19 13:16 ucode9.fw
lubuntu@lubuntu:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware | tail -n25
May 19 13:14:37 lubuntu NetworkManager[1197]: <info>  [1495199677.7850] manager[0x9bb78e8]: monitoring kernel firmware directory '/lib/firmware'.
May 19 13:14:38 lubuntu kernel: [   27.759122] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
May 19 13:14:38 lubuntu kernel: [   27.835097] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
May 19 13:14:38 lubuntu kernel: [   27.835118] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
May 19 13:14:38 lubuntu kernel: [   27.875963] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
May 19 13:14:38 lubuntu kernel: [   27.876075] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
May 19 13:14:38 lubuntu kernel: [   27.876732] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
May 19 13:14:38 lubuntu kernel: [   27.876768] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
May 19 13:14:38 lubuntu kernel: [   27.876772] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
May 19 13:14:38 lubuntu kernel: [   27.876845] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
May 19 13:14:38 lubuntu kernel: [   27.876914] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
May 19 13:15:29 lubuntu ureadahead[1017]: ureadahead:/lib/udev/rules.d/50-firmware.rules: Error retrieving chunk extents: Operation not supported
May 19 13:15:29 lubuntu ureadahead[1017]: ureadahead:/lib/modules/4.8.0-36-generic/kernel/drivers/firmware/dcdbas.ko: Error retrieving chunk extents: Operation not supported
May 19 13:15:29 lubuntu ureadahead[1017]: ureadahead:/lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko: Error retrieving chunk extents: Operation not supported
May 19 13:15:29 lubuntu ureadahead[1017]: ureadahead:/var/cache/fontconfig/fe547fea3a41b43a38975d292a2b19c7-le32d4.cache-6: Error retrieving chunk extents: Operation not supported
May 19 13:16:46 lubuntu NetworkManager[1197]: <info>  [1495199806.6014] manager: kernel firmware directory '/lib/firmware' changed
May 19 13:17:23 lubuntu kernel: [  193.325035] b43-wlan ERROR: Dual-core devices are not supported
May 19 13:17:23 lubuntu kernel: [  193.325047] b43: probe of ssb0:0 failed with error -524
```

---

### Post by wildmanne39 on 2017-05-19
The firmware is in the file but it is not loading, lets try to remove that module another way since we can not reboot, please do:
```
sudo modprobe -rv dell_laptop
sudo modprobe -rv b43
sudo modprobe -rv b44
sudo modprobe -rv ssb
sudo modprobe -v b44
sudo modprobe -v b43
```
Does it come on?

---

### Post by ardouronerous on 2017-05-19
Doesn't work, here's the result;

```
lubuntu@lubuntu:~$ sudo mkdir /lib/firmware/b43
lubuntu@lubuntu:~$ sudo cp Desktop/b43/* /lib/firmware/b43
lubuntu@lubuntu:~$ sudo modprobe -rv dell_laptop
rmmod dell_laptop
rmmod dell_smbios
rmmod dcdbas
lubuntu@lubuntu:~$ sudo modprobe -rv b43
rmmod b43
rmmod mac80211
rmmod cfg80211
rmmod bcma
lubuntu@lubuntu:~$ sudo modprobe -rv b44
rmmod b44
rmmod mii
lubuntu@lubuntu:~$ sudo modprobe -rv ssb
modprobe: FATAL: Module ssb is in use.
lubuntu@lubuntu:~$ sudo modprobe -v b44
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/ethernet/broadcom/b44.ko 
lubuntu@lubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
```

---

### Post by wildmanne39 on 2017-05-19
Thats all I know to do, I am sure if you could reboot, it would work.

I have used this method for 6 years and several other people too, and it almost always works.

---

### Post by ardouronerous on 2017-05-19
Thanks for the assist then, I really appreciate it :)

---

### Post by wildmanne39 on 2017-05-19
Your very welcome, it is possible someone else will jump in and have an alternative, but it is late here and I just can not think of one tonight, I will think more about it tomorrow.

I have installed Ubuntu on an usb drive before and it worked great and I took it with me and used it on other computers too.

---

### Post by wildmanne39 on 2017-05-19
I was not sure if it was possible with this driver but it is so have a look at the link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Way down the page it says install b43 with no internet that is the directions you want to follow, of course some of the numbers are going to change in the version of the firmware to install so you will have to look at them up from the live version you are running.

Let us know if it works.

---

### Post by ardouronerous on 2017-05-19
I tried it.

I installed these:

b43-fwcutter (1:019-2) - [http://packages.ubuntu.com/xenial/b43-fwcutter]("http://packages.ubuntu.com/xenial/b43-fwcutter")
firmware-b43-installer (1:019-2) - [http://packages.ubuntu.com/xenial/kernel/firmware-b43-installer]("http://packages.ubuntu.com/xenial/kernel/firmware-b43-installer")

Then I tried following the reload the b43/b43legacy module instructions, but to no avail, and it's maybe because I don't understand the instructions really.

---

### Post by wildmanne39 on 2017-05-19
Your wired connection is not working right?

---

### Post by ardouronerous on 2017-05-19
My wired connection works, but the location of the modem/router is too far, it's three floors up in my father's office, so it's kinda of a hassle to bring my laptop all the way up there.

---

### Post by wildmanne39 on 2017-05-19
We might can make it work with the wired connection but we may still have an issue with it wanting to be restarted instead of being able to use the commands to unload and reload the modules.

---

### Post by ardouronerous on 2017-05-19
Oh well, maybe I'll try a full install of Lubuntu on USB, but I'll have to first buy a 32GB USB first.

---

### Post by ardouronerous on 2017-05-19
Good news, I managed to get Internet on my LiveUSB using Wireless Bridging, I had this spare wireless router laying around in my room, however, this is my first time doing something like this.

Please note that I'm not using DD-WRT, the wireless router I have has wireless bridging option, however, I do have questions about wireless bridging and LiveUSB.

Is wireless bridging safe? Can a stranger cross my wireless bridge? It asked me for the SSID and the password of my WiFi and the wireless mode is using Wireless WAN.

On the LiveUSB, now that I've connected to the Internet, do I have to do updates?

I also heard there's a way to make Firefox settings portable, like save Firefox settings on USB, is that true?

---

### Post by Hadaka on 2017-05-20
Hi, you will not be able to keep any changes to your "Lubuntu" os or "Firefox " on a live
usb. You will need a "persistent" load or a full blown os as QIII suggested. You can get by
with 6 gig on a persistent load..but you cannot load the updates and other goodies. Nor
would you be able to get a full blown os on the usb with only 6 gig. For just playng a bit
and getting a feel for Lubuntu, I would suggest making a persistent usb load. Once you have
a desire and want a complete updated load..then load it on to the hard drive and do a dual boot
with  Ubuntu and Windows...depending on what you use your computer for, I would strongly
sugggest dual booting and not removing Windows XP from your drive, as there are many applications
that are not "Linux friendly" and will run only on Windows.
 I just completed making a persistent usb drive for Ubuntu 14.04, old Dell Inspiron 1300, 2gig ram and
a 32 gig hard drive...B44 /B43 Ethernet/Wifi  not dual booted..which I regret deleting windows xp. So I had to jump
through the same hoops you did,...NO internet access...intentionally..to make up a "How to" guide. If you would
like some help getting your system up and running, let us know. Also..and this is important...Where did you get
the iso file to download Lubuntu 16.04 ?..and where is it currently ?, because it will be needed to make a persistent
Lubuntu 16.04 usb. I am responding to your post via a persistent usb, b43 configuration using Ubuntu 14.04 with no
errors or complaints including changes to the preferences on Firefox.
Thanks

---

### Post by ardouronerous on 2017-05-20
At the moment, I'm quite happy with my LiveUSB system, I managed to get my Firefox addons, bookmarks and settings from my Xubuntu desktop to the live system via a spare USB.

On dual booting, I'm a little hesitant with that, I've never dual booted before and since this laptop is a family laptop, I don't want to accidently damage the Windows partition.

I downloaded my Lubuntu iso from a Torrent I downloaded from lubuntu.net.

---

### Post by Hadaka on 2017-05-20
Glad to hear you have it sorted out,if you are satisfied
with your live Lubuntu usb operation, please mark your
thread solved.
 How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks.

---

### Post by vasa1 on 2017-05-20
> **Hadaka said:**
> ... Also..and this is important...Where did you get
the iso file to download Lubuntu 16.04 ?...
There maybe temptation to go for the most recent version and that would be 16.04.2. However, doing so would put you on the "fast track" to newer and newer kernels for reasons explained in [LTS Enablement Stacks]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

If you'd rather stay behind on the kernel that originally came with 16.04, you need to start with the first 16.04 available from [http://old-releases.ubuntu.com/releases/16.04.0/](http://old-releases.ubuntu.com/releases/16.04.0/).

---

### Post by ardouronerous on 2017-05-21
> **Hadaka said:**
> Glad to hear you have it sorted out,if you are satisfied
with your live Lubuntu usb operation, please mark your
thread solved.
 How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks.

&#65279;I am happy with my LiveUSB, and I'd like to thank wildmanne39 and the Ubuntu community for the help, much appreciated :)

However, all I did was find a workaround, but I'm not sure if this thread is solved though, because the original issue wasn't really solved to begin with, the issue was the Broadcom wireless driver not working in LiveUSB and how to install the drivers without a reboot , all the attempts made by me and wildmanne39 didn't work, all I did was find a workaround, that is, I had a spare wireless router and created a wireless bridge, a workaround doesn't really fix the initial issue, because other people might have my problem and not have spare routers laying around.

---

