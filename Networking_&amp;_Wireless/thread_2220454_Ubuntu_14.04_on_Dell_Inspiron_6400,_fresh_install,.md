---
title: "Ubuntu 14.04 on Dell Inspiron 6400, fresh install, no wired or wifi"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by ikman on 2014-04-28
Fresh install on Dell Inspiron 6400 with 120GB HDD and 1GB RAM.

Had wired networking during the "try it" live CD and the the two Up/down arrows indicating wired connection during install (and selected option to install update and third party drivers). But one I removed install disk and rebooted there is no networking of any type. 
ifup -a    gave nothing
lsusb  showed only 5 root hubs, no devices

I need to have both wired and wireless. Where do I start? Thank you.

---

### Post by varunendra on 2014-04-28
Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by ikman on 2014-04-28
Thanks for helping me on this. I appreciate it.  (Looks like I have a Broadcom LAN device BCM4401-BO and a BCM4311 wifi device). Next step?  (I used the 32-bit OS as recommended by RAM amt)
```
$ uname -mr
3.13.0-24-generic i686
$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl
$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
usb_storage            48417  0 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
ssb                    51854  1 
mii                    13654  0 
wl                   3999690  1 
snd_hda_codec_idt      48877  1 
radeon               1416373  3 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
joydev                 17101  0 
gpio_ich               13229  0 
dell_wmi               12665  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
sparse_keymap          13708  1 dell_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
r852                   17722  0 
sm_common              16772  1 r852
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
nand                   58760  2 r852,sm_common
snd_rawmidi            25135  1 snd_seq_midi
ttm                    72698  1 radeon
nand_ecc               13136  1 nand
nand_bch               13067  1 nand
drm_kms_helper         46907  1 radeon
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bch                    17197  1 nand_bch
drm                   243792  5 ttm,drm_kms_helper,radeon
snd_timer              28584  2 snd_pcm,snd_seq
nand_ids                8547  1 nand
dell_laptop            17808  0 
lib80211               14040  1 wl
psmouse                91033  0 
mtd                    52813  2 nand,sm_common
i2c_algo_bit           13197  1 radeon
r592                   17711  0 
dcdbas                 14448  1 dell_laptop
coretemp               13195  0 
cfg80211              409394  1 wl
snd                    60871  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
memstick               16174  1 r592
serio_raw              13230  0 
soundcore              12600  1 snd
lpc_ich                16864  0 
mac_hid                13037  0 
wmi                    18673  1 dell_wmi
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
$ 
```

---

### Post by chili555 on 2014-04-28
I hope I am not stepping on Varun's toes; I know he's quite busy these days. Please hook up the ethernet. Yeah, yeah, I know, you say it's not working. Please open a terminal Ctrl+Alt+t and do:
```
sudo modprobe b44
```
At this point, your ethernet will spring to life. Next do:
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
Detach the ethernet, reboot and let us hear the result.

Why do I get all the easy ones??

---

### Post by ikman on 2014-04-28
Sorry. But that is my problem, wired Internet doesn't spring to life...

```

sudo modprobe b44

```
gives a blank line that stays empty for several minites until I press Ctrl+c

And while I was waiting I also tried a few others:

ipconfig, iwconfig, lspci -vnn -d 14e4:

Output showed only "lo" but no "eth0" 
The Broadcom controller showed [0200] for the wired device and [0280] for the wireless device

---

### Post by ikman on 2014-04-28
Oh, and I know the cable works because I unplug it to this computer to send the forum posts.  (But keep trying, I'm up for all the help I can get, and appreciate it greatly.)

---

### Post by chili555 on 2014-04-28
Please try a different order:```
sudo apt-get remove --purge bcmwl-kernel-source
```And then reboot. Then let us see:```
ifconfig
```If eth0 shows up, hook up the ethernet and:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

---

### Post by ikman on 2014-04-28
Ok. Now I have wired connection. Standing by for wireless instructions... :-)

---

### Post by chili555 on 2014-04-28
> **ikman said:**
> Ok. Now I have wired connection. Standing by for wireless instructions... :-)See post #7. Then reboot.

---

### Post by ikman on 2014-04-28
Yes. I just reread your instructions and did that (before you had to remind me.. really ).   You're right. That was too easy!!
I will mark as solved. Can you post one more time with a possible way to prevent this from happening? E.g., Is it because I checked the "use restricted drivers" box during the install, or something like that?  Any ideas for follow-on readers?

---

### Post by varunendra on 2014-04-29
> **chili555 said:**
> I hope I am not stepping on Varun's toes
You did, and took away the candy from me... again! Why?? :p

.. But I'd be a gentleman, and won't disclose my above feelings here.. so.. Thank You for the help! :D

> **ikman said:**
> Can you post one more time with a possible way to prevent this from happening? E.g., Is it because I checked the "use restricted drivers" box during the install, or something like that?  Any ideas for follow-on readers?

To prevent this from happening again -

[indent]***** Avoid anything that can install the proprietary driver "wl" (also called the "STA" driver, or "bcmwl-kernel-source" package) on the system. That driver works, but not well with some particular broadcom cards, including yours. This means -
[indent]* Don't mark "Install Updates" or "Use Restricted Drivers" option during installation.
* Don't accept the wireless driver proposed by the "Additional Driver" feature after installation.
* Don't follow any guides/posts/instructions that tell you to install the "wl" (or "STA") driver. (That driver is okay, but not for _your_ card).[/indent]

***** IF the STA driver got installed somehow, it is easy to get rid of it. Simply run the command -
```
sudo apt-get purge bcmwl-kernel-source
```
..then reboot. Done!

***** Sometimes (as a result of following some unusual or non-standard workaround), some blacklist entries or blacklist files remain behind despite purging the "bcmwl-kernel-source" package. In such cases, such entries/files need to be manually removed. The quickest way (in my opinion) to find if there are such remnant entries/files is running the following command -
```
egrep 'blacklist (b43|ssb)' /etc/modprobe.d/*
```
If it returns any entries (for example - *"[COLOR="#4B0082"]/etc/modprobe.d/blacklist-broadcom.conf:[/COLOR][COLOR="#FF0000"]blacklist b43[/COLOR]"*), note down the name of the file (the part in purple) that contains those entries, and either manually delete the entries or the file itself (should be done carefully, ask for help if not sure what you are doing).[/indent]

Essence of the above scenarios is - the STA driver or some unusual workarounds tend to blacklist the "b43" and "ssb" drivers (along with some others). You need to get rid of the STA driver and these blacklist entries - whatever way it is easy for you.

Hope I added an explanation, not a confusion. :p

---

