---
title: "Ethernet Drivers?"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by mdigitale on 2007-12-27
Hello Friends,

  I just purchased a new Compaq Presario (SR5130NX) 2.0GHz AMD Athlon 64 X2 Dual-Core Processor 3800+ to replace my 8 year old, trusty 800MHz dinosaur :]  This system came pre-installed with Windows Vista Home (yuck!!) so the first thing I did was format the drive and attempt to install Ubuntu 6.06 LTS from CD.

  I've re-installed Ubuntu several times with my old system and never encountered any problems -- this new system has thus far proven to prefer a more "adventurous" approach.  First I was having problems with APIC Timer/panic errors -- something that seems to plague a lot of systems using multiple cores.  Appending "noapic" to the boot command appears to have resolved that problem :)

  However, the system in it's current state does NOT recognize my Ethernet card (integrated with the system board).  My old system uses a PCI 3Com card and this was always automatically detected.  My chipset is GeForce 6150SE nForce 430 -- and it appears that Nvidia has published drivers (and source) for their LAN products for this board, however they are not targeted for Ubuntu, but rather Fedora and other varieties of Linux.

  I'm a relatively new Linux user, but I love it and would really like to keep using it on this new computer.  How does one go about installing "drivers" on Linux?  I guess I've always been spoiled with Ubuntu setting everything up for me so I don't even know where to begin.

  Any advice would be very much appreciated.

Thanks guys!

Mike

PS.  I'm using 32-bit Ubuntu.

---

### Post by chewearn on 2007-12-27
> **mdigitale said:**
> Hello Friends,

  I just purchased a new Compaq Presario (SR5130NX) 2.0GHz AMD Athlon 64 X2 Dual-Core Processor 3800+ to replace my 8 year old, trusty 800MHz dinosaur :]  This system came pre-installed with Windows Vista Home (yuck!!) so the first thing I did was format the drive and attempt to install Ubuntu 6.06 LTS from CD.

  I've re-installed Ubuntu several times with my old system and never encountered any problems -- this new system has thus far proven to prefer a more "adventurous" approach.  First I was having problems with APIC Timer/panic errors -- something that seems to plague a lot of systems using multiple cores.  Appending "noapic" to the boot command appears to have resolved that problem :)

  However, the system in it's current state does NOT recognize my Ethernet card (integrated with the system board).  My old system uses a PCI 3Com card and this was always automatically detected.  My chipset is GeForce 6150SE nForce 430 -- and it appears that Nvidia has published drivers (and source) for their LAN products for this board, however they are not targeted for Ubuntu, but rather Fedora and other varieties of Linux.

  I'm a relatively new Linux user, but I love it and would really like to keep using it on this new computer.  How does one go about installing "drivers" on Linux?  I guess I've always been spoiled with Ubuntu setting everything up for me so I don't even know where to begin.

  Any advice would be very much appreciated.

Thanks guys!

Mike

PS.  I'm using 32-bit Ubuntu.

I have a set-up similar to yours (GeForce 6150 nForce 4, AMD X2 64 3800+; it's not Compaq, but I never have the problems you described).

Try:
```
dmesg | grep eth
```

See what's going on with the ethernet hardware.

---

### Post by mdigitale on 2007-12-27
> **AstalaVista said:**
> I have a set-up similar to yours (GeForce 6150 nForce 4, AMD X2 64 3800+; it's not Compaq, but I never have the problems you described).

It's great to know that others are having success with similiar equipment :]

> **AstalaVista said:**
> 
Try:
```
dmesg | grep eth
```

See what's going on with the ethernet hardware.

I executed that command and received the following:
[17179580.388000] Driver 'sd' needs updating - please use bus_type methods

I'm not sure what that means but plan to do some Google searching.  Thanks for the help, Astalavista!

---

### Post by mdigitale on 2007-12-27
Well the results from the dmesg command were able to score me some hits on Google -- apparently the message I received is quite common amongst a wide array of hardware devices.  Probably the most interesting match was from another thread here on UbuntuForums:

[http://ubuntuforums.org/showthread.php?t=253876](http://ubuntuforums.org/showthread.php?t=253876)

The problem that guy was having sounds very similar to what I am experiencing.  Anyways, I thought I would run the commands he was advised to run and post the output in hopes that someone might be able to make sense of it and point me in the right direction :]

```
$ lspci
```
0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea(rev a1)
0000:00:01.0  ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
0000:00:01.1  SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
0000:00:01.2  RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a3)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1)
0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
0000:00:06:0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2)
0000:00:07.0 Bridge: nVidia Corporation:Unknown device 03ef (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)
0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d0 (rev a2)
0000.00.18.0 Host bridge: Advanced Micro Devices [AMD] K8 
[Athlon64/Opteron] Hyper-Transport Technology Configuration
0000.00.18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000.00.18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000.00.18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:0a.0 Communication controller: Conexant HSF 56K Data/Fax Modem

```
$ sudo lsmod
```
Module                                 Size                              Used by
ipv6                                   265728                           6
rfcomm                             40216                             0
l2cap                                26244                             5 rfcomm
bluetooth                         49892                             4 rfcomm,l2cap
ppdev                              9220                               0
powernow_k8                 12680                              0
cpufreq_userspace         4696                              1
cpufreq_stats                 5636                               0
freq_table                      4740                               2  powernow_k8,cpufreq_stats
cpufreq_powersave      1920                               0
cpufreq_ondemand       6428                              0
cpufreq_conservative 7332                                0
video                            16260                             0
tc1100_wmi                  6916                              0
sony_acpi                      5644                             0
pcc_acpi                      12416                             0
hotkey                         11556                            0
dev_acpi                      11140                           0
container                     4608                             0
button                         6672                             0
acpi_sbs                      19980                          0
battery                       9988                            1 acpi_sbs
i2c_acpi_ec                5120                             1 acpi_sbs
ac                               5252                             1 acpi_sbs
af_packet                  22920                            0
dm_mod                    58936                             1
md_mod                    72532                             0
parport_pc                35780                             0
lp                              11844                             0
parport                     36296                            3 ppdev,parport_pc,lp
tsdev                        8000                             0
serio_raw                 7300                             0
nvidia                        4550772                      0
agpgart                     34888                          1 nvidia
pcspkr                       2180                             0
psmouse                   36100                           0
rtc                             13492                           0
i2c_core                    21904                           2 I2C_acpi_ec, nvidia
shpchp                      45632                           0
pci_hotplug               29236                           1 shpchp
sg                             37920                           0
evdev                       9856                             1
ext3                         135688                          1
jbd                            58772                           1 ext3
usb_storage             74176                           0
ide_generic               1536                            0
ehci_hcd                   34184                          0
ohci_hcd                   21892                          0
usbcore                    130692                        4 usb_storage,ehci_hcd,ohci_hcd
sr_mod                     16932                          0
cdrom                       38560                         1 sr_mod
sd_mod                     19984                        3
generic                      5124                          0
sata_nv                     9732                          6
libata                         78992                        1 sata_nv
scsi_mod                   139496                      5 sg,usb_storage,sr_mod, sd_mod, libata
thermal                      13576                       0
processor                  23360                       2 powernow_k8, thermal
fan                             4868                        0
capability                  5000                         0
commoncap              7296                        1 capability
vga16fb                   13704                      1 
vgastate                  10368                      1 vga16fb
fbcon                       42784                      72
tileblit                       2816                       1 fbcon
font                          8320                       1 fbcon
bitblit                        6272                       1 fbcon
softcursor                2304                        1 bitblit

```
$ sudo ifconfig -a
```
lo              Link encap: Local Loopback
                 inet addr:127.0.0.1       Mask: 255.0.0.0
                 inet6 addr: :: 1/;128   Scope: Host
                 UP LOOPBACK RUNNING    MTU:16436  Metric: 1
                 RX packets: 561 erros:0 dropped: 0 overruns:0 frame:0
                TX packets: 561 errors:0 dropped:0 overruns:0 carrier:0
                 collisions: 0  txqueuelen:0
                RX bytes:28072 (27.4 KiB) TX bytes:28072(27.4KiB)

sit0           Link encap:IPv6-in-IPv4
                 NOARP MTU:1480  Metric:1
                 RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
                 TX packets:0  errors: 0 dropped: 0 overruns: 0  carrier:0
                 collisions:0 txqueuelen:0
                 RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)

```
$ sudo cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



The thing I find interesting about the following command is the reference to 'forcedeth'  -- on nVidias website they provide the source and binaries for their Ethernet cards, but they are all targeted  for other Linux packages (RedHat, Suse, etc.) -- no Ubuntu.  However, the source files for their Ethernet driver is named forcedeth.c

```
$ sudo modprobe forcedeth
$ sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
Forinfo, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while geting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device



Hopefully someone out there can make sense of this.   Any suggestions/expertise is appreciated!!!

Thanks,
Mike

---

### Post by chewearn on 2007-12-27
The thing is, when I issue "dmesg | grep eth", I got several messages about eth0 being detected, initialized, and kernel driver used.

Since your output does not have anything, I suspect something wrong at lower level; either there is no kernel driver (which is unlikely), the hardware is faulty, or the hardware is turned off.

Have you check the BIOS, see if the ethernet port is enabled?  Are you still able to boot into Windows?  You might be able to check whether the hardware is functioning in Windows.

---

### Post by him610 on 2007-12-27
If you can get a copy of 64-bit Ubuntu 7.10, try that instead of a 32-bit version. 
I initially attempted to install a 32-bit version, reasoning that driver support would probably be better; however, it would not install on my system with a similar configuration as yours.
Then I tried the 64-bit version and had the pleasure of the smoothest, trouble-free installation experience of an operating system yet. Version 7.10 will guide you through the download of the restricted drivers installation process which you probably need for the Nvidia chipset.

Cheers!

---

### Post by mdigitale on 2007-12-28
> **AstalaVista said:**
> The thing is, when I issue "dmesg | grep eth", I got several messages about eth0 being detected, initialized, and kernel driver used.

Since your output does not have anything, I suspect something wrong at lower level; either there is no kernel driver (which is unlikely), the hardware is faulty, or the hardware is turned off.

Have you check the BIOS, see if the ethernet port is enabled?  Are you still able to boot into Windows?  You might be able to check whether the hardware is functioning in Windows.

Thanks again for your reply.  I did install a copy of XP Pro and (after installing the Chipset drivers from nVidia) I was able to use the Ethernet connection.  I think I'll try installing a newer version (7.x) of Ubuntu once I get back to a broadband internet connection next month :)

Thanks again for your suggestions and help!

Mike

---

### Post by mdigitale on 2007-12-28
> **hgh9mrp said:**
> If you can get a copy of 64-bit Ubuntu 7.10, try that instead of a 32-bit version. 
I initially attempted to install a 32-bit version, reasoning that driver support would probably be better; however, it would not install on my system with a similar configuration as yours.
Then I tried the 64-bit version and had the pleasure of the smoothest, trouble-free installation experience of an operating system yet. Version 7.10 will guide you through the download of the restricted drivers installation process which you probably need for the Nvidia chipset.

Cheers!

Thanks for the suggestion about trying 64-bit 7.10.  I probably should have taken the hint when I encountered all the timer/panic errors trying to install the 32bit version :P  It's great to hear that you had success with 64-bit -- I'm feeling confident that it will probably also work for me.

Thanks again for your suggestion!

Mike

---

