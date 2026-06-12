---
title: "Hardy wireless problems after installing system updates"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Steffy on 2008-07-14
So I installed Hardy on my Presario v2000 yesterday, and after a bit of fiddling around, I finally got the wireless up and running, and everything was smooth. 

My first priority after that was to download and install all of the recommended system updates and reboot. Problem is, after they all downloaded, the wireless died, and I have absolutely no idea why.

Just as a note, I have a BCM4306 chipset, and installed the bcm43xx-firmware from here: [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/]("http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/"). I tried ndiswrapper, but it kept complaining that the inf files I was using were invalid.

Any help would be greatly appreciated.

---

### Post by Steffy on 2008-07-14
Oh, and just in case this is needed, the output of lshw -C network in the terminal:

```
*-network:1 UNCLAIMED
       
description: Network controller
       
product: BCM4306 802.11b/g Wireless LAN Controller
       
vendor: Broadcom Corporation
       
physical id: 6
       
bus info: pci@0000:02:06.0
       
version: 03
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master
       
configuration: latency=64

```

---

### Post by Steffy on 2008-07-14
Bump with more content.

Output of ifconfig and iwconfig:

```
steffy@Steffylicious:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:33:60:48  
          inet addr:192.168.0.128  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe33:6048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:534820 (522.2 KB)  TX bytes:114579 (111.8 KB)
          Interrupt:18 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60900 (59.4 KB)  TX bytes:60900 (59.4 KB)

```

```
steffy@Steffylicious:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

I'm finding this a bit strange. Before the updates, there was a third device, which I assume was the wireless adapter, called wlan0. That seems to have completely disappeared.

Once again, any feedback at all would be greatly appreciated.

---

### Post by nickdbliss on 2008-07-14
Your wireless driver is not working anymore after the updates. You need to install it again.

---

### Post by Steffy on 2008-07-14
I've tried reinstalling the packages, but that didn't seem to do anything.

---

### Post by nickdbliss on 2008-07-14
I have BCM4312 wireless chipset and i personally use Ndiswrapper. Can u give the output of #lspci

---

### Post by Steffy on 2008-07-14
#lspci gives no output.

lspci, without the hash, however, gives this:

```
steffy@Steffylicious:~$ lspci
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
**02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

I've bolded the part about the Broadcom adapter.

Does this help at all? Thanks.

---

### Post by nickdbliss on 2008-07-14
> **Steffy said:**
> #lspci gives no output.

lspci, without the hash, however, gives this:

```
steffy@Steffylicious:~$ lspci
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
**02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

I've bolded the part about the Broadcom adapter.

Does this help at all? Thanks.

Ok that # there meant to put that in terminal. Anyways , yes it helps couse there are rev 01 rev 02 as well for the same chipset u are having. Urs is rev 03. There is difference when u install drivers for each of them.

---

### Post by nickdbliss on 2008-07-14
Ok follow this post till end and i believe your problem will be solved. What kamasabi said there, is applicable in ur case as well. Try it out, if still you get stuck into some problem post it here. thanks

[http://ubuntuforums.org/showthread.php?t=735444](http://ubuntuforums.org/showthread.php?t=735444)

---

### Post by Steffy on 2008-07-14
Thanks for the link nickdbliss, but I've still been getting problems after following the instructions in the post.

I've installed and configured bcm45xx-fwcutter, but after that, wlan0 still doesn't show up anywhere. I've been considering just completely reinstalling Ubuntu and then configuring the wireless drivers after I've done the system updates, but I'd rather leave that for a last resort.

Anyways, got any more ideas? Thanks for helping out.

---

### Post by nickdbliss on 2008-07-14
> **Steffy said:**
> Thanks for the link nickdbliss, but I've still been getting problems after following the instructions in the post.

I've installed and configured bcm45xx-fwcutter, but after that, wlan0 still doesn't show up anywhere. I've been considering just completely reinstalling Ubuntu and then configuring the wireless drivers after I've done the system updates, but I'd rather leave that for a last resort.

Anyways, got any more ideas? Thanks for helping out.

Yeah how about try installing ndiswrapper?

---

### Post by Steffy on 2008-07-14
Every time I try to install drivers over ndiswrapper it says that they are "Invalid Drivers". I'll try again, but it looks like I might have to face a complete reinstall :(

---

### Post by nickdbliss on 2008-07-14
As a word of caution, did u remove the ethernet before tryign wireless and restarted ur network?

---

### Post by Steffy on 2008-07-14
Wut. I just tried installing the drivers with ndiswrapper again, and this time they decided to work. Thanks for your help nickdbliss.

---

### Post by nickdbliss on 2008-07-14
Your welcome.

---

### Post by Midwest-Linux on 2008-07-14
I have requested that someone put a "sticky" warning that updates can kill wireless. In my case it killed wireless and add/remove. There have been other comments where the updates have killed video or even the grub. 

Please, would one of the moderators or one of the administrators please put up a sticky warning users that updates can kill the wireless or worse. 

Thanks.

---

### Post by nickdbliss on 2008-07-14
Yes it is true indeed. My videos and graphic card drivers are not working after the update. They say it is a bug not solved yet. Stuck with no direct rendering.

---

