---
title: "Problem installing fwcutter on Gutsy"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by XJRodzx on 2008-09-12
I used gutsy before and had Wifi up and running. I upgraded to Hardy and found out that my card wasnt working well with it so I went back to Gutsy. Now my problem is...

Im trying to install the fwcutter package to enable the restricted driver. Im not able to get online in anyway using ubuntu because I dont have wired access. Is there a way to set this up manually?

Im able to connect using windows so if I need to dl any files I can do so from there.

Thanx

---

### Post by knattlhuber on 2008-09-12
That what you are looking for?

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fwcutter]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fwcutter")

You can download the package from there using Windows and then copy it to your Ubuntu installation.

Then do

```
sudo dpkg -i *filename*.deb
```

to install.

---

### Post by XJRodzx on 2008-09-12
thanx for the response, the install went well. The problem now is that I choose one of the wireless connections on my list and all I  get is a 0%. I know thats impossible because in Windows i connect to the same networks and I have anywhere from 70-75%

I tried some of the tutorials in this forum and havent had any luck yet.

Any ideas on what may be causing this issue?

---

### Post by knattlhuber on 2008-09-12
So you had your wireless running before under Gutsy with fwcutter?

Please post the output of

```
lspci
iwfonfig
```

I don't know nothing about fwcutter but with the info above somebody here might be able to help.

---

### Post by XJRodzx on 2008-09-12
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller

```

---

### Post by knattlhuber on 2008-09-12
OK, so you've got a Broadcom4306 chipset. That should actually work with fwcutter (or, alternatively, ndiswrapper).

You said that it was working on your previous Ubuntu installation? What method did you use to make it work then?

Can you please post the output of 

```
cat /etc/modprobe.d/blacklist
```

and also

```
iwconfig
```

---

### Post by XJRodzx on 2008-09-12
at /etc/modprobe.d/blacklist
```

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

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

I honestly dont remember what I did the last time. To be completely honest I dont remember doing anything at all. Thats why this problem is wrecking my brain so much.

Thanx for looking over my issue

---

### Post by knattlhuber on 2008-09-13
These three links might be useful:

[http://tsupra88.blogspot.com/]("http://tsupra88.blogspot.com/")
[http://ubuntuforums.org/showthread.php?t=779754]("http://ubuntuforums.org/showthread.php?t=779754")
[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

The first link suggests to blacklist bcm43xx after installing fwcutter, but, again, I have never used that card so I can comment on that.

Sorry I can't be of more help.

---

### Post by XJRodzx on 2008-09-13
No worries, your looking over my post and suggestions are help enough.

Thanx :)

---

