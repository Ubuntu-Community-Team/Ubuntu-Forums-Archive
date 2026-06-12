---
title: "Problems with wired Belkin F5D5000 / Realtek RTL8139 card"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by philcsf on 2008-08-07
First, excuse me for being a complete newbie to Linux, I used it a little bit over the previous year at university, but only basic stuff. Decided it was time to get it at home, and installed the latest version of Ubuntu onto a computer I patched together from old parts. The motherboard doesn't feature an on-board Ethernet port, so there is a Belkin F5D5000 Ethernet card installed into one of the PCI sockets.

However, I am not able to connect to a network connection using Network Manager, with an Ethernet cable connected straight to the router. It displays a 'Point to Point' connection that needs configuring, but nothing is displayed in the drop-down box for Ethernet Interface, and therefore the configuration cannot be finished.

*ifconfig* shows a Local Loopback connection, but no sign of my networking card. *lspci -v* shows the Realtek ethernet controller / Belkin PCI card as being detected, so it seems to be a driver issue rather than hardware - No idea where to start with checking that, though, can't find any linux drivers on the Belkin site. Any help would be greatly apprciated.

---

### Post by loboc on 2008-08-07
can you post the output of lspci and lsmod

---

### Post by loboc on 2008-08-07
Of cousre you cant the one that youd run that command on is not on the net

---

### Post by philcsf on 2008-08-07
Of course I can, just export the text to a file, and lob it on a USB stick.

```
**$ lspci -v**

00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
	Flags: bus master, medium devsel, latency 120
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Memory at eddff000 (32-bit, prefetchable) [size=4K]
	I/O ports at dc00 [disabled] [size=4]
	Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 120
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: ede00000-efefffff
	Prefetchable memory behind bridge: d5c00000-e5cfffff

00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]

00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
	Flags: medium devsel

00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06) (prog-if 10 [OHCI])
	Flags: bus master, medium devsel, latency 16, IRQ 10
	Memory at effdf000 (32-bit, non-prefetchable) [size=4K]

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Belkin F5D5000 PCI Card/Desktop Network PCI Card
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at de00 [size=256]
	Memory at efffff00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at effe0000 [disabled] [size=64K]
	Capabilities: <access denied>

01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at efef0000 [disabled] [size=64K]
	Capabilities: <access denied>
```

```
**$ lsmod**

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
ipv6                  267780  8 
joydev                 13120  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sky2                   47492  0 
lp                     12324  0 
evdev                  13056  5 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
button                  9232  0 
amd_k7_agp              9612  1 
pcspkr                  4224  0 
i2c_amd756              7428  0 
shpchp                 34452  0 
agpgart                34760  1 amd_k7_agp
i2c_core               24832  1 i2c_amd756
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
8139cp                 24704  0 
ata_generic             8324  0 
floppy                 59588  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ohci_hcd               25348  0 
usbcore               146028  5 usb_storage,libusual,usbhid,ohci_hcd
pata_amd               14212  2 
pata_acpi               8320  0 
libata                159344  3 ata_generic,pata_amd,pata_acpi
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
```

And here's a few more outputs which could be useful, i'unno.

```
**$ ifconfig -a**

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70476 (68.8 KB)  TX bytes:70476 (68.8 KB)

**$ sudo lshw -C Network**

  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

**$ cat /etc/network/interfaces**

auto lo
iface lo inet loopback

**$ dmesg | grep 8139**

[   31.570613] 8139too Fast Ethernet driver 0.9.28
[   31.996094] 8139too: probe of 0000:00:0b.0 failed with error -16
[   32.004059] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   32.004170] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   32.004180] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
```

---

### Post by loboc on 2008-08-07
what you are looking for is to see if the module for that card was loaded. The simplest thing to do would be put another card in  it and see if it gets auto detected, if you dont have another card open a terminal and navigate you way to 

```
cd /lib/modules/2.6.24-20-generic/kernel/drivers/net
``` 

The kernel number might be different if theres more than one check which one your running with 

```
uname -r
```

in that directory type 
```
ls -l | less
``` 
to get alist of drivers theres one that should work with your card 

google the details of lspci like realtek or anything else and "kernel module"

my guess is RTL8139 is your realtek shows up in lspci

if thats it try
```

sudo modprobe 8139co

```
and 

```
sudo modprobe 8139too

```
if one of those sticks and eth0 shows up in ifconfig then rock on

if one of those modules works and it continues to fail to autload it in add the module to 

/etc/modules

if neither those work keep googling the lspci details til you find the kernel module you need

---

### Post by sendblink23 on 2008-08-07
> **philcsf said:**
> Of course I can, just export the text to a file, and lob it on a USB stick. Gimme a second to sort it all out.

You can also ...  save the Text file.. into the Hard Drive of the regular My Documents in yoru Windows ;)

---

### Post by philcsf on 2008-08-07
Tried loading 8139cp, 8139too, pppoe, sky2 and r8169, but still no luck.

> **sendblink23 said:**
> You can also ...  save the Text file.. into the Hard Drive of the regular My Documents in yoru Windows ;)

Well, I would if I was dual-booting, but I have two seperate hardware systems here ;)

---

### Post by philcsf on 2008-08-07
Okay, so I finally found a Linux kernel module for the networking card, but I need to compile it myself. Seeing as I have no internet connection, I need build-essentials and all dependancies in order to do it myself, and using the packages website is just f***ing fustrating. I've hit a brick wall, and starting to lose my sanity.... see the following screenshots, where my system has Catch 22'd itself.

[IMG]http://img99.imageshack.us/img99/4297/screenshotpackageinstaloh1.png[/IMG]

[IMG]http://img396.imageshack.us/img396/6210/screenshotpackageinstalzc7.png[/IMG]

Seriously, what am I supposed to do?

---

### Post by loboc on 2008-08-07
if you download the dependant files from packages.ubuntu.com you can install them from a flash drive using gdebi once you have them on the drive and the drive mounted double clicking should open gdebi 

the command line way to install a apackage if that fails would be 

sudo dpkg -i /media/USB/packagename.deb

There may be a lot of dependencies if you still have the cdrom you can add it to apt sources using preferences>software sources and it may have enough packages on it to get you close, I would make it the only software source so apt doesnt think there are network packages with higher versions availible

---

### Post by loboc on 2008-08-07
Here was a guy in the same boat with a wireless driver

[http://ubuntuforums.org/showthread.php?t=332402](http://ubuntuforums.org/showthread.php?t=332402)

My advice is to get the cd into apt sources as the only entry then install build-essential
Put the cd in the drive and issue
```

sudo apt-cdrom add
 
```
then sudo nano /etc/apt/sources.list and comment anything thats starts

deb http: 

to 

#deb http: 

 
```

sudo apt-get update 
sudo apt-get clean
sudo apt-get install build-essential

```
and then fill in packages using the website download and flash stick to get anything not on the cd that the build requires

---

### Post by philcsf on 2008-08-07
Okay, so I got build-essentials from the Installation CD, thanks. I still can't get it to compile, though, the makefile seems to be pointing to the wrong directory.

Coped the files to a newly created /usr/src/linux-2.6.13-15/src/ (like it says in the readme), as well as the one that was already there for my version of the kernel, and still couldn't find the file /src/Makefile_linux26x. Drivers attached, I think something needs to be edited in them.

---

### Post by chili555 on 2008-08-07
I really don't think a new driver is the answer. Before we try that, let's try a couple of other things. I saw this post, that includes the all-important word SOLVED: [http://bbs.archlinux.org/viewtopic.php?id=46583](http://bbs.archlinux.org/viewtopic.php?id=46583)

First, I suggest you blacklist the *8139cp* module. sudo gedit /etc/modprobe.d/blacklist and add a line:```
blacklist 8139cp
```Proofread, save, close and reboot. Does your ethernet work now?

If not, try the next fix. sudo gedit /boot/grub/menu.lst and amend the *very first* line that includes **boot/vmlinuz** to add the following:```
pnpbios=off pnpacpi=off
```For example, in my case, the line would be amended to read:```
/boot/vmlinuz-2.6.24-19-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro **pnpbios=off pnpacpi=off**quiet splash
```Proofread, save, close and reboot. Does your ethernet now work?

---

### Post by philcsf on 2008-08-07
What do you know, the second fix worked! ^^ Thanks a lot, mate!

---

