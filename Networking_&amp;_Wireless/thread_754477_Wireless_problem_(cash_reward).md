---
title: "Wireless problem (cash reward)"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by dustin0 on 2008-04-13
I have a hp dv6000 series laptop. Everything else works except for the wireless. This has always been a pain in my rear. I followed this tutorial:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I am offering $15 to the user whoever heps me get this working, if more then one person helps me I can either split it up or just donate the $15 to ubuntuforums.


03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

lshw -C network

```
dustin@tuh2-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:5e:78:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```


ndiswrapper -l

```
dustin@tuh2-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
dustin@tuh2-laptop:~$ 

```

sudo iwlist scanning


```
dustin@tuh2-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

sudo iwconfig

```
dustin@tuh2-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dustin@tuh2-laptop:~$ 
```

---

### Post by Red-Shield on 2008-04-13
this is weird but do you know the name of your net work if so just try as root in a terminal **ifdown **, **ifup**, **iwconfig wlan0 essid "what ever the name is"** and run as root **dhclient**] i would think that should help post what you get and i will help you from there

---

### Post by dustin0 on 2008-04-13
> **Red-Shield said:**
> this is weird but do you know the name of your net work if so just try as root in a terminal **ifdown **, **ifup**, **iwconfig wlan0 essid "what ever the name is"** and run as root **dhclient**] i would think that should help post what you get and i will help you from there 

Didnt seem to work It just changed the iwconfig output to

wlan0     IEEE 802.11g  ESSID:"Dennerbox"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   


I took the password off so its unsecure but it still wont let me connect to any websites and ping doesnt work.

---

### Post by Red-Shield on 2008-04-14
what did you get when you ran sudo dhclient post it and i think i can help you.

---

### Post by dmizer on 2008-04-14
something else is driving your card (not ndiswrapper).  most likely the b43 module, which you'll have to blacklist.  this is not addressed in the howto, as this is a new native module as of Hardy.

shown by your post of lshw posted earlier (highlighted in red):
> **dustin0 said:**
> lshw -C network

```
dustin@tuh2-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       [COLOR="Red"]configuration: driver=b43-pci-bridge latency=0 module=ssb[/COLOR]
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:5e:78:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```
if ndiswrapper was driving your card, it would say something like this:
```
configuration: driver=bcmwl5 latency=0 module=ndiswrapper
```

you should check by looking at the modules under lsmod, but i believe these are the modules you'll have to include in your /etc/modprobe.d/blacklist:
```
blacklist b43
blacklist rfkill_input
blacklist mac80211
```

if that doesn't get you working, please post the output of lspci and lsmod.

---

### Post by dustin0 on 2008-04-14
After I added those to the blacklist file and restarted when i right click on the network manager the enable wireless is gone so it seems that i did something wrong or I wasnt suppose to do that.

lsmod

```
dustin@tuh2-laptop:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
snd_hda_intel         344088  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
sdhci                  19076  0 
video                  20112  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                40336  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
ac                      6916  0 
i2c_nforce2             7680  0 
battery                14212  0 
agpgart                34760  0 
wmi_acer                9644  0 
amd74xx                10000  0 [permanent]
k8temp                  6656  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  1 i2c_nforce2
ide_core              113996  1 amd74xx
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
pata_amd               14212  0 
ata_generic             8324  0 
ohci_hcd               25348  0 
ohci1394               33584  0 
ehci_hcd               37516  0 
sata_nv                27528  2 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
usbcore               146028  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
forcedeth              51980  0 
libata                159344  4 pata_amd,ata_generic,sata_nv,pata_acpi
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ssb                    32772  0 
thermal                16796  0 
processor              36872  4 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
dustin@tuh2-laptop:~$ 

```

lspic

```
dustin@tuh2-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
dustin@tuh2-laptop:~$ 

```

---

### Post by kevdog on 2008-04-14
Baiting people to help you by offering some bogus cash reward should be discouraged.  Its really childish behavior.  If you need help just ask, don't attach childish pleas for help!

---

### Post by dmizer on 2008-04-14
nope, you did everything just perfect.  just missed a module that still needs to be blacklisted.

add:
```
blacklist ssb
```
to /etc/modprobe.d/blacklist ... and try again.

---

### Post by KB3MKD on 2008-04-14
this may sound stupid, but on my acer laptop, there is a lighted button to enable/disable the wireless card.  It's supposed to be lighted when wieless is enabled.  the light doesn't operate correctly in Linux.  Several times the light was on when the wireless card was disabled, and it was off when I was reading this even though I was using the card.  The point is try hitting your button, and don't trust the light.

I also am using the b43legacy driver, not ndiswrapper, and it works.

---

### Post by dustin0 on 2008-04-14
> **dmizer said:**
> nope, you did everything just perfect.  just missed a module that still needs to be blacklisted.

add:
```
blacklist ssb
```
to /etc/modprobe.d/blacklist ... and try again.

Now when I do "iwconfig" the wlan0 device doesnt show up and the only networking option is wired.
Dont know if its suppose to do this or not.

---

### Post by dmizer on 2008-04-14
post:

```
lsmod | grep ndiswrapper
```

and (again)
```
lshw -C network
```

---

### Post by dustin0 on 2008-04-14
```
dustin@tuh2-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd
dustin@tuh2-laptop:~$ 
dustin@tuh2-laptop:~$ 
dustin@tuh2-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
dustin@tuh2-laptop:~$ 


```

---

### Post by dmizer on 2008-04-15
it still shows the ssb module is driving your card.  are you sure you have it blacklisted?

try the output of:
lsusb

again, just to make sure.

---

### Post by dustin0 on 2008-04-16
> **dmizer said:**
> it still shows the ssb module is driving your card.  are you sure you have it blacklisted?

try the output of:
lsusb

again, just to make sure.


This is my blacklist file and its on there unless i put it in wrong

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
blacklist b43
blacklist rfkill_input
blacklist mac80211
blacklist ssb
```

```
dustin@tuh2-laptop:~$ lsusb
Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dustin@tuh2-laptop:~$ 


```

---

### Post by Bosk22 on 2008-04-16
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

Keep the cash - Linux is free and so is the advise

Bosk

---

### Post by dustin0 on 2008-04-16
> **Bosk22 said:**
> [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

Keep the cash - Linux is free and so is the advise

Bosk

Thanks for posting however Im just going to give up on this. Until I get a desktop ubuntu just isnt for me. 

Time to rm -rf * everything

---

