---
title: "WG111v2 Stopped working w/ Gutsy upgrd on Compaq F579WM"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by LavianoTS386 on 2007-09-24
I upgraded Ubuntu from 7.04 to 7.10 Tribe 5 a few nights ago and discovered that my USB wireless dongle isn't being picked up by the network manager.

It used to be in Feisty that when I would put it in, it would just work. The device correctly shows up in the hardware manger though, so it clearly sees it. I plugged WG111v2 into my desktop (also using tribe 5) which uses similar hardware, (AMD 64, nforce4, nvidia 6600) and it takes off like a rocket, so it's clearly not that gutsy doesn't support it, or that the USB device isn't working.

I had bought the WG111v2 (netgear) to make up for the poor support for my integrated broadcom 4311 device, which even using the cutter program, only got me far enough to activate the light and nothing else.

I suspect it has something to do with the integrated wireless preventing the WG111x2. I tried blacklisting the broadcom driver, and I don't have the restricted firmware activated, yet still my USB device will not activate.

Is there anything i possibly haven't though of yet? I would prefer to not use ndiswrapper. The WG111v2 worked before, and I'd rather not resort to that (and I did try that once already and it failed)

FYI

I used noapic to install gutsy (as I did with Feisty). 

When I boot, the splash screen disappears for a short time and says something about the network manager, but it's not on the screen long enough to read.

The nvidia wired network connections work fine.

---

### Post by kevdog on 2007-09-24
Since you upgraded the kernel with your upgrade to Gusty, its likely you dont have the kernel module loaded (driver installed) or even the kernel module shipped with the new kernel.  Do you know the chipset of the USB stick, or how did you install drivers for the stick when you first bought it??

If you would have used ndiswrapper the same thing would have happened, but the fix for this would have been easy.

---

### Post by LavianoTS386 on 2007-09-24
^ I ran the update manager with -d in terminal. I thought it might have been the upgrade, so I then did a fresh install and it turns out the same way. Like I said I used to plug the thing in and it would work no configuring needed. When I tried it on my desktop, Tribe 5 recognized it and it worked.

Here's some additional information

lsusb:
> 
Bus 002 Device 002: ID 0930:6540 Toshiba Corp. 
Bus 002 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 15ca:00c3  
Bus 001 Device 001: ID 0000:0000  


sudo lshw -C network:
>   *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


Edit to add: **kevdog** I changed my wording to make my point clearer. Sorry for that confusion. Ndiswrapper did not work.

---

### Post by kevdog on 2007-09-24
Seems like I found the following:

The Netgear WG111 v2 USB card, contains a Realtek chipset

Can you post your /etc/modprobe.d/blacklist file???

Also do a lsmod -- this will list kernel modules loaded -- do you see anything like r8187 or something similar??

Does
modinfo r8181 or 818x list anything?

---

### Post by LavianoTS386 on 2007-09-24
lsmod:
> Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
isofs                  36412  1 
sr_mod                 17828  1 
usb_storage            72896  2 
libusual               18192  1 usb_storage
ipv6                  274020  10 
binfmt_misc            12936  1 
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
video                  18060  0 
ac                      6148  0 
dock                   10656  0 
battery                11012  0 
container               5504  0 
button                  8976  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
**rtl8187            35328 0 **
mac80211              171016  1 rtl8187
cfg80211                7304  1 mac80211
eeprom_93cx6            3200  1 rtl8187
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
psmouse                39952  0 
pcspkr                  4224  0 
i2c_nforce2             7040  0 
nvidia               4716468  32 
agpgart                35016  1 nvidia
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
k8temp                  6656  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 i2c_nforce2,nvidia
evdev                  11136  6 
ext3                  133768  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  6 
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  2 sr_mod,ide_cd
sata_nv                20612  3 
forcedeth              51592  0 
ehci_hcd               36108  0 
ohci_hcd               22916  0 
ata_generic             8452  0 
libata                124528  2 sata_nv,ata_generic
scsi_mod              147084  5 sr_mod,usb_storage,sg,sd_mod,libata
amd74xx                15260  0 [permanent]
ide_core              116548  3 usb_storage,ide_cd,amd74xx
usbcore               138248  7 usb_storage,libusual,rtl8187,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              31944  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40600  0 
commoncap               8320  1 apparmor


could **rtl8187 35328 0 ** be it?

blacklist:
> # This file lists those modules which we don't want to be loaded by
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

#broadcom
blacklist bcm43xx

---

### Post by kevdog on 2007-09-24
Ok, so it looks like the OS is loading the r8187 module.  Thats a good sign.

What is the output of the following:
iwlist scan
ifconfig -a
cat /etc/networking/interfaces

---

### Post by LavianoTS386 on 2007-09-24
Iwlist scan : says that lo & eth0 don't support scanning

ifconfig -a 
> eth0      Link encap:Ethernet  HWaddr 00:1B:24:4F:76:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

cat /etc/networking/interfaces

doesn't work it says no such file or directory.

---

### Post by kevdog on 2007-09-24
Sorry its /etc/network/interfaces

What does /etc/iftab show?

Also can you look at dmesg (just type this in the command line) and see if there is anything mentioned about your USB device.

---

### Post by LavianoTS386 on 2007-09-24
dmesg
> 0 (level, low) -> IRQ 10
[   20.152000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   20.272000] ieee80211_init: failed to initialize WME (err=-17)
[   20.300000] rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   20.300000] rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   20.300000] rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   20.300000] rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   20.300000] wmaster0: Failed to select rate control algorithm
[   20.300000] wmaster0: Failed to initialize rate control algorithm
[   20.412000] rtl8187: Cannot register device
[   20.412000] rtl8187: probe of 2-1:1.0 failed with error -2
[   20.412000] usbcore: registered new interface driver rtl8187
[   20.692000] lp: driver loaded but no devices found


> /etc/network/interfaces: command not found

> bash: /etc/iftab: No such file or directory


---

### Post by LavianoTS386 on 2007-09-25
any guess why it can't register the device?

---

