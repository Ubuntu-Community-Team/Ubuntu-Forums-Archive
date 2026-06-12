---
title: "wifi card stopped working with upgrade from edgy beta to edgy stable"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by tasuki on 2006-10-27
Hi people,

this completely sucks ](*,)

I made a clean edgy install when it was in beta, and the wireless card (prism) worked perfectly. Yesterday I made an upgrade to the "official" edgy release and it broke. Now my system can't even see the card (I'd think there was a hardware problem, but it still works in my old dapper).

The kernel didn't change... I don't know what did change though... is there any possibility to somehow get "recent changes" from apt-get ?

Also, anyone knows what could cause the system not to see the card?

---

### Post by tasuki on 2006-10-27
well... some more info...

lshw says (it changed the name from former eth1 to wlan0):
[INDENT]*-network:1 DISABLED
description: Ethernet interface
product: Prism 2.5 Wavelan chipset
vendor: Intersil Corporation
physical id: d
bus info: pci@00:0d.0
logical name: wlan0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=prism2_pci ip=10.0.0.32 multicast=yes[/INDENT]

and also:
[INDENT]vita@doma:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                               Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Failed to bring up wlan0.[/INDENT]

Please help me...

---

### Post by tasuki on 2006-10-27
and lsmod gives this:
```
Module                  Size  Used by
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  19
apm                    23280  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
ip_nat_ftp              4736  0
ip_nat_irc              3840  0
ip_conntrack_ftp        8816  1 ip_nat_ftp
ip_conntrack_irc        7920  1 ip_nat_irc
ipt_MASQUERADE          4864  1
iptable_nat             8964  1
ip_nat                 19884  4 ip_nat_ftp,ip_nat_irc,ipt_MASQUERADE,iptable_nat
ipt_LOG                 8320  5
xt_limit                3840  5
xt_tcpudp               4480  36
xt_state                3328  53
iptable_filter          4224  1
ip_conntrack           53216  8 ip_nat_ftp,ip_nat_irc,ip_conntrack_ftp,ip_conntrack_irc,ipt_MASQUERADE,iptable_nat,ip_nat,xt_state
nfnetlink               8216  2 ip_nat,ip_conntrack
ip_tables              15204  2 iptable_nat,iptable_filter
x_tables               16132  7 ipt_MASQUERADE,iptable_nat,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ip_tables
nls_iso8859_1           5248  2
nls_cp437               6912  2
vfat                   14720  2
fat                    56348  1 vfat
nls_utf8                3200  1
ntfs                  112116  1
lp                     12964  0
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  1
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
tsdev                   9152  0
gl620a                  5248  0
usbnet                 18568  1 gl620a
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
usbhid                 45152  0
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
hostap_pci             59152  0
hostap                123012  1 hostap_pci
ieee80211_crypt         7552  1 hostap
evdev                  11392  1
psmouse                41352  0
serio_raw               8452  0
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
orinoco_pci             8320  0
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
prism2_pci             74752  0
floppy                 63044  0
8139cp                 24832  0
8139too                29056  0
rt2500                188004  0
mii                     6912  2 8139cp,8139too
pcspkr                  4352  0
nvidia               4555092  12
soundcore              11232  1 snd
parport_pc             37796  1
parport                39496  2 lp,parport_pc
via_agp                11264  1
agpgart                34888  2 nvidia,via_agp
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
via686a                18568  0
i2c_isa                 6144  1 via686a
i2c_viapro              9876  0
i2c_core               23424  4 nvidia,via686a,i2c_isa,i2c_viapro
ext3                  142728  3
jbd                    62228  1 ext3
uhci_hcd               24968  0
usbcore               134912  5 gl620a,usbnet,usbhid,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  9
via82cxxx              10500  0 [permanent]
generic                 5764  0
processor              31560  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
```

---

### Post by Fran on 2006-10-27
Sorry not to offer any help.  Just to say "me too!".

Only additional info: System->Networking shows wlan0 as a _wired_ connection.

---Fran

---

### Post by tasuki on 2006-10-27
open the file /etc/modprobe.d/blacklist

and add the line:
blacklist prism2_pci

prism2_pci is borken and they added it nevertheless... (you should have modules orinoco, orinoco_pci and hermes)

hope this helps... (it did, for me)

---

### Post by Fran on 2006-10-27
Fabulous---works for me too.

Many thanks---Fran

---

### Post by Nycto on 2006-10-27
This worked brilliantly for me too, thanks mate.

---

### Post by mority on 2006-12-19
Aye! Solution works for me, too... :)

---

