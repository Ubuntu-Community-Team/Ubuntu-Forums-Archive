---
title: "Wireless Working but Can't Connect"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by arlorn on 2007-04-29
Hello. 

I just installed the latest version of Ubuntu Desktop, but I'm having trouble with my wireless connection. 

The problem I'm having is that Ubuntu seems to be able to detect and use the wireless connection, despite my not being able to. When I go into System > Administration > Network, and click on "Properties" for "Wireless Connection", I'm shown a list of wireless routers, mine included, in the area. 

However, after checking "Wireless Connection" and unchecking "Wired Connection", I get a "Server Not Found" page trying to use Firefox. 

**_What I've Tried_**
[LIST]
[*]In my configuration of "Wireless Connection", I've tried both "Roaming mode" and non-"Roming Mode". I've tried DHCP (which seems to work with my "Wired Connection"), and "Static IP" (which doesn't work with either, despite having a static ip). 

[*]Entering in my "Network Name", I see a prompt for my "Password Type". I normally have WPA set on my router (which isn't one of WEP (hex) or WEP (ascii) offered). I've tried not including a password, and tried changing my router to a WEP encryption, both to no avail. 

[*]If I plug in the ethernet cable directly into the computer, and turn my preference from a wireless signal to a "plug in" one, I have no problems. So the internet connection itself is not problematic.

[*]I'm actually switching from Windows, where the connection worked fine on XP, so the wireless hardware should also be working.
[/LIST]

I realize this has probably been covered before. I'm certainly not asking to waste your time walking me through the process, but if anyone could just point me to where I might be able to track down the answer, it would be much appreciated.

Thank you, very much, for your time,
   -Jess

(Edit) Also, regarding hardware, the output from lspci is:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

Also, oddly, whenever I change the encryption on my router to WEP and put in the **correct** password in the Network window, it takes some time before giving me the "Server Not Found" error, whereas if I put an **incorrect** password in, I get the error immediately. This would tend to indicate to me that the password is being accepted or validated, but that something else afterwords is failing. For example:
> 
Network Password: *password*
(Hit Reload on Firefox)
*20 second delay*
"Page Not Found"

> 
Network Password: *passwor*
(Hit Reload on Firefox)
"Page Not Found"


Thanks again,
   -Jess

---

### Post by arlorn on 2007-04-29
I apologize for my ignorance. 

I uninstalled Network manager and went with Wicd, which seems to have solved the problem entirely. 

Thanks to everyone who took the time to read.
    -Jess

---

### Post by JHuizingh on 2007-04-29
Jess, 

Could you post an lsmod so I can see what network drivers you are using?  I have a similar issue which I posted [Here on linuxquestions.]("http://www.linuxquestions.org/questions/showthread.php?t=549742")  It looks like you have the same wireless network adapter, and I'd like to get more information.

Thanks

---

### Post by arlorn on 2007-05-01
Sure. Here's the full printout from lsmod.

```

Module                  Size  Used by
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
sbp2                   23812  0 
uhci_hcd               25360  0 
ohci1394               36528  0 
michael_mic             3584  4 
arc4                    2944  4 
ecb                     4480  4 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  2 
ipv6                  268704  8 
binfmt_misc            12680  1 
speedstep_centrino      9920  0 
freq_table              5792  3 cpufreq_stats,cpufreq_ondemand,speedstep_centrino
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   24448  2 
drm                    81044  3 i915
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
container               5248  0 
ac                      6020  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
asus_acpi              17308  0 
battery                10756  0 
video                  16388  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  1 
ntfs                  107764  1 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
pcmcia                 39212  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ipw2200               148040  0 
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
sdhci                  18700  0 
mmc_core               26756  1 sdhci
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              10240  0 
tifm_core               9856  1 tifm_7xx1
serio_raw               7940  0 
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25116  1 
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  4 
evdev                  11008  1 
tsdev                   8768  0 
ext3                  133128  5 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  8 
ata_piix               15492  7 
8139cp                 25088  0 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394              299448  2 sbp2,ohci1394
8139too                27648  0 
mii                     6528  2 8139cp,8139too
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  3 uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

Admittedly, I'm rather new to certain aspects of Linux myself, so I'm not sure if I would be of any help in solving your problem... but do let me know if there's anything else I can do.

Good Luck,
   -Jess

---

### Post by arlorn on 2007-05-01
By the way, I read through your post on the other forum. I don't care to register there to respond, but it sounds to me like you just have something configured incorrectly. In other words, that you have your router set in one way and your computer's connection set in another.

As I've mentioned, I'm certainly no expert, but from the description you've given I am nearly positive it's that's the problem.

Can you connect to / configure your router at home, or are you on a shared network?

If you can manage your router from home, try disabling the wep encryption temporarily. If you still can't connect then, then I would make absolutely sure that everything was up-to-date on the change by resetting (restarting) the router and whatever network manager you're using (or restarting the computer... though that's more of a windows practice). Try connecting again then. At that point, if you can connect, it's definitely configuration. If you can't, it's probably not. 

Let me know what happens either way. I can, at least, offer my experience with screwing around with my own network for my personal use. 

Good Luck,
   -Jess

---

### Post by JHuizingh on 2007-05-09
Thanks for the feedback.  I did end up getting it fixed (with stuff that was already installed no less).  I first tried to install wicd, but the only version that I saw was for ubuntu 6.10.  It didn't work, so I reinstalled knetworkmanager (i'm using kubuntu).

Doing more research, I found out about this package called wpa_supplicant.  It was already installed on my machine.  I had to change some configurations to make my computer use that for my wireless, and I'm not sure why it isn't enabled by default.  It's possible that I screwed it up before, but I don't think that's the case.

I followed the directions on this page to get it set up:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)


Basically, I think if you run these steps from a default install of kubuntu 7.04 that wep is not working, it should fix the problem if you have the same wireless adapter as me, and maybe some others adapters would work as well.

Here are the steps:

[LIST=1]
[*]edit /etc/network/interfaces.  Replace the code for your wireless interface with                                      the following block, updating the adapter to match yours:

```
auto iface eth1 inet manual
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```
[*]Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
[*]Copy the file /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.template to /etc/wpa_supplicant.conf
[*]sudo /etc/init.d/dbus restart
[*]At this point the default network manager (knetworkmanager) should allow you to set up the wep network.  It will bring up the kde wallet and ask you to enter your password so it can store the wep keys.  Before this happens, you may also have to bring your wireless interface down with ifup/down or ifconfig.  I'm not completely sure because I also restarted the computer in my experimentation.
[/LIST]

Thats it.  I'm a little frustrated that it couldn't do this by default when I installed it, but I'm happy that I could figure out a good solution.  It's also easy to use after the initial setup.

---

### Post by JHuizingh on 2007-05-10
Update:

I HAD it working for a short time, but then I hosed it up somehow.  I've started a new thread [here]("http://ubuntuforums.org/showthread.php?p=2628603") because I seem to be having different issues than you.

---

