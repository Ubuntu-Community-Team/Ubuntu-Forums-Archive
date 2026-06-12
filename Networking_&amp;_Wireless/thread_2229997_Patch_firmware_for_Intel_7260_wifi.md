---
title: "Patch firmware for Intel 7260 wifi"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by kjetil-fleten on 2014-06-16
After upgrading from 13.10 to 14.04, bluetooth stoped working on a Intel 7260 wifi. I have successfully upgraded firmware to the second latest version (22.24.8.0), by downloading the code from [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi), unpacking and copying to /lib/firmware. That did not bring bluetooth back. There is a newer firmware version (23.14.9.0) that can be installed in the same manner, but it requires a patch before installing. I have copied the patch content at [https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=431031851ea72a25abb9ad4df56a0f3b997e3026](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=431031851ea72a25abb9ad4df56a0f3b997e3026) to a file I have called "patch", and then done "sudo patch iwlwifi-7260-9.ucode < patch".
 Unfortunately, I'm not familiar with the syntax of patch files, so I guess I have included to much, or to little in the patch file. The output varies from "**** Only garbage was found in the patch input" to "**** malformed patch at line 7: /* Highest firmware API version supported */",  depending on my syntax.
Can anyone help me get the patch right ?

[ATTACH]253998[/ATTACH]

---

### Post by chili555 on 2014-06-19
This is a patch to the underlying iwlwifi driver, specifically iwl-7000.c; not the firmware itself. The patch is only two lines, so you could easily make the change manually. It would involve downloading the backports package, making the change in iwl-7000.c and then compiling the entire package and installing it. Sounds daunting but isn't, really.

Do you think the firmware is required by bluetooth as well as wireless? I suspect not.

May we see:```
rfkill list all
lsmod
dmesg | grep -i blue
```Thanks.

---

### Post by jeremy31 on 2014-06-19
What is the actual name of the card ```
lspci
```
I have 2 different versions of the 7260, the bluetooth works only on the non AC card with 14.04

---

### Post by kjetil-fleten on 2014-06-27
Here is all output from: 
lspci
rfkill list all
lsmod
dmesg | grep -i blue

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Module                  Size  Used by
iptable_filter         12810  0 
ip_tables              27239  1 iptable_filter
x_tables               34059  2 ip_tables,iptable_filter
ctr                    13049  1 
ccm                    17773  1 
dm_crypt               23177  0 
joydev                 17381  0 
uvcvideo               80885  0 
hid_logitech_dj        18581  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
usbhid                 52570  0 
hid                   106148  4 usbhid,hid_logitech_dj
rfcomm                 69160  4 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
arc4                   12608  2 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  2 
iwlmvm                189774  0 
snd_hda_codec         192906  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
mac80211              626557  1 iwlmvm
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
crct10dif_pclmul       14289  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crc32_pclmul           13113  0 
snd_rawmidi            30144  1 snd_seq_midi
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  14 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
iwlwifi               169932  1 iwlmvm
mei_me                 18627  0 
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
lpc_ich                21080  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
nls_iso8859_1          12713  1 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i915                  783703  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
ahci                   25819  3 
libahci                32168  1 ahci
video                  19476  1 i915

[    4.090717] Bluetooth: Core ver 2.17
[    4.090942] Bluetooth: HCI device and connection manager initialized
[    4.090952] Bluetooth: HCI socket layer initialized
[    4.090956] Bluetooth: L2CAP socket layer initialized
[    4.090964] Bluetooth: SCO socket layer initialized
[    4.099431] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.099437] Bluetooth: BNEP filters: protocol multicast
[    4.099447] Bluetooth: BNEP socket layer initialized
[    4.122302] Bluetooth: RFCOMM TTY layer initialized
[    4.122316] Bluetooth: RFCOMM socket layer initialized
 [    4.122324] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2014-06-27
Do you have a ISO from 13.10 to do some testing with, burn it to DVD or write to USB.  Then select try Ubuntu and run the above commands again.  There must be some model specific module that is not finding the Bluetooth on 14.04 that worked on 13.10
this is what I see from those commands
```
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)

[    8.374801] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[    8.374860] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[    9.236236] Bluetooth: Core ver 2.17
[    9.236259] Bluetooth: HCI device and connection manager initialized
[    9.236267] Bluetooth: HCI socket layer initialized
[    9.236269] Bluetooth: L2CAP socket layer initialized
[    9.236274] Bluetooth: SCO socket layer initialized
[    9.619767] Bluetooth: hci0: read Intel version: 370710018002030d00
[   10.038926] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   10.198416] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   12.051076] Bluetooth: RFCOMM TTY layer initialized
[   12.051088] Bluetooth: RFCOMM socket layer initialized
[   12.051092] Bluetooth: RFCOMM ver 1.11
[   12.870850] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.870854] Bluetooth: BNEP filters: protocol multicast
[   12.870861] Bluetooth: BNEP socket layer initialized

lsmod | grep blue
bluetooth             395423  22 bnep,btusb,rfcomm
toshiba_bluetooth      12852  0 

```

---

### Post by kjetil-fleten on 2014-07-08
I tried to boot from 13.10 Live USB today, but unfortunately Bluetooth does not show up now, like it did when the system was installed.

Here is output from    lspci
rfkill list all
lsmod
dmesg | grep -i blue



```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               22728  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
arc4                   12608  2 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1 ghash_clmulni_intel
uvcvideo               80885  0 
iwlmvm                161349  0 
mac80211              596969  1 iwlmvm
snd_hda_codec_hdmi     41276  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  2 
joydev                 17377  0 
snd_hda_codec         188738  2 snd_hda_codec_hdmi,snd_hda_intel
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwlwifi               165398  1 iwlmvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
cfg80211              479757  3 iwlwifi,mac80211,iwlmvm
mac_hid                13205  0 
mei_me                 18421  0 
snd                    69141  14 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    77692  1 mei_me
soundcore              12680  1 snd
microcode              23518  0 
lpc_ich                21080  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
bnep                   19564  2 
rfcomm                 69070  0 
bluetooth             371874  10 bnep,rfcomm
squashfs               47663  1 
overlayfs              27858  1 
nls_iso8859_1          12713  1 
usb_storage            62062  1 
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   101512  4 usbhid,hid_logitech_dj
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
i915                  655752  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  4 i915,drm_kms_helper
ahci                   25819  1 
libahci                31898  1 ahci
video                  19318  1 i915
ubuntu@ubuntu:~$ dmesg | grep -i blue
[   22.772120] Bluetooth: Core ver 2.16
[   22.772144] Bluetooth: HCI device and connection manager initialized
[   22.772151] Bluetooth: HCI socket layer initialized
[   22.772153] Bluetooth: L2CAP socket layer initialized
[   22.772158] Bluetooth: SCO socket layer initialized
[   22.836280] Bluetooth: RFCOMM TTY layer initialized
[   22.836304] Bluetooth: RFCOMM socket layer initialized
[   22.836307] Bluetooth: RFCOMM ver 1.11
[   22.862281] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.862286] Bluetooth: BNEP filters: protocol multicast
[   22.862297] Bluetooth: BNEP socket layer initialized
ubuntu@ubuntu:~$ 
```

---

### Post by jeremy31 on 2014-07-08
This is the Intel Dual Band AC model?  Anything in ```
lsusb
```

---

### Post by kjetil-fleten on 2014-07-19
Yes, this is the Intel Dual Band AC model.

lsusb gives:```
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 1bcf:2885 Sunplus Innovation Technology Inc. ASUS Webcam
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jeremy31 on 2014-07-20
Unless a kernel update to 3.14 or 3.15 fixes the issue, I have no idea how to get it to work as the only laptop I can use the Dual Band AC card in never boots to a kernel downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and so far 3.13.0-30 doesn't make BT work

I think it is strange that nothing shows up in lsusb when my other intel 7260 does show a bluetooth device there.  It could be an Intel issue, I think there were non dual band intel wifi cards working as dual band in 13.10

The BT should show in lsusb as 8087:07dc so I wonder if ```
dmesg | grep 8087
``` might show something useful.  I put mine in another laptop, BT worked but the wifi was hard blocked and I think the wifi was hardblocked because it originally had a wifi/wimax card.

The card doesn't work at all when I boot into Win 7

---

### Post by kjetil-fleten on 2014-07-30
If it's useful, I don't know - but at least it shows something :-)
```
[    2.305950] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.550142] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
```

---

### Post by jeremy31 on 2014-07-30
> **kjetil-fleten said:**
> If it's useful, I don't know - but at least it shows something :-)
```
[    2.305950] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.550142] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
```

that showed up in your lsusb as an intel rate matching hub.  Anything in BIOS that can enable/disable bluetooth?

---

### Post by mazdarx7j on 2015-01-11
I am having the EXACT problem with 14.10. Same card as kjetil-fleten and same issue. Ran all the same commands. Checked that iwlwifi was loaded...nothing. Tried running Arch/Antergos to get the newest kernel in live cd and it didn't detect it either. I have no idea what to do and I am really regretting buying this card. 

I have also contacted Intel to ask for their help and their response was....a joke. 

They then hounded me to make sure that my experience was positive. They were more interested in customer reviews than helping me out it seems. 

I wish I had something to add to this thread and I will once I discover something. I just didn't want anyone to feel like they were alone with this issue.

---

### Post by kjetil-fleten on 2015-01-12
Actually, I found out that my card was broken, and that I had to replace it. After that, Bluetooth worked. 
I had some issues with a bluetooth headset after getting bluetooth to work, but that was then resolved by
sudo apt-get purge blueman

---

### Post by aileanr on 2015-01-21
Having the same problem with this card. Not showing up anywhere at all. 

I might send it back then and have it replaced.

---

