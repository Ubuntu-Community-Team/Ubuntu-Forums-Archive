---
title: "Bluetooth enabling on ASUS X500L"
date: 2022-10-02
forum: Networking &amp; Wireless
---

### Post by manny-velgara on 2022-10-02
Recently poured thru the forums for help in enabling my Bluetooth after installing ver 22.0.0.1 on my ASUS X500L. Found this thread [[https://ubuntuforums.org/showthread.php?t=2399393&referrerid=2173534]](https://ubuntuforums.org/showthread.php?t=2399393&referrerid=2173534]) and it seemed to work up until executing the third line "sudo apt install dkms rtbth-dkms blueman" 
sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install dkms rtbth-dkms blueman
sudo modprobe -v rtbth

It returns with this:
manny@manny-X550LN:~$ sudo apt install dkms rtbth-dkms blueman
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
dkms is already the newest version (2.8.7-2ubuntu2).
blueman is already the newest version (2.2.4-1).
rtbth-dkms is already the newest version (3.9.7~git20220502-1~jammy1).
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi i965-va-driver intel-media-va-driver libaacs0 libaom3 libass9 libavcodec58
  libavformat58 libavutil56 libbdplus0 libblas3 libbluray2 libbs2b0 libchromaprint1 libcodec2-1.0 libdav1d5 libflite1 libgme0
  libgsm1 libgstreamer-plugins-bad1.0-0 libigdgmm12 liblilv-0-0 libmfx1 libmysofa1 libnorm1 libnvidia-cfg1-515
  libnvidia-common-515 libnvidia-decode-515 libnvidia-egl-wayland1 libnvidia-encode-515 libnvidia-extra-515 libnvidia-fbc1-515
  libnvidia-gl-515 libopenmpt0 libpgm-5.3-0 libpostproc55 librabbitmq4 librubberband2 libserd-0-0 libshine3 libsnappy1v5
  libsord-0-0 libsratom-0-0 libsrt1.4-gnutls libssh-gcrypt-4 libswresample3 libswscale5 libudfread0 libva-drm2 libva-wayland2
  libva-x11-2 libva2 libvdpau1 libvidstab1.1 libx265-199 libxnvctrl0 libxvidcore4 libzimg2 libzmq5 libzvbi-common libzvbi0
  mesa-va-drivers mesa-vdpau-drivers nvidia-compute-utils-515 nvidia-kernel-source-515 nvidia-settings nvidia-utils-515
  pkg-config pocketsphinx-en-us screen-resolution-extra va-driver-all vdpau-driver-all xserver-xorg-video-nvidia-515
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up ar9462-dkms (2.0) ...
Removing old ar9462-2.0 DKMS files...
Deleting module ar9462-2.0 completely from the DKMS tree.
Loading new ar9462-2.0 DKMS files...
Building for 5.15.0-48-generic
Building for architecture x86_64
Building initial module for 5.15.0-48-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/ar9462-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-48-generic (x86_64)
Consult /var/lib/dkms/ar9462/2.0/build/make.log for more information.
dpkg: error processing package ar9462-dkms (--configure):
 installed ar9462-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 ar9462-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)


Not sure what to do next. Any help would be appreciated.

---

### Post by jeremy31 on 2022-10-02
Please post results from terminal for ```
lsusb; lspci -nnk | grep -iA3 net; dkms status
```

---

### Post by manny-velgara on 2022-10-02
Bus 001 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04f2:b40a Chicony Electronics Co., Ltd USB2.0 HD UVC WebCam
Bus 002 Device 004: ID 03f0:094a HP, Inc Optical Mouse [672662-001]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. RT3290 Wireless 802.11n 1T/1R PCIe [105b:e055]
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci
ar9462/2.0: added
rtbth/3.9.7, 5.15.0-48-generic, x86_64: installed

---

### Post by jeremy31 on 2022-10-03
```
sudo dkms uninstall ar9462/2.0
```
Then see if it still errors

---

### Post by manny-velgara on 2022-10-09
Here's the response:

Error! The module ar9462 2.0 is not currently installed.
This module is not currently ACTIVE for kernel 5.15.0-48-generic (x86_64).

---

### Post by jeremy31 on 2022-10-13
```
sudo dkms remove ar9462/2.0
```
Check ```
lsmod | grep rtbth
```

---

### Post by manny-velgara on 2022-10-19
> **jeremy31 said:**
> ```
sudo dkms remove ar9462/2.0
```
Check ```
lsmod | grep rtbth
```

Entered the above and nothing. The prompt shows nothing.

---

### Post by jeremy31 on 2022-10-23
Try ```
sudo modprobe rtbth
```

---

### Post by Yellow Pasque on 2022-10-24
> Consult /var/lib/dkms/ar9462/2.0/build/make.log for more information.

Could you share the contents of this file? (Please use code tags:  [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code) )

---

