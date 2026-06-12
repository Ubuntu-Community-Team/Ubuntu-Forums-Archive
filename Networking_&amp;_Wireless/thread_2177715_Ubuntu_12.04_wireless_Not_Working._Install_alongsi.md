---
title: "Ubuntu 12.04 wireless Not Working. Install alongside Win 7."
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by mx6KFEh on 2013-09-30
Hello, Just installed 12.04 alongside win 7 but my wireless is not working.  here is some info that i thought would be helpful based on the threads i have read. 

 ```
lsmod 


Module                          Size             Used by 
lib80211_crypt_tkip         17390           0 
wl                                3074618        0 
cfg80211                       525244  1       wl 
lib80211                        14352           2lib80211_crypt_tkip,wl 
btrfs                             816158         0 
zlib_deflate                   27110           1 btrfs 
ufs                               75150          0 
qnx4                            13396            0 
hfsplus                          89061          0 
hfs                               54780            0 
minix                           36386           0 
ntfs                             101633         0 
msdos                          17332            0 
jfs                               186588         0 
xfs                               888367         0 
libcrc32c                       12615           2btrfs,xfs 
reiserfs                         248298          0 
ext2                             73755            0 
bnep                            18258            2 
rfcomm                        47864           12 
parport_pc                     28284           0 
ppdev                            17113          0                
snd_hda_codec_hdmi        37434          1 
snd_hda_codec_idt         71153            1 
snd_hda_intel                44339            3 
snd_hda_codec              141716          3snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel 
coretemp                      13596           0 
joydev                          17613           0 
uvcvideo                        82214            0 
snd_hwdep                    13668           1snd_hda_codec 
videobuf2_core              40785           1uvcvideo 
snd_pcm                       102477          3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
i915                            620421            8 
videodev                      130053           2uvcvideo,videobuf2_core 
kvm                             455932          0 
snd_seq_midi                 13324           0 
videobuf2_vmalloc           13056          1uvcvideo 
videobuf2_memops         13202          1videobuf2_vmalloc 
snd_rawmidi                  30417           1snd_seq_midi 
btusb                            22431            0 
bluetooth                      247024           24bnep,rfcomm,btusb 
snd_seq_midi_event        14899          1snd_seq_midi 
snd_seq                        61930           2snd_seq_midi,snd_seq_midi_event 
drm_kms_helper           49597           1 i915 
snd_timer                    29989             2snd_pcm,snd_seq 
hp_wmi                       18092             0 
snd_seq_device             14497            3snd_seq_midi,snd_rawmidi,snd_seq 
sparse_keymap             13890           1 hp_wmi 
drm                            287564          4i915,drm_kms_helper 
microcode                    23017           0 
psmouse                     97873            0 
rtsx_pci_ms                13180             0 
serio_raw                  13215               0 
wmi                          19256            1 hp_wmi 
snd                           69533            16snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit              13564             1 i915 
soundcore                12680              1 snd 
intel_ips                  18066              0 
memstick                16605             1rtsx_pci_ms 
mei                        41820              0 
snd_page_alloc         18798             2snd_hda_intel,snd_pcm 
mac_hid                   13253            0 
lpc_ich                     17144            0 
video                       19652            1 i915 
lp                            17799              0 
parport                    46562           3parport_pc,ppdev,lp 
rtsx_pci_sdmmc       17800            0 
ahci                         25879          2 
rtsx_pci                   34214            2rtsx_pci_ms,rtsx_pci_sdmmc 
libahci                    31606              1 ahci 
r8169                      68716              0 




 lspci -nnk | grep -iA2 net 


02:00.0 Network controller [0280]:Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter[14e4:4727] (rev 01) 
    Subsystem: Hewlett-Packard CompanyDevice [103c:1483] 
    Kernel driver in use: wl 
-- 
03:00.0 Ethernet controller [0200]:Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express FastEthernet controller [10ec:8136] (rev 05) 
    Subsystem: Hewlett-Packard CompanyDevice [103c:166a] 
    Kernel driver in use: r8169 




iwconfig 


eth0      no wireless extensions. 


eth1      IEEE 802.11abg  ESSID:off/any 
          Mode:Managed  Access Point:Not-Associated   
          Retry  long limit:7   RTSthr:off   Fragment thr:off 
          Power Management:off 
          
lo        no wireless extensions. 




rfkill list all 


1: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
2: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
3: brcmwl-0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no  
```

Can someone help plz

---

### Post by mx6KFEh on 2013-09-30
:o  =  : o

---

### Post by Karlchen on 2013-09-30
Hm, seems as if your Broadcom 4313 is detected by Ubuntu perfectly well. Your Ubuntu 12.04 is using the same driver "wl" as mine.
Yet, I wonder whether you have failed to click on the little network manager icon perhaps?
Doing so - I mean clicking on it - will open a popup list of all the wireless networks which have been detected.
Select your own wireless LAN from the list, enter your passphrase when prompted to do so and network manager should connect.
[ATTACH=CONFIG]246633[/ATTACH]

---

### Post by Hadaka on 2013-09-30
Hi, give this a try
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v brcmsmac
```
boot
thanks

---

### Post by mx6KFEh on 2013-09-30
Thanks heaps Hadaka. It worked.

But...

Could you please expalin what those commands are and what did they do? What was not working? As a new commer to linux after many years of enduring windows, I would like to learn a thing or two here.

Regards,

Moe

---

### Post by Hadaka on 2013-09-30
Hi, glad its working!
your wireless card-BCM4313 [14e4:4727] can work on the wl driver
which is what you had loaded,however at this point in time that card
seems to work better with the native driver brcmsmac.
please mark your thread solved.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

