---
title: "wireless networking only works in roaming mode"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by amg on 2008-09-24
Good day,

I have a wireless setup here at my desktop working just-fine with the roaming enabled, however, every time I try to change this to manual, the wireless network goes down.

I *think* (not being an expert, hard to say) the fact that I have three network interfaces set might have something to do with it: eth0, wifi0, and ath0, under system->administration-network tools the same three are listed, however wifi0 and ath0 are "unknown interfaces", where eth0 is an "ethernat interface".

But, when I select eth0, the display box beneath show no data, and ath0 does (it gives me basic connection data).

Okay, so I try this:

lshx -C network and it return this:

```
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:0c:33:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 module=atl1 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wifi0
       version: 01
       serial: 00:1b:2f:c0:c1:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.10 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Note the name wifi0, which doesn't match anything under the GUI network tools application.

So, I'll do a lsmod and see if the module is loaded:

```
Module                  Size  Used by
wlan_wep                8064  0 
wlan_tkip              13696  2 
af_packet              23812  4 
nls_cp437               6656  1 
isofs                  36388  1 
udf                    88612  0 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ipv6                  267780  18 
ppdev                  10372  0 
autofs4                23044  0 
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
wlan_scan_sta          14720  1 
hci_usb                16540  2 
ath_rate_sample        14336  1 
snd_seq_oss            35584  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
atl1                   36364  0 
nvidia               7825536  34 
snd_seq_midi            9376  0 
mii                     6400  1 atl1
snd_rawmidi            25760  1 snd_seq_midi
i2c_core               24832  1 nvidia
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
ath_pci               101024  0 
wlan                  207728  6 wlan_wep,wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_hal               192592  3 ath_rate_sample,ath_pci
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  0 
button                  9232  0 
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  4 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sg                     36880  0 
sd_mod                 30720  3 
pata_jmicron            7040  1 
usbhid                 31872  0 
hid                    38784  1 usbhid
pata_acpi               8320  0 
floppy                 59588  0 
ata_piix               19588  2 
ata_generic             8324  0 
ahci                   28420  0 
libata                159344  5 pata_jmicron,pata_acpi,ata_piix,ata_generic,ahci
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```

It is, as are some other wifi/ethernet modules (as fas as I can tell from name-based guessing).

Okay, so lets see what iwconfig has to say about this:

```
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"ESSID"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:7E:2B:94   
          Bit Rate:18 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-65 dBm  Noise level=-94 dBm
          Rx invalid nwid:22687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

Okay, this one says ath0, which, under network-tools gives data, even though network tools thinks this interface is unknown.

What am I supposed to do? I want networking to be brought up at boot-time, but if I can't get networking to work manually, how can I accomplish that?

If I add anything to /etc/network/interfaces the network goes down. I've tried various solutions in these forums, but none have seemed to solve my specific problem.

I'd appreciate anything you can do to help.

---

### Post by amg on 2008-09-25
Nobody knows?

---

