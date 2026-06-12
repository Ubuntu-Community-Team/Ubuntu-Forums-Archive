---
title: "Realtek RTL8192 Wireless is not working"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by lotharmat on 2009-07-30
Hello All,

I have just bought a Samsung R522 which comes with the above card in it. 

I have run lspci and it shows the following

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

Is there any way to get this card working with Jaunty?

Many thanks,

Mat

---

### Post by llamabr on 2009-07-30
[http://ubuntuforums.org/showthread.php?p=3539861](http://ubuntuforums.org/showthread.php?p=3539861)

Different card, but manufactuerer, and same problem.  Mine was eventually solved by upgrading to 9.04.

---

### Post by lotharmat on 2009-07-30
That could be a problem - I'm running 9.04

---

### Post by lotharmat on 2009-08-02
Is the 8192 the chipset or does it use a different one - if so does anyone know if an alternative could be used.

Also - Does anyone know if there are plans afoot to include support for this card in a forthcoming version of the kernel (pardon my ignorance - I'm trying to learn..) 

I really want to use ubuntu on this laptop (dual boot with Windows 7 - simply for the use of Adobe Premiere Pro) 

Cheers people.

Mat

---

### Post by LewRockwell on 2009-08-02
Looks like it's being developed.

[http://lwn.net/Articles/338063/](http://lwn.net/Articles/338063/)

At the above linked page you'll scroll down to new device drivers, then down to Staging, and then near the end of that list you'll see RTL8192

sucks to be new...at least for awhile...

.

---

### Post by lotharmat on 2009-08-03
> **LewRockwell said:**
> Looks like it's being developed.

[http://lwn.net/Articles/338063/](http://lwn.net/Articles/338063/)

At the above linked page you'll scroll down to new device drivers, then down to Staging, and then near the end of that list you'll see RTL8192

sucks to be new...at least for awhile...

.

Awesome! Although I thought that my RTL8192 was a PCI device - So does this mean that it if the Realtek RTL8192 USB wifi devices are being developed, then the PCI card will also work?

---

### Post by Baeser55110 on 2009-08-05
*bump*

---

### Post by LewRockwell on 2009-08-05
> **lotharmat said:**
> Awesome! Although I thought that my RTL8192 was a PCI device - So does this mean that it if the Realtek RTL8192 USB wifi devices are being developed, then the PCI card will also work?

drivers relate to the chipset moreso than the actual physical composition of the device itself, but it only makes sense to address the various devices which utilize those chipsets

hope that helps

.

---

### Post by LewRockwell on 2009-08-05
read through this thread...

[http://ubuntuforums.org/showthread.php?t=1190996](http://ubuntuforums.org/showthread.php?t=1190996)

.

---

### Post by mariogiov on 2009-10-16
The new (mainline) kernel at [COLOR="Blue"][kernel.org]("http://kernel.org")[/COLOR] includes staging drivers for all variations of this card (rtl8192e, se, and u), kindly developed by (I believe) Greg Kroah-Hartman/the hard-working folks at the [[COLOR="Blue"]Linux Driver Project[/COLOR]]("http://www.linuxdriverproject.org").

As of this writing (10.16.2009), the current mainline kernel source is 2.6.32-rc5. Compiling the kernel is not too hard and there are a number of helpful [[COLOR="Blue"]guides[/COLOR]]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") available online. Make sure you select the appropriate drivers when doing your configuration! Compilation takes a while and you don't want to wait an hour to find out you didn't include the drivers you need.

---

### Post by lotharmat on 2009-10-24
Does anyone know when this kernel will be released mainstream?

I'm too much of a n00b to be compiling kernels.

I've got Windows 7 on my laptop but I want to dual boot it with Ubuntu. I think I'm one of those weird people who love both OS's (Vista was a pile of poo though) I got into Ubuuntu at 8.10 (on my Work's Fujitsu Siemens Lifebook) and absolutely loved it. Unfortunately I couldn't get wireless to work with my home laptop (Samsung R522) so as soon as wireless works out of the box; I'll put Ubuntu on the Samsung too.

---

### Post by valros on 2009-11-04
I just bought a Toshiba L505-S5990. It comes with Realtek 8192e and of course it is not recognized by Karmic, ndiswrapper also seems to not be available to Karmic yet, is there any hope for this or am I stuck with Windows.

---

### Post by Neonii on 2009-11-19
Bump.

Any news on this issue?

---

### Post by llamabr on 2009-11-19
> **valros said:**
> I just bought a Toshiba L505-S5990. It comes with Realtek 8192e and of course it is not recognized by Karmic, ndiswrapper also seems to not be available to Karmic yet, is there any hope for this or am I stuck with Windows.

What do you mean, ndiswrapper is not available?  If it's not in the repos (and I assure you that it is), you can always build it.

---

### Post by Dude-PWB- on 2009-11-19
Depends on which 8192 wireless chipset you have? There is 8192e, 8192se, 8192u, 8192su.

I have my 8192e internal adapter working fine with the linux drivers from realtek.

Here are a few threads to look at.

[http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)

[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

---

### Post by northd_tech on 2009-11-24
Here is another thread on the Realtek 8192E wireless:

[http://ubuntuforums.org/showthread.php?p=8381452](http://ubuntuforums.org/showthread.php?p=8381452)

[General wireless diagnostic]
[http://ubuntuforums.org/showthread.php?t=1332242](http://ubuntuforums.org/showthread.php?t=1332242)

For these Realtek 819x chips/cards, you really want to read chili555's thread that Dude recommended above though (seems to be the only way anyone has succeeded with the 2.6.31 kernel and 64-bit):

******
[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)
******

---

### Post by RMau on 2009-12-04
Okay, I surrender. I cannot make 9.10 and the Realtek wireless in my Gateway play nice. Is there a version of Ubuntu that works with the Realtek cards? Or do I need to skip the built-in WiFi and go with a supported USB?

Thanks!

---

### Post by bikepunk on 2009-12-28
I found the solution, on this other thread :
[http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)
The solution I'm using now is exactly : 
[http://ubuntuforums.org/showthread.php?t=1239342#10](http://ubuntuforums.org/showthread.php?t=1239342#10)

If you don't know how to use ndiswrapper, I recomend to have a look at :
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

it seems that it's possible to avoid using ndiswrapper and compile instead the linux driver, but I didn't try yet.

---

### Post by lotharmat on 2010-01-29
I've just tried to use a live CD of Lucid Lynx with the RTL8192E card.

The card is kind of recognised but there is an error in dmesg log.

I'll post it later on to see if any of the clever buggers on her can make sense of it!

Later.

---

### Post by lotharmat on 2010-01-29
Well - That's it!

```
[   78.493865] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   78.497707] ieee80211_crypt: registered algorithm 'NULL'
[   78.497711] ieee80211_crypt: registered algorithm 'TKIP'
[   78.497712] ieee80211_crypt: registered algorithm 'CCMP'
[   78.497714] ieee80211_crypt: registered algorithm 'WEP'
[   78.497726] 
[   78.497727] Linux kernel driver for RTL8192 based WLAN cards
[   78.497728] Copyright (c) 2007-2008, Realsil Wlan
[   78.497785] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   78.497793] rtl819xE 0000:02:00.0: setting latency timer to 64
[   78.560674] Dot11d_Init()
[   78.560685] IRQ 16
[   78.667604] uvcvideo: Found UVC 1.00 device Namuga 1.3M Webcam (0ac8:c335)
[   78.676323] input: Namuga 1.3M Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input9
[   78.676432] usbcore: registered new interface driver uvcvideo
[   78.676436] USB Video Class driver (v0.1.0)
[   78.941393] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000
[   78.976767] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   79.360062] usb 2-3: reset high speed USB device using ehci_hcd and address 2
[   80.287327]   alloc irq_desc for 22 on node -1
[   80.287330]   alloc kstat_irqs on node -1
[   80.287337] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   80.287399] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   80.500496] rtl819xE: PlatformInitFirmware()==>
[   80.500497] 
[   80.500519] rtl819xE 0000:02:00.0: firmware: requesting RTL8192E/boot.img
[   80.529380] hda_codec: ALC272: BIOS auto-probing.
[   80.530851] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   80.539643] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   80.539709] HDA Intel 0000:01:00.1: setting latency timer to 64
[   80.547019] rtl819xE:request firmware fail!
[   80.547021] 
[   80.547023] rtl819xE:ERR in init_firmware()
[   80.547024] 
[   80.547026] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   80.547027] 
[   80.551493] sky2 eth0: enabling interface
[   80.553754] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by lotharmat on 2010-01-30
Update - 

Just booted 'pendrivelinux - 9.10' installed the driver that Realtek emailed me et voila! I'm typing this reply using wireless!

w00t! etc...

---

### Post by ninioperdido on 2010-02-14
lotharmat:
Can you send me the realtek driver?
I have a rtl8191s(u) not working with ndiswrapper and 2.6.31 staging drivers.

The final error message on both cases are:
[FONT="Courier New"]ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT]

The interface is on /proc/net/dev and can be used with iwconfig/ifconfig but no network is discover.

I hope can be a chance ;).

Thanks!

---

### Post by quicky2g on 2012-10-08
I have an [Acer Veriton Nettop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883103629") running Debain 6.0.6 with a Realtek RTL8192DE wireless card. I downloaded the Unix/Linux driver from the Realtek website but compiling the module from source kept failing. The README file mentioned using [compat-wireless]("http://linuxwireless.org/en/users/Download/stable/"). The versions of compat-wireless seemed to be organized based on kernel versions. Debian is currently running 2.6.32-5. I tried compat-wireless v2.6 but it didn't work. After extracting the tar.bz2 file and going through the README file, there's a command showing the wireless cards it supports:
```
./scripts/driver-select
```v2.6 didn't have the right driver available. I downloaded v3.5 and it did:
```

Supported 802.11 drivers:
        ath5k
        ath9k
        ath9k_ap
        ath9k_htc
        carl9170
        ath6kl
        b43
        zd1211rw
        rt2x00
        wl1251
        wl12xx
        brcmsmac
        brcmfmac

Supported Ethernet drivers:
        atl1
        atl2
        atl1e
        atl1c
        alx

Supported group drivers:
        atheros <  ath5k ath9k carl9170 zd1211rw ath6kl >
        ath <  ath5k ath9k carl9170 ath6kl >
        brcm80211 <  brcmsmac brcmfmac >
        intel <  iwlwifi, iwlegacy >
        rtl818x <  rtl8180 rtl8187 >
        rtlwifi <  rtl8192ce >
        ti <  wl1251 wl12xx (SPI and SDIO)>

Supported group drivers: Bluetooth & Ethernet:
        atlxx <  atl1 atl2 atl1e alx>
        bt <  Linux bluetooth drivers >

```gcc, kernel headers, and all the other usual software for compiling packages should be installed. I compiled the driver successfully using the instructions in the README file. Pay attention to output after the scripts finish installing the kernel modules. There are a few extra commands needed to load the drivers into the kernel and reboot, but I can't remember what they are. I'm using the rtlwifi driver with no problems. Hope this helps!

---

