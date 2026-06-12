---
title: "Wirless not working."
date: 2010-10-01
forum: New to Ubuntu
---

### Post by dommyp15 on 2010-10-01
So im a complete newbie to ubuntu and I installed the 32 bit version on my dell dimension e310 desktop pc. I have a linksys wirless-g PCI wireless network adapter and It wont even detect any networks. I installed it by just downloading it from the web and did not use a CD. Any suggestions are much appreciated.

Thanks!

---

### Post by djyoung4 on 2010-10-01
> **dommyp15 said:**
> So im a complete newbie to ubuntu and I installed the 32 bit version on my dell dimension e310 desktop pc. I have a linksys wirless-g PCI wireless network adapter and It wont even detect any networks. I installed it by just downloading it from the web and did not use a CD. Any suggestions are much appreciated.

Thanks!
did you enable the driver.  System --> Administration --> Hardware Drivers
enable the driver if there is one there otherwise try
```
ifconfig
```
in a terminal and post the results

---

### Post by dommyp15 on 2010-10-01
It said there are no proprietary drivers available. The output from the terminal reads...

eth0       Link encap: Ethernet   HWaddr 00:16:76:38:30:92
             UP BROADCAST MULTICAST  MTU: 1500  Metric: 1
             RX packets : 0 errors : 0 dropped : 0 overruns : 0 frame : 0
             TX packets : 0 errors : 0 dropped : 0 overruns : 0 carrier : 0
             collisions : 0 txqueuelen : 1000
             RX bytes : 0 ( 0.0 B)  TX bytes : 0 ( 0.0 B)

lo          Link encap : Local Loopback
             inet addr : 127.0.0.1  Mask:255.0.0.0
             inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  METRIC:1
            RX packets : 140 errors : 0 dropped : 0 overruns : 0 frame : 0
            TX packets : 140 errors : 0 dropped : 0 overruns : 0 carrier : 0
            collisions : 0 txqueuelen : 0
            RX bytes : 10960 ( 10.9 B)  TX bytes : 10960 ( 10.9 B)

---

### Post by djyoung4 on 2010-10-01
is it a built in wireless card or one you plug into a usb

---

### Post by dommyp15 on 2010-10-01
Its built into a PCI slot

---

### Post by dommyp15 on 2010-10-01
I also have windows xp running on this computer and the wireless works fine on it. I checked to see if the driver/device was enabled in windows and it is.

---

### Post by djyoung4 on 2010-10-01
will you post the output of 
```
lspci
```

---

### Post by Hippytaff on 2010-10-01
Have you tried here 

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

---

### Post by dommyp15 on 2010-10-01
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
    00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
    00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
    00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
    00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
    00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
    00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
    00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
    00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
    00:1f.2 RAID bus controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
    00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    03:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)

---

### Post by Hippytaff on 2010-10-01
```

sudo lsmod | grep bcm4318

```

to see if the driver is installed

---

### Post by dommyp15 on 2010-10-01
Module                  Size  Used by
    nls_iso8859_1           4633  0 
    nls_cp437               6351  0 
    vfat                   10866  0 
    fat                    55350  1 vfat
    usb_storage            49833  0 
    binfmt_misc             7960  1 
    ppdev                   6375  0 
    snd_hda_codec_idt      61450  1 
    snd_hda_intel          25677  2 
    snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
    fbcon                  39270  71 
    tileblit                2487  1 fbcon
    font                    8053  1 fbcon
    snd_hwdep               6924  1 snd_hda_codec
    bitblit                 5811  1 fbcon
    snd_pcm_oss            41394  0 
    softcursor              1565  1 bitblit
    snd_mixer_oss          16299  1 snd_pcm_oss
    snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
    vga16fb                12757  0 
    snd_seq_dummy           1782  0 
    vgastate                9857  1 vga16fb
    snd_seq_oss            31219  0 
    snd_seq_midi            5829  0 
    snd_rawmidi            23420  1 snd_seq_midi
    arc4                    1473  2 
    snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
    snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
    i915                  321160  3 
    drm_kms_helper         30742  1 i915
    snd_timer              23649  2 snd_pcm,snd_seq
    b43                   182322  0 
    snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
    drm                   199204  4 i915,drm_kms_helper
    mac80211              238448  1 b43
    snd                    71106  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
    i2c_algo_bit            6024  1 i915
    cfg80211              148546  2 b43,mac80211
    soundcore               8052  1 snd
    video                  20623  1 i915
    led_class               3764  1 b43
    snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
    output                  2503  1 video
    intel_agp              29095  2 i915
    psmouse                64576  0 
    dell_wmi                2177  0 
    lp                      9336  0 
    dcdbas                  6886  0 
    serio_raw               4918  0 
    parport                37160  2 ppdev,lp
    hid_logitech            8820  0 
    ff_memless              5109  1 hid_logitech
    usbhid                 41084  1 hid_logitech
    hid                    83440  2 hid_logitech,usbhid
    ssb                    45092  1 b43
    e100                   32985  0 
    mii                     5237  1 e100
    dm_raid45              75532  0 
    floppy                 63156  0 
    xor                     4685  1 dm_raid45

---

### Post by dommyp15 on 2010-10-01
the code "grep bcm4318" didnt produce anything

---

### Post by Hippytaff on 2010-10-01
You might need to install the driver using Ndsiwrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318)

---

### Post by dommyp15 on 2010-10-01
Im having trouble with trying to install ndiswrapper. I didnt install from a disk I installed from a direct download from the web. I transfered the files for the program via usb mass storage device but the program doesnt seem to work..can anyone walk me through this?

Thanks!

---

### Post by Hippytaff on 2010-10-02
[http://wwww.ubuntuforums.org/showthread.php?t=523092](http://wwww.ubuntuforums.org/showthread.php?t=523092)

---

### Post by dommyp15 on 2010-10-03
so i have acquired the drivers I need but I'm still having trouble installing them. I am using ndis wrapper but every time I enter to command "sudo ndiswrapper -i (file directory) i get this output..

Manage ndis drivers for ndiswrapper.
-i inffile                     install driver described by .inf file
-d devid driver          use installed 'driver' for 'devid'
-e driver                   remove 'driver'
-l                             list installed drivers
-m                           write configuration in modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX

as usual any suggestions are very appreciated

---

### Post by Hippytaff on 2010-10-04
I think this is a list of possible commands, maybe the syntax your entering is wrong.
 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

### Post by Griffiss on 2010-10-04
Did you include the name of the .inf file where you write '(file directory)'?

Also, it'll be easier for us to help if you write here exactly what you type. Even easier if you include it within code tags ```
like this
```

Do this by preceding the code with the word 'code' in square brackets, and putting '/code' in square brackets at the end. Use this when you give the outputs here too.

---

### Post by lkraemer on 2010-10-04
Ok, you chose to use ndiswrapper.  To blacklist the b43 driver open
a Terminal Console and use:
```

sudo nano /etc/modprobe.d/blacklist.conf

```
 and add B43 at the end.  Use CNTRL O to Save and CNTRL X to exit.
Post the information in the file:
```

cat /etc/modprobe.d/blacklist.conf

```

Post the outout of:
```

ndiswrapper -l

```


You should have done something like the following:

To install the Windows Drivers that are located on your Desktop in a
folder named broadcom (.sys & .inf files):
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l
lsmod
ifconfig
iwconfig

```
Post the output of the last 4 commands.

To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
Blacklist b43 & b44:
```

sudo nano /etc/modprobe.d/blacklist.conf

```
Add B43 & B44 to the end of the file.
ie....
LAST LINE OF FILE.........
B43
B44

Then save the edits.

Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```


lk

---

