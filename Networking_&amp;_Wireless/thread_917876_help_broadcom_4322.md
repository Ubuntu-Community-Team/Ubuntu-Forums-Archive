---
title: "help broadcom 4322"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by wilkiuks on 2008-09-12
:confused: help broadcom 4322 

--------------------------------------------------------------------------------

hou can i get my card broadcom 4322 working on ubuntu8.04 mi karnel is 2,6,24-19-generic .
lspci :
nerwork controller : broadcom corporation BCM4322 802,11a/b/g/n wireless lan controller .
my pc is dell studio 1535 and my card is Dell Wireless 1510 Half Mini Card (802.11n) 
can ani one help my ? and sory for my bad english

---

### Post by TSupra88 on 2008-09-12
.

---

### Post by wilkiuks on 2008-09-12
its not working

---

### Post by wilkiuks on 2008-09-12
DISCLAIMER
----------

This is an OFFICAL-RELEASE of Broadcom's hybrid Linux driver for use with Broadcom
BCM4312 based hardware (device ID 4315).

IMPORTANT NOTE AND DISCUSSION OF HYBRID DRIVER
----------------------------------------------

There are different tar's for 32 bit and 64 bit x86 CPU architectures.  Make sure you use the
appropriate tar, as the hybrid binary must be of the appropriate architectural type.

Otherwise the hybrid binary is agnostic to the specific version of Linux kernel
because it is designed to perform all interactions with the OS through OS specific
files (wl_linux.c, wl_iw.c) and an OS abstraction layer file (osl_linux.c). 
All of these interactions are done through functions which make the hybrid binary
OS version independent.  All Linux OS specific code is provided in source form
allowing re-targeting to different kernel versions and fixing OS related issues.

BUILD AND INSTALLATION INSTRUCTIONS
-----------------------------------

hybrid-portsrc.tar.gz
hybrid-portsrc-x86_64.tar.gz

On the target machine, setup the source/hybrid/build directory

1.  Create a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz
        64 bit:                             tar -xzf <path>/hybrid-portsrc-x86_64.tar.gz

After untar'ing you should have a src and lib sub directory plus a Linux
2.6 "kbuild" external makefile (Makefile).   The lib sub directory has the pre-built
binary, wlc_hybrid.o_shipped.  

You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable
kernel module (LKM):

On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

You should now have a LKM, wl.ko inside this directory.

On this or a machine with the same kernel version, install the driver.

1.  Validate you don't have loaded (or built into the kernel) the Linux community provided
      driver for Broadcom hardware.  This exists in two forms: either "bcm43xx" or a split form
      of "b43" plus "b43legacy".  If these modules were loaded you would either
        a) rmmod bcm43xx or
        b) rmmod b43; rmmod b43legacy
2.  Make available 802.11 TKIP crypto module:      modprobe ieee80211_crypt_tkip
3.  Insert the Broadcom wl module:                 insmod <path>/wl.ko

Some kernel come with pre-installed Broadcom driver that support Broadcom 4312 family of
PCIE cards. If the kernel support one of those pre-installed driver, you must remove it
in order to install the new driver.  Some of existing driver provided by the Linux community that
supports Broadcom hardware are b43/b43legacy/bcm43xx.  There is also a ssb driver that is loaded
along with b43. This ssb driver also must to be remove.

If the kernel supports blacklist, you can add those drivers to the blacklist file so that it will
not be loaded on next reboot.

can some one help me to do this becouse i don't understand wat to do her

---

### Post by wilkiuks on 2008-09-13
help

---

### Post by wilkiuks on 2008-09-17
1. Validate you don't have loaded (or built into the kernel) the Linux community provided
driver for Broadcom hardware. This exists in two forms: either "bcm43xx" or a split form
of "b43" plus "b43legacy". If these modules were loaded you would either
a) rmmod bcm43xx or
b) rmmod b43; rmmod b43legacy
2. Make available 802.11 TKIP crypto module: modprobe ieee80211_crypt_tkip
3. Insert the Broadcom wl module: insmod <path>/wl.ko
:confused:

---

### Post by SeanHodges on 2008-09-17
OK, there are 3 drivers available for your card:

1) the free (as in freedom) one, called "b43"

2) the proprietory one from Broadcom, called "wl"

3) the Windows one, which can be run under "ndiswrapper"


You will not be able to use the first one, it will not work because your card is too new. (It requires something called "Phy-N" support, which is currently unfinished)

The second one will hopefully work for you. It should be an option if you go to System -> Administration -> Hardware Drivers. It is will be called "wl" and you will want to tick the Enabled box and reboot to use it. Note that this is a "restricted driver", which means that Ubuntu is not able to fix bugs, you'll be relying on Broadcom for support.

If the second one is not visible in the Hardware Drivers dialog, or if it doesn't work properly after you turned it on, then you will need to use the Windows driver with ndiswrapper to use your wireless card. There are lots of tutorials on how to do this in these forums, search for one that matches your card.

---

### Post by Bucky Ball on 2008-09-17
> **SeanHodges said:**
> OK, there are 3 drivers available for your card:

1) the free (as in freedom) one, called "b43"

2) the proprietory one from Broadcom, called "wl"

3) the Windows one, which can be run under "ndiswrapper"


You will not be able to use the first one, it will not work because your card is too new. (It requires something called "Phy-N" support, which is currently unfinished)

The second one will hopefully work for you. It should be an option if you go to System -> Administration -> Hardware Drivers. It is will be called "wl" and you will want to tick the Enabled box and reboot to use it. Note that this is a "restricted driver", which means that Ubuntu is not able to fix bugs, you'll be relying on Broadcom for support.

If the second one is not visible in the Hardware Drivers dialog, or if it doesn't work properly after you turned it on, then you will need to use the Windows driver with ndiswrapper to use your wireless card. There are lots of tutorials on how to do this in these forums, search for one that matches your card.

The wireless cards in the Dell Studio 15 machines are ***extremely*** problematic at this point and wl is the most successful option to date. Dell should be emailed about this by all Linux/Ubuntu users who are having loads of trouble getting them up. Ya see, things are not what they seem with that card, therefore it is confusing.

One solution, and this sounds bizarre but known to work in some cases, is to make sure you download and install Hardy 8.0.4.1 version. You will find that the 'Broadcom B43 Driver' is in Hardware Drivers in 8.0.4 *not* wl. ndiswrapper is a last resort and 98% unsuccessful (bcmwl5.inf doesn't normally work with this card - as you say, too new). :(

You could have a look here:

[http://ubuntuforums.org/showthread.php?t=920226](http://ubuntuforums.org/showthread.php?t=920226)

... and follow the progress here:

[http://ubuntuforums.org/showthread.php?p=5805351#post5805351](http://ubuntuforums.org/showthread.php?p=5805351#post5805351)

We have been working on a Dell Studio 15 for a couple of days. Take no notice that it is not quite the same card as the one here. The fix will no doubt work for both, if there is one (as mentioned, wl seems the only option after extensive research).

---

### Post by SeanHodges on 2008-09-17
> **Bucky Ball said:**
> You will find that the 'Broadcom B43 Driver' is in Hardware Drivers in 8.0.4 *not* wl. ndiswrapper is a last resort and 98% unsuccessful (bcmwl5.inf doesn't normally work with this card - as you say, too new). :(

I can confirm ndiswrapper *does* work, I'm using it right now with my Broadcom 4328 (same driver as 4322). You have to use the driver supplied on the Dell website, as the one on the Broadcom website does not seem to work on Dell machines (Windows OR ndiswrapper)

However, I agree that the "wl" driver is the best way to go, at least until the b43 driver catches up. If the wl driver doesn't work properly (connection drop-outs are the most common problem) then you need to fall back to ndiswrapper.

wilkiuks: You will need to enable the "Hardy Proposed" repository to get the "wl" driver in your Hardware Drivers. First go to System -> Administration -> Software Sources and click on the "Updates" tab. Then tick "Proposed Updates (hardy-proposed)" and then Close and Reload on the dialog that pops up. It should automatically update your Hardware Drivers, and you can follow my earlier instructions.


Edit: BuckyBall I've read some of those threads you mentioned. The b43 driver (using fwcutter) works for you because you are running an older chipset "4311", see [http://linuxwireless.org/en/users/Drivers/b43#supported](http://linuxwireless.org/en/users/Drivers/b43#supported)

---

### Post by Bucky Ball on 2008-09-17
> **SeanHodges said:**
> 

Edit: BuckyBall I've read some of those threads you mentioned. The b43 driver (using fwcutter) works for you because you are running an older chipset "4311", see [http://linuxwireless.org/en/users/Drivers/b43#supported](http://linuxwireless.org/en/users/Drivers/b43#supported)

I know and mention it is an older one in that thread.

:)

---

### Post by jimmccool on 2008-09-17
Yes this does indeed work. Enable the 'hardy proposed' repositories as advised and it does work - I'm using it now.

Now this 1535 laptop *really* hums along. Much better than Vista.

---

### Post by wilkiuks on 2008-09-18
ok i will tray to use our edvise .

---

