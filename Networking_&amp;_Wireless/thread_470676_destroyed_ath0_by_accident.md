---
title: "destroyed ath0 by accident"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by fracktor on 2007-06-11
I was recently messing around with aircrack-ng and somehow managed to destroy ath0 and now my wireless does not work. In the device manager I can see the card being recognized (DWL-G520) but it does not show up in the network properties,it just shows the wired and modem connections. Is there an easy way to reinstall the wireless card. I had not been using madwifi or anything like that, Feisty just picked up my wireless card and it always worked. Sorry I can't be more specific on how I actually deleted ath0, I don't remember the whole process I followed. Any advice is greatly appreciated.

---

### Post by kevdog on 2007-06-11
What does your /etc/network/interfaces file look like?? 

Is there an auth0 entry contained in this file?

---

### Post by cantormath on 2007-06-11
and 

what does 
sudo iwconfig ath0 
say?

---

### Post by fracktor on 2007-06-11
Sorry I am at work right now and cant try those commands. I will post the output of sudo iwconfig ath0  later today. Thanks for the quick reply.

---

### Post by tgalati4 on 2007-06-11
Try a complete powerdown, remove the battery, wait a few minutes, reboot.

---

### Post by fracktor on 2007-06-12
sudo ifconfig ath0
ath0: Error fetching interface information: Device not found

--------------------------------------------------------------------------------

/etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

--------------------------------------------------------------------

Also, lspci shows
00:10.0 ethernet controller: Atheros Communications AR5212 802.11abg nic

---

### Post by spd106 on 2007-06-12
Try this
```
sudo modprobe ath_pci
```

If that fails, it might be helpful to post the output of these commands
```
lsmod
```
```
modinfo ath_pci
```

---

### Post by tturrisi on 2007-06-12
change this:
auto wlan0
iface wlan0 inet dhcp
to this:
iface ath0 inet dhcp
wireless-essid YOUR-ESSID-HERE
auto ath0

When you run aircrack-ng, the first thing to do is destroy" the existing interface using airmon-ng:
airmon-ng stop ath0
Then put the card into monitor mode:
airmon-ng start wifi0 11 (where 11 = the channel you want to use)
Then bring up the interface:
ifconfig ath0 up
The above destroys the managed mode device & creates a monitor mode device.

When done using aircrack-ng you have to kill the device again.
Then bring it up in managed mode using madwifi tools, or reboot:
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta
or
wlanconfig ath create wlandev wifi0 wlanmode sta
a reboot will work too if you don't fool with any gui network connection tools that overwrite /etc/network.interfaces.

---

### Post by fracktor on 2007-06-12
Thank you all for the quick replies. Its greatly appreciated. I will try the solutions when i get home tonight from work and post the outcome tonight or tomorrow. Thanks again...

---

### Post by fracktor on 2007-06-15
Its still not working, here are the results...

I followed the steps and changed the following
auto wlan0
iface wlan0 inet dhcp
to this:
iface ath0 inet dhcp
wireless-essid YOUR-ESSID-HERE
auto ath0


sudo modprobe ath_pci
WARNING: Error inserting ath_hal (/lib/modules/2.6.20-15-generic/volatile/ath_hal.ko): Invalid module format
FATAL: Could not open '/lib/modules/2.6.20-15-generic/madwifi/ath_pci.ko': No such file or directory


sudo modinfo ath_pci
modinfo: could not open /lib/modules/2.6.20-15-generic/madwifi/ath_pci.ko: No such file or directory


sudo wlanconfig ath create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device


lsmod

Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
sg                     36252  0 
sd_mod                 23428  2 
usb_storage            72256  1 
libusual               17936  1 usb_storage
udf                    85252  1 
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
fuse                   46612  3 
sbp2                   23812  0 
lp                     12452  0 
hci_usb                18204  2 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
bluetooth              55908  7 rfcomm,l2cap,hci_usb
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
pcspkr                  4224  0 
usbhid                 26592  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nvidia               4713780  32 
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid                    27392  1 usbhid
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sis_agp                 9604  1 
emu10k1_gp              4736  0 
soundcore               8672  1 snd
wlan                  204484  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
gameport               16520  2 emu10k1_gp
agpgart                35400  2 nvidia,sis_agp
i2c_sis96x              6532  0 
i2c_core               22784  3 i2c_ec,nvidia,i2c_sis96x
af_packet              23816  4 
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
8139too                27648  0 
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  5 
pata_sis               14220  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  5 sg,sd_mod,usb_storage,sbp2,libata
floppy                 59524  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  7 usb_storage,libusual,hci_usb,usbhid,ehci_hcd,ohci_hcd
sis5513                14856  0 [permanent]
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by spd106 on 2007-06-15
You don't seem to have the madwifi driver installed. This means you need to either reinstall the linux-restricted-modules packages (that contain the madwifi driver) or rebuild the driver from source.

---

### Post by fracktor on 2007-06-15
I will try and reinstall the linux-restricted-modules and see what happens. Thanks for your reply.

---

### Post by tturrisi on 2007-06-15
> **fracktor said:**
> I will try and reinstall the linux-restricted-modules and see what happens. Thanks for your reply.

You cannot use the stock madwifi driver in restricted modules package with aircrack!  You can't use any packaged madwifi driver w/ aircrack.  The driver needs to be patched. Do this:

1. remove any existing madwifi drivers, uninstall via Synaptic if already installed them.
2. build the latest madwifi from source & patch using the aircrack madwifi patch.

3. next, open a ROOT terminal and do:
```
apt-get install build-essential
apt-get install linux-headers-`uname -r`
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```
Make sure the version of aircrack-ng you have is the latest STABLE version:
[http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=f8a31ae84c65078df2691440b5c44f26](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=f8a31ae84c65078df2691440b5c44f26)

---

