---
title: "help with wifi on dell ASAP"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by rico002 on 2008-06-24
hello, i have a inspiron 1525 and i have wifi and i cant seem to get internet on my laptop could some one please plese help me thanks again to everyone

---

### Post by pytheas22 on 2008-06-24
Please post the output of:
```

lspci
```

as as information about anything you already tried to make the wifi work.  Also, go to System>Administration>Hardware Drivers and if you see a box about enabling wireless, check it.  That might be all it takes to solve your problem.

---

### Post by rico002 on 2008-06-24
> **pytheas22 said:**
> Please post the output of:
```

lspci
```

as as information about anything you already tried to make the wifi work.  Also, go to System>Administration>Hardware Drivers and if you see a box about enabling wireless, check it.  That might be all it takes to solve your problem.

lani@lani-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


thats it

---

### Post by pytheas22 on 2008-06-24
Apparently you need to use ndiswrapper for your chipset as it's still not supported by the native drivers (that's the conclusion I gather from a very quick Google search; if I'm wrong, someone please correct me).  Please try this:

1. open a terminal and type:

```
sudo gedit /etc/modprobe.d/blacklist
```

and in the file that pops open, add these four lines to the bottom:
```

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist b43 ssb
```

then save the file.

2. follow the instructions at [http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/) for setting up ndiswrapper for this card.

If it still doesn't work after you do the stuff above, please post back with the output of:
```

cat /etc/modprobe.d/blacklist
ndiswrapper -l
iwconfig
lshw -C Network
```

---

### Post by rico002 on 2008-06-24
i checked admin ...... hardware drivers and there is nothing there

---

### Post by rico002 on 2008-06-24
Steps

1. Install Ndiswrapper Common and Ndiswrapper Utils (You can do it using synaptic)
2. Download The Driver from [ftp://ftp.dell.com/network/R151517.EXE](ftp://ftp.dell.com/network/R151517.EXE) and unzip it somewhere. You will see a folder named DRIVER
3. Execute the following commands


step 1 when i go to synaptic i get this message-
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and step 2 is an exe file extesion

---

### Post by pytheas22 on 2008-06-25
Apparently you have a problem with apt; run:
```

sudo dpkg --configure -a
```

and try the steps again.

As for the .exe, just run it with wine.  If you don't have wine installed, type:
```

sudo apt-get install wine
```

to get it.  Then right-click on the .exe and select "open with wine."  It should extract directories out of the .exe; these contain the files you need.  It may also start the Windows installer for the driver, but you can cancel that.

---

### Post by jpizzale on 2008-06-25
I am having the same problem. I tried ndiswrapper, still unable to connect. I see the wireless networks, but for some reason my password is always rejected. Here is the code that was recommended to be posted.

However instead of using the driver that was listed at [http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/), I found the driver for my wireless card and installed that.

jpizzale@jonathans-laptop:~$ cat /etc/modprobe.d/blacklist
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

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist b43 ssb
jpizzale@jonathans-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4315) present (alternate driver: wl)
jpizzale@jonathans-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
jpizzale@jonathans-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:40:bf:c9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:a9:70:b1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
jpizzale@jonathans-laptop:~$ 
jpizzale@jonathans-laptop:~$

---

### Post by rico002 on 2008-06-25
this isnt very user friendly, im not a my comp right now but i wish this was easier for laptops, i connect to the internet through ethernet w/o configure anything on the laptop and it works fine....so this wireless crap is wack

---

### Post by pytheas22 on 2008-06-25
jpizzale,

ndiswrapper is not working properly because the native driver is still trying to control your card.  To blacklist the native driver, press alt-f2 and enter "gksudo gedit /etc/modprobe.d/blacklist"  Add to that file the line:
```

blacklist wl
```

Save the file and reboot, and hopefully ndiswrapper will be working.  If it's not, please post the output of:
```

ndiswrapper -l
iwconfig
```

rico002,

I know it's not user-friendly and I'm sorry it's not easier.  Unfortunately Broadcom, the manufacturer of your card, is extraordinarily uncooperative with Linux.  If it would release the source for its drivers, or at least documentation, or even a binary compatibility layer, things would be a lot better.  Thanks to a huge amount of reverse-engineering work that would not have been necessary at all if Broadcom were reasonable, we do now finally have native drivers that work well with most Broadcom cards, but unfortunately yours is an exception.

I know the "blame the hardware manufacturer" line is an excuse that you hear too often from Linux users, but in Broadcom's case it's true.  Broadcom has gone way out of its way to make it as absolutely difficult as possible to get its hardware working on open-source operating systems.  This is especially regretful since a huge amount of Broadcom's money is made by selling chips for wireless routers that in most cases run Linux--so Broadcom has great wireless drivers for Linux; it just doesn't want to share them.  If you wish it weren't this way, you could [write to Broadcom]("http://www.broadcom.com/contact/feedback.php") asking why it can't cooperate with Linux developers.

When you get back to your computer and can post information about what you've done, hopefully we can solve this problem.

---

### Post by rico002 on 2008-06-25
> **pytheas22 said:**
> jpizzale,

ndiswrapper is not working properly because the native driver is still trying to control your card.  To blacklist the native driver, press alt-f2 and enter "gksudo gedit /etc/modprobe.d/blacklist"  Add to that file the line:
```

blacklist wl
```

Save the file and reboot, and hopefully ndiswrapper will be working.  If it's not, please post the output of:
```

ndiswrapper -l
iwconfig
```

rico002,

I know it's not user-friendly and I'm sorry it's not easier.  Unfortunately Broadcom, the manufacturer of your card, is extraordinarily uncooperative with Linux.  If it would release the source for its drivers, or at least documentation, or even a binary compatibility layer, things would be a lot better.  Thanks to a huge amount of reverse-engineering work that would not have been necessary at all if Broadcom were reasonable, we do now finally have native drivers that work well with most Broadcom cards, but unfortunately yours is an exception.

I know the "blame the hardware manufacturer" line is an excuse that you hear too often from Linux users, but in Broadcom's case it's true.  Broadcom has gone way out of its way to make it as absolutely difficult as possible to get its hardware working on open-source operating systems.  This is especially regretful since a huge amount of Broadcom's money is made by selling chips for wireless routers that in most cases run Linux--so Broadcom has great wireless drivers for Linux; it just doesn't want to share them.  If you wish it weren't this way, you could [write to Broadcom]("http://www.broadcom.com/contact/feedback.php") asking why it can't cooperate with Linux developers.

When you get back to your computer and can post information about what you've done, hopefully we can solve this problem.


i am truly thankful for your concern, this is y i hate laptops, i perfer pc, nonetheless it isnt even my laptop, its my sisters hahaha, so i dont really care but for futre reference the knowledge wouldnt hurt, so she is gonna put vista back on and at the end of the month im buying parts for my comp and hopefully will be running Linux. but once i get to the laptop i will see thanks again for greatfull help...i cannot stress the greatfull help

---

### Post by jpizzale on 2008-06-25
I tried the edit and now I don't even see any wireless networks.

Here is the output from the ndiswrapper -l and the iwconfig.

jpizzale@jonathans-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4315) present (alternate driver: wl)
jpizzale@jonathans-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I even tried to blacklist the wl6 and restart, but to no avail.

---

### Post by pytheas22 on 2008-06-25
> I tried the edit and now I don't even see any wireless networks.

Here is the output from the ndiswrapper -l and the iwconfig.

jpizzale@jonathans-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
device (14E4:4315) present (alternate driver: wl)
jpizzale@jonathans-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

I even tried to blacklist the wl6 and restart, but to no avail. 

You only need to blacklist the native Linux drivers so that they don't try to control the card in place of ndiswrapper (they might try to control it even if they won't work).

But that aside, the reason it's not working is that ndiswrapper doesn't recognize your card (I should have seen this from your first post but I didn't notice; sorry).  What you want to see is a line that says:

bcmwl6 : driver installed, **hardware present**

when you see both, you're good.

Are you sure that you installed the right Windows driver for your card?  Even if you did, some of the Windows drivers just don't work.  See if you can find a different release of it and install that.  If you have the CD that came with your wireless card with drivers on it, those would be the best to use.

EDIT: I found a [thread]("http://ubuntuforums.org/showthread.php?t=786397") for getting ndiswrapper working with your card.  It mentions having to do a "hack" to get it working.  Usually ndiswrapper should just work pretty well, but maybe your card requires a special step.  The thread also says your Windows .inf file should be bcmwl5.inf, different from what you have.

I would try following those instructions, and using the Windows drivers that are linked to there.  If you installed ndiswrapper from the repositories (i.e. Synaptic) and want to clear out your existing configuration so that you can have a clean slate going into that tutorial, do:

```
sudo apt-get remove --purge ndiswrapper*
```

or you could just try applying the "hack" and downloading the different Windows drivers to see if that will do it.  Installing the latest stable ndiswrapper release from source instead of using the repositories may also not hurt.

---

