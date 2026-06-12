---
title: "*-network UNCLAIMED"
date: 2023-02-09
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2023-02-09
I am running Ubuntu 22.04 on a HP lap Top HP 15-dw4047nr.   The lap Top came with windows and the wifi worked after doing a clean install no wifi and  *-network UNCLAIMED.  I can connect with an ethernet cable.

gordon@gordon-HP-Laptop-15-dw4xxx:~$ lshw -c network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eno1
version: 15
serial: 5c:60:ba:ee:e5:c8
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
resources: irq:16 ioport:4000(size=256) memory:50904000-50904fff memory:50900000-50903fff
*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: ioport:3000(size=256) memory:50800000-508fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 

Gordon33

---

### Post by chili555 on 2023-02-09
Please run and post:

```
lspci -nnk | grep 0280 -A3
```

---

### Post by gordon33 on 2023-02-09
Hello Chili55

ordon@gordon-HP-Laptop-15-dw4xxx:~$ lspci -nnk | grep 0280 -A3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b852]
	DeviceName: WLAN
	Subsystem: Hewlett-Packard Company Device [103c:88e3]


Gordon33

---

### Post by chili555 on 2023-02-10
Please do:

```
sudo apt update
sudo apt install git bc build-essential
git clone https://github.com/lwfinger/rtw89.git
cd rtw89
make
sudo make install
sudo modprobe rtw_8852be

```
Your wireless should now be working.

You have built the driver for your current kernel version only. When Update Manager installs a later kernel version, known as linux-image, recompile:

```
cd rtw89
make clean
git pull
make
sudo make install
sudo modprobe rtw_8852be
```Please retain the file and these instructions for that time.

---

### Post by gordon33 on 2023-02-10
hello chili555 

I followed the instructions for the codes.  After that I shut down the lap top and restarted it.  Still no wifi.  below is all the information from the codes:



gordon@gordon-HP-Laptop-15-dw4xxx:~$ sudo apt update
[sudo] password for gordon: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Hit:2 [https://ppa.launchpadcontent.net/kelebek333/drivers/ubuntu](https://ppa.launchpadcontent.net/kelebek333/drivers/ubuntu) jammy InRelease
Hit:3 [https://ppa.launchpadcontent.net/kelebek333/kablosuz/ubuntu](https://ppa.launchpadcontent.net/kelebek333/kablosuz/ubuntu) jammy InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease                      
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
gordon@gordon-HP-Laptop-15-dw4xxx:~$ sudo apt install git bc build-essential
git clone [https://github.com/lwfinger/rtw89.git](https://github.com/lwfinger/rtw89.git)
cd rtw89
make
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
bc is already the newest version (1.07.1-3build1).
bc set to manually installed.
build-essential is already the newest version (12.9ubuntu3).
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi i965-va-driver
  intel-media-va-driver libaacs0 libaom3 libass9 libavcodec58 libavformat58
  libavutil56 libbdplus0 libblas3 libbluray2 libbs2b0 libchromaprint1
  libcodec2-1.0 libdav1d5 libflashrom1 libflite1 libftdi1-2 libgme0 libgsm1
  libgstreamer-plugins-bad1.0-0 libigdgmm12 liblilv-0-0 libllvm13 libmfx1
  libmysofa1 libnorm1 libopenmpt0 libpgm-5.3-0 libpostproc55 librabbitmq4
  librubberband2 libserd-0-0 libshine3 libsnappy1v5 libsord-0-0 libsratom-0-0
  libsrt1.4-gnutls libssh-gcrypt-4 libswresample3 libswscale5 libudfread0
  libva-drm2 libva-wayland2 libva-x11-2 libva2 libvdpau1 libvidstab1.1
  libx265-199 libxvidcore4 libzimg2 libzmq5 libzvbi-common libzvbi0
  mesa-va-drivers mesa-vdpau-drivers pocketsphinx-en-us va-driver-all
  vdpau-driver-all
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb
  git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 8 not upgraded.
Need to get 4,121 kB of archives.
After this operation, 20.9 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 liberror-perl all 0.17029-1 [26.5 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.6 [953 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.6 [3,142 kB]
Fetched 4,121 kB in 1s (6,584 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 202827 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17029-1_all.deb ...
Unpacking liberror-perl (0.17029-1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.34.1-1ubuntu1.6_all.deb ...
Unpacking git-man (1:2.34.1-1ubuntu1.6) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.34.1-1ubuntu1.6_amd64.deb ...
Unpacking git (1:2.34.1-1ubuntu1.6) ...
Setting up liberror-perl (0.17029-1) ...
Setting up git-man (1:2.34.1-1ubuntu1.6) ...
Setting up git (1:2.34.1-1ubuntu1.6) ...
Processing triggers for man-db (2.10.2-1) ...
Cloning into 'rtw89'...
remote: Enumerating objects: 1871, done.
remote: Counting objects: 100% (522/522), done.
remote: Compressing objects: 100% (170/170), done.
remote: Total 1871 (delta 381), reused 454 (delta 350), pack-reused 1349
Receiving objects: 100% (1871/1871), 5.07 MiB | 11.15 MiB/s, done.
Resolving deltas: 100% (1386/1386), done.
make -C /lib/modules/5.15.0-60-generic/build M=/home/gordon/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-60-generic'
  CC [M]  /home/gordon/rtw89/core.o
  CC [M]  /home/gordon/rtw89/chan.o
  CC [M]  /home/gordon/rtw89/mac80211.o
  CC [M]  /home/gordon/rtw89/mac.o
  CC [M]  /home/gordon/rtw89/phy.o
  CC [M]  /home/gordon/rtw89/fw.o
  CC [M]  /home/gordon/rtw89/cam.o
  CC [M]  /home/gordon/rtw89/efuse.o
  CC [M]  /home/gordon/rtw89/regd.o
  CC [M]  /home/gordon/rtw89/sar.o
  CC [M]  /home/gordon/rtw89/coex.o
  CC [M]  /home/gordon/rtw89/ps.o
  CC [M]  /home/gordon/rtw89/debug.o
  CC [M]  /home/gordon/rtw89/ser.o
  CC [M]  /home/gordon/rtw89/wow.o
  LD [M]  /home/gordon/rtw89/rtw89core.o
  CC [M]  /home/gordon/rtw89/rtw8852a.o
  CC [M]  /home/gordon/rtw89/rtw8852a_table.o
  CC [M]  /home/gordon/rtw89/rtw8852a_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852a_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852a.o
  CC [M]  /home/gordon/rtw89/rtw8852ae.o
  LD [M]  /home/gordon/rtw89/rtw_8852ae.o
  CC [M]  /home/gordon/rtw89/rtw8852b.o
  CC [M]  /home/gordon/rtw89/rtw8852b_table.o
  CC [M]  /home/gordon/rtw89/rtw8852b_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852b_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852b.o
  CC [M]  /home/gordon/rtw89/rtw8852be.o
  LD [M]  /home/gordon/rtw89/rtw_8852be.o
  CC [M]  /home/gordon/rtw89/rtw8852c.o
  CC [M]  /home/gordon/rtw89/rtw8852c_table.o
  CC [M]  /home/gordon/rtw89/rtw8852c_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852c_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852c.o
  CC [M]  /home/gordon/rtw89/rtw8852ce.o
  LD [M]  /home/gordon/rtw89/rtw_8852ce.o
  CC [M]  /home/gordon/rtw89/pci.o
  LD [M]  /home/gordon/rtw89/rtw89pci.o
  MODPOST /home/gordon/rtw89/Module.symvers
  CC [M]  /home/gordon/rtw89/rtw89core.mod.o
  LD [M]  /home/gordon/rtw89/rtw89core.ko
  BTF [M] /home/gordon/rtw89/rtw89core.ko
Skipping BTF generation for /home/gordon/rtw89/rtw89core.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw89pci.mod.o
  LD [M]  /home/gordon/rtw89/rtw89pci.ko
  BTF [M] /home/gordon/rtw89/rtw89pci.ko
Skipping BTF generation for /home/gordon/rtw89/rtw89pci.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852a.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852a.ko
  BTF [M] /home/gordon/rtw89/rtw_8852a.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852a.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852ae.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852ae.ko
  BTF [M] /home/gordon/rtw89/rtw_8852ae.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852ae.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852b.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852b.ko
  BTF [M] /home/gordon/rtw89/rtw_8852b.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852b.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852be.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852be.ko
  BTF [M] /home/gordon/rtw89/rtw_8852be.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852be.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852c.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852c.ko
  BTF [M] /home/gordon/rtw89/rtw_8852c.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852c.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852ce.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852ce.ko
  BTF [M] /home/gordon/rtw89/rtw_8852ce.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852ce.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-60-generic'
gordon@gordon-HP-Laptop-15-dw4xxx:~/rtw89$ sudo make install
make -C /lib/modules/5.15.0-60-generic/build M=/home/gordon/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-60-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-60-generic'
Install rtw89 SUCCESS
gordon@gordon-HP-Laptop-15-dw4xxx:~/rtw89$ sudo modprobe rtw_8852be
gordon@gordon-HP-Laptop-15-dw4xxx:~/rtw89$ sudo modprobe rtw_8852becd rtw89
make clean
git pull
make
modprobe: FATAL: Module rtw_8852becd not found in directory /lib/modules/5.15.0-60-generic
Already up to date.
make -C /lib/modules/5.15.0-60-generic/build M=/home/gordon/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-60-generic'
  CC [M]  /home/gordon/rtw89/core.o
  CC [M]  /home/gordon/rtw89/chan.o
  CC [M]  /home/gordon/rtw89/mac80211.o
  CC [M]  /home/gordon/rtw89/mac.o
  CC [M]  /home/gordon/rtw89/phy.o
  CC [M]  /home/gordon/rtw89/fw.o
  CC [M]  /home/gordon/rtw89/cam.o
  CC [M]  /home/gordon/rtw89/efuse.o
  CC [M]  /home/gordon/rtw89/regd.o
  CC [M]  /home/gordon/rtw89/sar.o
  CC [M]  /home/gordon/rtw89/coex.o
  CC [M]  /home/gordon/rtw89/ps.o
  CC [M]  /home/gordon/rtw89/debug.o
  CC [M]  /home/gordon/rtw89/ser.o
  CC [M]  /home/gordon/rtw89/wow.o
  LD [M]  /home/gordon/rtw89/rtw89core.o
  CC [M]  /home/gordon/rtw89/rtw8852a.o
  CC [M]  /home/gordon/rtw89/rtw8852a_table.o
  CC [M]  /home/gordon/rtw89/rtw8852a_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852a_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852a.o
  CC [M]  /home/gordon/rtw89/rtw8852ae.o
  LD [M]  /home/gordon/rtw89/rtw_8852ae.o
  CC [M]  /home/gordon/rtw89/rtw8852b.o
  CC [M]  /home/gordon/rtw89/rtw8852b_table.o
  CC [M]  /home/gordon/rtw89/rtw8852b_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852b_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852b.o
  CC [M]  /home/gordon/rtw89/rtw8852be.o
  LD [M]  /home/gordon/rtw89/rtw_8852be.o
  CC [M]  /home/gordon/rtw89/rtw8852c.o
  CC [M]  /home/gordon/rtw89/rtw8852c_table.o
  CC [M]  /home/gordon/rtw89/rtw8852c_rfk.o
  CC [M]  /home/gordon/rtw89/rtw8852c_rfk_table.o
  LD [M]  /home/gordon/rtw89/rtw_8852c.o
  CC [M]  /home/gordon/rtw89/rtw8852ce.o
  LD [M]  /home/gordon/rtw89/rtw_8852ce.o
  CC [M]  /home/gordon/rtw89/pci.o
  LD [M]  /home/gordon/rtw89/rtw89pci.o
  MODPOST /home/gordon/rtw89/Module.symvers
  CC [M]  /home/gordon/rtw89/rtw89core.mod.o
  LD [M]  /home/gordon/rtw89/rtw89core.ko
  BTF [M] /home/gordon/rtw89/rtw89core.ko
Skipping BTF generation for /home/gordon/rtw89/rtw89core.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw89pci.mod.o
  LD [M]  /home/gordon/rtw89/rtw89pci.ko
  BTF [M] /home/gordon/rtw89/rtw89pci.ko
Skipping BTF generation for /home/gordon/rtw89/rtw89pci.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852a.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852a.ko
  BTF [M] /home/gordon/rtw89/rtw_8852a.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852a.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852ae.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852ae.ko
  BTF [M] /home/gordon/rtw89/rtw_8852ae.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852ae.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852b.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852b.ko
  BTF [M] /home/gordon/rtw89/rtw_8852b.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852b.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852be.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852be.ko
  BTF [M] /home/gordon/rtw89/rtw_8852be.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852be.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852c.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852c.ko
  BTF [M] /home/gordon/rtw89/rtw_8852c.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852c.ko due to unavailability of vmlinux
  CC [M]  /home/gordon/rtw89/rtw_8852ce.mod.o
  LD [M]  /home/gordon/rtw89/rtw_8852ce.ko
  BTF [M] /home/gordon/rtw89/rtw_8852ce.ko
Skipping BTF generation for /home/gordon/rtw89/rtw_8852ce.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-60-generic'
gordon@gordon-HP-Laptop-15-dw4xxx:~/rtw89$ sudo make install
make -C /lib/modules/5.15.0-60-generic/build M=/home/gordon/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-60-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-60-generic'
Install rtw89 SUCCESS

---

### Post by chili555 on 2023-02-10
> Still no wifi.Let's see:

```
sudo modprobe rtw_8852be
sudo dmesg | grep rtw

```
You might need to disable secure boot.

---

### Post by mIk3_08 on 2023-02-11
> **gordon33 said:**
> I am running Ubuntu 22.04 on a HP lap Top HP 15-dw4047nr.   The lap Top came with windows and the wifi worked after doing a clean install no wifi and  *-network UNCLAIMED.  I can connect with an ethernet cable.

gordon@gordon-HP-Laptop-15-dw4xxx:~$ lshw -c network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eno1
version: 15
serial: 5c:60:ba:ee:e5:c8
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-58-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
resources: irq:16 ioport:4000(size=256) memory:50904000-50904fff memory:50900000-50903fff
*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: ioport:3000(size=256) memory:50800000-508fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 

Gordon33
I also experience this one to my laptop wifi  broadcom proprietary driver. I don't know if we have the same issue. But maybe this will help. What I did is that, as far as I can remember, I did an update and upgrade to my system then I enable my secure boot from bios then it requires me then to enroll MOK uefi/efi during boot to enable my broadcom wifi driver. Then works smoothly then after. Regards and cheers.

---

### Post by gordon33 on 2023-02-13
Hello mIk3_08

was able to enable my secure boot in bios.  Their was no other pop up requirements to enroll MOK uefi/efi.   Still no wifi.   But ,I was able to do a wire less print.

---

### Post by jeremy31 on 2023-02-13
Post results for ```
uname -r; mokutil --sb; sudo dmesg | grep rtw
```

---

### Post by gordon33 on 2023-02-13
Hello Jeremy31

ordon@gordon-HP-Laptop-15-dw4xxx:~$ ^[[200~uname -r; mokutil --sb; sudo dmesg | grep rtw~
uname: command not found
SecureBoot enabled
gordon@gordon-HP-Laptop-

---

### Post by gordon33 on 2023-02-18
Hello All
After running    sudo apt dist-upgrade I got report problem clicking on report I got the following reply.



Problem in r8822bu-dkms

The problem cannot be reported:

This does not seem to be an official Ubuntu package.  Please retry after updating the indexes  of available packages, if that does not work then remove related third party packages and try again.

Close

---

