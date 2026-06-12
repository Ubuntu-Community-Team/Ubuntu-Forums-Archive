---
title: "wireless card"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by xmech on 2007-01-13
i have a d-link wda 1320 wireless networking card. when i go under network my card is not recognized. How do i get my wireless internet set up.

---

### Post by xmech on 2007-01-14
come on someone, must know

---

### Post by tturrisi on 2007-01-14
That card has an atheros chipset, thus needs the linux madwifi drivers.  Run synaptic, enable the multi-universe repositories and install the linux-restricted-modules that match your kernel.  Reboot.

---

### Post by xmech on 2007-01-14
how do i enable multi universe repositories.

i think i already have linux-restricted-modules. have a look at this screenshot

---

### Post by tturrisi on 2007-01-14
post the results of:
uname -r
lspci
lsmod
iwlist

---

### Post by xmech on 2007-01-14
uname -r
2.6.17-10-generic

ispci
bash: ispci: command not found

ismod
bash: ismod: command not found

iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

---

### Post by xmech on 2007-01-14
bump

---

### Post by jimbren on 2007-01-15
That's Lspci and Lsmod.  Except you don't want to use an uppercase L, I'm just showing you the letter.

so it's 

```
lspci
```

and

```
lsmod
```

post the output from these commands.

And remember...be patient.


kisses,

jimbo

---

### Post by tturrisi on 2007-01-15
and come to think of it, forget about using iwlist, do:
iwconfig
(this command IS an "i" not "l".
...and post the contents of /var/log/dmesg after reboot

---

### Post by xmech on 2007-01-15
spci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:09.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)

 lsmod
Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  3 
drm                    74644  4 radeon
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
lp                     12964  0 
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
af_packet              24584  2 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tda9887                18448  0 
tuner                  54828  0 
tsdev                   9152  0 
snd_emu10k1           128288  1 snd_emu10k1_synth
cx8800                 35212  0 
cx88xx                 63908  1 cx8800
ir_common              28548  1 cx88xx
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
snd_intel8x0           34844  1 
i2c_algo_bit           10376  1 cx88xx
snd_rawmidi            27264  4 snd_seq_virmidi,snd_seq_midi,snd_emu10k1,snd_mpu401_uart
snd_ac97_codec         97696  2 snd_emu10k1,snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
sis_agp                 9860  1 
agpgart                34888  2 drm,sis_agp
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
video_buf              27652  2 cx8800,cx88xx
tveeprom               16144  1 cx88xx
v4l2_common            17280  2 tuner,cx8800
compat_ioctl32          2432  1 cx8800
8139cp                 24832  0 
8139too                29056  0 
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
psmouse                41352  0 
analog                 12960  0 
evdev                  11392  2 
pcspkr                  4352  0 
snd_pcm                84612  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
v4l1_compat            15108  1 cx8800
btcx_risc               6280  2 cx8800,cx88xx
mii                     6912  2 8139cp,8139too
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd_page_alloc         11400  3 snd_emu10k1,snd_intel8x0,snd_pcm
serio_raw               8452  0 
gameport               17160  1 analog
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
floppy                 63044  0 
videodev               10752  2 cx8800,cx88xx
snd                    58372  18 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore              11232  1 snd
i2c_sis96x              6660  0 
i2c_core               23424  7 i2c_ec,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom,i2c_sis96x
ext3                  142728  1 
jbd                    62228  1 ext3
ohci_hcd               22532  0 
ehci_hcd               34696  0 
usbcore               134912  3 ohci_hcd,ehci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
sis5513                15368  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

/var/log/dmesg
bash: /var/log/dmesg: Permission denied

sorry for been impatient- i didnt want the message to get lost.

I think its a hardware problem, i just noticed there are 2 leds on the bak of the card, 
one is for power-(and it isnt on)

I am going to change pci slots and see what that does

---

### Post by camlost on 2007-01-28
did this get resolved? because I seem to be having similar problems with my wda-1320 card and I was hoping to just piggyback on this thread.

---

### Post by kb4jhu on 2007-08-26
I a newb to fedora 7.  I have a D-Link Wireless card WDA-1320 I am trying to configure.

I have read and have attempted to load the  two drivers from:  [http://atrpms.net/dist/f7/madwifi/](http://atrpms.net/dist/f7/madwifi/)

1 -- madwifi-devel-0.9.4-38_r2512.fc7.i386.rpm  - madwifi kernel header files

2 -- madwifi-0.9.4-38_r2512.fc7.i386.rpm  - A linux device driver for Atheros chipsets (ar5210, ar5211, ar5212)

Header file (#1) loads as it should.

When I load (#2) device driver I receive -- the error --> madwifi-kmdl-1:0.9.4-38-r2512.fc7 needed.

I went the RPM site and no such driver exists.  How do I resolve the dependency error?

V/R

-Michael KB4JHU

---

