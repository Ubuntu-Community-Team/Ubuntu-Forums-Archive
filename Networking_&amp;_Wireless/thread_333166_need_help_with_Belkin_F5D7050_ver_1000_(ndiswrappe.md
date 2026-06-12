---
title: "need help with Belkin F5D7050 ver 1000 (ndiswrapper)"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by vixvix on 2007-01-07
hi,
I have tried to bring my F5D7050 up for days with no luck.
It is usb, according to prism54 project, the v1000 using prism GW3887, and the windows driver have a file called PRISMAXP.sys.

Here are some info:
```

lsusb
Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

iwconfig
lo        no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


```

I installed the ndiswrapper 1.8 and here is the output

```

ndiswrapper -l
Installed drivers:
bknusb          driver installed, hardware present

dmesg|grep usb
[42949391.200000] usbcore: registered new driver rt73usb
[42949391.890000] usbcore: registered new driver islusb
[42949394.440000] usbcore: registered new driver ndiswrapper
[42949592.370000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

```

I tried the depmod and modprobe and dmesg showed the ndiswrapper loaded. But I think I miss something, after rebooting, the iwconfig still shows the rausb0 using RT2500USB driver instead of ndiswrapper. 

I tried to remove the rt2570.ko from the following path
/lib/modules/2.6.17-10-server/kernel/drivers/usb/net/rt2570
Then I got an error message said the rt73usb cannot loda rt2570.  And iwconfig gives me a wireless device call eth1 instead of rausb0 with driver ieee 802.11.

It seems even I have ndiswrapper installed, it still not binding to the usb adapter yet.

Any helps appreciated! TIA.

---

### Post by vixvix on 2007-01-07
Basicly, I would like to know how to remove the connection between the rt73(rt2500) with the rausb0 and let the rausb0 driven by ndiswrapper. Thanks.

---

### Post by vixvix on 2007-01-12
I made it myself.

The key is to remove all the modules loaded by default. In my case, they are islsm_usb rt73usb rt2570. Do a lsmod|grep usb will show them in the usbcore section.

sudo rmmod islsm_usb rt73usb rt2570

If ndiswrapper is loaded, rm it in the list above as well.

Make sure the ndiswrapper is updated version the 1.8 instead 1.1.

Then load the driver, and modprobe
sudo ndiswrapper -i bknUSB.inf
ndiswrapper -l

sudo depmod -a
sudo modprobe ndiswrapper

DANG! The usb key blink! Then just follow the ndiswrapper doc or wiki for further configurations.

---

### Post by orastem on 2007-02-09
Thanks a lot, this last bit made my key to blink at me. :KS

---

### Post by babysteps on 2007-04-26
[QUOTE=vixvix;1978988]hi,
I have tried to bring my F5D7050 up for days with no luck.
It is usb, according to prism54 project, the v1000 using prism GW3887, and the windows driver have a file called PRISMAXP.sys.

Here are some info:
[CODE]
lsusb
Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi


Vixvix,

It's great that you got your Belkin working!  I've been running around, learning a lot about this Belkin USB Wireless G  - the fact that it can be a lot of things, which is making getting a working network quite the scenic route.  

The Belkin I'm trying to use has on the back  FCCID: K7SF5D7050A.  Made in China. 
With lsusb it only shows 050d: 7050 Belkin  Components
The CD with Windows drivers on it is for 98SE, Me, 2000 and XP and has P74470 Part #F5D7050 printed on the CD. 
It is a Wireless G  USB Network Adapter, 802.11g, 54 Mbps, 2.4 GHz.

Before changing to Ubuntu, I never did get it to work with the Acer laptop that was running Windows 2000 Prefessional. 

So, I was wondering about your Belkin info, the part about the file named PRISMAXP.sys.  Is this in the driver folder of the installation CD for Windows?
On the CD I have, the .inf and .sys files says rt2500usb, which is why I kept trying to install it with Ndiswrapper...come very close a few times.  

I think it's safe to say that there are a LOT of different chipsets out there for this Belkin. I just want to find out how one can know for sure which driver and which method to use.  

Thanks for your input!

Babysteps

---

### Post by pfwd.tech on 2007-05-26
Hi Vixvix,
Im using the same usb chipset as you (Belkin f5d7050 v1000) and im having problems.  Can you tell me where you got the PRISMAXP.sys. from thanks

---

### Post by Mr_bleu on 2007-05-27
I can't open anything after my belkin's inserted.  Right now, I'm thinking of trading it off for some spare computer parts.  I have the same stick.  I can't even tell what version it is.  I've tried booting with it installed and inserting it after boot.  During boot, it takes an extremely longgggggggggggggggggg time.  Over 3 minutes after windows manager starts loading. Linksys it is from now on, unless I find a belkin product that's linux compatible.:(:frown:

---

### Post by pfwd.tech on 2007-05-28
> **Mr_bleu said:**
> I can't even tell what version it is. 

in the terminal type lsusb and it will teel you the version number

---

### Post by Mr_bleu on 2007-05-28
I can't even get a terminal window to open.  I have to push the shutdown button.

---

### Post by pfwd.tech on 2007-05-29
humm can you get to the terminal when you restart?

---

### Post by vixvix on 2007-06-11
Hi Dudes,
Sorry for the delay. Since I use mostly suse at work, and I recently dont have time playing with my ubuntu box at home, so I seldom checked out here.

Anyway, the key to get the adapter work is to remove the native driver holding the device.

babysteps: there are a more post out there and in this forum regarding your t2500usb.inf version usb key. And hopefully you might have solved it by the time I am writing this.

pfwd.tech: the PRISMAXP.sys is part of the windows driver. But the ndiswrapper loads the belkin.inf file. So you just need to mount the cd or fat(32) or ntfs and copy the whole folder of the driver to your linux box and use ndiswrapper to load it.

---

### Post by bmc6053 on 2007-10-18
Hey now, the RT drivers will not work no matter how hard you try.

Version 1 is PrismGT/GW3887 (net2280). Just use the correct driver and you should be fine. Mine (which is also a version 1, which they still have at the damn stores sense its only a couple months old) installed fine with ndiswrapper on Gutsy. 

fist uninstall any driver that was NOT belkins driver and do any cleanup that may be required (ie. rmmod rt73usb etc). Also, make sure you are on 32bit as there are no 64-bit drivers for the V1 from belkin.

After doing the install of the driver as posted before, make sure to do the hoopla required after installing the driver or just use the ndiswrapper gui and then:

sudo -s

ndiswrapper -m
modprobe ndiswrapper

Reboot and it should show up and work, if not do:

sudo -s

ndiswrapper -ma
ndiswrapper -mi for good measure, then try it.

It may be worthwhile to note that for whatever reason, I have to unplug my adapter if I lose connection (or reboot) before I'm able to reconnect for some reason. I also happen to use WiFi-Radar - it gets the job done.

---

