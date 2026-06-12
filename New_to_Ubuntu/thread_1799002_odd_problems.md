---
title: "odd problems"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by blacksheep115 on 2011-07-07
I got 2 problems i was wondering if someone could help me with.  I tried posting in general help area but says i don't have access?  It's been a while since i've logged on so not sure if thats it.  First problem is, i tried to update to a newer version of ubuntu from 8.04 but i'm using a external montior and when it boots into KDE i get on the monitor No RGB Support.  I'm guessing it's because of screen resolution, because the older versions did the same but i could use the fixvesa command and it would fix the xorg.conf file.  On the newer versions i tried editing the xorg.conf (no longer in /etc/X11) and that didn't work neither did copying an old version of the vesa to the new area.  Second problem is on a seperate computer.  I was trying to use the newer comp to test a usb wireless that i couldn't get to work on the older one.  So i disabled the onboard wireless, it worked fine on this computer with the newer kernel/OS.  So when i went to re-enable the wireless in bios i had some problems.  Neither windows or Ubuntu would find the onboard.  So it was a bios problem i figured out after hours of slamming my head against the wall.  So i reinstalled both and it sitll didn't work.  Then in bios i used the command restore to default.  Like 4 or 5 times before finally the card showed up again.  But it only works in windows... in linux it shows in iwconfig/lspci and also the wireless light is on but when i scan for the network it shows none are available.  Any help much appreciated! (sorry to the mods if i wasn't supposed to post here)

---

### Post by jtarin on 2011-07-07
Issue the command and post the results.```
lspci
``` 
Also separately the command ```
lsmod
``` and post.

---

### Post by blacksheep115 on 2011-07-08
hey jtarin thanks for replying, i'm guessing your request for commands is from my new computer since the onboard is pci based.  Here is my results from your commands.  As i said before iwconfig shows it as wlan0, lspci shows it up and lsmod shows broadcomm. But i like i said since i reset defaults in bios a couple times windows now picks it up but ubuntu doesn't even with showing it active and with wlan led on.

lspci
> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
also lsmod shows alot
> Module                  Size  Used by
nls_iso8859_1           3301  1 
nls_cp437               4971  1 
vfat                    8810  1 
fat                    49021  1 vfat
usb_storage            40486  1 
uas                     7524  0 
dm_crypt               14560  0 
snd_atiixp             11935  2 
snd_atiixp_modem        8627  0 
arc4                    1141  2 
snd_ac97_codec        101425  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
ac97_bus                 982  1 snd_ac97_codec
b43                   292690  0 
snd_seq_dummy           1358  0 
snd_pcm                68875  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            26216  0 
snd_seq_midi            4460  0 
snd_rawmidi            18745  1 snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
joydev                  8649  0 
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              248838  1 b43
snd_timer              17835  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              152934  2 b43,mac80211
hp_wmi                  5315  0 
sparse_keymap           3098  1 hp_wmi
snd                    50345  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfkill                 14987  2 cfg80211,hp_wmi
psmouse                52655  0 
soundcore               6016  1 snd
lp                      7373  0 
snd_page_alloc          6769  3 snd_atiixp_modem,snd_atiixp,snd_pcm
wmi                     8740  1 hp_wmi
shpchp                 24986  0 
parport                29468  1 lp
mac_hid                 3029  0                                                                                                                                                     
serio_raw               3712  0                                                                                                                                                     
i2c_piix4               7907  0                                                                                                                                                     
k8temp                  3007  0                                                                                                                                                     
radeon                901424  2                                                                                                                                                     
ttm                    54611  1 radeon                                                                                                                                              
drm_kms_helper         30726  1 radeon
8139too                18772  0 
ati_agp                 5018  0 
usbhid                 35213  0 
drm                   171919  5 radeon,ttm,drm_kms_helper
hid                    67599  1 usbhid
8139cp                 16920  0 
ssb                    37712  1 b43
video                  10930  0 
mii                     4058  2 8139too,8139cp
pata_atiixp             3264  2 
i2c_algo_bit            4852  1 radeon
agpgart                27382  3 ttm,ati_agp,drm 

in second part on the old comp i downloaded htc_9721.fw and put it into firmware dir... If i plug it in it registers but in iwconfig i only get it as wlan%d but can't get wicd to pick it up as that.  It seems to respond just can't find any networks with it.  But if i reboot with it pluged in i get "failed to initialize usb device".
Sorry for so many questions in one post but appreciate all the help.

---

### Post by jtarin on 2011-07-08
What version did you upgrade to? I see you have an ethernet card, can you get a hardwire connection? One of the better ways to get your wireless working is to hardwire connect then Ubuntu will download drivers for your wireless if available. I see you have a broadcom....you might search the forums for that.

---

### Post by blacksheep115 on 2011-07-08
I think you may have misread my problems all together.  The computer in which we are talking about has never had a problem, with the version of ubuntu i'm running now or previous ones.  I only encountered problems when i turned off the onboard wireless to test the usb wireless i was trying to get to work on my older computer.  Like i said it took multiple times resetting the bios to even get windows to find it.  Between the resetting of the bios i had multple freezes.  But finally got it working in windows.  On the older computer i got the wireless usb finally recognized by copying the firmware to the firmware dir.  But it still does not give me a device name just only wlan%d  i can put it into monitor mode but still can't connect to any devices.  For the newer comp it should have nothing to do with drivers or compatability since i've used this computer with onboard for years. Sorry to be a pain but i appreciate the help!

---

### Post by westie457 on 2011-07-08
> **blacksheep115 said:**
> I think you may have misread my problems all together.  The computer in which we are talking about has never had a problem, with the version of ubuntu i'm running now or previous ones.  I only encountered problems when i turned off the onboard wireless to test the usb wireless i was trying to get to work on my older computer.  Like i said it took multiple times resetting the bios to even get windows to find it.  Between the resetting of the bios i had multple freezes.  But finally got it working in windows.  On the older computer i got the wireless usb finally recognized by copying the firmware to the firmware dir.  But it still does not give me a device name just only wlan%d  i can put it into monitor mode but still can't connect to any devices.  For the newer comp it should have nothing to do with drivers or compatability since i've used this computer with onboard for years. Sorry to be a pain but i appreciate the help!

Hi just to add my two cents here. Whenever I have tried to test a usb wireless dongle on my laptop have had to temporarily remove drivers for the on-board chip and had to leave hardware switch for the wireless turned on. Any other way would not work properly on my Acer laptop. I have had both running at the same time with the result that internet speed went down to dial-up speeds. So use one or the other not both at the same time and the on-board wireless must be turned on.

---

### Post by blacksheep115 on 2011-07-08
Hey westie thanks for the post!  I think i'm confusing people, posting to many questions in 1 thread was a bad idea :)  The laptop when i tested the usb the onboard was turned off.  After i removed it, and tried switching the onboard back on is when i started having problems.  Never had them going both at the same time.  But turning it back on is what i think my problem is.  But i just figured if windows could find it, linux should be able to also.  And it's a fresh install of ubuntu and the usb has never been plugged in since i reinstalled... So it shouldn't be the driver?  as always thanks for the help, if you can think of anything else please post.

---

### Post by Miljet on 2011-07-08
> I think i'm confusing people
I think you are correct. I have read the entire thread several times and still don't know what version of Ubuntu, which computer you are having trouble with, which computer you ran the previous commands on, and so forth. 

Jtarin is the best person to help with wireless problems, but I think you are going to have to better explain the problem before anyone can help. Perhaps it would help if you stick to explaining the problem computer?

---

### Post by blacksheep115 on 2011-07-09
Sorry for making a jibberish post Miljet, i'll try to better explain myself and start with 1 problem at a time.
Wireless Problem: (was working before i tested a usb wireless device)
HP laptop
Ubuntu 10.04
Dual boot with windows XP

lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsmod
Module                  Size  Used by
nls_iso8859_1           3301  1 
nls_cp437               4971  1 
vfat                    8810  1 
fat                    49021  1 vfat
usb_storage            40486  1 
uas                     7524  0 
dm_crypt               14560  0 
snd_atiixp             11935  2 
snd_atiixp_modem        8627  0 
arc4                    1141  2 
snd_ac97_codec        101425  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
ac97_bus                 982  1 snd_ac97_codec
b43                   292690  0 
snd_seq_dummy           1358  0 
snd_pcm                68875  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            26216  0 
snd_seq_midi            4460  0 
snd_rawmidi            18745  1 snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
joydev                  8649  0 
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              248838  1 b43
snd_timer              17835  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              152934  2 b43,mac80211
hp_wmi                  5315  0 
sparse_keymap           3098  1 hp_wmi
snd                    50345  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfkill                 14987  2 cfg80211,hp_wmi
psmouse                52655  0 
soundcore               6016  1 snd
lp                      7373  0 
snd_page_alloc          6769  3 snd_atiixp_modem,snd_atiixp,snd_pcm
wmi                     8740  1 hp_wmi
shpchp                 24986  0 
parport                29468  1 lp
mac_hid                 3029  0                                                                                                                                                     
serio_raw               3712  0                                                                                                                                                     
i2c_piix4               7907  0                                                                                                                                                     
k8temp                  3007  0                                                                                                                                                     
radeon                901424  2                                                                                                                                                     
ttm                    54611  1 radeon                                                                                                                                              
drm_kms_helper         30726  1 radeon
8139too                18772  0 
ati_agp                 5018  0 
usbhid                 35213  0 
drm                   171919  5 radeon,ttm,drm_kms_helper
hid                    67599  1 usbhid
8139cp                 16920  0 
ssb                    37712  1 b43
video                  10930  0 
mii                     4058  2 8139too,8139cp
pata_atiixp             3264  2 
i2c_algo_bit            4852  1 radeon
agpgart                27382  3 ttm,ati_agp,drm

fixed it "rfkill unblock wifi"

---

### Post by blacksheep115 on 2011-07-09
Problem 2
Older Computer
Athlon 64 2ghz
Ubuntu 8.04
Wireless Problems: (trying to get usb device to work)
If the computer is turned on and the usb is plugged in, the computer finds it but labels it wlan%d in iwconfig.  If i boot the computer with usb plugged in already it says Usb can't be initialized.

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046e:5520 Behavior Tech. Computer Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9030 NetGear, Inc.
Bus 001 Device 002: ID 05dc:a740 Lexar Media, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
sg                     19941  0
sbs                     8449  0
sbshc                   2600  1 sbs
video                  15442  0
output                  1288  1 video
cpufreq_powersave        626  0
cpufreq_ondemand        6601  0
cpufreq_stats           3065  0
freq_table              1999  2 cpufreq_ondemand,cpufreq_stats
cpufreq_performance      630  0
cpufreq_conservative     7556  0
iptable_filter           876  0
ip_tables               9295  1 iptable_filter
x_tables               10096  2 iptable_filter,ip_tables
ath9k_htc              51106  0
mac80211              237599  1 ath9k_htc
ath9k_common            1342  1 ath9k_htc
ath9k_hw              264011  2 ath9k_htc,ath9k_common
ath                    11887  2 ath9k_htc,ath9k_hw
cfg80211              136187  3 ath9k_htc,mac80211,ath
rfkill                 11984  1 cfg80211
compat                 11173  3 ath9k_htc,mac80211,cfg80211
led_class               1779  2 ath9k_htc,compat
lp                      7036  0
snd_ca0106             28000  2
snd_ac97_codec         87928  1 snd_ca0106
ac97_bus                 762  1 snd_ac97_codec
snd_pcm_oss            33571  0
snd_mixer_oss          12346  1 snd_pcm_oss
snd_pcm                57794  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
rtc_cmos                7678  0
rtc_core               11351  1 rtc_cmos
rtc_lib                 1526  1 rtc_core
snd_seq_dummy           1015  0
parport_pc             18091  1
ns558                   1687  0
parport                24463  2 lp,parport_pc
gameport                6725  2 ns558
snd_seq_oss            23461  0
snd_seq_midi            3720  0
snd_rawmidi            14527  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      4304  2 snd_seq_oss,snd_seq_midi
option                 14643  0
usbserial              25922  1 option
psmouse                31899  0
serio_raw               3344  0
snd_seq                40162  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_viapro              5123  0
snd_timer              14918  3 snd_pcm,snd_seq
snd_seq_device          4165  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
via_ircc               15966  0
snd                    38765  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                   86535  1 via_ircc
via_agp                 4984  1
shpchp                 25507  0
agpgart                22417  1 via_agp
soundcore               4239  1 snd
snd_page_alloc          5469  2 snd_ca0106,snd_pcm
evdev                   6681  8
pata_acpi               2308  0
pata_via                6579  0
via_rhine              17649  0
ata_generic             2247  0
fuse                   49697  1

---

### Post by Miljet on 2011-07-10
That is a much better explaination of the problems. I am not very knowledgable about wireless problems, especially those involving Broadcom chipsets. Hopefully one of the wireless gurus will come along and offer some help now. This post will at least bump your thread back to the top of the list.

---

### Post by blacksheep115 on 2011-07-12
Yeah i apologize to jtarin, you and westie for my ignorance.  Normally when i'm on to post i've been diping into the sauce a bit. Was not my intention to insult or mislead anyone.  Still stands laptop1 fixed, older computer not so much.  Still hoping for help.  BTW broadcomm chipset has been fixed, now working on the problem 2, which by lsusb i detect is a atheros chipset.  I installed ath9k driver but when computer boots it says usb can't be initalized, when i plug  in usb after boot it finds it in iwconfig as wlan%d.  I can put the wireless into monitor mode but can't connect to anything.  I'm running a older version of ubuntu because the newer ones for some reason don't work on my external monitor, says No RGB support.

---

### Post by jtarin on 2011-07-12
[MadWifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi#Ubuntu%208.04%20%28Hardy%29") has had good results with Atheros chips.

Ubuntu 8.04 (Hardy)

    The drivers are in the _**restricted modules package**_; also see the madwifi-tools package.

     ```
sudo apt-get install linux-restricted-modules madwifi-tools 
```

---

