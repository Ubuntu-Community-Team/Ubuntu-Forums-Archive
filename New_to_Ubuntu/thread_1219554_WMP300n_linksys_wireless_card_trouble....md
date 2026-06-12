---
title: "WMP300n linksys wireless card trouble..."
date: 2009-07-21
forum: New to Ubuntu
---

### Post by shadowber on 2009-07-21
I bought the linksys wmp300n card, and cannot get it working.

I followed the directions posted in this thread ([http://ubuntuforums.org/showthread.php?t=539208](http://ubuntuforums.org/showthread.php?t=539208)) and it still does not work....

can anyone help me?

---

### Post by keplerspeed on 2009-07-21
What exactly did you try from the thread?

Firstly, With a clean install, I would go to system>admin>hardware drivers and see if a driver pops up there. If not, you will need to use ndiswapper and the windows driver.

But firstly, what have you tried, and what have you changed?

---

### Post by shadowber on 2009-07-21
OK, first I tried the driver in hardware drivers, I activated it, but nothing came up... so I deactivated it and followed all the instructions from anewguy 3 or 4 posts in, and.... nothing...

---

### Post by keplerspeed on 2009-07-21
Well I would go back to the driver in hardware drivers. If it is avaliable, try to stay away from ndiswrapper.

But first lets see what chipset you have. Open a terminal, and post the output of:
```

lspci -v | less

```

---

### Post by shadowber on 2009-07-21
what info in particular (its very long)

---

### Post by keplerspeed on 2009-07-21
Sorry, we need the section from that output concerning the wireless card. It cant be seen, as it should be near the bottom. Can you find it, or paste the entire output?

---

### Post by shadowber on 2009-07-21
this it?

02:09.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
        Subsystem: Linksys Device 0060
        Flags: bus master, fast devsel, latency 32, IRQ 17
        Memory at fdef4000 (32-bit, non-prefetchable) [size=16K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

---

### Post by shadowber on 2009-07-21
btw, I have jaunty...

---

### Post by keplerspeed on 2009-07-21
Yes thats it thanks. You have a:
```

Broadcom Corporation BCM43XG (rev 01)

```

Please enter:
```

iwconfig

```

Does wlan0 (or similar) exist?

---

### Post by shadowber on 2009-07-21
I assume you meant iwconfig....

I get 
lo        no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

---

### Post by keplerspeed on 2009-07-21
So you have ndiswapper installed atm?

If so enter:
```

ndiswrapper -l

```
So we can see what driver you have installed.

---

### Post by keplerspeed on 2009-07-21
For ndiswrapper follow this:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by shadowber on 2009-07-21
ok i get this


WARNING: All config files need .conf: /etc/modprobe.d/blacklist-restricted, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipw3945, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4329) present (alternate driver: ssb)

---

### Post by keplerspeed on 2009-07-21
It appears that you have edited the old /etc/modprode.d/blacklist file instead of the new config file /etc/modprode.d/blacklist.conf HOWEVER, it appears that the driver has installed fine, and the hardware is correctly detected.

To have the driver installed fine, but no wlan0 is obscure. Please either reboot or enter this to the terminal and recheck if wlan0 has appeared:
```

sudo depmod -a
sudo modprobe ndiswrapper

```

ACTUALLY:

post here your /etc/modprode.d/blacklist file, and /etc/modprode.d/blacklist.conf files also.

---

### Post by shadowber on 2009-07-21
OK, I edited the new one, and will restart now... I'll tell you if there's any change... and thanx for your help...

---

### Post by shadowber on 2009-07-21
well, no change...

---

### Post by keplerspeed on 2009-07-21
Can you post what is in your blacklist and blacklsit.conf files?

the /etc/modprode.d/blacklist file shouldnt exist, delete it.

The /etc/modprode.d/blacklist.conf file should have this at the end, when using ndiswrapper:
```

blacklist bcm43xx

blacklist b43

blacklist b43legacy

blacklist ssb

```

---

### Post by shadowber on 2009-07-21
theres nothing in blacklist (though I put that line in there and took it out once you told me I needed to edit the .conf one)

and this is in the .conf

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

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# broadcom default no firmware, using ndiswrapper instead
blacklist BCM43XG

---

### Post by keplerspeed on 2009-07-21
Ok please remove the "blacklist" file.

Then in blacklist.conf remove "# broadcom default no firmware, using ndiswrapper instead
blacklist BCM43XG"

and add the lines as I have said above in post #17, then reboot.

---

### Post by shadowber on 2009-07-21
ok I did all that, however there is no change...

---

### Post by keplerspeed on 2009-07-21
Hmm. Not sure now. Maybe one of the wireless guru's can shed some light on this. Kevdog?

The BCM43XG is hard to find info on. Doesnt sound like the best card. Can you take it back? Wireless is one thing with linux that you need to be carefull with, ensure your card is well supported before buying.

---

### Post by shadowber on 2009-07-21
ye I guess I can take it back....

do you have a wireless n card you can suggest to me?

---

### Post by keplerspeed on 2009-07-21
OOOOh yes. Get a D-Link DWA-510 (ver. A1).

Works out of the box. see here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

Pretty much the ralink chipsets have good support. Broadcom generally is harder to set up.

---

### Post by shadowber on 2009-07-21
ok thanx... and thanx for trying to help with this one... I will return this if I dont fix it in two days....

---

### Post by keplerspeed on 2009-07-21
Cheers, hope you work something out!

---

### Post by kevdog on 2009-07-22
I dont know a lot about that card.  Can you post the whole thing:
lsmod and lshw -C network

---

### Post by shadowber on 2009-07-22
lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             91016  0 
vboxdrv               117544  1 vboxnetflt
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
ndiswrapper           193436  0 
sbp2                   30476  0 
lp                     17156  0 
snd_hda_intel         434100  3 
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
nvidia               9550692  36 
psmouse                61972  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  15620  0 
i2c_nforce2            14980  0 
agpgart                42696  1 nvidia
serio_raw              13316  0 
soundcore              15200  1 snd
pcspkr                 10496  0 
k8temp                 12416  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
joydev                 18368  0 
usbhid                 42336  0 
forcedeth              61712  0 
ssb                    41220  0 
floppy                 64324  0 
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
vesafb                 13828  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit



and
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:f8:f7:13:5d:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by kevdog on 2009-07-23
I see ndiswrapper and ssb modules loaded.  What driver are you trying to use?

---

### Post by shadowber on 2009-07-23
I beleive its bcmwl5


I got it from here... [http://ubuntuforums.org/showpost.php?p=3284510&postcount=5](http://ubuntuforums.org/showpost.php?p=3284510&postcount=5)

---

