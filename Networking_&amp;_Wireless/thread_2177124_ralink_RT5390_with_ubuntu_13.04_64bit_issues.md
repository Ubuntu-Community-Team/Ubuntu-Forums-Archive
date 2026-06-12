---
title: "ralink RT5390 with ubuntu 13.04 64bit issues"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by Ashiata on 2013-09-27
Hello...
 
I installed ubuntu 13.04 64bit with my asus x55u, dual booting with windows 8. The wireless works just fine with windows. I have Ralink RT5390 wireless card.

When trying out ubuntu, the wireless would detect different wifi spots including from my house but it wouldn`t connect. I would type in the password and it took a long time and just asked for password again or disconnected. After a lot of reading, I came up with the following solution from different threads:
> 
1. download driver [http://www.mediatek.com/_en/07_downl...il.php?sn=5001](http://www.mediatek.com/_en/07_downl...il.php?sn=5001)
2 tar -xvf /home/USERNAME/Downloads/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2. bz2.bz2
3 cd 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
4 download patch [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)
5 patch -p1 <rt5592sta_fix_64bit_3.8.patch (if asks for directory point it to pci_main_dev.c)
6 make sure /os/linux/config.mk reads HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
7 make
8 sudo make install
9 modprobe rt5390sta
10 sudo gedit /etc/modprobe.d/blacklist.conf
11 At the end of the file, add these lines:

# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

I restarted the computer and it worked perfectly, the wireless connected fast to my house`s router, it also was detecting a lot more wifi connections from neighbours, signal strenght was good, speed too. Then I shut down my computer and started it again, and suddenly the wifi adapter is not being detected anymore. With windows, its still working fine, with ubuntu its as if the kernel is not being detected or something. I did not delete or change anything.  Before doing this whole thing, if I`d do the command:

lspci -vvnn

Id get (for the network controller part):
> 01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fea00000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci

Sorry I didn`t do this while it was working, but now after restart when it stopped working, if I do the same I get:


> 01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at fea00000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>



Notice it doesn`t say anything about kernel driver in use anymore.. Why not?  How can I get it to work again ?

Thanks!

---

### Post by wildmanne39 on 2013-09-27
Hi, please remove these > blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
from the blacklist file.
Then reboot is wireless now on?
Thanks

---

### Post by shultz.andrey on 2013-11-26
I've got the same problem. Yesterday I download updates and my notebook (Asus x301a) lost wifi and network connection. Last post resolve problem with wifi connections, but I still can't connect via cable. How can I resolve this problem?

---

### Post by varunendra on 2013-11-26
Welcome to the forums shultz !

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
```
This will tell us about your network cards, both wired and wireless, and the drivers currently loaded.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by shultz.andrey on 2013-11-27
```
lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14f7]
    Kernel driver in use: r8169

```

```

lsmod

Module                  Size  Used by
bnep                   17669  2 
rfcomm                 37420  4 
bluetooth             202232  10 bnep,rfcomm
parport_pc             27504  0 
ppdev                  12817  0 
binfmt_misc            17260  1 
snd_hda_codec_hdmi     36186  1 
snd_hda_codec_realtek    63791  1 
joydev                 17097  0 
snd_hda_intel          38307  2 
snd_hda_codec         117617  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
rt5390sta            1377300  0 
arc4                   12543  2 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
i915                  539721  3 
uvcvideo               71279  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
rt2800pci              18198  0 
rt2800lib              60947  1 rt2800pci
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
rt2x00pci              14151  1 rt2800pci
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_timer              24411  2 snd_pcm,snd_seq
videobuf2_core         39161  1 uvcvideo
rt2x00lib              48570  3 rt2x00pci,rt2800lib,rt2800pci
drm_kms_helper         47545  1 i915
mac80211              526519  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              436243  2 mac80211,rt2x00lib
snd                    56485  14 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   228489  4 i915,drm_kms_helper
psmouse                81065  0 
videodev               95806  2 uvcvideo,videobuf2_core
asus_nb_wmi            12734  0 
asus_wmi               23517  1 asus_nb_wmi
eeprom_93cx6           13168  1 rt2800pci
sparse_keymap          13658  1 asus_wmi
mei                    36197  0 
mac_hid                13037  0 
rtsx_pci_ms            12875  0 
crc_ccitt              12627  1 rt2800lib
memstick               15842  1 rtsx_pci_ms
wmi                    18590  1 asus_wmi
lpc_ich                16925  0 
coretemp               13131  0 
serio_raw              13031  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
microcode              18286  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
video                  18894  2 i915,asus_wmi
hid_generic            12484  0 
usbhid                 41805  0 
hid                    87001  2 hid_generic,usbhid
rtsx_pci_sdmmc         17238  0 
r8169                  61543  0 
rtsx_pci               32831  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25507  2 
libahci                26108  1 ahci

```

---

### Post by varunendra on 2013-11-28
> **shultz.andrey said:**
> ```

**[COLOR="#FF0000"]rt5390sta[/COLOR]**            1377300  0
....
....
**[COLOR="#FF0000"]rt2800pci[/COLOR]**              18198  0 
rt2800lib              60947  1 rt2800pci
....

```

Both the proprietary and the native drivers are loading simultaneously which may be causing problem. You can use one of them at a time, not both at once. Since you have installed the proprietary one, it means the native one might have not worked satisfactorily for you, so let's blacklist it to try the proprietary one. Please open a terminal (Ctrl-Alt-T) and run the following command (you may copy-paste to avoid typo)-
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then either reboot and check -
```
lsmod | egrep '5390|rt2'
```
You should see only "**rt5390sta**" in the outputs. If so, can you connect? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by shultz.andrey on 2013-11-28
Unfortunately code

```
[COLOR=#000000][FONT=Ubuntu Mono]echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
```

doesn't help me. It also cut my wifi.

---

### Post by varunendra on 2013-11-28
Please post back the report I asked for.

---

