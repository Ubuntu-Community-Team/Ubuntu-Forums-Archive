---
title: "Realtek RTL8102EL LAN / RTL8101E / r8169 - no network access"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by kogz on 2008-06-28
Hello,

I have bought Intel Atom based motherboard - D945GCLF.

It has **RTL8102EL **ethernet controller installed in a fact.
*lspci -nn* says that it has: **RTL8101E**

I have installed Ubuntu Server 8.04.1 from daily snapshots... My network doesn't work.. It seems like controller works, link is up, but I can't access any network.... :/

I see that **r8169 **kernel module is used.. I heard it has lots of bugs... Is it true? What can I do?

My kernel version: **2.6.24-19-server**

Thanks for any suggestions!

K.

---

### Post by kogz on 2008-07-01
Today Intel has hosted new driver for this controller. Hope it will work.

[r8101-1.006.00r1.zip](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2916&DwnldID=16242&lang=eng)

---

### Post by missilesilo on 2008-07-05
Were you able to use that driver? I get this when I try to compile it:

```
root@david-nettop:/usr/src/linux-headers-2.6.24-19# cd /home/david/Desktop/r8101-1.006.00
root@david-nettop:/home/david/Desktop/r8101-1.006.00# ls
Makefile  readme  release_note.txt  src
root@david-nettop:/home/david/Desktop/r8101-1.006.00# make clean modules
make -C src/ clean
make[1]: Entering directory `/home/david/Desktop/r8101-1.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/david/Desktop/r8101-1.006.00/src'
make -C src/ modules
make[1]: Entering directory `/home/david/Desktop/r8101-1.006.00/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/david/Desktop/r8101-1.006.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/david/Desktop/r8101-1.006.00/src/r8101_n.o
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c: In function ‘rtl8101_init_board’:
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:2193: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c: In function ‘rtl8101_init_one’:
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:2552: error: ‘struct net_device’ has no member named ‘poll’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:2553: error: ‘struct net_device’ has no member named ‘weight’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c: In function ‘rtl8101_rx_interrupt’:
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3601: error: ‘struct net_device’ has no member named ‘quota’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3601: warning: type defaults to ‘int’ in declaration of ‘_y’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3601: error: ‘struct net_device’ has no member named ‘quota’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3601: warning: comparison of distinct pointer types lacks a cast
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c: In function ‘rtl8101_interrupt’:
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3781: error: too few arguments to function ‘netif_rx_schedule_prep’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3782: error: too few arguments to function ‘__netif_rx_schedule’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c: In function ‘rtl8101_poll’:
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3828: error: ‘struct net_device’ has no member named ‘quota’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3828: warning: type defaults to ‘int’ in declaration of ‘_y’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3828: error: ‘struct net_device’ has no member named ‘quota’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3836: error: ‘struct net_device’ has no member named ‘quota’
/home/david/Desktop/r8101-1.006.00/src/r8101_n.c:3839: error: too few arguments to function ‘netif_rx_complete’
make[3]: *** [/home/david/Desktop/r8101-1.006.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/david/Desktop/r8101-1.006.00/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/david/Desktop/r8101-1.006.00/src'
make: *** [modules] Error 2
root@david-nettop:/home/david/Desktop/r8101-1.006.00# 
```

---

### Post by kogz on 2008-07-06
> **missilesilo said:**
> Were you able to use that driver? I get this when I try to compile it:
...


Hi, 'unfortunately' I haven't checked this driver.

OK guys. I have just solved a problem. It was simple. Don't know why but snapshot version of Ubuntu Server 8.04.1 had **ufw** firewall enabled by default. It caused network paralysed.

Official release has this feature turned off by default.

---

### Post by kogz on 2008-07-06
Damn.. Actually it's half-solved..

When I power on machine, ubuntu boots, after boot network still doesn't work.
After **shutdown -h now** and power on again it still doesn't work.

**BUT **after restart operating system by **shutdown -r now** command IT WORKS!

WTF? I'm a little confused.. :/ Dunno what to do..

---

### Post by kogz on 2008-07-06
OK. Just found something!

Made some diagnostics and found some differences! Take a look!

**sudo lshw -C network** when network **works **properly:
```

  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:45:26:66
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.13 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

**sudo lshw -C network** when network **doesn't work** properly:
```

  *-generic
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: ff
       serial: 00:1c:c0:45:26:66
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s

```

But can't see any serious differences in **sudo dmesg** output in **both **cases:
```

[   31.213018] r8169 Gigabit Ethernet driver 2.2LK loaded
[   31.213069] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   31.213102] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   31.213122] r8169 0000:01:00.0: unknown MAC (27a00000)
[   31.213729] eth0: RTL8169 at 0xf8844000, 00:1c:c0:45:26:66, XID 24a00000 IRQ 220
...
[   41.098156] r8169: eth0: link up
[   41.098169] r8169: eth0: link up

```
What to do? What to do? :)

---

### Post by ecosprog on 2008-07-07
Hmmmmm.......  Just bought this same board which should arrive here today or tomorrow. I was looking a putting the desktop version of Hardy on the system, but had also considered the server version.

At the moment I haven´t got any suggestions but once the board is here and up and running I´ll let you know what I find. 

This is going to be my main computer and will replace a badly failing IBM T30 notebook so it needs to pretty much work out of the box. Can´t live without a computer for very long.

As said, once I´m up and running I´ll let you know what happens with the NIC.

---

### Post by kogz on 2008-07-07
[Finally found soulution!](http://ubuntuforums.org/showpost.php?p=4210510&postcount=6)

Now it works perfectly. I hope it'll be fixed by ubuntu kernel team someday.

---

### Post by TheDemonHell on 2008-07-13
Could you help a newbie install this? I don't understand how the fix works.

---

### Post by kogz on 2008-07-14
1. Download r8101 driver from Realtek official site - [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)
2. Apply hardy patch - [http://www.alessiotreglia.com/wp-content/uploads/r8101-1.007.00.hardy.diff.txt](http://www.alessiotreglia.com/wp-content/uploads/r8101-1.007.00.hardy.diff.txt)
3. Read README and do as it says.
4. Deactivate r8169 driver:

```
mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old
depmod -a
```

5. Rebuild initrd.img

```
mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old mkinitramfs -o /boot/initrd.img-`uname -r`
```

6. Reboot

---

### Post by qarmig on 2008-07-15
As luck would have it (and Murphy's Law predicts) this did not work for me. I have the D945GCLF with an RTL8102LE (with the usual problems mentioned above) but I also have an ethernet card in the spare PCI slot, which has - guess what... - the RTL8169! So I actually need both the r8101 and the r8169 drivers to work :(

Your solution kogz disables the r8169 in favor of the r8101. If I re-enabled the r8169 after taking the steps mentioned above (and confirming that the r8101 works), ubuntu once again preferred the r8169 driver for both cards. I tried several times to force r8101 though the udev rules but it didn't work. Finally, I came to the following solution to have both drivers enabled:

A. Take ALL the steps mentioned above. It is especially important to disable the r8169 driver and make the initrd.img without it, otherwise the following will not work.

B. Re-enable the r8169 driver.

```
mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko
depmod -a
```

C. blacklist the r8169 driver and add it to /etc/modules

```
echo "blacklist r8169" >> /etc/modprobe.d/blacklist-network
echo "r8169" >> /etc/modules
```

D. Reboot

Now the r8101 is loaded first and assigned to eth0, and the r8169 is enabled later and is assigned to eth1. I have read some other solutions that mention rebuilding a patched version of the r8169 driver that ignores the problematic card (I don't remember the link) - which is the proper solution BTW - but I'll leave that to the kernel devs....

---

### Post by kogz on 2008-07-30
Intel hes just released new BIOS (I haven't tested it yet):
[http://downloadmirror.intel.com/16609/ENG/LF_0095_ReleaseNotes.pdf](http://downloadmirror.intel.com/16609/ENG/LF_0095_ReleaseNotes.pdf)

> PRODUCTS: D945GCLF (Standard BIOS)
BIOS Version 0095

About This Release:
&#8226; July 24, 2008
&#8226; LF94510J.86A.0095.2008.0723.2334
&#8226; VBIOS info: Build Number: 1374 PC 14.12 08/28/2006 16:30:16
&#8226; PXE info: Realtek* RTL8111B/8111C/8101E/8102E Ethernet Controller v2.171 (080703)

New Fixes/Features:
&#8226; Removed support for the PNP DMI interface.
&#8226; Fixed SMBios data mismatched.
&#8226; Fixed issue where front panel LED remains yellow instead of green after system wake from S1 with USB devices.
&#8226; Fixed issue where "Memory Size Decrease" event has incorrect event count.
&#8226; Fixed S3 resume time more than 2 seconds when accessing verb table 2.
**&#8226; Fixed issue with Wake on LAN.**
&#8226; Hid 667MHz option in Memory Configuration page.
&#8226; Fixed issue where keys pressed in POST are visible after boot in the BIOS Data Area (BDA) keyboard buffer.
&#8226; Updated processor support.
&#8226; Added workaround for issue where &#8220;Power surge on hub port&#8221; message appears intermittently.
&#8226; Updated Chassis Type SMBIOS structure.
&#8226; Fixed issue where Express BIOS Update allowed custom BIOS to be loaded over standard BIOS and vice versa.
&#8226; Fixed an issue where an error would occur when running Express BIOS Update after running iflashwin.
&#8226; Fixed issue where language display in BIOS setup does not change as per language selected.
&#8226; Added 800x480 video resolution support.
**_&#8226; Updated Realtek* PXE ROM for 8111C Gigabit LAN support._**
&#8226; Fixed BIOS setup page showing wrong LAN MAC address.
&#8226; Changed BIOS to check the first 12 characters of the old and new BIOS ID in recovery path instead of 8 characters.

Well.. Does D945GCLF's Ethernet controller work in gigabit speed from now?

---

### Post by DocWu on 2008-07-31
I've had the same problem with the NIC on the G945GCLF board. Sometimes the NIC would not be recognized, other times it would work fine.

I just loaded the new BIOS firmware. Time will tell if that fixes it. I'm keeping my fingers crossed.

---

### Post by kogz on 2008-07-31
I've just done an upgrade of last ubuntu-server kernel, and BIOS.

Ethtool says that gigabit speed is still not supported. Anyone can confirm?

---

### Post by kogz on 2008-08-05
> **kogz said:**
> Intel hes just released new BIOS (I haven't tested it yet):
[http://downloadmirror.intel.com/16609/ENG/LF_0095_ReleaseNotes.pdf](http://downloadmirror.intel.com/16609/ENG/LF_0095_ReleaseNotes.pdf)

Well.. Does D945GCLF's Ethernet controller work in gigabit speed from now?

Another BIOS update available: [http://downloadmirror.intel.com/16676/ENG/LF_0099_ReleaseNotes.pdf](http://downloadmirror.intel.com/16676/ENG/LF_0099_ReleaseNotes.pdf)

---

