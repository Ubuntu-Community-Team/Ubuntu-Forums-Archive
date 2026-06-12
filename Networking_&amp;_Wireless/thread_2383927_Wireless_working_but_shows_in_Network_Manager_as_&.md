---
title: "Wireless working but shows in Network Manager as &quot;device not managed&quot;"
date: 2018-01-31
forum: Networking &amp; Wireless
---

### Post by robert-4elanclose on 2018-01-31
Hi all,

I have a Sony Vaio VGN-FW51MF.

Freshly installed Xubuntu 17.10 Server and obviously connected to a network during setup.

Now I have the issue that although I'm connected I cannot manage the network connection and cannot setup my VPN using the network manager.

I've read several posts and tried multiple things...

Below is the results of the various code items that should describe the hardware - If I've missed anything, please let me know... I've got no idea what to do next.

Cheers,

Rob.

```
rob@battleship:/usr/share/polkit-1/actions$ lspci -nnk | grep -iA2 net06:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1301]
	Kernel driver in use: iwlwifi
--
08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 14)
	Subsystem: Sony Corporation 88E8055 PCI-E Gigabit Ethernet Controller [104d:9035]
	Kernel driver in use: sky2
	Kernel modules: sky2
rob@battleship:/usr/share/polkit-1/actions$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd BCM2046 Bluetooth Device
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183d Ricoh Co., Ltd Sony Vaio Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rob@battleship:/usr/share/polkit-1/actions$ iwconfig
lo        no wireless extensions.


enp8s0    no wireless extensions.


wlp6s0    IEEE 802.11  ESSID:"SKY378CD"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 90:21:06:8F:26:39   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6561  Invalid misc:1735100   Missed beacon:0


rob@battleship:/usr/share/polkit-1/actions$ rfkill list all
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
rob@battleship:/usr/share/polkit-1/actions$ lsmod
Module                  Size  Used by
rfcomm                 77824  14
snd_hrtimer            16384  1
des_generic            24576  0
md4                    16384  0
nls_utf8               16384  1
cifs                  712704  2
fscache                61440  1 cifs
ccm                    20480  3
bnep                   20480  2
coretemp               16384  0
uvcvideo               90112  0
kvm                   581632  0
irqbypass              16384  1 kvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_codec_realtek    94208  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  4
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
joydev                 20480  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
input_leds             16384  0
serio_raw              16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
r592                   20480  0
memstick               16384  1 r592
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
bluetooth             540672  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
lpc_ich                24576  0
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
arc4                   16384  2
iwldvm                229376  0
snd                    81920  20 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
mac80211              778240  1 iwldvm
iwlwifi               249856  1 iwldvm
soundcore              16384  1 snd
cfg80211              610304  3 iwlwifi,mac80211,iwldvm
mac_hid                16384  0
sony_laptop            61440  0
shpchp                 36864  0
ib_iser                49152  0
rdma_cm                57344  1 ib_iser
iw_cm                  45056  1 rdma_cm
ib_cm                  49152  1 rdma_cm
ib_core               212992  4 ib_iser,ib_cm,rdma_cm,iw_cm
iscsi_tcp              20480  0
libiscsi_tcp           20480  1 iscsi_tcp
libiscsi               53248  3 ib_iser,libiscsi_tcp,iscsi_tcp
scsi_transport_iscsi    94208  4 ib_iser,libiscsi,iscsi_tcp
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
btrfs                1097728  0
raid10                 49152  0
raid456               143360  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_xor,async_pq,raid456,async_memcpy,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              118784  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  40960  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
hid_logitech_hidpp     32768  0
amdkfd                188416  1
hid_logitech_dj        20480  0
amd_iommu_v2           20480  1 amdkfd
radeon               1470464  3
sdhci_pci              28672  0
usbhid                 49152  0
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
ahci                   36864  1
firewire_ohci          40960  0
drm_kms_helper        167936  1 radeon
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
sdhci                  45056  1 sdhci_pci
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
libahci                32768  1 ahci
sky2                   61440  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   356352  6 radeon,ttm,drm_kms_helper
video                  40960  1 sony_laptop

```

---

### Post by chili555 on 2018-01-31
>  If I've missed anything, please let me know... I've got no idea what to do next.Please show us:```
cat /etc/network/interfaces
cat /etc/netplan/01-network-manager-all.yaml
```If the last command yields no result, then run:```
ls /etc/netplan
```And then:```
cat /etc/netplan/<file_you_found>.yaml
```

---

### Post by robert-4elanclose on 2018-01-31
Here you go...

```
rob@battleship:~/Downloads/iwlwifi-5000-ucode-8.83.5.1$ cat /etc/network/interfaces# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)
# Generated by debian-installer.


# The loopback interface
auto lo
iface lo inet loopback
rob@battleship:~/Downloads/iwlwifi-5000-ucode-8.83.5.1$ cat /etc/netplan/01-network-manager-all.yaml
cat: /etc/netplan/01-network-manager-all.yaml: No such file or directory
rob@battleship:~/Downloads/iwlwifi-5000-ucode-8.83.5.1$ ls /etc/netplan
01-netcfg.yaml
rob@battleship:~/Downloads/iwlwifi-5000-ucode-8.83.5.1$ cat /etc/netplan/01-netcfg.yaml
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  wifis:
    wlp6s0:
      dhcp4: yes
      dhcp6: yes
      access-points:
        SKY378CD:
          password: xxxxxxxx

```

I obviously removed the password :)

Thanks so much

---

### Post by chili555 on 2018-01-31
Your netplan file assumes the usual server configuration; that is, no desktop environment, no Network Manager and no GUI. However, you have installed and apparently prefer NM. Let's see if we can reconfigure netplan.

First, let's back up the current file so that if things are not quite right, we can recover. From the terminal:```
sudo mv /etc/netplan/01-netcfg.yaml  /etc/netplan/01-netcfg.yaml.bak
```Now we write a new file:```
sudo nano /etc/netplan/01-network-manager-all.yaml
```Add the following to the new file:```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```Please note that the spacing, indentation, etc. are crucial and must be exact. Proofread carefully twice. Save the file (Ctrl+o followed by Enter) and exit the text editor (Ctrl+x).

Cross your fingers and reboot. Any improvement?

---

### Post by robert-4elanclose on 2018-01-31
Fingers were crossed. You are a star - I hadn't expected that adding the GUI would result in it not creating the hooks to the NM and allowing it to be used when operational. Thanks so much.

I don't always use the GUI, would I have to undo this to run without a GUI?

Cheers for being so clear and helpful.

Rob.

---

### Post by robert-4elanclose on 2018-01-31
Just realised that I didn't actually say... It worked perfectly!

---

### Post by chili555 on 2018-01-31
> I don't always use the GUI, would I have to undo this to run without a GUI?
I'm not exactly sure, but I suspect so. We would be very interested in your report, however!

My advice is to do one or the other and stick to it. Having said that, I have no experience with VPN and haven't any idea how to set it up in netplan!

Glad it's working as expected.

---

