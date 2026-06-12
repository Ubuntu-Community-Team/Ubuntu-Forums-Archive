---
title: "Network adapter doensn't work"
date: 2005-10-02
forum: Networking &amp; Wireless
---

### Post by Lethargic on 2005-10-02
My US.Robotics pci network adapter (USR997902) doesn't work on Ubuntu. I have the linux drivers on the cdrom but i don't know how to install it. This is the readme that i have found:
> 
<RTL8169 Linux kernel driver>
Version: 2.0
Date:    2004-04-16
This is the Linux kernel driver released for 
RealTek RTL8169s/8110s Gigabit Ethernet controller.
<Requirements>
- kernel source tree (supported versions 2.4.x or 2.6.x)
- compiler/binutils for kernel compilation
<Quick install with proper kernel settings>
Unpack the tarball :
unzip r8169_linuxdrv_vxx.zip
Change to the directory:
cd r8169
If you are running the target kernel, then you should be
able to do :
make clean modules	(as root or with sudo)
make install
depmod -a
<Force Media Speed>
The media can be forced to one of the 5 modes as follows.
Cmd: "insmod r8169 media = SET_MEDIA"
For example:
"insmod r8169 media = 0x04" will force PHY to operate in 100Mpbs Half-duplex.
SET_MEDIA can be:
_10_Half        = 0x01
_10_Full        = 0x02
_100_Half       = 0x04
_100_Full       = 0x08
_1000_Full      = 0x10
Force media type for multiple cards could be performed as:
"insmod r8169 media=0x04,0x10"
which force PHY to operate at 100Mbps half-duplex and 1000Mbps full-duplex.
<Advanced feature>
- Supports Jumbo Frame
- Hardware Tx/Rx flow control

Can someone help me with installing this driver?
Greetz Lethargic

---

### Post by cwaldbieser on 2005-10-02
[QUOTE=Lethargic]My US.Robotics pci network adapter (USR997902) doesn't work on Ubuntu. I have the linux drivers on the cdrom but i don't know how to install it. This is the readme that i have found:
Can someone help me with installing this driver?
Greetz Lethargic[/QUOTE]
Basically, you have the source code for the driver and you need to compile it.  The first thing you should do is use apt-get or synaptic to get the "build-essentials" package.  You can then type the following command to verify your compiler is installed:
```

$ gcc --version

gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

You will probably also need to use apt-get / synaptic to get the kernel headers.  The package will be named something like "linux-headers-xxx" where the xxx is the version numbers of the kernel you are running.  If you are not sure what version you are running, type:
```

$ uname -a

```
After that it is mostly a matter of typing in the commands in the README file, but it you have questions during the process, keep asking questions!  A lot of the output that is generated from the compiler can be intimidating, but most of it is just normal diagnostic messages.

---

### Post by mheirbrant on 2006-04-22
I had the same problem with the US Robotics 1000BaseT Realtek r8169 NIC on Fedora Core 4.

I found a bug in the source code of the driver USR provides here:
[http://www.usr.com/support/product-template.asp?prod=7902](http://www.usr.com/support/product-template.asp?prod=7902)

copy the directory structure to a new directory called /r8169
find the source code file: r8169_n.c in the subdirectory src
make the file read/write
edit the file and search for the string "slot"
delete the string ", pdev->slot_name"
save the modified file

then you may go ahead with the instructions.

Reboot your computer.
It should then work....

Marc

---

