---
title: "Lenovo Thinkpad Yoga 2015 (20FY0002US) Wireless Issue"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by Max_Fitton on 2015-12-29
Hello!

I recently got this laptop, and I've been trying since to get the wireless working on Ubuntu. The wireless card is an Intel Dual Band 8260-AC, which doesn't seem to have any Intel-supported drivers. I'm guessing that that's the issue; however, some searches online have revealed people using this same laptop's wireless out of the box with no issue, which leads me to believe I might be missing something.

I'm a fairly new user to Linux, but I have some Unix experience from my last Apple machine. I'm a CS student, so I'm not afraid to get my hands wet in making this work. That said, I've spent a few hours trying to resolve the issue with no avail.

The troubleshooting is made more difficult by this model's lack of an Ethernet port; I need to switch from my Linux partition to my Windows partition whenever I'd like to do anything internet related. If this isn't fixable, I'm willing to just do development work on a virtual machine. That said, I'd really appreciate it if someone could help me figure out what's going on.

Thanks

---

### Post by jeremy31 on 2015-12-29
Post the result of ```
lspci -nnk | grep -iA2 net; uname -a; dmesg | grep iwl; ls /lib/firmware/ | grep iwlwifi; rfkill list all
```

---

### Post by Max_Fitton on 2015-12-29
```
00:1f.6 Ethernet controller [0200]: Intel Corporation Device [8086:1570] (rev 21)	Subsystem: Lenovo Device [17aa:504c]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Device [8086:1130]
06:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1347] (rev a2)
Linux mfitton 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-105-6.ucode
iwlwifi-135-6.ucode
iwlwifi-2000-6.ucode
iwlwifi-2030-6.ucode
iwlwifi-3160-10.ucode
iwlwifi-3160-12.ucode
iwlwifi-3160-7.ucode
iwlwifi-3160-8.ucode
iwlwifi-3160-9.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2a-6.ucode
iwlwifi-6000g2b-6.ucode
iwlwifi-6050-5.ucode
iwlwifi-7260-10.ucode
iwlwifi-7260-12.ucode
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode
iwlwifi-8000C-16.ucode
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

There ya go!

---

### Post by Frogs Hair on 2015-12-29
Moved to *Networking & Wireless*

---

### Post by chili555 on 2015-12-30
The version of the driver *iwlwifi* included in Ubuntu prior to 15.10 doesn't cover your device. I suggest we install a later driver. Please download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/12/18/backports-20151218.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/12/18/backports-20151218.tar.gz) Right click the file and select 'Extract Here.'  Now:

```
cd ~/Desktop/backports-20150923
make clean
make defconfig-iwlwifi
make
sudo make install
```
Reboot. Any improvement?

You have compiled the driver for your currently installed kernel version only. When Update Manager installs a later linux-image, after the required reboot, please recompile:

```
cd ~/Desktop/backports-20150923
make clean
make defconfig-iwlwifi
make
sudo make install
```
Please retain the files and these instructions for that time.

---

### Post by Max_Fitton on 2015-12-30
That fixed it! Thank you so much for your help :)

---

### Post by chili555 on 2015-12-30
Please use thread tools at the top to mark the thread Solved. The searchers will appreciate it.

---

