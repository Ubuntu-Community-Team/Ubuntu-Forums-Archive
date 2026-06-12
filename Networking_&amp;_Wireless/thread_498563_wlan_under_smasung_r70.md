---
title: "wlan under smasung r70"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by marceli_ossi on 2007-07-11
hello everybody,

here is my previuos post [http://ubuntuforums.org/showthread.php?p=2999127#post2999127](http://ubuntuforums.org/showthread.php?p=2999127#post2999127)

I described there all.

My problem is that I want to install intelcard from samsung r70 under ubuntu. Ubuntu didn't recoginze it directly...

Can anybody tell me what shall I do. I'm not so familiar with ubuntu.

I already created interface in etc/networks for my wlan but I got the error
```
wlan0: Error while getting interface flags: no such device
```

additional info : what is in interfaces in etc/networks/
```
auto wlan0
iface wlan0 inet dynamic
    wireless-mode master
    wireless-essid "******************"
    wireless-channel 1
    wireless-key ********************

```

---

### Post by marceli_ossi on 2007-07-12
can anybody support me ???

---

### Post by marceli_ossi on 2007-07-14
in the mean time I'm reading the installation from intel and I'm wondering where can I find 
CONFIG_FW_LOADER ??

---

### Post by marceli_ossi on 2007-07-15
I had also another problem >
in console I wrote % modprobe mac80211 <- result without any problems
then I wrote lsmod>
```
Module                  Size  Used by
mac80211              175364  0 
cfg80211               22920  1 mac80211
nls_iso8859_1           5120  1 
vfat                   14208  1 
fat                    53916  1 vfat
usb_storage            72256  1 
libusual               17936  1 usb_storage
af_packet              23816  0 
nls_cp437               6784  1 
isofs                  36284  0 
udf                    85252  0 
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
ac                      6020  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 10816  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               42500  0 
pcmcia                 39212  0 
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
agpgart                35400  0 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hci_usb                18204  2 
i2c_core               22784  1 i2c_ec
sky2                   43528  0 
bluetooth              55908  7 rfcomm,l2cap,hci_usb
sdhci                  18700  0 
mmc_core               26756  1 sdhci
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
serio_raw               7940  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
ata_generic             9092  0 
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 usb_storage,sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  7 usb_storage,libusual,uvcvideo,hci_usb,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
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


so what I see , I had installed mod80211
but during installing >
```
% tar xvf iwlwifi-0.0.38.tgz
% cd iwlwifi-0.0.38 
% make

```
I got error that no mod80211 header can be found ....

Can anybody tell me what I'm doing wrong

Please people HELP ME !!!!!!!!!!!!!!!!!!

---

### Post by fredj on 2007-07-16
I believer the R70 is a Samsung notebook with a built in Intel wireless chip. Is this correct?
Open a terminal and type sudo lshw -class network. Then post the results here.
Open a terminal and type cd /etc/network
Then type sudo gedit interfaces and post the contents of the interfaces file here.

---

