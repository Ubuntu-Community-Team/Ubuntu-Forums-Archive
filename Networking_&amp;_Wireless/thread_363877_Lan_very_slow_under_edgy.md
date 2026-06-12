---
title: "Lan very slow under edgy"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by MasterZ on 2007-02-17
Hello, 

I have a problem with my LAN connection which is very slow under ubuntu. 

When I try to watch a DVD from a windows server box in another room and the DVD is in the DVD player of the ubuntu PC (I have only 1 dvd player :) ) the sound ans video are very choppy. 

If I boot the DVD player PC in windows, I can see the movie remotely without problems. 

I thought there was a problem in my network configuration and I did a little test : 
I transferred a 1Gb file from this PC to another one. First by using ubuntu, next using windows. 

The result are stunning: 
Windows took 2min 14 sec to transfer 1Gb
Ubuntu took 4min 02 sec to transfer the same file. 

I think I have a problem :-k 

I'm using the on-board lan card of my A8N32-SLI motherboard (nforce4). 

I checked with ethtool that my card was set to 100baseT/Full. This is correct. 

What could I check next ? How do I know which network driver is used ?

Thanks for helping,


MasterZ

---

### Post by gradedcheese on 2007-02-17
off the top of my head -- I would start by disabling IPv6, that might help.  You can see what modules are loaded by running "lsmod" -- look for the nforce driver there.

---

### Post by MasterZ on 2007-02-17
Hi, 

I disabled IPV6, but the results are the same. 

Here's my lsmod output, i do not know what to look at in there:
```

Module                  Size  Used by
isofs                  38076  1 
udf                    89348  0 
smbfs                  71288  4 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nfsd                  234276  13 
exportfs                7296  1 nfsd
lockd                  67976  2 nfsd
sunrpc                165948  8 nfsd,lockd
powernow_k8            15008  2 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  0 
sg                     37404  0 
sr_mod                 18212  1 
nls_iso8859_1           5248  2 
nls_cp437               6912  2 
vfat                   14720  2 
fat                    56348  1 vfat
nls_utf8                3200  4 
ntfs                  112116  4 
it87                   22180  2 
hwmon_vid               4096  1 it87
eeprom                  8208  0 
i2c_isa                 6144  1 it87
sbp2                   24584  0 
lp                     12964  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
sk98lin               191700  0 
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
nvidia               4554836  20 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
agpgart                34888  1 nvidia
sky2                   43012  0 
tsdev                   9152  0 
usb_storage            75072  1 
sata_sil24             12932  0 
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 12960  0 
snd_rawmidi            27264  2 snd_mpu401_uart,snd_seq_midi
i2c_nforce2             8192  0 
libusual               17040  1 usb_storage
psmouse                41352  0 
snd_timer              25348  2 snd_pcm,snd_seq
gameport               17160  1 analog
usbhid                 45152  0 
pcspkr                  4352  0 
evdev                  11392  5 
i2c_core               23424  6 i2c_ec,it87,eeprom,i2c_isa,nvidia,i2c_nforce2
serio_raw               8452  0 
floppy                 63044  0 
shpchp                 42144  0 
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
pci_hotplug            32828  1 shpchp
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd                    58372  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142856  2 
jbd                    62228  1 ext3
ohci1394               37040  0 
ide_generic             2432  0 
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
ieee1394              306104  2 sbp2,ohci1394
forcedeth              32268  0 
ide_cd                 33696  0 
cdrom                  38944  2 sr_mod,ide_cd
ide_disk               18560  11 
generic                 6276  0 
amd74xx                15260  0 [permanent]
sata_nv                11268  0 
libata                 74892  2 sata_sil24,sata_nv
scsi_mod              144648  5 sg,sr_mod,sbp2,usb_storage,libata
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


```

I searched on asus and nvidia website, but i do not find any nforce4 drivers for linux. I thought that i had seen some posts on these forums speaking about installation of nforce drivers. 
Where can I find those drivers? 

MasterZ

---

### Post by MasterZ on 2007-02-18
I found out that the network driver is 'forcedeth'. 
It was version 0.54 with the default edgy installation, I upgraded to forcedeth 0.60. 

Ufortunately the results are the same. 

I also tested with the second integrated NIC on my motherboard. This one is using the sky2 driver. 
The transfer still takes 4+ minutes.  
So it does not seem to be a driver issue. 

I did some other tests : 

rcp the same file from a dapper box to my edgy pc took **1min 40 sec. **
copy the smae file between the two PCs via nautilus and a SMB share took **6 min 20 sec** :confused: 

So, could it be that samba is creating so much overhead that its slowing down the network transfer by a **factor 4 !!**

What could I do to speed up the sharing of files with samba ? 

MasterZ

---

### Post by gradedcheese on 2007-02-18
interesting!  Samba does create a lot of overhead by nature of what it's doing, but I have never measured it myself.  I would however have expected rcp or scp to be much faster, but that's a huge factor that you're seeing.  I'll look around and see if there are performance tips that could be worth applying, you should google around too.

---

### Post by RandomJoe on 2007-02-18
SMB and NFS do have a lot more overhead than just a straight copy with a network-aware tool.  I transfer large files around my LAN frequently, and 'scp' is significantly faster, even with the encryption/decryption overhead, than NFS or SMB ever thought about being.

You can try tuning Samba, I was browsing the Samba docs and various HOWTOs this weekend preparatory to setting up a new server at work and noticed there is a line that can be added which lets you set block sizes and such.  I know on NFS this can make a large difference in performance.  (I've not set up a Samba server yet, I'll get to have that fun in about a week...!)

Here's a link to the "Performance Tuning" appenix of O'Reilly's Using Samba book (found thru Google):
[http://www.oreilly.com/catalog/samba/chapter/book/appb_02.html](http://www.oreilly.com/catalog/samba/chapter/book/appb_02.html)

---

