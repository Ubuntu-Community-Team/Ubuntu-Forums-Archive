---
title: "[SOLVED] ethernet stopped working"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by theomp on 2008-09-09
Hi, My ethernet connection has stopped working(wireless still fine and ethernet works when I run from the live cd). I'll being searching the forums and trying various things for days but still no joy. I'll list below all the relevent details that I think concern this issue.
I've tried bringing all the interfaces down and up again and restarting the NetworkManager. 
Thanks in advance for any help

Eoghan

[HTML]
<code>
eobeirn@eobeirn-laptop:~$ lspci | grep -i ethernet
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

eobeirn@eobeirn-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186656 (182.2 KB)  TX bytes:186656 (182.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:a5:1e:3e  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fea5:1e3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3545939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3369946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2645543505 (2.4 GB)  TX bytes:1299088305 (1.2 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-A5-1E-3E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eobeirn@eobeirn-laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

eobeirn@eobeirn-laptop:~$ lsmod 
Module                  Size  Used by
usbhid                 31872  0 
hid                    38784  1 usbhid
ipv6                  267780  10 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
dock                   11280  0 
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
af_packet              23812  4 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344728  6 
arc4                    2944  2 
joydev                 13120  0 
ecb                     4480  2 
snd_pcm_oss            42144  0 
blkcipher               8324  1 ecb
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
iwl3945                89588  0 
snd_seq_oss            35584  0 
fglrx                1555468  23 
mac80211              221812  1 iwl3945
sdhci                  19076  0 
dcdbas                  9504  0 
snd_seq_midi            9376  0 
evdev                  13056  9 
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
snd_rawmidi            25760  1 snd_seq_midi
cfg80211               35168  2 iwl3945,mac80211
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0 
video                  19856  0 
output                  4736  1 video
snd                    56996  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  0 
battery                14212  0 
button                  9232  0 
soundcore               8800  2 snd
ac                      6916  0 
shpchp                 34452  0 
agpgart                34760  2 fglrx,intel_agp
pci_hotplug            30880  1 shpchp
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  3 
ssb                    49540  0 
pcmcia                 40876  1 ssb
pcmcia_core            40596  2 ssb,pcmcia
mii                     6400  0 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
eobeirn@eobeirn-laptop:~$  
</code>
[/HTML]

---

### Post by Iowan on 2008-09-09
Kindof a lonely-looking **/etc/network/interfaces ** file...
Should the connection be DHCP?  If so, try adding the lines:```
auto eth0
iface eth0 inet dhcp
```

---

### Post by theomp on 2008-09-10
thanks Iowan. I tried that and still no joy. 
I suspect that the issue is with the controllers module. Looking through dmesg I saw some errors releating to the b44 module

[   28.010087] b44: disagrees about version of symbol ssb_device_is_enabled
[   28.010092] b44: Unknown symbol ssb_device_is_enabled
[   28.010169] b44: disagrees about version of symbol ssb_pcicore_dev_irqvecs_enable
[   28.010173] b44: Unknown symbol ssb_pcicore_dev_irqvecs_enable
[   28.010324] b44: disagrees about version of symbol ssb_bus_may_powerdown
[   28.010327] b44: Unknown symbol ssb_bus_may_powerdown
[   28.010519] b44: disagrees about version of symbol ssb_pcihost_register
[   28.010522] b44: Unknown symbol ssb_pcihost_register
[   28.010836] b44: disagrees about version of symbol ssb_dma_set_mask
[   28.010839] b44: Unknown symbol ssb_dma_set_mask
[   28.011043] b44: disagrees about version of symbol ssb_device_enable
[   28.011046] b44: Unknown symbol ssb_device_enable
[   28.011299] b44: disagrees about version of symbol ssb_driver_unregister
[   28.011303] b44: Unknown symbol ssb_driver_unregister
[   28.011455] b44: disagrees about version of symbol __ssb_driver_register
[   28.011458] b44: Unknown symbol __ssb_driver_register
[   28.011579] b44: disagrees about version of symbol ssb_bus_powerup
[   28.011582] b44: Unknown symbol ssb_bus_powerup
[   28.011887] b44: disagrees about version of symbol ssb_clockspeed
[   28.011890] b44: Unknown symbol ssb_clockspeed
[   28.012018] b44: disagrees about version of symbol ssb_dma_translation
[   28.012021] b44: Unknown symbol ssb_dma_translation

Seeing this I tried removing and loading the module again

eobeirn@eobeirn-laptop:~$ sudo modprobe -vr b44
[sudo] password for eobeirn: 
rmmod /lib/modules/2.6.24-19-generic/updates/drivers/ssb/ssb.ko
rmmod /lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko
rmmod /lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko
rmmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko
eobeirn@eobeirn-laptop:~$ sudo modprobe -v b44
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko 
insmod /lib/modules/2.6.24-19-generic/updates/drivers/ssb/ssb.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko 
FATAL: Error inserting b44 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)
eobeirn@eobeirn-laptop:~$ 

I'm going to have a trawl through google and see if I can find the cause(and solution) of these errors

---

### Post by theomp on 2008-09-10
Ok, I've managed to get this fixed now.
The issue seems to have being caused by the last kernel update(2.6.24-19) that I ran.
This caused the module for the ethernet controllor(b44) to stop working. I've now updated to 2.6.24-21 and have my ethernet back....Whoo-Hoo!!

---

