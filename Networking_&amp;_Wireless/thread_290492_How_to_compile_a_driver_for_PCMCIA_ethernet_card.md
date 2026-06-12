---
title: "How to compile a driver for PCMCIA ethernet card?"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by MarkRW on 2006-11-01
I've got Xubuntu 6.06 (Dapper) running on an old Gateway laptop and trying to get a PCMCIA ethernet card going. I've got a MakeFile and  a .c file from the manufacturer (Argosy). What's the next step? I have to compile the driver, right? There's a readme.txt as follows:



Comments for 8139too.c version 1.0.0
2001/10/31 by ShuChen Shao

1.This driver was originally based on 8139too.c version "0.9.15".
	
2.It has been enhanced to support RTL8139C+ PCI ethernet chips and tested in 2.4.2 kernel.

3.RTL8139C+ PCI ethernet chips is set to support C+ mode by default.
  If FORCE_C_Mode below is enabled, the RTL8139C+ chip will be forced to support C mode 
  after reboot.

4.This program can be compiled using the attached Makefile.
  And the object file named 8139too.o should be moved to the directory 
  /lib/modules/2.4.2-2/kernel/drivers/net/

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

##############################################################################################
Comments for 8139too.c version 1.0.1
2001/11/21 by ShuChen Shao

1.It is able to support RTL8139C+ PCI ethernet chips in RedHat 7.2 (kernel 2.4.7).
  In addition, it is backward compatiable with RedHat 7.1 (kerne 2.4.2).

---

