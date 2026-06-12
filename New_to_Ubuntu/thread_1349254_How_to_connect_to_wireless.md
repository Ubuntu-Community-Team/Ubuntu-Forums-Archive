---
title: "How to connect to wireless?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by rolando.m on 2009-12-08
I just installed Ubuntu and I can't figure out how to get online with it. I assume that it has something to do with the icon in the upper right hand corner. When I click on it I see:

Wired Network
  disconnected
VPN Connections >

How do I connect to my wireless network?

---

### Post by frenchn00b on 2009-12-08
what do you see: 

```
iwconfig

iwlist scan 

```

try [http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php) :
it works with fluxbox too 
 
```
apt-get install wicd
wicd-client 
```

---

### Post by rolando.m on 2009-12-08
When I type "iwconfig" this is what it says

lo  no wireless extensions

etho   no wireless extensions

What now?

---

### Post by frenchn00b on 2009-12-08
> **rolando.m said:**
> When I type "iwconfig" this is what it says

lo  no wireless extensions

etho   no wireless extensions

What now?

you need to install your driver for your wireless. what is your pc / hardware ? 
```
lspci -n 
```

does it says OK into this page for hardware ? [here]("http://kmuto.jp/debian/hcl/")

paste the end of your dmesg
```
$ dmesg
```
normally it says that a driver / firmware is missing 
> dmesg | less 
 
wont be difficult to get it working

---

### Post by rolando.m on 2009-12-08
I can't connect to the internet with a wired connection either so it is a bit hard to copy/paste the output.

When I connect an ethernet connection nothing seems to happen. My hardware is a HP Mini. I'm not too sure beyond that.

---

### Post by rolando.m on 2009-12-08
I copied it to a document and transfered it to this computer with a thumb drive. This is what dmesg says:

```

[    3.728698] PM: Checking hibernation image.
[    3.729129] PM: Resume from disk failed.
[    3.737508] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.737520] EXT4-fs (sda1): write access will be enabled during recovery
[    3.772814] EXT4-fs (sda1): barriers enabled
[   10.094808] kjournald2 starting: pid 373, dev sda1:8, commit interval 5 seconds
[   10.094867] EXT4-fs (sda1): delayed allocation enabled
[   10.094876] EXT4-fs: file extents enabled
[   10.115566] EXT4-fs: mballoc enabled
[   10.115599] EXT4-fs (sda1): recovery complete
[   10.116828] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   11.176867] type=1505 audit(1260201159.331:2): operation="profile_load" pid=396 name=/sbin/dhclient3
[   11.177053] type=1505 audit(1260201159.331:3): operation="profile_load" pid=396 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.177182] type=1505 audit(1260201159.331:4): operation="profile_load" pid=396 name=/usr/lib/connman/scripts/dhclient-script
[   31.659165] type=1505 audit(1260201179.812:5): operation="profile_load" pid=397 name=/usr/bin/evince
[   31.660400] type=1505 audit(1260201179.812:6): operation="profile_load" pid=397 name=/usr/bin/evince-previewer
[   31.661641] type=1505 audit(1260201179.816:7): operation="profile_load" pid=397 name=/usr/bin/evince-thumbnailer
[   32.297946] type=1505 audit(1260201180.451:8): operation="profile_load" pid=399 name=/usr/lib/cups/backend/cups-pdf
[   32.298235] type=1505 audit(1260201180.451:9): operation="profile_load" pid=399 name=/usr/sbin/cupsd
[   32.479733] type=1505 audit(1260201180.631:10): operation="profile_load" pid=400 name=/usr/sbin/tcpdump
[   33.279448] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k 
[   33.682929] udev: starting version 147
[   33.683522] EXT4-fs (sda1): internal journal on sda1:8
[   34.763691] Linux video capture interface: v2.00
[   35.052744] lp: driver loaded but no devices found
[   35.299135] uvcvideo: Found UVC 1.00 device Webcam-101 (05c8:0202)
[   35.305503] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[   35.305639] usbcore: registered new interface driver uvcvideo
[   35.305649] USB Video Class driver (v0.1.0)
[   35.329508] intel_rng: FWH not detected
[   35.429226] cfg80211: Calling CRDA to update world regulatory domain
[   36.774909] cfg80211: World regulatory domain updated:
[   36.774924] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   36.774950] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.774957] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.774964] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   36.774970] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.774977] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   36.802283] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   36.837356] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   37.238635] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   37.281152] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   37.281274] b43: probe of ssb0:0 failed with error -95
[   37.281372] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   37.341418] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.641699] type=1505 audit(1260229987.795:11): operation="profile_replace" pid=773 name=/sbin/dhclient3
[   39.642014] type=1505 audit(1260229987.795:12): operation="profile_replace" pid=773 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   39.642201] type=1505 audit(1260229987.795:13): operation="profile_replace" pid=773 name=/usr/lib/connman/scripts/dhclient-script
[   40.210745] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.210814] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   40.371362] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   40.381808] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   40.382018] input: HDA Intel Mic at Sep Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   40.382206] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   40.382390] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   42.913108] sky2 eth0: enabling interface
[   42.913739] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.379588] CPU0 attaching NULL sched-domain.
[   52.379604] CPU1 attaching NULL sched-domain.
[   52.393534] CPU0 attaching sched-domain:
[   52.393546]  domain 0: span 0-1 level SIBLING
[   52.393555]   groups: 0 1
[   52.393570] CPU1 attaching sched-domain:
[   52.393577]  domain 0: span 0-1 level SIBLING
[   52.393585]   groups: 1 0
[   63.877471] type=1505 audit(1260230012.031:14): operation="profile_replace" pid=792 name=/usr/bin/evince
[   63.879845] type=1505 audit(1260230012.031:15): operation="profile_replace" pid=792 name=/usr/bin/evince-previewer
[   63.882501] type=1505 audit(1260230012.035:16): operation="profile_replace" pid=792 name=/usr/bin/evince-thumbnailer
[   64.543885] type=1505 audit(1260230012.695:17): operation="profile_replace" pid=1218 name=/usr/lib/cups/backend/cups-pdf
[   64.544514] type=1505 audit(1260230012.699:18): operation="profile_replace" pid=1218 name=/usr/sbin/cupsd
[   64.729980] type=1505 audit(1260230012.883:19): operation="profile_replace" pid=1219 name=/usr/sbin/tcpdump
[   65.478921] ppdev: user-space parallel port driver
[   74.701018] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00af0900
[ 1533.935830] CPU0 attaching NULL sched-domain.
[ 1533.935846] CPU1 attaching NULL sched-domain.
[ 1533.945191] CPU0 attaching sched-domain:
[ 1533.945204]  domain 0: span 0-1 level SIBLING
[ 1533.945213]   groups: 0 1
[ 1533.945227]   domain 1: span 0-1 level MC
[ 1533.945235]    groups: 0-1 (__cpu_power = 2048)
[ 1533.945251] CPU1 attaching sched-domain:
[ 1533.945258]  domain 0: span 0-1 level SIBLING
[ 1533.945266]   groups: 1 0
[ 1533.945278]   domain 1: span 0-1 level MC
[ 1533.945285]    groups: 0-1 (__cpu_power = 2048)
[ 1534.662077] CPU0 attaching NULL sched-domain.
[ 1534.662090] CPU1 attaching NULL sched-domain.
[ 1534.680412] CPU0 attaching sched-domain:
[ 1534.680428]  domain 0: span 0-1 level SIBLING
[ 1534.680442]   groups: 0 1
[ 1534.680463] CPU1 attaching sched-domain:
[ 1534.680473]  domain 0: span 0-1 level SIBLING
[ 1534.680485]   groups: 1 0
[ 1556.592640] CPU0 attaching NULL sched-domain.
[ 1556.592652] CPU1 attaching NULL sched-domain.
[ 1556.608098] CPU0 attaching sched-domain:
[ 1556.608107]  domain 0: span 0-1 level SIBLING
[ 1556.608114]   groups: 0 1
[ 1556.608123]   domain 1: span 0-1 level MC
[ 1556.608129]    groups: 0-1 (__cpu_power = 2048)
[ 1556.608140] CPU1 attaching sched-domain:
[ 1556.608145]  domain 0: span 0-1 level SIBLING
[ 1556.608151]   groups: 1 0
[ 1556.608159]   domain 1: span 0-1 level MC
[ 1556.608165]    groups: 0-1 (__cpu_power = 2048)
[ 1559.620582] CPU0 attaching NULL sched-domain.
[ 1559.620601] CPU1 attaching NULL sched-domain.
[ 1559.636242] CPU0 attaching sched-domain:
[ 1559.636258]  domain 0: span 0-1 level SIBLING
[ 1559.636272]   groups: 0 1
[ 1559.636293] CPU1 attaching sched-domain:
[ 1559.636304]  domain 0: span 0-1 level SIBLING
[ 1559.636315]   groups: 1 0
[ 2724.126178] CPU0 attaching NULL sched-domain.
[ 2724.126191] CPU1 attaching NULL sched-domain.
[ 2724.164110] CPU0 attaching sched-domain:
[ 2724.164120]  domain 0: span 0-1 level SIBLING
[ 2724.164126]   groups: 0 1
[ 2724.164136]   domain 1: span 0-1 level MC
[ 2724.164142]    groups: 0-1 (__cpu_power = 2048)
[ 2724.164154] CPU1 attaching sched-domain:
[ 2724.164159]  domain 0: span 0-1 level SIBLING
[ 2724.164164]   groups: 1 0
[ 2724.164173]   domain 1: span 0-1 level MC

```

---

### Post by frenchn00b on 2009-12-08
> **rolando.m said:**
> I can't connect to the internet with a wired connection either so it is a bit hard to copy/paste the output.

When I connect an ethernet connection nothing seems to happen. My hardware is a HP Mini. I'm not too sure beyond that.

I have one too, you are lucky. I can tell you all about it.
I use debian to make it work. here is teh cdrom to get eth0 network cable working first, to install.
[http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso)

then
for the wifi, here is the link to get the eth1 working and bluetooh:
driver : [http://ubuntuforums.org/showthread.php?t=1305742&highlight=hp+mini](http://ubuntuforums.org/showthread.php?t=1305742&highlight=hp+mini)
and howto
I can post a tar.gz of the files if you want. Just : sudo sh myscript.sh 
and you get wifi :)

---

### Post by rolando.m on 2009-12-08
Thanks! 

For the .iso, since I don't have a CD drive, can I transfer it with a thumb drive? Since I'm new to Linux I'm not sure how that works.

---

### Post by rolando.m on 2009-12-08
OK, I got the Debian .iso mounted on the netbook but I'm not sure what to do with it.

---

### Post by frenchn00b on 2009-12-08
> **rolando.m said:**
> Thanks! 

For the .iso, since I don't have a CD drive, can I transfer it with a thumb drive? Since I'm new to Linux I'm not sure how that works.

nobody replies as you see:  [here]("http://www.linuxquestions.org/questions/debian-26/unetbootin-not-working-how-to-make-a-pendrive-testing-installer-netinstall-773954/") 
I installed it with an external usb drive
if you make this famous pendrive, or have time to post there. linus, the guy will help you. he is really a fan of linux and active.
 
do you have an email address?   I just made a tar.gz with the wifi installer.
I put a readme inside. PM me. The problem is cuz the file is 5mb and i havent storage on any ftp.


> 
Firmware drivers non-free

The required firmware can be determined with the following device/ firmware enumeration or by using the newly developed fw-detect script (packaged in sidux-scripts).

$ fw-detect

The output of fw-detect describes the commands needed to install and activate the firmware:

Example:

#Detected driver that requires firmware to operate
#Follow these instructions to obtain the correct firmware
# and activate the zd1211rw driver:
apt-get update
apt-get install zd1211-firmware
modprobe -r zd1211rw
modprobe zd1211rw

To install firmware from git repos, you need to:

apt-get install git-core

Should you need to prefetch firmware .debs, to put on a usb-key for example, you can download them as either a zip or tar.gz file from [http://cdimage.debian.org/cdimage/unofficial/non-free/firmware/sid/current/](http://cdimage.debian.org/cdimage/unofficial/non-free/firmware/sid/current/)

We try to provide packages for legally redistributable firmware from our non-free repositories, but not all vendors allow this.


---

### Post by JBAlaska on 2009-12-08
I think the easiest thing to do is use your other computer to navigate to this [Page](http://packages.ubuntu.com/karmic/bcmwl-kernel-source) click on the appropriate link for "Download bcmwl-kernel-source" Either x86 or AMD64 (I don't know what Atom the HP mini has N270 32-bit or 230 and 330 64-bit), choose a mirror and d/l the "bcmwl-kernel-source" deb to your thumb drive.

Copy the deb to your HP Mini and double click it to install, Reboot.

Go to System, Administration, Hardware Drivers and enable the Broadcom STA driver.

---

### Post by frenchn00b on 2009-12-08
what does say :

```
apt-cache search linux image | grep linux-image
```

you will need a kernel >=2.6.30 
as daily built debian testing
for cable eth0

or to install sky2 driver, if i recall well

making a pendrive with an installer:
[http://www.debian.org/releases/stable/i386/ch04s03.html.en#usb-copy-flexible](http://www.debian.org/releases/stable/i386/ch04s03.html.en#usb-copy-flexible)

---

### Post by Evanion on 2009-12-08
hmm im runnign a tx2590eo... 
now i can get wired connection. but my wireless wont work. 
WMware detects the hardware ... but i can seem to get it to work in ether ubuntu or win7 (via wmware)

and when i try to install the driver in the post above ... i get "Error: Dependency is not satisfiable: dkms"

need to go .. more to follow

---

### Post by frenchn00b on 2009-12-08
> **Evanion said:**
> hmm im runnign a tx2590eo... 
now i can get wired connection. but my wireless wont work. 
WMware detects the hardware ... but i can seem to get it to work in ether ubuntu or win7 (via wmware)

and when i try to install the driver in the post above ... i get "Error: Dependency is not satisfiable: dkms"

need to go .. more to follow

try ceni or wicd to get wireless workign if iwlist scan gives somethnig

---

### Post by rolando.m on 2009-12-08
> **JBAlaska said:**
> I think the easiest thing to do is use your other computer to navigate to this [Page](http://packages.ubuntu.com/karmic/bcmwl-kernel-source) click on the appropriate link for "Download bcmwl-kernel-source" Either x86 or AMD64 (I don't know what Atom the HP mini has N270 32-bit or 230 and 330 64-bit), choose a mirror and d/l the "bcmwl-kernel-source" deb to your thumb drive.

Copy the deb to your HP Mini and double click it to install, Reboot.

Go to System, Administration, Hardware Drivers and enable the Broadcom STA driver.

I tried this. I got an Error that says: Error: Dependency is not satisfiable: dkms

Any ideas?

---

### Post by rolando.m on 2009-12-08
> **frenchn00b said:**
> what does say :

```
apt-cache search linux image | grep linux-image
```

you will need a kernel >=2.6.30 
as daily built debian testing
for cable eth0



It says 2.6.31-14-generic-Linux kernel image for version 2.6.31 on x8/x86_64

---

### Post by rolando.m on 2009-12-08
> **frenchn00b said:**
> nobody replies as you see:  [here]("http://www.linuxquestions.org/questions/debian-26/unetbootin-not-working-how-to-make-a-pendrive-testing-installer-netinstall-773954/") 
I installed it with an external usb drive
if you make this famous pendrive, or have time to post there. linus, the guy will help you. he is really a fan of linux and active.
 
do you have an email address?   I just made a tar.gz with the wifi installer.
I put a readme inside. PM me. The problem is cuz the file is 5mb and i havent storage on any ftp.

I'm really confused by this. Once I make the Debian .iso bootable what am I trying to do with it? I only want the driver from it correct? I'm new to linux completely so I'm not sure how to install just the driver I need or what it's even called.

The .tar.gz file gives me an error that says tar: This does not look like a tar archive

Thanks for your help!

---

### Post by arnicainthemembrane on 2009-12-08
I just installed Intrepid on my Eeepc 1005HA and there is neither wireless nor ethernet connection. Presently the machine is dual booting winxp and ubuntu.

01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network

Thus far the drivers I've tried have failed to work, any advice?

---

### Post by rolando.m on 2009-12-08
> **JBAlaska said:**
> I think the easiest thing to do is use your other computer to navigate to this [Page](http://packages.ubuntu.com/karmic/bcmwl-kernel-source) click on the appropriate link for "Download bcmwl-kernel-source" Either x86 or AMD64 (I don't know what Atom the HP mini has N270 32-bit or 230 and 330 64-bit), choose a mirror and d/l the "bcmwl-kernel-source" deb to your thumb drive.

Copy the deb to your HP Mini and double click it to install, Reboot.

Go to System, Administration, Hardware Drivers and enable the Broadcom STA driver.


@JBAlaska OK, I figured out that I also had to install dkms before I could install the other .deb. I did that and was able to run the installer just fine. I rebooted and when I got to System, Administration, Hardware Drivers and click on activate a window comes up with a status bar that runs for a few seconds and then goes away. It still says in the Hardware Drivers window that This driver is not activated. I can't seem to activate the Broadcom STA driver...

---

### Post by rolando.m on 2009-12-09
I just wanted to follow up in case anyone has an HP Mini and is reading this that I got the install file from frenchN00b to run and it fixed my wifi problem. PM me if you need it.

---

### Post by frenchn00b on 2009-12-11
> **rolando.m said:**
> I just wanted to follow up in case anyone has an HP Mini and is reading this that I got the install file from frenchN00b to run and it fixed my wifi problem. PM me if you need it.

Hurra ! I am glad it helped you. 
I spent 1 full days to make out how to install this wifi beast, then created this file for rolando, to help him. 
rolando: what's ur kernel? 
could you post: 
> lsmod
and
> uname -a 
kernel has to be not too old, otherwise no webcam and no eth0

Beware : HP mini wifi + bluetooth is buggy
sky2 module is buggy too
one shall notify them (bug)

by the way waht about hte webcam?
Ok 

 I give you the tricK, you wont seek many hours on googling :
>    mplayer -tv device=/dev/video0  tv:// 
 
even better, how to record an avi with it?
... ;) mencoder, I have a made script for that

---

### Post by fooman on 2009-12-11
i have the hp mini 1035nr and everything except wireless worked out of box with UNR 9.10

for wireless,  all it took was to hook up the ethernet and reinstall the "bcmwl-kernel-source" package:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

been working ever since.  :D

---

### Post by Lemuel111 on 2010-01-12
I'm really struggling getting connected. I am using Ubuntu 9.10 & have tried using the Belkin wireless G+ usb adapter with no success. I bought a D-Link G122 having read in the forum that this works 'out of the box'. However on attaching it nothing happened (apart from the link light on the device itself occassionaly flashing - more than the Belkin did!). I have read different forums but the main prob is that I have no wired connection I can use. I have a cross over cable which I could attatch to my laptop which works wireless via windows xp but I don't know how to set it up. Even then I read I need the Ralink 2500 driver but when you go to sight to download it, hey presto 'page unavailable'! So I am at a total loss of what to do. So if anyone can help me get on line, with Ubuntu and wireless vial one of my adapters that would be great.:(

---

### Post by frenchn00b on 2010-01-12
> **Lemuel111 said:**
> I'm really struggling getting connected. I am using Ubuntu 9.10 & have tried using the Belkin wireless G+ usb adapter with no success. I bought a D-Link G122 having read in the forum that this works 'out of the box'. However on attaching it nothing happened (apart from the link light on the device itself occassionaly flashing - more than the Belkin did!). I have read different forums but the main prob is that I have no wired connection I can use. I have a cross over cable which I could attatch to my laptop which works wireless via windows xp but I don't know how to set it up. Even then I read I need the Ralink 2500 driver but when you go to sight to download it, hey presto 'page unavailable'! So I am at a total loss of what to do. So if anyone can help me get on line, with Ubuntu and wireless vial one of my adapters that would be great.:(

we can try to help. 
I would have choosen netgear rather than belkin. oK; 
wicd-client works?

otherwise : 
use command line: 

I do when it is open: 

```
iwconfig eth1 essid HOTPOT-MYTOWN
dhclient    # this is the key to connect

```

```
man iwconfig 
for more options
```

and it gets connected

---

### Post by Matt_Johnson on 2010-01-12
what about using ndiswrapper?

---

### Post by frenchn00b on 2010-01-13
> **Matt_Johnson said:**
> what about using ndiswrapper?

ndiswrapper is the driver for inf. windows drivers. How does it work?

the problem with kde wireless is that it is not automatic, the selection of the driver is quite complicated, and lot of drivers (including ndiswrapper ) are proposed. I can believe that for new incomers to linux + added to the complexity a large range of wireless options might be tricky ... Not easy ... well I never managed to make my kde work with wireless; I did it console based: it is simple more this way, you know what it is happening;

btw ceni (from sid) is  a console based wireless configurator but but ...
not wokring : one cannot add the key for wpa or web using middle click from mouse :(

here a link of the powerful guy : [http://manual.sidux.com/en/internet-connecting-en.htm#netcardconfig](http://manual.sidux.com/en/internet-connecting-en.htm#netcardconfig)

---

### Post by frenchn00b on 2010-01-13
I have here a sidux cool script : fw-detect, to be tried

[http://svn.berlios.de/svnroot/repos/fullstory/sidux-scripts/trunk/fw-detect](http://svn.berlios.de/svnroot/repos/fullstory/sidux-scripts/trunk/fw-detect)

---

### Post by Lemuel111 on 2010-01-13
> **frenchn00b said:**
> we can try to help. 
I would have choosen netgear rather than belkin. oK; 
wicd-client works?

otherwise : 
use command line: 

I do when it is open: 

```
iwconfig eth1 essid HOTPOT-MYTOWN
dhclient    # this is the key to connect

``````
man iwconfig 
for more options
```and it gets connected


How do see if wicd-cient works?

Thanks

---

### Post by frenchn00b on 2010-01-13
> **Lemuel111 said:**
> How do see if wicd-cient works?

Thanks

s```
udo iwlist -scan
```
if I recall well ... 
then you scan for wifi

or there is : 
wifi-radar 

or ```
ceni
``` can scan ...
 
well, other users may help

---

### Post by Lemuel111 on 2010-01-13
> **frenchn00b said:**
> s```
udo iwlist -scan
```if I recall well ... 
then you scan for wifi

or there is : 
wifi-radar 

or ```
ceni
``` can scan ...
 
well, other users may help

Tried installing udo but couldn't install all of it because of error:-
   :~$ udo iwlist -scan
  
  The program 'udo' is currently not installed.  You can install it by typing:
  
  sudo apt-get install udo
  
  udo: command not found
  
  :~$ sudo apt-get install udo
  
  Reading package lists... Done
  
  Building dependency tree       
  
  Reading state information... Done
  
  The following NEW packages will be installed
  
    udo
  
  0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
  
  Need to get 177kB of archives.
  
  After this operation, 532kB of additional disk space will be used.
  
  Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe udo 6.4.1-1
  
    Could not resolve ‘gb.archive.ubuntu.com’
  
  Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/u/udo/udo_6.4.1-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/u/udo/udo_6.4.1-1_i386.deb)  Could not resolve ‘gb.archive.ubuntu.com’
  
  E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I can't run apt-get update because I can't get on line but how do I do '--fix-missing'? Any other suggestions? 

Thanks

---

### Post by bkratz on 2010-01-13
sorry for interjecting, but I am sure he wanted you to run

sudo iwlist scan

and just misspelled some things.

I haven't read the rest of this thread and don't know what udo did or loaded.

---

### Post by Lemuel111 on 2010-01-14
> **bkratz said:**
> sorry for interjecting, but I am sure he wanted you to run

sudo iwlist scan

and just misspelled some things.

I haven't read the rest of this thread and don't know what udo did or loaded.


Did this and got 'Interface doesn't support scan' for both lo & eth0. 

Problem is I can't get conntected to internet via a cable either. Only poss option is via a crossover cable to my windows xp laptop which has internet connection but I don't know how to set it up.

---

### Post by bkratz on 2010-01-14
First of all I know nothing about the Ralink devices, but is this the address you were looking for earlier?

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by Lemuel111 on 2010-01-15
Thanks for that. I managed to download what I think is the right driver. However I am still not used to tar.gz files. I extracted and read the read me file which just totally confused being a novice. However I tried typing the first line in terminal & this is what I got:-
   sudo apt-get install tofrodos
  
  dos2unix: command not found
  
  $ sudo apt-get install tofrodos
  
  [sudo] password: 
  
  Reading package lists... Done
  
  Building dependency tree       
  
  Reading state information... Done
  
  The following NEW packages will be installed
  
    tofrodos
  
  0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
  
  Need to get 19.9kB of archives.
  
  After this operation, 81.9kB of additional disk space will be used.
  
  Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main tofrodos 1.7.8.debian.1-1
  
    Could not resolve ‘gb.archive.ubuntu.com’
  
  Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tofrodos/tofrodos_1.7.8.debian.1-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tofrodos/tofrodos_1.7.8.debian.1-1_i386.deb)  Could not resolve ‘gb.archive.ubuntu.com’
  
  E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
  
  $ dos2unix *
  
  The program 'dos2unix' is currently not installed.  You can install it by typing:
  
  sudo apt-get install tofrodos
  
  dos2unix: command not found
  
   
   THIS IS THE PROBLEM I KEEP HAVING! I try to install one of these programmes but can't because I need to be connected to aviod the above problems but I can't get conntect via a wire either apart from poss a cross over wire to my laptop but I don't know how to set it up. So I just seem to be going round in circles at the moment.


(Below is the main part of the read me file which just goes way over my head. If someone can help me get past the above hirdle would they also be able to take me step by step through the below???:-
  Build Instructions:  
  ====================
  0) $dos2unix *
        $chmod 644 *
        $chmod 755 Configure
      1) cp Makefile.x Makefile               // x is your kernel 

  2) $make
  3) $insmod rt2570.ko     # Insert driver module
  4) $ifconfig rausb0 up  # Bring up device 
  5) $dhclient rausb0  # Get network IP address
      Note: Script functionality:
    Configure       retrive linux version 
    6) ./LINUX_RACONFIG_Vx.x.x.x/bin/"Linux"/RaConfig2500 

  if lack of libstdc++.so.6, cp ./LINUX_RACONFIG_Vx.x.x.x/libstdc++.so.6 /usr/lib
    7)Edit(or add the line) in /etc/modules.conf
       alias rausb0 rt2570 

  8) Create and edit 'ifcfg-rausb0' file in /etc/sysconfig/network-script/
     DEVICE='rausb0'
     ONBOOT='yes'
     BOOTPROTO='dhcp' 
    ===============================================================================================
  CONFIGURATION:  
  ====================
  RT2500 driver can be configured via following interfaces, 
  i.e. i)RaConfig2500, ii)wireless extension,
    i) RaConfig2500 is utility for rt25usb. 

  ii)  Wireless extension usage please refer to man page of 'iwconfig', 'iwlist' and 'iwpriv'. 
       Here is definition for private command 'iwpriv')


Thanks in advance.

---

### Post by Lemuel111 on 2010-01-25
I've managed to get connected via an ethernet cable, I've downloaded wicd, got the downloads for RT2500 for the D-link G122 usb wireless adapter via synaptic & got all my updates through update manager BUT still can't get the wireless to connect! Any suggestions??

---

### Post by Lemuel111 on 2010-01-27
I found this website[COLOR=#1F497D][/COLOR]
[http://anirudhs.chaosnet.org/blog/2005.10.23.html](http://anirudhs.chaosnet.org/blog/2005.10.23.html)

 It looks as though this might solve the problem however being new to Linux I don't know how to do what is suggested. It all looks very confusing to me. Would anyone be able to take me through it step by step in really simple terms?? That would be really appreciated. Thanks. 

   [COLOR=#1F497D][URL="http://anirudhs.chaosnet.org/blog/2005.10.23.html"]
[/URL][/COLOR]

[COLOR=#1F497D][/COLOR]

---

### Post by Lemuel111 on 2010-02-02
Surely someone out there would be willing to help me! I'm want to be free of Windows but I've been trying to get help for over a week & still no one responds. Please can some one help guide a beginner to linux through this. Thanks.

---

### Post by Lemuel111 on 2010-02-03
I've downloaded the driver but when I carry out the 1st instruction in the read me file:-
tar -xvzf rt73-cvs-daily.tar.gz

This is what I get:-
tar: rt73-cvs-daily.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Any suggestions???

---

