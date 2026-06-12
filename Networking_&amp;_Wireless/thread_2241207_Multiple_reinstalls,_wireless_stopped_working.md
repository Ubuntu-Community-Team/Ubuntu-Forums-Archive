---
title: "Multiple reinstalls, wireless stopped working"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by ruberad on 2014-08-24
Hey all, looking for some help. I have had a Dell mini that for years has been doing wifi fine with 11.04, but I was unable to get the recent forced Skype upgrade to work with video, so I decided to upgrade to 14.04 (32-bit). I did that, wireless was working, video was not. So I tried reinstalling back to 12.04, wireless was working, I figured out the video thing (LD_PRELOAD...), so I decided for one final time to reinstall 14.04 again, but now wireless does not work. Before I would always see my wifi ID, plus a few neighbors' wifi IDs in the networking dropdown, and could just select mine, enter the password, and bingo. I no longer see any wifi IDs in the dropdown (although somehow through the installs if I Edit Connections, the wifi area still knows what the network ID is). Note the wifi is still working, the kids were able to play Wii U online this afternoon, and that connects through the wifi. Everything seems to work fine, as long as I plug an ethernet cable in, but where this netbook is supposed to "live", I don't want a cable stretching across the room...

I have tried working through the [troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), so I have a lot of output files saved off from doing lshw -C network, etc, I will paste them here, hopefully y'all can help me push through this:

nm-tool:

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:21:70:C4:A8:73

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
-----------------------------------------------------------------------------------------------

lswh -C network:
  *-network
       description: Network controller
       product: **BCM4312** 802.11b/g LP-PHY
       vendor: **Broadcom **Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=b43-pci-bridge** latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c4:a8:73
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff
-------------------------------------------------------------------------------------------------------

lspci:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
**03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)**
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
----------------------------------------------------------------------------------

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.
-----------------------------------------------------------------------------------


rfkill list:

0: compal-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: compal-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
------------------------------------------------------------------------------------

lsmod:

Module                  Size  Used by
snd_hda_codec_realtek    55125  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
b43                   356470  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
dell_laptop            17808  0 
compal_laptop          19199  0 
dcdbas                 14448  1 dell_laptop
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
rfcomm                 53664  0 
bcma                   42043  1 b43
coretemp               13195  0 
bnep                   18895  2 
bluetooth             342206  10 bnep,rfcomm
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
mac80211              546051  1 b43
joydev                 17101  0 
serio_raw              13230  0 
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  2 b43,mac80211
i915                  705659  3 
lpc_ich                16864  0 
drm_kms_helper         47182  1 i915
jmb38x_ms              18222  0 
memstick               16174  1 jmb38x_ms
drm                   244037  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
video                  18903  1 i915
parport_pc             31981  0 
mac_hid                13037  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
r8169                  61562  0 
ssb                    51854  1 b43
mii                    13654  1 r8169
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci

---

### Post by varunendra on 2014-08-25
Have you installed the firmware required by the b43 driver? With a wired connection -
```
sudo apt-get install linux-firmware-nonfree
```
Reboot.

If you have already installed it, does scanning for networks manually, then attempting to connect to the desired network help? That is -
```
sudo iwlist scan
```
..then, assuming it detects available networks after this, try connecting to the desired one.

If this helps, we can make it automatic so you don't have to run 'iwlist scan' manually.

If it doesn't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by ruberad on 2014-08-25
Thank you for the tips, I did not do anything different between my two installs of 14.04 (with a 12.04 install in-between), and wireless worked on my first 14.04 install. I will give a try to linux-firmware-nonfree and see if iwlist scan shows anything, but before the result was:
```

> sudo iwslist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

I'll also try the wireless_script and post results...thanks!

---

### Post by praseodym on 2014-08-25
You need this firmware file for the low-power chipset LP-PHY:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by varunendra on 2014-08-25
> **ruberad said:**
> ..I did not do anything different between my two installs of 14.04 (with a 12.04 install in-between), and wireless worked on my first 14.04..

..which means you were using the proprietary "wl" driver that works in Live mode, needs to be installed manually on an installed system, gets automatically installed during OS installation if you select the "Install Updates" options during installation,.... and .... is quite often more trouble than a solution.

The native "b43" is the recommended driver for your card, and what I or praseodym suggested would install the proprietary firmware that it requires to work. The 'linux-firmware-nonfree' and what praseodym suggested are just two different ways (besides some others) that lead to the same solution - getting you the required firmware.

---

### Post by ruberad on 2014-08-26
Bingo!

I tried first
```
sudo apt-get install install linux-firmware-nonfree
```
and rebooted, and everything was back the same as before. I didn't get a chance to try the praseodym solution, which apparently might equivalently work. Thank you so much! This is such a simple and I bet common solution, it should be up near the beginning of the wifi troubleshooting page (or was it there somewhere and I missed it?)

So then what happened is I forgot to check "install updates" on that final install? Should I reinstall, or will everything work itself out with regular updates?

---

### Post by varunendra on 2014-08-26
> **ruberad said:**
> Bingo!
Sweetest word in the entire world!! 8-)

> **ruberad said:**
> This is such a simple and I bet common solution, it should be up near the beginning of the wifi troubleshooting page (or was it there somewhere and I missed it?)
That is mentioned in the sticky thread : [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
So yes, a common fix and has been placed in the 'read-and-try-it-first' place, not uncommon for users to miss it though.

> So then what happened is I forgot to check "install updates" on that final install? Should I reinstall, or will everything work itself out with regular updates?
Yes, you must have 'forgot' (for good) to check the "install updates" option while installing the OS. You can install the essential updates anytime later once the OS is installed (you are automatically prompted for that if you are connected to internet and updates are available). The only difference is that these 'later' updates don't automatically install device drivers without asking you first.

The proprietary drivers, if available, are offered on an installed system by the "Additional Drivers" program, and it may still ask you to install the "wl" driver *(also called STA driver, package name "bcmwl-kernel-source")*. But now that your native driver is working fine as expected, I strongly suggest to NOT accept that offer of STA driver by the "Additional Drivers" option. You can even disable its prompt from "Software Sources" if it bothers you.

The current driver needs the firmware to be installed manually only once (on a fresh installation). It is then automatically updated with other updates and you don't need to install it again.

---

