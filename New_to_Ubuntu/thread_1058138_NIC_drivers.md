---
title: "NIC drivers"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-02
The NIC on my computer seems to have crapped out, so I installed a belkin gigabit ethernet card that someone gave me. The CD that came with it had a folder for linux installation. I followed the readme, but whenever I try to make it, I get an error saying 

```
make[1]: *** No rule to make target `/src/Makefile_linux26x'. Stop
```

The readme says it supports kernel 2.6.* and I'm using 2.6.27-9

Anyone got any Ideas?

---

### Post by Titan8990 on 2009-02-02
Is it not working "out of the box"?

---

### Post by rgb96 on 2009-02-02
No. My computer doesn't even seem to realize that the new card is there.

---

### Post by kestrel1 on 2009-02-02
post the output of ```
lspci
```
Also did you copy the folder from the CD to your HD before trying to get this installed?

---

### Post by Titan8990 on 2009-02-02
Usually all NIC cards work out of the box via open source modules in the kernel. I suspect your compilation is failing because you do not have the linux header files (in most distros you need the entire kernel source).


Try this:


sudo apt-get install linux-headers-`uname -r`-generic

---

### Post by rgb96 on 2009-02-02
How can I do that if I have no internet connection though?

---

### Post by Titan8990 on 2009-02-02
We will worry about that in a min. Post the output of lscpi as directed by the other user.

---

### Post by rgb96 on 2009-02-02
okay, here is lspci

```
00:00.0 Host bridge: nVidia Corporation nForce 2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 2 Memory Controller1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce 2 Memory Controller4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce 2 Memory Controller3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce 2 Memory Controller2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce 2 Memory Controller5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce 2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce 2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce 2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce 2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce 2 USB Controller (rev a4)
00:04.0 Ethernet Controller: nVidia Corporation nForce 2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce 2 AC97 Audio Controller (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce 2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce 2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce 2  FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce 2 AGP (rev a1)
01:06.0 Communication controller : Digium, Inc. Wildcard TE405P quad-span T1/E1/J1 card SOV (rev 02)
1:08.0 Communication controller : Agere Systems LT WinModem (rev 02)
2:00.0 VGA Compatible Controller: nVidia Corporation NV18 [GeForce 4 MX - nForce GPU] (rev a3)

```

sorry that took so long. that computer is not connected to the internet, and in another, unrelated problem, I can not mount any usb devices to it.

---

### Post by kestrel1 on 2009-02-02
I assume that the ethernet controller that is not working is the Nvidia one listed?
As I said previously, have you copied the folder for your new card from the CD to your hard drive before trying to get the drivers inastalled? You could be having a problem with this if the command that is run tries to write back to the CD for some reason.

---

### Post by rgb96 on 2009-02-02
Yeah, I copied it to my harddrive as instructed by the readme.

No luck.

---

### Post by kestrel1 on 2009-02-02
Could you post the readme or a link to read it online

---

### Post by rgb96 on 2009-02-02
<Linux device driver for Belkin F5D5005 Ethernet controllers>

  This is the Linux device driver released for BELKIN F5D5005 Ethernet controllers.
	 

<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

Copy the Linuxdrv folder from the CD provided to your hard drive

Create a folder called src in the linux src directory:
	mkdir /usr/src/linux-2.6.13-15/src

Copy Makefile, Makefile_linux24x, Makefile_linux26x, and F5D5005.n into /usr/src/linux-2.6.13-15/src/


  Change to the directory:
	Linuxdrv/

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a




<Force Media Speed>

 The media can be forced to one of the 5 modes as follows.

        Cmd: "insmod F5D5005.ko media = SET_MEDIA" (for Linux kernel 2.6.x)
	note: for Linux kernel 2.4.x "insmod F5D5005.o media = SET_MEDIA"

        For example:
         "insmod F5D5005.ko media = 0x04" will force PHY to operate in 100Mpbs Half-duplex.

         SET_MEDIA can be:
                _10_Half        = 0x01
                _10_Full        = 0x02
                _100_Half       = 0x04
                _100_Full       = 0x08
                _1000_Full      = 0x10


   Force media type for multiple cards could be performed as:

         "insmod F5D5005.ko media=0x04,0x10"

   which force PHY to operate at 100Mbps half-duplex and 1000Mbps full-duplex.



<Advanced feature>

  - Supports Jumbo Frame
  - Hardware Tx/Rx flow control

==================
Support Disclaimer
==================

Drivers for Linux have been included on this CD. While Belkin has tested these for functionality, we provide no support for their use. For additional help with the linux and linux drivers please visit [www.linux.org](www.linux.org).

---

### Post by kestrel1 on 2009-02-02
I think thie problem you are having with this are to do with the kernel that you are running & the instructions above.
When you created the directory as described above > Create a folder called src in the linux src directory:
mkdir /usr/src/linux-2.6.13-15/src
did you create it as named?

---

### Post by rgb96 on 2009-02-02
No. I substituted in the name of the folder that was closest to it. I think it was  /usr/src/linux-headers-2.6.27-9/src

---

### Post by kestrel1 on 2009-02-02
You are not running the latest kernel if that is the correct folder. You should be on 2.6.27-11, but having said that I would have thought that would have worked anyway, as the kernel version isn't really the issue.

---

### Post by mgmiller on 2009-02-02
The nvidia ethernet controller that is revealed by your posted lspci output is built into your motherboard, it is not on the Belkin card.  Is the built in the one that died?  If it is, you need to go into your BIOS and disable it there, before trying to get the new card to be recognized.  If the old one is "partially broken", which may be the case here, because it shows up in lspci, it may be preventing the system from even seeing the new NIC.

---

### Post by kestrel1 on 2009-02-02
> **mgmiller said:**
> The nvidia ethernet controller that is revealed by your posted lspci output is built into your motherboard, it is not on the Belkin card.  Is the built in the one that died?  If it is, you need to go into your BIOS and disable it there, before trying to get the new card to be recognized.  If the old one is "partially broken", which may be the case here, because it shows up in lspci, it may be preventing the system from even seeing the new NIC.

I should have spotted that one.:D

---

### Post by rgb96 on 2009-02-02
Good suggestion. I'll go try that.

---

### Post by stchman on 2009-02-02
I would purchase an ethernet controller more Linux friendly.  They are pretty cheap.  You can probably get a cheap 10/100 NIC for under $7.

I am really surprised though that Linux does not support that card OOB.

---

### Post by rgb96 on 2009-02-02
I disabled the on board card in the BIOS and now it no longer shows up in lspci, but I didn't seem to find a new one.

Now I'm getting this error.

```
SIOCSIFFLAGS error: no such device
```

I tried going in and changing /etc/network/interfaces from eth0 to eth1 and eth2 but got the same error on both of those.

---

### Post by mgmiller on 2009-02-02
OK, the BIOS change is no longer masking the error messages from the Belkin NIC.  My suggestion would be if you can't get the Linux driver for it working, to pick up almost any other brand of NIC.  Like a previous poster said, 10/100's can be had for very little money and normally just work OOTB without issues.  

Also, are you sure the Belkin is a working NIC?

---

### Post by rgb96 on 2009-02-02
Okay. Any suggestions on a more Linux friendly Card?

It should be working, I just got it new from IT this morning.

---

### Post by mgmiller on 2009-02-02
I've always had good luck with Intel and 3com.  There shouldn't be anything to configure, they are plug and play OOTB.

---

### Post by rgb96 on 2009-02-02
okay great. Thanks

---

### Post by kestrel1 on 2009-02-03
Just found something about this card on the net:
[http://techgoesboom.com/archives/2004/11/01/belkin_f5d5005_on_ubuntu.php](http://techgoesboom.com/archives/2004/11/01/belkin_f5d5005_on_ubuntu.php)
Apparently if you issue this command:```
modprobe sk98lin
```
It should load the drivers. I think you will need to sudo the command though.
Might be worth looking at.

---

