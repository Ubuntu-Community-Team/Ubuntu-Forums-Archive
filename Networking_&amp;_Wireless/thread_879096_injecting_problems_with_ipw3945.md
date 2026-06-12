---
title: "injecting problems with ipw3945"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-08-03
Hi all, i'm trying to enable injecting for my ipw3945.  I tried using backtrack 3 as a live cd, but i couldn't inject on it so i am trying it in my normal install.  i followed this tutorial 
[http://aircrack-ng.org/doku.php?id=ipw3945](http://aircrack-ng.org/doku.php?id=ipw3945)
and it all goes fine until the end, when i type 
sudo modprobe -r ipwraw
and it gives me the message
FATAL: Module ipw3945 not found.

these are the commands i typed in the terminal from the tutorial

sudo apt-get install build-essential
sudo apt-get install libssl-dev
wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2)
tar -xjf ipwraw-ng*
cd ipwraw-ng
make
sudo make install
sudo make install_ucode
echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw
sudo depmod -ae
sudo modprobe -r ipw3945
sudo modprobe ipwraw




also, if i do get injecting working will i have to do all of this from a live cd all over again if i want it to work?

also also, how do you get the little code boxes around code that i type out? it looks better on these posts but i don't know how to do it

---

### Post by shortridge11 on 2008-08-03
whoops, i checked my lsmod and it came out with

Module                  Size  Used by
af_packet              23812  4 
i915                   32512  2 
drm                    82452  3 i915
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ipv6                  267780  12 
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
video                  19856  0 
output                  4736  1 video
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
evdev                  13056  8 
dcdbas                  9504  0 
snd_seq_dummy           4868  0 
serio_raw               7940  0 
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
sdhci                  19076  0 
cfg80211               15112  1 iwlwifi_mac80211
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
mmc_core               51460  1 sdhci
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
battery                14212  0 
ac                      6916  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25492  1 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
soundcore               8800  1 snd
psmouse                40336  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
pata_acpi               8320  0 
b44                    28432  0 
ohci1394               33584  0 
ata_generic             8324  0 
ieee1394               93752  2 sbp2,ohci1394
ssb                    34308  1 b44
mii                     6400  1 b44
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  3 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


and i saw that i'm using iwl3945....doesn't that support injecting?  i still can't inject though

---

