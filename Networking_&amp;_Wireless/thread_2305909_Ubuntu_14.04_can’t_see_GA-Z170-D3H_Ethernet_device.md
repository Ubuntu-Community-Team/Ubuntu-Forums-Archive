---
title: "Ubuntu 14.04 can’t see GA-Z170-D3H Ethernet device"
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by glob3 on 2015-12-10
I've installed Biolinux 8.07 (Ubuntu 14.04 based) on GIGABYTE GA-Z170-D3H (with i7-6700) machine in dual-boot with Win10 successfully, however got one problem.
During installation from live USB-flash, Ubuntu can't see the internal motherboard wired ethernet device and can't connect to Internet. The only way to connect to LAN is USB Wi-fi adapter, which was identified. Important: after rebooting, in Win10 both devices work nicely.
I've upgraded the system via Wi-fi adapter, but in Ubuntu the ethernet device doesn't work till now.
After googling I've tried several commands without any success (below). I would greatly appreciate if someone can help me.
```
sudo apt-get update 
sudo apt-get dist-upgrade
```
And some others:
```
sudo apt-get install ethtool                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
The following packages were automatically installed and are no longer required:
  freeglut3 icu-devtools libglw1-mesa libicu-dev libtcmalloc-minimal4
  linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

sudo ethtool eth0                                      
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6176 (6.1 KB)  TX bytes:6176 (6.1 KB)

sudo lshw -C network 
*-network UNCLAIMED     
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
version: 31
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:df100000-df11ffff

dmesg | grep -e eth -e e1000
[    0.000000] efi: mem170: type=3, attr=0xf, range=[0x00000000848e0000-0x00000000848e1000) (0MB)
[    0.000000] efi: mem171: type=4, attr=0xf, range=[0x00000000848e1000-0x00000000848e2000) (0MB)
```

---

### Post by chili555 on 2015-12-10
Please tell us a bit more about your ethernet device; from the terminal:```
lspci -nn | grep 0200
```Thanks.

---

### Post by glob3 on 2015-12-10
> **chili555 said:**
> Please tell us a bit more about your ethernet device; from the terminal:```
lspci -nn | grep 0200
```Thanks.

Here:
```
00:1f.6 Ethernet controller [0200]: Intel Corporation Device [8086:15b8] (rev 31)
```

---

### Post by chili555 on 2015-12-10
> Intel Corporation Device [[COLOR="#FF0000"]8086:15b8[/COLOR]]Your device is covered by the driver e1000e in later versions of Ubuntu. We wonder if it is included in 14.04. Please check for us:```
modinfo e1000e | grep 15B8
```You ought to see:```
alias:          pci:v00008086d0000[COLOR="#FF0000"]15B8[/COLOR]sv*sd*bc*sc*i*
```If not, tell us.

If so, load the driver and see if the ethernet springs to life:```
sudo modprobe e1000e
ifconfig
```Do you now see an eth0 interface? Can you connect?

If not, check the log for errors, warnings, clues, funny business, etc.:```
dmesg | grep e100
```

---

### Post by glob3 on 2015-12-10
```
modinfo e1000e | grep 15B8
```

Returns nothing. Empty string.

---

### Post by chili555 on 2015-12-10
With a working internet connection, please do:```
sudo apt-get install build-essential linux-headers-generic
```Download the tar.gz file here to your desktop: [http://sourceforge.net/projects/e1000/files/e1000e%20stable/3.3.1/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/3.3.1/)  Right-click it and select 'Extract Here.' Now, back to the terminal:```
cd ~/Desktop/e1000e-3.3.1/src
make
sudo make install
sudo modprobe e1000e
```Now are there any signs of life?```
ifconfig
```

---

### Post by glob3 on 2015-12-10
IT WORKS!!! Great! 
Thank you very much!

---

### Post by chili555 on 2015-12-10
> **glob3 said:**
> IT WORKS!!! Great! 
Thank you very much!You are very welcome, but hold on a second or two.

You have compiled the driver for your currently running kernel version only. When Update Manager installs a later linux-image, after the requested reboot, recompile:```
cd ~/Desktop/e1000e-3.3.1/src
make clean
make
sudo make install
sudo modprobe e1000e
```Please retain the file and these instructions for that time.

Finally, please use the thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by oldfred on 2015-12-10
The Z170 is new, and you may do better with 15.10 but may still need newer kernels & drivers.
They temporally added kernel 4.3 to 16.04, but plan on 4.4 when Linus releases 4.4. And 4.5 will be too near final release of 16.04.

       Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

On my Z97 Asus motherboard I had to make many UEFI setting changes to get it to correctly boot and work in UEFI mode.

Older Gigabyte boards have had issues with iommu, not sure if you need that setting or not.
       turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)

---

