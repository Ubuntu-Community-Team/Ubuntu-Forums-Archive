---
title: "Unable to load Unity"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by ubunwhat on 2011-07-03
Ok, I have almost succeeded in finally installing Ubuntu on this Satellite.  Just one more major hurdle before ironing out all the smaller kinks such as microphone / camera not working etc.  The big hurdle is that I am unable to load Unity.  Every time I try to log in I get a message that I have insufficient hardware for Unity and must run classic instead, and then classic is loaded automatically.  This makes no sense as I actually have more than the required specs for Unity.  What I have, as per System Monitor, is...

Memory 1.5gb
Processor 0: 1.73ghz
Processor 1: 1.73ghz
Free Space: 199gb

My processor is the gma 950 chipset which is within requirements per the Ubuntu wiki.  The only thing I can think of is that it is because I am running in nomodeset, which is the only way I can boot this chipset.  Does anyone know if this could be the issue, or if there is something else that I am missing?

---

### Post by Frogs Hair on 2011-07-03
See if there is a proprietary driver for your graphics chip/card . You can check from  Administration > Additional Drivers in Classic Gnome . If there is a recommended driver offered , install it and try to login to Ubuntu. If not I defer to another who has experience with your  setup .

---

### Post by wildmanne39 on 2011-07-04
> **ubunwhat said:**
> Ok, I have almost succeeded in finally installing Ubuntu on this Satellite.  Just one more major hurdle before ironing out all the smaller kinks such as microphone / camera not working etc.  The big hurdle is that I am unable to load Unity.  Every time I try to log in I get a message that I have insufficient hardware for Unity and must run classic instead, and then classic is loaded automatically.  This makes no sense as I actually have more than the required specs for Unity.  What I have, as per System Monitor, is...

Memory 1.5gb
Processor 0: 1.73ghz
Processor 1: 1.73ghz
Free Space: 199gb

My processor is the gma 950 chipset which is within requirements per the Ubuntu wiki.  The only thing I can think of is that it is because I am running in nomodeset, which is the only way I can boot this chipset.  Does anyone know if this could be the issue, or if there is something else that I am missing?
Hi, I believe nomodeset will cause that problem, run this command in a terminal
```
lspci | grep VGA
```
also
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
 and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by ubunwhat on 2011-07-04
lspci | grep VGA

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

/usr/lib/nux/unity_support_test -p

```
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.12-devel

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

lsmod

```
Module                  Size  Used by
binfmt_misc            13213  1 
vesafb                 13449  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
arc4                   12473  2 
pcmcia                 39671  0 
snd_hda_codec_realtek   255820  1 
ath5k                 144412  0 
joydev                 17322  0 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ath                    19141  1 ath5k
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12898  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  1 tifm_7xx1
snd                    55295  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
cfg80211              156212  3 ath5k,ath,mac80211
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  450944  1 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
firewire_ohci          31504  0 
drm_kms_helper         40745  1 i915
firewire_core          56138  1 firewire_ohci
drm                   180037  3 i915,drm_kms_helper
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13184  1 i915
r8169                  42534  0 
video                  18951  1 i915
```

---

### Post by ubunwhat on 2011-07-04
I'm wondering if the fix in this link might help me...

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

I'm reluctant to dive into it because I really am just a bit beyond newbie status with Linux. Also, I don't seem to have an xorg.conf file.  I'm not even sure if 11.04 uses xorg.conf, as this solution is now over two years old.  Any advice?

---

### Post by wildmanne39 on 2011-07-04
> **ubunwhat said:**
> I'm wondering if the fix in this link might help me...

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

I'm reluctant to dive into it because I really am just a bit beyond newbie status with Linux. Also, I don't seem to have an xorg.conf file.  I'm not even sure if 11.04 uses xorg.conf, as this solution is now over two years old.  Any advice?Hi, that guide is for an old version of ubuntu, I would not use it. Run this command and it will tell us if the module is loaded for your intel card, I suspect since you are running nomodeset that it is not.
```

sudo lspci -k
```

---

### Post by goldshirt9 on 2011-07-04
seems i am not alone with this error

i was instructed to try
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

hope it helps

---

### Post by wildmanne39 on 2011-07-04
> **goldshirt9 said:**
> seems i am not alone with this error

i was instructed to try
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

hope it helpsHi,
> The only thing I can think of is that it is because I am running in nomodeset, which is the only way I can boot this chipset. Does anyone know if this could be the issue, or if there is something else that I am missing?

he has already done that I think that is what is causing him to not be able to run unity, can you confirm that?, can you run unity with nomodeset, if so does it limit your 3d capabilities?

---

### Post by ubunwhat on 2011-07-04
Wildmanne,

Thanks for your help with this.  The results of lspci are:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff04
	Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff04
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff03
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel modules: i2c-i801
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7106
	Kernel driver in use: ath5k
	Kernel modules: ath5k
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
	Kernel driver in use: r8169
	Kernel modules: r8169
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```

As for the other suggestion you are correct.  I am running nomodeset now, which is the only way I can get anything but a black screen so far.  However, running nomodeset does prevent from running unity as it does not enable xma.  At least that is what I gathered from my understanding the few articles that I have found on the matter.  Of course my understanding is more than a bit suspect.

---

### Post by wildmanne39 on 2011-07-05
Hi, I am not an expert but looking at the information you posted you can see that each module loaded has a driver in use except the one for your graphics controller.
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff04
	Kernel modules: intelfb, i915
I am pretty sure that is because of the nomodeset, have you tried to find out why you can not boot without nomodeset? I think we are going to hae to fix that before you can get to the unity desktop.

---

### Post by ubunwhat on 2011-07-05
Apparently this particular chipset just doesn't play well with Linux, hence the nomodeset.  I found several threads on this site and others about installing drivers for the chipset, but I haven't figured out how.  I went into synaptic and downloaded the said drivers, but the only way I know of to use them is through the driver manager.  When I use the driver manager it searches and says that there are no drivers available, so I am a bit lost on that front at well.

---

### Post by wildmanne39 on 2011-07-05
> **ubunwhat said:**
> Apparently this particular chipset just doesn't play well with Linux, hence the nomodeset.  I found several threads on this site and others about installing drivers for the chipset, but I haven't figured out how.  I went into synaptic and downloaded the said drivers, but the only way I know of to use them is through the driver manager.  When I use the driver manager it searches and says that there are no drivers available, so I am a bit lost on that front at well.Hi, if you installed them in synaptic then you should be using them. Can you give me the link to see what drivers they are talking about?

---

### Post by ubunwhat on 2011-07-05
Actually it was essentially the link I posted earlier pertaining to Jaunty that had been quoted and regurgitated elsewhere.  The drivers listed there are the ones I downloaded.  My guess is that they were of no use because, and correct me if I'm wrong here, but if they are on the system and I boot without nomodeset then the system would try to use them, right?  And if it did try to use them and all I got was a black screen then they didn't work.  Or am I missing a step.  At some point I got into some type of driver manager, I have no idea how, lol, and it scanned my system and told me that there are no third party drivers currently installed, which made little sense as this was after I downloaded those drivers via synaptic and synaptic clearly shows them as being installed.  It really is quite frustrating.  I hated unity at first, but once I got used to it I really liked it and now I am disappointed to be stuck back on classic.

On an unrelated note, well, maybe it's related, I don't know...  I have what is probably a stupid question.  This machine has had a problem for years with a vertical white line down the center of the screen.  It was there the whole time I used Windows on it and I just assumed it was because of damage to the video card.  Now that I have Ubuntu installed the line is gone, which seems impossible unless it's because the video card is simply not being used at all.  The begs my remedial question... How can the system not use the video card at all and still render literally everything just fine.  I have no problem playing videos, games, or anything else as it is presently configured.  It just seems like it has to be using the card in some capacity.

---

### Post by wildmanne39 on 2011-07-05
> **ubunwhat said:**
> Actually it was essentially the link I posted earlier pertaining to Jaunty that had been quoted and regurgitated elsewhere.  The drivers listed there are the ones I downloaded.  My guess is that they were of no use because, and correct me if I'm wrong here, but if they are on the system and I boot without nomodeset then the system would try to use them, right?  And if it did try to use them and all I got was a black screen then they didn't work.  Or am I missing a step.  At some point I got into some type of driver manager, I have no idea how, lol, and it scanned my system and told me that there are no third party drivers currently installed, which made little sense as this was after I downloaded those drivers via synaptic and synaptic clearly shows them as being installed.  It really is quite frustrating.  I hated unity at first, but once I got used to it I really liked it and now I am disappointed to be stuck back on classic.

On an unrelated note, well, maybe it's related, I don't know...  I have what is probably a stupid question.  This machine has had a problem for years with a vertical white line down the center of the screen.  It was there the whole time I used Windows on it and I just assumed it was because of damage to the video card.  Now that I have Ubuntu installed the line is gone, which seems impossible unless it's because the video card is simply not being used at all.  The begs my remedial question... How can the system not use the video card at all and still render literally everything just fine.  I have no problem playing videos, games, or anything else as it is presently configured.  It just seems like it has to be using the card in some capacity.
Hi, I have an intel chipset for graphics controller in  an old laptop, It worked great with an older version of ubuntu but that version can not even be downloaded anymore. I would go into synaptic and see if the drivers you installed are there then right click on it and click to remove completely.

---

### Post by ubunwhat on 2011-07-05
Can you explain what that would do?  It didn't work before I installed them, and it didn't work after I installed them.  How will uninstalling change anything?  I'm confused by this one.

---

### Post by wildmanne39 on 2011-07-05
> **ubunwhat said:**
> Can you explain what that would do?  It didn't work before I installed them, and it didn't work after I installed them.  How will uninstalling change anything?  I'm confused by this one.Hi, because you can not try to fix the problem while they are installed they will conflict with other one that was already installed, unless you completely remove that old driver first, you can only have one driver installed for your video card at a time. Since the one you installed from synaptic was from a thread on an old release I would think that is the driver you should get rid of and then we can go from there, but they have to be completely gone or the one you was using before you installed the one from synaptic. The way to get rid of the one that was installed first would be to blacklist it since it came with the kernel, but that one should have been the best for your card.

---

### Post by ubunwhat on 2011-07-05
> **wildmanne39 said:**
> Hi, because you can not try to fix the problem while they are installed they will conflict with other one that was already installed, unless you completely remove that old driver first, you can only have one driver installed for your video card at a time. Since the one you installed from synaptic was from a thread on an old release I would think that is the driver you should get rid of and then we can go from there, but they have to be completely gone or the one you was using before you installed the one from synaptic. The way to get rid of the one that was installed first would be to blacklist it since it came with the kernel, but that one should have been the best for your card.

Ok, I think that I have removed all of the ones that I installed, but I am still a bit confused because in nomodeset none of the drivers are installed, right?

---

### Post by ubunwhat on 2011-07-06
Wilde, 

I ran across this from last October when they were testing Unity.  Apparently the gma 950 issue was evident then as well.  It seems like the solution is installing a specific intel driver listed in this thread, but that seems a bit beyond my capabilities.  Would you mind reading this thread and letting me know if I am correct, and, if so, how to install that driver?

[http://ubuntuforums.org/archive/index.php/t-1680305.html]("http://ubuntuforums.org/archive/index.php/t-1680305.html")

---

### Post by ubunwhat on 2011-07-06
Ok, another possible rey of hope.  I downloaded and ran compiz-check and got the same results as the person in the above linked thread.  I was told that I could not run compiz because I am using the vesa driver. This is odd because everything else says that I am using the i915 driver.  Somehow I need to download the driver mentioned in that thread and get the system to use it.  Right?


Edit:  Maddening. Just as the person in that thread said.  I checked Synaptic and the xserver-xorg-video-intel drivers is already installed.  I reinstalled it just to be sure and then ran compiz-check again.  It showed me using the vesa driver.  It asked if I wanted to check for better drivers, I said yes, it checked and said that there are no other drivers installed.  Am I chasing my tail here?

---

### Post by wildmanne39 on 2011-07-06
> **ubunwhat said:**
> Ok, another possible rey of hope.  I downloaded and ran compiz-check and got the same results as the person in the above linked thread.  I was told that I could not run compiz because I am using the vesa driver. This is odd because everything else says that I am using the i915 driver.  Somehow I need to download the driver mentioned in that thread and get the system to use it.  Right?


Edit:  Maddening. Just as the person in that thread said.  I checked Synaptic and the xserver-xorg-video-intel drivers is already installed.  I reinstalled it just to be sure and then ran compiz-check again.  It showed me using the vesa driver.  It asked if I wanted to check for better drivers, I said yes, it checked and said that there are no other drivers installed.  Am I chasing my tail here?
Hi, what is suppose to happen is nomodeset is suppose to tell the bios not to use the intel driver until ubuntu is booted and then it is suppose to come on, so the questions is,why is yours not coming on? The intel driver is installed by default on all ubuntu now days, when you reinstalled the intel i915 driver did you restart your system, and did you make nomodeset permanent? I know I asked that before but it is getting late and I do not remember.

---

### Post by wildmanne39 on 2011-07-06
Hi, I asked a friend to take a look and see if we can get you fixed up.

---

### Post by ubunwhat on 2011-07-06
I had to make nomodeset permanent as it is literally the only way that I can get past the grub without hitting the infinite black screen.  I could try editing the Grub again to remove nomodeset, but it seems pointless without doing something else first to ensure that the xorg driver loads.  I will give it a shot in the morning but it's very late here and I have an early meeting so I am going to have to bail for the night.  If you think of any way to ensure that the driver will load when I drop nomodeset please post it here and I will check tomorrow before I try to reboot out of nomodeset.  It's just, as I said, I can't imagine it working without doing something to ensure that specific driver loads and not the vesa driver.  Otherwise, it's just the same as I was doing before.

One final thought:  You said earlier in the thread that I had no video driver loaded based on the results that you had me post. Compiz-check says I have vesa loaded, and lsmode says I have i915 loaded.  I'm not sure what that means, but it can't be good.

---

### Post by ubunwhat on 2011-07-06
One, even more final thought:  When I look at the xorg driver in Synaptic the box next to it is green.  It seems that most other things I have installed are a different color with a Ubuntu logo next to them.  This is just... green.  I'm not sure if that is relevant.

---

### Post by wildmanne39 on 2011-07-06
> **ubunwhat said:**
> I had to make nomodeset permanent as it is literally the only way that I can get past the grub without hitting the infinite black screen.  I could try editing the Grub again to remove nomodeset, but it seems pointless without doing something else first to ensure that the xorg driver loads.  I will give it a shot in the morning but it's very late here and I have an early meeting so I am going to have to bail for the night.  If you think of any way to ensure that the driver will load when I drop nomodeset please post it here and I will check tomorrow before I try to reboot out of nomodeset.  It's just, as I said, I can't imagine it working without doing something to ensure that specific driver loads and not the vesa driver.  Otherwise, it's just the same as I was doing before.

One final thought:  You said earlier in the thread that I had no video driver loaded based on the results that you had me post. Compiz-check says I have vesa loaded, and lsmode says I have i915 loaded.  I'm not sure what that means, but it can't be good.Hi, that is ok that it is green, and do not undo nomodeset yet, hopefully my friend will be on here soon and can get you fixed up. I was looking at the modules loaded by the kernel, that is how your driver is loaded and it did not show that the intel driver was loaded.

---

### Post by coffeecat on 2011-07-06
Hi, sorry for the several hour delay. I am the one wildmanne39 contacted, but different time-zones and prior demands on my time this morning has made the "soon" into more than 8 hours. I'll just post quickly to show I haven't forgotten and then do some digging around to see if I can find something.

I think this is what we need focus on:

> **ubunwhat said:**
> 
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

The 954GM video chipset is becoming a bit old now. Regrettably, as the xserver is developed further and as video drivers are rewritten for compatibility with the newer versions of the xserver and newer video cards, support for older cards tends to drop off. Which is why a card like the 945GM can work perfectly well in a previous version of Ubuntu but become problematic in the latest version. Whatever - I am sure I saw a fix for this video chipset in Natty. If I find something I'll post back.

---

### Post by ubunwhat on 2011-07-06
> **coffeecat said:**
> Hi, sorry for the several hour delay. I am the one wildmanne39 contacted, but different time-zones and prior demands on my time this morning has made the "soon" into more than 8 hours. I'll just post quickly to show I haven't forgotten and then do some digging around to see if I can find something.

I think this is what we need focus on:



The 954GM video chipset is becoming a bit old now. Regrettably, as the xserver is developed further and as video drivers are rewritten for compatibility with the newer versions of the xserver and newer video cards, support for older cards tends to drop off. Which is why a card like the 945GM can work perfectly well in a previous version of Ubuntu but become problematic in the latest version. Whatever - I am sure I saw a fix for this video chipset in Natty. If I find something I'll post back.

Thanks for your help, Coffee.  I know that the chipset is hardly bleeding edge at this point, but unfortunately it is not one that can be swapped out or upgraded.  I'm stuck with the 945 for as long as I have the machine.  And I absolutely LOVE this machine.

---

### Post by wildmanne39 on 2011-07-06
Hi, I am going to continue to research this problem as well,since you had unity before it is just a matter of getting your driver to load again, in the mean time you can go into software center and install unity 2d and it looks almost like unity, I did not tell the difference between the two, but you would not have 3d support.
Thank you very much coffecat for helping us out with this situation, I appreciate it very much.

---

### Post by ubunwhat on 2011-07-06
> **wildmanne39 said:**
> Hi, I am going to continue to research this problem as well,since you had unity before it is just a matter of getting your driver to load again, in the mean time you can go into software center and install unity 2d and it looks almost like unity, I did not tell the difference between the two, but you would not have 3d support.
Thank you very much coffecat for helping us out with this situation, I appreciate it very much.

Oh hold on.  Two points here.  First, I had no idea that Unity 2d existed.  I will definitely give that a shot.  Second, I have to go back to the very beginning of this thread and point out that Unity never worked on this machine.  In fact, I could never get Ubuntu working at all on this machine prior to Sunday.  When I first tried to install it I couldn't get anything working so I set the machine aside and used an old Compaq Presario.  That is where I had Unity etc.  However, after becoming more confident in Ubuntu, and quite frankly remembering how great this machine is, I thought I would give it another go.  I was stunned that I was actually able to get Ubuntu working even in classic mode.  I guess that goes to show what a little confidence and experience will do.  However, now that I have it working in classic mode I really want to go back to Unity.  I find it odd that there are so many threads out there, even during beta testing for Unity, that talk about this problem and they just sort of.... end.  People stop posting.  Some seem to figure it out, others just seem to give up.  I know this is a fairly common chipset but how it behaves will be machine specific to an extent and I have actually not seen any threads anywhere about the Satellite P205 aside from the dozen or so that I have started over the last year or so.

---

### Post by wildmanne39 on 2011-07-06
> **ubunwhat said:**
> Oh hold on.  Two points here.  First, I had no idea that Unity 2d existed.  I will definitely give that a shot.  Second, I have to go back to the very beginning of this thread and point out that Unity never worked on this machine.  In fact, I could never get Ubuntu working at all on this machine prior to Sunday.  When I first tried to install it I couldn't get anything working so I set the machine aside and used an old Compaq Presario.  That is where I had Unity etc.  However, after becoming more confident in Ubuntu, and quite frankly remembering how great this machine is, I thought I would give it another go.  I was stunned that I was actually able to get Ubuntu working even in classic mode.  I guess that goes to show what a little confidence and experience will do.  However, now that I have it working in classic mode I really want to go back to Unity.  I find it odd that there are so many threads out there, even during beta testing for Unity, that talk about this problem and they just sort of.... end.  People stop posting.  Some seem to figure it out, others just seem to give up.  I know this is a fairly common chipset but how it behaves will be machine specific to an extent and I have actually not seen any threads anywhere about the Satellite P205 aside from the dozen or so that I have started over the last year or so.Hi, ok the way I have been reading your first post I thought you had unity working at one point, if not then it may not be possible because it is an old chipset, but unity 2d should be just fine.

---

### Post by coffeecat on 2011-07-06
@ubunwhat, I've been doing a bit of digging around, but I'm afraid I haven't come up with much. Some people with your graphics chipset seem to be able to boot into a Unity desktop, but others report problems such as a black screen and nothing seems to be resolved in their threads.

I have one suggestion, and I really don't know whether it will help. Instead of the "nomodeset" option you discovered, try "i915.modeset=1" (without the quotes). When you get the grub screen, edit the first entry as a temporary try-out replacing nomodeset with i915.modeset=1.

My guess is that this may give you a black screen. If so, you need to reboot gracefully. Use the magic key sequence:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

Having commenced a reboot and got back to the grub menu, try "i915.modeset=0" instead. But I fear this may simply do the same as  "nomodeset", though.

---

### Post by ubunwhat on 2011-07-06
I had Unity working in the Presario I was using.  I simply slid the drive into the Toshiba once I got classic working on a different drive.  I still have to say, however, based on the threads, that it does seem that it should work.  This chipset is a bit dated in terms of laptops, but is still widely used in netbooks, and Unity was originally developed for netbooks.  The beta thread shows a lot of netbook owners who were testing Unity having problems with this chipset, but it doesn't actually tell you the resolution.

---

### Post by ubunwhat on 2011-07-06
> **coffeecat said:**
> @ubunwhat, I've been doing a bit of digging around, but I'm afraid I haven't come up with much. Some people with your graphics chipset seem to be able to boot into a Unity desktop, but others report problems such as a black screen and nothing seems to be resolved in their threads.

I have one suggestion, and I really don't know whether it will help. Instead of the "nomodeset" option you discovered, try "i915.modeset=1" (without the quotes). When you get the grub screen, edit the first entry as a temporary try-out replacing nomodeset with i915.modeset=1.

My guess is that this may give you a black screen. If so, you need to reboot gracefully. Use the magic key sequence:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

Having commenced a reboot and got back to the grub menu, try "i915.modeset=0" instead. But I fear this may simply do the same as  "nomodeset", though.

I tried both of those early on.  Much as you suspect, i915=1 gave me a black screen.  However, and I find this curious, i915=0 also gave me a black screen rather than working in the same manner as nomodeset.

---

### Post by wildmanne39 on 2011-07-06
Hi, it appears unity 2d will be you best option.

---

### Post by wildmanne39 on 2011-07-06
@coffeecat
Hi, thank you for your help it is greatly appreciated.

---

### Post by coffeecat on 2011-07-07
> **wildmanne39 said:**
> Hi, it appears unity 2d will be you best option.

@ubunwhat, yes I agree with wildmanne39. I think Unity 2d will be your only way of using Unity with that Intel chipset. I am disappointed for you. It's not the best video chipset in the world, but it was capable of supporting compiz in earlier versions of Ubuntu. If I do happen to come across anything, I'll post again.

---

