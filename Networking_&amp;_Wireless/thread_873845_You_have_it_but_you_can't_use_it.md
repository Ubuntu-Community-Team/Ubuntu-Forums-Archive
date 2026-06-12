---
title: "You have it but you can't use it?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by PCessna on 2008-07-29
This one makes me almost cry.

I have three network controllers, A Intel adapter never used, a broadcom wirless and I always use it(in desktop computer not laptop), and some other stupid thing it detecs

So I can't use it, dont know wtf..

So Now I'm searching around, And I go into Driver testing or something, and I go through some random tests, and son of a (blank) right there, all 3 controls, all details, not one digit wrong. I click yes these are mine,,

Do you have connection to internet. No. 

Test over.. WTF???

How do I enable a controller to use it, The only time I saw this bitch show my controller was in some stupid test, please help (im on Windows on same comp atm which seems to always work)

Not details will be provided. Ask Ubuntu :P.. Like I said read below my request pleasse

Thanks very much

---

### Post by PCessna on 2008-07-29
> **PCessna said:**
> This one makes me almost cry.

I have three network controllers, A Intel adapter never used, a broadcom wirless and I always use it(in desktop computer not laptop), and some other stupid thing it detecs

So I can't use it, dont know wtf..

So Now I'm searching around, And I go into Driver testing or something, and I go through some random tests, and son of a (blank) right there, all 3 controls, all details, not one digit wrong. I click yes these are mine,,

Do you have connection to internet. No. 

Test over.. WTF???

How do I enable a controller to use it, The only time I saw this bitch show my controller was in some stupid test, please help (im on Windows on same comp atm which seems to always work)

Not details will be provided. Ask Ubuntu :P.. Like I said read below my request pleasse

Thanks very much
Please respond

---

### Post by chili555 on 2008-07-29
When I respond to a post, I hope there will be some details provided:> Not details will be provided. Ask Ubuntu :PI also hope it will be family friendly. I have no further response.

---

### Post by PCessna on 2008-07-29
> **chili555 said:**
> When I respond to a post, I hope there will be some details provided:I also hope it will be family friendly. I have no further response.

Why respond if you don't know about controllers, It wastes not only my time. I'm so mad right now, I really am. Comon, Please I am only ask for a simple response on how to use a Broadcom wirless control. If you want the model, I don't know what to tell you? 

Windows says the following:
BCM94318MPG (Board)
BCM4318 (Chipset) 
I know no further, Ubuntu just said Broadcom something. If you want to be rude and reply to reply, May I say in my opinion I think it's rude. 

Sorry for my anger and invalid question, But I need a response!

Here:
BCM4318
802.11b/g Transceiver with BroadRange&#8482; Technology
[http://broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E](http://broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E)
I'm now looking as hard as I can, Help with be highly appreciated

Edit 3: It seems there is no driver for my specific chipset, Can someone please help me thank you

---

### Post by PCessna on 2008-07-29
> **PCessna said:**
> Why respond if you don't know about controllers, It wastes not only my time. I'm so mad right now, I really am. Comon, Please I am only ask for a simple response on how to use a Broadcom wirless control. If you want the model, I don't know what to tell you? 

Windows says the following:
BCM94318MPG (Board)
BCM4318 (Chipset) 
I know no further, Ubuntu just said Broadcom something. If you want to be rude and reply to reply, May I say in my opinion I think it's rude. 

Sorry for my anger and invalid question, But I need a response!

Here:
BCM4318
802.11b/g Transceiver with BroadRange™ Technology
[http://broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E](http://broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4318E)
I'm now looking as hard as I can, Help with be highly appreciated

Edit 3: It seems there is no driver for my specific chipset, Can someone please help me thank you
Please respond

---

### Post by kdorf on 2008-07-29
First of all, posting repeatedly like that will not get your question answered. It makes people want to ignore you. Read the link in my signature.

Have you Googled this at all?

Post the content of "lspci" and "lsmod" in the terminal (without quotes).

---

### Post by PCessna on 2008-07-29
First of all, posting repeatedly like that will not get your question 
answered.
So will making it wait for 4+ hours, Community

It makes people want to ignore you. 
No Way!

Read the link in my signature.
Thanks for the tips ¬.¬

Have you Googled this at all?
Yes sir, Spent a good 20 min and got nothing.

Post the content of "lspci" and "lsmod" in the terminal (without quotes).
willdo later. :)

---

### Post by PCessna on 2008-07-29
Took me a big process to get from Linux to Windwos but :)
```
paul@paul-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7500 LE] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
05:00.0 Multimedia controller: ViXS Systems, Inc. Unknown device 2100
07:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem
07:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
paul@paul-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16256  1 
fat                    60592  1 vfat
ipv6                  311848  14 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  0 
cpufreq_ondemand       11152  2 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    10632  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
video                  23444  0 
output                  5632  1 video
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
af_packet              27272  2 
rfkill_input            6528  0 
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
lirc_mceusb2           16900  0 
lirc_dev               18248  1 lirc_mceusb2
b43                   159152  0 
rfkill                 10128  11 rfkill_input,b43
mac80211              192532  1 b43
cfg80211               17680  1 mac80211
led_class               7176  1 b43
input_polldev           6928  1 b43
snd_hda_intel         440408  3 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
i2c_core               28544  0 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
serio_raw               9092  0 
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                46236  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 10912  0 
soundcore              10400  1 snd
shpchp                 38172  0 
intel_agp              30624  0 
heci                   65944  0 
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
pcspkr                  4992  0 
pci_hotplug            34608  1 shpchp
evdev                  14976  13 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
loop                   21508  2 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
ata_generic             9988  0 
sg                     41880  0 
sd_mod                 33280  4 
usb_storage            82496  1 
usbhid                 35296  0 
hid                    44992  1 usbhid
pata_marvell            9472  0 
libusual               23520  1 usb_storage
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
ssb                    39428  1 b43
ahci                   33028  1 
pata_acpi               9856  0 
uhci_hcd               29856  0 
ehci_hcd               41996  0 
libata                176432  4 ata_generic,pata_marvell,ahci,pata_acpi
scsi_mod              178488  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
usbcore               169904  7 lirc_mceusb2,usb_storage,usbhid,libusual,uhci_hcd,ehci_hcd
e1000                 137536  0 
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  5 
paul@paul-desktop:~$ 
```

---

### Post by PCessna on 2008-07-29
What further information do you want? The community is absolutely ```
**ridiculous **
```
I need a response! Please! What do you want out of me?

---

### Post by Sef on 2008-07-29
> I need a response! Please! What do you want out of me?

Have patience.  Everyone here is a volunteer, so at times your post is answered fast and at times slow.  If you want fast help all the time, then [pay]("http://www.ubuntu.com/support/paid") for it.

---

### Post by loell on 2008-07-29
you have **Broadcom Corporation BCM4318 [AirForce One 54g]**

perhaps this post may help you, 

[http://ubuntuforums.org/showpost.php?p=5469730&postcount=13]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")

---

### Post by PCessna on 2008-07-30
> **loell said:**
> you have **Broadcom Corporation BCM4318 [AirForce One 54g]**

perhaps this post may help you, 

[http://ubuntuforums.org/showpost.php?p=5469730&postcount=13]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")

:):)

Thank you very much, worked last night, but I was too tired to get back on forums. I'm finally thanking you from Linux Ubuntu :D

---

### Post by loell on 2008-07-30
glad it worked. :)

---

### Post by omegatotal on 2008-08-02
trying this my self, and it appears to be working! hotdamn!  GREAT POST!

---

