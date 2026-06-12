---
title: "No ethernet or wifi on fresh Lubuntu 16.04 install, Acer Aspire 5560"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by centipede2 on 2016-09-15
Installed alongside Windows 7. No wired or wireless intnernet, even after reboot, even during usb test.

---

### Post by wildmanne39 on 2016-09-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by centipede2 on 2016-09-15
I'm sorry, I'm sort of confused. Can you rephrase that? Do you want me to run those commands, and copy and paste the output in a comment here?

---

### Post by wildmanne39 on 2016-09-15
Sorry about that it has been a long day and I missed the first part of the copy and paste, I have edited the previous post.

---

### Post by centipede2 on 2016-09-16
> **Wild Man said:**
> Sorry about that it has been a long day and I missed the first part of the copy and paste, I have edited the previous post.

```
john@john-Aspire-5560:~$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux john-Aspire-5560 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
john@john-Aspire-5560:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] NetLink BCM57785 Gigabit Ethernet PCIe [1025:0605]
	Kernel driver in use: tg3
	Kernel modules: tg3
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
	Subsystem: Foxconn International, Inc. BCM43227 802.11b/g/n [105b:e040]
	Kernel driver in use: bcma-pci-bridge
john@john-Aspire-5560:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1bcf:288a Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-Aspire-5560:~$ iwconfig
lo        no wireless extensions.


enp1s0f0  no wireless extensions.


john@john-Aspire-5560:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
john@john-Aspire-5560:~$ lsmod
Module                  Size  Used by
b43                   417792  0
mac80211              737280  1 b43
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43
snd_hda_codec_realtek    86016  1
snd_hda_codec_hdmi     53248  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
kvm_amd                65536  0
snd_hwdep              16384  1 snd_hda_codec
kvm                   536576  1 kvm_amd
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0
input_leds             16384  0
irqbypass              16384  1 kvm
bcma                   53248  1 b43
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
k10temp                16384  0
snd                    81920  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
i2c_piix4              24576  0
autofs4                40960  2
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  4 usbhid,hid_logitech_dj,hid_logitech_hidpp
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  2
psmouse               126976  0
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
syscopyarea            16384  1 drm_kms_helper
sdhci_pci              28672  0
sdhci                  45056  1 sdhci_pci
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
tg3                   163840  0
fb_sys_fops            16384  1 drm_kms_helper
ptp                    20480  1 tg3
drm                   360448  5 ttm,drm_kms_helper,radeon
pps_core               20480  1 ptp
ahci                   36864  2
libahci                32768  1 ahci
wmi                    20480  1 acer_wmi
fjes                   28672  0
video                  40960  1 acer_wmi
john@john-Aspire-5560:~$ ^C



```

---

### Post by wildmanne39 on 2016-09-16
You have the wrong driver installed for your wireless please do the following:

Your Broadcom 14e4:4358 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now we install the deb files. Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
Your wireless should know work, it would be a lot easier with an internet connection but if you can not get online this will have to do.
Thanks

---

### Post by centipede2 on 2016-09-16
> **Wild Man said:**
> You have the wrong driver installed for your wireless please do the following:

Your Broadcom 14e4:4358 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now we install the deb files. Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
Your wireless should know work, it would be a lot easier with an internet connection but if you can not get online this will have to do.
Thanks

All that's in "Pool" are two folders, "main" and "universe". "universe" has a folder called "c", main has a few folders titled "g" "l" "m" "s" and "u".

EDIT: So "main" doesn't have "d", and "pool" doesn't have "restricted".

---

### Post by wildmanne39 on 2016-09-16
The driver is right where the directions says it is on my ubuntu 16.04, I extracted it and I tried to upload it for you but the forum will not let me. Did you just insert the cd or liveusb you did not boot from it right?

---

### Post by centipede2 on 2016-09-16
> **Wild Man said:**
> The driver is right where the directions says it is on my ubuntu 16.04, I extracted it and I tried to upload it for you but the forum will not let me. Did you just insert the cd or liveusb you did not boot from it right?

I'm looking in the USB installer (while in Lubuntu proper, not a live session). Perhaps those files exist in the Ubuntu USB installer, and I can just make one of those real quick and grab the files from there? Or are they in the Ubuntu installer ISO and I can copy them without having to spend 2 minutes creating the entire installer?

---

### Post by wildmanne39 on 2016-09-16
If you have a copy of ubuntu or lubuntu downloaded in your downloads file you can click on it and follow the directions to the file then extract it to your desktop then install it that way. I am using ubuntu mate 16.04 and the file is there it should be the same for lubuntu and ubuntu.

---

### Post by centipede2 on 2016-09-19
> **Wild Man said:**
> You have the wrong driver installed for your wireless please do the following:

Your Broadcom 14e4:4358 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and navigate to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now we install the deb files. Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
Your wireless should know work, it would be a lot easier with an internet connection but if you can not get online this will have to do.
Thanks

Thanks for your help. This is on a work computer so I wasn't able to mess with it over the weekend.

Just to clarify, are you saying that I should install the files, and then run those commands? Or are you saying that I should install those files BY running the commands?

EDIT: I did both, and neither worked. Once either file is on the desktop, double clicking them shows red text about missing or broken dependencies. Running the commands you mentioned seemed to return the same error, though in a lot more complex language. Now when I double click either file I get a popup warning me about broken dependencies; In Synaptec, the broken packages are listed as: bcmwl-kernel-source and dkms.

---

### Post by wildmanne39 on 2016-09-19
You have to find the files then drag them to your desktop the you install the files be running the commands one at a time and just copy and paste for accuracy.

If you have a cell phone you might be able to plug it into a usb port and that is called tethering, I have done that and it gave me fast internet connection and I used that to install wifi drivers that would be easier if  you can not find those files.

---

### Post by centipede2 on 2016-09-19
What I meant to say is that I've done all of that. But I get errors, the ones I described above about broken dependencies.

I got the files from the Ubuntu installer. The Lubuntu installer was lacking them.

---

### Post by wildmanne39 on 2016-09-19
Please post the errors.

---

### Post by centipede2 on 2016-09-19
I did. Initially double clicking them would open up the installer, but with red text that warned of broken or missing dependencies. Then I ran the commands, which returned very verbose versions of seemingly the same problem: broken or missing dependencies. Now when I open the installers, I get an actual popup error that warns of broken or missing dependencies.

In frustration I've simply tried Ubuntu proper. Wifi works on the USB live test, so I'm going through the proper installation right now. We'll see how it turns out. I was hoping to use Lubuntu though because it's supposed to be lightweight and I want as much resources as possible available to this old laptop since I'm hoping to use it for a pretty heavy internet-based Electronic Medical Records chart documenting system.

---

### Post by wildmanne39 on 2016-09-19
If you still have problems post back.
Thanks

---

