---
title: "Restricted Driver problem for Intel® PRO/Wireless 3945ABG"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Plamo on 2007-11-23
Okay, so here's my situation.
I just put Ubuntu 7.1 onto my laptop (Fujitsu S7110) and when I enter my network connections it doesn't show the wireless connection. I checked restricted drivers and the wireless card was sitting there, enabled. 

The first thing I tried was downloading the iwlwifi-1.0.0-1 driver. I went into the terminal, and used the make command which returned the following error: Makefile:21: WARNING: $SHELL not set to bash. If you experience build  errors, try 'make SHELL=/bin/bash'." This didn't work.

The next thing I tried was using the sudo modprobes.

> sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee90211_crypt
sudo modprobe mac80211
sudo modprobe iwl3945
After sudo modprobe iwl3945 I got the message:
>  "FATAL: Error inserting iwl3945 (/lib/modules/2.6.22-14-generic/unubtu/wireless/iwlwifi/iwlwifi/origin/iwl3845.ko): Unknown symbol in module, or unknown parameter (see dmsg)".


Anyone have ideas on what I should do? I should probably note that they'll have to be pretty much step by step, as I'm completely new to linux/ubuntu.

Thanks in advance.

---

### Post by wjp.reg on 2007-11-23
> **Plamo said:**
> Okay, so here's my situation.
I just put Ubuntu 7.1 onto my laptop (Fujitsu S7110) and when I enter my network connections it doesn't show the wireless connection. I checked restricted drivers and the wireless card was sitting there, enabled. 

The first thing I tried was downloading the iwlwifi-1.0.0-1 driver. I went into the terminal, and used the make command which returned the following error: Makefile:21: WARNING: $SHELL not set to bash. If you experience build  errors, try 'make SHELL=/bin/bash'." This didn't work.

The next thing I tried was using the sudo modprobes.


After sudo modprobe iwl3945 I got the message:


Anyone have ideas on what I should do? I should probably note that they'll have to be pretty much step by step, as I'm completely new to linux/ubuntu.

Thanks in advance.

> when I enter my network connections it doesn't show the wireless connection.

It has been my experience that the 3945abg works out of the box, so I am not sure what you have experienced.

what is it that you are expecting?

---

### Post by Plamo on 2007-11-23
I'm looking to get my wireless net connection working.
lshw:
[HTML]  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:84:e4:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.2.105 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
[/HTML]

Now if I'm correct, this means I must assign drivers somehow...

Edit:
I'm giving NDISwrapper a shot, here's what I found for my card
[HTML]
        Card: Intel PRO/Wireless 3945ABG
      Driver: version 11.1.1.0 driver netw4v32.inf (from the intel web site) seemed to work fine but it turned out to be a dud. The Dell driver for the Dell Latitude D630 (http://ftp.us.dell.com/network/R164255.EXE) also has netw4v32.inf and this one worked on my Dell Latitude D630 - go figure.
      Other: both drivers were evaluated on debian etch - wpa_supplicant didn&#8217;t seem to work, even with the Dell driver but WEP worked
      pciid: 8086:4222
      Driver: version 10.1.0.13 http://www.intel.com/support/wireless/wlan/sb/cs-010623.htm (w39n51.inf, unfortunatly the download is 80MB because it&#8217;s packaged with &#8220;Intel PROset/Wireless software&#8221;, and drivers for the 2200BG and 2915ABG).
      Other: Tested on Gentoo Linux, with gentoo patched kernel 2.6.15-r1 (SMP hasn&#8217;t been tested yet, I had some problems with it, so reverted to non-SMP). You need to patch your kernel to use 16K Stacks (rather than the default 8K). Patches can be found via LinuxAnt. I found mine at http://www.linuxant.com/driverloader/wlan/downloads-patches.php.
[/HTML]

I went hunting for the driver it suggested (w39n51.inf) and could not find it on the link given.

Edit 2:

I've managed to find this; which sounds like what I need, however, I need someone to expand on exactly how to accomplish this:
> The drivers from Intel: [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/). Because the drivers are not (and maybe will not, see discussions on the LKML) in the kernel, you need the drivers, the binary, and the ecxternal IEEE package. You get this all on the IPW website mentioned above. Read the INSTALL manual. At a short: copy firmware to the place of your firmwareloader, remove all IEEE stuff (network drivers,etc) and compile/install IEEE and IPWDrivers package. At the moment you can not install the ipw drivers, you have to manually load and unload them via the scripts. This will change when the driver is stable. This worked quite good for me with IPWDrivers version 0.0.74 and ieee80211-1.1.12 (or later). 

As always, thanks.

---

### Post by pviegas on 2007-11-25
Hi thre,

I have presicelly the same problem.
I have a Toshiba P100-332.

Any solution?

---

### Post by pviegas on 2007-11-25
Hi Guys,

I was able to get mine working.
I followed a bug on launchpa that said this applies to all 2.6.22 kernels "generic-i386".
Just use the "generic" and it will work.

I have the 2.6.22-14-generic and booting with the non-i386 worked out-of-the-box.

I had previously loaded the linux-restricted-modules and I think it is mandatory since the network driver for the 3945ABG is a restricted driver.

Hope it helps you to.

Regards,

---

### Post by sohaibafifi on 2007-12-25
finnaly i have installed the driver how?
first you must install the ndisgtk 
next the unshield package
you must have at less the driver installer for windows 
extract it using unshield then you will find the inf file 
run ndisgtk and install the driver from 

hmmmmmmmmmmm!
......thank you
[www.sohaibafifi.com](www.sohaibafifi.com)

---

