---
title: "Broadcom BCM4313"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by charlie19 on 2014-04-10
Hi guys, 
As you can probably tell i'm a very new ubuntu user but do have some general computing experience. 

The problem I seem to be having is that when I am connected to the WiFi in my house, I seem to be sucking all of the connection from the other devices?

So basically when I cant use any other device on the WiFi when my laptop running unbuntu 12.04 (full updated and all of the proprietry drivers are enabled and downloaded).

As soon as i disabled my wireless on my laptop, everything else all of a sudden comes back to life?

eth0      Link encap:Ethernet  HWaddr e8:11:32:3d:e6:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


eth1      Link encap:Ethernet  HWaddr b4:74:9f:5a:aa:c0  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b674:9fff:fe5a:aac0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:257433 errors:59 dropped:0 overruns:0 frame:690930
          TX packets:182815 errors:549 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:292802645 (292.8 MB)  TX bytes:25842254 (25.8 MB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:12364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1020990 (1.0 MB)  TX bytes:1020990 (1.0 MB)


dont know if that is of any use to you, ANY help would be absolutely fantastic as it is driving me insane.


Thank you very much, Charlie.

---

### Post by chili555 on 2014-04-10
I'll bet it's a Broadcom.

Please run and post:```
lspci -nn | grep 0280
```This is not super weird or even weird. We have seen and solved this before.

---

### Post by charlie19 on 2014-04-10
> **chili555 said:**
> I'll bet it's a Broadcom.

Please run and post:```
lspci -nn | grep 0280
```This is not super weird or even weird. We have seen and solved this before.


Hi chili, thanks for your reply and sorry for my ignorance and being a noob to this !

here is the information you requested:

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]
**02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)**
06:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


look forward to your reply

---

### Post by chili555 on 2014-04-10
Hmmmm. A Broadcom. 

We need just a few more pieces of information:```
uname -r
sudo dpkg -s bcmwl-kernel-source 
```The second command will produce a lot of useless-to-us information; just pick out and post Status and Version.

---

### Post by charlie19 on 2014-04-10
> **chili555 said:**
> Hmmmm. A Broadcom. 

We need just a few more pieces of information:```
uname -r
sudo dpkg -s bcmwl-kernel-source 
```The second command will produce a lot of useless-to-us information; just pick out and post Status and Version.


charlie@charlie-R540-R580-R780-SA41-E452-E852:~$ uname -r
3.11.0-19-generic
charlie@charlie-R540-R580-R780-SA41-E452-E852:~$ sudo dpkg -s bcmwl -kernel -source
[sudo] password for charlie: 
Package `bcmwl' is not installed and no info is available.


dpkg-query: error: package name in specifier '-kernel' is illegal: must start with an alphanumeric character
charlie@charlie-R540-R580-R780-SA41-E452-E852:~$ sudo dpkg -s bcmwl-kernal-source
Package `bcmwl-kernal-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
charlie@charlie-R540-R580-R780-SA41-E452-E852:~$ 



thats all im getting?

---

### Post by chili555 on 2014-04-10
>  sudo dpkg -s bcmwl -kernel -sourceIt is not bcmwl  -kernel  -source all spread out; it is bcmwl-kernel-source all jammed together. Please try again.

---

### Post by charlie19 on 2014-04-10
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4186
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>



sorry about that :(

---

### Post by chili555 on 2014-04-10
We are going to try an experiment; you have one of the trickiest devices to get going properly in the universe. Lucky you! Please try:```
sudo -i
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot. Your wireless will not be working until you do:```
sudo modprobe brcmsmac
```Now does it connect, surf the web and, more importantly, not kick other devices off the network? If so, we'll make a change or two to make this persistent.

---

### Post by charlie19 on 2014-04-10
seems to be working ! on my phone at least

---

### Post by charlie19 on 2014-04-10
I've just tried working on my other laptop next to it and it still doesnt work at all :confused:

---

### Post by chili555 on 2014-04-10
Does your laptop connect using the driver *brcmsmac* intead of *wl*? If so, we'll turn our attention to the router.

Away for a couple of hours. I'll see you a bit later.

---

### Post by charlie19 on 2014-04-10
I'm not really sure to be honest with you?

would it help changing the channel on the router?

---

### Post by chili555 on 2014-04-10
> **charlie19 said:**
> I'm not really sure to be honest with you?

Is the computer turned on? Is the driver brcmsmac loaded and not wl?```
lsmod
```When you click the Network Manager icon, do you see your network? [http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu(1).png) If you click on your network, does it connect? Having done so, can you open Firefox and surf the web?

---

### Post by charlie19 on 2014-04-10
Module                  Size  Used by
vesafb                 13876  1 
bnep                   24107  2 
rfcomm                 74718  12 
parport_pc             32866  0 
ppdev                  17711  0 
usblp                  23015  0 
binfmt_misc            17508  1 
snd_hda_codec_hdmi     41773  1 
snd_hda_codec_realtek    57219  1 
snd_hda_intel          57134  7 
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12573  2 
brcmsmac              564374  0 
brcmutil               15618  1 brcmsmac
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cordic                 12574  1 brcmsmac
uvcvideo               82247  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
b43                   397389  0 
fglrx                6728867  244 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
videobuf2_vmalloc      13216  1 uvcvideo
btusb                  28374  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17613  0 
snd_timer              29989  2 snd_pcm,snd_seq
mac80211              623607  2 brcmsmac,b43
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              499466  3 brcmsmac,b43,mac80211
bluetooth             391726  24 bnep,rfcomm,btusb
ssb                    62919  1 b43
snd                    73753  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcma                   47094  3 brcmsmac,b43
mac_hid                13253  0 
psmouse               104093  0 
soundcore              12680  1 snd
intel_ips              18520  0 
samsung_laptop         18627  0 
video                  19574  1 samsung_laptop
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                21163  0 
amd_iommu_v2           19227  1 fglrx
serio_raw              13413  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
usb_storage            66567  1 
sky2                   59109  0 
ahci                   30063  2 
libahci                32118  1 ahci



yes i can surf the web my point was that when im connected on this device using ubuntu the other devices drop connection or have difficulty loading.

---

### Post by chili555 on 2014-04-10
We may have better luck if we also remove and blacklist b43:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r b43
exit
```

Let's next turn our attention to the router.  WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1,6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

I also recommend that you fully update the router's firmware.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

---

