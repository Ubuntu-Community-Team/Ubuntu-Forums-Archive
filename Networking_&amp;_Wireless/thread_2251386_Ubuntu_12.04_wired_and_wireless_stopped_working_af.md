---
title: "Ubuntu 12.04 wired and wireless stopped working after installing additional drivers"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by parazitus on 2014-11-04
Hello,

I've been using Ubuntu 12.04 since a long time with the Broadcom wireless driver and it was working just fine. A few days ago I did a kernel upgrade and the wireless stopped working. Then I installed the wireless Broadcom driver (which seemed to have uninstalled in correlation to the kernel upgrade) and after this both wired and wireless stopped working. I'm sure it's not a hardware problem since they work fine when I boot on windows (I have dual boot). It's really frustrating and I'm left with no internet on my PC.

One more thing to note, on boot it waits for 60 seconds for network configuration and then times out and continues booting.

Any ideas on how I can get things to work?

```

$ uname -a
Linux geko 3.13.0-39-generic #66~precise1-Ubuntu SMP Wed Oct 29 09:56:49 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6238 (6.2 KB)  TX bytes:6238 (6.2 KB)

$ iwconfig
lo        no wireless extensions.

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: memory:f9bfe000-f9bfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

Thanks!

---

### Post by Hadaka on 2014-11-04
Hi,additional drivers are a bad thing.
please open a terminal ctrl/alt/t
and with ethernet cable attached please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot
your wired connection should be now working. so with that working
connection please do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
boot
remove the wired cable ..test wireless
thanks.

---

### Post by parazitus on 2014-11-04
[FONT=arial]Hey,
thanks for the help, wired network works after uninstalling bcmwl, but I had to manually set the dns in /etc/resolv.conf
Wireless still doesn't work and my computer hangs (i.e. it's completely dead) when I do:

```

[FONT=arial]sudo modprobe b43[/FONT]
```[/FONT][FONT=arial]

[/FONT]I've tried restarting and reinstalling b43-fwcutter and firmware-b43-installer, but it's the same thing, it still hangs when I do modprobe b43. It seems to be doing something intensive since the fan start working 5 minutes after it hangs.
[FONT=arial]
Any ideas on how to solve this?

Thanks!
[/FONT]

---

### Post by Hadaka on 2014-11-04
Without any printouts its diffiult, all i can do is guess..
i would suggest you do  an update to bring things in line.
```
sudo apt-get update
```
and post the results of..
```
lsmod
rfkill list all

```thanks.

---

### Post by parazitus on 2014-11-04
hi Hakada,

```

$ iwconfig
eth2      no wireless extensions.

lo        no wireless extensions.

$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$ lsmod
Module                  Size  Used by
btrfs                 867337  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    75385  0 
qnx4                   13396  0 
hfsplus               108401  0 
hfs                    54819  0 
minix                  36454  0 
ntfs                   97805  0 
msdos                  17332  0 
jfs                   186939  0 
xfs                   942481  0 
libcrc32c              12644  2 btrfs,xfs
reiserfs              248975  0 
joydev                 17575  0 
snd_hda_codec_idt      59430  1 
snd_hda_intel          57222  3 
snd_hda_codec         199156  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  2 snd_hda_intel,snd_hda_codec
dell_wmi               12761  0 
hid_a4tech             12651  0 
sparse_keymap          13890  1 dell_wmi
hid_generic            12548  0 
gpio_ich               13526  0 
snd_seq_midi           13324  0 
snd_rawmidi            30465  1 snd_seq_midi
b43                   397438  0 
snd_seq_midi_event     14899  1 snd_seq_midi
dell_laptop            18315  0 
r852                   18157  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
mac80211              658125  1 b43
dcdbas                 15017  1 dell_laptop
sm_common              16908  1 r852
nand                   64690  2 r852,sm_common
mtd                    59754  2 sm_common,nand
cfg80211              502970  2 b43,mac80211
nvidia              10675249  33 
nand_ids                8627  1 nand
snd_timer              30038  2 snd_pcm,snd_seq
r592                   18148  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_bch               13227  1 nand
bch                    22063  1 nand_bch
uvcvideo               82247  0 
nand_ecc               13312  1 nand
memstick               16968  1 r592
videobuf2_core         40972  1 uvcvideo
snd                    73890  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev              139761  2 uvcvideo,videobuf2_core
psmouse               113331  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
soundcore              12680  1 snd
lpc_ich                21163  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
usbhid                 53111  0 
ssb_hcd                12909  0 
hid                   106605  3 hid_a4tech,hid_generic,usbhid
serio_raw              13462  0 
bcma                   52421  1 b43
btusb                  32519  0 
mac_hid                13253  0 
wmi                    19363  1 dell_wmi
drm                   308868  2 nvidia
video                  19914  0 
rfcomm                 74748  12 
bnep                   19884  2 
bluetooth             411194  24 btusb,rfcomm,bnep
parport_pc             32866  0 
ppdev                  17711  0 
lp                     17799  0 
parport                42481  3 parport_pc,ppdev,lp
binfmt_misc            17508  1 
b44                    40453  0 
firewire_ohci          45158  0 
sdhci_pci              23263  0 
sdhci                  43409  1 sdhci_pci
ahci                   30063  2 
libahci                32825  1 ahci
firewire_core          69403  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
mii                    13981  1 b44
ssb                    63241  3 b43,ssb_hcd,b44

```

---

### Post by Hadaka on 2014-11-04
Hi,with a working wired connection please do..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf r952
sudo modprobe -rf r852
sudo modprobe -rf b43
sudo modprobe b43
sudo rm /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep 'b44|b43|wlan'
```
please post the outbut of the dmesg..thanks

---

### Post by parazitus on 2014-11-05
Hi,

Same thing, when I do "sudo modprobe b43" my computer completely locks up. It worked after a restart though.
Here's the output of dmesg:
```

$ dmesg | egrep 'b44|b43|wlan'
[    1.196173] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.216510] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:a6:04:b9
[    3.578117] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    3.620086] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[    3.648764] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[    3.648770] b43 ssb0:0: Direct firmware load failed with error -22
[    3.648772] b43 ssb0:0: Falling back to user helper
[    6.816227] b44 ssb1:0 eth2: Link is up at 100 Mbps, full duplex
[    6.816232] b44 ssb1:0 eth2: Flow control is off for TX and off for RX
[   63.712363] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[   63.712372] b43 ssb0:0: Direct firmware load failed with error -22
[   63.712376] b43 ssb0:0: Falling back to user helper
[  123.872343] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  123.872351] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  127.840226] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[  127.864383] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[  127.864395] b43 ssb0:0: Direct firmware load failed with error -22
[  127.864402] b43 ssb0:0: Falling back to user helper
[  187.872119] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[  187.872124] b43 ssb0:0: Direct firmware load failed with error -22
[  187.872126] b43 ssb0:0: Falling back to user helper

```

---

### Post by Hadaka on 2014-11-05
hi, you are missing your firmware
 123.872343] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found

from a working wired connection,,,please do
```
sudo apt-get update
sudo apt-get upgrade
sudo modprobe -rf b43
sudo modprobe b43
```
is it working now??

---

### Post by parazitus on 2014-11-05
ah.. the frustration.

I still get the same dmesg output as before, even after doing modprobe b43:

```
$ dmesg | egrep 'b44|b43|wlan'
[    1.256185] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.276573] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:a6:04:b9
[    3.743512] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    3.784308] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[    3.836262] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[    3.836264] b43 ssb0:0: Direct firmware load failed with error -22
[    3.836266] b43 ssb0:0: Falling back to user helper
[   63.964211] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[   63.964220] b43 ssb0:0: Direct firmware load failed with error -22
[   63.964224] b43 ssb0:0: Falling back to user helper
[  124.124441] b43 ssb0:0: Direct firmware load failed with error -2
[  124.124454] b43 ssb0:0: Falling back to user helper
[  124.128633] b43 ssb0:0: Direct firmware load failed with error -2
[  124.128643] b43 ssb0:0: Falling back to user helper
[  124.134639] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  124.134645] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  124.134647] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  150.812205] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  150.812213] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

```

and when I purge the driver and reinstall, my computer locks when I do "sudo modprobe b43"

---

### Post by jeremy31 on 2014-11-05
```
ls /lib/firmware/b43
```
see if the firmware is there

---

### Post by Hadaka on 2014-11-05
please show the output of..
```
sudo apt-get update
sudo apt-get upgrade
```
and then do and post..
```
sudo su
ls /lib/firmware/b43 | grep ucode5.fw
exit 0
```
thanks

---

### Post by parazitus on 2014-11-05
hi Jeremy,

it seems to be there:
```
$ sudo ls /lib/firmware/b43
a0g0bsinitvals5.fw   lp0bsinitvals14.fw     sslpn2bsinitvals17.fw
a0g0bsinitvals9.fw   lp0bsinitvals15.fw     sslpn2bsinitvals19.fw
a0g0initvals5.fw     lp0bsinitvals16.fw     sslpn2initvals17.fw
a0g0initvals9.fw     lp0initvals13.fw        sslpn2initvals19.fw
a0g1bsinitvals13.fw  lp0initvals14.fw        ucode11.fw
a0g1bsinitvals5.fw   lp0initvals15.fw        ucode13.fw
a0g1bsinitvals9.fw   lp0initvals16.fw        ucode14.fw
a0g1initvals13.fw    n0absinitvals11.fw     ucode15.fw
a0g1initvals5.fw     n0bsinitvals11.fw        ucode16_lp.fw
a0g1initvals9.fw     n0bsinitvals16.fw        ucode16_mimo.fw
b0g0bsinitvals13.fw  n0initvals11.fw        ucode16_sslpn.fw
b0g0bsinitvals5.fw   n0initvals16.fw        ucode16_sslpn_nobt.fw
b0g0bsinitvals9.fw   pcm5.fw            ucode17.fw
b0g0initvals13.fw    sslpn0bsinitvals16.fw  ucode19.fw
b0g0initvals5.fw     sslpn0initvals16.fw    ucode20.fw
b0g0initvals9.fw     sslpn1bsinitvals20.fw  ucode5.fw
lp0bsinitvals13.fw   sslpn1initvals20.fw    ucode9.fw

```

---

### Post by parazitus on 2014-11-05
Hi Hadaka,

Here are the outputs:

```

$ sudo apt-get update
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                                                                      
Hit http://dl.google.com stable Release.gpg                                                                                                     
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                           
Hit http://extras.ubuntu.com precise Release                                                                                                           
Hit http://archive.canonical.com precise Release                                                                                                
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                    
Hit http://dl.google.com stable Release                                                                                                                
Get:2 http://security.ubuntu.com precise-security Release [53.0 kB]                                                                                    
Hit http://ppa.launchpad.net precise Release                                                                                                   
Hit http://extras.ubuntu.com precise/main Sources                                                                                                 
Hit http://archive.canonical.com precise/partner Sources                                                                                         
Hit http://dl.google.com stable/main amd64 Packages                                                                                                    
Hit http://ppa.launchpad.net precise/main Sources                                                                                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                         
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                             
Hit http://ppa.launchpad.net precise/main Sources                                                                                                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                                               
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                          
Hit http://archive.canonical.com precise/partner amd64 Packages                                                                                  
Hit http://archive.canonical.com precise/partner i386 Packages                                                                                   
Ign http://archive.canonical.com precise/partner TranslationIndex                                                                                
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                       
Hit http://dl.google.com stable/main i386 Packages                                                                         
Ign http://dl.google.com stable/main TranslationIndex                                                                                                  
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                         
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                       
Hit http://ppa.launchpad.net precise/main Sources                                                                                                
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                         
Hit http://fr.archive.ubuntu.com precise Release.gpg                                                                                                   
Get:3 http://fr.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                           
Get:4 http://fr.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                                         
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                        
Hit http://ppa.launchpad.net precise/main Sources                                                                                       
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                 
Hit http://ppa.launchpad.net precise/main TranslationIndex                                                                                             
Get:5 http://security.ubuntu.com precise-security/main Sources [112 kB]                                                                 
Hit http://ppa.launchpad.net precise/main Sources                                                                                       
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                              
Hit http://fr.archive.ubuntu.com precise Release                                                                                                       
Get:6 http://fr.archive.ubuntu.com precise-updates Release [194 kB]                                                                             
Hit http://ppa.launchpad.net precise/main Translation-en                                                                                               
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                                         
Get:8 http://security.ubuntu.com precise-security/universe Sources [33.0 kB]                                                                           
Ign http://dl.google.com stable/main Translation-en_US                                                                                                 
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,780 B]                                                                         
Get:10 http://security.ubuntu.com precise-security/main amd64 Packages [432 kB]                                                                        
Ign http://archive.canonical.com precise/partner Translation-en_US                                                                                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                            
Ign http://dl.google.com stable/main Translation-en                                                                                                    
Ign http://extras.ubuntu.com precise/main Translation-en                                                                            
Ign http://archive.canonical.com precise/partner Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                         
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_US       
Ign http://ppa.launchpad.net precise/main Translation-en                                
Ign http://ppa.launchpad.net precise/main Translation-en_US                             
Ign http://ppa.launchpad.net precise/main Translation-en                                
Ign http://ppa.launchpad.net precise/main Translation-en_US                             
Ign http://ppa.launchpad.net precise/main Translation-en          
Get:11 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:12 http://security.ubuntu.com precise-security/universe amd64 Packages [99.5 kB]
Get:13 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,443 B]
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [465 kB]        
Get:15 http://fr.archive.ubuntu.com precise-backports Release [53.1 kB]                  
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]  
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [106 kB]
Get:18 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,645 B]       
Hit http://security.ubuntu.com precise-security/main TranslationIndex                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                 
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                 
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                   
Hit http://fr.archive.ubuntu.com precise/main Sources                                       
Hit http://fr.archive.ubuntu.com precise/restricted Sources 
Hit http://fr.archive.ubuntu.com precise/universe Sources   
Hit http://fr.archive.ubuntu.com precise/multiverse Sources 
Hit http://fr.archive.ubuntu.com precise/main amd64 Packages
Hit http://fr.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://fr.archive.ubuntu.com precise/universe amd64 Packages
Hit http://fr.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://fr.archive.ubuntu.com precise/main i386 Packages                                                          
Hit http://security.ubuntu.com precise-security/main Translation-en                                                  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                            
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                            
Hit http://security.ubuntu.com precise-security/universe Translation-en                                              
Hit http://fr.archive.ubuntu.com precise/restricted i386 Packages                          
Hit http://fr.archive.ubuntu.com precise/universe i386 Packages      
Hit http://fr.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://fr.archive.ubuntu.com precise/main TranslationIndex       
Hit http://fr.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://fr.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://fr.archive.ubuntu.com precise/universe TranslationIndex   
Get:19 http://fr.archive.ubuntu.com precise-updates/main Sources [479 kB]
Get:20 http://fr.archive.ubuntu.com precise-updates/restricted Sources [8,000 B]
Get:21 http://fr.archive.ubuntu.com precise-updates/universe Sources [111 kB]
Get:22 http://fr.archive.ubuntu.com precise-updates/multiverse Sources [8,889 B]
Get:23 http://fr.archive.ubuntu.com precise-updates/main amd64 Packages [842 kB]
Get:24 http://fr.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.2 kB]
Get:25 http://fr.archive.ubuntu.com precise-updates/universe amd64 Packages [249 kB]
Get:26 http://fr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:27 http://fr.archive.ubuntu.com precise-updates/main i386 Packages [874 kB]  
Get:28 http://fr.archive.ubuntu.com precise-updates/restricted i386 Packages [13.2 kB]
Get:29 http://fr.archive.ubuntu.com precise-updates/universe i386 Packages [256 kB]
Get:30 http://fr.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://fr.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://fr.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://fr.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://fr.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:31 http://fr.archive.ubuntu.com precise-backports/main Sources [5,551 B]
Get:32 http://fr.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:33 http://fr.archive.ubuntu.com precise-backports/universe Sources [40.6 kB]
Get:34 http://fr.archive.ubuntu.com precise-backports/multiverse Sources [5,737 B]
Get:35 http://fr.archive.ubuntu.com precise-backports/main amd64 Packages [6,617 B]
Get:36 http://fr.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:37 http://fr.archive.ubuntu.com precise-backports/universe amd64 Packages [43.3 kB]
Get:38 http://fr.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,405 B]
Get:39 http://fr.archive.ubuntu.com precise-backports/main i386 Packages [6,620 B]
Get:40 http://fr.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:41 http://fr.archive.ubuntu.com precise-backports/universe i386 Packages [43.1 kB]
Get:42 http://fr.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,399 B]
Get:43 http://fr.archive.ubuntu.com precise-backports/main TranslationIndex [202 B]
Get:44 http://fr.archive.ubuntu.com precise-backports/multiverse TranslationIndex [202 B]
Get:45 http://fr.archive.ubuntu.com precise-backports/restricted TranslationIndex [193 B]
Get:46 http://fr.archive.ubuntu.com precise-backports/universe TranslationIndex [205 B]
Hit http://fr.archive.ubuntu.com precise/main Translation-en
Hit http://fr.archive.ubuntu.com precise/multiverse Translation-en
Hit http://fr.archive.ubuntu.com precise/restricted Translation-en
Hit http://fr.archive.ubuntu.com precise/universe Translation-en            
Hit http://fr.archive.ubuntu.com precise-updates/main Translation-en
Hit http://fr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://fr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://fr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/restricted Translation-en
Get:47 http://fr.archive.ubuntu.com precise-backports/universe Translation-en [34.5 kB]
Fetched 4,649 kB in 5s (812 kB/s)                          
Reading package lists... Done

```

```

adi@geko:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  lib32gcc1 lib32stdc++6 libatomic1 libgcc1 libgcc1:i386 libgfortran3 libgomp1 libgomp1:i386 libitm1 libquadmath0 libstdc++6 libstdc++6:i386 libtsan0
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

```

root@geko:/home/adi# ls /lib/firmware/b43 | grep ucode5.fw
ucode5.fw
root@geko:/home/adi# exit 0
exit

```

---

### Post by Hadaka on 2014-11-05
Hi, give this a try..
```
sudo apt-get dist-upgrade
sudo modprobe -rf b43
sudo modprobe b43
```
post the output please
thanks.

---

### Post by parazitus on 2014-11-06
Still doesn't work. dmesg logs that the firmware couldn't be loaded and gave error -22 (see last listing). If I try reinstalling b43-fwcutter and firmware-b43-installer, my computer blocks when I do "modprobe b43" (but it works after a restart).

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  gcc-4.9-base gcc-4.9-base:i386
The following packages will be upgraded:
  lib32gcc1 lib32stdc++6 libatomic1 libgcc1 libgcc1:i386 libgfortran3 libgomp1 libgomp1:i386 libitm1 libquadmath0 libstdc++6 libstdc++6:i386 libtsan0
13 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,170 kB of archives.
After this operation, 1,358 kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  gcc-4.9-base gcc-4.9-base libgcc1 libgcc1 libstdc++6 libstdc++6 libatomic1 libquadmath0 libgfortran3 libgomp1 libgomp1 libitm1 libtsan0 lib32gcc1
  lib32stdc++6
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main gcc-4.9-base amd64 4.9.2-0ubuntu1~12.04 [17.7 kB]
Get:2 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main gcc-4.9-base i386 4.9.2-0ubuntu1~12.04 [17.7 kB]
Get:3 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libgcc1 amd64 1:4.9.2-0ubuntu1~12.04 [45.4 kB]
Get:4 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libgcc1 i386 1:4.9.2-0ubuntu1~12.04 [56.0 kB]
Get:5 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libstdc++6 i386 4.9.2-0ubuntu1~12.04 [366 kB]
Get:6 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libstdc++6 amd64 4.9.2-0ubuntu1~12.04 [347 kB]
Get:7 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libatomic1 amd64 4.9.2-0ubuntu1~12.04 [10.6 kB]
Get:8 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libquadmath0 amd64 4.9.2-0ubuntu1~12.04 [143 kB]
Get:9 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libgfortran3 amd64 4.9.2-0ubuntu1~12.04 [357 kB]
Get:10 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libgomp1 i386 4.9.2-0ubuntu1~12.04 [46.8 kB]
Get:11 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libgomp1 amd64 4.9.2-0ubuntu1~12.04 [44.0 kB]
Get:12 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libitm1 amd64 4.9.2-0ubuntu1~12.04 [37.9 kB]
Get:13 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main libtsan0 amd64 4.9.2-0ubuntu1~12.04 [269 kB]
Get:14 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main lib32gcc1 amd64 1:4.9.2-0ubuntu1~12.04 [55.7 kB]
Get:15 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/ precise/main lib32stdc++6 amd64 4.9.2-0ubuntu1~12.04 [357 kB]
Fetched 2,170 kB in 1s (1,280 kB/s)
Selecting previously unselected package gcc-4.9-base.
(Reading database ... 449911 files and directories currently installed.)
Unpacking gcc-4.9-base (from .../gcc-4.9-base_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Selecting previously unselected package gcc-4.9-base:i386.
Unpacking gcc-4.9-base:i386 (from .../gcc-4.9-base_4.9.2-0ubuntu1~12.04_i386.deb) ...
Processing triggers for ccache ...
Updating symlinks in /usr/lib/ccache ...
Setting up gcc-4.9-base (4.9.2-0ubuntu1~12.04) ...
Setting up gcc-4.9-base:i386 (4.9.2-0ubuntu1~12.04) ...
(Reading database ... 449921 files and directories currently installed.)
Preparing to replace libgcc1:i386 1:4.8.1-2ubuntu1~12.04 (using .../libgcc1_1%3a4.9.2-0ubuntu1~12.04_i386.deb) ...
De-configuring libgcc1 ...
Unpacking replacement libgcc1:i386 ...
Preparing to replace libgcc1 1:4.8.1-2ubuntu1~12.04 (using .../libgcc1_1%3a4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.9.2-0ubuntu1~12.04) ...
Setting up libgcc1:i386 (1:4.9.2-0ubuntu1~12.04) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/local/lib/libisl.so.10.2.1-gdb.py is not an ELF file - it has the wrong magic bytes at the start.

(Reading database ... 449921 files and directories currently installed.)
Preparing to replace libstdc++6 4.8.1-2ubuntu1~12.04 (using .../libstdc++6_4.9.2-0ubuntu1~12.04_amd64.deb) ...
De-configuring libstdc++6:i386 ...
Unpacking replacement libstdc++6 ...
Preparing to replace libstdc++6:i386 4.8.1-2ubuntu1~12.04 (using .../libstdc++6_4.9.2-0ubuntu1~12.04_i386.deb) ...
Unpacking replacement libstdc++6:i386 ...
Setting up libstdc++6 (4.9.2-0ubuntu1~12.04) ...
Setting up libstdc++6:i386 (4.9.2-0ubuntu1~12.04) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/local/lib/libisl.so.10.2.1-gdb.py is not an ELF file - it has the wrong magic bytes at the start.

(Reading database ... 449935 files and directories currently installed.)
Preparing to replace libatomic1 4.8.1-2ubuntu1~12.04 (using .../libatomic1_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libatomic1 ...
Preparing to replace libquadmath0 4.8.1-2ubuntu1~12.04 (using .../libquadmath0_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libquadmath0 ...
Preparing to replace libgfortran3 4.8.1-2ubuntu1~12.04 (using .../libgfortran3_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libgfortran3 ...
Preparing to replace libgomp1:i386 4.8.1-2ubuntu1~12.04 (using .../libgomp1_4.9.2-0ubuntu1~12.04_i386.deb) ...
De-configuring libgomp1 ...
Unpacking replacement libgomp1:i386 ...
Preparing to replace libgomp1 4.8.1-2ubuntu1~12.04 (using .../libgomp1_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libgomp1 ...
Setting up libgomp1:i386 (4.9.2-0ubuntu1~12.04) ...
Setting up libgomp1 (4.9.2-0ubuntu1~12.04) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/local/lib/libisl.so.10.2.1-gdb.py is not an ELF file - it has the wrong magic bytes at the start.

(Reading database ... 449935 files and directories currently installed.)
Preparing to replace libitm1 4.8.1-2ubuntu1~12.04 (using .../libitm1_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libitm1 ...
Preparing to replace libtsan0 4.8.1-2ubuntu1~12.04 (using .../libtsan0_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement libtsan0 ...
Preparing to replace lib32gcc1 1:4.8.1-2ubuntu1~12.04 (using .../lib32gcc1_1%3a4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement lib32gcc1 ...
Preparing to replace lib32stdc++6 4.8.1-2ubuntu1~12.04 (using .../lib32stdc++6_4.9.2-0ubuntu1~12.04_amd64.deb) ...
Unpacking replacement lib32stdc++6 ...
Setting up libatomic1 (4.9.2-0ubuntu1~12.04) ...
Setting up libquadmath0 (4.9.2-0ubuntu1~12.04) ...
Setting up libgfortran3 (4.9.2-0ubuntu1~12.04) ...
Setting up libitm1 (4.9.2-0ubuntu1~12.04) ...
Setting up libtsan0 (4.9.2-0ubuntu1~12.04) ...
Setting up lib32gcc1 (1:4.9.2-0ubuntu1~12.04) ...
Setting up lib32stdc++6 (4.9.2-0ubuntu1~12.04) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/local/lib/libisl.so.10.2.1-gdb.py is not an ELF file - it has the wrong magic bytes at the start.

```

```

$ sudo modprobe -rf b43
$ sudo modprobe b43
$

```

```

$ dmesg | egrep 'b44|b43|wlan'
[    1.236191] b44: Broadcom 44xx/47xx 10/100 PCI ethernet dri
ver version 2.0
[    1.260607] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:a6:04:b9
[    3.901299] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    3.960888] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[    3.997931] b43 ssb0:0: firmware, attempted to load /lib/firmware/b43/ucode5.fw, but failed with error -22
[    3.997937] b43 ssb0:0: Direct firmware load failed with error -22
[    3.997939] b43 ssb0:0: Falling back to user helper

```

---

### Post by Hadaka on 2014-11-06
Let's try a different method.
disconnect the ethernet cable, lets load this
like it has no internet. click the link,post #7
make sure to get the zip file first.
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
once complete, boot and test.

---

### Post by parazitus on 2014-11-06
I can't believe it.. it worked! :))

Thanks a lot. I've marked this thread as solved.

---

### Post by jeremy31 on 2014-11-06
My question is does ```
ls /lib/firmware/b43
``` work without using sudo now?

---

### Post by parazitus on 2014-11-06
hi Jeremy,

Yes, it works without sudo. Permissions were overwritten by the files from the archive that Hadaka mentioned.
Do you think that was the problem?

---

### Post by jeremy31 on 2014-11-06
> **parazitus said:**
> hi Jeremy,

Yes, it works without sudo. Permissions were overwritten by the files from the archive that Hadaka mentioned.
Do you think that was the problem?

It may have been part of the problem, I found some 2 year old posts that the poster had chmod +755 on the b43 file

---

### Post by Hadaka on 2014-11-06
Glad that worked !!
enjoy

---

