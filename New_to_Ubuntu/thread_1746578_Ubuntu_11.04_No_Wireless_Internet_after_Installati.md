---
title: "Ubuntu 11.04: No Wireless Internet after Installation"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2011-05-01
I just installed Ubuntu 11.04 in my current laptop. (The previous one was usurped.) I can still go online in the other operating system (Windows XP), but the only way I can go online in Ubuntu is by plugging it into the cable modem.
How can this be fixed?

Here is a some information that I was able to compile:
>To "nm-applet":```
kalayaan001@Kalayaan-MM061:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:1727): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```How can we initialize the D-Bus manager?

> To "nm-tool":```
kalayaan001@Kalayaan-MM061:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:19:B9:85:01:CA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```

> To "rfkill list":```

kalayaan001@Kalayaan-MM061:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

> To "lspci":```
kalayaan001@Kalayaan-MM061:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I hope that the information (and their division) helped.

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by spikoley on 2011-05-06
Plug it in so you can get online and run the updates.  After the updates are done check the Additional Drivers.  This might be a Broadcom driver issue and the Additional Drivers might fix it.  I did this in the past to get my Broadcom wireless card working.

---

### Post by computerandu on 2011-05-06
Hi,
Here is what you need to do. Use other Broadcom drivers. Download these drivers (from Windows or through wired network or a friend’s computer or from wherever you are reading this article  ). Install these instead of the one provided by Ubuntu 11.04.

For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

Now remove the previous drivers using: sudo apt-get remove bcmwl-kernel-source

Now install the appropriate driver. Restart your computer. If restarting doesn’t work try shut down and then start it (strange…but works). Enjoy 

Source: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by josephmills on 2011-05-06
hi there could we please see a ```
lspci -vnn | grep b43 
```
to make sure that you need the b43 or the sta or a different mod all together
could we also see a 
```
rfkill list all 
``` I know that we have seen a rfkill list but not all night be the same thing might not

---

### Post by RedStarYellowSun on 2011-05-06
> **josephmills said:**
> hi there could we please see a ```
lspci -vnn | grep b43 
```
to make sure that you need the b43 or the sta or a different mod all together
could we also see a 
```
rfkill list all 
``` I know that we have seen a rfkill list but not all night be the same thing might not

Here are the results:
```
kalayaan001@Kalayaan-MM061:~$ lspci -vnn | grep b43
kalayaan001@Kalayaan-MM061:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
kalayaan001@Kalayaan-MM061:~$
```
I hope this helps.

Thanks for the response!

Take care,
RedStarYellowSun

---

### Post by jtarin on 2011-05-06
> **josephmills said:**
> hi there could we please see a ```
lspci -vnn | grep b43 
```
to make sure that you need the b43 or the sta or a different mod all together

*_From his previously run lspci._*
Network controller: Broadcom Corporation **_BCM4311 _**802.11b/g WLAN (rev 01)

Try running the command "lsmod" so we can see what driver/module your using for this controller.
You might want to follow computerandu's advice.

---

### Post by ngronewold on 2011-05-06
RedStar, if you're laptop is one of the Dell Inspiron series and has a Broadcom wireless card inside, then here is the solution (no coding required):

Re: 11.04 wireless issues
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Now it works.

You have to be hooked up to the internet via a land line for this to work though. I struggled for hours with land internet but no wireless connection until I found this solution here on the Forum.

---

### Post by RedStarYellowSun on 2011-05-07
> **ngronewold said:**
> RedStar, if you're laptop is one of the Dell Inspiron series and has a Broadcom wireless card inside, then here is the solution (no coding required):

Re: 11.04 wireless issues
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Now it works.

You have to be hooked up to the internet via a land line for this to work though. I struggled for hours with land internet but no wireless connection until I found this solution here on the Forum.

I have installed in my laptop all 4 entries under the Synaptic  keyword "bcm4311": firmware-b43-installer, bcmwl-kernel-source, broadcom-sta-common, and broadcom-sta-source. (There is even b43-fwcutter, though that appears for the broader keywork "bcm".)

The processes you suggested is the same as just uninstalling bcmwl-kernel-source, broadcom-sta-common, and broadcom-sta-source? Right?

Thanks again.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2011-05-07
> **jtarin said:**
> *_From his previously run lspci._*
Network controller: Broadcom Corporation **_BCM4311 _**802.11b/g WLAN (rev 01)

Try running the command "lsmod" so we can see what driver/module your using for this controller.
You might want to follow computerandu's advice.

Yeah, I did what computerandu suggested, but when I ran Update Manager and restarted, I was back to square 1. Do you know how to make Update Manager not undo it?

I'll reboot to Ubuntu to get lsmod. One moment...
Got it! Here it is:
```
kalayaan001@Kalayaan-MM061:~$ lsmod 
Module                  Size  Used by 
sha256_generic         20911  2  
cryptd                 19801  0  
aes_i586               16956  141  
aes_generic            38023  1 aes_i586 
parport_pc             32111  0  
ppdev                  12849  0  
dm_crypt               22463  1  
snd_hda_codec_idt      60537  1  
joydev                 17322  0  
snd_hda_intel          24140  2  
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0  
snd_rawmidi            25269  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
binfmt_misc            13213  1  
wl                   2642531  0  
dell_wmi               12601  0  
snd_timer              28659  2 snd_pcm,snd_seq 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
sparse_keymap          13666  1 
dell_wmi dell_laptop            13515  0  
dcdbas                 14054  1 dell_laptop 
r852                   17878  0  
sm_common              16737  1 r852 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
nand                   49822  2 r852,sm_common 
nand_ids                8547  1 nand 
psmouse                73312  0  
nand_ecc               13070  1 nand 
mtd                    26720  2 sm_common,nand 
serio_raw              12990  0  
soundcore              12600  1 snd 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
lib80211               14570  1 wl 
lp                     13349  0  
parport                36746  3 parport_pc,ppdev,lp 
radeon                896428  3  
firewire_ohci          31504  0  
sdhci_pci              13623  0  
ttm                    65184  1 radeon 
sdhci                  22720  1 sdhci_pci 
firewire_core          56138  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
drm_kms_helper         40745  1 radeon 
drm                   180037  5 radeon,ttm,drm_kms_helper 
video                  18951  0  
i2c_algo_bit           13184  1 radeon 
kalayaan001@Kalayaan-MM061:~$ 
```
Sorry for the delay. I have had to re-space the code a number of times.

Thanks again.

Take care,
RedStarYellowSun

---

### Post by josephmills on 2011-05-07
> **jtarin said:**
> *_From his previously run lspci._*
Network controller: Broadcom Corporation **_BCM4311 _**802.11b/g WLAN (rev 01)

Try running the command "lsmod" so we can see what driver/module your using for this controller.
You might want to follow computerandu's advice.
try ```
lspci -vnn | grep 14e4
``` some times the model number is different please see [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by ngronewold on 2011-05-07
> **RedStarYellowSun said:**
> I have installed in my laptop all 4 entries under the Synaptic  keyword "bcm4311": firmware-b43-installer, bcmwl-kernel-source, broadcom-sta-common, and broadcom-sta-source. (There is even b43-fwcutter, though that appears for the broader keywork "bcm".)

The processes you suggested is the same as just uninstalling bcmwl-kernel-source, broadcom-sta-common, and broadcom-sta-source? Right?

Thanks again.

Take care,
RedStarYellowSun

The process I went through was a lot easier than what you described. I simply went to the hardware drivers and dumped broadcom's STA (which Ubuntu automatically attempted to install when I upgraded from 10.04). After that I went through the universal search app in the upper left to get to Synaptic Package Manager and did steps 1,2,3.

Hope this helps.

---

### Post by RedStarYellowSun on 2011-05-07
> **josephmills said:**
> try ```
lspci -vnn | grep 14e4
``` some times the model number is different please see [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

```
kalayaan001@Kalayaan-MM061:~$ lspci -vnn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
kalayaan001@Kalayaan-MM061:~$
```

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2011-05-07
> **ngronewold said:**
> The process I went through was a lot easier than what you described. I simply went to the hardware drivers and dumped broadcom's STA (which Ubuntu automatically attempted to install when I upgraded from 10.04). After that I went through the universal search app in the upper left to get to Synaptic Package Manager and did steps 1,2,3.

Hope this helps.

Darn it, I made a mistake and uninstalled the wrong drivers. Do you happen to have a link to the current b43-fwcutter & firmware-b43-installer deb files?

Thanks again.

Take care,
RedStarYellowSun

---

### Post by Nonmouse on 2011-05-07
> **ngronewold said:**
> RedStar, if you're laptop is one of the Dell Inspiron series and has a Broadcom wireless card inside, then here is the solution (no coding required):

Re: 11.04 wireless issues
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Now it works.

You have to be hooked up to the internet via a land line for this to work though. I struggled for hours with land internet but no wireless connection until I found this solution here on the Forum.


AWESOME!  This process worked exactly for me with a Dell Latitude D420.  Great Find! Saved me hours!

---

### Post by ngronewold on 2011-05-09
> **RedStarYellowSun said:**
> Darn it, I made a mistake and uninstalled the wrong drivers. Do you happen to have a link to the current b43-fwcutter & firmware-b43-installer deb files?

Thanks again.

Take care,
RedStarYellowSun


Sorry for the hiatus.

Those two should be listed in the Synaptic Package Manager (after scrolling down the list some).  If not then I'm afraid I don't have a link.  If they got deleted for good then perhaps a fresh re-install would restore them?

---

### Post by josephmills on 2011-05-10
please see [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
post number 41

---

### Post by BertN45 on 2011-05-10
I have the same wifi, I used the simplet method:

- de-activate te Broadcom STA driver using "Additional Drivers"
- Go to the synaptic package manager and type bcm and unstall everything related to the wifi drivers.
- type b43 and install the firmware-b43-installer and b43-fwcutter.

That was enough to get my BCM4311 working.

---

### Post by computerandu on 2011-05-11
> **BertN45 said:**
> I have the same wifi, I used the simplet method:

- de-activate te Broadcom STA driver using "Additional Drivers"
- Go to the synaptic package manager and type bcm and unstall everything related to the wifi drivers.
- type b43 and install the firmware-b43-installer and b43-fwcutter.

That was enough to get my BCM4311 working.

To use this solution, one needs to be connected through a wired network...not feasible for those having only wired connection available with them...:(

---

### Post by TheNessus on 2011-05-11
You don't need internet access to get the deb.

It is also found on an Ubuntu .iso, here:
/pool/restricted/b/bcmwl/

if it asks for dependencies first, they too can be found somewhere in /pool/

---

### Post by BertN45 on 2011-05-11
> **TheNessus said:**
> You don't need internet access to get the deb.

It is also found on an Ubuntu .iso, here:
/pool/restricted/b/bcmwl/

if it asks for dependencies first, they too can be found somewhere in /pool/

Thank you for this info. I expect, it would  install as described,  if you tick the Ubuntu CD in the "other software" tab in the "repository" menu of the Synaptic Package Manager..

---

### Post by TheNessus on 2011-05-13
> **BertN45 said:**
> Thank you for this info. I expect, it would  install as described,  if you tick the Ubuntu CD in the "other software" tab in the "repository" menu of the Synaptic Package Manager..

yes it would. I took the longer course of action because I don't have a cd drive and virtually mounting it could not work as a repo.

---

### Post by Coretj on 2011-05-13
You guys rock!!!

---

