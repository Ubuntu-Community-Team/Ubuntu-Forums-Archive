---
title: "How to reinstall wifi drivers"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by afonscortada on 2014-01-12
I'm a totally beginer in Ubuntu. During my first experimentations, I've modificated the drivers of the wifi card.

How should reinstall the drivers?

When I put "lspci" in the console, it returns this:

10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Thank you.

---

### Post by chili555 on 2014-01-12
I doubt if you modificated the drivers themselves; you may have tried to apply a driver parameter. May we see:```
cat /etc/modprobe.d/iwlwifi.conf
ls /etc/modprobe.d
dmesg | grep iwl
```

---

### Post by afonscortada on 2014-01-13
This is what returns:

casa@casa-HP-Compaq-6910p:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi nohwcrypt=1

casa@casa-HP-Compaq-6910p:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-rare-network.conf  iwlegacy.conf~
ath9k.conf                  blacklist-watchdog.conf      iwlwifi.conf
blacklist-ath_pci.conf      iwl4965.conf                 oss-compat.conf
blacklist.conf              iwlagn.conf                  vmwgfx-fbdev.conf
blacklist-firewire.conf     iwlagn.conf~                 wlan.conf
blacklist-framebuffer.conf  iwled.conf                   wlan.conf~
blacklist-modem.conf        iwled.conf~
blacklist-oss.conf          iwlegacy.conf

casa@casa-HP-Compaq-6910p:~$ dmesg | grep iwl
[   15.777961] iwl4965: Unknown parameter `nohwcrypt'
[  843.568713] iwl4965: Unknown parameter `nohwcrypt'

---

### Post by chili555 on 2014-01-13
As you can see, 'nohwcrypt' isn't a valid parameter for your device. Let's remove the file completely:```
sudo rm /etc/modprobe.d/iwlwifi.conf
```In more recent Ubuntu versions, the file ought to contain a lot more than what was there; which version are you running?```
lsb_release -d
```I am also suspicious about these files;let's have a look:```
cat /etc/modprobe.d/iwlagn.conf
cat /etc/modprobe.d/wlan.conf
cat /etc/modprobe.d/iwled.conf
cat /etc/modprobe.d/iwlegacy.conf 
cat /etc/modprobe.d/iwl4965.conf
```You don't have an Atheros wireless card, so let's eliminate that file:```
sudo rm /etc/modprobe.d/ath9k.conf
```You have been very busy!

What issue were you trying to solve when you added these files? Maybe there is a better way.

---

### Post by afonscortada on 2014-01-13
I'm running Ubuntu 12.04.4 LTS.

Let's see the files:

~$ cat /modprobe.d/iwlagn.conf
options iwlagn led_mode=1
~$ cat /modprobe.d/wlan.conf
options iwlcore led_mode=1
options iwlagn led_mode=1
options iwifi led_mode=1
~$ cat /modprobe.d/iwled.conf
~$ cat /modprobe.d/iwlegacy.conf
options iwlegacy led_mode=1

~$ cat /modprobe.d/iwl4965.conf
options iwl4965 nohwcrypt=0

I was trying to enable de constantly blinking mode of the wireless led.

---

### Post by chili555 on 2014-01-13
On my 12.04 system, the driver for your device is iwl4965; confirm:```
lsmod | grep iwl
```You should see iwl4965 and iwl-legacy (*not *iwlegacy)  loaded. If your system reports different, stop and tell us about it before you proceed.

Assuming these are correct, let's fix up the files:```
sudo rm /etc/modprobe.d/iwlagn.conf
sudo rm /etc/modprobe.d/wlan.conf
sudo rm /etc/modprobe.d/iwled.conf
sudo rm /etc/modprobe.d/iwlegacy.conf
sudo rm /etc/modprobe.d/iwl4965.conf
gksudo gedit /etc/modprobe.d/iwl-legacy.conf 
```A new empty file will open. Add a single line:```
options iwl-legacy led_mode=1
```Proofread, save and close the file. Reboot and tell us how it's working.

---

### Post by afonscortada on 2014-01-14
This is what returns:

iwl_legacy             71334  0 
mac80211              436493  1 iwl_legacy
cfg80211              178877  2 iwl_legacy,mac80211

---

### Post by chili555 on 2014-01-14
> **afonscortada said:**
> This is what returns:

iwl_legacy             71334  0 
mac80211              436493  1 iwl_legacy
cfg80211              178877  2 iwl_legacy,mac80211We don't actually see iwl4965 loaded. Please reboot so we have a clean slate and let's then see if we can see any errors or problems:```
sudo modprobe iwl4965
dmesg | grep iwl
```Thanks.

---

### Post by afonscortada on 2014-01-14
I've done this:

> 
```
sudo rm /etc/modprobe.d/iwlagn.conf
sudo rm /etc/modprobe.d/wlan.conf
sudo rm /etc/modprobe.d/iwled.conf
sudo rm /etc/modprobe.d/iwlegacy.conf
sudo rm /etc/modprobe.d/iwl4965.conf
gksudo gedit /etc/modprobe.d/iwl-legacy.conf 
```

```
options iwl-legacy led_mode=1
```
.

And it's working!

Thank you a lot!

---

### Post by chili555 on 2014-01-14
Awesome! Glad it's working.

---

