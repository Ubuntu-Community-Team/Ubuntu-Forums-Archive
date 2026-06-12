---
title: "No wifi connection on ASUS X75V RALINK RT3290STA"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by anton22 on 2014-11-26
Please help.
Already tried to intall rt3290sta driver.

```

anton@berocket:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr bc:ee:7b:b6:64:f8  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::beee:7bff:feb6:64f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1228777 (1.2 MB)  TX bytes:1228777 (1.2 MB)

ra0       Link encap:Ethernet  HWaddr 48:5a:b6:7b:a6:a5  
          inet6 addr: fe80::4a5a:b6ff:fe7b:a6a5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```

```

anton@berocket:~$ iwconfig 
ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.


```

```

anton@berocket:~$ lsmod
Module                  Size  Used by
wl                   4207846  0 
lib80211               14381  1 wl
bbswitch               13943  0 
cfg80211              484040  1 wl
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_intel          56451  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
mxm_wmi                13021  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143148  0 
kvm                   455785  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
snd                    69322  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport_pc             32701  0 
ppdev                  17671  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
lpc_ich                21080  0 
nvidia              10675249  35 
mei_me                 18627  0 
soundcore              12680  1 snd
rt3290sta            1170520  1 
mei                    82276  1 mei_me
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i915                  784207  2 
wmi                    19177  2 mxm_wmi,asus_wmi
video                  19476  2 i915,asus_wmi
drm_kms_helper         55071  1 i915
mac_hid                13205  0 
drm                   303102  5 i915,drm_kms_helper,nvidia
i2c_algo_bit           13413  1 i915
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  3 hid_generic,usbhid
psmouse               106714  0 
ahci                   25819  3 
alx                    32452  0 
libahci                32716  1 ahci
mdio                   13807  1 alx

```

```

anton@berocket:~$ uname -a
Linux berocket 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by chili555 on 2014-11-26
May we also see:```
rfkill list all
lspci -nn | grep 0280
```Thanks.

---

### Post by anton22 on 2014-11-26
Sure.

```

anton@berocket:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```

03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]

```

Thanks for helping

Maybe it will help to:

```

anton@berocket:~$ iwlist scanning
ra0       No scan results

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

```

anton@berocket:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7a1a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7a18000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7900000-f79fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7800000-f78fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7a17000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7a16000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: medium devsel, IRQ 10
    Memory at f7a15000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]

01:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 21ba
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

03:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
    Subsystem: Foxconn International, Inc. Device e055
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7910000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860

03:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
    Subsystem: Foxconn International, Inc. Device e056
    Flags: bus master, fast devsel, latency 0, IRQ 3
    Memory at f7900000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7800000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: alx

```

---

### Post by chili555 on 2014-11-26
Your device is supported by the native driver rt2800pci. Why did you feel the need to compile, at some difficuly, I suspect, an older, less-good driver?

You also have a conflicting driver installed and I suggest we remove it:```
sudo apt-get purge bcmwl-kernel-source
```

---

### Post by anton22 on 2014-11-26
When i just installed clean ubuntu 14.01 wifi was not working too, so i tried to looking for solution.
Could you help me make it work please?

Executed:
```

sudo apt-get purge bcmwl-kernel-source
```

---

### Post by chili555 on 2014-11-26
Please try:```
sudo modprobe -r rt3290sta
sudo modprobe rt2800pci
iwconfig
dmesg | grep rt2
```Thanks.

---

### Post by anton22 on 2014-11-26
```

anton@berocket:~$ sudo modprobe -r rt3290sta
modprobe: FATAL: Module rt3290sta is in use.

```

```

anton@berocket:~$ sudo modprobe rt2800pci

```

```

anton@berocket:~$ iwconfig
ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

```

```

anton@berocket:~$ dmesg | grep rt2
[   14.397881] register rt2860
[   18.115951] <==== rt28xx_init, Status=0
[   18.156334] <==== rt28xx_init, Status=0
[   18.195933] <==== rt28xx_init, Status=0

```

Thank you.

---

### Post by chili555 on 2014-11-26
> anton@berocket:~$ sudo modprobe -r rt3290sta
modprobe: FATAL: Module rt3290sta is in use.Oops! Please try:```
sudo ifconfig ra0 down
sudo modprobe -rf rt3290sta
sudo modprobe rt2800pci
iwconfig
dmesg | grep rt2
```

---

### Post by anton22 on 2014-11-26
```

anton@berocket:~$ sudo ifconfig ra0 down
anton@berocket:~$ sudo modprobe -rf rt3290sta
anton@berocket:~$ sudo modprobe rt2800pci
anton@berocket:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

anton@berocket:~$ dmesg | grep rt2
[   14.397881] register rt2860
[   18.115951] <==== rt28xx_init, Status=0
[   18.156334] <==== rt28xx_init, Status=0
[   18.195933] <==== rt28xx_init, Status=0
anton@berocket:~$ 


```

Thank you.

---

### Post by anton22 on 2014-11-26
Maybe you have to know too, just removed fro blacklist:
rt2800pci
rt2x00pci
rt2860pci

---

### Post by chili555 on 2014-11-26
Are rt2800pci and all her cousins loaded and not rt3290sta?```
lsmod | grep -e rt2 -e rt3
```

---

### Post by anton22 on 2014-11-26
I'm not so proficient in installing drivers in Ubuntu, so i just executed what you gave to me

```

anton@berocket:~$ lsmod | grep -e rt2 -e rt3
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              626557  3 rt2x00lib,rt2x00pci,rt2800lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib

```

Just letting you know that wifi connection if off at all.
Earlier i saw Wifi - disconnected, now it's not visible in network.

Thanks

---

### Post by chili555 on 2014-11-26
You are unlikely to get a connection with ethernet attached, which you do have, however, I'd think that an interface wlan0 would show up in iwconfig and some signs of life in dmesg. Would you mind blacklisting rt3290sta and rebooting with the ethernet detached? Then let's gather some diagnostics, still with the ethernet detached:```
iwconfig  >  wifi.txt
dmesg  >> wifi.txt
lsmod | grep rt2  >>  wifi.txt
lsmod  >>  wifi.txt
```Then hook up the ethernet so you can connect. Find the file wifi.txt in your user directory. Paste it here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by anton22 on 2014-11-26
Added to blacklist rt3290sta

Did as you said, here is the link - [http://paste.ubuntu.com/9257567/](http://paste.ubuntu.com/9257567/)

Thanks

---

### Post by anton22 on 2014-11-26
Sorry, seems i did not understand what should i do to reach this one:

"Would you mind blacklisting rt3290sta and rebooting with the ethernet  detached? Then let's gather some diagnostics, still with the ethernet  detached"

Could you explain please?

---

### Post by anton22 on 2014-11-26
Sorry for confusing.
Turned off the network, rebooted, run the commands, here is a link - [http://paste.ubuntu.com/9257701/](http://paste.ubuntu.com/9257701/)
Thanks

---

### Post by chili555 on 2014-11-26
> **anton22 said:**
> Sorry for confusing.
Turned off the network, rebooted, run the commands, here is a link - [http://paste.ubuntu.com/9257701/](http://paste.ubuntu.com/9257701/)
ThanksThis time it appears you have *removed* rt3290sta from the blacklist and added rt2800pci. That's the reverse of what I requested.Please try again.

---

### Post by anton22 on 2014-11-26
> **chili555 said:**
> This time it appears you have *removed* rt3290sta from the blacklist and added rt2800pci. That's the reverse of what I requested.Please try again.

It becomes automatically.
I will run commands and paste results again.

Might could run the ```
sudo dkms remove rt3290sta/2.6.0.0 --all
```  ?


This is my blacklist file [http://paste.ubuntu.com/9257848/](http://paste.ubuntu.com/9257848/)

---

### Post by chili555 on 2014-11-26
> Might could run the
```
sudo dkms remove rt3290sta/2.6.0.0 --all
```
?No, please. Let's see:```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by anton22 on 2014-11-26
Just did what you said again.
Turn off network, reboot, run commands into wifi.txt and then turn network on.
Here is result - [http://paste.ubuntu.com/9257920/](http://paste.ubuntu.com/9257920/)

```

anton@berocket:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt3290sta

```

Thanks for helping.

---

### Post by chili555 on 2014-11-26
> rt3290sta            1170520  1 I need a break. I'll check back a bit later. Maybe Sheldon will offer me a hot beverage...

---

### Post by anton22 on 2014-11-26
Thanks for helping.
If nothing comes on mind i can reinstal ubuntu again so we can start from beginnig.

Hope to hear from you again.

---

### Post by anton22 on 2014-11-26
I started from the beginning and this is what i reached

```


anton@berocket:~$ sudo modprobe -r rt3290sta
modprobe: FATAL: Module rt3290sta is in use.
anton@berocket:~$ sudo ifconfig ra0 down
anton@berocket:~$ sudo modprobe -rf rt3290sta
anton@berocket:~$ sudo modprobe rt2800pci
anton@berocket:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
anton@berocket:~$ dmesg | grep rt2
[   14.780225] register rt2860
[   18.861176] <==== rt28xx_init, Status=0
[   18.900991] <==== rt28xx_init, Status=0
[   18.940369] <==== rt28xx_init, Status=0
[ 1315.529296] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[ 1315.537643] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected


anton@berocket:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

anton@berocket:~$ rfkill unblock 0
anton@berocket:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

anton@berocket:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: &#1054;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1103; &#1085;&#1077; &#1087;&#1086;&#1079;&#1074;&#1086;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1080;&#1079;-&#1079;&#1072; RF-kill


```


PS: after reboot everything get back to rt3290sta

---

### Post by chili555 on 2014-11-27
> PS: after reboot everything get back to rt3290staI assumed you meant you re-installed, no?? How did it get back to rt3290sta? Did you reinstall that, too?

I doubt that an older, less good driver is ever going to fix this:```
anton@berocket:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]
```We probably can fix it, but not by installing a different driver. 

Please clarify what you have done. I'm not sure I can help you much if, while I sleep, you install, re-install, re-download, dkms, etc. and basically change everything we've tried to do so far.

---

### Post by anton22 on 2014-11-27
No no, by reboot i mean "sudo reboot", simple restart of laptop.
Look, we move to 
```

sudo modprobe rt2800pci
```

But after i do ```

sudo reboot

```
It looks like settings for rt3290sta come back.

So what we do to replace driver rt3290sta is not permament, but temporary.

I hope i'm clear.
I did not do anything without you :)

---

### Post by chili555 on 2014-11-27
Is the module asus_nb_wmi loaded?```
lsmod
```You don't have to post the whole list, just tell me if it is or isn't there. If it is, please do:```
sudo -i
echo "options asus_nb_wmi wapf=1" > /etc/modprobe.d/asus.conf
exit
```Reboot and show me:```
rfkill list all
```

---

### Post by anton22 on 2014-11-27
I had
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi

So i did what you said, doing reboot.

```

anton@berocket:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by anton22 on 2014-11-27
Hey, there is Wi Fi now and seems to be working.
Could you please explain in 2 words what did we do?

Thanks so much, wizard!

---

### Post by chili555 on 2014-11-27
I can't explain it in two words, but the little module that is supposed to translate key presses into action, asus_nb_wmi, often needs a parameter to work correctly. I hate to admit that I discovered and corrected this a few months ago by trial and error, not by wizardry. 

What is even worse is that the parameter is sometimes =0, most often =1, and infrequently =4. I took my best shot and it worked.

---

### Post by anton22 on 2014-11-27
```

anton@berocket:~$ dmesg | grep -e ra0 -e rt2
[   14.686497] register rt2860
[   18.120611] <==== rt28xx_init, Status=0
[   18.210843] <==== rt28xx_init, Status=0
[   18.300853] <==== rt28xx_init, Status=0

```

I'm sitting via Wi-Fi now. Need to test a little, but it's progress that i can connect at all.
So could you tell me what was wrong with it? So i know for future, in case of reinstalling ubuntu, what should i do to make it work?

Thanks.

---

### Post by anton22 on 2014-11-27
So after i reinstall ubuntu again, this would be enough to execute?

```

sudo -i
echo "options asus_nb_wmi wapf=1" > /etc/modprobe.d/asus.conf
exit
```

Thanks.

---

### Post by chili555 on 2014-11-27
> **anton22 said:**
> So after i reinstall ubuntu again, this would be enough to execute?

```

sudo -i
echo "options asus_nb_wmi wapf=1" > /etc/modprobe.d/asus.conf
exit
```

Thanks.That and a reboot should do it. Please use thread tools at the top to mark Solved.

---

### Post by anton22 on 2014-11-27
Thank you a lot.
Good luck!

---

