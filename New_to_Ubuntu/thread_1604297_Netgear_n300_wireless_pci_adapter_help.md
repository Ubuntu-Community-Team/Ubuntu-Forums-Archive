---
title: "Netgear n300 wireless pci adapter help"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by crazy8rgood on 2010-10-23
Alright, I've been trying, and trying, and trying for the past 3-4 hours to find out how to install this adapter (it's for my desktop, which has no connection and a fresh install of Lucid Lynx on it (also my first ever install/use of ubuntu), i'm on my laptop right now). I've scoured the internet, only understood half of what I've read, and just went around in circles for a while doing pretty much nothing. I'm fairly sure i need ndiswrapper, but I have no idea how to get that installed, I've tried and I'm fairly sure I'm doing it wrong.

HALP MEH, PLEASE!

(also, if this is the wrong section, feel free to move this/delete this/just tell me, I'm new to this forum)

---

### Post by nzadLithium on 2010-10-23
can you run from the terminal:
uname -a
lspci
lsmod

post the output here

also find the model number of your wireless card, it'll probably be written near the barcode on the box.

---

### Post by crazy8rgood on 2010-10-23
> **nzadLithium said:**
> can you run from the terminal:
uname -a
lspci
lsmod

post the output here

also find the model number of your wireless card, it'll probably be written near the barcode on the box.
The model number is WN311B (if what I'm reading is the model number).

And this is the output:

```
tyler@tyler-desktop:~$ uname-a
uname-a: command not found
tyler@tyler-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
02:09.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
02:0a.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
tyler@tyler-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp             12446  2 
snd_ac97_codec        100646  1 snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
b43                   163523  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
mac80211              205146  1 b43
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
radeon                674824  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  2 b43,mac80211
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
ppdev                   5259  0 
snd                    54148  14 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 b43
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
parport_pc             25962  1 
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_atiixp,snd_pcm
i2c_piix4               8335  0 
ati_agp                 5094  0 
agpgart                31724  3 ttm,drm,ati_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  0 
usbhid                 36110  0 
ohci1394               26950  0 
8139too                18545  0 
hid                    67032  1 usbhid
ieee1394               81181  1 ohci1394
ssb                    38671  1 b43
3c59x                  31839  0 
8139cp                 16186  0 
mii                     4381  3 8139too,3c59x,8139cp
pata_atiixp             3148  3 
sata_sil                6959  0 

```Hope that's helpful.

EDIT: I realized I messed up the uname thing, here's the real output for that:

```
Linux tyler-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 201
0 i686 GNU/LInux
```
Sorry 'bout that.

---

### Post by nzadLithium on 2010-10-23
can you run 
ifconfig

Searching on the net seems to say your wireless chipset is supported by the b43 module, which you have loaded.

---

### Post by crazy8rgood on 2010-10-23
> **nzadLithium said:**
> can you run 
ifconfig

Searching on the net seems to say your wireless chipset is supported by the b43 module, which you have loaded.
I have no idea what the b43 module is, but this is what I get when I run ifconfig:

```
tyler@tyler-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:85:c7:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xdc00 

eth1      Link encap:Ethernet  HWaddr 00:50:da:c8:84:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8976 (8.9 KB)  TX bytes:8976 (8.9 KB)
```

---

### Post by nzadLithium on 2010-10-23
The b43 module is basically a device driver for your network card. Ubuntu has detected that your card should be supported by that driver however it seems somewhere the b43 module has not loaded sucessfully. 
What happens if you do dmesg | grep b43

---

### Post by crazy8rgood on 2010-10-23
> **nzadLithium said:**
> The b43 module is basically a device driver for your network card. Ubuntu has detected that your card should be supported by that driver however it seems somewhere the b43 module has not loaded sucessfully. 
What happens if you do dmesg | grep b43

```

tyler@tyler-desktop:~$ dmesg | grep b43
[    1.115657] b43-pci-bridge 0000:02:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.588755] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[    9.636126] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[    9.636236] b43: probe of ssb0:0 failed with error -95
```

?

---

### Post by nzadLithium on 2010-10-23
try
sudo apt-get install linux-firmware-nonfree
sudo rmmod b43
sudo modprobe b43
dmesg | tail

This assumes you have a working internet connection on that computer.

---

### Post by crazy8rgood on 2010-10-23
> **nzadLithium said:**
> try
sudo apt-get install linux-firmware-nonfree
sudo rmmod b43
sudo modprobe b43
dmesg | tail

This assumes you have a working internet connection on that computer.
I don't. That's why I need to install the adapter. :/

---

### Post by nzadLithium on 2010-10-23
you can download it from here:
[http://packages.ubuntu.com/maverick/linux-firmware-nonfree](http://packages.ubuntu.com/maverick/linux-firmware-nonfree)

stick it on a flash drive or cd or something and install the package from there.

---

### Post by crazy8rgood on 2010-10-23
> **nzadLithium said:**
> you can download it from here:
[http://packages.ubuntu.com/maverick/linux-firmware-nonfree](http://packages.ubuntu.com/maverick/linux-firmware-nonfree)

stick it on a flash drive or cd or something and install the package from there.
Alright sweet, thanks for that.

Now what, just do the last 3 lines of code from your last post?

I assume the first line finds it on the web and installs it or whatever, right?

---

### Post by nzadLithium on 2010-10-23
yup.

The two lines after restart the driver so your using the new files.
The last line checks the drivers output information so we can see if it worked.

---

### Post by crazy8rgood on 2010-10-24
> **nzadLithium said:**
> yup.

The two lines after restart the driver so your using the new files.
The last line checks the drivers output information so we can see if it worked.
Alright, well, I did that, and I got this:

```
tyler@tyler-desktop:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
tyler@tyler-desktop:~$ sudo modprobe b43
tyler@tyler-desktop:~$ dmesg | tail
[ 5209.027472] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700fd68), AE_LIMIT
[ 5209.027525] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)
[ 5209.067429] ACPI Error: Illegal I/O port address/length above 64K: 0x00400020/4 (20090903/hwvalid-154)
[ 5209.067446] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] (20090903/evregion-424)
[ 5209.067458] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700fd68), AE_LIMIT
[ 5209.067510] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)
[ 5285.519929] b43-phy1: Broadcom 4321 WLAN found (core revision 11)
[ 5285.560039] b43-phy1 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[ 5285.560083] b43: probe of ssb0:0 failed with error -95
[ 5285.560144] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]

```

---

### Post by nzadLithium on 2010-10-24
It seems that driver doesn't like your card :S
We can try the drivers made by broadcom next. If that doesn't work then we'll try ndiswrapper but its a cleaner solution to do it using linux programs, which is why im leaving ndiswrapper as a last resort.

If you go to system->administration->additional drivers
are you able to disable b43 and enable wl?

---

### Post by crazy8rgood on 2010-10-24
> **nzadLithium said:**
> It seems that driver doesn't like your card :S
We can try the drivers made by broadcom next. If that doesn't work then we'll try ndiswrapper but its a cleaner solution to do it using linux programs, which is why im leaving ndiswrapper as a last resort.

If you go to system->administration->additional drivers
are you able to disable b43 and enable wl?
I don't have an Additional Drivers option under Administration. :/

This is most unfortunate.

EDIT: I do have a "Hardware Drivers" option, though, I'll check that. One sec.

EDIT2: It says "No Proprietary drivers are in use on this system."

EDIT3: It's one in the morning right now, and I have to get up early, so I'm just gonna come back and check on this tomorrow sometime.

Thanks for the help though, man, much appreciated.

---

### Post by nzadLithium on 2010-10-24
well if its not in the list i'd then try ndiswrapper that should work.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by crazy8rgood on 2010-10-24
> **nzadLithium said:**
> well if its not in the list i'd then try ndiswrapper that should work.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Alright, I'm gonna need some help with this:

> Without an Internet connection, you can still install ndiswrapper-utils  from the Desktop CD. If you installed from that, the repository in which  ndiswrapper-utils is found is on the CD, but not within the live  session. You need to boot into your new Ubuntu installation and then  reinsert the Desktop CD. You will be asked if you want to add the  packages on the CD to your list of repositories.

I'm not entirely sure what it means by "Desktop CD". Do I have to burn the ndiswrapper files to a CD? Where do I find the files?

---

### Post by crazy8rgood on 2010-11-09
> **crazy8rgood said:**
> Alright, I'm gonna need some help with this:



I'm not entirely sure what it means by "Desktop CD". Do I have to burn the ndiswrapper files to a CD? Where do I find the files?
Sorry for the double post, but the screen for the laptop I was using to connect to the internet broke, and I just recently got it fixed.

By now, I'm thinking "Desktop CD" means the CD I used to install Ubuntu. I just really need to know if I'm right in thinking this.

---

### Post by crazy8rgood on 2010-11-14
> **crazy8rgood said:**
> Sorry for the double post, but the screen for the laptop I was using to connect to the internet broke, and I just recently got it fixed.

By now, I'm thinking "Desktop CD" means the CD I used to install Ubuntu. I just really need to know if I'm right in thinking this.
Sorry for the TRIPLE post. But noones helping me here and I just need this question answered.

---

### Post by nzadLithium on 2010-11-15
I assume your looking at this?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing) Packages (Without Internet access)

That is referring to your installation cd. You should according to that be able to put in the cd, add the files on disk to your repository then type 
sudo apt-get update
sudo apt-get install ndis-gtk ndiswrapper-utils ndiswrapper-common

that should get the software installed, then you will need to load the windows driver. 
it says you should blacklist the broadcom driver so:
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

download the windows driver or find the windows driver cd.
check for the .inf file for your wireless. If you can't find it you'll need to extract it.
To extract it you'll need:
if its a .cab:
[http://packages.ubuntu.com/lucid/i386/cabextract/download](http://packages.ubuntu.com/lucid/i386/cabextract/download)
if its an installshield installer:
[http://packages.ubuntu.com/lucid/i386/unshield/download](http://packages.ubuntu.com/lucid/i386/unshield/download)
[http://packages.ubuntu.com/lucid/i386/libunshield0/download](http://packages.ubuntu.com/lucid/i386/libunshield0/download)

once you've found the files you can go to:
system >> administration >> windows wireless drivers
click install new driver
point it to the inf file you found
hopefully then you'll be able to connect to wireless networks

you'll have to do this bit to get everything working automatically:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart)

---

