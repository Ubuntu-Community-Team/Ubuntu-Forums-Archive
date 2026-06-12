---
title: "XServer-xorg not working?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Master_Odin on 2009-12-17
One day, after coming out of sleep, my computer wasn't displaying things correctly (everything was the opposite color) and it was unusable. I thought "Oh hey, this sucks, I'll just restart my computer". Lo and behold, when I restarted, I see a screen flash, a quick bit of text (to quick to make out) and then I see the command line with "ttyl" at the top. Needless to say, I'm stuck and would rather not have to re-install Ubuntu over this, but rather, learn more about the xserver-xorg package as this is obviously a problem with it.

My question is two-fold:
1) How do I go about fixing this?

2) If fixing it requires the internet, how can I connect to a wireless internet connection that has a password on it?

---

### Post by leprkhn on 2009-12-17
Try:
```
sudo dpkg-reconfigure xserver-xorg
```

That should reconfigure your x-server.

---

### Post by leprkhn on 2009-12-17
Also, connecting to a wireless network without the aid of a GUI tool:
Assuming your wireless connection is called wifi0 (rename to suit your connection name) do this:
```
sudo nano /etc/network/interfaces
```
add this:

auto wifi0
iface wifi0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX

Then:
```
sudo /etc/init.d/networking restart
```

May be unnecessary though if reconfiguring your x-server works.

---

### Post by Master_Odin on 2009-12-17
> **leprkhn said:**
> Try:
```
sudo dpkg-reconfigure xserver-xorg
```

That should reconfigure your x-server.

nothing changed. :(

---

### Post by leprkhn on 2009-12-17
ok.
How about:
```
sudo /etc/init.d/gdm start
```

---

### Post by Master_Odin on 2009-12-17
> **leprkhn said:**
> ok.
How about:
```
sudo /etc/init.d/gdm start
```
Gave me that the command wasn't found. When I do:
```

sudo apt-get install gdm

```
I get that it isn't installed (and that I can), but then I get a bunch of errors saying "Failed to fetch http://blah" for various archives of Ubuntu (meaning my internet isn't connected).

---

### Post by jamieleshaw on 2009-12-17
Hello, please paste the output of the terminal command lspci
Thanks

---

### Post by nerdy_kid on 2009-12-17
please also post output of 
```

cat /etc/X11/default-display-manager

```

also did you install any updates just before this problem arose?

---

### Post by Master_Odin on 2009-12-17
> 
00:00.0 host bridge: Intel corporation mobile 945gm/pm/gms, 943/940 gml and 945gt express memory controller hub (rev 03)
00:01.0 pci bridge: Intel corporation mobile 945gm/pm/gms, 943/940 gml and 945gt express pci express root port (rev 03)
00:1b.0 audio device: Intel corporation 82801g (ich7 family) high definition audio controller (rev 01)
00:1c.0 pci bridge: Intel corporation 82801g (ich7 family) pci express port 1 rt 1 (rev 01)
00:1c.1 pci bridge: Intel corporation 82801g (ich7 family) pci express port 2 rt 2 (rev 01)
00:1c.2 pci bridge: Intel corporation 82801g (ich7 family) pci express port 3 rt 3 (rev 01)
00:1d.0 usb controller: Intel corporation 82801g (ich7 family) usb uhci controller #1 (rev 01)
00:1d.1 usb controller: Intel corporation 82801g (ich7 family) usb uhci controller #2 (rev 01)
00:1d.2 usb controller: Intel corporation 82801g (ich7 family) usb uhci controller #3 (rev 01)
00:1d.3 usb controller: Intel corporation 82801g (ich7 family) usb uhci controller #4 (rev 01)
00:1d.7 usb controller: Intel corporation 82801g (ich7 family) usb2 ehci controller (rev 01)
00:1e.0 pci bridge: Intel corporation 82801 mobile pci bridge (rev e1)
00:1f.0 isa bridge: Intel corporation 82801gbm (ich7-m) lpc interface bridge (rev 01)
00.1f.2 ide interface: Intel corporation 82801g (ich7 family) smbus controller (rev 01)
01:00.0 vga compatible controller: Nvidia corporation g72m [quadro nvs 110m/geforce go 7300] (rev a1)
03:01.0 cardbus bridge: 02 micro, inc. 0z601/6912/711e0 cardbus/smartcardbus controller (rev 40)
09:00.0 ethernet controller: Broadcam corporation netxtreme bcm5752 gigabit ethernet pci express (rev 02)
0c:00.0 network controller: Intel corporation pro/wireless 3945abg [golan] network connection (rev 02)

^
v
> 
/usr/sbin/gdm


---

### Post by jamieleshaw on 2009-12-17
ok, It might work if you install the Nvidia driver.
S if your in a terminal that has networking you can
type sudo aptitude install nvidia-glx-new linux-restricted-modules
then once it's finished type startx

---

### Post by nerdy_kid on 2009-12-18
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo service gdm start

```

you might also try
```

sudo startx

```

and please attach /etc/X11/xorg.conf.old and /var/log/Xorg.0.log



NOTE:
to transfer the files without GUI you probaly want a flash drive:

mount it:
sudo mkdir /media/FLASH_DRIVE
sudo mount -t msdos /dev/sdb1 /media/FLASH_DRIVE  (is this doesnt work replace msdos with vfat, this is assuming that the flash drive is /dev/sdb, which it should be if you only have one hard-drive)
sudo cp /etc/X11/xorg.conf.old /media/FLASH_DRIVE/xorg.conf.old
sudo cp /var/log/Xorg.0.log /media/FLASH_DRIVE/Xorg.0.log
sudo umount /media/FLASH_DRIVE
all set

---

