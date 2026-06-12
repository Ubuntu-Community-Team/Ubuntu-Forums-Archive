---
title: "Asus F3S Series Intel Wireless WiFi Link 4965AGN Problem After Some Updates"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by caglar.dursun on 2008-11-04
Hi ...

Something happened my wireless connection and I still dont know why ?When the first instalation happened everything looked fine and working but after some kernel and library updates my wireless connection and wlan0 interface lost.

I have been searching a solution during 3 days & there is no working solution for me.Here is the some information about my system.

uname -r
2.6.24-21-generic

dmesg | grep wl
[   54.359830] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   54.359833] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   54.445608] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   54.824759] iwl4965: Radio disabled by HW RF Kill switch

lsmod
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
joydev                 13120  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
uvcvideo               58116  0 
snd_mixer_oss          17920  1 snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
iwl4965               105844  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
atl1                   36364  0 
v4l2_common            18304  2 uvcvideo,videodev
psmouse                40336  0 
nvidia               7825536  36 
iwlwifi_mac80211      218980  1 iwl4965
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
mii                     6400  1 atl1
serio_raw               7940  0 
video                  19856  0 
cfg80211               15112  1 iwlwifi_mac80211
output                  4736  1 video
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
sdhci                  19076  0 
snd_seq_midi            9376  0 
battery                14212  0 
mmc_core               51460  1 sdhci
ac                      6916  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            19064  0 
button                  9232  0 
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
led_class               6020  1 asus_laptop
pcspkr                  4224  0 
evdev                  13056  6 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
ata_generic             8324  0 
sg                     36880  0 
sd_mod                 30720  6 
usb_storage            73664  1 
libusual               19108  1 usb_storage
ahci                   28548  3 
ata_piix               19588  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 



Do you have any idea what's going on ?

---

### Post by caglar.dursun on 2008-11-04
Here we go ... I download new drivers from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) and still doesn't existing wlan0 or any wireless connection.

this is the result of ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:38:99:25  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe38:9925/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:15795 (15.4 KB)  TX bytes:11381 (11.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138900 (135.6 KB)  TX bytes:138900 (135.6 KB)

I'm gonna lose my mind.

---

### Post by caglar.dursun on 2008-11-10
Here i am & after two weeks,i still cannot use the wireless anymore.I hate linux.

---

### Post by eargonz on 2008-11-12
Hi there, I'm having the same problem. I installed Ubuntu on a Gateway M-153XL, and at first everything was OK, but suddenly the wireless conection fell. I thougt that it wasn't big deal, but then I realised I counldn't get it to work again. I'm getting crazy trying to fix it!!

The card is the same one as yours, please if you find a way to fix it, tell me, I'll do the same for you.

Thanks

---

### Post by caglar.dursun on 2008-11-28
Yeap,

I fixed it two weeks ago.I upgrade to ubuntu 8.10.Now it's fine.When I checked the module list again iwl4965 disapeared and iwlang comes.I guess the problem was iwl4965 module.

---

### Post by caglar.dursun on 2008-11-28
If you still having the same problem your wireless card.May be I can help this time.

---

### Post by rickn on 2009-10-27
I have this problem with an Asus F3S laptop on 9.04 Jaunty.  No hardware kill switch on this model.  It worked under 8.10.  Man, this is killing me.

uname -a

Linux chirpy 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

dmesg | grep iwlagn

[   10.002365] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   10.002368] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   10.002507] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.002515] iwlagn 0000:03:00.0: setting latency timer to 64
[   10.002557] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   10.039574] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.039631] iwlagn 0000:03:00.0: irq 2295 for MSI/MSI-X
[   18.406863] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   18.466136] iwlagn: Radio disabled by HW RF Kill switch

---

### Post by rickn on 2009-10-27
Sigh. It's really hard to admit this, but I just found the RF kill switch on the front edge. Nuff said.

---

