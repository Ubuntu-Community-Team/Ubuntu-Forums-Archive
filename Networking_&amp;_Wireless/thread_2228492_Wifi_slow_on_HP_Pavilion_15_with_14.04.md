---
title: "Wifi slow on HP Pavilion 15 with 14.04"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by Tom_Collins on 2014-06-07
I'm having trouble with slow and inconsistent wifi on my HP Pavilion 15-n228us laptop with Ubuntu 14.04. I'm very new to Linux and I'm having a difficult time troubleshooting this. I purchased a D-Link DWA-131 adapter thinking that the laptop's wifi card was a dead end on Ubuntu, but this adapter performs just as poorly. So far, I have followed the instructions posted [here]("http://bernaerts.dyndns.org/linux/74-ubuntu/277-ubuntu-precise-dwa-131-rev-b1") (minus step 3) to get my D-Link adapter to work. Any help would be greatly appreciated.

Here's the details on my wireless card:
```
  *-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 54:35:30:47:f5:8b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 ioport:3000(size=256) memory:f1000000-f1003fff

```


Here are the details on my D-Link USB adapter:
```

  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@5:2
       logical name: wlan1
       serial: d8:fe:e3:2c:34:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.13.0-29-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by squakie on 2014-06-07
There is another driver for that wireless adapter that has worked for that adapter in multiple vendor's laptops.  Have a look at:

[http://ubuntuforums.org/showthread.php?t=2160177](http://ubuntuforums.org/showthread.php?t=2160177)

The solution worked great for me.  I had problems later, but I know I made some other changes I shouldn't have ;) that messed everything up.

---

### Post by Tom_Collins on 2014-06-15
So I'm at my wits end here. I've been fighting this OS + laptop for a month and would have just reinstalled Windows, but I need to learn Linux for work. I have tried the solution given [here in post #11]("http://ubuntuforums.org/showthread.php?t=2162026"), but I encountered errors and don't know how to proceed. I have tried to install Ubuntu 12.04, because I've read that some people have had success with that version, but it simply hangs once I try to log in. I have tried to upgrade the kernel to version 3.14.6 using the instructions [here]("http://linuxg.net/how-to-install-kernel-3-14-6-on-ubuntu-linux-mint-and-their-derivative-systems/"). Again, I encountered the following errors:
```

tom@pavilion:~$ sudo dpkg -i linux-image-3.14.6*.deb linux-headers-3.14.6*.deb
[sudo] password for tom: 
Selecting previously unselected package linux-image-3.14.6-031406-generic.
(Reading database ... 251653 files and directories currently installed.)
Preparing to unpack linux-image-3.14.6-031406-generic_3.14.6-031406.201406071635_amd64.deb ...
Done.
Unpacking linux-image-3.14.6-031406-generic (3.14.6-031406.201406071635) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive linux-image-3.14.6-031406-generic_3.14.6-031406.201406071635_amd64.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.14.6-031406-generic /boot/vmlinuz-3.14.6-031406-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.14.6-031406-generic /boot/vmlinuz-3.14.6-031406-generic
Selecting previously unselected package linux-headers-3.14.6-031406.
Preparing to unpack linux-headers-3.14.6-031406_3.14.6-031406.201406071635_all.deb ...
Unpacking linux-headers-3.14.6-031406 (3.14.6-031406.201406071635) ...
Selecting previously unselected package linux-headers-3.14.6-031406-generic.
Preparing to unpack linux-headers-3.14.6-031406-generic_3.14.6-031406.201406071635_amd64.deb ...
Unpacking linux-headers-3.14.6-031406-generic (3.14.6-031406.201406071635) ...
Setting up linux-headers-3.14.6-031406 (3.14.6-031406.201406071635) ...
Setting up linux-headers-3.14.6-031406-generic (3.14.6-031406.201406071635) ...
Errors were encountered while processing:
 linux-image-3.14.6-031406-generic_3.14.6-031406.201406071635_amd64.deb

```

I'm wondering if I'd have some success if I installed a different wireles card, but I don't know where to begin. I could really use a Linux pro to walk me through this if there even is a solution. Any help is greatly appreciated.

Thanks.

---

