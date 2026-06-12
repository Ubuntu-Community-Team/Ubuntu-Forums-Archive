---
title: "Dell Wireless 1450 USB"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by imagoth2004 on 2008-11-26
So I originally posted this issued on launchpad, and I still haven't heard from anyone, so I decided to post here... Originally when I installed Ubuntu my wireless works. However, it drops connection a LOT. Usually when there is a sudden change in the environment (walking between the line of my router in the living room and to the wireless card in my room, or when I close the door.) so I figured it might help if I installed the drivers that came with my cd. So I installed ndisgtk, and the other two programs it automatically puts on when you install it with Synaptic Package Manager. I copied the drivers (all of them on the disc) to a folder I made on the root of the file system. Then I used Windows Wireless Drivers when it installed during the ndis stuff, and it installed fine... So I figured that's all I needed to do since that's all it said online, so I went to reboot, and when I got back into the system it says that my wireless isn't connected at all. I checked iwconfig, and it's non-existent. So I uninstalled the driver, and rebooted then still nothing. Then I uninstalled the 3 ndis programs, and still nothing. I'm still a beginner with anything linux related, so help a /b/rotha out?

PC: Compaq Presario: SR1911X
Wireless model: Dell wireless 1450 Wireless USB adapter: 413c:8104
Ubuntu 8.10
Kernel: 2.6.27-7-generic x86_64

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:f6:b5:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55840 (55.8 KB)  TX bytes:55840 (55.8 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Module                  Size  Used by
nls_iso8859_1          13568  1 
nls_cp437              15232  1 
vfat                   21120  1 
fat                    64824  1 vfat
binfmt_misc            18700  1 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
rfcomm                 51104  0 
sco                    20612  2 
l2cap                  33280  6 bnep,rfcomm
bluetooth              70820  6 bnep,rfcomm,sco,l2cap
ppdev                  16904  0 
powernow_k8            23684  0 
cpufreq_ondemand       16400  1 
cpufreq_userspace      12420  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    16392  0 
container              12288  0 
video                  28948  0 
output                 11776  1 video
wmi                    15808  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
psmouse                51612  0 
serio_raw              14596  0 
pcspkr                 11136  0 
k8temp                 13568  0 
snd_hda_intel         489264  3 
snd_usb_audio         107776  1 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
snd_usb_lib            27264  1 snd_usb_audio
snd_hwdep              16904  1 snd_usb_audio
ndiswrapper           253696  0 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  2 snd_usb_lib,snd_seq_midi
wacom                  29824  0 
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
evdev                  20512  9 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  19 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
i2c_nforce2            15752  0 
nvidia               7804864  36 
i2c_core               36128  2 i2c_nforce2,nvidia
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usb_storage            92864  1 
sd_mod                 45864  5 
crc_t10dif             10240  1 sd_mod
libusual               31784  1 usb_storage
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sg                     45408  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
sata_nv                35208  2 
pata_amd               22020  0 
ata_generic            14212  0 
pata_acpi              13568  0 
forcedeth              68112  0 
libata                200160  4 sata_nv,pata_amd,ata_generic,pata_acpi
ohci_hcd               34972  0 
ehci_hcd               48908  0 
scsi_mod              183160  5 usb_storage,sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
usbcore               175376  10 snd_usb_audio,snd_usb_lib,ndiswrapper,wacom,usb_storage,libusual,usbhid,ohci_hcd,ehci_hcd
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3

---

### Post by imagoth2004 on 2008-11-27
:/ It's a shame no one is helping here. I decided to just reinstall ubuntu and run off of the generic driver it's using. Is there a way to make ubuntu change drivers, or at least give me a less confusing installation guide on what to do. I'm really getting sick of losing connection when I walk through my door to use the bathroom.

---

### Post by imagoth2004 on 2008-11-27
I'm srsly at the point of just going back to XP. Even though I hate Windows as long as I have a steady, normal speed connection without having to unplug the adapter ever 5-10 min I'd be willing.

---

### Post by Dareajoe on 2008-11-27
How can I make my dell wireless 1450 wireless USB adapter not lag so much.....?In a game such as Runescape by Jagex Ltd, I get a very annoying 8 second delay whenever I command my character to move to a targeted position. Please help...!thanks..

---

### Post by Ayuthia on 2008-11-28
> **imagoth2004 said:**
> :/ It's a shame no one is helping here. I decided to just reinstall ubuntu and run off of the generic driver it's using. Is there a way to make ubuntu change drivers, or at least give me a less confusing installation guide on what to do. I'm really getting sick of losing connection when I walk through my door to use the bathroom.

If you are losing connection when you are walking through your door, it sounds like your wireless is getting interference.  Are there other routers out there that are using the same channel or are there any electronic devices that might be causing the interference?  Even though you are having no problems in Windows, Windows is using a different driver so the results are different.

---

### Post by imagoth2004 on 2008-11-28
Problem solved. I looked more into it, and found that the only driver for the wireless adapter (the one I'm using) Is 32-bit only. So I installed the 32-bit OS, and reinstalled ndiswrapper. Everything is fine now. No drops or anything. It would be nice if someone could remake the ndiswrapper list and post if it's a 32 or 64 bit driver though. :/

---

