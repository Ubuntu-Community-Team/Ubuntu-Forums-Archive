---
title: "Wifi off after dual boot Ubuntu 22.04"
date: 2022-08-15
forum: Networking &amp; Wireless
---

### Post by lajuan21 on 2022-08-15
Hi,

I purchased a new Lenovo laptop with Win 11 Pro on it. I installed 22.04 and now the wifi is turned off while using Ubuntu. It sees the adapter but not working. Still pretty new to Linux and this is what's installed on my laptop:

lajuan@lajuan-ThinkBook-15-G4-ABA:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:4853 Realtek Semiconductor Corp. Bluetooth Radio
Bus 003 Device 002: ID 10a5:9800 FPC FPC Sensor Controller L:0001 FW:25.26.23.14
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 30c9:0030 Luxvisions Innotech Limited Integrated Camera
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 7
02:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller 980
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b852
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Barcelo (rev c2)
06:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller
06:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
06:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
06:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
06:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 01)
06:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ 

I first checked additional drivers and nothing shows up. I'm assuming the laptop sees the hardware but, must be a driver issue.

---

### Post by lajuan21 on 2022-08-15
BTW, Laptop is dual boot. I've also noticed when you dual boot a Windows machine, it will either mess with the graphics or network hardware.

---

### Post by chili555 on 2022-08-17
I suspect that you have no working driver, but let's check. Please run and post: ```
lspci -nnk | grep 0280 -A3
```This might be helpful: [https://askubuntu.com/questions/1412450/network-driver-for-realtek-10ecb852](https://askubuntu.com/questions/1412450/network-driver-for-realtek-10ecb852)

---

### Post by praseodym on 2022-08-20
Turn off FastBoot (or whatever it is called) in W10

---

### Post by lajuan21 on 2022-08-22
Here are my results....

---

### Post by lajuan21 on 2022-08-22
Fast boot is off and I can see the network adapter turned on in BIOS but, it doesn't show turned on when I log into Ubuntu. I had a similar issue with another laptop I dual booted on a Dell in the past. I had to force the wifi on with instructions I found in forum.

---

### Post by chili555 on 2022-08-22
Your wireless device has no driver. With a working nternet connection by ethernet, tethering or whatever means possible, open a teminal and do:

```
sudo apt update
sudo apt install git bc
git clone https://github.com/HRex39/rtl8852be.git
cd rtl8852be
make
```
Several possibly harmless warnings will appear.

```
sudo make install
```
Reboot. You will probably need to disable secure boot.

After each kernel update, you must recompile:

```
cd rtl8852be
make clean
git pull
make
sudo make install
```

---

### Post by lajuan21 on 2022-08-22
I must have done something wrong because after all that, here's my results and still no WIFI:

lajuan@lajuan-ThinkBook-15-G4-ABA:~$ cd rtl8852be
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ make clean
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
#make -C /lib/modules/5.15.0-46-generic/build M=/home/lajuan/rtl8852be clean
cd phl ; rm -fr */*/*/*/*.mod.c */*/*/*/*.mod */*/*/*/*.o */*/*/*/.*.cmd */*/*/*/*.ko
cd phl ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd phl ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd phl ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd phl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux/hwsim ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
/bin/sh: 1: cd: can't cd to os_dep/linux/hwsim
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ git pull
Already up to date.
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ make
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
#rm -f .symvers.8852be
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-46-generic/build M=/home/lajuan/rtl8852be  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-46-generic'
arch/x86/Makefile:142: CONFIG_X86_X32 enabled but no binutils support
make[1]: gcc: No such file or directory
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
  You are using:           
/bin/sh: 1: gcc: not found
(standard_in) 1: syntax error
  CC [M]  /home/lajuan/rtl8852be/platform/platform_linux_pc_pci.o
/bin/sh: 1: gcc: not found
make[2]: *** [scripts/Makefile.build:297: /home/lajuan/rtl8852be/platform/platform_linux_pc_pci.o] Error 127
make[1]: *** [Makefile:1881: /home/lajuan/rtl8852be] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-46-generic'
make: *** [Makefile:637: modules] Error 2
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ sudo make install
[sudo] password for lajuan: 
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
install -p -m 644 8852be.ko  /lib/modules/5.15.0-46-generic/kernel/drivers/net/wireless/
install: cannot stat '8852be.ko': No such file or directory
make: *** [Makefile:646: install] Error 1
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$

---

### Post by chili555 on 2022-08-22
> make[1]: gcc: No such file or directoryPlease do:
```
sudo apt update
sudo apt install build-essential bc

```
And then try again.

> make: *** [Makefile:637: modules] Error 2When 'make' ends in an error, stop and fix it. All further steps will fail as you've seen.

---

### Post by lajuan21 on 2022-08-26
Thanks BUT, the last step, isn't coming up with an error. It say not found. Here are my results:
```
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo apt install
[sudo] password for lajuan: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo apt install build-essential bc
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
bc is already the newest version (1.07.1-3build1).
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu dpkg-dev fakeroot g++
  g++-11 gcc gcc-11 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libasan6 libatomic1 libbinutils libc-dev-bin
  libc-devtools libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0
  libdpkg-perl libfakeroot libfile-fcntllock-perl libgcc-11-dev libitm1
  liblsan0 libnsl-dev libstdc++-11-dev libtirpc-dev libtsan0 libubsan1
  linux-libc-dev lto-disabled-list manpages-dev rpcsvc-proto
Suggested packages:
  binutils-doc debian-keyring g++-multilib g++-11-multilib gcc-11-doc
  gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-11-multilib
  gcc-11-locales glibc-doc bzr libstdc++-11-doc
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu build-essential dpkg-dev
  fakeroot g++ g++-11 gcc gcc-11 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan6 libatomic1
  libbinutils libc-dev-bin libc-devtools libc6-dev libcc1-0 libcrypt-dev
  libctf-nobfd0 libctf0 libdpkg-perl libfakeroot libfile-fcntllock-perl
  libgcc-11-dev libitm1 liblsan0 libnsl-dev libstdc++-11-dev libtirpc-dev
  libtsan0 libubsan1 linux-libc-dev lto-disabled-list manpages-dev
  rpcsvc-proto
0 upgraded, 38 newly installed, 0 to remove and 2 not upgraded.
Need to get 53.8 MB of archives.
After this operation, 185 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 binutils-common amd64 2.38-3ubuntu1 [221 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libbinutils amd64 2.38-3ubuntu1 [662 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libctf-nobfd0 amd64 2.38-3ubuntu1 [106 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libctf0 amd64 2.38-3ubuntu1 [103 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 binutils-x86-64-linux-gnu amd64 2.38-3ubuntu1 [2,328 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 binutils amd64 2.38-3ubuntu1 [3,186 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.1 [20.4 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-46.49 [1,298 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1 [112 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6 [68.5 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1 [192 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libnsl-dev amd64 1.3.0-2build2 [71.3 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.1 [2,099 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libcc1-0 amd64 12-20220319-1ubuntu1 [47.2 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libitm1 amd64 12-20220319-1ubuntu1 [30.2 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libatomic1 amd64 12-20220319-1ubuntu1 [10.4 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libasan6 amd64 11.2.0-19ubuntu1 [2,283 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 liblsan0 amd64 12-20220319-1ubuntu1 [1,069 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libtsan0 amd64 11.2.0-19ubuntu1 [2,261 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libubsan1 amd64 12-20220319-1ubuntu1 [976 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libgcc-11-dev amd64 11.2.0-19ubuntu1 [2,526 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 gcc-11 amd64 11.2.0-19ubuntu1 [20.1 MB]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1 [5,112 B]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libstdc++-11-dev amd64 11.2.0-19ubuntu1 [2,083 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 g++-11 amd64 11.2.0-19ubuntu1 [11.4 MB]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1 [1,412 B]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.1 [237 kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 lto-disabled-list all 24 [12.5 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.1 [922 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 build-essential amd64 12.9ubuntu3 [4,744 B]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1 [31.5 kB]
Get:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 fakeroot amd64 1.28-1ubuntu1 [60.4 kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libalgorithm-diff-perl all 1.201-1 [41.8 kB]
Get:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3 [11.9 kB]
Get:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.1 [28.9 kB]
Get:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 libfile-fcntllock-perl amd64 0.22-3build7 [33.9 kB]
Get:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 manpages-dev all 5.10-1ubuntu1 [2,309 kB]
Fetched 53.8 MB in 4s (14.9 MB/s)        
Extracting templates from packages: 100%
Selecting previously unselected package binutils-common:amd64.
(Reading database ... 197070 files and directories currently installed.)
Preparing to unpack .../00-binutils-common_2.38-3ubuntu1_amd64.deb ...
Unpacking binutils-common:amd64 (2.38-3ubuntu1) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../01-libbinutils_2.38-3ubuntu1_amd64.deb ...
Unpacking libbinutils:amd64 (2.38-3ubuntu1) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../02-libctf-nobfd0_2.38-3ubuntu1_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.38-3ubuntu1) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../03-libctf0_2.38-3ubuntu1_amd64.deb ...
Unpacking libctf0:amd64 (2.38-3ubuntu1) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../04-binutils-x86-64-linux-gnu_2.38-3ubuntu1_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.38-3ubuntu1) ...
Selecting previously unselected package binutils.
Preparing to unpack .../05-binutils_2.38-3ubuntu1_amd64.deb ...
Unpacking binutils (2.38-3ubuntu1) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../06-libc-dev-bin_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc-dev-bin (2.35-0ubuntu3.1) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../07-linux-libc-dev_5.15.0-46.49_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.15.0-46.49) ...
Selecting previously unselected package libcrypt-dev:amd64.
Preparing to unpack .../08-libcrypt-dev_1%3a4.4.27-1_amd64.deb ...
Unpacking libcrypt-dev:amd64 (1:4.4.27-1) ...
Selecting previously unselected package rpcsvc-proto.
Preparing to unpack .../09-rpcsvc-proto_1.4.2-0ubuntu6_amd64.deb ...
Unpacking rpcsvc-proto (1.4.2-0ubuntu6) ...
Selecting previously unselected package libtirpc-dev:amd64.
Preparing to unpack .../10-libtirpc-dev_1.3.2-2ubuntu0.1_amd64.deb ...
Unpacking libtirpc-dev:amd64 (1.3.2-2ubuntu0.1) ...
Selecting previously unselected package libnsl-dev:amd64.
Preparing to unpack .../11-libnsl-dev_1.3.0-2build2_amd64.deb ...
Unpacking libnsl-dev:amd64 (1.3.0-2build2) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../12-libc6-dev_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc6-dev:amd64 (2.35-0ubuntu3.1) ...
Selecting previously unselected package libcc1-0:amd64.
Preparing to unpack .../13-libcc1-0_12-20220319-1ubuntu1_amd64.deb ...
Unpacking libcc1-0:amd64 (12-20220319-1ubuntu1) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../14-libitm1_12-20220319-1ubuntu1_amd64.deb ...
Unpacking libitm1:amd64 (12-20220319-1ubuntu1) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../15-libatomic1_12-20220319-1ubuntu1_amd64.deb ...
Unpacking libatomic1:amd64 (12-20220319-1ubuntu1) ...
Selecting previously unselected package libasan6:amd64.
Preparing to unpack .../16-libasan6_11.2.0-19ubuntu1_amd64.deb ...
Unpacking libasan6:amd64 (11.2.0-19ubuntu1) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../17-liblsan0_12-20220319-1ubuntu1_amd64.deb ...
Unpacking liblsan0:amd64 (12-20220319-1ubuntu1) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../18-libtsan0_11.2.0-19ubuntu1_amd64.deb ...
Unpacking libtsan0:amd64 (11.2.0-19ubuntu1) ...
Selecting previously unselected package libubsan1:amd64.
Preparing to unpack .../19-libubsan1_12-20220319-1ubuntu1_amd64.deb ...
Unpacking libubsan1:amd64 (12-20220319-1ubuntu1) ...
Selecting previously unselected package libgcc-11-dev:amd64.
Preparing to unpack .../20-libgcc-11-dev_11.2.0-19ubuntu1_amd64.deb ...
Unpacking libgcc-11-dev:amd64 (11.2.0-19ubuntu1) ...
Selecting previously unselected package gcc-11.
Preparing to unpack .../21-gcc-11_11.2.0-19ubuntu1_amd64.deb ...
Unpacking gcc-11 (11.2.0-19ubuntu1) ...
Selecting previously unselected package gcc.
Preparing to unpack .../22-gcc_4%3a11.2.0-1ubuntu1_amd64.deb ...
Unpacking gcc (4:11.2.0-1ubuntu1) ...
Selecting previously unselected package libstdc++-11-dev:amd64.
Preparing to unpack .../23-libstdc++-11-dev_11.2.0-19ubuntu1_amd64.deb ...
Unpacking libstdc++-11-dev:amd64 (11.2.0-19ubuntu1) ...
Selecting previously unselected package g++-11.
Preparing to unpack .../24-g++-11_11.2.0-19ubuntu1_amd64.deb ...
Unpacking g++-11 (11.2.0-19ubuntu1) ...
Selecting previously unselected package g++.
Preparing to unpack .../25-g++_4%3a11.2.0-1ubuntu1_amd64.deb ...
Unpacking g++ (4:11.2.0-1ubuntu1) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../26-libdpkg-perl_1.21.1ubuntu2.1_all.deb ...
Unpacking libdpkg-perl (1.21.1ubuntu2.1) ...
Selecting previously unselected package lto-disabled-list.
Preparing to unpack .../27-lto-disabled-list_24_all.deb ...
Unpacking lto-disabled-list (24) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../28-dpkg-dev_1.21.1ubuntu2.1_all.deb ...
Unpacking dpkg-dev (1.21.1ubuntu2.1) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../29-build-essential_12.9ubuntu3_amd64.deb ...
Unpacking build-essential (12.9ubuntu3) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../30-libfakeroot_1.28-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.28-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../31-fakeroot_1.28-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.28-1ubuntu1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../32-libalgorithm-diff-perl_1.201-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.201-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../33-libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-6build3) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../34-libalgorithm-merge-perl_0.08-3_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-3) ...
Selecting previously unselected package libc-devtools.
Preparing to unpack .../35-libc-devtools_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc-devtools (2.35-0ubuntu3.1) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../36-libfile-fcntllock-perl_0.22-3build7_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-3build7) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../37-manpages-dev_5.10-1ubuntu1_all.deb ...
Unpacking manpages-dev (5.10-1ubuntu1) ...
Setting up manpages-dev (5.10-1ubuntu1) ...
Setting up lto-disabled-list (24) ...
Setting up libfile-fcntllock-perl (0.22-3build7) ...
Setting up libalgorithm-diff-perl (1.201-1) ...
Setting up binutils-common:amd64 (2.38-3ubuntu1) ...
Setting up linux-libc-dev:amd64 (5.15.0-46.49) ...
Setting up libctf-nobfd0:amd64 (2.38-3ubuntu1) ...
Setting up libfakeroot:amd64 (1.28-1ubuntu1) ...
Setting up libasan6:amd64 (11.2.0-19ubuntu1) ...
Setting up fakeroot (1.28-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (
fakeroot) in auto mode
Setting up libtirpc-dev:amd64 (1.3.2-2ubuntu0.1) ...
Setting up rpcsvc-proto (1.4.2-0ubuntu6) ...
Setting up libatomic1:amd64 (12-20220319-1ubuntu1) ...
Setting up libdpkg-perl (1.21.1ubuntu2.1) ...
Setting up libubsan1:amd64 (12-20220319-1ubuntu1) ...
Setting up libnsl-dev:amd64 (1.3.0-2build2) ...
Setting up libcrypt-dev:amd64 (1:4.4.27-1) ...
Setting up libbinutils:amd64 (2.38-3ubuntu1) ...
Setting up libc-dev-bin (2.35-0ubuntu3.1) ...
Setting up libalgorithm-diff-xs-perl (0.04-6build3) ...
Setting up libcc1-0:amd64 (12-20220319-1ubuntu1) ...
Setting up liblsan0:amd64 (12-20220319-1ubuntu1) ...
Setting up libitm1:amd64 (12-20220319-1ubuntu1) ...
Setting up libc-devtools (2.35-0ubuntu3.1) ...
Setting up libalgorithm-merge-perl (0.08-3) ...
Setting up libtsan0:amd64 (11.2.0-19ubuntu1) ...
Setting up libctf0:amd64 (2.38-3ubuntu1) ...
Setting up libgcc-11-dev:amd64 (11.2.0-19ubuntu1) ...
Setting up libc6-dev:amd64 (2.35-0ubuntu3.1) ...
Setting up binutils-x86-64-linux-gnu (2.38-3ubuntu1) ...
Setting up binutils (2.38-3ubuntu1) ...
Setting up dpkg-dev (1.21.1ubuntu2.1) ...
Setting up libstdc++-11-dev:amd64 (11.2.0-19ubuntu1) ...
Setting up gcc-11 (11.2.0-19ubuntu1) ...
Setting up g++-11 (11.2.0-19ubuntu1) ...
Setting up gcc (4:11.2.0-1ubuntu1) ...
Setting up g++ (4:11.2.0-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mo
de
Setting up build-essential (12.9ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make: *** [Makefile:637: modules] Error 2
Command 'make:' not found, did you mean:
  command 'make' from deb make (4.3-4.1build1)
  command 'make' from deb make-guile (4.3-4.1build1)
  command 'makeg' from deb xutils-dev (1:7.7+6ubuntu1)
Try: sudo apt install <deb name>
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make:***[Makefile:637:modules] Error 2
make:***[Makefile:637:modules]: command not found
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make: ***[Makefile:637: modules] Error 2
Command 'make:' not found, did you mean:
  command 'makeg' from deb xutils-dev (1:7.7+6ubuntu1)
  command 'make' from deb make (4.3-4.1build1)
  command 'make' from deb make-guile (4.3-4.1build1)
Try: sudo apt install <deb name>
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ ^[[200~make: *** [Makefile:637: modules] Error 2
make:: command not found
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make: *** [Makefile:637: modules] Error 2 
Command 'make:' not found, did you mean:
  command 'makeg' from deb xutils-dev (1:7.7+6ubuntu1)
  command 'make' from deb make (4.3-4.1build1)
  command 'make' from deb make-guile (4.3-4.1build1)
Try: sudo apt install <deb name>
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ 
```


Do I need to start from the beginning of the installing the driver process or did I miss something? I really appreciate your help!!!! #Newbie101OnBoard

---

### Post by chili555 on 2022-08-26
> Do I need to start from the beginning of the installing the driver processYes.

From your previous post, we are sure that you have 'make' installed as it's a dependency of build-essential. Confirm:

```
make --version
```Also, you are in the wrong directory:

> lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make:***[Makefile:637:modules] Error 2

The little ~ symbol indicates that you are in the /home/lujuan directory. The driver files are in the directory that you cloned (downloaded) called rtl8852be. That's why the instructions include the step:

```
cd rtl8852be
```After doing so, the prompt should read:```
 lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$

```You can confirm that you are in the directory containing the driver files by listing the contents:```
 ls
```You should see:
```
clean      core         include  Makefile  phl       README.md  wlan0dhcp
common.mk  ifcfg-wlan0  Kconfig  os_dep    platform  runwpa
```Or very similar.

I am fairly certain that 'make' is installed correctly. Please do:

```
cd rtl8852be  ###Only if you have not done so already
make
sudo make install
```Please tell us the result.

---

### Post by lajuan21 on 2022-08-31
So, I started from the beginning and after reboot continue the steps and here are my results:

```
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ cd rtl8852be
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ make clean
#make -C /lib/modules/5.15.0-46-generic/build M=/home/lajuan/rtl8852be clean
cd phl ; rm -fr */*/*/*/*.mod.c */*/*/*/*.mod */*/*/*/*.o */*/*/*/.*.cmd */*/*/*/*.ko
cd phl ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd phl ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd phl ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd phl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux/hwsim ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
/bin/sh: 1: cd: can't cd to os_dep/linux/hwsim
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ git pull
remote: Enumerating objects: 26, done.
remote: Counting objects: 100% (26/26), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 16 (delta 8), reused 11 (delta 6), pack-reused 0
Unpacking objects: 100% (16/16), 15.04 KiB | 770.00 KiB/s, done.
From [https://github.com/HRex39/rtl8852be](https://github.com/HRex39/rtl8852be)
   83817c0..7e9d096  main       -> origin/main
   60d838a..28daf8c  dev        -> origin/dev
Updating 83817c0..7e9d096
Fast-forward
 LICENSE   | 674 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 README.md |  29 ++-
 2 files changed, 695 insertions(+), 8 deletions(-)
 create mode 100644 LICENSE
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ make
#rm -f .symvers.8852be
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-46-generic/build M=/home/lajuan/rtl8852be  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-46-generic'
  CC [M]  /home/lajuan/rtl8852be/platform/platform_linux_pc_pci.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/osdep_service.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/osdep_service_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/rtw_cfg.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/os_intfs.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/ioctl_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/xmit_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/mlme_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/recv_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/ioctl_cfg80211.o
/home/lajuan/rtl8852be/os_dep/linux/ioctl_cfg80211.c: In function &#8216;rtw_get_chbwoff_from_cfg80211_chan_def&#8217;:
/home/lajuan/rtl8852be/os_dep/linux/ioctl_cfg80211.c:6233:21: warning: this statement may fall through [-Wimplicit-fallthrough=]
 6233 |                 *ht = 0;
      |                 ~~~~^~~
/home/lajuan/rtl8852be/os_dep/linux/ioctl_cfg80211.c:6235:9: note: here
 6235 |         case NL80211_CHAN_WIDTH_20:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/wifi_regd.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/rtw_android.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/rtw_proc.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/nlrtw.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/rtw_rhashtable.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/pci_intf.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/pci_ops_linux.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/ioctl_mp.o
  CC [M]  /home/lajuan/rtl8852be/os_dep/linux/ioctl_efuse.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_cmd.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_security.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_debug.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_io.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_ioctl_query.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_ioctl_set.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_ieee80211.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_mlme.o
/home/lajuan/rtl8852be/core/rtw_mlme.c: In function &#8216;_disconnect_msg_hdlr&#8217;:
/home/lajuan/rtl8852be/core/rtw_mlme.c:5842:20: warning: this statement may fall through [-Wimplicit-fallthrough=]
 5842 |                 if (status == RTW_PHL_STATUS_SUCCESS)
      |                    ^
/home/lajuan/rtl8852be/core/rtw_mlme.c:5846:9: note: here
 5846 |         case MSG_EVT_DISCONNECT:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/core/rtw_mlme_ext.o
/home/lajuan/rtl8852be/core/rtw_mlme_ext.c: In function &#8216;mgt_dispatcher&#8217;:
/home/lajuan/rtl8852be/core/rtw_mlme_ext.c:1810:38: warning: this statement may fall through [-Wimplicit-fallthrough=]
 1810 |                         ptable->func = &OnAuthClient;
      |                         ~~~~~~~~~~~~~^~~~~~~~~~~~~~~
/home/lajuan/rtl8852be/core/rtw_mlme_ext.c:1812:9: note: here
 1812 |         case WIFI_ASSOCREQ:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/core/rtw_sec_cam.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_mi.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_wlan_util.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_vht.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_he.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_pwrctrl.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_rf.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_chplan.o
  CC [M]  /home/lajuan/rtl8852be/core/monitor/rtw_radiotap.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_recv.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_recv_shortcut.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_sta_mgt.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_ap.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_csa.o
  CC [M]  /home/lajuan/rtl8852be/core/wds/rtw_wds.o
  CC [M]  /home/lajuan/rtl8852be/core/mesh/rtw_mesh.o
  CC [M]  /home/lajuan/rtl8852be/core/mesh/rtw_mesh_pathtbl.o
  CC [M]  /home/lajuan/rtl8852be/core/mesh/rtw_mesh_hwmp.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_xmit.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_xmit_shortcut.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_p2p.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_tdls.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_br_ext.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_sreset.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_rm.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_rm_fsm.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_rm_util.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_trx.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_beamforming.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_scan.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_phl.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_phl_cmd.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-internal.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-internal-enc.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-gcm.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-ccm.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-omac1.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/ccmp.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/gcmp.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-siv.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/aes-ctr.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/sha256-internal.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/sha256.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/sha256-prf.o
  CC [M]  /home/lajuan/rtl8852be/core/crypto/rtw_crypto_wrap.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_swcrypto.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_trx_pci.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_mp.o
  CC [M]  /home/lajuan/rtl8852be/core/rtw_btc.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_init.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_debug.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_rx.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_rx_agg.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_api_drv.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_role.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_sta.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_mr.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_sec.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_chan.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_sw_cap.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_util.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_pkt_ofld.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_connect.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_chan_info.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_wow.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_dm.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_chnlplan.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_country.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_chnlplan_6g.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_regulation.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_regulation_6g.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_led.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_trx_mit.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_acs.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_mcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_ecsa.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/phl_dbg_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/phl_ser_dbg_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_msg_hub.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_sound.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_twt.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_notify.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_sound_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_p2pps.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_thermal.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_txpwr.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_ps.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/phl_ps_dbg_cmd.o
In file included from /home/lajuan/rtl8852be/phl/test/../phl_headers.h:61,
                 from /home/lajuan/rtl8852be/phl/test/phl_ps_dbg_cmd.c:16:
/home/lajuan/rtl8852be/phl/test/phl_ps_dbg_cmd.c: In function &#8216;phl_ps_cmd_parser&#8217;:
/home/lajuan/rtl8852be/phl/test/../test/phl_ps_dbg_cmd.h:19:12: warning: this statement may fall through [-Wimplicit-fallthrough=]
   19 |         do {                                                            \
      |            ^
/home/lajuan/rtl8852be/phl/test/phl_ps_dbg_cmd.c:100:17: note: in expansion of macro &#8216;PS_CNSL&#8217;
  100 |                 PS_CNSL(out_len, used, output + used, out_len - used,
      |                 ^~~~~~~
/home/lajuan/rtl8852be/phl/test/phl_ps_dbg_cmd.c:104:9: note: here
  104 |         case PHL_PS_HELP:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_ps.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_dispatch_engine.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_dispatcher.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_dispr_controller.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_ser.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_general.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_scan.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_cmd_btc.o
  CC [M]  /home/lajuan/rtl8852be/phl/phl_watchdog.o
  CC [M]  /home/lajuan/rtl8852be/phl/hci/phl_trx_pcie.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/trx_test.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/test_module.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/cmd_disp_test.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_config.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_rx.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_reg.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_efuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_txpwr.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/mp/phl_test_mp_cal.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/verify/phl_test_verify.o
  CC [M]  /home/lajuan/rtl8852be/phl/test/verify/dbcc/phl_test_dbcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api_mac.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api_bb.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api_rf.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api_btc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api_efuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_com_i.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_init.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_io.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_rx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_sta.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_cam.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_csi_buffer.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_beamform.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_sound.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_chan.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_str_proc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_fw.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_cap.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_ser.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_ps.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_c2h.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_dbcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_chan_info.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_wow.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_ld_file.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_regulation.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_led.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_trx_mit.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_acs.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_mcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_api.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_twt.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_notify.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_p2pps.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_thermal.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_txpwr.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/hal_pci.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/hal_test_module.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_cal.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_config.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_efuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_reg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_rx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/test/mp/hal_test_mp_txpwr.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/efuse/hal_efuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/addr_cam.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/cmac_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/coex.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/cpuio.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/dbgpkg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/dbgport_hw.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/dbg_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/dle.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/efuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/fwcmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/fwdl.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/fwofld.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/gpio.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hci_fc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hdr_conv.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw_seq.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/h2c_agg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.o
/home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.c: In function &#8216;cfg_mac_bw&#8217;:
/home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.c:1639:26: warning: this statement may fall through [-Wimplicit-fallthrough=]
 1639 |                 txsc80 = rtw_hal_bb_get_txsc(hal_com, cfg->pri_ch,
      |                          ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 1640 |                                              cfg->central_ch, cfg->cbw,
      |                                              ~~~~~~~~~~~~~~~~~~~~~~~~~~
 1641 |                                              CHANNEL_WIDTH_80);
      |                                              ~~~~~~~~~~~~~~~~~
/home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.c:1643:9: note: here
 1643 |         case CHANNEL_WIDTH_80:
      |         ^~~~
/home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.c:1644:26: warning: this statement may fall through [-Wimplicit-fallthrough=]
 1644 |                 txsc40 = rtw_hal_bb_get_txsc(hal_com, cfg->pri_ch,
      |                          ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 1645 |                                              cfg->central_ch, cfg->cbw,
      |                                              ~~~~~~~~~~~~~~~~~~~~~~~~~~
 1646 |                                              CHANNEL_WIDTH_40);
      |                                              ~~~~~~~~~~~~~~~~~
/home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hw.c:1648:9: note: here
 1648 |         case CHANNEL_WIDTH_40:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/hwamsdu.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/init.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/la_mode.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mport.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/phy_rpt.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/power_saving.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/pwr.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/p2p.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/role.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/rx_filter.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/rx_forwarding.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/rrsr.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/ser.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/security_cam.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/sounding.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/status.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/tblupd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/tcpip_checksum_offload.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/trx_desc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/trxcfg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/twt.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/wowlan.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/flash.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/spatial_reuse.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/pwr_seq_func.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/phy_misc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/_pcie.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mac_8852b/gpio_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mac_8852b/init_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mac_8852b/pwr_seq_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/mac_ax/mac_8852b/pwr_seq_func_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/fw_ax/rtl8852b/hal8852b_fw.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/fw_ax/rtl8852b/hal8852b_fw_log.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/mac/fw_ax/rtl8852b/hal8852b_fw_u1.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/hal_btc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_def.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_action.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_fw.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_dbg_cmd.o
/home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_dbg_cmd.c: In function &#8216;halbtc_cmd_parser&#8217;:
/home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_dbg_cmd.c:26:12: warning: this statement may fall through [-Wimplicit-fallthrough=]
   26 |         do {                                                    \
      |            ^
/home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_dbg_cmd.c:2000:17: note: in expansion of macro &#8216;BTC_CNSL&#8217;
 2000 |                 BTC_CNSL(out_len, used, output + used, out_len - used,
      |                 ^~~~~~~~
/home/lajuan/rtl8852be/phl/hal_g6/btc/halbtc_dbg_cmd.c:2005:9: note: here
 2005 |         case HALBTC_HELP:
      |         ^~~~
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/btc/btc_8852b/btc_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/rtl8852b_halinit.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/rtl8852b_mac.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/rtl8852b_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/rtl8852b_phy.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/rtl8852b_ops.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/hal_trx_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/rtl8852be_halinit.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/rtl8852be_halmac.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/rtl8852be_io.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/rtl8852be_led.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/rtl8852be_ops.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/rtl8852b/pci/hal_trx_8852be.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_api.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_rua_tbl.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_auto_dbg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_cfo_trk.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_ch_info.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_cmn_rpt.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dbcc.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dbg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dbg_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dfs.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_edcca.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_env_mntr.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_hw_cfg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_init.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_interface.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_la_mode.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_math_lib.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_mp.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_plcp_gen.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_plcp_tx.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_pmac_setting.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_psd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_physts.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_pwr_ctrl.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_ra.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_statistics.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_ant_div.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dig.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_fwofld.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_dyn_csi_rsp.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_8852b/halbb_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_8852b/halbb_8852b_api.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_8852b/halbb_hwimg_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/bb/halbb_8852b/halbb_reg_cfg_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_pmac.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_api.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_dbg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_dbg_cmd.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_ex.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_hw_cfg.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_init.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_interface.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_pwr_table.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_iqk.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_8852b_api.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_hwimg_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_txgapk_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_iqk_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_reg_cfg_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_dack_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_dpk_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_set_pwr_table_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_efuse_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_tssi_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_kfree_8852b.o
  CC [M]  /home/lajuan/rtl8852be/phl/hal_g6/phy/rf/halrf_8852b/halrf_psd_8852b.o
  LD [M]  /home/lajuan/rtl8852be/8852be.o
  MODPOST /home/lajuan/rtl8852be/Module.symvers
  CC [M]  /home/lajuan/rtl8852be/8852be.mod.o
  LD [M]  /home/lajuan/rtl8852be/8852be.ko
  BTF [M] /home/lajuan/rtl8852be/8852be.ko
Skipping BTF generation for /home/lajuan/rtl8852be/8852be.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-46-generic'
#cp Module.symvers .symvers.8852be
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ sudo make install
[sudo] password for lajuan: 
install -p -m 644 8852be.ko  /lib/modules/5.15.0-46-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 5.15.0-46-generic
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ 
```

I still don't see the WIFI enabled

---

### Post by chili555 on 2022-09-02
If you load the module, are there any errors?

```
sudo modprobe 8852be
```

Are there any clues in the logs?

```
sudo dmesg | grep 8852
```

---

### Post by sokudo on 2022-09-04
What kernel do you have, I originally had a problem with pop!_OS bc kernel was like 5.19, then I down graded it, and did the exact same install from HRex and it worked for me no turning it off and on. also when you do the first make, make sure -j8 flag is there

[https://github.com/HRex39/rtl8852be](https://github.com/HRex39/rtl8852be). 

I downgraded my pops kernel which was at 5.19 to i think 5.18. as you will see on the github page there is a particular way to install as per the kernel version. Then when i installed Ubuntu, 22.04 I didnt even need to down grade the kernel. Hope this helps

---

### Post by lajuan21 on 2022-09-13
```
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo modprobe 8852be
[sudo] password for lajuan: 
modprobe: ERROR: could not insert '8852be': Operation not permitted
lajuan@lajuan-ThinkBook-15-G4-ABA:~$
```

---

### Post by lajuan21 on 2022-09-13
```
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo dmesg | grep 8852
[sudo] password for lajuan: 
[    1.763815] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000b lmp_ver=0b lmp_subver=8852
[    1.763819] Bluetooth: hci0: RTL: unknown IC info, lmp subver 8852, hci rev 000b, hci ver 000b
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ ^C
lajuan@lajuan-ThinkBook-15-G4-ABA:~$
```

---

### Post by lajuan21 on 2022-09-13
```
ajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo dmesg | grep 8852
[sudo] password for lajuan: 
[    1.763815] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000b lmp_ver=0b lmp_subver=8852
[    1.763819] Bluetooth: hci0: RTL: unknown IC info, lmp subver 8852, hci rev 000b, hci ver 000b
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ ^C
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ make --version
GNU Make 4.3
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ cd rtl8852be
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ ls
8852be.ko     8852be.o   ifcfg-wlan0  Makefile        phl        wlan0dhcp
8852be.mod    clean      include      modules.order   platform
8852be.mod.c  common.mk  Kconfig      Module.symvers  README.md
8852be.mod.o  core       LICENSE      os_dep          runwpa
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ make
#rm -f .symvers.8852be
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-46-generic/build M=/home/lajuan/rtl8852be  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-46-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-46-generic'
#cp Module.symvers .symvers.8852be
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ sudo make install
install -p -m 644 8852be.ko  /lib/modules/5.15.0-46-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 5.15.0-46-generic
lajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$
```

---

### Post by chili555 on 2022-09-13
Please disable Secure Boot and try again.

---

### Post by lajuan21 on 2022-09-21
After about two weeks, my WIFI was working and stopped working a few days ago. The ONLY thing that happened was an major update. After the laptop rebooted, the WIFI is now disabled again..

---

### Post by chili555 on 2022-09-21
May we see:

```
rfkill list all
sudo dmesg | grep -e wlp -e 8852
lsmod | grep 8852
```

I suspect that you need to recompile and install the driver.

---

### Post by lajuan21 on 2022-09-23
Here are my results:

lajuan@lajuan-ThinkBook-15-G4-ABA:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ sudo dmesg | grep -e wlp -e 8852
[sudo] password for lajuan: 
[    1.893560] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000b lmp_ver=0b lmp_subver=8852
[    1.893565] Bluetooth: hci0: RTL: unknown IC info, lmp subver 8852, hci rev 000b, hci ver 000b
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ lsmod | grep 8852
lajuan@lajuan-ThinkBook-15-G4-ABA:~$ ^C
lajuan@lajuan-ThinkBook-15-G4-ABA:~$

---

### Post by chili555 on 2022-09-24
> The ONLY thing that happened was an major update. Which probaby included a kernel update. In that case, recompile:

```
cd rtl8852be
make clean
git pull
make
sudo make install
sudo modprobe 8852be
```

The wireless should spring to life.

---

### Post by lajuan21 on 2022-12-05
Sorry!!!! Been tied up with school work!!!! On the last step I'm getting this error:
 
ajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ sudo modprobe 8852be
modprobe: ERROR: could not insert '8852be': Operation not permitted

---

### Post by chili555 on 2022-12-05
> **lajuan21 said:**
> Sorry!!!! Been tied up with school work!!!! On the last step I'm getting this error:
 
ajuan@lajuan-ThinkBook-15-G4-ABA:~/rtl8852be$ sudo modprobe 8852be
modprobe: ERROR: could not insert '8852be': Operation not permittedIs Secure Boot off or on?

---

### Post by lajuan21 on 2022-12-05
I believe I turned it off but, I can check

---

### Post by smbunn on 2022-12-14
*Are there any other BIOS settings we should be aware of to improve the reliability of Ubuntu booting correctly and seeing all the device drivers?*

---

### Post by lajuan21 on 2022-12-29
Hi,

So, I turned off secure boot and as soon as my laptop booted in Ubuntu it displayed wireless!!!! I'll test when I get home to see if it maintains BUT, wanted to to thank you for your assistant!!!!!!!!!!

---

### Post by lajuan21 on 2023-01-11
So, every time my laptop either does a Windows' or Ubuntu update my WIFI goes off and I don't know if it's my Microsoft or Ubuntu turning it off after updates. Is there a way to force it to stay on?

---

### Post by chili555 on 2023-01-11
>  my WIFI goes off Meaning what? That the airplane mode is on? That it won't connect? That there is no longer any driver? Please clarify.

Please recall that when a driver is installed with make and sudo make install, it will be installed for the running kernel only. Any update that brings along a newer kernel version, after the requested reboot, you must reinstall the driver. Please see post #22 above.

There is a mechanism to do all of this automagically called DKMS. However, as far as I know, there is not yet a dkms version of your 8852be driver.

---

### Post by lajuan21 on 2023-02-10
Meaning after every update with Ubuntu, the wireless adapter gets turned off and I have to do the steps to enable it. Is there a way to prevent this from happening?

---

### Post by lajuan21 on 2023-02-10
Thanks!!!!!!!!

---

