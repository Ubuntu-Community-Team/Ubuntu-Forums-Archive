---
title: "Broadcom wireless OFFICAL-RELEASE of hybrid Linux driver on Hardy"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by leshachek on 2008-10-20
This one is a good reference point at ->
[http://www.workswithu.com/2008/10/02/broadcom-switches-to-the-light-side-the-start-of-a-new-era/](http://www.workswithu.com/2008/10/02/broadcom-switches-to-the-light-side-the-start-of-a-new-era/)

Here is step by step instruction on how to install wireless non-free driver. Read a license statement before proceed.
 
I was using my HP Presario V6000 laptop running Kubuntu 8.04.1 Hardy. This is a 64-bit machine.

1. Download appropriate STA driver from 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
to a local directory.

In my case it was hybrid-portsrc-x86_64.tar.gz

2. Have a check README file.
Untar the appropriate 32/64 bit file
   tar -xzf <path>/hybrid-portsrc-x86_64.tar.gz

You should have then a src and lib sub directory plus a Linux 2.6 "kbuild" external makefile (Makefile). The lib sub directory has the pre-built binary, wlc_hybrid.o_shipped.  

3. You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable kernel module (LKM).

In a command shell in a the directory where you can locate Makefile file run the following commands.

Test (optional).
   make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
If no errors then build the LKM, i.e. wl.ko.
   make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

You should now have a LKM, wl.ko in this directory.

4, Install the driver.

Validate you don't have loaded (or built into the kernel) the Linux community provided driver for Broadcom hardware.
The drive may exists in two forms: either "bcm43xx" or a split form of "b43" plus "b43legacy".
If these modules were loaded you would either
        a) rmmod bcm43xx or
        b) rmmod b43; rmmod b43legacy

5. Load 802.11 TKIP crypto module. This is required if you're using WPA encryption.

   modprobe ieee80211_crypt_tkip

6. Insert the Broadcom wl module:
   insmod <path>/wl.ko

7. Have a check wireless connection.
If you're running KNetworkManager you should be able to observe a wireless network now.

Some kernel come with pre-installed Broadcom driver that support Broadcom 4312 family of PCIE cards. If the kernel support one of those pre-installed driver, you must remove it in order to install the new driver.  Some of existing driver provided by the Linux community that
supports Broadcom hardware are b43/b43legacy/bcm43xx.

There is also a ssb driver that is loaded along with b43. This ssb driver also must to be remove. That's what I did on this laptop.

8. If everything above is OK then make these changes permanent.

There should be two files *.ko and ssb.ko located in /lib/modules/'uname -r'/kernel/net/wireless/b43.
They are not needed anymore.

If the kernel supports blacklist, you can add those drivers to the blacklist file so that it will not be loaded on next reboot.
Add the following two lines in blacklist located in /etc/modprobe.d directory.

# replaced by wl
blacklist b43
blacklist ssb
  
9. Build module dependencies and update the kernel image initrd.img-2.6.24.xxx in /boot directory.

   $sudo depmod -a
   $update-initramfs -u

To check up.
Make sure you have modutils installed.
depmod updates modules.dep file
modprobe -b
etc/modprobe.conf
modprobe -c displays config.file.
modprobe -a to insert ALL modules listed in the command line.

---

### Post by Ayuthia on 2008-10-20
You should not have to compile the driver if you have the most recent update of Hardy (kernel version 2.6.24-21 or higher).  It is now included in linux-restricted-modules.  All you should have to do is go into System->Administration->Hardware Drivers and there should be an option out there for Broadcom STA (with a few extra words).  You just need to enable it and disable the b43 version. 

There is more information about it in the sticky:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by leshachek on 2008-10-21
> **Ayuthia said:**
> You should not have to compile the driver if you have the most recent update of Hardy (kernel version 2.6.24-21 or higher). 

Thanks, it's good to know so quick there is a better solution available now.
I'm currently running 2.6.24-19 and will be upgrading the kernel soon.

---

