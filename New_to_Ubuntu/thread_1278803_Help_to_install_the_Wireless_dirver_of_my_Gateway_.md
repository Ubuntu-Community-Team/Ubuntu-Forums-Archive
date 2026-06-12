---
title: "Help to install the Wireless dirver of my Gateway Notebook"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by yoshiyuti on 2009-09-30
I'm a begginer using ubuntu, and I need hel to install my Realtek Wireless driver in my pc,  I have read other posts of the same topic, but they don't resolve me problem.

If there is anyone that can help me I will be glad.

---

### Post by wobin77 on 2009-09-30
You can start with providing the right information. 

Go Terminal and type:
```
 lspci 
```
 and provide the output here.

If it's a usb wireless adaptor:
```
lsusb
```
and provide the output here.

You can also check your hardware update and see if your wifi card is listed there, and auto-install the drivers through Synaptic.

---

### Post by yoshiyuti on 2009-09-30
output for lspci

  	 	 	 	 	 	  00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
 00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
 00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) 
 00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 
 00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) 
 00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
 00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) 
 00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
 00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
 00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
 00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
 00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
 00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
 00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
 00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia 
 00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
 01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
 01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller 
 05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22) 
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01) 
 

output for lsusb

  	 	 	 	 	 	  Bus 006 Device 003: ID 04f2:b027 Chicony Electronics Co., Ltd  
 Bus 006 Device 001: ID 0000:0000   
 Bus 005 Device 001: ID 0000:0000   
 Bus 004 Device 001: ID 0000:0000   
 Bus 003 Device 001: ID 0000:0000   
 Bus 002 Device 001: ID 0000:0000   
 Bus 001 Device 001: ID 0000:0000

---

### Post by starcannon on 2009-09-30
Not sure if this will get us the exact chipset or not, but lets try this:
```
sudo lshw > ~/Desktop/hardware.doc
``` 
Post it as an attachment, I'll take a peek later.
Please also, which exact model of Gateway Laptop is this?
Is there more information about the wifi module on a sticker/tag on the bottom of the laptop?

I'll check in later.

---

### Post by wobin77 on 2009-09-30
You can try to download the driver from here: [http://driverscollection.com/?H=RTL8101E&By=RealTek&SS=Linux](http://driverscollection.com/?H=RTL8101E&By=RealTek&SS=Linux)

---

### Post by yoshiyuti on 2009-09-30
here is the attachment, I hope it will help

thanks wobin77 with the link to  download the driver RTL8101 but that one is for the ethernet driver, and that driver is fine, Thank you

---

### Post by starcannon on 2009-09-30
Sticker for the win!
You have an    	 	 	 	 	Realtek RTL8187SE (802.11 b/g) wifi chipset; this little beast can be a pita, but there has been work done, and even an Ubuntu package put together here:
[http://boskastrona.ovh.org/index.php?content=download&PHPSESSID=9d7cd44be063517b32a619f81cb58926](http://boskastrona.ovh.org/index.php?content=download&PHPSESSID=9d7cd44be063517b32a619f81cb58926)

This is the same wifi module that shipped with my wifes MSi Wind, I chose to void the warranty, and put in an intel Pro Wireless 3495abg wifi card instead.

It looks like you should be able to get this thing running with that driver, and perhaps some additional help here at the forums.

Keep us posted on your progress, don't hesitate to ask as many questions as you need to; and when you get it working, perhaps take time to do a write up over at [Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")?

---

### Post by yoshiyuti on 2009-09-30
I have already download the deb files, but the only problem I have found with my computer is that the files is for i386 architecture and I'm using a 64-bits AMD.

This option didn't work.

Thanks

---

### Post by starcannon on 2009-09-30
> **yoshiyuti said:**
> I have already download the deb file, but the only problem I have found with my coputer is that the files is for i386 architecture and I'm using a X64 AMD.

This option didn't work.

Thanks

Are you running the 64bit or 32bit version of Ubuntu, you can run 32bit Ubuntu on a 64 bit CPU, I do it because of the plethora of available software for 32bit, it just makes life easier, and there is no notable performance loss in my situation.

If you need to compile it from scratch the source is available here:
[http://code.google.com/p/msi-wind-linux/](http://code.google.com/p/msi-wind-linux/)

There is even a script there to do most of the work for you.
You will need to install build-essential before you begin:
```
sudo apt-get install build-essential
```

Here's a guide to compiling software in linux [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Holler out if you have questions.

GL

---

### Post by yoshiyuti on 2009-10-07
Hi I'm still trying to configure my wireless card, i was using the Ubuntu 8.04 64-bit, but I remove it to install the 32-bit version, I have make all the intruction that you have suggest me, but there wasn't any good result.

Now I'm using the 8.10 distro
and I'm still trying to install the wireless card, so it can be usefull in the laptop

---

### Post by yoshiyuti on 2009-10-16
Hi I was trying all the options that you give me in this forum and all the other that I have read in the other forums that I was reading, but I didn't a solution to install the wireless driver,  the only solution that i have found was to install the 9.04 x86 version to the computer and then the distro recognize the wireless card automatically.  after making the upgrade to the 9.04 the wireless card works good with the Ubuntu 9.04.  Now I'm trying to install it in the 8.10 64-bits let see if I can find a option for this one.

---

