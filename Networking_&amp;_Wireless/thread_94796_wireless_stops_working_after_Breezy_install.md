---
title: "wireless stops working after Breezy install"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by o_fortuna on 2005-11-24
I just installed Breezy on my system over Hoary using an install cd, and now the wireless won't work
It's a d-link dwl ag-530 (Atheros AR5212 802.11abg rev 01). It worked just fine with ndiswrapper under Hoary.

In Breezy, under System-->Administration-->Networking, it's detected as 'ath0' (it was 'wlan0' under Hoary), but if I click 'configure', it just sits there forever doing nothing:confused: . I can't do anything that requires root privaleges, log off, or shut down/restart without using the power button, even if I close the window (it just sits forever doing nothing if I try anything).
'ath0' is listed under iwconfig, but any configuration changes I make don't have any effect, and it still won't connect to the network.

Typing 'sudo ifup ath0' just gives me 'Ignoring unknown interface ath0=ath0.' Trying to do mostly anything with the card either does nothing or it does the same thing as clicking 'configure' in the Networing applet.

I tried setting it up with ndiswrapper using the same drivers that worked perfectly in Hoary, but even though it shows 'driver present, hardware present', there is no 'wlan0' to configure in Networking.
This is really confusing. How can I get the new drivers to work/get the old drivers to work? I dont' get why the hardware would *stop* working after I upgraded...

---

### Post by Lambert on 2005-11-25
My atheros card worked perfectly in breezy so not sure why you had such problems with it so far. 

With ath0 locking up like that not sure I can offer any help there except this.

From terminal run this command

```
sudo ifconfig -v ath0 up
```

You may see some error output, if so post that here. It may lock you up again though running this.

For ndiswrapper you need to remove the native driver and blacklist it otherwise there will be a driver conflict or you won't even see wlan0.

```
 sudo modprobe -r ath_pci
```

then

```
sudo echo ath_pci >> /etc/modprobe.d/blacklist
```

This adds the atheros driver so it doesn't load.

then go through the process of setting up and using ndiswrapper.

---

### Post by o_fortuna on 2005-11-25
```
sudo ifconfig -v ath0 up
```
just gives me
```
segmentation fault
```
After that, everything stops working again:( .

Thanks for your help with ndiswrapper, though. I managed to get that working so at least I can get online again:cool: .

---

### Post by o_fortuna on 2005-11-25
I just rebooted my system, and something seems awry.

I had to put this:
```
echo ath_pci >> /etc/modprobe.d/blacklist
```
into a root terminal because of
```
sudo echo ath_pci >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
```
But, it seems that, after the restart, this line had no effect, as the ath_pci driver still loaded. I tried to manually disable (modprobe -r) ndiswrapper and ath_pci, and modprobe ndiswrapper again, but it just gave me:
```
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'ath_pci'
```
After I deleted the file, modprobe started working again and I got the network working, but it's a nuisance to have to do this every time I start up the system.

Any clue how to get this working? Thanks!

---

### Post by Lambert on 2005-11-25
2nd time I've seen somebody not have a black list today.

Here is the full output of my blacklist.

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

# watchdog drivers should be loaded only if a watchdog daemon is installed
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i8xx_tco
blacklist ib700wdt
blacklist indydog
blacklist machzwd
blacklist mixcomwd
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist sbc60xxwdt
blacklist sc1200wdt
blacklist sc520_wdt
blacklist scx200_wdt
blacklist softdog
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


Create a file and copy this into it then add ath_pci to the bottom and try again.

---

### Post by o_fortuna on 2005-11-25
Thanks for your help! I added 'blacklist ath_pci' since just 'ath_pci' gave me an error. Everything seems to work now! Thanks very much!:D

EDIT: On second thought, although adding 'blacklist ath_pci' doesn't cause any error, for some strange reason, it still appeared after I restarted my computer :confused: .

---

