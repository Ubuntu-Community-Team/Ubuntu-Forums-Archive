---
title: "wan0 missing 12.04"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by gshacte on 2013-11-26
I have an older Dell system on which I installed Ubunbtu 12.04 desktop.  It has no internal wireless, so I purchased a Panda mini usb flash. It requires no driver install. lsusb does show it in the list. However, ifconfig only shows eth0 and the loopback, but there is no wan0. Your advice would be appreciated.

---

### Post by chili555 on 2013-11-26
I assume you mean w**l**an0. Please show us what it says:```
lsusb
```Thanks.

---

### Post by gshacte on 2013-11-26
interfaces has 
 auto lo
 iface lo inet loopback

Output of ifconfig shows only eth0 and lo

No error message when doing 'sudo service network-manager restgart'

---

### Post by gshacte on 2013-11-26
Sorry. lsusb shows
Bus 001 device 003:id 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
etc

---

### Post by chili555 on 2013-11-26
The fix actually depends on your exact version. Please let us see:```
uname -r
modinfo rt2800usb | grep 3070
```If you get a result from the second command, then show us:```
sudo modprobe rt2800usb
iwconfig
```

---

### Post by gshacte on 2013-11-26
uname -r
    3.8.0-29-generic
modinfo......
     alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
     alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
     alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*

modprobe ....
    WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
 (After the above command was issued, the led on the wireless flash began flashing)

iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.

   
    
Thank you. If you can explain what just occurred, I would appreciate it.

---

### Post by chili555 on 2013-11-26
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.Let's see if we really need this and try to fix it:```
cat  /etc/modprobe.d/blacklist.save
cat  /etc/modprobe.d/blacklist.conf
```> (After the above command was issued, the led on the wireless flash began flashing)And did it connect?> If you can explain what just occurred, I would appreciate it. The correct driver rt2800usb didn't load automagically; let's try to find out why and correct it. If you have been trying to fix things by blacklisting, I suspect we're going to find out why!

---

### Post by gshacte on 2013-11-26
I guess (and I am guessing - I am not on a level where I should even be speculating, but I do anyway!) that the modprobe loaded the needed module to the Kernal. The wireless flash usb is sold as plug and play for this level of Linux, so perhaps I would mention to the wireless flash vendor that this process was required to get the environment going.

---

### Post by chili555 on 2013-11-26
> **gshacte said:**
> I guess (and I am guessing - I am not on a level where I should even be speculating, but I do anyway!) that the modprobe loaded the needed module to the Kernal. The wireless flash usb is sold as plug and play for this level of Linux, so perhaps I would mention to the wireless flash vendor that this process was required to get the environment going.I think that remains to be determined. If you have a blacklist.save file, someone, maybe you, has made a change that may have helped or hurt to get the device going on boot. Let's dig deeper before we draw any conclusions.

---

### Post by gshacte on 2013-11-26
blacklist.save
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
*******************************************
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
blacklist rt2800usb
blacklist b43

---

### Post by chili555 on 2013-11-26
Ah, haaa! See, the needed driver rt2800usb is blacklisted; that's why it didn't load on boot. We really don't need the .save file, let's remove it:```
sudo rm /etc/modprobe.d/blacklist.save
```Now let's fix the .conf file:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove these two lines:```
blacklist rt2800usb
blacklist b43 
```Proofread carefully, save and close gedit. Reboot and give us your report.

---

### Post by gshacte on 2013-11-26
Your suspicion was correct.  I had pursued this on my own before opening the thread, specifically regarding the blacklist.conf file. When you asked me to send the contents of blacklist.saved and conf to you, a file I had played with earlier I became confident that the problem was of my own creation. As you can see from the content of the files above, I guess the presence of rt2800usb in the file prevented the module from being installed. 

Before contacting you, I did add the blacklist b43to the file (based on ubuntuforums.org/showthread.php?t=1966631  entry #9) that I found. I see now that b43  module had nothing to do with the particular device I am using and that it was a mistake to add it to the blacklist file. But I honestly do not recall entering rt2800usb into the blacklist.conf file. But I must have. Sorry I ended up having you resolve a problem that was of my own creation. I removed the b43 and rt2800usb from the blacklist.conf and booted, and all is well. I am up on the wireless now. Thanks much again for your help and sorry for what amounted to my unintentional misdirection.

---

### Post by chili555 on 2013-11-27
No worries! I have done the same myself in an attempt to fix something. I have to ask myself if I was actually the person to make a change in a file or preferences. It happens to all of us.

I'm just glad it's working now. Have fun!

---

### Post by gshacte on 2013-12-01
Thanks for the support. Your suspicion was correct. I had played with the blacklist file earlier, based on a link that I found that said that the presence of some modules can lead to the problem. I realize now that adding b43 to the list ([http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631))  (item#9) has nothing to do with my issue. But I am at a loss to explain the blacklist of rt2800usb. I don't recall adding that, unless, when I in error downloaded a driver for the wireless flash from the Panda site, which in my case, was not needed, that software added that item to the list after backing up the blacklist file. In any case, I am in good shape and I appreciate your attention to this. You can close this out as resolved.

---

### Post by chili555 on 2013-12-01
Only the original poster is allowed to mark a thread as solved. Please do! [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

