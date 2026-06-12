---
title: "Slow wireless internet Netgear WG111v2 USB"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Bonkerz on 2007-05-21
Argh! This download cap of 28kb is annoying the hell out of me. Before Feisty, I had a normal 300kb+ download rate, but now it has been reduced to a mere 28kb at most. I've tried ndiswrapper, didn't solve it. I've tried using various networking programs in place of Network Manager, such as Wicd, wifiradar, etc, and they didn't solve it. I've edited the nsswitch.conf file and removed the mdns entries, and that didn't solve it.

What else should I try?

---

### Post by Bonkerz on 2007-05-21
bump for justice

---

### Post by LordChaos73 on 2007-05-25
Please post the results of the following commands here:

- dmesg |grep -i "wireless interface" (i.e. wlan0)

- lsmod

- cat /etc/network/interfaces

- ndiswrapper -l

What version of Wg111v2 Windows drivers are you using ?

---

### Post by Bonkerz on 2007-06-20
```
[   45.182214] wlan0: starting scan
[   46.418318] wlan0: scan completed
[   46.535012] wlan0: Initial auth_alg=0
[   46.535017] wlan0: authenticate with AP 00:09:5b:71:65:d2
[   46.536394] wlan0: RX authentication from 00:09:5b:71:65:d2 (alg=0 transaction=2 status=0)
[   46.536396] wlan0: authenticated
[   46.536399] wlan0: associate with AP 00:09:5b:71:65:d2
[   46.538259] wlan0: RX AssocResp from 00:09:5b:71:65:d2 (capab=0x5 status=0 aid=8)
[   46.538261] wlan0: associated
[   56.848761] wlan0: no IPv6 routers present
[  235.456000] wlan0: starting scan
[  236.692000] wlan0: scan completed
[  236.808000] wlan0: Initial auth_alg=0
[  236.808000] wlan0: authenticate with AP 00:09:5b:71:65:d2
[  236.808000] wlan0: RX authentication from 00:09:5b:71:65:d2 (alg=0 transaction=2 status=0)
[  236.808000] wlan0: authenticated
[  236.808000] wlan0: associate with AP 00:09:5b:71:65:d2
[  236.812000] wlan0: RX AssocResp from 00:09:5b:71:65:d2 (capab=0x5 status=0 aid=8)
[  236.812000] wlan0: associated
[  245.952000] wlan0: no IPv6 routers present
[  507.396000] wlan0: Initial auth_alg=0
[  507.396000] wlan0: authenticate with AP 00:09:5b:71:65:d2
[  507.596000] wlan0: authenticate with AP 00:09:5b:71:65:d2
[  507.796000] wlan0: authenticate with AP 00:09:5b:71:65:d2
[  507.996000] wlan0: authentication with AP 00:09:5b:71:65:d2 timed out
[  566.676000] wlan0: Initial auth_alg=0
[  566.676000] wlan0: authenticate with AP 00:09:5b:71:65:d2
[  566.676000] wlan0: RX authentication from 00:09:5b:71:65:d2 (alg=0 transaction=2 status=0)
[  566.676000] wlan0: authenticated
[  566.676000] wlan0: associate with AP 00:09:5b:71:65:d2
[  566.680000] wlan0: RX AssocResp from 00:09:5b:71:65:d2 (capab=0x5 status=0 aid=8)
[  566.680000] wlan0: associated
[  577.064000] wlan0: no IPv6 routers present

```

```
binfmt_misc            11272  1 
xt_limit                2688  8 
xt_tcpudp               3328  10 
iptable_mangle          2816  0 
ipt_LOG                 6528  8 
ipt_MASQUERADE          3456  0 
nf_nat                 17964  1 ipt_MASQUERADE
ipt_TOS                 2304  0 
ipt_REJECT              4608  1 
nf_conntrack_irc        7064  0 
nf_conntrack_ftp        9728  0 
nf_conntrack_ipv4      17932  7 
xt_state                2560  6 
nf_conntrack           59864  6 ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
nfnetlink               6680  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3072  1 
ip_tables              12232  2 iptable_mangle,iptable_filter
x_tables               15108  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
powernow_k8            11404  0 
cpufreq_userspace       4116  0 
cpufreq_stats           5508  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        7676  1 
freq_table              4740  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     6560  0 
tc1100_wmi              7172  0 
pcc_acpi               12160  0 
dev_acpi               11140  0 
sony_acpi               5388  0 
video                  15492  0 
sbs                    14752  0 
i2c_ec                  5120  1 sbs
dock                    9216  0 
button                  7696  0 
battery                 9860  0 
container               4352  0 
ac                      5124  0 
asus_acpi              16412  0 
backlight               6016  1 asus_acpi
ipv6                  252768  22 
fuse                   44436  1 
psmouse                37640  0 
lp                     11332  0 
snd_intel8x0           32796  1 
snd_ac97_codec         97312  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                76680  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  1 snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                49648  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               4711732  32 
arc4                    2048  2 
ecb                     3584  2 
blkcipher               5888  1 ecb
rc80211_simple          5504  1 
rtl8187                34048  0 
mac80211              172804  2 rc80211_simple,rtl8187
cfg80211               21896  1 mac80211
analog                 11680  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6            3456  1 rtl8187
gameport               15112  1 analog
parport_pc             34980  1 
parport                35272  2 lp,parport_pc
pcspkr                  3072  0 
rtc                    13232  0 
k8temp                  5760  0 
snd                    51716  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  2 snd_intel8x0,snd_pcm
shpchp                 33300  0 
pci_hotplug            31160  1 shpchp
amd64_agp              12804  1 
agpgart                34096  2 nvidia,amd64_agp
i2c_nforce2             5888  0 
i2c_core               21648  3 i2c_ec,nvidia,i2c_nforce2
evdev                  10112  3 
tsdev                   7872  0 
ext3                  129288  1 
jbd                    53032  1 ext3
mbcache                 8196  1 ext3
ide_cd                 31648  0 
cdrom                  36512  1 ide_cd
ide_disk               16000  3 
sata_nv                19716  0 
ata_generic             8196  0 
libata                125208  2 sata_nv,ata_generic
scsi_mod              141580  1 libata
usbhid                 25056  0 
hid                    25728  1 usbhid
floppy                 58020  0 
generic                 4228  0 [permanent]
amd74xx                14236  0 [permanent]
ehci_hcd               32780  0 
ohci_hcd               21252  0 
usbcore               131480  5 rtl8187,usbhid,ehci_hcd,ohci_hcd
raid10                 24704  0 
raid456               123408  0 
xor                    15752  1 raid456
raid1                  23936  0 
raid0                   8704  0 
multipath               8832  0 
linear                  6400  0 
md_mod                 77076  7 raid10,raid456,raid1,raid0,multipath,linear
thermal                13832  0 
processor              22956  2 powernow_k8,thermal
fan                     4740  0 
dm_mod                 57164  4 
fbcon                  41760  0 
tileblit                2688  1 fbcon
font                    8320  1 fbcon
bitblit                 6016  1 fbcon
softcursor              2304  1 bitblit
vesafb                  8196  0 
capability              5000  0 
commoncap               7296  1 capability

```

```
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.0.8
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Home



iface wmaster0 inet static
address 192.168.0.8
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Home





auto wlan0

```

```
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)

```

Using latest wg111v2 driver which is v3.30

Please help me get this thing up to speed :o(

---

### Post by Wherdgo on 2007-06-23
I'm having the same problem with a Netgear wg511v2 PCMCIA, using WPA2

I consistently get "wlan0: authentication with AP xx:xx:xx:xx:xx:xx timed out"

Any way of lengthening the timeout period, or where?

---

### Post by Bonkerz on 2007-06-25
I just replaced my USB dongle with a $25 Ativa from Office Depot. Works out of the box.

---

### Post by nomizzz on 2008-05-04
I'm also having the same problem, but it's with the Netgear WG111v3 USB dongle.  I'm using Ubuntu 8.04 Hardy Heron with the ndiswrapper GUI installed, any updates on this situation?

---

### Post by sennep on 2008-05-06
> **nomizzz said:**
> I'm also having the same problem, but it's with the Netgear WG111v3 USB dongle.  I'm using Ubuntu 8.04 Hardy Heron with the ndiswrapper GUI installed, any updates on this situation?

Are you using win98 drivers or XP drivers? At least for the wg111v2 you're supposed to use win98 drivers, so this might be true for the wg111v3 as well.

---

