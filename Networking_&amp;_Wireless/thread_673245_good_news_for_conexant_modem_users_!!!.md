---
title: "good news for conexant modem users !!!"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by hilariousastal on 2008-01-20
Well .... dell relaeased the drivers for their OEM users ...... Any one searching for the drivers can confirm that his/her modem is supported or not by these drivers by looking at the following information: The PCI ID's supported are :

HSF/HSFi (Standard and SmartDAA)

	PCI ID {127A,14F1}:{2013,2014,2015,2016}
	PCI ID {127A,14F1}:{1023,1024,1026}
	PCI ID {127A,14F1}:4311 (RIPTIDE)
	PCI ID {127A,14F1}:{1025,1085,2005} (if it doesn't work, try HCF driver)
	PCI ID {127A,14F1}:{2003,2004,2006}
	PCI ID 127A:2114

	PCI ID 14F1:{2043,2044,2045,2046}
	PCI ID 14F1:{2063,2064,2065,2066}
	PCI ID 14F1:2093
	PCI ID 14F1:{201A,201B}
	PCI ID 14F1:{204A,204B}
	PCI ID 14F1:{2143,2144,2145,2146}
	PCI ID 14F1:{2163,2164,2165,2166}
	PCI ID 14F1:{2343,2344,2345,2346}
	PCI ID 14F1:{2363,2364,2365,2366}
	PCI ID 14F1:{2443,2444,2445,2446}
	PCI ID 14F1:{2463,2464,2465,2466}

	PCI ID 14F1:{2F00,2F01,2F02,2F03,2F04}
	PCI ID 14F1:{2F10,2F11,2F12,2F13,2F14}
	PCI ID 14F1:{2702,2703,2704,2705}
	PCI ID 14F1:{2F20,2F30}
	PCI ID 14F1:{2F40,2F50}

	PCI ID 158B:0001 (Allied Data Technologies)
	PCI ID 158B:0005 (Allied Data Technologies)

	PCI ID 16EC:2F00 (U.S. Robotics USR5660A (265660A) 56K PCI Faxmodem)

	USB ID 0572:1300
	USB ID 0572:1301
	USB ID 0572:1302
	USB ID 0572:1303
	USB ID 08E3:0111 (Olitec Speed'Com USB V92 Ready)
	USB ID 0803:1300 (Zoom Telephonics USB V.92)
	USB ID 0803:1301 (Hayes USB V92 model 15355)
	USB ID 145F:0106 (Trust MD-1250)
	USB ID 148D:1671 (Creative Modem Blaster V.92 USB DE5671-1)
	USB ID 148D:1672 (Creative Modem Blaster V.92 USB DE5673-1)

HDA (High Definition Audio) Modems

	only under 2.6.16 or newer kernels

	HDA VENDOR ID 14F12BFA
	HDA VENDOR ID 14F12C06

INTEL AC-Link Controller (ICH)

	PCI ID 8086:7186
	PCI ID 8086:7196
	PCI ID 8086:2416
	PCI ID 8086:2446
	PCI ID 8086:2486
	PCI ID 8086:24C6
	PCI ID 8086:24D6
	PCI ID 8086:266D
	PCI ID 8086:2426

	PCI ID 10DE:00D9 (NVIDIA nForce3)
	PCI ID 10DE:01C1 (NVIDIA)

VIA AC-Link Controller

	PCI ID 1106:3068

ALI AC-Link Controller

	PCI ID {1025,10B9}:5453
	PCI ID {1025,10B9}:5457

	The internal modem of HP omnibook xe4500 series machines should work
	with this driver.

ATI AC-Link Controller

	PCI ID 1002:434D
	PCI ID 1002:4378

SIS AC-Link Controller

	PCI ID 1039:7013



The best way to check ur PCI ID is to run scanmodem tool.

Hope this information helps some one !!!

---

### Post by Shazaam on 2008-01-20
Yes that is a nice driver. If you update your kernel all you have to do is re-install the Dell driver. Much better than trying to get an updated driver from linuxant.
Unfortunately it's only for HSF modems. No HCF support. :(

---

### Post by SoDanishWasLike on 2008-01-23
I think this is the link: [http://linux.dell.com/files/ubuntu/modem-drivers/](http://linux.dell.com/files/ubuntu/modem-drivers/)

---

### Post by go_beep_yourself on 2008-01-28
> **SoDanishWasLike said:**
> I think this is the link: [http://linux.dell.com/files/ubuntu/modem-drivers/](http://linux.dell.com/files/ubuntu/modem-drivers/)

I ran the scanModem script. Here is what I got. What should I do next? Do I need one of those dell ubuntu packages?

ModemData.txt
[http://rafb.net/p/9T4yQe26.html](http://rafb.net/p/9T4yQe26.html)

scanout.00:1f.6
[http://rafb.net/p/TpMc4f13.html](http://rafb.net/p/TpMc4f13.html)

---

### Post by alfredo911 on 2008-01-29
I am in trouble.  Lack of a intel connected driver for the modem.

I have an old 356 type computer connected to the internet at 26400 bps - on a good day.
Purchased a new machine without an OS. Loaded Ubunt 7.10 from a CD, went fine.  New computer is a Intel Celeron D 360, 160 gb hard drive, modem, sound, video etc.are on the mother board and do not work work, Ubuntu runs fine.

Others have purchased the same compmuter and got arouind the problem by replacing the modem with a new pci modem for which they had the driver. Once they had the modem connection they couild down load and or find the other drivers they needed - using as an operating system  XP. My intention is to leave Micro Soft far behind. 

Others have identified the computer as a Compaq SR5010, the video (945g Express Chipset), sound card brought to lilfe by Realtek ALC 888.

Any advice short of loading MS OS would be most welcome.
A Googl search brouight me to your post.

---

