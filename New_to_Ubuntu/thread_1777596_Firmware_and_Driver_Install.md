---
title: "Firmware and Driver Install"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Fat-n00b on 2011-06-07
I have a wireless adapter/NIC that I want use in/with latest version Ubuntu 11.04 (AMD 64 bit)

The model adapter is RT2561...

Drivers and Firmware for Linux can be found at:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I have download both files:
/home/username/Documents/RT61_Firmware_V1.2.zip
/home/username/Documents/2010_0825_RT61_Linux_STA_v1.1.2.6.tar.bz2

But now how do I use them??

I am absolute beginner with Linux/Ubuntu so I need very detailed step by step instructions on how to get this driver installed... Maybe even need to know how to enable the wireless card...

Thanks,

Fat-n00b

---

### Post by wolfen69 on 2011-06-08
I have that exact wireless card, and it is supported "out of the box" in ubuntu. Just click your network icon on the top (right side) panel, and you should see a list of available networks. Most of the time, things "just work" in linux. ;)

---

### Post by Fat-n00b on 2011-06-08
Not sure what is going on... but Ubuntu does not seem to recognize it.

Maybe the firmware is to old...

The actual product I purchased is Rosewill RNX-G300E IEEE 802.11b/g PCI Wireless:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166012](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166012)

But from my understanding it is just a repackaged Ralink RT2561

---

### Post by jtarin on 2011-06-08
Are both of you using the same version of Ubuntu?

---

### Post by jtarin on 2011-06-08
Post your results from the terminal command ```
lspci
``` and then ```
lsmod
```

---

### Post by wolfen69 on 2011-06-09
> **jtarin said:**
> Are both of you using the same version of Ubuntu?

My card with the Ralink 2561 chipset has worked with every version of ubuntu, and every distro for that matter. It is *well* supported.

---

### Post by jtarin on 2011-06-09
> **wolfen69 said:**
> My card with the Ralink 2561 chipset has worked with every version of ubuntu, and every distro for that matter. It is *well* supported.
64-bit also? Let's see what "lsmod" and "lspci" say.

---

### Post by Fat-n00b on 2011-06-09
> **jtarin said:**
> 64-bit also? Let's see what "lsmod" and "lspci" say.
 
Will do when I get back to the house... Ubuntu 11.04 AMD 64

---

### Post by Fat-n00b on 2011-06-09
lsmod results
```
Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
radeon                982197  3 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
snd_hda_intel          33211  2 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
drm                   227495  5 radeon,ttm,drm_kms_helper
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  0 
sp5100_tco             13744  0 
ppdev                  17113  0 
i2c_algo_bit           13400  1 radeon
i2c_piix4              13303  0 
parport_pc             36959  1 
snd_timer              29602  2 snd_seq,snd_pcm
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
edac_mce_amd           23464  0 
asus_atk0110           17976  0 
soundcore              12680  1 snd
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
pata_atiixp            13165  0 
r8169                  48022  0 
```

lspci results
```
0:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

---

### Post by wildmanne39 on 2011-06-09
> **Fat-n00b said:**
> lsmod results
```
Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
radeon                982197  3 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
snd_hda_intel          33211  2 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
drm                   227495  5 radeon,ttm,drm_kms_helper
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  0 
sp5100_tco             13744  0 
ppdev                  17113  0 
i2c_algo_bit           13400  1 radeon
i2c_piix4              13303  0 
parport_pc             36959  1 
snd_timer              29602  2 snd_seq,snd_pcm
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
edac_mce_amd           23464  0 
asus_atk0110           17976  0 
soundcore              12680  1 snd
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
pata_atiixp            13165  0 
r8169                  48022  0 
```

lspci results
```
0:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```
Hi, I did a lot of searching and found this to be the solution to your problem.
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

### Post by jtarin on 2011-06-09
> **wildmanne39 said:**
> Hi, I did a lot of searching and found this to be the solution to your problem.
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)I'm glad you found it wildmanne39. I just got back to the thread and noticed something amiss from the OP's original statement and the lspci I asked for. Good you found a page.:p

---

### Post by Fat-n00b on 2011-06-10
> **jtarin said:**
> I'm glad you found it wildmanne39. I just got back to the thread and noticed something amiss from the OP's original statement and the lspci I asked for. Good you found a page.:p
 
This is actual product I purchased:
Rosewill RNX-G300E IEEE 802.11b/g PCI Wireless:
[[COLOR=#444444]http://www.newegg.com/Product/Produc...82E16833166012[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166012")

But from my understanding it is just a repackaged Ralink RT2561
 
I will try those directions when I get home...

---

### Post by jtarin on 2011-06-10
> **Fat-n00b said:**
> This is actual product I purchased:
Rosewill RNX-G300E IEEE 802.11b/g PCI Wireless:
[[COLOR=#444444]http://www.newegg.com/Product/Produc...82E16833166012[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166012")

But from my understanding it is just a repackaged Ralink RT2561
 
I will try those directions when I get home...Your "lspci" command shows a different story. **Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)**
Do you have more than one wireless card because this repackaged Ralink RT2561 is not showing.

---

### Post by Fat-n00b on 2011-06-10
> **jtarin said:**
> Your "lspci" command shows a different story. **Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)**
Do you have more than one wireless card because this repackaged Ralink RT2561 is not showing.
 
No... Just the one, but this is why I thought the firmware needed to be updated... But the info on Newegg sight could be wrong or I was sent the wrong box so many years go.
 
I will try those directions when I get home to see if works.
 
Actually a little searching through Rosewill's site shows that Newegg's site might truely be incorrcet
 
Rosewill lists the chip as
88W8335 + 88W8010 Marvell
 
Found at:
[http://www.rosewill.com/products/s_935/productDetail.htm](http://www.rosewill.com/products/s_935/productDetail.htm)
 
So all this time and I was searching for the wrong thing.

---

### Post by Fat-n00b on 2011-06-10
In the directions it says that I need a different drive the AMD 64 version but the address listed seems to get redirected... Will it still work?
 
How would I change the following to point/get the the 64 bit driver?
 
```
 
mkdir mrv
cd mrv
wget -c http://www.cafuego.net/stuff/mrv.zip
unzip mrv.zip
sudo ndiswrapper -i mrv8335.inf
sudo ndiswrapper -m
cd ..
rm -rf ./mrv

```
 
Is the above exactly what I type into terminal?

Can you help me to understand each line?
 
mkdir mrv:
I assume this means MaKe DIRectory(folder) named "mrv"
 
cd mrv:
Change Directory(folder) to "mrv"
 
wget -c blah blah
basically download file from blah blah
 
unzip easy enough
 
sudo 
As root users
 
ndiswrapper -i mrv8335.inf 
????
 
diswrapper -m
????
 
cd ..
Change Directory (I would guess the .. means up 2 parent directories)

rm -rf ./mrv
?????

---

### Post by Fat-n00b on 2011-06-11
Well that driver did not work... and I can not find the other 64bit driver.

---

### Post by jtarin on 2011-06-11
> **Fat-n00b said:**
> No... Just the one, but this is why I thought the firmware needed to be updated... But the info on Newegg sight could be wrong or I was sent the wrong box so many years go.
 
I will try those directions when I get home to see if works.
 
Actually a little searching through Rosewill's site shows that Newegg's site might truely be incorrcet
 
Rosewill lists the chip as
88W8335 + 88W8010 Marvell
 
Found at:
[http://www.rosewill.com/products/s_935/productDetail.htm](http://www.rosewill.com/products/s_935/productDetail.htm)
 
So all this time and I was searching for the wrong thing.No....not all this time.:p
I assume you followed the directions to that link implicitly?

---

### Post by jtarin on 2011-06-11
[Your 64-bit driver]("http://download.cnet.com/Marvell-Libertas-802-11g-b-Wireless-LAN-Client-Adapter/3000-2112_4-166388.html"). :)
Build,Build,Build,Build.

---

### Post by VOT Productions on 2011-06-11
For ndiswrapper to work, you need to do **sudo apt-get install ndiswrapper**

---

### Post by VOT Productions on 2011-06-11
> **Fat-n00b said:**
> 
[CODE] 
 
ndiswrapper -i mrv8335.inf 
????



This makes your driver be the one above using Ndiswrapper 

> **Fat-n00b said:**
> 

diswrapper -m
????

 

Not sure why you have to do that, but it removes the driver.

> **Fat-n00b said:**
> 

rm -rf ./mrv
?????

Removes the mrv folder.

Follow the ndiswrapper command. Then if it doesn't work try the rest.
Use the link above from jtarin for the .inf file.

---

### Post by jtarin on 2011-06-11
> **VOT Productions said:**
> For ndiswrapper to work, you need to do **sudo apt-get install ndiswrapper**
Good Point. I think it was assumed by linking to that page of Ubuntu Documentation. Reading it over it only talks about configuring....not installing.So Fat-n00b check to see if you have it installed....if not follow VOT Productions suggestion on installing.

---

### Post by VOT Productions on 2011-06-11
This forum needs a thanks button.

---

### Post by Fat-n00b on 2011-06-11
> **jtarin said:**
> [Your 64-bit driver]("http://download.cnet.com/Marvell-Libertas-802-11g-b-Wireless-LAN-Client-Adapter/3000-2112_4-166388.html"). :)
Build,Build,Build,Build.

Guys thanks for all the help so far... I feel we are getting closer... But I am not sure if it is not working or is it that I dont know where I need to be looking for wireless connections... How do I view a list of connections?

So status so far:

So I followed the directions (but replaced the url with path info to the .inf file of WinX64 driver that was downloaded from link above).  Was not sure which INF file to use?

BTW did you know that ndiswrapper tool has a GUI...

So now I have installed that and the ndiswrapper tool GUI says that the hardware is present for driver Netmw26... (the WinX64 driver).  

I then did a hard reboot.  But best I can tell nothing has changed lspci still list the same thing...

So now how do I test my connection... below is the result if I try to use iwlist
```
ubuntu@SlowPoke:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```How do I know I that wlan0 is the interface I need to scan?

---

### Post by jtarin on 2011-06-11
Post the results from ```
ifconfig
```

---

### Post by jtarin on 2011-06-11
> **Fat-n00b said:**
> 
I then did a hard reboot.  But best I can tell nothing has changed lspci still list the same thing...
"lspci" will not change.....that is the equipment.....your installing the module (driver) for that.

---

### Post by wildmanne39 on 2011-06-11
> **jtarin said:**
> [Your 64-bit driver]("http://download.cnet.com/Marvell-Libertas-802-11g-b-Wireless-LAN-Client-Adapter/3000-2112_4-166388.html"). :)
Build,Build,Build,Build.Hi, that is great you found that driver I looked all over and just could not find it yesterday.

---

### Post by jtarin on 2011-06-11
> **wildmanne39 said:**
> Hi, that is great you found that driver I looked all over and just could not find it yesterday.
Well the link on the Ubuntu Documentation page re-directed to a wrong page so I entered it in Google and came up with [this]("http://www.google.com/search?sclient=psy&hl=en&site=webhp&source=hp&q=http%3A%2F%2Fwww.versiontracker.com%2Fdyn%2Fmoreinfo%2Fwin%2F131948&btnG=Google+Search") and as you can see the selection is narrowed down considerably. it's not always that easy. :p The Ubuntu Documentation page should be brought up to date.

---

### Post by wildmanne39 on 2011-06-12
> **jtarin said:**
> Well the link on the Ubuntu Documentation page re-directed to a wrong page so I entered it in Google and came up with [this]("http://www.google.com/search?sclient=psy&hl=en&site=webhp&source=hp&q=http%3A%2F%2Fwww.versiontracker.com%2Fdyn%2Fmoreinfo%2Fwin%2F131948&btnG=Google+Search") and as you can see the selection is narrowed down considerably. it's not always that easy. :p The Ubuntu Documentation page should be brought up to date.
Hi, can anyone change the link on that page?

---

### Post by jtarin on 2011-06-12
> **wildmanne39 said:**
> Hi, can anyone change the link on that page?
Gotta jump through a hoop or two which I'm too lazy to do.....look to the bottom....I think there's a link.

---

### Post by Fat-n00b on 2011-06-12
Thanks guys...

ifconfig returns:
```
@SlowPoke:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:88:1b:49  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe88:1b49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30626 (30.6 KB)  TX bytes:10654 (10.6 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)
```

---

### Post by VOT Productions on 2011-06-12
Run in a terminal **ifup wlan0**

---

### Post by Fat-n00b on 2011-06-12
> **VOT Productions said:**
> Run in a terminal **ifup wlan0**

```
SlowPoke:~$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
```

---

### Post by jtarin on 2011-06-12
Whenever you get "permission denied" after issuing a command try prefacing the command with "sudo". 9 out of 10 it should work.

---

### Post by Fat-n00b on 2011-06-12
> **jtarin said:**
> Whenever you get "permission denied" after issuing a command try prefacing the command with "sudo". 9 out of 10 it should work.

Thank you... Good to know.
```

SlowPoke:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0
```

---

### Post by jtarin on 2011-06-12
Run the command "lsmod".

---

### Post by Fat-n00b on 2011-06-13
> **jtarin said:**
> Run the command "lsmod".

```
Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
fglrx                2739144  102 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17113  0 
ndiswrapper           249811  0 
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_usbmidi_lib,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
edac_core              53845  0 
psmouse                73535  0 
sp5100_tco             13744  0 
edac_mce_amd           23464  0 
i2c_piix4              13303  0 
k8temp                 13016  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
parport_pc             36959  1 
asus_atk0110           17976  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  6 
r8169                  48022  0 
pata_atiixp            13165  0 
libahci                26642  1 ahci

```

---

### Post by Fat-n00b on 2011-06-13
THANK YOU GUYS!

Ok not sure what changed or what happened but IT WORKS!

---

### Post by jtarin on 2011-06-13
Good enough for me!!:p

---

