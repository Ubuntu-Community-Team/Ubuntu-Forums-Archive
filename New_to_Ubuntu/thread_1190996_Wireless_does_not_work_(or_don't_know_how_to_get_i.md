---
title: "Wireless does not work (or don't know how to get it to work) on Samsung N120"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by yume00 on 2009-06-18
Hi,

I'm new to Ubuntu, and I got a new Samsung N120 (it is cool, btw), and heard about UNR somehow. So I downloaded UNR 9.04 into a 8GB USB key and ran it as live image.

It took about 2 minutes to load, and I ended up with a nice interface. However, I just can't get wireless to work. When I right click on the wireless icon on the top right hand corner, I only got "Wired Connection", and VPN Connections. I left click on it, and then went to add a connection under the wireless tab in the network manager. I put in the SSID, WPA info etc (shouldn't I be able to see the SSID from the broadcast anyway?), hit apply. The entry is there, but still nothing happened.

I'm suspecting there might be something wrong with the wireless driver. But I have no idea how to check or verify. Any help would be appreciated!

Before anyone asks, yes, wireless works perfectly in Windows XP. :)

Thanks.

---

### Post by Idefix82 on 2009-06-18
Welcome! Not sure what UNR is but I will just assume that it's Ubuntu. Can you open the terminal, type in
```
lshw -C network
```
and paste the output here? It will show the make of your wireless card and the driver that is currently loaded for it.

---

### Post by yume00 on 2009-06-18
By UNR I meant Ubuntu Netbook Remix. Sorry I was too lazy. :P

It took me a little while to find out where to get a terminal. :P But here is the output. Thanks!
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fb:9a:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:96:0c:54:54:79
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fb:9a:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:96:0c:54:54:79
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Idefix82 on 2009-06-18
Can you also give us the output from
```
lspci
```

---

### Post by yume00 on 2009-06-18
I saw this in the wireless and networking forum, so I just run the whole thing. Hope that would help (and also saves me a few reboots :P)

1 ) Machine Brand and Model (PC/Laptop):
Samsung N120

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)


$ lsusb

Bus 001 Device 005: ID 0ac8:c335 Z-Star Microelectronics Corp. 
Bus 001 Device 003: ID 1516:8628 CompUSA 128M Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3 ) check interface:
Code:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:77:fb:9a:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ iwconfig


(hint) if the Wireless interface name is wlan0 you can also use
Code:

$ iwconfig wlan0

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


4 ) Check for modules:
Code:

$ lsmod

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   65540  3 
drm                    96296  4 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
btusb                  19608  2 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25360  0 
intel_agp              34108  1 
output                 11008  1 video
soundcore              15200  1 snd
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usbhid                 42336  0 
usb_storage            82880  1 
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


5 ) Kernel boot messages
Code:

$ dmesg

.....

[   60.872809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   60.872819] Bluetooth: BNEP filters: protocol multicast
[   60.918990] Bridge firewalling registered
[   62.440698] lp: driver loaded but no devices found
[   62.459802] ppdev: user-space parallel port driver
[   63.733986] [drm] Initialized drm 1.1.0 20060810
[   63.757339] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   63.757352] pci 0000:00:02.0: setting latency timer to 64
[   63.757710] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   63.770167] [drm:i915_setparam] *ERROR* unknown parameter 4
[   63.770240] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   64.970973] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   66.033879] sky2 eth0: enabling interface
[   66.034432] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.147372] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   76.379009] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  210.600697] Monitor-Mwait will be used to enter C-2 state
[  210.619539] Marking TSC unstable due to TSC halts in idle


6 ) Network configuration
Code:

$ sudo lshw -C network

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fb:9a:d2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:64:4a:6a:a8:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


7 ) Scan for networks:
Code:

$ iwlist scan

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


8 ) Ubuntu Version:
Code:

$ lsb_release -d

ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

ubuntu@ubuntu:~$ -uname -mr
bash: -uname: command not found


10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart

ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

Edit: I went into Windows system manager and check, the wireless card is Realtek 8192E 802.11n wireless card.

---

### Post by yume00 on 2009-06-19
*bump*

(Or can a mod please move it to wireless / networking forum please?)

---

### Post by Idefix82 on 2009-06-19
I haven't found anybody who has confirmed that he got this card to work under Linux so we will need to experiment a bit. Do you know if your Ubuntu is 32 or 64 bit? To find out, type in the terminal
```
uname -a
```
and paste the output here.

Meanwhile, find your windows wireless driver. Let's hope that it's an archive that you can extract (it might be an .exe file but still be an archive, try unpacking it with WinZip). If you managed to do that then find a .inf and a .sys file that correspond exactly to your wireless card and copy both of them somewhere on the hard drive, where you can access them from within Ubuntu.

Let us know when you have done all that and we will see whether we can get your card to work using ndiswrapper.

By the way, there's no need to open two forums about the same topic.

---

### Post by smallrock on 2009-06-20
Hi. I got wifi working on Samsung n120 with Ubuntu 9.04 Jaunty UNR by using Ndiswrapper. Just install ndiswrapper with Synaptic, download Windows XP driver for Samsung n120 wifi card Realtek 8192 (samsung webpage) and unpack it, and then just find net819xp.inf file with ndiswrapper and it should work (off course you need to set up your wifi functions like ssid, password etc.) Ndiswrapper may say that it couldn't find the device, but it works.
Good luck.

---

### Post by Baeser55110 on 2009-08-04
> **smallrock said:**
> Hi. I got wifi working on Samsung n120 with Ubuntu 9.04 Jaunty UNR by using Ndiswrapper. Just install ndiswrapper with Synaptic, download Windows XP driver for Samsung n120 wifi card Realtek 8192 (samsung webpage) and unpack it, and then just find net819xp.inf file with ndiswrapper and it should work (off course you need to set up your wifi functions like ssid, password etc.) Ndiswrapper may say that it couldn't find the device, but it works.
Good luck.

I have the same wifi card, but on a Toshiba U500, will the driver work the same?  Thanks.

Bae

---

### Post by LewRockwell on 2009-08-05
> **Baeser55110 said:**
> I have the same wifi card, but on a Toshiba U500, will the driver work the same?  Thanks.

Bae

most of the guts on those netbooks are from the same primary source

that RTL8192 wifi unit seems to the newest device we've got to conquer

I'd follow the same procedures as found above and test it out

just remember what you do so that you can undo it later if necessary

.

---

### Post by gead on 2009-08-18
I have a Toshiba T500-119 with RTL8192SE Wifi card.
This card is not automatically recognised by Ubuntu 9.04.
I tried Vista Driver using ndiswrapper but didn't managed to get it work.

However while using Win2K driver it worked successfully

The procedure to be followed is detailed below:

Initially I have the following:
iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     no wireless extensions.

lspci | grep -i net

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Procedure:
1- Download the driver using the following thread: [http://www.station-drivers.com/telec...ivers.com).exe]("http://www.station-drivers.com/telechargement/realtek/wifi/rtl-8191se_1080.7.0520%28www.station-drivers.com%29.exe")

2- Use Wine to extract it in <Your Directory>.

3- Install ndiswrapper if not available (I didn't do it because already available as per 9.04)

4- Load the driver:

cd <Your Directory>
sudo ndiswrapper -i ./91_92_SE_Driver/Win2K/net8192se.inf

5- Check that driver was successfully loaded:

ndiswrapper -l

net8192se : driver installed
        device (10EC:8172) present

6- Create a module to load it in the linux kernel. This module will be created from Windows driver:

sudo ndiswrapper -m

7- Load dynamically the created module in the kernel:

sudo modprobe ndiswrapper

At this step and if the procedurre succeded we should have a valid interface eth1 or wlan0. This Can be checked using iwconfig command.

8- Finallty load automatically ndiswrapper at boot system:

echo "ndiswrapper"|sudo tee -a /etc/modules

With the above steps RTL8192SE should work successfully on Ubuntu 9.04

---

### Post by lotharmat on 2009-09-05
Does any one think that this card will work natively with Karmic?

---

### Post by aidanjt on 2009-09-05
> **lotharmat said:**
> Does any one think that this card will work natively with Karmic?

It wont.  The native driver code was stripped out of the rtl8191su driver as of the current git snapshot of Linux 2.6.31.  Someone is probably working on giving it a driver of it's own, which make sense.

---

### Post by Sweevo on 2009-09-06
You could try following my steps, detailed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126")

I know that they are for a different netbook, but the WLAN looks like it's the same to me.

---

### Post by MrPerfect72 on 2009-10-08
Advanced users of Linux can use an XP driver from the Samsung CD "System Software Media" or download from the manufacturers site and install it on your computer using ndiswrapper. Just use the normal LAN until WLAN is working! :-) My Samsung N120 works fine with Ubuntu now.

I really recommend a clean install of Ubuntu. It is true liberty.:) I might come back with a more detailed description soon.

---

### Post by mariogiov on 2009-10-16
The new (mainline) kernel at [[COLOR="Blue"]kernel.org[/COLOR]]("http://kernel.org") includes staging drivers for all variations of this card (rtl8192e, se, and u), kindly developed by (I believe) Greg Kroah-Hartman/the hard-working folks at the [[COLOR="Blue"]Linux Driver Project[/COLOR]]("http://www.linuxdriverproject.org").

As of this writing (10.16.2009), the current mainline kernel source is 2.6.32-rc5. Compiling the kernel is not too hard and there are a number of helpful [[COLOR="Blue"]guides[/COLOR]]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") available online. Make sure you select the appropriate drivers when doing your configuration! Compilation takes a while and you don't want to wait an hour to find out you didn't include the drivers you need.

---

### Post by npallett on 2009-10-22
> **LewRockwell said:**
> most of the guts on those netbooks are from the same primary source

that RTL8192 wifi unit seems to the newest device we've got to conquer

I'd follow the same procedures as found above and test it out

just remember what you do so that you can undo it later if necessary

.


You need to download and install the native Linux Realtek 8192Se 32Bit or 64Bit driver from the following locations

for the 64Bit version:

[http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

for the 32Bit version:

[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)

These drivers work with Jaunty's 2.6.28 kernels


Youl'll need to compile the drivers, so make sure you do:

sudo apt-get install build-essential

This will ensure you have the right tools installed for compilation.

Good Luck.

---

### Post by lotharmat on 2009-10-24
is the 8192SE the same as the 8192E?

---

### Post by northd_tech on 2009-11-24
> **lotharmat said:**
> is the 8192SE the same as the 8192E?

I wouldn't count on it- the 64-bit sourcecode linked by npallett above was throwing many error messages at me earlier today.  (Ultimate Ubuntu 2.4 64-bit based upon 9.10 Karmic Koala ubuntu).

I haven't been able to get the 64-bit Windows drivers to work either under ndiswrapper (but the 32-bit stuff worked great on the older Ultimate Ubuntu 2.3 / Jackalope 9.04).

More info here:

[http://ubuntuforums.org/showpost.php?p=8381379&postcount=26](http://ubuntuforums.org/showpost.php?p=8381379&postcount=26)

[http://ubuntuforums.org/showthread.php?t=1227061](http://ubuntuforums.org/showthread.php?t=1227061)

[http://ubuntuforums.org/showpost.php?p=8348344&postcount=15](http://ubuntuforums.org/showpost.php?p=8348344&postcount=15)

EDIT:  Someone (chili555) got it to compile on the same 2.6.31 kernel that I've been attempting with on this thread:

 [NOTE:  I believe that this was successful for a 32-bit ubuntu for the 8192SE (which is apparently different sourcecode than is needed by the 8192E Realtek PCI interface that I'm trying to fix for wlan0). [http://ubuntuforums.org/showpost.php?p=8335065&postcount=2](http://ubuntuforums.org/showpost.php?p=8335065&postcount=2)

---

