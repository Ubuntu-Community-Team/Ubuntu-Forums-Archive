---
title: "[SOLVED] lost eth0 connection"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by j.ameriks on 2007-09-04
Hi all, hoping you can help me with this issue. I am a relative newbie to linux, but not computers and I really have no idea how to begin troubleshooting this issue.

Installed feisty to dual boot on a Vista desktop and all went ok, including network connection (ie it recognized my network card and I had no issues connecting to the internet). I downloaded all upgrades to the new kernel (-16) and had no additional issues. Over the ensuing weeks I booted to Vista and to Feisty on multiple occasions, and each time everything went as planned. Then over this weekend, I booted to vista and when I rebooted to feisty, I had lost all internet connection, in fact it appears as though feisty no longer starts my NIC at all (NIC light does not come on when ethernet cord is plugged in). However, it works fine in Vista.

I have tried multiple suggestions I hoped would work here, including restarting networking (sudo /etc/init.d/networking restart), dbus (sudo /etc/init.d/dbus restart), and ifdown/ifup. Nothing works -- the NIC shows no signs of life and I don't have a connection.

From here I am lost as to what to do diagnostically. Can anyone please help? Let me know what info to post and how to get it? Any help would be appreciated.

---

### Post by eluzi on 2007-09-04
Have u tried 'lsmod' to check if the NIC drivers r up ? What's the model ?

---

### Post by j.ameriks on 2007-09-04
> **eluzi said:**
> Have u tried 'lsmod' to check if the NIC drivers r up ? What's the model ?

Model is an onboard NIC --  listed as a Realtek RTL-8139/8139C/8139C+ in ubuntu. Motherboard is an ASUS A8AE-LE.

As for lsmod, not sure which module I am looking for. I had the results of lsmod, they are posted below:

```

Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268960  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
powernow_k8            16064  1 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
battery                10756  0 
ac                      6020  0 
button                  8720  0 
video                  16388  0 
sbs                    15652  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
container               5248  0 
dock                   10268  0 
i2c_ec                  6016  1 sbs
nls_utf8                3072  1 
ntfs                  107764  1 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  1 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
usb_storage            72256  1 
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
libusual               17936  1 usb_storage
nvidia               7252756  34 
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
af_packet              23816  4 
i2c_piix4               9740  0 
serio_raw               7940  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_piix4
psmouse                38920  0 
pcspkr                  4224  0 
parport_pc             36388  1 
soundcore               8672  1 snd
ati_agp                10124  0 
k8temp                  6656  0 
parport                36936  3 ppdev,lp,parport_pc
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 nvidia,ati_agp
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  6 
8139too                27648  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ehci_hcd               34188  0 
ohci_hcd               22532  0 
sata_sil               12808  3 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
usbcore               134280  5 usb_storage,libusual,ehci_hcd,ohci_hcd
atiixp                  7440  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
libata                125720  2 sata_sil,ata_generic
scsi_mod              142348  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
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

### Post by eluzi on 2007-09-04
The modules seem to be up, they are those 8139*... Take a peek at /var/log/syslog to check if there's any record of NIC problems...

---

### Post by j.ameriks on 2007-09-04
Eluzi, thank you for your help. Actually I believe I found the solution to this issue (well it worked for me, I am typing this from my feisty install....).

I am not sure how, but my bios settings were changed to disable the NIC card being booted from ROM -- it was being "woken" by the OS at boot. Vista was able to do this, but apparently linux cannot. By changing my BIOS settings to allow for the onboard NIC to be booted from ROM, my connection at login was restored.

Thanks again for your help with this, and I did solve it.

---

