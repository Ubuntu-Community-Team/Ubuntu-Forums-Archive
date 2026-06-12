---
title: "Need help with Belkin Wireless"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by weatherman1293 on 2007-08-24
On my last install, I foobar'd ubuntu with ndiswrapper, so I'd like to avoid that now.

I need help with getting my Belking F5D ver. 7000 working. 

lspci shows up with:
```
01:06.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

```

A iwconfig shows up with no wireless extensions.

---

### Post by Austin_KW on 2007-08-24
A quick google search reveals your chipset.

700f	Realtek RTL8185L 802.11 b/g Wireless Lan Controller
Belkin Model F5D7000 ver.7000 PCI Card

And a quick search of these forums suggest the windows driver with ndiswrapper
[http://ubuntuforums.org/showthread.php?t=381878&highlight=RTL8185L&page=2](http://ubuntuforums.org/showthread.php?t=381878&highlight=RTL8185L&page=2)

---

### Post by weatherman1293 on 2007-08-24
> **Austin_KW said:**
> A quick google search reveals your chipset.

700f	Realtek RTL8185L 802.11 b/g Wireless Lan Controller
Belkin Model F5D7000 ver.7000 PCI Card

And a quick search of these forums suggest the windows driver with ndiswrapper
[http://ubuntuforums.org/showthread.php?t=381878&highlight=RTL8185L&page=2](http://ubuntuforums.org/showthread.php?t=381878&highlight=RTL8185L&page=2)

OK, but if I have to reinstall Ubuntu...

(At least this time my /home is in a different partition)

---

### Post by weatherman1293 on 2007-08-24
Still a no-go. I even did a modprobe ndiswrapper and I can't see anything along the lines of wireless.

---

### Post by Austin_KW on 2007-08-24
I dont have this chipset. I have a different revision.

Which driver sid you use with ndiswrapper. I saw a post suggesting using the win98 driver from the cd. See [http://ubuntuforums.org/showthread.php?t=491680&highlight=RTL8185L](http://ubuntuforums.org/showthread.php?t=491680&highlight=RTL8185L)

---

### Post by weatherman1293 on 2007-08-24
I saw that also.

I might go back and try that.

As of right now with a Vista driver, iwconfig returns nothing.

---

### Post by weatherman1293 on 2007-08-24
All works now! The trick is to use the WIN98 driver.

I might post the drivers needed in the wiki with an entire guide.

---

### Post by weatherman1293 on 2007-08-24
Now that I rebooted again, it likes freezing periodically, and it won't connect.

It sees my network, but when I click on it nothing happens.

---

### Post by weatherman1293 on 2007-08-24
bump

---

### Post by kevdog on 2007-08-24
Can you post the following:

lshw -C network
/etc/modprobe.d/blacklist

Unfortunately your chipset is a pain in the a$$

---

### Post by weatherman1293 on 2007-08-24
LSHW:

```
  *-network:0 DISABLED    
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 6
       bus info: pci@01:06.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:2e:69:db
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.47+Realtek,02/01/2007,5.1097.0 latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: ioport:c800-c8ff iomemory:ed003000-ed0031ff irq:18
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:12:0c:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.101 latency=32 multicast=yes
       resources: iomemory:ed000000-ed001fff irq:20

```

Blacklist:
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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
```

> **kevdog said:**
> 
Unfortunately your chipset is a pain in the a$$
You can say that again, seeming this is my 3rd install trying to get it to work.

---

### Post by weatherman1293 on 2007-08-24
```
*-network:0 DISABLED    
```

That would probably be the problem, how to go about enabeling?

---

### Post by kevdog on 2007-08-24
Is your wireless device turned on?? or do you see lights on with the device??

The only reason Im asking is the following:
```
 *-network:0 DISABLED  
```

It appears as if you have ndiswrapper and the rtl8187 driver installed.  Disabled to me seems to suggest the device might be turned off, either in the bios, or a switch or some key combination.  If Im totally wrong, do:

dmesg | more

And look for any section relating to your card, or wlan0.

And try not running wired and wireless together, meaning reboot without the ethernet cable plugged -- not sure if that will help, but its worth a shot!

---

### Post by weatherman1293 on 2007-08-24
```

[  214.921060] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  221.884078] ndiswrapper (mp_reset:62): wlan0 is being reset

```

---

### Post by kevdog on 2007-08-24
Ok -- anything more that might help such as the reason its not ready??

Are you sure the device is turned on??

---

### Post by weatherman1293 on 2007-08-24
I'm positive as it works in Windows

---

### Post by kevdog on 2007-08-24
Are there lights that are lit on the card??  or anything else in dmesg?

---

### Post by weatherman1293 on 2007-08-25
After a couple of reboots, it works now.

Must be something within the system config.

---

### Post by Austin_KW on 2007-08-25
use the command "lsmod" to list the drivers loaded. Freezing/"sometimes working"  is often a sympton of conflicting drivers perhaps a native and a windows driver trying to manage the device.

---

### Post by weatherman1293 on 2007-08-25
My god, if a native driver's trying to run the show, it should have done that before the windows driver got installed.

---

### Post by weatherman1293 on 2007-08-25
```

Module                  Size  Used by
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
i915                   24448  4 
drm                    81044  5 i915
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
container               5248  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
battery                10756  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
nls_utf8                3072  1 
ntfs                  107764  1 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
lp                     12452  0 
fuse                   46612  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
xpad                    9988  0 
usblp                  14848  0 
snd_emu10k1           121248  1 snd_emu10k1_synth
snd_intel8x0           34332  1 
snd_ac97_codec         98464  2 snd_emu10k1,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
emu10k1_gp              4736  0 
ndiswrapper           188252  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
gameport               16520  2 emu10k1_gp
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
parport_pc             36388  1 
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
psmouse                38920  0 
snd                    54020  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_page_alloc         10888  3 snd_emu10k1,snd_intel8x0,snd_pcm
serio_raw               7940  0 
i2c_i810                6276  0 
i2c_algo_bit            8712  1 i2c_i810
intel_agp              25244  1 
i2c_core               22656  3 i2c_ec,i2c_i810,i2c_algo_bit
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35400  3 drm,intel_agp
af_packet              23816  8 
joydev                 10816  0 
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  6 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
usbhid                 26592  0 
hid                    27392  1 usbhid
floppy                 59524  0 
ata_piix               15492  5 
b44                    28044  0 
mii                     6528  1 b44
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sd_mod,sg,sr_mod,libata
ohci_hcd               22532  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  8 xpad,usblp,ndiswrapper,usbhid,ohci_hcd,ehci_hcd,uhci_hcd
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

---

