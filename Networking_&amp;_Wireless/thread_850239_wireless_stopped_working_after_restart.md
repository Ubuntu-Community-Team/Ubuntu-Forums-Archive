---
title: "wireless stopped working after restart"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by risknothin on 2008-07-05
My laptop (dell insiron 1525) ran out of batteries and when i restarted the wifi network is not working. the WIFI light is off. How do i turn wifi back on?

---

### Post by risknothin on 2008-07-05
update to my issues: 

wifi did not work when i installed ubuntu 8.04, update of software files and wifi began to work. worked for a few weeks. this morning i could not connect to wifi. 

under hardware drivers the only driver listed is wl <-- which im assuming is the wireless driver. the driver is enabled but states that its status is not in use.

i'm not to familure w/ ubuntu the only thing i can think to do is partition my hard drives to save all my data and do a freash install.

any other ideas?

---

### Post by prshah on 2008-07-05
> **risknothin said:**
> 
wifi did not work when i installed ubuntu 8.04, update of software files and wifi began to work. worked for a few weeks. this morning i could not connect to wifi. 

Open a terminal (Applications-Accessories-Terminal), then give the following commands and then check if WiFi is working again. ```

sudo /etc/init.d/networking restart

```

Post back errors, if any.

---

### Post by risknothin on 2008-07-05
* Reconfiguring network interfaces...                                   [ OK ] 



nothing happened. 

is there a way for me to uninstall the driver that ubuntu downloaded for my wireless card and then reinstall it?

---

### Post by prshah on 2008-07-05
> **risknothin said:**
> 
is there a way for me to uninstall the driver that ubuntu downloaded for my wireless card and then reinstall it?

No need to _uninstall_ but we can force reload the driver to check if you get any errors. Can you post the outputs of ```
iwconfig
lsmod
```

---

### Post by risknothin on 2008-07-05
lo        no wireless extensions.

eth0      no wireless extensions.

brian@brian-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  311848  10 
af_packet              27272  2 
i915                   38144  2 
drm                   105896  3 i915
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  2 
cpufreq_ondemand       11152  1 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
dcdbas                 11312  0 
evdev                  14976  7 
serio_raw               9092  0 
psmouse                46236  0 
pcspkr                  4992  0 
sdhci                  21508  0 
snd_hda_intel         440408  3 
mmc_core               59272  1 sdhci
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
sky2                   53892  0 
ieee80211_crypt         8192  0 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  23444  0 
output                  5632  1 video
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 10912  0 
wmi_acer               11076  0 
battery                16776  0 
ac                      8328  0 
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
intel_agp              30624  1 
iptable_nat             9604  0 
nf_nat                 23980  1 iptable_nat
nf_conntrack_ipv4      21904  2 iptable_nat
nf_conntrack           79216  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          4480  0 
iptable_filter          4608  0 
ip_tables              24104  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               23560  2 iptable_nat,ip_tables
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
pata_acpi               9856  0 
ata_generic             9988  0 
ata_piix               24196  0 
ahci                   33028  2 
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
libata                176432  4 pata_acpi,ata_generic,ata_piix,ahci
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               29856  0 
ehci_hcd               41996  0 
usbcore               169904  3 uhci_hcd,ehci_hcd
thermal                19744  0 
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3

---

### Post by risknothin on 2008-07-07
i still cannot get the wireless card to work, it won't turn on.

any ideas?

---

