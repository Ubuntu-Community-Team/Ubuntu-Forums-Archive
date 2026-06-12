---
title: "xubuntu 11.04 wireless issue"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by Moskupols on 2011-05-28
Hi!
I'm using D-Link DWA-645 Wi-Fi adapter to connect to my home router. Basically it does not confirm non-windows, so i used [_[COLOR="RoyalBlue"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=4804935") solution with Xubuntu 10.10, and it worked perfectly. 
Problems started just after updating to 11.04. Network settings haven't changed, but when i'm trying to connect, it thinks a lot and then answers that it can't do that. What should i do to fix the connection?

---

### Post by terrykiwi83 on 2011-05-28
please post the output of

```

lsmod

```

and

```

inxi -N

```

and open the file /etc/modprobe.d/blacklist.conf and paste its contents here? That'll let us see your active drivers, devices and drivers in use and any items that are blacklisted :)

---

### Post by Moskupols on 2011-05-28
ok, here it is
lsmod:
```

Module                  Size  Used by
arc4                   12473  2 
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
joydev                 17322  0 
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
pcmcia                 39671  0 
snd_seq_midi           13132  0 
i915                  450944  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
drm                   180037  2 i915,drm_kms_helper
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
psmouse                73312  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
ppdev                  12849  0 
irda                  185091  0 
parport_pc             32111  1 
video                  18951  1 i915
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
b44                    35301  0 
firewire_ohci          31504  0 
wbsd                   18373  0 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core 

```

it does not know about program with name "inxi".

blacklist.conf:
```

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

### Post by terrykiwi83 on 2011-05-28
either am blind or I cannot see that your network adapter is installed. What is the make and model of your adapter?

---

### Post by Moskupols on 2011-05-28
[D-link DWA-645]("http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB%2FDLProductCarouselMultiple&cid=1197319492297&p=1197356142823&packedargs=ParentPageID%3D1197335068935%26ProductParentID%3D1195808623950%26TopLevelPageProduct%3DBusiness%26category%3DQuickProductFinder%26locale%3D1195806691854%26term%3DDWA-645&pagename=DLinkEurope-GB%2FDLWrapper")

---

### Post by terrykiwi83 on 2011-05-28
> **Moskupols said:**
> Hi!
I'm using D-Link DWA-645 Wi-Fi adapter to connect to my home router. Basically it does not confirm non-windows, so i used [_[COLOR="RoyalBlue"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=4804935") solution with Xubuntu 10.10, and it worked perfectly. 
Problems started just after updating to 11.04. Network settings haven't changed, but when i'm trying to connect, it thinks a lot and then answers that it can't do that. What should i do to fix the connection?

when you say it thinks, do you mean it actually sees your router (wireless network) and won't connect? or doesn't it even see your network?

---

### Post by Moskupols on 2011-05-28
yes, it detects the network and tries to connect automatically, it requests password

---

### Post by Toz on 2011-05-29
Have a look here: [http://ubuntuforums.org/showthread.php?t=1672881](http://ubuntuforums.org/showthread.php?t=1672881)

---

