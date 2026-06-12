---
title: "Problem with Broadcom Corporation BCM4312 LP-PHY"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by Kenta15 on 2011-08-05
Ok so i haded PCLinuxOS on my computer and it work perfectly and even the wifi with Broadcom Corporation BCM4312 802.11b/g LP-PHY and then for some reason i wanted to move to ubuntu 11.04 and then i couldn't get the wifi to work it connects but then it disconnect again what should i do?

---

### Post by fuzzyworbles on 2011-08-05
OH! i had that mini-pci card once. to get it to work you have to install the correct firmware downloader. go to synaptic and search for broadcom and try the two firmwares that pop up. one of them does the trick, but i forget which.

---

### Post by Kenta15 on 2011-08-05
It seen that i already have does install...

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands please:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep b43
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Kenta15 on 2011-08-05
ok here are the outcomes...

sudo lshw  -C network

```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:91:cd:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:54:3f:f7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)


```nm-tool

```
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        00:23:5A:54:3F:F7

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto Resureccion] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:24:2B:91:CD:0F

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Resureccion:    Infra, 68:7F:74:52:C3:C4, Freq 2442 MHz, Rate 0 Mb/s, Strength 100 WPA
    M&N-guest:       Infra, 68:7F:74:52:C3:C5, Freq 2442 MHz, Rate 54 Mb/s, Strength 100
    RUTH/PC:         Infra, 94:0C:6D:FB:D2:D6, Freq 2437 MHz, Rate 0 Mb/s, Strength 40 WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             206.248.95.217
    DNS:             206.248.79.242


```lspci  -nn | grep 0280
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

```rfkill list all
```
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod  |  grep b43
```
It dosen't show anything
```

---

### Post by wildmanne39 on 2011-08-05
Hi, you have the wrong driver installed it is wl, it should be b43.

Uninstall the wl driver you installed then run this command please.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```
unplug your wired connection and restart your computer, and it should be working if not we may need to black list the old driver.
Thank you

---

### Post by Kenta15 on 2011-08-05
Hi, how do i unistall the wl driver?

---

### Post by wildmanne39 on 2011-08-05
Hi, post the results of these commands please:
```
lsmod | grep b43
```
```
modinfo b43
```
```
dmesg | grep b43
```
```
sudo iwlist scan
```
Thank you

---

### Post by Kenta15 on 2011-08-05
Hi, how do i uninstall the wl driver??
Outcomes:
lsmod  |  grep b43

```
It dosen't show anything
```modinfo b43
```
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       FW13
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     3B39048A306116455E54E68
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,cfg80211
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
```dmesg  |  grep b43
```
It dosen't show anything
```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 68:7F:74:52:C3:C4
                    ESSID:"Resureccion"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-41 dBm  Noise level:-92 dBm
                    IE: Unknown: DD6B0050F204104A0001101044000102103B000103104700103E6AD03EC7A7D2AD4E9E134BAADDA539102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 68:7F:74:52:C3:C5
                    ESSID:"M&N-guest"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-41 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
```

---

### Post by wildmanne39 on 2011-08-05
Hi, run this script and it should get you going.

Down load the file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43 /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
then unplug your wired connection and restart your computer.
Thank you

---

### Post by Kenta15 on 2011-08-05
It show the following error

```
mv: cannot move `b43' to `/lib/firmware/b43': Directory not empty

```

---

### Post by wildmanne39 on 2011-08-05
Hi, ok try it this way.
```
cd Desktop
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

---

### Post by Kenta15 on 2011-08-05
Hi, well i did it and then restarted my computer but it havent change it still does the same...
Here's a video that show what happen
[http://www.youtube.com/watch?v=glbJbdxBSJ4](http://www.youtube.com/watch?v=glbJbdxBSJ4)
and at the end it stay's like that forever

---

### Post by wildmanne39 on 2011-08-05
Hi, I tried to play your video but it will not play on my computer for some reason.
Run this command please
```
lsmod
```
and post the results here.
thank you

---

### Post by Kenta15 on 2011-08-06
Hi here are the results

lsmod
```
Module                  Size  Used by
michael_mic            12540  0 
arc4                   12473  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
radeon                900494  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17203  0 
wl                   2642531  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
serio_raw              12990  0 
sp5100_tco             13456  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
shpchp                 32345  0 
video                  18951  0 
ati_agp                13202  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
pata_atiixp            12968  0 
ahci                   21591  2 
atl1c                  36237  0 
libahci                25548  1 ahci

```

---

### Post by wildmanne39 on 2011-08-06
Hi, you do not have any drivers installed for your card.

Try this command again.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```
unplug your wired connection and restart your computer, and it should be working, if not post the results of 
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by Kenta15 on 2011-08-06
Hi thanks for the reply, it still not working here's the outcome:

```
kenta15@Kenta15:~$ cat /etc/modprobe.d/blacklist.conf
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

```

---

### Post by westie457 on 2011-08-06
> **Kenta15 said:**
> Hi thanks for the reply, it still not working here's the outcome:

```
kenta15@Kenta15:~$ cat /etc/modprobe.d/blacklist.conf
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

[COLOR="Red"]# replaced by b43 and ssb.
blacklist bcm43xx[/COLOR]

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

```

Hi you still have the wrong drivers installed.
Open Synaptic Package Manager and type bcm into the quick search box. At the top left corner of the package list pane is a box with a S in it. Click there to bring all installed items to the top. Using the attached screenshot as a guide you need to mark b43-fwcutter and firmware-b43-lpphy-installer for installation. [COLOR="Red"]Only those two[/COLOR]. Mark any other installed packages for complete removal. Click Apply. When this has finished do as wildmanne39 has already suggested. Unplug the wired connection and reboot your computer. Your wireless should now be working.

---

