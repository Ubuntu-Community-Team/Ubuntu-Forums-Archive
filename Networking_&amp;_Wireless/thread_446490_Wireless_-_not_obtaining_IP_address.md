---
title: "Wireless - not obtaining IP address"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by yagerd001 on 2007-05-17
My laptop has built-in broadcomm, but I also have an atheros pc card, which was much easier to config.  Both wireless show up, and the atheros pccard says it's working, according to the LEDs.  But Neither wireless gets an ipadress when set to dynamic address config.  Here's what lsmod gives me:

:/etc/network$ lsmod
Module                  Size  Used by
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
vmnet                  39076  13 
vmmon                 113420  0 
nls_cp437               6784  1 
cifs                  217080  1 
binfmt_misc            12680  1 
ppdev                  10116  0 
powernow_k8            16064  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
container               5248  0 
ac                      6020  0 
video                  16388  0 
dock                   10268  0 
asus_acpi              17308  0 
button                  8720  0 
backlight               7040  1 asus_acpi
battery                10756  0 
af_packet              23816  2 
nls_utf8                3072  0 
ntfs                  107764  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  7 
nfs                   240876  1 
lockd                  64904  1 nfs
sunrpc                161340  3 nfs,lockd
ipv6                  268704  8 
pcmcia                 39212  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
nvidia               4713780  22 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
joydev                 10816  0 
bcm43xx               125332  0 
ieee80211softmac       31232  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
psmouse                38920  0 
serio_raw               7940  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
k8temp                  6656  0 amd64_agp              13700  1 
agpgart                35400  2 nvidia,amd64_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
i2c_nforce2             6784  0 
i2c_core               22784  3 i2c_ec,nvidia,i2c_nforce2
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  6 
sata_nv                20868  0 
ata_generic             9092  0 
libata                125720  2 sata_nv,ata_generic
scsi_mod              142348  2 sbp2,libata
generic                 5124  0 [permanent]
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ohci_hcd               22532  0 
amd74xx                15260  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  3 ohci_hcd,ehci_hcd
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

Any suggestions?  I probably messed up when I installed with two wireless interfaces connected.

[email]yagerd001@hawaii.rr.com[/email]

---

### Post by jbro on 2007-05-17
What are you using to try to make your DHCP connection? /etc/init.d/networking? NetworkManager? Wifi Radar? When you try to connect exactly what happens? Does it attempt for a long time and silently fail? Do you get some type of error message? The other thing I might recommend is to do the following.

[LIST=1]
[*]Open a terminal (Applications->Accessories->Terminal).
[*]In the terminal type ```
sudo tail -f /var/log/messages
```. This will show log messages as they come in. Note the last timestamp you see.
[*]Try to connect to the network using your normal method. Watch the log messages roll in (hopefully).
[*]Look through the messages that appear to see if there is anything helpful. Post the resulting log information here so people here can take a look at it.
[/LIST]

Posting the output of the commands ifconfig and iwconfig may also be helpful.

Regards,
jbro

---

