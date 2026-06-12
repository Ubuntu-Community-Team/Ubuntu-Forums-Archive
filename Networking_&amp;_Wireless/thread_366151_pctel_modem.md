---
title: "pctel modem"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Rory from the Rock on 2007-02-20
Hi sorry to double post,  but I have not had any responce in the beginners forum.

Here is my problem...
I downloaded the driver for my pctel modem and burned it(on my wife's window's box). Seems to have worked fine.
I was following the directions for Ubuntu-txt on the DL page.


The pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz has precompiled
drivers suitable for use ONLY with Ubuntu kernel 2.6.15-23-386.
Copy it into your Linux partition.
Open a command console. Verify that the package is displayed by:
$ ls pctel*
If not change directory (cd) to the correct folder and recheck.

Unpack with:
$ tar zxf pctel*.tgz
THere should be a new folder pctel-0.9.7-9-rht-6
Check with:
$ ls -d pctel*
Move into it with
$ cd pctel-0.9.7-9-rht-6
Look around:
$ ls
Move into the src/ folder
$ cd src
$ ls

The drivers to be installed are selectively displayed with:
$ ls *.ko
linmodem.ko pctel_hw.ko pctel.ko
Install then with Root priviledges with:
$ sudo make install

Back down a folder:
$ cd ../
Read the documentation on how to proceed further.


But briefly, the drivers will be loaded by
$ sudo modprobe pctel
Check with
$ lsmod | grep pctel

If loaded the modem should be found at /dev/ttyS_PCTEL0 by:
$ sudo wvdialconf /etc/wvdial.conf
Edit in your personal information with
$ sudo gedit /etc/wvdial.conf
to the format below:

[Dialer Defaults]
Modem = /dev/ttyS_PCTEL0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 3015560020
Username = YourLoginName
Password = YourLoginPassWord

### to make a record
# wvdial 2>&1 | tee wvdial.out

## usually not necessary
# Auto DNS = yes
#### End wvdial.conf

Then you should be able to dialout with:
$ sudo wvdial

Once online do enjoy browsing for a while. Then do:
$ sudo apt-get update
$ sudo apt-get upgrade

This will correct the problem causing the compile failure:
error : stdio.h
You should then be able to compile your own drivers for other kernels,
following the standard instructions.

O.K. that was the .txt file...

"I got to the...Read the documentation on how to proceed further...and did not know how to open the faq file. When I "sudo modprobe pctel" the computer tried to find my modem but this came up...Sorry could not find your modem... Did you configure it properly with setserial.

I do not know if it was configured properly or not...

Also when I went back to the src directory and ls this is what is now in that directory
configure linmodem-2.6.c Make log ptserial-2.6.h
i8xxhal.s linmodem-2.6.h ptmodule.c ptserial_hw2.6.c
include Make file~ ptserial-2.4.6.c ptserial_pci-2.6.c
inst Makefile-2.4.in ptserial-2.4.7.c ptserial_pci-2.6.0
Lib Makefile-2.6.in ptserial-2.6.c ptserial_pci-2.6.0
uart.s


This is as far as I got..


Help

---

