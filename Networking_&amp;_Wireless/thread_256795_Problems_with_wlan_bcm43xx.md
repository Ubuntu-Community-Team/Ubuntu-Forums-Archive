---
title: "Problems with wlan bcm43xx"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by martinrandau on 2006-09-13
Hi,
I run the k8 kernel on a HP amd64. I know the wlan can work under linux because I got it working with ndiswrapper under suse without any problems. 

I have used the howto to get my broadcom wireless card working with bcm43xx-fwcutter. But it doesn't work and I get the following errors after rebooting:

dmesg | tail: 
```
[  202.750471] handlers:
[  202.750474] [<ffffffff880ad860>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  202.750490] Disabling IRQ #7
[ 1231.151349] printk: 1 messages suppressed.
[ 1231.151355] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.152440] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.165102] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.166235] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.179108] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.179307] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.193394] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.209101] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.210123] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1231.223100] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1236.540523] printk: 15 messages suppressed.
[ 1236.540528] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1236.544830] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1247.807781] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1247.808237] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1247.833539] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1256.425779] printk: 22 messages suppressed.
[ 1256.425784] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1256.426850] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
```

lsmod: 
```
Module                  Size  Used by
rfcomm                 44512  0
l2cap                  29376  5 rfcomm
ppdev                  10760  0
powernow_k8            12480  1
cpufreq_userspace       8544  1
cpufreq_stats           7624  0
freq_table              5888  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_ondemand        9128  0
cpufreq_conservative    10408  0
video                  18248  0
tc1100_wmi              8520  0
sony_acpi               6548  0
pcc_acpi               15488  0
hotkey                 13128  0
dev_acpi               14724  0
container               5696  0
button                  8288  0
acpi_sbs               24024  0
battery                11656  1 acpi_sbs
ac                      6600  1 acpi_sbs
i2c_acpi_ec             6400  1 acpi_sbs
i2c_core               26048  1 i2c_acpi_ec
nls_utf8                3008  1
ntfs                  100736  1
dm_mod                 62536  1
md_mod                 76152  0
sr_mod                 19108  0
sbp2                   27268  0
parport_pc             40176  0
lp                     14464  0
ipv6                  298240  10
parport                43532  3 ppdev,parport_pc,lp
joydev                 12544  0
arc4                    2816  1
hci_usb                19604  2
ieee80211_crypt_wep     6784  1
tsdev                   9600  0
bluetooth              58116  7 rfcomm,l2cap,hci_usb
usbhid                 42400  0
snd_hda_intel          21088  1
snd_hda_codec         190344  1 snd_hda_intel
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
psmouse                39748  0
pcspkr                  3016  0
sdhci                  16448  0
mmc_core               34884  1 sdhci
snd_pcm               104008  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
serio_raw               9156  0
snd_timer              28424  1 snd_pcm
snd                    68000  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  1 snd
snd_page_alloc         13328  2 snd_hda_intel,snd_pcm
af_packet              27020  4
bcm43xx               126668  0
ieee80211softmac       32000  1 bcm43xx
ieee80211              38664  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7872  2 ieee80211_crypt_wep,ieee80211
shpchp                 50720  0
pci_hotplug            32592  1 shpchp
sg                     43056  0
evdev                  13888  2
ext3                  145360  1
jbd                    70312  1 ext3
ide_generic             2176  0
ohci_hcd               23044  0
forcedeth              33868  0
ohci1394               36684  0
ieee1394              368472  2 sbp2,ohci1394
ehci_hcd               35592  0
usbcore               146428  5 hci_usb,usbhid,ohci_hcd,ehci_hcd
ide_cd                 35104  0
cdrom                  40568  2 sr_mod,ide_cd
generic                 6724  0
sd_mod                 20864  4
amd74xx                16496  0 [permanent]
sata_nv                11972  7
libata                 84960  1 sata_nv
scsi_mod              159928  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                15884  0
processor              29160  2 powernow_k8,thermal
fan                     5832  0
capability              6536  0
commoncap               9088  1 capability
vga16fb                14480  1
cfbcopyarea             4544  1 vga16fb
vgastate                9792  1 vga16fb
cfbimgblt               3584  1 vga16fb
cfbfillrect             5184  1 vga16fb
fbcon                  42496  72
tileblit                3520  1 fbcon
font                    9344  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3136  1 bitblit
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"randaunet"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
 
I have looked around the forums but haven't found any solution.

Please help!

---

### Post by crusty_collins on 2006-09-16
I have the same card,  Try to add the
```

iwconfig eth2 ap $mac_of_router 


```
Also I had to add my wifi card to /etc/iftab
```
eth2 mac 00:16:B6:12:A4:25 arp 1
```

---

### Post by lupine_nickt on 2006-09-17
There's some sort of conflict going on with your IRQs. Post the contents of the file /proc/interrupts - and disable whatever is on the same number as your wlan card, if you can (that should fix it)...

xF,

...Nick

---

### Post by sjieke on 2006-09-19
Hello,

I have also a bcm43xx wireless card and I got it working using ndiswrapper and blacklisting the bcm43xx driver.

Go to the wiki for detailed instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

---

### Post by martinrandau on 2006-09-19
Hi, 
yes it was that guide that I followed over and over again. I tried ndiswrapper 32-bit and 64-bit as well as bcm43xx with fwcutter 32-bit and 64-bit but nothing worked. As I was in a hurry getting it fixed (it was my gf's computer and she was leaving for England) I installed suse and got it working easily with ndiswrapper. 

Too bad I didn't know how to fix irq conflicts as that was the first thing that came to my mind when I saw the errors... 

Thanks for the help, anyway!

---

### Post by trubblemaker on 2006-10-17
fyi there is a boot setting that you can you to detect irq conflicts, can remember it off the top of my head, but I had an issue with an old CDROM drive that insisted on messing with my IRQ's so I learnt if for a while.

a google search will sort it out for you.

---

### Post by veugelenw on 2007-08-08
I have the same issue, using the same card:


```

[ 2013.516000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2013.516000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2073.520000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2073.520000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2073.520000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2133.520000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2133.520000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2193.524000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2193.524000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2193.524000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2253.524000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2253.524000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

```

---

### Post by wareagle on 2008-03-01
> **lupine_nickt said:**
> There's some sort of conflict going on with your IRQs. Post the contents of the file /proc/interrupts - and disable whatever is on the same number as your wlan card, if you can (that should fix it)...


How do I disable such a device?  Also, is it possible to change the IRQ?

FYI, I figured out my modem has been causing this problem (along with others) since I had to use an unsupported driver to get it working.

---

### Post by kaginken on 2008-03-01
Try just blacklisting your modem - assumming you don't use dial-up anymore...  ;D

---

### Post by wareagle on 2008-03-01
I don't generally but I needed it last week for a networking class that I was in.  I was trying to observe TCP slow start, retransmissions, and Nagel's algorithm, which show up a lot more on a low-bandwidth connection.  =)

Also, I sometimes use it if I travel and go someplace that (God forbid) doesn't have wireless.

---

### Post by kaginken on 2008-03-01
You can un-blacklist it very easily by just commenting it out in the blacklist file...it's worth seeing if that is what may be causing your IRQ conflict if that is indeed the source of your woes...

God Speed !

---

### Post by fraterm on 2008-04-05
similar set of error messages here:  

IRQ Conflict here disturbs me, as the IRQ for the eth0 is the same as the bcm43xx

10:    4788683    4677379    XT-PIC-XT        bcm43xx, eth0

How exactly does one resolve an irq sharing conflict such as this properly?

---

