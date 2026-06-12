---
title: "Help!! WLAN driving me mad"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by timohnani on 2007-08-13
Hi,

I have a Buffalo Airstation G54 (WLI2-USB2-G54). I am having a very very difficult time with it. I have gone through the forums and I've tried (at least I think I tried) everything including NDISWrapper and direct drivers. But nothing seems to work. 

According to the NDISWrapper website the WUSB54Gv1 device should work with my device. But it doesn't seem to work. 

I manage to setup NDISWrapper but when I enter iwconfig my usb wireless adapter is not there. So I am completely stumped. 

if anybody has any advice on what I should try I would appreciate it very much!

Timo

---

### Post by noob12 on 2007-08-14
Posting these would help
```

lsusb

lshw -C network

ndiswrapper -l

ndiswrapper -v

grep ndiswrapper /etc/modules

grep ndiswrapper /etc/modprobe.d/*

```

---

### Post by timohnani on 2007-08-14
Hi,

Hopefully this helps:

**lsusb:**

> timo@timo-desktop:~$ lsusb
Bus 006 Device 002: ID 03f0:0704 Hewlett-Packard DeskJet 825c
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "                                                              TetraHub"
Bus 002 Device 002: ID 0411:0050 MelCo., Inc.
Bus 002 Device 001: ID 0000:0000


**lshw -C network:**

> timo@timo-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:2f:62:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:e400-e4ff iomemory:dfffff00-dfffffff irq:17

**ndiswrapper -l:**

No output

**ndiswrapper -v:**

> timo@timo-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:2f:62:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:e400-e4ff iomemory:dfffff00-dfffffff irq:17

**iwconfig**

> timo@timo-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


The rest of the commands give no output. This is likely a result of the fact that I just reinstalled Kubuntu. So its a completely clean install. 

Also as you can see the only network card that is recognised is my ethernet card. My usb wlan adapter is not recognised. It can be seen in lsusb and the usb light on my adapter lights up. So my computer can actually see the device but obviously isn't using it. 


From the Ndiswrapper website I got the following information about my wlan adapter:

> Card: Buffalo Tech WLI2-USB2-G54 (USB2 device), 54mbps
 Chipset: Prism54
 usbid: 0411:0050
 Driver: Driver for WLI2-USB2-G54 from [http://www.buffalotech.com/support/downloads.php](http://www.buffalotech.com/support/downloads.php) has some issues. Instead, use the driver for Linksys WUSB54G, which works fine.
 Other: Works with WEP, WPA using both AES and TKIP ciphers.
 Other: I just tested this device with WUSB54Gv1 and v2 drivers from Linksys and ndiswrapper claims that the hardware isn&#8217;t installed. The driver from Buffalo causes a kernel panic. YMMV. 8 Nov 2004
 Other:Had the same problem with version 0.10 but, Works with ndiswrapper v0.11 (both drivers ), i&#8217;m using kernel 2.6.7 and Slackware 10, Buffalo one has caused a kernel panic under heavy loads. CH - 22-Nov-2004

So from what I can tell I have 2 options. 1 is to try and get the WUSB54Gv1 driver to work with ndiswrapper or to use the Prism54 driver. 

Which option should I choose? Can you point me in the right direction to get instructions to set these up. 

Does the kernel come with any of the drivers or modules pre-installed? 

Any help would be appreciated. 

Timo

---

### Post by noob12 on 2007-08-14
Ubuntu ships with the ndiswrapper kernel module v1.38, but the kernel module is not loaded by default.   That's easy to set up.  You may need to install the ndiswrapper-utils-1.9 package from the repository.   

Personally I've found that the shipped version (1.38) of the kernel module works fine for the three sets of hardware and drivers that I commonly use it with.  But several other forum participants  have found that they needed to build and install the current 1.47 from sources.

What I would generally recommend is to try things in this order:  a native linux driver if it is prebuilt  or easy to build and is known to be stable and reliable,  otherwise try the shipped ndiswrapper with the Windows driver, and finally build and install the latest released ndiswrapper from source and try that.

I don't have any direct experience with the Prism54 and the linux drivers.  Their own FAQ says the PCI drivers are stable, the v1 usb drivers are mostly stable with some issues that require manual reloading occasionally.

The basic ndiswrapper HOWTO is here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Readers will help if you need help stepping through.

---

### Post by bluefightingcat on 2007-08-16
Hi,

Yesterday just tried installing my native windows drivers using ndiswrapper (v1.37 and v1.47) for my WLI2-USB2-G54. Whilst I did manage to get them loaded and running, the drivers are unstable and crash my system everytime. It requires a hard reset each time. But this is as was mentioned on the ndiswrapper website: 

> #
Card: Buffalo Tech WLI2-USB2-G54 (USB2 device), 54mbps

    *
      Chipset: Prism54
    *
      usbid: 0411:0050
    *
      **Driver: Driver for WLI2-USB2-G54 from [http://www.buffalotech.com/support/downloads.php](http://www.buffalotech.com/support/downloads.php) has some issues.** Instead, use the driver for Linksys WUSB54G, which works fine.
    *
      Other: Works with WEP, WPA using both AES and TKIP ciphers.
    *
      Other: I just tested this device with WUSB54Gv1 and v2 drivers from Linksys and ndiswrapper claims that the hardware isn’t installed. The driver from Buffalo causes a kernel panic. YMMV. 8 Nov 2004
    *
      Other:Had the same problem with version 0.10 but, Works with ndiswrapper v0.11 (both drivers ), i’m using kernel 2.6.7 and Slackware 10, Buffalo one has caused a kernel panic under heavy loads. CH - 22-Nov-2004



So as mentioned in the instructions I tried the Linksys WUSB54G drivers with version 1.47 of ndiswrapper. I only tried v1 of the drivers. Whilst I managed to get it loaded into ndiswrapper it seems that it doesn't recognise my adapater. Instead of getting the following message: 

> Installed ndis drivers:
  {name of driver}  driver present, hardware present

I get 

> Installed ndis drivers:
  {name of driver}  driver present

The "hardware present" bit is missing. So I guess that doesn't work. 

Any ideas why this would happen? Or is it just a bad driver?

The next thing I will try today is to use the v2 of the WUSB54G driver. Hopefully I will have more luck with this version. I also intend to try and use the prism54 native linux driver. But the instructions seem complicated so I am not sure how successful I will be with that. 


If you have any suggestions I would appreciate them. 

Otherwise I will keep you posted. 


BFC

---

### Post by noob12 on 2007-08-16
timo:  Your lshw -C network output does not show the device.  It doesn't seem to be claimed by the driver.

Due to some apparent cut and paste mistakes, you did not actually provide the output of the ndiswrapper commands I'd asked for; we need that to determine what you've got installed.  It doesn't seem to be installed properly.

I can walk you through that, but I need to understand where you currently are.

---

### Post by bluefightingcat on 2007-08-16
Hi,

Sure I am at work. Will send you the details as soon as I get home. 

BFC

---

### Post by Roswellgrey on 2007-08-16
> **timohnani said:**
> 

So from what I can tell I have 2 options. 1 is to try and get the WUSB54Gv1 driver to work with ndiswrapper or to use the Prism54 driver. 

Timo

In case this helps ..... ( and you want to try the WUSB54G V1 drivers)

I have just got my WUSB54G V1 working on a new install of Fiesty

I couldnt get WPA working without the latest ( v1.47) version of ndiswrapper, but, to be fair, that might have been me .  

However, what I did is as follows ....

1. Using Synaptic Package Manager, get package "build-essential"

2. Completely remove old version of ndiswrapper and ndiswrapper-utils via Synaptic Package manager

And just to be very  sure ... 

```
[I]sudo modprobe -r ndiswrapper 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
[/I]
```

3 Download and install latest version of ndiswrapper

Download latest source from sourceforge, then

```
tar xvfz ndiswrapper-1.47.tar.gz 
cd ndiswrapper-1.47
sudo make uninstall
sudo make
sudo make install
```

4. Blacklist all the drivers that the WUSB54G might use by adding the following to the /etc/modprobe.d/blacklist file

```
[I]blacklist islsm_usb
blacklist bcm43xx
blacklist rt2500
blacklist rt2561
blacklist rt25xx
blacklist rt2570
blacklist r8187
blacklist r818x
blacklist NET2280
blacklist ISL3886
blacklist islsm
blacklist p54u
blacklist prism54
blacklist prism54usb
blacklist prism54_usb
blacklist prism54common[/I]
```

5. Get latest  drivers from Linysys website ( I used the UK site), for the WUSB54G V1

Unpack the DRIVERS/WUSB54GV1 directory somewhere.

6. Configure ndiswrapper to use this driver ...

In the directory with the above driver in ...

```

sudo ndiswrapper -i WUSB54G.inf
```

*check its ok  : *
```

*sudo ndiswrapper -l*
```

7. Now, reboot ( in case there are old drivers loaded), Don't connect the Wifi USB yet !

8. Load up the driver : 
```

*sudo modprobe ndiswrapper*
```

9. Then plug in the USB Wifi device, and hopefully it will be recognised

[I]use```
 dmesg
``` and check at the bottom that its not throwing any errors, and that the device is seen
[/I]
If you get a load of errors, unplug and replug the USB Wifi.

At the bottom of the output of dmesg you are looking for *similar* to 

[ 2806.224441] ndiswrapper: driver wusb54g (The Cisco-Linksys, LLC.,01/12/2004, 1.0.8.0) loaded
[ 2808.027440] wlan0: ethernet device 00:0c:41:fb:d0:29 using NDIS driver: wusb54g, version: 0x10008, NDIS version: 0x501, vendor: 'Linksys Wireless-G USB Network Adapter', 1915:2234.F.conf
[ 2808.027540] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA


```
ndiswrapper -l
``` should show 

wusb54g : driver installed
        device (1915:2234) present (alternate driver: prism54usb)

I cannot seem to get rid of the alternate driver, but it doesn't seem to cause any pain ...

Now ....

iwconfig should show wlan0 as an available device ...

network-manager applet should now see the device 

If your AP has SSID broadcast disabled, you will have to use scripts or wicd to configure, as it wont associate with the AP with network-manager ...

If it works, you will need to make ndiswrapper autostart on boot

Some of the above might be unnecessary, but it works on my box :)

HTH

---

### Post by bluefightingcat on 2007-08-16
Hi Roswellgrey,

Thanks for the info. Essentially I did most of the stuff you did. However I didn't blacklist all the devices you mentioned. 

I will try and do the whole process again according to your instructions. When I did last time I had my USB adapter connected. 

I'll let you know how it turns out. 

Thanks for the help.

BFC

---

### Post by Roswellgrey on 2007-08-16
Hope it works :)

I picked up the blacklist idea from here 

[http://ubuntuforums.org/showthread.php?p=2557642#post2557642]("http://ubuntuforums.org/showthread.php?p=2557642#post2557642")

and it seemed to work for me.  

Let us know how you get on .....

---

### Post by bluefightingcat on 2007-08-16
Hi Roswellgrey,

I tried your method unfortunately it didn't work. Here are the results: 

**lsusb**

> timo@timo-desktop:~$ lsusb
Bus 006 Device 002: ID 03f0:0704 Hewlett-Packard DeskJet 825c
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 0411:0050 MelCo., Inc.
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000


As you can see MelCo., Inc. refers to my usb device. So it definitely can be seen by my system. 


**lshw -C network**

> timo@timo-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:2f:62:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=62.78                                                              .153.78 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:e400-e4ff iomemory:dfffff00-dfffffff irq:17


This is refering to my wired ethernet card. 

**ndiswrapper -l**

> timo@timo-desktop:~$ ndiswrapper -l
wusb54g : driver installed


This is a bit wierd because the " device (1915:2234) present (alternate driver: prism54usb)" is missing. Obviously the driver is not seeing my usb device.

**ndiswrapper -v**

> timo@timo-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

**grep ndiswrapper /etc/modules**

This doesn't produce any output

**grep ndiswrapper /etc/modprobe.d/***

This doesn't produce any output either

**iwconfig**

> timo@timo-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

 


So I think it is safe to say that this driver doesn't work for me. This was done using ndiswrapper 1.47 and v1 of the driver. 

I will no proceed to try with the v2 of the driver. Will post the outcome in my next post.

BFC

---

### Post by bluefightingcat on 2007-08-16
Hi,

Ok i've just tried version 2 of the driver. Gave me exactly the same result as in my previous post. I will now try and use version 4. 

BFC

---

### Post by Roswellgrey on 2007-08-16
Oh Dear :(

I wonder how using another manufactures driver is supposed to work ?

What I mean is ... the device ID of the Linksys is 1915:2234 and this is obviously present within the .inf file for the driver .

As your device id is 0411:0050, I cannot see how ndiswrapper will ever match the Linksys driver to the USB Device ID...   Unless you hack the inf file :confused:

Perhaps someone more knowledgeable could explain ??

---

### Post by bluefightingcat on 2007-08-16
Hi,

I just tried the version 4. I even tried version 4 for VISTA but with no luck. I am running out of options here. 

There is on more driver that I have read might work. 

However you do raise a valid point about the device id. Could that be the reason its not working?? hmmmmm.....

let me try the other driver and then we'll see what I can do. 

BFC

---

### Post by bluefightingcat on 2007-08-16
GREAT NEWS!!!! I've done it! \\:D/

I thought about what you said and I hacked the .inf file myself. I just replaced my usb id instead of the ones that were in the .inf file. 

And so far it seems to work perfectly. I have to test for a while to see whether the connection is stable. I use WEP encryption and so far it seems to work. 

Once I have tested for a while I will then write a HowTo on these forums so that others with my device can try the same thing. 

Thanks a million for your help!!! =D>

BFC :biggrin:

---

### Post by Roswellgrey on 2007-08-16
Excellent ! :)

---

