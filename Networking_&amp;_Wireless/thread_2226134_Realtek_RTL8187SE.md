---
title: "Realtek RTL8187SE"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by ralph6 on 2014-05-25
Hy there im ralph im a total newbee to linux. im running lubuntu on my msi u100. mainly cause its light and fast. i just installed but i cant get the wifi to work. can someone sort me out? i got no idea! thanks 






lubuntu@lubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
Linux lubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
lubuntu@lubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0110]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: r8180
lubuntu@lubuntu:~$ lsusb
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lubuntu@lubuntu:~$ iwconfig
wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

lubuntu@lubuntu:~$ rfkill list all
lubuntu@lubuntu:~$ lsmod
Module                  Size  Used by
zram                   18032  2 
cfg80211              409394  0 
dm_crypt               22622  0 
msi_wmi                13130  0 
gpio_ich               13229  0 
sparse_keymap          13708  1 msi_wmi
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dm_multipath           22402  0 
snd_rawmidi            25135  1 snd_seq_midi
scsi_dh                14458  1 dm_multipath
psmouse                91033  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
coretemp               13195  0 
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
r8187se               155125  0 
lpc_ich                16864  0 
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
eeprom_93cx6           13168  1 r8187se
soundcore              12600  1 snd
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
squashfs               42874  1 
overlayfs              27158  1 
nls_iso8859_1          12617  1 
dm_mirror              21756  0 
dm_region_hash         20121  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
i915                  705396  2 
ums_realtek            17733  0 
usb_storage            48417  2 ums_realtek
r8169                  61562  0 
mii                    13654  1 r8169
i2c_algo_bit           13197  1 i915
drm_kms_helper         46907  1 i915
wmi                    18673  1 msi_wmi
drm                   243792  3 i915,drm_kms_helper
video                  18903  1 i915
lubuntu@lubuntu:~$

---

### Post by squakie on 2014-05-25
I don't know if the module is present in 14.04 or not, but try the following:

- open a terminal window (ctrl/alt/F1)
- type:  sudo modprobe rtl8187 <press enter>
- if no error check in the network manager (the icon on the top line) and be sure networking is enabled, wireless networking is enabled
- now look on that same network manager screen and see if any available wireless networks are showing

- if there were errors in any of the above please post them back here.

I don't know if this works now or not.  I saw another thread for 13.10 which said the driver is included with Ubuntu now and to modprobe it (this let's the kernel know there is a module avaiable).

If this works, post back and I'll show you how to make in permanent.

---

### Post by ralph6 on 2014-05-26
Dude it worked thanks. so simple too ok if you now how! straight forward with your Instructions

I typed in the line as you suggested No error 
went onto network manager added a new wireless network typed in the pw all works fine.

Thank you !!!!!!!!!!!!!!!!!!!!!:guitar:

---

### Post by squakie on 2014-05-26
In order to make it permanent, so you don't have to do the modprobe everytime you reboot, you need to add it to the file that the kernel sees to know it should add a module.  That file is /etc/modules.  You can't edit that file unless you use sudo:

sudo gedit /etc/modules
go to the end of the file and start a new line
type:

rtl8187 <press enter>

Now just save the file and exit.  Whenever you reboot the module will be loaded automatically now.

Glad it worked for you!  Welcome, and enjoy Ubuntu!  Remember - any questions or problems - just post back in the forum with a descriptive title and a good explanation and the people here will try to help you.  It's a great volunteer community!

---

