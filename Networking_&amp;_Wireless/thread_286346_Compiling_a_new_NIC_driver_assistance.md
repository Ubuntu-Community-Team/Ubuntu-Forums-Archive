---
title: "Compiling a new NIC driver assistance"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by digimars on 2006-10-27
After upgrading to Edgy on my laptop, my Internet connection is sucking.  On the same laptop, I can log into Windows XP and notice a significant speed increase.  So I figured that the drivers that the kernel is using just aren't  effecient enough or something.  

So I went to the manufacturer's website (it's a Realtek RTL8101L NIC) and they actually had a Linux driver on the website, but it said that it was for the 2.4.x kernel.  I figured that since Edgy runs a newer kernel, this should be OK.

I downloaded the driver, only to find that it is the source code for it.  So I guess that I will need something like build-essentials for it, right?

Also, in the directions below

```

8139too.c release note
2001/10/31 by ShuChen Shao

1.This driver was originally based on 8139too.c version "0.9.15".
	
2.It has been enhanced to support RTL8139C+ PCI ethernet controller.

3.RTL8139C+ PCI ethernet chips is set to support C+ mode by default.
  If FORCE_C_Mode below is enabled, the RTL8139C+ chip will be forced to support C mode 
  after reboot.


4.This program can be compiled using the attached Makefile.
  Please remember to SPECIFY "NEW_INCLUDE_PATH" in Makefile according to your linux environment.
  The object file named 8139too.o should be moved to the directory 
  /lib/modules/<linux-version>/kernel/drivers/net/
  The driver could be brought up by the following steps:
	'insmod 8139too'
	'ifconfig eth0 up'

5.It can support Auto-Negotiation ability,that is
	10-half	 0x01
	10-full	 0x02
	100-half 0x04
	100-full 0x08
  If 10-half mode is expected, it can be achieved by the following steps:
	#ifconfig eth0 down
	#rmmod 8139too
	#insmod 8139too media=0x01

6.If the "Install Type", selected during the Linux install procedure, is "laptop",
  this driver can work normally for CardBus application without any modification.
  Otherwise, reinstall Linux and select "Install Type" as "laptop". 
  Then this driver can also work.

---------------------------------------------------------------------------------------
8139too.c version 1.5.0 release note
2003/3/4 by ShuChen  Shao

1.Add flag in Makefile to specify access type to operation register on PCI
ethernet chips.

```

it says to put the driver in lib/modules/<linux-version>/kernel/drivers/net/, will this work in Ubuntu?  I know that they do some things different, I just want to put the driver in the right directory.

Also, is this even worth attempting?

---

