---
title: "queries on ethernet"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by brett5 on 2014-02-18
I have a windows computer that I had to install the Ethernet driver before I could get access to the internet through a Ethernet cable.

Everytime I reformat I would have to install the Ethernet driver from the disc.

I would like to know that if I install Ubuntu over my windows( completely replace it ), will I have internet access or do I have to get the LAN driver for the Linux version?I have the motherboard disc which contain the LAN driver with it but I think its for windows only. 

this post has nothing to do with wireless network.

---

### Post by tgalati4 on 2014-02-18
Boot from a Live Ubuntu DVD or USB stick.  Plug in your ethernet cable.  Open a terminal:

```
ifconfig
```

If you see some network stuff with eth0 and an IP address and you can ping google, then you should be OK.

```
ping www.google.com
```

Control-C to quit.

So if it works in the Live Session, then you can be reasonably sure it will work once it is installed permanently on your hard disk.  Most drivers (called modules in linux) are already included in the base distribution.

---

### Post by fdrake on 2014-02-18
all the computers that i used,  windows needs spec drivers to access the ethernet and the wireless . you should be fine with ubuntu out of the box. at leats for the ethernet.

---

### Post by brett5 on 2014-02-19
Currently I have a ssd with windows on it and a 1 TB hdd , if I clean my 1 TB, then download the Ubuntu ISO to the empty 1 TB hdd, can I boot the ISO from the 1TB hdd then install Ubuntu replacing windows in the ssd?

I do not have any USB stick atm but will a hard drive act like a USB stick? Its a sata hard drive so its directly connected to the SATA port on the motherboard. 

I understand that when installing Ubuntu, I can choose a drive to install it to, so it should be able to wipe my ssd with windows on it and fully replace it with Ubuntu?

---

### Post by fdrake on 2014-02-19
yes you can you can configure the iso in the /iso folder (needs to be in anothe partition since you want to replace ubuntu with it!) and change grup so that you can select the iso as a kernel and boot from it. 
look here: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
 you don't even need to install it. the boot process is really fast so you can just keep it there in my opinion too

---

### Post by brett5 on 2014-02-19
I mean if I have an empty 1 TB hdd and I saved the ISo on it, then allow my motherboard to boot from the hdd, will it be able to boot directly off the hdd's ISO since the Iso is the only file in the hdd

 idk how this GRUB thing work but can I install Ubuntu's ISO directly off a hdd with Ubuntu ISO on it? I guess the Ubuntu ISO would be in the root of the hdd like how people only have the ISO on a thumb drive and boot with the thumb drive to install.

I do not want to try Ubuntu, I wan to install it to replace my windows

---

### Post by fdrake on 2014-02-19
ahhh that's a different story. Just format the hdd to fat32 and use unebootin to extract the iso into the hdd . unebootin treats any hard drive and usb ate the same way, no difference. Yes then you can boot like that.
[http://www.wikihow.com/Make-a-Bootable-Ubuntu-with-USB-Drive-Using-UNetbootin](http://www.wikihow.com/Make-a-Bootable-Ubuntu-with-USB-Drive-Using-UNetbootin)

---

### Post by Bucky Ball on 2014-02-19
Just for clarity, an ISO file, in and of itself, will not magically boot. It needs to be accompanied by a some kind of boot file on the device. This is what the UNetbootin USB creator will sort out.

For instance, effectively you're suggesting you copy the ISO to a drive and then boot from it and it will boot to the installer. No. That is like copying the ISO to a USB and expecting it to boot. It won't. You need to burn the image, or iso, with some kind of tool that will make it bootable.

---

### Post by brett5 on 2014-02-19
If I get the Ubuntu disc, I realize there's 2 option, one of it is to try and another is to install. Does the install option work like the windows 7 installation disc?

---

### Post by Bucky Ball on 2014-02-19
It works like the Ubuntu installation disk. In what way do you mean does it works like the Windows installation disk? It has a graphical GUI but basically it's set and forget. The main decision you need to make is whether you are going to create Ubuntu partitions and install manually or let Ubuntu install automagically.

There are two options regardless of whether you use the disk, USB or a hard drive.

---

