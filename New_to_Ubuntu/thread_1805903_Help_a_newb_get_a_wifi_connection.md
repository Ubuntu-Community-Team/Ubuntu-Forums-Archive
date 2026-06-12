---
title: "Help a newb get a wifi connection?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by ehehlomy on 2011-07-16
As you may already assume, I've just downloaded Ubuntu and gotten an account here. The latter was only a result of my first issue with Ubuntu!
I logged into it after installing it onto my Dell Inspiron 1501 laptop, and everything was going as smoothly as it could... Until I tried to access the internet through Firefox. My little Wifi light is off (it was always on in Windows Vista; we have a wireless network) and obviously I'm not getting aaaany internet on it... I looked in the little internet icon up top (which is sorta empty-cone-like at the moment, if that is of importance) and our wifi thingy isn't there, as it should be.
This is bothersome :|
I lurked around for a bit before starting a new thread, because I didn't want to be brought down in flames of
"you're the zillionth person to say this! redundancy! rage rage! answer is easy! noob!"
but sadly... I looked, and my teeny little computer-illiterate brain was swamped. I need someone to tell it to me easy, all nice and dumbed down... please?
 
Ps~ I had seen [this]("http://ubuntuforums.org/showthread.php?t=1730670") thread, and everyone with the issue seemed happy with their results of the fix. So... I tried, and didn't get very far. I went to System Settings/Additional Drivers, but nothing was there. It told me "Downloading package indexes failed, please check your network status. Most drivers will not be available."
Then it says, after I close that, that "No proprietary drivers are in use on this system."
So how do I deactivate a STA driver? Gaaaah!
I go to Synaptic Package Manager, and there is nothing like "B43" in the list. Double gaaah!
 
So please... Help a newb?
 
 
Edit- goodness this is wordy...

---

### Post by quesadilla on 2011-07-16
so are you acessing this on a different browser or a different computer? if its a different browser, fifrefox probably wasn't installed correctly.  If no internet will work at all, try and make sure if you are using a wireless card that is in correctly.

---

### Post by Neoncamouflage on 2011-07-16
This happens every time my laptop dies due to a dead battery. I have to go to the wifi icon on the top bar, right click - enable networking. Wait about ten seconds, and hit the wifi button on your computer (if you have one). Then either choose a connection or let it autoconnect if there's one set up.

Hope it helps.

---

### Post by ehehlomy on 2011-07-16
I'm on a different computer altogether... I wish something else worked aside of firefox, because then, I would use that instead. I can, however, access internet on the same computer, just through the other os (which is Windows Vista)
 
Networking is enabled already, and I tried Fn F2, but the light still won't come on...

---

### Post by wildmanne39 on 2011-07-16
Hi, type this into a terminal
```
sudo lshw -C network
```
```
lspci -nn
```
```
lsmod
```
```
iwconfig

```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by ehehlomy on 2011-07-16
[FONT=Arial][SIZE=2]Heh, I moved everything over to this computer, but I did all in Ubuntu:[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Part of first:[/SIZE][/FONT]
 
```
 
*-network DISABLED
 
       description: Wireless interface
 
       physical id: 2
 
       logical name: wlan0
 
       serial: 00:19:7e:93:45:04
 
       capabilities: ethernet physical wireless
 
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
 
[FONT=Arial][SIZE=2](See, I was looking on the troubleshooting thing in Ubuntu help, and it told me that if it said disabled, I must not have it turned on... Which I tried to do multiple times.)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Second:[/SIZE][/FONT]
 
```
 
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
 
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
 
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
 
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
 
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
 
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
 
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
 
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
 
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
 
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
 
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
 
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
 
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
 
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
 
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
 
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
 
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
 
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
 
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
 
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
 
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

```
 
[FONT=Arial][SIZE=2]third:[/SIZE][/FONT]
 
```
 
Module                  Size  Used by
 
nls_iso8859_1          12713  1 
 
nls_cp437              16991  1 
 
vfat                   21708  1 
 
fat                    61374  1 vfat
 
binfmt_misc            17565  1 
 
parport_pc             36959  0 
 
ppdev                  17113  0 
 
snd_hda_codec_idt      71137  1 
 
snd_hda_intel          33211  2 
 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
 
radeon                982197  3 
 
snd_hwdep              13604  1 snd_hda_codec
 
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
 
joydev                 17606  0 
 
snd_seq_midi           13324  0 
 
arc4                   12529  2 
 
snd_rawmidi            30486  1 snd_seq_midi
 
ttm                    76664  1 radeon
 
snd_seq_midi_event     14899  1 snd_seq_midi
 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
 
drm_kms_helper         42136  1 radeon
 
b43                   318638  0 
 
snd_timer              29602  2 snd_pcm,snd_seq
 
drm                   227495  5 radeon,ttm,drm_kms_helper
 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
 
sp5100_tco             13744  0 
 
mac80211              294370  1 b43
 
dell_wmi               12681  0 
 
i2c_piix4              13303  0 
 
sparse_keymap          13898  1 dell_wmi
 
i2c_algo_bit           13400  1 radeon
 
psmouse                73535  0 
 
dell_laptop            13827  0 
 
edac_core              53845  0 
 
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 
serio_raw              13166  0 
 
cfg80211              178528  2 b43,mac80211
 
dcdbas                 14438  1 dell_laptop
 
edac_mce_amd           23464  0 
 
soundcore              12680  1 snd
 
k8temp                 13016  0 
 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
 
shpchp                 37297  0 
 
video                  19438  0 
 
lp                     17825  0 
 
parport                46458  3 parport_pc,ppdev,lp
 
usb_storage            53538  1 
 
b44                    36000  0 
 
uas                    17996  0 
 
ahci                   25951  1 
 
sdhci_pci              13989  0 
 
sdhci                  27387  1 sdhci_pci
 
pata_atiixp            13165  1 
 
libahci                26642  1 ahci
 
ssb                    51945  2 b43,b44

```
 
[FONT=Arial][SIZE=2]fourth:[/SIZE][/FONT]
 
```
 
lo        no wireless extensions.
 
 
 
eth0      no wireless extensions.
 
 
 
wlan0     IEEE 802.11bg  ESSID:off/any  
 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
 
          Retry  long limit:7   RTS thr:off   Fragment thr:off
 
          Power Management:off

```

---

### Post by TBABill on 2011-07-16
Ok, here's what needs to be done. If you still have your Ubuntu disk, the best thing to do since you have no other option is to see if you have an option to add a CD or DVD as a source. Since I don't have any idea what Ubuntu version you are using I'll assume you are using Ubuntu 10.04 LTS. Can you click System, Administration, Software Sources and see if there's a box about 2/3 of the way down that says "CDROM with ubuntu 10.04 Lucid Lynx" or something similar if it's a different version of Ubuntu. Then check that box, click reload when prompted.

After that, go to a terminal and type in ```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` After that, it should begin installing the driver right from the CD. Once it finishes, then go to System, administration, hardware drivers and enable the b43 driver. Once it finishes you may need to restart.

Edit: from your post above it appears you have no firmware installed but the b43 is active. It just needs the firmware to work, but install as if nothing has been configured yet just as I showed above.

---

### Post by TBABill on 2011-07-16
If none of that works, try this link and follow the no internet instructions for b43: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by ehehlomy on 2011-07-16
Thank you for telling me what the issue is!
Eh... I wish I could say otherwise, but I don't have a disk. Is there any other possible way to get the firmware? Or... is there a way to somehow get it from the download link on their site?

---

### Post by wildmanne39 on 2011-07-17
> **domskhel said:**
> Thank you for telling me what the issue is!
Eh... I wish I could say otherwise, but I don't have a disk. Is there any other possible way to get the firmware? Or... is there a way to somehow get it from the download link on their site?Hi, if you have a wired connection you can install it by going to synaptic and clicking install.

If you do not have a wired connection you can use another computer to download the livecd version of ubuntu and then boot ubuntu put in the cd then open synaptic and make sure cd is checked by clicking on settings, repositories, when the window opens you well see install from cd/dvd and put a check by cdrom then click close and reload.

Hers is a good set off instructions for install the driver for your card which is the 4311. You also need to uninstall the sta driver before you install your driver.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

If you need more help please post back here.

---

### Post by ehehlomy on 2011-07-17
I followed the instructions, I just don't know how to uninstall the sta driver, that's has to be my last problem in the way of getting internet. I'm still not getting access, even after rebooting... But hey, my wifi light came on! Thaaaanks

---

### Post by wildmanne39 on 2011-07-17
> **domskhel said:**
> I followed the instructions, I just don't know how to uninstall the sta driver, that's has to be my last problem in the way of getting internet. I'm still not getting access, even after rebooting... But hey, my wifi light came on! ThaaaanksHi, open synaptic type in bcm and it will bring up the drivers for the card, you can see what is installed it will have a little green box by it,find the one that says sta and right click on it and choose to remove completely. If it does not work come back here for more help if it does mark solved please.

---

### Post by ehehlomy on 2011-07-17
Alright, well, I'm in Synaptic Package Manager, and I can't find anything of bcm or sta in there... Does that mean it's not even there, and I have some other sort of issue?
Thank you so much for helping me, by the way...

---

### Post by wildmanne39 on 2011-07-17
> **domskhel said:**
> Alright, well, I'm in Synaptic Package Manager, and I can't find anything of bcm or sta in there... Does that mean it's not even there, and I have some other sort of issue?
Thank you so much for helping me, by the way...Hi, are you connected to the internet with a wire connection when you open synaptic? Look in additional drivers and see if the sta driver is active there? if so deactivate it. Also now that you have a driver installed run these commands in a terminal
```
lsmod
```
```
rfkill list All 
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by ehehlomy on 2011-07-17
[FONT=Arial][SIZE=2]Oooookay, now I've got it![/SIZE][/FONT]
[FONT=Arial][SIZE=2]Thank you so much![/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-07-17
Hi, have you went to the top right corner of the screen and clicked on the internet icon and see if wireless is enabled? If so and you still can not use it make sure that firefox is not in offline mode. If that is ok then try this in a terminal and see if it turns on. 
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
If is does not connect run this and post the outcome.
```
iwconfig
```

---

### Post by wildmanne39 on 2011-07-19
> **domskhel said:**
> [FONT=Arial][SIZE=2]Oooookay, now I've got it![/SIZE][/FONT]
[FONT=Arial][SIZE=2]Thank you so much![/SIZE][/FONT]Hi, your welcome!! I am glad it is working enjoy ubuntu.

---

