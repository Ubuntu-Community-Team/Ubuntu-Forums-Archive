---
title: "Asus USB-N13 Wireless Adapter Problems"
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2014-05-31
I set up a dual boot Win 7 and Ubuntu 12.04.   Everything went great, except Win 7 cannot get on the internet with my Asus USB-N13 Wireless Adapter.  Ubuntu found the adapter right away and I was online. 

When Win 7 is on, the blue light on the adapter just blinks.  When Ubuntu is on the blue light on the adapter is on steady. 

Has anyone encountered this problem? 

Thank You

---

### Post by praseodym on 2014-05-31
Hi,

please show the outputs of:
```

uname -a
lsusb
iwconfig
lsmod
rfkill list
```

---

### Post by SUPERFITTER on 2014-05-31
dennis@dennis1:~$ uname -a
Linux dennis1 3.2.0-63-generic #95-Ubuntu SMP Thu May 15 23:05:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
dennis@dennis1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
dennis@dennis1:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"XXXXXXXXXXXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:B6:53:35   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.

dennis@dennis1:~$ lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32530  1 
snd_hda_codec_realtek   224215  1 
cx18_alsa              13768  1 
mxl5005s               46356  1 
s5h1409                18842  1 
tuner_simple           18550  1 
tuner_types            24318  1 tuner_simple
cs5345                 13095  1 
tda9887                14154  1 
tda8290                22616  0 
tuner                  27428  2 
arc4                   12529  2 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  4 snd_hda_codec_hdmi,cx18_alsa,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192cu             103277  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111269  1 rtl8192cu
mac80211              506862  3 rtl8192cu,rtl8192c_common,rtlwifi
serio_raw              13211  0 
snd                    79041  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,cx18_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx18                  133528  1 cx18_alsa
dvb_core              110670  1 cx18
cx2341x                28331  1 cx18
videobuf_vmalloc       13589  1 cx18
videobuf_core          26390  2 cx18,videobuf_vmalloc
tveeprom               21249  1 cx18
v4l2_common            16454  4 cs5345,tuner,cx18,cx2341x
videodev               98259  5 cs5345,tuner,cx18,cx2341x,v4l2_common
v4l2_compat_ioctl32    17128  1 videodev
nouveau               775039  3 
cfg80211              205774  2 rtlwifi,mac80211
ttm                    76949  1 nouveau
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi
shpchp                 37201  0 
i915                  478689  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
drm_kms_helper         46978  2 nouveau,i915
joydev                 17693  0 
drm                   241971  6 nouveau,ttm,i915,drm_kms_helper
mac_hid                13253  0 
i2c_algo_bit           13423  3 cx18,nouveau,i915
video                  19651  2 nouveau,i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62190  0 
usbhid                 47238  0 
hid                    99883  1 usbhid
usb_storage            49198  0 
dennis@dennis1:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dennis@dennis1:~$

---

### Post by praseodym on 2014-06-01
Replace the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by SUPERFITTER on 2014-06-02
> **praseodym said:**
> Replace the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

praseodym:

Will this affect my getting on line with Ubuntu 12.04?    

Windows 7 is the only system that will not allow me to get on line.

Thank You

---

### Post by praseodym on 2014-06-02
No, it only replaces the native Linux driver

---

### Post by SUPERFITTER on 2014-06-02
Well I replaced the Linux driver, now I cannot boot into Ubuntu and I still cannot get on line with Windows 7?

---

### Post by praseodym on 2014-06-02
Unplug the stick and try to boot

---

### Post by SUPERFITTER on 2014-06-02
I booted without the stick and it booted ok

---

### Post by SUPERFITTER on 2014-06-03
How do I remove this:

 	Code:
 	sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget [https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

---

### Post by jimmy-jad on 2014-06-03
Am i the only one who realised that this problem is on his win 7 side... ubuntu is working.....

Download and install the windows driver, on the windows side.... 
[http://www.asus.com/Networking/USBN13/HelpDesk_Download/](http://www.asus.com/Networking/USBN13/HelpDesk_Download/)

---

### Post by SUPERFITTER on 2014-06-05
How do I remove this, so I can at least use Ubuntu?

Replace the driver via:
 	Code:
 	sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget [https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

---

### Post by SUPERFITTER on 2014-06-05
> **jimmy-jad said:**
> Am i the only one who realised that this problem is on his win 7 side... ubuntu is working.....

Download and install the windows driver, on the windows side.... 
[http://www.asus.com/Networking/USBN13/HelpDesk_Download/](http://www.asus.com/Networking/USBN13/HelpDesk_Download/)

_[[COLOR=#000000]jimmy-jad[/COLOR]]("http://ubuntuforums.org/member.php?u=1885370")_

That  driver is the same as the one on the disk that came with the Asus  Dongle. There is something in Windows 7 that is either turned off,  has a boxed checked or a box unchecked.  I just don't know where to look to correct the problem.  Ubuntu 12.04 was working great with the dongle before I changed the Linux Driver.  I just have to get it to work with Windows 7 and now Ubuntu.

Thank you for the help!

---

### Post by praseodym on 2014-06-06
Remove it via
```

sudo apt-get remove --purge rtl8192cu*
```
Remove the line "blacklist rtl8192cu" via
```

gksudo gedit /etc/modprobe.d/blacklist.conf
```
Save, close the editor and reboot

---

### Post by SUPERFITTER on 2014-06-06
> **praseodym said:**
> Remove it via
```

sudo apt-get remove --purge rtl8192cu*
```
Remove the line "blacklist rtl8192cu" via
```

gksudo gedit /etc/modprobe.d/blacklist.conf
```
Save, close the editor and reboot

That did not work. If I boot without the dongle and then plug it in, the mouse and screen freezes.  If I reboot with the dongle plugged in I get a black screen with some code and it freezes.

---

### Post by SUPERFITTER on 2014-06-06
dennis@dennis1:~$ 
dennis@dennis1:~$ 
dennis@dennis1:~$ sudo apt-get remove --purge rtl8192cu*
[sudo] password for dennis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8192cu-tjp-dkms_1.6_all.deb
E: Couldn't find any package by regex 'rtl8192cu-tjp-dkms_1.6_all.deb'
dennis@dennis1:~$ 
dennis@dennis1:~$ 
dennis@dennis1:~$ gksudo gedit /etc/modprobe.d/blacklist.conf


blacklist.conf

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
blacklist rtl8192cu
blacklist rtl8192cu



Untitled Document 1 - gedit

Just keeps loading.  Nothing there.

---

### Post by praseodym on 2014-06-06
```
blacklist rtl8192cu
blacklist rtl8192cu
```
Remove these lines and reboot without the dongle. Plug it in and check

```
iwconfig
lsmod

```

---

### Post by SUPERFITTER on 2014-06-07
> **praseodym said:**
> ```
blacklist rtl8192cu
blacklist rtl8192cu
```
Remove these lines and reboot without the dongle. Plug it in and check

```
iwconfig
lsmod

```

dennis@dennis1:~$ blacklist rtl8192cu
blacklist: command not found
dennis@dennis1:~$ blacklist rtl8192cu
blacklist: command not found
dennis@dennis1:~$

---

### Post by praseodym on 2014-06-08
You need to open the file via
```

gksudo gedit /etc/modprobe.d/blacklist.conf
```

Remove the lines, save, close the editor and reboot.

---

### Post by SUPERFITTER on 2014-06-08
Ubuntu now works again with Asus USB-N13 Dongle.  Now I have to get it to work with my [COLOR=#0000ff]_Windows 7_[/COLOR] duel boot.

---

### Post by SUPERFITTER on 2014-06-09
> **SUPERFITTER said:**
> Ubuntu now works again with Asus USB-N13 Dongle.  Now I have to get it to work with my [COLOR=#0000ff]_Windows 7_[/COLOR] duel boot.


Any one know how to get Windows 7 connected to the internet with an Asus USB-N13 dongle

---

### Post by SUPERFITTER on 2014-06-09
Can I use a different brand of Dongle for Windows 7 and my Asus USB-N13 dongle for Ubuntu?  Can I leave them both plugged in all the time without problems when I boot?

---

