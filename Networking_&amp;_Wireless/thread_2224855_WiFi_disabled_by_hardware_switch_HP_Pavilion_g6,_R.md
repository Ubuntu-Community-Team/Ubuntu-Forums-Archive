---
title: "WiFi disabled by hardware switch: HP Pavilion g6, Ralink RT5390"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by Marc_Sabatella on 2014-05-18
I am trying to install (actually, "try without installing") Ubuntu Studio 14.04 on my HP Pavilion g6 with the Ralink RT5390 wireless card.  No luck - wireless is disabled "by hardware switch" and will not enable with the F12 key that normally accomplishes this under Windows.  I've seen a whole slew of threads here and elsewhere on this, but mostly from three years ago, involving previous releases of Ununtu.

I have little confidence that specific suggestions (which sometimes involved needing to recompile the kernel!) provide in 2011 are still relevant.  But my symptoms seem common enough: the networking menu reports WiFi is disabled by hardware switch, rfkill reports my device is hard blocked, toggling the F12 key (the usual hardware WiFi switch for this model) accomplishes nothing.  Other function keys work as expected - F2/F3 for brightness, etc.

FWIW, the laptop was sold with Windows 7 and that's what it has been running.  I once tried to install Windows but ran into a similar issue - F12 would only toggle Airplane Mode and would not actually enable the WiFi.  I had updated the BIOS back then in an effort to get this working, but no luck, so I reverted to Windows 7.  I had encountered the same problem I am having now last years when I tried out a previous version of Ubunto (12.something, I think).  i was hoping that if the issue was a kernel incompatibility, this would have fixed by now, but no such luck I guess.

I'm a Linux newbie but I used other Unix variants decades ago and remember a thing or two.

---

### Post by varunendra on 2014-05-21
Hello Marc, Welcome to the forums!

Please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
lsusb
lsmod
grep -i switch /var/log/syslog
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Marc_Sabatella on 2014-06-03
Sorry to have disappeared.  I actually ended up getting a "new" (to me) computer and installing Ubuntu on that - this seemed a better way to go for me anyhow.

---

### Post by elringo70 on 2014-09-18
I have the exact same problem, any solution???

---

### Post by chili555 on 2014-09-18
We hope you will start at post #2.

---

### Post by cezar2 on 2015-04-11
I hope you can help me.

Code:
> cezar:~$ uname -mr
3.13.0-49-generic x86_64
cezar:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci
cezar:~$ lsusb
Bus 002 Device 002: ID 0461:4dd8 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cezar:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             391136  10 bnep,rfcomm
uvcvideo               80885  0 
snd_hda_codec_realtek    65580  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          56531  6 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
hp_wmi                 14062  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
sparse_keymap          13948  1 hp_wmi
snd_rawmidi            30144  1 snd_seq_midi
arc4                   12608  2 
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
radeon               1522664  3 
mac80211              630669  3 rt2x00lib,rt2x00pci,rt2800lib
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 17381  0 
serio_raw              13462  0 
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
ttm                    93424  1 radeon
drm_kms_helper         55071  1 radeon
kvm_amd                60026  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
kvm                   455835  1 kvm_amd
rtsx_pci_ms            18151  0 
k10temp                13126  0 
memstick               16966  1 rtsx_pci_ms
snd                    69322  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
shpchp                 37032  0 
hp_wireless            12637  0 
video                  19476  0 
i2c_algo_bit           13413  1 radeon
wmi                    19177  1 hp_wmi
i2c_piix4              22155  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
psmouse               106714  0 
r8169                  67581  0 
mii                    13934  1 r8169
rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   29915  2 
libahci                32716  1 ahci
cezar:~$ grep -i switch /var/log/syslog
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [    0.444009] Switched to clocksource hpet
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [    1.540347] Console: switching to colour frame buffer device 170x48
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [    1.620377] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [    1.620904] ACPI: Lid Switch [LID]
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [    3.397090] Switched to clocksource tsc
Apr 11 16:58:35 monica-HP-2000-Notebook-PC kernel: [   15.096242] Console: switching to colour dummy device 80x25
Apr 11 16:58:36 monica-HP-2000-Notebook-PC kernel: [   17.117647] Console: switching to colour frame buffer device 170x48
Apr 11 16:58:45 monica-HP-2000-Notebook-PC NetworkManager[810]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/ieee80211/phy0/rfkill0) (driver rt2800pci)
Apr 11 16:58:45 monica-HP-2000-Notebook-PC NetworkManager[810]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (platform driver hp-wmi)
Apr 11 16:58:45 monica-HP-2000-Notebook-PC NetworkManager[810]: <info> WiFi disabled by radio killswitch; enabled by state file
Apr 11 16:58:45 monica-HP-2000-Notebook-PC NetworkManager[810]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 11 16:58:45 monica-HP-2000-Notebook-PC NetworkManager[810]: <info> WiMAX enabled by radio killswitch; enabled by state file

Thanks

---

### Post by chili555 on 2015-04-11
> **cezar2 said:**
> I hope you can help me.

Code:

ThanksI notice this:> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (platform driver hp-wmi)I wonder if you remove the module, the wireless might spring to life:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```I also assume you have located and switched every wireless switch or key combination on your laptop and had no change.

May we also see:```
cat /sys/devices/platform/hp-wmi/rfkill/rfkill1
```It will likely be a 1 or a 0.

---

