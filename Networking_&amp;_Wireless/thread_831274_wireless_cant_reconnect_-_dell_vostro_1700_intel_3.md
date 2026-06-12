---
title: "wireless cant reconnect - dell vostro 1700 intel 3945"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by rob_munro on 2008-06-16
Hi out there,

I am having strange prob with my wireless network, everything starts fine but after a while there will be a dropout, then sometimes the wireless will come back but other times it seems like the driver has crashed or something and the OS can't talk to the card. 

Then lots of stuff hangs. but after a system restart everything is fine again. 

The problem is that its only staying up for about half an hour at the moment so i can't get much done beetween restarts.

Even if i do the old:-
ifconfig
ifup
ifdown
the command line hangs and i cant even use Ctrl+C to quit.

Does anyone have any ideas? maybe i can restart the module or something but not sure how.


```
robm@cobra:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 4937
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1c:bf:7c:11:e6
Sending on   LPF/eth1/00:1c:bf:7c:11:e6
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Resource temporarily unavailable.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Resource temporarily unavailable.

```
--------------------------------------------------------------

```
robm@cobra:~$ lsmod 
Module                  Size  Used by
vmnet                  44596  15 
vmblock                16288  3 
vmmon                 945260  0 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
video                  18060  14 
ipv6                  273892  12 
battery                11012  0 
sbs                    19592  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14080  2 
fat                    54300  1 vfat
af_packet              24840  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
hsfhda                111712  1 
hsfserial              24740  1 hsfhda
hsfengine            1265420  2 hsfhda,hsfserial
hsfosspec             105832  6 hsfhda,hsfserial,hsfengine
snd_hda_intel         315952  1 
snd_pcm_oss            42752  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9600  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw3945               119840  0 
joydev                 11328  0 
nvidia               6221648  36 
uvcvideo               48644  0 
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               26112  1 nvidia
compat_ioctl32          2304  1 uvcvideo
ieee80211              35656  1 ipw3945
snd                    57508  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
sdhci                  18828  0 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
pcspkr                  4224  0 
mmc_core               28420  1 sdhci
psmouse                39952  0 
serio_raw               8068  0 
soundcore               8800  1 snd
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  8 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
b44                    28300  0 
mii                     6528  1 b44
ahci                   23300  7 
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 hsfosspec,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor
```
------------------------------------------------------------------------------------------------------
ifocnfig hangs terminal and cant ctl+C
-----------------------------------------------------------------------------------------------------
 sudo ifdown eth1 hangs

---

### Post by rob_munro on 2008-06-16
Sorry i forgot to mention i am on Gutsy 7.10

---

### Post by chili555 on 2008-06-16
> the command line hangs and i cant even use Ctrl+C to quit.I think you have bigger problems than the driver for 3945, perhaps IRQ conflicts, but that's a guess. Here are three diagnostic tools. First, open a terminal and do:```
sudo cat /var/log/messages | grep iwl
```Or try:```
sudo cat /var/log/messages | grep IRQ
```Next, before you type 'ifconfig' in a terminal, open another terminal and do:```
sudo tail -f /var/log/messages
```Leave this terminal open and watch for errors to appear as you 'ifconfig.'

You might also run:```
top
```See what's eating CPU cycles before, during and after you 'ifconfig.'

---

### Post by rob_munro on 2008-06-26
I cant see any interrupt conflicts 
```
sudo cat /var/log/messages | grep IRQ
```
gives
```

Jun 24 09:01:35 cobra kernel: [   11.264215] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 24 09:01:35 cobra kernel: [   11.705480] ENABLING IO-APIC IRQs
Jun 24 09:01:35 cobra kernel: [   12.075017] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Jun 24 09:01:35 cobra kernel: [   12.075110] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jun 24 09:01:35 cobra kernel: [   12.075201] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Jun 24 09:01:35 cobra kernel: [   12.075292] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Jun 24 09:01:35 cobra kernel: [   12.075383] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 24 09:01:35 cobra kernel: [   12.075475] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 24 09:01:35 cobra kernel: [   12.075567] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 24 09:01:35 cobra kernel: [   12.075651] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 24 09:01:35 cobra kernel: [   12.107998] PCI: Using ACPI for IRQ routing
Jun 24 09:01:35 cobra kernel: [   12.196138] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 24 09:01:35 cobra kernel: [   12.196164] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 24 09:01:35 cobra kernel: [   12.196193] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 24 09:01:35 cobra kernel: [   12.196221] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jun 24 09:01:35 cobra kernel: [   13.126169] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 24 09:01:35 cobra kernel: [    3.268000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
Jun 24 09:01:35 cobra kernel: [    3.376000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
Jun 24 09:01:35 cobra kernel: [    3.484000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 24 09:01:35 cobra kernel: [    3.588000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
Jun 24 09:01:35 cobra kernel: [    3.692000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 24 09:01:35 cobra kernel: [    3.796000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
Jun 24 09:01:35 cobra kernel: [    3.900000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 19
Jun 24 09:01:35 cobra kernel: [    4.004000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 24 09:01:35 cobra kernel: [    4.532000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jun 24 09:01:35 cobra kernel: [    6.336000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 24 09:01:35 cobra kernel: [    6.340000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 24 09:01:35 cobra kernel: [    6.396000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun 24 09:01:35 cobra kernel: [   13.016000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Jun 24 09:01:35 cobra kernel: [   13.296000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 24 09:01:35 cobra kernel: [   13.476000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 24 09:01:35 cobra kernel: [   13.640000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 25 09:48:53 cobra kernel: [   10.184068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 25 09:48:53 cobra kernel: [   10.625332] ENABLING IO-APIC IRQs
Jun 25 09:48:53 cobra kernel: [   11.066513] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Jun 25 09:48:53 cobra kernel: [   11.066606] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jun 25 09:48:53 cobra kernel: [   11.066697] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Jun 25 09:48:53 cobra kernel: [   11.066788] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Jun 25 09:48:53 cobra kernel: [   11.066879] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 25 09:48:53 cobra kernel: [   11.066972] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 25 09:48:53 cobra kernel: [   11.067064] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 25 09:48:53 cobra kernel: [   11.067149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 25 09:48:53 cobra kernel: [   11.114062] PCI: Using ACPI for IRQ routing
Jun 25 09:48:53 cobra kernel: [   11.202159] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 09:48:53 cobra kernel: [   11.202185] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 09:48:53 cobra kernel: [   11.202214] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 25 09:48:53 cobra kernel: [   11.202242] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jun 25 09:48:53 cobra kernel: [   12.129766] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 25 09:48:53 cobra kernel: [    3.320000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
Jun 25 09:48:53 cobra kernel: [    3.424000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Jun 25 09:48:53 cobra kernel: [    3.528000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Jun 25 09:48:53 cobra kernel: [    3.632000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Jun 25 09:48:53 cobra kernel: [    3.736000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Jun 25 09:48:53 cobra kernel: [    3.840000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
Jun 25 09:48:53 cobra kernel: [    3.984000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Jun 25 09:48:53 cobra kernel: [    4.108000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 25 09:48:53 cobra kernel: [    4.108000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 25 09:48:53 cobra kernel: [    4.164000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun 25 09:48:53 cobra kernel: [    4.168000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 09:48:53 cobra kernel: [    4.716000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jun 25 09:48:53 cobra kernel: [   12.912000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Jun 25 09:48:53 cobra kernel: [   13.028000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 25 09:48:53 cobra kernel: [   13.480000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 09:48:53 cobra kernel: [   13.624000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Jun 25 21:36:42 cobra kernel: [   11.919895] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 25 21:36:42 cobra kernel: [   12.565297] ENABLING IO-APIC IRQs
Jun 25 21:36:42 cobra kernel: [   12.990487] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Jun 25 21:36:42 cobra kernel: [   12.990655] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jun 25 21:36:42 cobra kernel: [   12.990818] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Jun 25 21:36:42 cobra kernel: [   12.990979] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Jun 25 21:36:42 cobra kernel: [   12.991141] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 25 21:36:42 cobra kernel: [   12.991306] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 25 21:36:42 cobra kernel: [   12.991470] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 25 21:36:42 cobra kernel: [   12.991653] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 25 21:36:42 cobra kernel: [   13.045168] PCI: Using ACPI for IRQ routing
Jun 25 21:36:42 cobra kernel: [   13.145770] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 21:36:42 cobra kernel: [   13.145803] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 21:36:42 cobra kernel: [   13.145840] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 25 21:36:42 cobra kernel: [   13.145877] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jun 25 21:36:42 cobra kernel: [   14.493298] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 25 21:36:42 cobra kernel: [    4.368000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
Jun 25 21:36:42 cobra kernel: [    4.476000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
Jun 25 21:36:42 cobra kernel: [    4.584000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 25 21:36:42 cobra kernel: [    4.688000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
Jun 25 21:36:42 cobra kernel: [    4.792000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 25 21:36:42 cobra kernel: [    4.896000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
Jun 25 21:36:42 cobra kernel: [    5.000000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 19
Jun 25 21:36:42 cobra kernel: [    5.104000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jun 25 21:36:42 cobra kernel: [    6.904000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 21:36:42 cobra kernel: [    7.432000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 25 21:36:42 cobra kernel: [    7.436000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 25 21:36:42 cobra kernel: [    7.488000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun 25 21:36:42 cobra kernel: [   16.280000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Jun 25 21:36:42 cobra kernel: [   16.292000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 25 21:36:42 cobra kernel: [   16.344000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 25 21:36:42 cobra kernel: [   16.664000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 25 21:36:42 cobra kernel: [   68.008000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 26 09:02:19 cobra kernel: [   15.226045] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 26 09:02:19 cobra kernel: [   15.871446] ENABLING IO-APIC IRQs
Jun 26 09:02:19 cobra kernel: [   16.277478] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Jun 26 09:02:19 cobra kernel: [   16.277645] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Jun 26 09:02:19 cobra kernel: [   16.277833] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Jun 26 09:02:19 cobra kernel: [   16.277995] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Jun 26 09:02:19 cobra kernel: [   16.278158] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 26 09:02:19 cobra kernel: [   16.278322] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 26 09:02:19 cobra kernel: [   16.278486] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jun 26 09:02:19 cobra kernel: [   16.278635] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 26 09:02:19 cobra kernel: [   16.332114] PCI: Using ACPI for IRQ routing
Jun 26 09:02:19 cobra kernel: [   16.432786] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 26 09:02:19 cobra kernel: [   16.432820] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 26 09:02:19 cobra kernel: [   16.432857] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 26 09:02:19 cobra kernel: [   16.432893] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jun 26 09:02:19 cobra kernel: [   17.781268] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 26 09:02:19 cobra kernel: [    4.376000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
Jun 26 09:02:19 cobra kernel: [    4.480000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Jun 26 09:02:19 cobra kernel: [    4.584000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 26 09:02:19 cobra kernel: [    5.112000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jun 26 09:02:19 cobra kernel: [    6.912000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
Jun 26 09:02:19 cobra kernel: [    7.024000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Jun 26 09:02:19 cobra kernel: [    7.132000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 26 09:02:19 cobra kernel: [    7.136000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Jun 26 09:02:19 cobra kernel: [    7.240000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Jun 26 09:02:19 cobra kernel: [    7.348000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Jun 26 09:02:19 cobra kernel: [    7.452000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Jun 26 09:02:19 cobra kernel: [    7.504000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jun 26 09:02:19 cobra kernel: [   16.388000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 26 09:02:19 cobra kernel: [   16.696000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Jun 26 09:02:19 cobra kernel: [   16.700000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 26 09:02:19 cobra kernel: [   16.980000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20


```

I have had /var/log/messages tailed while doing ifconfig, ifup, ifdown and i don't get any output into the log file, weird.

To me it looks like some sort of resource deadlock, like some resource isn't being released then the wireless connection drops out. So that when i try to reconnect the systems calls are waiting for a resource.

---

