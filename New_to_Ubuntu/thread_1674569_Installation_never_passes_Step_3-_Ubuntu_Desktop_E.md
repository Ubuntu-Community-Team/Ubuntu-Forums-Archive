---
title: "Installation never passes Step 3- Ubuntu Desktop Edition 10.10"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by claxie on 2011-01-24
Spent a good hour on Step 3 'Prepare to install Ubuntu' [here:]("http://www.ubuntu.com/desktop/get-ubuntu/download") 

Tried on laptop with same USB and booting from USB worked perfectly and was --A LOT-- faster.

I don't know what you need but here's some stuff.

Computer is old (5-7 years)

Wired internet connection
45GB free space on 75GB hard drive

Mainboard : Gigabyte 7VM400AM-RZ
Chipset : VIA KM400
Processor : AMD Athlon XP @ 1916MHz
Physical Memory : 512MB (1 x 512 DDR-SDRAM )
Video Card : VT82C570 MV IDE Controller KM400 Graphics Adapter
Hard Disk : Maxtor 6Y200P0 (204GB)
Hard Disk : Seagate ST380011A (80GB)
CD-Rom Drive : Toshiba-Samsung CD-R/RW SH-R522C
Network Card : Atheros Communications AR5005G 802.11a/b/g Wireless Network Adapter
Network Card : VIA Technologies VT6102 Rhine II Fast Ethernet Adapter
Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 2 (32-bit)


What else do you need to know? Do I need to upgrade something?

I have quit installation twice at Step 3 because of this. Has something messed up?

---

### Post by robert shearer on 2011-01-24
Your link, step 3 is to burn the cd or make a usb image. ?? Seems you have made the usb image and can boot from it on the laptop.
What I think you are saying is that you can't get the AMD machine to boot from usb ??

Is it possible that booting from usb is either disabled in bios (needs enabling) or the machine is not capable of booting from usb ??. (too old)

Have you tried making a live Ubuntu cd and booting from that ?


Note > Tried on laptop with same USB and booting from USB worked perfectly and was --A LOT-- faster.
Might be that the laptop has usb-2.0 whilst your old desktop has usb-1.1
Though this review says usb2.0...
[http://reviews.cnet.com/motherboards/gigabyte-7vm400am-rz-motherboard/1707-3049_7-32041739.html](http://reviews.cnet.com/motherboards/gigabyte-7vm400am-rz-motherboard/1707-3049_7-32041739.html)


> Video Card : VT82C570 MV IDE Controller KM400 Graphics Adapter
Is that the onboard graphics or a video card in the agp (green) slot  ?.

---

### Post by claxie on 2011-01-24
> **robert shearer said:**
> Your link, step 3 is to burn the cd or make a usb image. ?? Seems you have made the usb image and can boot from it on the laptop.
What I think you are saying is that you can't get the AMD machine to boot from usb ??

Is it possible that booting from usb is either disabled in bios (needs enabling) or the machine is not capable of booting from usb ??. (too old)

Have you tried making a live Ubuntu cd and booting from that ?


Note 
Might be that the laptop has usb-2.0 whilst your old desktop has usb-1.1
Though this review says usb2.0...
[http://reviews.cnet.com/motherboards/gigabyte-7vm400am-rz-motherboard/1707-3049_7-32041739.html](http://reviews.cnet.com/motherboards/gigabyte-7vm400am-rz-motherboard/1707-3049_7-32041739.html)
Sorry, I wasn't clear. From that link, click Show me how next to Install at step 4. Step 3 of what you see now. Prepare to install.

My problem is that step 3 freezes during installation.

Do you think a CD would be better/faster than USB?

---

### Post by robert shearer on 2011-01-24
I have just checked my Gigabyte 7VM400M-RZ (similar version) and only one of the usb ports is usb2.0 ! the others are 1.1 (**too slow**)

So try the usb drive in another port and keep trying others until you get the one that works fastest.
[B]
Yes the cd would be "better"[/B] as it will boot and install and removes the variable of the wrong usb port.


Note > My problem is that step 3 freezes during installation

 The system is not freezing, it is still installing just very very very slowly as it is running usb1.1 speed and moving data at max 12Mbits/second.
usb 2.0 transfers at 480Mbits/second.
Quite a difference.

---

