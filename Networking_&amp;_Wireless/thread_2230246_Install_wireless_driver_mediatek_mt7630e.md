---
title: "Install wireless driver mediatek mt7630e"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by Vyivrain on 2014-06-18
Hello, I'm trying to install wi-fi driver, but as a beginner don't know what to do, googling didn't do much.So this is information after this commands:
1:
```

vyivrain@vyivrain-X550VB:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
Linux vyivrain-X550VB 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
2:
```

vyivrain@vyivrain-X550VB:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
	Subsystem: Foxconn International, Inc. Device [105b:e074]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169

```
3:
```

vyivrain@vyivrain-X550VB:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```
4:
```

vyivrain@vyivrain-X550VB:~$ rfkill list all
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
```

vyivrain@vyivrain-X550VB:~$ lsmod
Module                  Size  Used by
btrfs                 835954  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    74890  0 
qnx4                   13317  0 
hfsplus               107516  0 
hfs                    54677  0 
minix                  36140  0 
ntfs                   97369  0 
msdos                  17332  0 
jfs                   181348  0 
xfs                   912173  0 
libcrc32c              12644  2 xfs,btrfs
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
joydev                 17381  0 
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
snd_hda_intel          52355  3 
serio_raw              13462  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  1 mei_me
i915                  783703  4 
nouveau              1097199  1 
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
drm_kms_helper         52758  2 i915,nouveau
drm                   302817  8 ttm,i915,drm_kms_helper,nouveau
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
mac_hid                13205  0 
video                  19476  3 i915,nouveau,asus_wmi
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169

```
And after this point I don't know, what to do. Thx for answering.

---

### Post by deadflowr on 2014-06-18
Moved to **Networking and Wireless**

---

### Post by DuckHook on 2014-06-18
I don't have your WIFI chipset, but a brief Google search shows that it has problematic support in the Linux kernel and there isn't much of a workaround at this point either. Details are in [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146") bug report, especially comment #31.

My reading of the situation is that you must either be prepared to regress to kernel 3.5.x (Ubuntu 12.04.0) or else patiently wait for the bug to be fixed in an upcoming release. Some reports suggest that OpenSUSE appears to have fixed the bug (or included patched drivers) in their release, so you might try that distro instead.

The fact is that I'm not knowledgeable about this issue at all, but seeing as no one else has responded, thought that you might appreciate at least an amateurish look into things.

BTW, you did well posting with so much info. It's always easier to look into things when a problem is accompanied with proper info.

---

### Post by chili555 on 2014-06-18
> it has problematic support in the Linux kernel and there isn't much of a workaround at this point either.I have studied this on several occasions and even tried to compile the driver. DuckHook is quite correct. I am unaware of any method to get this device going in Ubuntu 14.04.

---

### Post by Vyivrain on 2014-06-21
On windows 8, I have ralink drivers installed for wi-fi. Maybe if I install the same or another version of this driver I could start my wi-fi off running? But the problem is I didn't find any good tutorial for installing that on ubuntu 14.04.

---

### Post by DuckHook on 2014-06-23
> **Vyivrain said:**
> On windows 8, I have ralink drivers installed for wi-fi. Maybe if I install the same or another version of this driver I could start my wi-fi off running? But the problem is I didn't find any good tutorial for installing that on ubuntu 14.04.Unfortunately, it isn't that simple:

Linux and Windows are two completely different animals. Using a Windows driver in Linux is analogous to using a Ford engine part in a Toyota. Though both are cars, they are entirely different machines and parts cannot just be interchanged at leisure. WinXP drivers are the only ones (to my knowledge) that can be force-fitted into Linux and that is done through a butt-ugly kludge called *ndiswrapper* that degrades performance if it works at all. W8 drivers simply will not work, and the same cited bug report implies that no XP driver exists for this relatively newish chipset.

If you want to continue using Ubuntu on this computer, your best bet is to buy a cheap USB WIFI stick (starting at $3.00 on ebay) that is known to work in Ubuntu. *chili555* has stated that s/he cannot get this WIFI chipset to work in Linux, and if *chili* (bona fide guru) can't do it, no one can.

---

### Post by chili555 on 2014-06-23
If it were me, I'd invest US$12-15 in a supported USB wireless device and wait a year or so for the mt7630e to gain support.

If you'd like to try the butt-ugly kludge called ndiswrapper that degrades performance if it works at all, you'll need the XP driver files, probably .inf and .sys appropriate to your architecture; either 32- or 64-bit. If you can find these, we'll be happy to help you *try* ndiswrapper.

Sadly, in Linux, not every device is perfectly supported from the day it is introduced.

---

### Post by cqfd93 on 2014-09-01
Hi,

Check out comment #161 (and if it doesn't work for you, comment #125) of bug #1220146

[https://bugs.launchpad.net/ubuntu/+s...6/comments/161]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161")
[https://bugs.launchpad.net/ubuntu/+s...6/comments/125]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125")

Hope this helps

---

### Post by plaksa28 on 2014-10-11
[http://community.linuxmint.com/tutorial/view/1796](http://community.linuxmint.com/tutorial/view/1796)
[https://askubuntu.com/questions/459436/ubuntu-14-04-ralink-rt-3290-wireless-lan-hard-blocked/487012#487012?newreg=47de4132557d4a5187a785543b5ffb54](https://askubuntu.com/questions/459436/ubuntu-14-04-ralink-rt-3290-wireless-lan-hard-blocked/487012#487012?newreg=47de4132557d4a5187a785543b5ffb54)


Sorry, I do not speak English))),But I understand your problem

---

### Post by jamur on 2015-03-04
I solved it for my Asus N750JV like this
[http://ubuntuforums.org/showthread.php?t=2250569&highlight=mediatek+mt7630e](http://ubuntuforums.org/showthread.php?t=2250569&highlight=mediatek+mt7630e)
see second comment.

---

### Post by Brdics_Zoltn on 2016-01-16
Thanx! Helped on my HP Probook 450 G1 also.

---

