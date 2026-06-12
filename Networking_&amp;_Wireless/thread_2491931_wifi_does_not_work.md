---
title: "wifi does not work"
date: 2023-10-25
forum: Networking &amp; Wireless
---

### Post by d3vestator on 2023-10-25
after getting my nividia drivers and other issues resolved i noticed that i have no wifi or wifi driver available because i can not see the wifi button
[https://paste.ubuntu.com/p/4mpybdHFqj/](https://paste.ubuntu.com/p/4mpybdHFqj/) before i had wifi issues

---

### Post by MAFoElffen on 2023-10-26
From the information from your 'system-info' report, please post the results of this within CODE Tags:
```

lsusb -v -s 13d3:3563
sudo lspci -nnv | grep -A11 -i network | grep -Ei 'subsystem|kernel'

```
I'm thinking it just may come up as a Realtek 'rtl8821ce'... We'll see.

---

### Post by MAFoElffen on 2023-10-26
In fact... I'm fairly sure that is a good guess on that... (just based on the model shown)  I'm going to bed soon, so I'll post the instruction for that for you. 

If that is there, then do this. Open a terminal.
```

cd ~/Downloads
sudo apt download rtl8821ce-dkms

```
The file that will download from Jammy is: rtl8821ce-dkms_5.5.2.1-0ubuntu11~0.22.04.1_all.deb

Copy that file onto a USB flash drive and get it to your Vivo laptop. Copy it into your Download directory. Open a terminal session on it.
```

cd ~/Downloads
sudo dpkg -i rtl8821ce-dkms_5.5.2.1-0ubuntu11~0.22.04.1_all.deb
sudo reboot

```
Test it.

Good night. Will check this in the morning.

---

### Post by d3vestator on 2023-10-26
the network controller is a mediatek MT7921, it says advanced error reporting
i am communicating on my pc, so I'm not copying the commands

---

### Post by MAFoElffen on 2023-10-26
Okay... 

The driver for that has been in the Linux kernel since 5.12. You are on Linux Kernel 6.2.0-32-generic. It should be there. Nevermind, found something. 

I found this: [https://askubuntu.com/questions/1444909/wifi-not-working-unavailable-22-10-mediatek-mt7921](https://askubuntu.com/questions/1444909/wifi-not-working-unavailable-22-10-mediatek-mt7921)
- Look at answer #1 Follow those directions and see if it works for you.

---

### Post by d3vestator on 2023-10-26
so i went to the page you offered, and after inputting the commands they suggested, my network interface card did not show up, so i did more research on a ubuntu help page about troubleshooting wifi network interface card, and im pretty i have no drivers for it because they said output lshw -C network and check if there is drivers installed on the right side of configuration: which mine only says latency=0.

however i went to the MediaTek page itself to see if there are Linux mt7921 drivers available, but wasn't able to find any

---

### Post by MAFoElffen on 2023-10-26
You never did show me the output of any of those commands... So I do not know. I understand that it has no internet, so that would require you to take photos of that and attach them to a post as an attachment.

Question though... When you boot that laptop with a LiveUSB, does it then have working WiFi?

---

### Post by d3vestator on 2023-10-26
it does

```

buntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: MT7921 802.11ax PCI Express Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 90:e8:68:d1:e7:5f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=mt7921e driverversion=5.15.0-43-generic firmware=____010000-20220209150915 ip=10.0.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: iomemory:ff0-fef iomemory:ff0-fef iomemory:ff0-fef irq:82 memory:ff20300000-ff203fffff memory:ff20400000-ff20403fff memory:ff20404000-ff20404fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


```
can i somehow take this driver put it on a usb and download it?

---

### Post by MAFoElffen on 2023-10-26
This may sounds too simple, but two people with this Wifi Card in ASUS laptops say this worked for them:

Start laptop and let boot fully. Hold down the power button, and keep holding it down for over a full minute. left off the power button. Press power button to start. Check. 

For some reason, they said that reset both their wifi card and bluetooth, and that after that, it started working. Couldn't hurt to try that right?

---

### Post by d3vestator on 2023-10-26
unfortunately, that simple trick did not work

---

### Post by MAFoElffen on 2023-10-26
It was worth a try. Which driver if any does it say it is using on it's own? Or is it unclaimed?

---

### Post by d3vestator on 2023-10-26
the driver is posted on #8 thread right side of configuration
driver version is 5.15, and i dont what you mean by unclaimed
what i also notice between the removeable usb and the computer version is that the removeable version has a network interface name of wlp2s0 which i remember, however my computer version doesn't have a name

---

### Post by MAFoElffen on 2023-10-26
> **d3vestator said:**
> the driver is posted on #8 thread right side of configuration
driver version is 5.15, and i dont what you mean by unclaimed
what i also notice between the removeable usb and the computer version is that the removeable version has a network interface name of wlp2s0 which i remember, however my computer version doesn't have a name
No. You misunderstood what I was saying. In Post #8, that is what it shows as when it was booted from the LiveUSB and working...

For comparison, run the same command on it when it is boot on it's on, when it is not working. Does it say another driver? Or no driver at all?

Yes post #8 says it is working with the internal kernel drivers from Linux kernel version 5.15.0-43-generic... But your installed system has kernel 6.2.0-32

---

### Post by MAFoElffen on 2023-10-26
Okay. I need a bit more info. This one ran from being booted from a LiveUSB, so you can cut and paste the output into a post...
```

sudo lspci -nnk | grep -A3 -Ei 'Network controller'

```
Do the same booted on it's own and copy down what it says to repost, so we have a comparison of the two.

---

### Post by d3vestator on 2023-10-26
live usb
```

ubuntu@ubuntu:~$ sudo lspci -nnk | grep -A3 -Ei 'Network controller'
02:00.0 Network controller [0280]: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter [14c3:7961]
    Subsystem: AzureWave Device [1a3b:4680]
    Kernel driver in use: mt7921e
    Kernel modules: mt7921e


```

Computer version
```

ubuntu@ubuntu:~$ sudo lspci -nnk | grep -A3 -Ei 'Network controller'
02:00.0 Network controller [0280]: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter [14c3:7961]
    Subsystem: AzureWave Device [1a3b:4680]
03:00:0 Non-Volatile memory controller [0108]: Intel corpporation Device [8086:flaa] (rev 03)
Subsystem: Intel Corporation Device [8086:390f]

```

---

### Post by MAFoElffen on 2023-10-26
Okay.

Booted on it's own, please try this.
```

sudo rmmod mt76   # I do not care if it says it is not there. We just want to ensure it is not loaded
sudo rmmod mt7601uigbvf    # I do not care if it says it is not there. We just want to ensure it is not loaded
sudo modprobe mt7921e
sudo nmcli networking off
sudo nmcli networking on
sudo lspci -nnk | grep -A3 -Ei 'Network controller'

```
Check the output of the 'lspic' command and see if the output adds the last two lines below "Subsystem: ..." as
```

    Kernel driver in use: mt7921e
    Kernel modules: mt7921e

```
To make sure it is loading...

---

### Post by MAFoElffen on 2023-10-27
No feedback yet?

If they are there or not... The module is provide by the binaries from package linux-firmware, 

This is what I see in the notes for the firmware for those:
```

BT_RAM_CODE_MT7961_1_2_hdr.bin     | linux-firmware: update firmware for mediatek bluetooth chip (MT7921)
WIFI_MT7961_patch_mcu_1_2_hdr.bin  | linux-firmware: update firmware for MT7921 WiFi device
WIFI_RAM_CODE_MT7961_1.bin         | linux-firmware: update firmware for MT7921 WiFi device

```
and should be found on the system by doing
```

ls /usr/lib/firmware/mediatek/*MT7961*.bin

```
My laptop is Linux kernel 6.2.0-33-generic, and on it I see these firmware binaries:
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ ls /usr/lib/firmware/mediatek/*MT7961*.bin
/usr/lib/firmware/mediatek/BT_RAM_CODE_MT7961_1_2_hdr.bin
/usr/lib/firmware/mediatek/WIFI_MT7961_patch_mcu_1_2_hdr.bin
/usr/lib/firmware/mediatek/WIFI_RAM_CODE_MT7961_1.bin

```
Please confirm yours is similar... When the laptop is booted on it's own (from the 6.2.0 kernel)

---

### Post by d3vestator on 2023-10-27
this is the wrong picture. 

```


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292958&stc=1[/IMG]

```

---

### Post by d3vestator on 2023-10-27
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292959&stc=1[/IMG]


this was for the first question

---

### Post by d3vestator on 2023-10-27
and for your second response, mine is similar

---

### Post by MAFoElffen on 2023-10-27
Run these two commands (indicated in red) and check the output (shown on my laptop to show you what it should look like):
```

mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ [COLOR=#ff0000]modinfo mt7921e[/COLOR]
filename:       /lib/modules/6.2.0-33-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko
license:        Dual BSD/GPL
author:         Lorenzo Bianconi <lorenzo@kernel.org>
author:         Sean Wang <sean.wang@mediatek.com>
firmware:       mediatek/WIFI_MT7922_patch_mcu_1_1_hdr.bin
firmware:       mediatek/WIFI_RAM_CODE_MT7922_1.bin
firmware:       mediatek/WIFI_MT7961_patch_mcu_1_2_hdr.bin
firmware:       mediatek/WIFI_RAM_CODE_MT7961_1.bin
srcversion:     E328FAB2A274BDA6C4B7CAB
alias:          pci:v000014C3d00000616sv*sd*bc*sc*i*
alias:          pci:v000014C3d00000608sv*sd*bc*sc*i*
alias:          pci:v000014C3d00007922sv*sd*bc*sc*i*
alias:          pci:v000014C3d00007961sv*sd*bc*sc*i*
depends:        mt76-connac-lib,mt76,mt7921-common
retpoline:      Y
intree:         Y
name:           mt7921e
vermagic:       6.2.0-33-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        3A:94:F3:77:AE:60:32:06:49:35:7B:8D:A9:DE:EB:5F:7F:E6:9E:B4
sig_hashalgo:   sha512
signature:      A1:A2:29:12:70:5B:DD:B5:E5:8A:5D:A7:60:A7:D9:98:78:83:AA:BC:
        4D:37:19:22:59:35:D4:06:CB:A1:02:86:E8:D2:59:B7:58:C5:4F:B9:
        19:CB:61:59:BA:B9:FA:9D:5D:9E:D9:7A:B6:0A:27:C7:72:60:DB:76:
        37:81:53:2D:39:61:66:4F:AD:19:C6:31:02:F1:74:AA:FE:A5:BB:39:
        F7:A3:91:D1:0C:57:A0:D2:BD:B3:9E:83:6A:F5:23:E2:36:68:16:D4:
        97:BF:0D:DB:F9:B3:C4:76:88:30:9E:40:BF:56:B3:D6:DE:0C:7A:75:
        6C:D2:9A:8F:89:EF:F4:38:A1:03:6E:D3:14:B9:30:FE:EA:94:DE:E6:
        BE:47:35:36:DD:A1:A4:1E:1A:14:93:4A:31:0B:34:72:34:3F:97:87:
        1F:51:5A:37:46:EF:28:E1:D1:98:5A:AF:7A:5C:C0:53:02:F8:33:86:
        71:36:4E:05:D3:B1:70:2F:20:C6:33:47:E5:B6:E4:60:00:58:C1:C4:
        CE:55:44:F1:9C:28:3B:3A:0E:C9:37:C4:83:92:CA:61:ED:5D:85:60:
        24:76:BB:22:E8:5E:47:BB:AA:5A:67:DC:0F:20:D3:75:61:A0:A3:6F:
        7D:B1:3E:3E:54:E0:AA:DA:0B:7E:9D:A2:6E:96:6E:96:48:D7:2A:92:
        10:2F:43:41:F6:C0:4B:B9:AC:5F:42:E2:12:04:2B:B9:6F:E6:80:A1:
        35:0C:5D:45:E1:BB:17:A1:97:C8:BD:80:AD:76:63:29:C7:59:4B:ED:
        FA:BE:F6:1B:D2:94:60:C7:8F:09:51:F8:FC:2D:AD:3D:DF:C7:A2:3C:
        21:3A:E8:DA:AB:7B:B7:1D:E2:88:08:41:F3:06:98:F2:39:19:CB:DD:
        1A:18:AC:67:44:9A:13:CD:DE:79:A1:B0:7D:64:2C:FD:EA:D7:46:5E:
        EF:4F:ED:11:F0:EC:5F:13:DF:AE:9D:E3:82:22:04:FE:25:57:BE:76:
        E5:B9:4C:BF:B2:98:3A:6A:BC:7E:CB:CE:02:17:BF:37:15:D5:08:64:
        97:0B:5B:28:CE:14:A1:60:8E:61:4A:50:2F:B4:C7:28:56:CC:CC:62:
        4A:70:E3:7C:67:83:5C:D9:F9:7E:EF:5F:E7:F4:62:3D:65:5C:D3:A0:
        A8:80:C4:9A:73:F7:B9:26:3C:E1:6A:11:92:B9:A2:52:FD:F7:96:75:
        D9:27:BE:89:11:7F:8E:B0:6E:B6:77:86:BF:2A:B2:58:74:8B:9F:9A:
        1C:04:97:4F:CC:D3:49:57:BA:10:68:F0:20:D4:A6:A7:70:47:9B:0D:
        EF:87:04:9A:6F:FF:F6:E4:4D:3E:4D:36
parm:           disable_aspm:disable PCI ASPM support (bool)

mafoelffen@Mikes-ThinkPad-T520:~/Downloads$ [COLOR=#ff0000]ls -l /lib/modules/6.2.0-33-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko[/COLOR]
-rw-r--r-- 1 root root 111177 Sep  7 00:11 /lib/modules/6.2.0-33-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko

```

---

### Post by d3vestator on 2023-10-27
i get an error, so im unsure if i am in the wrong directory. should i be in my home directory? or /urb/lib/firmware/MediaTek directory?

---

### Post by MAFoElffen on 2023-10-27
Neither. It does matter where you are to run those. Here are the commands again, with very slight changes:
```

sudo modinfo mt7921e
ls -lah /lib/modules/*-generic/kernel/drivers/net/wireless/mediatek/*/*/mt7921e.ko

```
I know that second one is still going to be very hard to manually re-type without errors, but we are looking for that driver, which should have been built when the kernel installed. 

If you have too much trouble typing that, then a short-cut might be to do
```

find /lib/modules/*-generic -name mt7921e.ko

```

---

### Post by d3vestator on 2023-10-27
so sudo modinmt7921e shows error
but the ls -l /lib/modules on lib/modules/????/????? show 

[CODE]
-rw-r--r-- 1 root root 109K AUG 16 04:42 /lib/modules/6.2.0-31-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko

-rw-r--r-- 1 root root 109K AUG 16 04:38 /lib/modules/6.2.0-32-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko

---

### Post by MAFoElffen on 2023-10-27
So it looks like if, at the Grub2 Menu > Advanced Options > ... If you booted from an Ubuntu menu item with kernels 6.2.0-31-generic or 6.2.0-32-generic, that your wifi would work.

Could you please test that?

If it boots and has working wifi again, then do
```

sudo apt update
sudo apt install --reinstall linux-image-generic linux-image-generic-hwe-22.04 linux-image-6.2.0-33-generic

```

---

### Post by d3vestator on 2023-10-27
for some reason i cannot connect to any of the ubuntu wifi network, i am able to choose my network, but it never connects, and i know the password is correct
the 31 and 32 version dont even shutdown properly

---

### Post by MAFoElffen on 2023-10-27
Let's open another doorway into it... You are going to want to boot from your Installer LiveUSB to do this... Do "Try". Connect to your WiFi network.

Start a browser to get back to this post... Start a terminal session.
```

cd ~/Downloads
sudo su

```

Copy everything within this code block:
```

cat <<'EOF' >> ./GetMeIn
#!/bin/bash
# MAFoElffen,<mafoelffen@ubuntu.com,2023.10.27
# filename: GetMeIn
# purpose: Custom chroot script for D3vastator
#

mount /dev/nvme0n1p6 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
EOF

```
Paste it into the terminal session, then hit enter. That will create that script in the downloads directory. Then do
```

chmod +x ./GetMeIn
./GetMeIn

```
You should be chrooted into your system... with a working network from the Live Session...

Then do
```

mount -a
apt update
apt install --reinstall linux-image-generic linux-image-generic-hwe-22.04 linux-image-6.2.0-33-generic
apt install --reinstall network-manager
apt remove --purge nvidia*
apt install nvidia-driver-470
exit
sudo umount /mnt

```
Shutdown. Boot up to test it.

---

### Post by d3vestator on 2023-10-28
last part of the code
is that still in the live session? no right?

---

### Post by MAFoElffen on 2023-10-28
Yes. 

That will be from booted into the Live Environment, because after running that script... after if it chroot's into your installed system, what you then enter will finish the mounts in the fstab, and then each other command that follows that can work to help reinstall things within it, while using the working wifi from the Live Environment.

---

### Post by d3vestator on 2023-10-28
```


ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ cat <<'EOF' >> ~/Downloads/GetMeIn
#!/bin/bash
# MAFoElffen,<mafoelffen@ubuntu.com,2023.10.27
# filename: GetMeIn
# purpose: Custom chroot script for D3vastator
#

mount /dev/nvme0n1p6 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
EOF
ubuntu@ubuntu:~/Downloads$ sudo chmod +x ~/Downloads/GetMeIn
~/Downloads/GetMeIn
mount: /mnt: must be superuser to use mount.
mount: /mnt/dev: mount point does not exist.
mount: /mnt/proc: mount point does not exist.
mount: /mnt/sys: mount point does not exist.
mount: /mnt/run: mount point does not exist.
chroot: cannot change root directory to '/mnt': Operation not permitted
ubuntu@ubuntu:~/Downloads$ sudo chmod +x ~/Downloads/GetMeIn
ubuntu@ubuntu:~/Downloads$ mount -a
ubuntu@ubuntu:~/Downloads$ sudo apt update
Ign:1 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy InRelease
Hit:2 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy Release
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:5 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Get:6 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [896 kB]
Get:7 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:8 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [180 kB]
Get:9 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [43.0 kB]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/main DEP-11 48x48 Icons [16.9 kB]
Get:11 http://security.ubuntu.com/ubuntu jammy-security/main DEP-11 64x64 Icons [26.5 kB]
Get:12 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [11.4 kB]
Get:13 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [1,016 kB]
Get:14 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [164 kB]
Get:15 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 c-n-f Metadata [536 B]
Get:16 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages [1,395 kB]   
Get:17 http://archive.ubuntu.com/ubuntu jammy/restricted amd64 Packages [129 kB]
Get:18 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [1,104 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [240 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/main DEP-11 48x48 Icons [36.1 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy-updates/main DEP-11 64x64 Icons [55.1 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [16.1 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [1,036 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [167 kB]
Get:26 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [536 B]
Fetched 6,864 kB in 3s (2,019 kB/s)      
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
556 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ubuntu:~/Downloads$ sudo apt install --reinstall linux-image-generic linux-image-6.2.0-33-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-image-5.15.0-87-generic linux-modules-5.15.0-87-generic
  linux-modules-6.2.0-33-generic linux-modules-extra-5.15.0-87-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools
  linux-headers-5.15.0-87-generic linux-doc | linux-hwe-6.2-source-6.2.0
  linux-hwe-6.2-tools linux-headers-6.2.0-33-generic
  linux-modules-extra-6.2.0-33-generic
The following NEW packages will be installed:
  linux-image-5.15.0-87-generic linux-image-6.2.0-33-generic
  linux-image-generic linux-modules-5.15.0-87-generic
  linux-modules-6.2.0-33-generic linux-modules-extra-5.15.0-87-generic
0 upgraded, 6 newly installed, 0 to remove and 556 not upgraded.
Need to get 137 MB of archives.
After this operation, 635 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-modules-5.15.0-87-generic amd64 5.15.0-87.97 [22.4 MB]
Get:2 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-image-5.15.0-87-generic amd64 5.15.0-87.97 [11.5 MB]
Get:3 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-modules-6.2.0-33-generic amd64 6.2.0-33.33~22.04.1 [25.6 MB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-image-6.2.0-33-generic amd64 6.2.0-33.33~22.04.1 [13.6 MB]
Get:5 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-modules-extra-5.15.0-87-generic amd64 5.15.0-87.97 [64.0 MB]
Get:6 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-image-generic amd64 5.15.0.87.84 [2,482 B]
Fetched 137 MB in 9s (15.4 MB/s)                                               
Selecting previously unselected package linux-modules-5.15.0-87-generic.
(Reading database ... 206909 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.15.0-87-generic_5.15.0-87.97_amd64.deb
 ...
Unpacking linux-modules-5.15.0-87-generic (5.15.0-87.97) ...
Selecting previously unselected package linux-image-5.15.0-87-generic.
Preparing to unpack .../1-linux-image-5.15.0-87-generic_5.15.0-87.97_amd64.deb .
..
Unpacking linux-image-5.15.0-87-generic (5.15.0-87.97) ...
Selecting previously unselected package linux-modules-6.2.0-33-generic.
Preparing to unpack .../2-linux-modules-6.2.0-33-generic_6.2.0-33.33~22.04.1_amd
64.deb ...
Unpacking linux-modules-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Selecting previously unselected package linux-image-6.2.0-33-generic.
Preparing to unpack .../3-linux-image-6.2.0-33-generic_6.2.0-33.33~22.04.1_amd64
.deb ...
Unpacking linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Selecting previously unselected package linux-modules-extra-5.15.0-87-generic.
Preparing to unpack .../4-linux-modules-extra-5.15.0-87-generic_5.15.0-87.97_amd
64.deb ...
Unpacking linux-modules-extra-5.15.0-87-generic (5.15.0-87.97) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../5-linux-image-generic_5.15.0.87.84_amd64.deb ...
Unpacking linux-image-generic (5.15.0.87.84) ...
Setting up linux-modules-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Setting up linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-87-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-6.2.0-33-generic
I: /boot/initrd.img is now a symlink to initrd.img-6.2.0-33-generic
Setting up linux-image-5.15.0-87-generic (5.15.0-87.97) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-6.2.0-33-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-87-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-87-generic
Setting up linux-modules-extra-5.15.0-87-generic (5.15.0-87.97) ...
Setting up linux-image-generic (5.15.0.87.84) ...
Setting up linux-modules-5.15.0-87-generic (5.15.0-87.97) ...
Processing triggers for linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs is disabled since running on read-only media
Processing triggers for linux-image-5.15.0-87-generic (5.15.0-87.97) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs is disabled since running on read-only media
ubuntu@ubuntu:~/Downloads$ sudo apt install --reinstall network-manager
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 556 not upgraded.
Need to get 2,203 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 network-manager amd64 1.36.6-0ubuntu2 [2,203 kB]
Fetched 2,203 kB in 2s (1,373 kB/s)        
(Reading database ... 215449 files and directories currently installed.)
Preparing to unpack .../network-manager_1.36.6-0ubuntu2_amd64.deb ...
Unpacking network-manager (1.36.6-0ubuntu2) over (1.36.6-0ubuntu2) ...
Setting up network-manager (1.36.6-0ubuntu2) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for man-db (2.10.2-1) ...
ubuntu@ubuntu:~/Downloads$ ^C
ubuntu@ubuntu:~/Downloads$ ^C
ubuntu@ubuntu:~/Downloads$ ^C
ubuntu@ubuntu:~/Downloads$ 


```

---

### Post by d3vestator on 2023-10-28
i cannot get past the install drive 470 without errors and black screen
```

failed to set up autoamount arbitrary executable file fromats file system automount point
failed to start ubuntu live cd installer
failed to start snap daemon and there was another one that disappeared

```

---

### Post by MAFoElffen on 2023-10-29
> **d3vestator said:**
> i cannot get past the install drive 470 without errors and black screen
```

failed to set up autoamount arbitrary executable file fromats file system automount point
failed to start ubuntu live cd installer
failed to start snap daemon and there was another one that disappeared

```

You were not chrooted into the installed system. You were still in the Live environment before any chroot...  

Shut down. 

Boot up fresh from the LiveUSB & use "Try"...

Do the steps over again, in order.

---

### Post by d3vestator on 2023-10-29
i think i missing a step or a misunderstanding in communication i dont seem to understand,
so this code creates a fie named getmein

```

cat <<'EOF' >> ~/Downloads/GetMeIn
#!/bin/bash
# MAFoElffen,<mafoelffen@ubuntu.com,2023.10.27
# filename: GetMeIn
# purpose: Custom chroot script for D3vastator
#

mount /dev/nvme0n1p6 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env bash --login
EOF


```
after copy pasting the command, i press enter because the file mouse clicker is still blinking, then i change the permission[u+x or +x], so that i can run it as executable. am i suppose run ./GetMeIn after? w. Should it automatically chroot me into my machine?.

---

### Post by MAFoElffen on 2023-10-29
Remember before executing that script, to make sure you are connected to your wifi.

Yes. That will execute that script to do all those commands for you. You will notice the prompt of the command line prompt change to user 'root'.

Then you just continue with the other commands.

---

### Post by MAFoElffen on 2023-10-29
Here is an explanation of the commands there... Use what it in the previous post. This post is just to explain each line to you...
```

cat <<'EOF' >> ~/Downloads/GetMeIn    [COLOR=#ff0000]# read until the next "EOF" marker and echo the whole contents between those markers into a file located at that path.[/COLOR]
#!/bin/bash
# MAFoElffen,<mafoelffen@ubuntu.com,2023.10.27
# filename: GetMeIn
# purpose: Custom chroot script for D3vastator
#

mount /dev/nvme0n1p6 /mnt  [COLOR=#ff0000]# mount the installed system partition noted in your system-info report to /mnt [/COLOR]
mount --make-private --rbind /dev  /mnt/dev [COLOR=#ff0000]# mount the system's /dev directory to /mnt[/COLOR]
mount --make-private --rbind /proc /mnt/proc [COLOR=#ff0000]# mount the system's /proc directory to /mnt[/COLOR]
mount --make-private --rbind /sys  /mnt/sys [COLOR=#ff0000]# mount the system's /sys directory to /mnt[/COLOR]
mount --make-private --rbind /run  /mnt/run [COLOR=#ff0000]# mount the system's /run directory to /mnt[/COLOR]
chroot /mnt /usr/bin/env bash --login [COLOR=#ff0000]# chroot into the system mounted at /mnt, carrying in the $ENVVAR's and start a BASH Shell[/COLOR]
EOF

## Next
chmod +x ~/Downloads/GetMeIn [COLOR=#ff0000]# Add execute permision to the script file to execute[/COLOR]
~/Downloads/GetMeIn [COLOR=#ff0000]# execute the script[/COLOR]

##
mount -a [COLOR=#ff0000]# finish mounting the other pieces of your installed system[/COLOR]
apt update [COLOR=#ff0000]# update the APT cache[/COLOR]
apt install --reinstall linux-image-generic linux-image-generic-hwe-22.04 linux-image-6.2.0-33-generic [COLOR=#ff0000]# reinstall the linux-kernelseries mechanism & the specific kernel version, becaseu for some reason it did not build the module you need for wifi correctly.[/COLOR]
apt install --reinstall network-manager [COLOR=#ff0000]# because there were other errors with Network Manager, so suspected as compromised[/COLOR]
apt remove --purge nvidia* [COLOR=#ff0000]# ensure there are no left-over pieces of your nvidia driver there[/COLOR]
apt install nvidia-driver-470 [COLOR=#ff0000]# Install the driver version that NVidia confirms works with your GPU.[/COLOR]
exit [COLOR=#ff0000]# Exit the chroot[/COLOR]
sudo umount /mnt [COLOR=#ff0000]# unmount the mounts we did, so it closes down it's filesystem gracefully[/COLOR]

```

---

### Post by d3vestator on 2023-10-29
```

buntu@ubuntu:~/Downloads$ sudo ~/Downloads/GetMeIn
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: /mnt/dev: mount point does not exist.
mount: /mnt/proc: mount point does not exist.
mount: /mnt/sys: mount point does not exist.
mount: /mnt/run: mount point does not exist.
chroot: failed to run command &#8216;/usr/bin/env&#8217;: No such file or directory


```
am i still doing something wrong?

---

### Post by MAFoElffen on 2023-10-29
Sorry. Dang. 

I see the problem. I changed/updated that in the original post. I left out a command which changes all of that == Added one line to it at the start of the instructions.

Go back to Post #27, at the start of the instructions, right after you change directories to you Downloads folder, do
```

sudo su

```
That will make you the root user, to do all that with elevated permissions...

---

### Post by d3vestator on 2023-10-29
```

oot@ubuntu:/home/ubuntu/Downloads# ls
GetMeIn
root@ubuntu:/home/ubuntu/Downloads# ~/Downloads/GetMeIn
bash: /root/Downloads/GetMeIn: No such file or directory


```

i cant use sudo su before copying the script or it says no such file or directory

---

### Post by MAFoElffen on 2023-10-29
Okay... Changed Post #27: [https://ubuntuforums.org/showthread.php?t=2491931&p=14163028#post14163028](https://ubuntuforums.org/showthread.php?t=2491931&p=14163028#post14163028)

That should work now.

---

### Post by d3vestator on 2023-10-29
```

ubuntu@ubuntu:~/Downloads$ sudo su
root@ubuntu:/home/ubuntu/Downloads# ./GetMeIn
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: /mnt/dev: mount point does not exist.
mount: /mnt/proc: mount point does not exist.
mount: /mnt/sys: mount point does not exist.
mount: /mnt/run: mount point does not exist.
chroot: failed to run command ‘/usr/bin/env’: No such file or directory
root@ubuntu:/home/ubuntu/Downloads# 


```

---

### Post by MAFoElffen on 2023-10-29
> **d3vestator said:**
> ```

ubuntu@ubuntu:~/Downloads$ sudo su
[COLOR=#ff0000]## >>> There are a bunch of commands that should have happened and been between this where are they?[/COLOR]
root@ubuntu:/home/ubuntu/Downloads# ./GetMeIn
[COLOR=#ff0000]Mount is denied because the NTFS volume is already exclusively opened.
[/COLOR]The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: /mnt/dev: mount point does not exist.
mount: /mnt/proc: mount point does not exist.
mount: /mnt/sys: mount point does not exist.
mount: /mnt/run: mount point does not exist.
chroot: failed to run command &#8216;/usr/bin/env&#8217;: No such file or directory
root@ubuntu:/home/ubuntu/Downloads# 

```
Please show me this, still from the LiveUSB. DO not reboot it until we are through.
```

mount | grep -v -e 'snaps\|/var\|/sys\|/proc\|/run\|/sys\|tempfs\|mqueue\|hugetlbfs\|devpts'
lsblk -e7

```
*** Hoping we can take care of this through completion today... Step-by-step.

---

### Post by d3vestator on 2023-10-29
```


root@ubuntu:/home/ubuntu/Downloads# mount | grep -v -e 'snaps\|/var\|/sys\|/proc\|/run\|/sys\|tempfs\|mqueue\|hugetlbfs\|devpts'
udev on /dev type devtmpfs (rw,nosuid,relatime,size=7822232k,nr_inodes=1955558,mode=755,inode64)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime,errors=continue)
/cow on / type overlay (rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work,xino=off)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime,inode64)
/dev/nvme0n1p6 on /mnt type fuseblk (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)



root@ubuntu:/home/ubuntu/Downloads# lsblk -e7
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    1   7.5G  0 disk 
&#9492;&#9472;sda1        8:1    1   7.5G  0 part /cdrom
nvme0n1     259:0    0 476.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   260M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 243.5G  0 part 
&#9500;&#9472;nvme0n1p4 259:4    0   3.9G  0 part 
&#9500;&#9472;nvme0n1p5 259:5    0   228G  0 part 
&#9500;&#9472;nvme0n1p6 259:6    0   1.1G  0 part /mnt
&#9492;&#9472;nvme0n1p7 259:7    0   200M  0 part 
root@ubuntu:/home/ubuntu/Downloads# 


```

---

### Post by MAFoElffen on 2023-10-29
> **d3vestator said:**
> ```

root@ubuntu:/home/ubuntu/Downloads# mount | grep -v -e 'snaps\|/var\|/sys\|/proc\|/run\|/sys\|tempfs\|mqueue\|hugetlbfs\|devpts'
/dev/nvme0n1p6 on /mnt [COLOR=#ff0000]type fuseblk[/COLOR] (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

```
That is not matching up with what showed up there on your 'system-info' report...

Please do this:
```

umount /mnt

```
Then show this
```

lsblk -e7 -o name,label,size,fstype,type,mountpoint,device

```

---

### Post by jeremy31 on 2023-10-29
Moved to Networking, see the wireless script link in my signature and post results

---

### Post by d3vestator on 2023-10-29
how do i submit a link to the results? because its too long to post?

---

### Post by jeremy31 on 2023-10-29
Do in terminal ```
cat wireless-info.txt|nc termbin.com 9999
```
Post termbin URL from terminal

---

### Post by d3vestator on 2023-10-29
[https://termbin.com/p6v3](https://termbin.com/p6v3)

---

### Post by MAFoElffen on 2023-10-29
@jeremy31, you have mail (PM)

@D3vastator -- That was run from the Installer LiveUSB right? (So jeremy31 knows that that was not from booted from your installed system...) 

His installed is 6.2.0-33. Your wifi-info report was run from 5.14.0-43... [https://ubuntuforums.org/showthread.php?t=2491931&p=14163020#post14163020](https://ubuntuforums.org/showthread.php?t=2491931&p=14163020#post14163020)

---

### Post by jeremy31 on 2023-10-29
First try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo iwconfig wlp2s0 txpower 20
sudo iwconfig wlp2s0 power off
```
Also do ```
sudo apt install --reinstall linux-modules-extra-6.2.0-33-generic
```
Reboot

---

### Post by d3vestator on 2023-10-29
am i suppose to be outputting the commands out of the live environmentthe paste was from a live environment

the network interface card wlp2s0 isn't recognized on my installed system

---

### Post by MAFoElffen on 2023-10-29
He can't do that from the LiveUSB, until he chroots in... then he will have a working wifi connectivity from the Live Environment to do that. Doig that while not, makes no change on what is installed on the system.

Chicken and egg situation.

---

### Post by jeremy31 on 2023-10-29
Can he boot to an older kernel from grub/advanced options and have wifi or USB tether a smart phone?

---

### Post by MAFoElffen on 2023-10-29
> **d3vestator said:**
> am i suppose to be out of the live environment?

No... Lets "combine" what we are both telling you to do...

Form the LiveUSB, you have networking... We need to see which partition is the actual one that your current LiveUSB see's as where Ubuntu is installed, so that you can mount that. and chroot into it, so that you have both an internet connection to install packages, and be connected to the installed system to make changes to it...

That make sense?

---

### Post by MAFoElffen on 2023-10-29
> **jeremy31 said:**
> Can he boot to an older kernel from grub/advanced options and have wifi or USB tether a smart phone?
I asked him to try that. Failed.


When he did that, the module loaded, but... It said he had networking, but threw NM errors and couldn't connect to his local WiFi network... So suspected that piece may be compromised also.

I know, right? LOL

Still need to see this:
```

lsblk -e7 -o name,label,size,fstype,type,mountpoint,device

```

---

### Post by d3vestator on 2023-10-29
i have wifi working on the 6.2.0-32-generic. not sure why it wasn't working before

```

untu@ubuntu:~$ lsblk -e7 -o name,label,size,fstype,type,mountpoint,device
lsblk: unknown column: device


```

---

### Post by jeremy31 on 2023-10-29
> **d3vestator said:**
> i have wifi working on the 6.2.0-32-generic. not sure why it wasn't working before

```

untu@ubuntu:~$ lsblk -e7 -o name,label,size,fstype,type,mountpoint,device
lsblk: unknown column: device


```

Run my commands from [https://ubuntuforums.org/showthread.php?t=2491931&page=2&p=14163348#post14163348](https://ubuntuforums.org/showthread.php?t=2491931&page=2&p=14163348#post14163348) in that kernel

---

### Post by MAFoElffen on 2023-10-29
Yes, while it's still working. Agree.

---

### Post by d3vestator on 2023-10-29
```

buntu@ubuntu:~$ sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
ubuntu@ubuntu:~$ sudo iwconfig wlp2s0 txpower 20
ubuntu@ubuntu:~$ sudo iwconfig wlp2s0 power off
ubuntu@ubuntu:~$ sudo apt install --reinstall linux-modules-extra-6.2.0-33-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package linux-modules-extra-6.2.0-33-generic
E: Couldn't find any package by glob 'linux-modules-extra-6.2.0-33-generic'

```

---

### Post by MAFoElffen on 2023-10-29
Can you try to install those manually?
```

sudo apt install --reinstall linux-image-generic linux-generic-hwe-22.04
sudo apt install --reinstall linux-modules-extra-6.2.0-33-generic linux-modules-extra-6.2.0-33-generic \
    linux-headers-6.2.0-33-generic linux-image-6.2.0-33-generic

```
Because something broke with that process for you on yours.

Tell us how that goes.

---

### Post by MAFoElffen on 2023-10-29
After that, if successful... Then what we are going to look for is
```

find /lib/modules/*-generic -name mt7921e.ko

```
To see if it built the modules...

---

### Post by d3vestator on 2023-10-29
```

ubuntu@ubuntu:~$ find /lib/modules/*-generic -name mt7921e.ko
/lib/modules/5.15.0-43-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko

```

---

### Post by MAFoElffen on 2023-10-29
That is NOT from you installed system is it? I already know that is not. That is from the LiveUSB's Live Environment "try" right?

Remember when I said, you need to be aware of where you are, and if it would make a difference on your installed system?

Let's back up... You said that when you booted your system, without the LiveUSB, and at the Grub2 > Advanced > a boot option that used kernel 6.2.0-32, that that WFi now works and now connects to your local Wifi... Right? 

That is what both jeremy31 assumed happened and where you were, to be able to do those commands.

Where were you booted from when you entered those commands we asked you to do?

---

### Post by d3vestator on 2023-10-29
i havent done any commands on the 6.2.0-32
all of it has been done from the live usb besides the last commands you want me to do on the installed system

---

### Post by MAFoElffen on 2023-10-29
And you have wifi working if booted on 6.2.0-32 on your installed system now right?

If so, do "all" those commands while booted on your installed system, while booted from kernel 6.2.0-32.

That is where you needed to be on your installed system to make changed to it.

---

### Post by d3vestator on 2023-10-29
It is commands jeremy31 wanted me to output?

---

### Post by MAFoElffen on 2023-10-29
These ones:
```

sudo apt update
sudo apt install --reinstall linux-image-generic linux-generic-hwe-22.04
sudo apt install --reinstall linux-modules-extra-6.2.0-33-generic linux-modules-extra-6.2.0-33-generic linux-headers-6.2.0-33-generic linux-image-6.2.0-33-generic
find /lib/modules/*-generic -name mt7921e.ko

```

---

### Post by MAFoElffen on 2023-10-30
Any progress?

---

### Post by d3vestator on 2023-10-30
sorry, i was at school

```

liam@vivobook:~$ sudo apt update
[sudo] password for liam: 
Sorry, try again.
[sudo] password for liam: 
Hit:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease                                    
Hit:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease                                   
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease                  
Hit:5 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease 
Ign:6 https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy InRelease
Hit:7 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu jammy InRelease
Err:8 https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy Release
  404  Not Found [IP: 2620:2d:4000:1::3e 443]
Reading package lists... Done                                  
E: The repository 'https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
liam@vivobook:~$ sudo apt install --reinstall linux-image-generic linux generic-hwe-22.04
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package linux
E: Unable to locate package generic-hwe-22.04
E: Couldn't find any package by glob 'generic-hwe-22.04'
liam@vivobook:~$ sudo apt install --reinstall linux-modules-extra-6.2.0-33-generic linux-modules-extra-6.2.0-33-generic linux-headers-6.2.0-33-generic linux-image-6.2.0-33-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi8:i386 libflashrom1 libftdi1-2 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libicu70:i386 libllvm13 libllvm15:i386 libmd0:i386
  libnvidia-cfg1-535 libnvidia-common-535 libnvidia-compute-535 libnvidia-compute-535:i386
  libnvidia-decode-535 libnvidia-decode-535:i386 libnvidia-egl-wayland1 libnvidia-encode-535
  libnvidia-encode-535:i386 libnvidia-extra-535 libnvidia-fbc1-535 libnvidia-fbc1-535:i386
  libnvidia-gl-535 libnvidia-gl-535:i386 libpciaccess0:i386 libqt5designer5 libqt5help5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libsensors5:i386 libstdc++6:i386 libvdpau1 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386
  libxcb1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0
  libxshmfence1:i386 libxxf86vm1:i386 linux-headers-6.2.0-31-generic linux-hwe-6.2-headers-6.2.0-31
  linux-image-6.2.0-31-generic linux-modules-6.2.0-31-generic linux-modules-extra-6.2.0-31-generic
  mesa-vdpau-drivers pkg-config python3-packaging python3-pyqt5 python3-pyqt5.sip
  screen-resolution-extra vdpau-driver-all xserver-xorg-video-nvidia-535
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-hwe-6.2-headers-6.2.0-33
The following NEW packages will be installed:
  linux-headers-6.2.0-33-generic linux-hwe-6.2-headers-6.2.0-33
  linux-modules-extra-6.2.0-33-generic
0 upgraded, 3 newly installed, 1 reinstalled, 0 to remove and 120 not upgraded.
Need to get 89.9 MB/104 MB of archives.
After this operation, 542 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-hwe-6.2-headers-6.2.0-33 all 6.2.0-33.33~22.04.1 [13.0 MB]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-6.2.0-33-generic amd64 6.2.0-33.33~22.04.1 [3,382 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-modules-extra-6.2.0-33-generic amd64 6.2.0-33.33~22.04.1 [73.6 MB]
Fetched 89.9 MB in 4s (23.5 MB/s)                               
Selecting previously unselected package linux-hwe-6.2-headers-6.2.0-33.
(Reading database ... 221050 files and directories currently installed.)
Preparing to unpack .../linux-hwe-6.2-headers-6.2.0-33_6.2.0-33.33~22.04.1_all.deb ...
Unpacking linux-hwe-6.2-headers-6.2.0-33 (6.2.0-33.33~22.04.1) ...
Selecting previously unselected package linux-headers-6.2.0-33-generic.
Preparing to unpack .../linux-headers-6.2.0-33-generic_6.2.0-33.33~22.04.1_amd64.deb ...
Unpacking linux-headers-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Preparing to unpack .../linux-image-6.2.0-33-generic_6.2.0-33.33~22.04.1_amd64.deb ...
Unpacking linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) over (6.2.0-33.33~22.04.1) ...
Selecting previously unselected package linux-modules-extra-6.2.0-33-generic.
Preparing to unpack .../linux-modules-extra-6.2.0-33-generic_6.2.0-33.33~22.04.1_amd64.deb ...
Unpacking linux-modules-extra-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Setting up linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Setting up linux-modules-extra-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
Setting up linux-hwe-6.2-headers-6.2.0-33 (6.2.0-33.33~22.04.1) ...
Setting up linux-headers-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-33-generic
   ...done.
Processing triggers for linux-image-6.2.0-33-generic (6.2.0-33.33~22.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-33-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.2.0-33-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-33-generic
Found initrd image: /boot/initrd.img-6.2.0-33-generic
Found linux image: /boot/vmlinuz-6.2.0-32-generic
Found initrd image: /boot/initrd.img-6.2.0-32-generic
Found linux image: /boot/vmlinuz-6.2.0-31-generic
Found initrd image: /boot/initrd.img-6.2.0-31-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
liam@vivobook:~$ find /lib/modules/*-generic -name mt7921e.ko
/lib/modules/6.2.0-31-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko
/lib/modules/6.2.0-32-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko
/lib/modules/6.2.0-33-generic/kernel/drivers/net/wireless/mediatek/mt76/mt7921/mt7921e.ko
liam@vivobook:~$ 


```

---

### Post by d3vestator on 2023-10-30
the wifi bluetooth and my touchpad all seem to work in the 6.2.0-33, of course there is another problem
my pc doesent shutoff if i type the shutdown command and i get startup commands again but nothing with a [FAILED] symbol

---

### Post by MAFoElffen on 2023-10-30
Okay, now start up "Software & Updates" > "Other Software" tab... > Uncheck the "https://ppa.launchpadcontent.net/micahflee/ppa/ubuntu" PPA checkbox... apply. exit. That PPA is throwing a "not found" error in your apt results...

Then do:
```

sudo apt update
sudo apt autoremove
sudo apt upgrade

```
Then do this again:
```

find /lib/modules/*-generic -name mt7921e.ko

```
To ensure it successfully built a wifi module for 6.2.0-35, which is the current kernel. I just want to be positive that your updates are building that module for you (on their own) before you mark this as "Solved"...

---

### Post by d3vestator on 2023-10-30
invalid config param 0014[something like that]
for software and updates, i have ppa/yannnuboot jammy main and ppa/mafoelffen/jammy main. is this correct of the ones that should be checked?

---

### Post by MAFoElffen on 2023-10-31
And that is an ampgpu error that they say is just a warning, not an error, with a patch pending, that supposedly, just adjusts the warning level for that message. For the iGPU that you do not even use. You use your NVidia GPU... LOL

Did it apply updates successfully? Is the new wifi module there for your new kernel?

---

### Post by d3vestator on 2023-10-31
My gnu grub doesnt work.

i wanted to install python on my ubuntu system and it worked, however next morning(today) i got up and booted my computer and noticed that it doesnt work, there is no GNU grub, it doesn't give me option to access ubuntu

everything was working fine before i install python
this was the article [https://phoenixnap.com/kb/how-to-install-python-3-ubuntu](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu)
everytime i do something else, i end up breaking it

---

### Post by d3vestator on 2023-10-31
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292987&stc=1[/IMG]

---

### Post by MAFoElffen on 2023-10-31
Did you make a backup of your system before you did that? Restore that backup... (But I know you probably didn't.)

Quit reading old articles on the internet and following outdated information! You installed a version of Python3 that is outdated (3.8). Your system had Python3 bersion  3.10.12 installed, and that is deeply engrained into the system ,were chaging that breaks things big-time. 

If you are going to try something new, please pay attention to the dates things were written. You already had Python3 installed. You could have check the version via
```

python3 --version

```

You know the instructions I gave you to chroot into your system? That is the only other way to be able to fix this problem...

Mark the Wifi problem as solved, and open another thread in the "Installations and Upgrades" to work on this new problem.

LOL. By the time we are through with these self-inflicted problems, you are going to be a Linux Expert! You have already treaded into places most people don't even touch upon.

See you there in the new thread.

---

