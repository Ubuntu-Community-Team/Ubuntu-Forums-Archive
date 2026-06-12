---
title: "USB Wireless Adapter 0471:20cc Philips driver loads but doesn't associate to device"
date: 2014-07-27
forum: Networking &amp; Wireless
---

### Post by shane-p-kelly7 on 2014-07-27
[B]Background to potential cause
[/B][SIZE=2][SIZE=2]So for a long time my wireless adapter was working with xubuntu 13.10 but then I failed an upgraded to 14.01.  After the failed upgrade it was still working and to fix it I cleaned up the package system and did a apt-get upgrade and everything seem to be working fine.  After a day my wireless stopped working.  I was suggested to post here from [here]("http://www.reddit.com/r/linux/comments/2bnbit/questions_on_wireless_functionality/").
[/SIZE]
[SIZE=3]**The Problem**
[/SIZE][SIZE=2]So I start learning about wireless troubleshooting and the first adapter, the original working one, I try to troubleshoot needs mode switching. So to avoid dealing with that I tried using the 0471 Philiips adapter.  The problem with both of them is that lsmod finds both but the drivers don't load and associate with the device to create a wlan0.  Since at first the drivers didn't load at all, I found out I need the driver [here]("http://wireless.kernel.org/en/users/Drivers/zd1211rw") and since it was already downloaded I just loaded it with modprobe.  I even added it to /etc/modules but in both cases nothing uses it, lsmod:

[/SIZE][/SIZE]```
rt2800usb              27034  0

and 

zd1211rw               63742  0
```
[SIZE=2]
I don't remember why I added the rt2800usb driver but neither of the two are being used. So I'm guessing this is why when I try to find them with ```
sudo lshhw -c network
``` only the Ethernet shows up.


Here is my pastepin from the wireless script: [/SIZE][http://pastebin.ubuntu.com/7876367/](http://pastebin.ubuntu.com/7876367/) for some reason it didn't save the zd1211rw information so I added that manually in the modinfo section. [SIZE=2]

[/SIZE]dmesg also didn't show what I thought would be important so here is the output of dmesg pertaining to my device:
```

[    2.892628] usb 4-2: new low-speed USB device number 2 using ohci-pci[    3.062678] usb 4-2: New USB device found, idVendor=0471, idProduct=20cc
[    3.062680] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.062682] usb 4-2: Product: MCE USB IR Receiver- Spinel plus
[    3.062683] usb 4-2: Manufacturer: PHILIPS
[    3.081706] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    3.083444] input: PHILIPS MCE USB IR Receiver- Spinel plus as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input7
[    3.083561] hid-generic 0003:0471:20CC.0003: input,hiddev0,hidraw2: USB HID v1.00 Keyboard [PHILIPS MCE USB IR Receiver- Spinel plus] on usb-0000:00:12.1-2/input0
[    3.180510] Switched to clocksource tsc
[    3.265044] scsi 8:0:0:0: Direct-Access     WD       10EADS External  1.75 PQ: 0 ANSI: 4
[    3.265220] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    3.265773] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.266406] sd 8:0:0:0: [sdb] Write Protect is off
[    3.266409] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    3.267030] sd 8:0:0:0: [sdb] No Caching mode page found
[    3.267033] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[    3.268904] sd 8:0:0:0: [sdb] No Caching mode page found
[    3.268906] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[    3.287403]  sdb: sdb1
[    3.289641] sd 8:0:0:0: [sdb] No Caching mode page found
[    3.289643] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[    3.289646] sd 8:0:0:0: [sdb] Attached SCSI disk
[    3.344334] usb 4-3: new full-speed USB device number 3 using ohci-pci

```

---

### Post by praseodym on 2014-07-27
Obviously, the device ID is not part of the module rt2800usb. Try to add it manually:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "0471 20cc" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```
This is _one_ line, you better c/p it. After that reload the driver after adding nameservers:
```
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
sudo modprobe -rfv rt2800usb zd1211rw
sudo modprobe -v rt2800usb
```
Replug the stick and check:
```
lsmod
iwconfig
dmesg | grep rt2
sudo iwlist scan
```

---

### Post by shane-p-kelly7 on 2014-07-28
[Pastebin]("http://pastebin.ubuntu.com/7885147/") of output of commands and some extra dmesg stuff. Your probably most interested in this stuff:

```

$ lsmod
Module                  Size  Used by
rt2800usb              27034  0 

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

$ dmesg | grep rt2
[   14.170930] usbcore: registered new interface driver rt2800usb
[  210.940448] usbcore: deregistering interface driver rt2800usb
[  219.284187] usbcore: registered new interface driver rt2800usb

$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```

I think the registering and deregistering of the driver rt2800usb was because both that and the zd1211rw driver are initially registered.  When I removed the zd1211rw driver from /etc/modules it no longer did the registering and deregistering.  Or was that just from the two modprobe commands you had me run?

Either way it didn't look successful.  Why did we use the rt2800usb driver instead of the zd1211rw driver?

---

### Post by praseodym on 2014-07-28
Ok, this is not a wifi adapter, but an infrared remote adapter! You can easily remove that file

```
sudo rm /etc/modprobe.d/rt2800usb.conf
```

[http://www.linux-hardware-guide.com/2013-10-04-zotac-zbox-id82-mini-pc-intel-core-i3-2330m-22ghz-1x-sata-iii-intel-hd-3000](http://www.linux-hardware-guide.com/2013-10-04-zotac-zbox-id82-mini-pc-intel-core-i3-2330m-22ghz-1x-sata-iii-intel-hd-3000)

What computer is it? Can you check the BIOS if wireless is activated there?

---

### Post by chili555 on 2014-07-28
I must be very confused here. Maybe someone can increase my medication or explain better. Both your dmesg and Googling the usb.id of 0471:20cc suggest that this is not a wireless network adapter but an infrared receiver. In other words, you insert this USB device in the computer and sit across the room with a remote control and a bowl of popcorn and control functions on the computer. Viz:> [    2.892628] usb 4-2: new low-speed USB device number 2 using ohci-pci[    3.062678] usb 4-2: New USB device found, idVendor=[COLOR="#FF0000"]0471[/COLOR], idProduct=[COLOR="#FF0000"]20cc[/COLOR]
[    3.062680] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.062682] usb 4-2: Product: MCE [COLOR="#FF0000"]USB IR Receiver[/COLOR]- Spinel plus
[    3.062683] usb 4-2: Manufacturer: PHILIPS
[    3.081706] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    3.083444] input: PHILIPS MCE [COLOR="#FF0000"]USB IR Receiver[/COLOR]- Spinel plus as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input7What am I misunderstanding here?

Neither rt2800usb nor zd1211rw are going to help because they are not built for IR receivers but for wireless network adapters.

EDIT: My colleague praseodym is exactly correct! And fast.

---

### Post by praseodym on 2014-07-28
Right:
> 
```
##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x13b1:0x0031 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```
13b1:0031 was the earlier wifi, supported by rt2800usb, its a Linksys adapter with Ralink rt3072 chipset.

---

### Post by shane-p-kelly7 on 2014-07-28
OMG I'm an idiot.  I'm so sorry. I should never trust grandma when she gives me an electronics device and says its something.  So I this time I asked my dad for his and he actually gave me a USB adapter and that one works fine.  I'm guessing something with the upgrade messed up the mode switching for my original device but having switched that with my dad I have no more problems.  Thanks for saving me from my stupidity!

---

