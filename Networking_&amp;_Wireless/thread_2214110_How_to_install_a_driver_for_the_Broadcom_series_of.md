---
title: "How to install a driver for the Broadcom series of PCI wireless cards"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by chili555 on 2014-03-30
**Before we get started**

There are dozens of Broadcom wireless cards and more seem to appear every day. The key to finding the correct driver for any network card is the pci.id. To find out which one you have, open the terminal by pressing CTRL+ALT+T (It should open a window with a blank background) and inside the terminal we run the following command:


```
lspci -nn -d 14e4:
```


You will get something like this:


> Broadcom Corporation BCM4306 802.11bgn Wireless Network Adapter [*14e4:4320*] (rev 03)


The pci.id in this example is 14e4:4320 as seen inside the [...]. We will also need the revision version (if it appears) for some special cases. In this case it is rev 03 as shown inside the (...) at the end. So what you will need at the end is: [14e4:4320] (rev 03)

With this new information you can look in the table below and select the appropriate method to install your driver. 

For example, In this case, since you have the 14e4:4320 rev 03, we go down the list to the one that shows the exact same pci.id. if you were in Ubuntu 12.04 you would install the firmware-b43-installer package. If you were in 14.04 or 14.10 you would also install the  firmware-b43-installer package. 

**NOTE** - If you have previously installed any drivers, have blacklisted or uncommented any driver files or configuration files or have done any changes whatsoever to the system to make the drivers work, you will need to undo them in order to follow this guide. We assume you are doing this from scratch and have not changed the configuration files, modules or drivers in the system in any way (apart from updating it).


For example, if you previously installed the bcmwl-kernel-source package, you will need to remove it by using the purge method:
```
sudo apt-get purge bcmwl-kernel-source
```
If you have just installed Ubuntu, you will need to build an index of available packages before we can install your driver:
```
sudo apt-get update
```
Now use the pci.id you found in the grid below to find the method to install your driver. This applies with all cases, except as noted. The installation procedure is done in terminal and while connected to the internet with a temporary wired ethernet connection or USB modem or whatever means possible:
```
sudo apt-get install <package>
``` And then reboot.

```
_pci.id_                     _12.04 LTS_                             _14.04 LTS and Later_

14e4:0576                  Special case #1                       Special case #1
14e4:4301                  firmware-b43legacy-installer          firmware-b43legacy-installer
14e4:4306                  firmware-b43legacy-installer          firmware-b43legacy-installer
14e4:4306 rev 2            firmware-b43legacy-installer          firmware-b43legacy-installer
14e4:4306 rev 3            firmware-b43-installer                firmware-b43-installer
14e4:4307                  firmware-b43-installer                firmware-b43-installer
14e4:4311                  firmware-b43-installer                firmware-b43-installer
14e4:4312                  firmware-b43-installer                firmware-b43-installer
14e4:4313                  firmware-b43-installer                firmware-b43-installer
14e4:4315                  firmware-b43-lpphy-installer          firmware-b43-installer
14e4:4318                  firmware-b43-installer                firmware-b43-installer
14e4:4319                  firmware-b43-installer                firmware-b43-installer
14e4:4320 rev 02           firmware-b43legacy-installer          firmware-b43legacy-installer
14e4:4320 rev 03           firmware-b43-installer                firmware-b43-installer
14e4:4324                  firmware-b43-installer                firmware-b43-installer
14e4:4325                  firmware-b43legacy-installer          firmware-b43legacy-installer
14e4:4328                  bcmwl-kernel-source                   firmware-b43-installer
14e4:4329                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:432a                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:432b                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:432c                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:432d                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:4331                  firmware-b43-installer                firmware-b43-installer
14e4:4353                  Special case #1                       Special case #1
14e4:4357                  Special case #1                       Special case #1
14e4:4358                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:4359                  bcmwl-kernel-source                   bcmwl-kernel-source
14e4:4365                  Special case #2                       bcmwl-kernel-source
14e4:43a0                  unknown                               bcmwl-kernel-source
14e4:43b1 	    	   unknown		                 bcmwl-kernel-source
14e4:4727                  Special case #3                       Special case #1

```


_Special case #1:_ This device uses the driver combination bcma and brcmsmac. It shouldn&#8217;t be necessary to install anything at all. Required firmware is installed by default in the package linux-firmware. In a few cases, it is necessary to blacklist b43 and ssb: ```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

In some cases, blacklisting ssb will disable your Broadcom ethernet card. Post a new question for help.

_Special case #2:_  Probably only working in 64-bit only. See: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)


_Special case #3:_  Use bcmwl-kernel-source for kernel version less than 3.8; check with the terminal command: uname -r. For kernel versions 3.8 and later, use brcmsmac. Also see Special case #1.

If you have a Broadcom card that has a different pci.id, please ask a new question. Once derived, the solution will be added to this howto.

---

### Post by praseodym on 2014-03-30
Hi chili555,

thx for this how-to. Will it be stickied? 

The Broadcom-STA driver is buggy from 12.04 until 13.10. It should be mentioned that Version **6.30.223.141** works well. It may be installed according to these steps for 32 and 64 bit, respectively, with dkms for any of the above versions of Ubuntu:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS)

---

### Post by Elfy on 2014-03-30
Thanks for doing this chili555.

I've closed it though - or it will quickly fill with people posting in this rather than a thread per person/issue.

---

