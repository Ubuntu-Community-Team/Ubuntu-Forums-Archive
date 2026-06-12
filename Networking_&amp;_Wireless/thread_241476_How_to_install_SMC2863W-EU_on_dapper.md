---
title: "How to install SMC2863W-EU on dapper"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by Dev_Null on 2006-08-22
Since I've been reading tons of useful information on this forum since the day I installed Ubuntu I thought it's my time to give something back to the community.

I've spend a lot of time getting the USB SMC2862W-eu working on my computer (hp pavilion ze4600 laptop) and by now I'm not yet forgotten how I managed to do this. If my computer ever needs a fresh installation and I'm forgotten how to get wireless working, all I'll have to do is to digg up my own post. :)

Finally, this is not a step by step 'copy paste' guide. You'll need to know how to download a file (starting browser etc.) and edit a text file.

let's get started.

**1. Download needed files**
Get ndiswrapper: [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
Get smc drivers: [http://www.smc.com](http://www.smc.com)

**2. Installing ndiswrapper**
Untar the source and change dir to the unpacked source.
```

tar xvzf ndis...tar.gz
cd ndis...
```

If you don't have _build-essential_ and _linux-headers_ install them wit apt-get or synaptic.

Uninstall previous installed ndiswrappar installations. And do a fresh install of the latest version.
```

sudo su
make uninstall
make
make install
```

**3. Instaling the driver**
Unpack the driver with unzip and go into the 'Driver' directory where you'll find 'SMC2862w.inf'.
```

ndiswrapper -i SMC2862w.inf
ndiswrapper -l
```

If everything ok you should see the driver listed.

**4. How it didn't work**
Well, this isn't exactly a usefull part but it took a while for me to get to the next step. This is probably the place where most people get stuck.
```

modprobe ndiswrapper
```

Plugin the stick and press the 'reset' button to reboot your system, since it will probably hang after plugging in the stick.

**5. How to make it work**
First I added apci=off to the kernel boot line and this worked but also disabled QnQ so my cpu was running at full speed all the time => no good, noapic solved this.
This are my current bootoptions in /boot/grub/menu.lst
```

title		Ubuntu
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro noapic
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
```

REBOOT NOW or you'll have to use your reset button again.

I've not yet automated module loading so here are the commands to do it manual. If you do not rmmod rt2570 and you unplug the USB stick it will be picked up by that driver instead of ndiswrapper and it will not work.
```

sudo su
rmmod rt2570
modprobe ndiswrapper
```

plug in the device and have a look the dmesg output
```

dmesg
```

should end with something like this:
```

[17186785.324000] ndiswrapper: driver smc2862w (SMC,06/28/2005, 3.3.25.0) loaded
[17186787.636000] wlan0: vendor: 'SMC2862W-G EZ Connect g 2.4Ghz 802.11g Wireless USB 2.0 Adapter'
[17186787.636000] wlan0: ethernet device 00:04:e2:ed:d9:f1 using NDIS driver smc2862w, 0707:EE13.F.conf
[17186787.636000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
```

To make it possible to have the wlan device  plugged in al the time (at boot) I blklisted the folowing modules in /etc/modprobe.d/blacklist:
```
blacklist islsm
blacklist islsm_usb
blacklist rt2570
```


Goto System > Administration > Networking and configure your network. You can also install wifi-radar or another tool you prefer.

Good luck!

---

