---
title: "[SOLVED] Just installed, ethernet and wireless not working"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by kar314 on 2008-09-15
Hello everyone,

I just installed ubuntu as a 75% partition (windows vista is the remaining 25%). When I was trying out the program by installing within windows, the ethernet and wireless worked with no problems. But, now with this new installation neither work. 

I have a Dell studio 1535 lap top with dell wireless 1397 WLAN mini-card. Please let me know if any other information would be helpful.

Thank you very much.

---

### Post by Bucky Ball on 2008-09-15
Could you open a terminal (Applications->Accessories->Terminal) and copy/paste this please:

**lspci**

Could you copy the result and post it back here. :)

---

### Post by kar314 on 2008-09-15
Just as an addendum, I see the animation like it is trying to connect to the ethernet, but then when i try to open a web page there is no connection.

Here is the result from typing: lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10) 
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by Bucky Ball on 2008-09-15
Okay, thanks. This line concerns your card:

Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe

... not a Dell. This brand can be problematic, but getting easier. Dell is an assembler, eg they get parts from various manufacturers, put ´em in a box, check it&#347; working and ship em out. 

Open Synaptics, search for then install this:

bcm43xx-fwcutter

Go to System->Administration->Hardware Drivers and make sure the Broadcom B43 Driver is ticked and in use. If it is not, tick it and close. If it is ticked but indicating not in use, then untick it, close, open Hardware Drivers again and tick it. If all looks right, ticked and in use but no blue light on wireless, then untick and tick again (this will reload but this time with fwcutter installed which it needs to run). Then apply changes (close). If this causes Ubuntu to ask you to download anything, agree. See how you go.

---

### Post by kar314 on 2008-09-15
Thank you so much for replying.

So I went to the drivers section, and the only one listed (under a device driver subheading) was 'wl' and it said it was not in use. Therefore, I didn't see broadcom B43 at all.

---

### Post by Bucky Ball on 2008-09-15
kar314, sorry but just been informed on another thread that this card is **not** supported by that driver on those machines. You might want to check the last few posts on this thread:

[http://ubuntuforums.org/showthread.php?t=920226](http://ubuntuforums.org/showthread.php?t=920226)

---

### Post by kar314 on 2008-09-15
I see, so does that mean there is something I can download, or is there nothing I can do really?

---

### Post by Bucky Ball on 2008-09-16
[http://ubuntuforums.org/showthread.php?t=920226](http://ubuntuforums.org/showthread.php?t=920226)

Have a look at the last post there. As you are using the Studio 15 also, looks like a reinstall of the Hardy 8.0.4.1 should have your wireless connection up 'out of the box' without a problem. Did you install from the Ubuntu disk that came with the machine (if one did)? Apparently that is the problem, even though it was working fine running within Windoze (probably using its drivers).

As I say, check that thread and see how you go. :)

---

### Post by kar314 on 2008-09-16
Thanks for your help. I actually have 8.04.1 installed now. I burned it onto a disk, it didn't come with my computer at all. 

Also, I have no idea why the ethernet isn't working. This seems to not have happened to anyone, where the wireless is a common-ish problem. It just makes it almost impossible to download things.

---

### Post by Ayuthia on 2008-09-16
Can you go into the Terminal and post the result of:
```
lshw -C network
```

I think that the issue with your ethernet card might be somewhat common, but is usually listed under the driver that it is using instead of the card name.  This command will help us see what driver it is using.

---

### Post by Bucky Ball on 2008-09-16
* I have updated this at bottom of page. :)

Yea, this is a mystery to me. Never come across it before. You might want to try the ndiswrapper option, but not sure if that will work with your card. 

With ndiswrapper, you get the Windoze drivers and use ndiswrapper to install them in Linux. As I say, this might work but not all cards work with that either (I had humungous problems and never got it working in Gutsy). An install of 8.0.4 got mine up in minutes using b43-fwcutter and Broadcom B43 Driver but older model than yours. 

Sorry we couldn't get to the bottom of it. Here's some leads:

[http://delltalk.us.dell.com/supportforums/board/message?board.id=insp_general&thread.id=288187](http://delltalk.us.dell.com/supportforums/board/message?board.id=insp_general&thread.id=288187)

This seems to be working for some:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

This is a known problem with this card, lotsa headaches and pages of interest:

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
[http://ubuntuforums.org/showthread.php?p=5782446](http://ubuntuforums.org/showthread.php?p=5782446)

As I say, Broadcom cards have always been a nightmare - I would personally be tempted to approach Dell about this issue, they may have a fix as no doubt they have had plenty of complaints/enquiries from the Linux community by now.

* Update - I have no idea why this doesn't work by downloading b43-fwcutter from Synaptic Package Manager and then switching on the Broadcom b43 Driver in Hardware Drivers in System->Admin->Hardware Drivers but anyway ... most confusing. On further research, the Studio 15 is a rare beast! Even though the card is called one thing, it is based on another (as Dell cards are apparently). So, seems people have been having success with ndiswrapper and your card, but not everyone. If this doesn't work, you should purge ndiswrapper and all of its components and it is clumsy and best avoided but I guess you are ripping your hair out by now ... so. If all else fails ... try this:

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Don't worry that it doesn't seem to be for your card - this comes from a page where someone successfully set your card up using these instructions here:

[http://ubuntuforums.org/archive/index.php/t-650729.html](http://ubuntuforums.org/archive/index.php/t-650729.html)

Again, good luck and let me know how things go. Ayuthia may have some further ideas ... :)

---

### Post by kar314 on 2008-09-16
Thanks for all the great advice Bucky. I'll be sure to try out your ideas this evening. It's just frustrating not being able to have a connection...which makes downloading things a little trickier. 


Ayuthia, thanks for replying, here is the result of typing lshw -C network into the terminal:

WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Network controller 
       product: BCM4310 USB Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
  *-network 
       description: Ethernet interface 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:21:70:73:cc:17 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes

---

### Post by Ayuthia on 2008-09-16
If you are still having problems with your wireless and you don't mind reinstalling, I think that 8.04.1 will work with your card.  The 4310 card is actually a 4312 card with a 14e4:4315 chipset.  This card is not supported by the b43 developers yet.  However, Broadcom has made a new driver (wl) that will work with your card.  Unfortunately when the driver came out with Hardy 8.04, it was not always working.  There have been some revisions now and it seems that more people have been able to get it to work for this card by using 8.04.1.

As for your wired card, I am looking into this one.  I have run into a few postings where people had problems with getting the tg3 module to start up but for some reason, I cannot find them now.

---

### Post by Bucky Ball on 2008-09-17
Ayuthia, kar314 has done it. I advised this same thing last page.

> **kar314 said:**
> Thanks for your help. I actually have 8.04.1 installed now. I burned it onto a disk, it didn't come with my computer at all. 

Also, I have no idea why the ethernet isn't working. This seems to not have happened to anyone, where the wireless is a common-ish problem. It just makes it almost impossible to download things.

:(

wl driver seems like next cab off the rank as far as options go, green as it is. And thanks for the further info as to the identity of this enigmatic card.

:)

---

### Post by kar314 on 2008-09-17
wl is on my list of drivers, but it said it was not in use.

---

### Post by Ayuthia on 2008-09-17
> **kar314 said:**
> wl is on my list of drivers, but it said it was not in use.

Does wl show up when you do the following in the Terminal:
```
lsmod|grep wl
```

---

### Post by kar314 on 2008-09-17
When I typed in that command, there was no output in the terminal.

---

### Post by Ayuthia on 2008-09-17
> **kar314 said:**
> When I typed in that command, there was no output in the terminal.
If that is the case, lets see if we can find the wl.ko file.  If we can, we can load it:
```
sudo updatedb
locate wl.ko
```These commands will update the search database and then it will look for the wl.ko file.

If it returns a file location for wl.ko, go ahead and try:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```
This will remove the possible conflicting module and load the wl module.

---

### Post by kar314 on 2008-09-17
Problem solved:

I was trying to connect on my school network...after installing all the updates on an unsecured connection everything works. Hopefully I'll figure this out at home too. Thank you for all your help.

---

