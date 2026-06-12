---
title: "Must use 'sudo modeprobe b43' after reboot"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by colleps1 on 2014-01-31
I have to use 'sudo modprobe b43' every time i power on and/or reboot. This is a very simple and quick thing to do, however... My girl friend is using my laptop for school and shes not real swift with the terminal and gets confused easily as she is still very green to Ubuntu. Is there any way to make the wireless automatically work when rebooting/powering on with out having to to run the afore mentioned?


lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by chili555 on 2014-01-31
It may be blacklisted somewhere; let's check: ```
ls /etc/modprobe.d
```We'll eliminate the blacklist and it should then be good to go.

---

### Post by colleps1 on 2014-01-31
ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         iwlwifi.conf
b43.conf                    blacklist-oss.conf           mlx4.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf  Untitled Document 1
blacklist.conf              blacklist-watchdog.conf      vmwgfx-fbdev.conf
blacklist-firewire.conf     broadcom-sta-common.conf
blacklist-framebuffer.conf  dkms.conf

---

### Post by chili555 on 2014-01-31
Here in UbuntuForums HQ, we have a very technical term: Holee Molee! That's a busy directory you have there! Let's have a peek at a few of these and see if we can first, spot and correct the trouble; and, second, get rid of useless clutter:```
cd /etc/modprobe.d
cat iwlwifi.conf
cat blacklist.conf
cat broadcom-sta-common.conf
cat b43.conf
```And my personal favorite:```
cat Untitled\ Document\ 1
```If this one is blank, simply remove it:```
sudo rm Untitled\ Document\ 1
```

---

### Post by colleps1 on 2014-01-31
Here is what I got:):P

kevo@kevo-Ubuntu:~$ cd /etc/modprobe.d
kevo@kevo-Ubuntu:/etc/modprobe.d$ cat iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
kevo@kevo-Ubuntu:/etc/modprobe.d$ cat blacklist.conf
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
blacklist bcma
blacklist brcm80211
blacklist acer-wmi
kevo@kevo-Ubuntu:/etc/modprobe.d$ cat broadcom-sta-common.conf
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
kevo@kevo-Ubuntu:/etc/modprobe.d$ cat b43.conf
options b43 hwtkip=1

---

### Post by colleps1 on 2014-01-31
kevo@kevo-Ubuntu:~$ cat Untitled\ Document\ 1
cat: Untitled Document 1: No such file or directory

Did I do that in the correct directory?

---

### Post by chili555 on 2014-01-31
There you see b43 is blacklisted. Let's fix it:```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```There is a minor problem we need to address:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines:```
blacklist bcma
blacklist brcm80211
```First bcma is a dependency of b43; it will eventually get loaded, but why throw out a roadblock? Second, there isn't a module named brcm80211 since about Ubuntu 5.04 or some such! Proofread your changes carefully, save and close gedit. Reboot. Is it working perfectly now?

PS - I am a bit skeptical about this:> options b43 hwtkip=1But if it's working as expected, we won't touch or even breathe on it!

---

### Post by colleps1 on 2014-01-31
It's people like you that make Ubuntu amazing!! Im glad I switched 8 years ago. All is working well. Did a shut down and repowered and it worked. 
Thank you Thank you. I will mark this as [SOLVED]

---

### Post by chili555 on 2014-01-31
Awesome! Glad it's working. Have fun!

---

### Post by Ralph_Lam on 2014-02-02
post deleted.  Posting in new thread

---

### Post by chili555 on 2014-02-02
> or soul I start a new thread?Yes, please, and include:```
lspci -nn | grep 0280
```

---

