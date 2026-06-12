---
title: "driver on NDiswrapper hangs Hardy Heron"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by spraveenitpro on 2008-04-27
Hi 

I have a compaq C768TU with the following Atheros AR242x Wireless card,

[COLOR="Red"]home@home-laptop:/etc/ndiswrapper$ lspci | grep Wireless
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/COLOR]

This was working perfectly fine with ndiswrapper on Gutsy gibbon, but on upgrading to Hardy the machine hangs on booting after the login screen. The wireless driver being used is Net5416.inf from the vendor Atheros site. Now disabling the Wifi [pressing the wifi button] allows the laptop to boot normally. Hence I have uninstalled the misbehaving driver . 

root@home-laptop:~/Desktop# sudo ndiswrapper -l
root@home-laptop:~/Desktop# 

Please let me know the correct driver to install.Thank you.

Praveen

---

### Post by kevdog on 2008-04-27
Boot into the machine.  Do a depmod -a. Load the driver inside ndiswrapper.  Check dmesg for errors.  What does ndiswrapper -l say at this point along with modinfo ndiswrapper. Then load ndiswrapper into the kernel and hopefully check dmesg again.  There is most likely a driver conflict.

---

### Post by spraveenitpro on 2008-04-27
Hi kevdog

I did a Depmod -a followed by ndiswrapper -l

[COLOR="Red"]home@home-laptop:~$ ndiswrapper -l 
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
home@home-laptop:~$ [/COLOR]

how do i check dmesg for errors ? this is the output of modinfo ndiswrapper :

[COLOR="Red"]
home@home-laptop:~$ sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.52
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     0B3A678F6DE891D9F074C3E
depends:        usbcore
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
home@home-laptop:~$ [/COLOR]

Please let me know how to check dmesg and driver conflict

Thx .Praveen

---

### Post by kevdog on 2008-04-27
please post

lsmod| grep ath

type dmesg
post only section related to ndiswrapper and not entire output

---

### Post by spraveenitpro on 2008-04-27
home@home-laptop:~$ sudo lsmod| grep ath
[sudo] password for home: 
home@home-laptop:~$ 

home@home-laptop:~$ type dmesg
dmesg is /bin/dmesg
home@home-laptop:~$ 

This is the only output that I got.

Praveen

---

### Post by kevdog on 2008-04-27
Please try to do some additional reading

lsmod | grep ath
dmesg

---

### Post by spraveenitpro on 2008-04-27
Here it is

home@home-laptop:~$ lsmod | grep ath
home@home-laptop:~$


ok I get this on typing dmesg


home@home-laptop:~$ dmesg | grep ndiswrapper
[   37.540547] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   37.649597] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   37.649875] ndiswrapper (ZwClose:2227): closing handle 0xdfaaf728 not implemented
[   38.062417] ndiswrapper: using IRQ 22
[   38.274728] usbcore: registered new interface driver ndiswrapper
[  182.559940] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed (00010003)
[  212.269816] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed (00010003)
home@home-laptop:~$ 

Thank You,
Praveen

---

### Post by kevdog on 2008-04-27
I have no idea what this means:

[ 182.559940] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed (00010003)
[ 212.269816] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed (00010003)

Although this is the source of the error you may have to google around what causes this and what possible solutions may be.

---

### Post by spraveenitpro on 2008-04-27
Hi Kevdog

Googling doesnt return any results...I am planning to unload the existing
net5211.inf and restart from the begining.

Praveen

---

### Post by kevdog on 2008-04-27
No way you can just use the madwifi drivers for this card?  Something seems strange for sure.

---

### Post by spraveenitpro on 2008-04-28
Hi Kevdog

So should I use Ndiswrapper or madwifi , 
I have used ndiswrapper and it worked but hangs the machine,
Dont know how to use madwifi, can u let me know how do go about it.

Thank you.
Praveen

---

