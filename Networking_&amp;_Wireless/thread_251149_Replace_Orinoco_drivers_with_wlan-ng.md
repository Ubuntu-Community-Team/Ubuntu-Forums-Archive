---
title: "Replace Orinoco drivers with wlan-ng"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by HellSpam on 2006-09-05
I've been looking everywhere for a guide on how to do this. Anyone?

---

### Post by tturrisi on 2006-09-05
This is for Fedora but may give clues as to how to achieve in Debian-Ubuntu:
```
A Common Problem With Linux-WLAN And Fedora Core 1

In older versions of Fedora Core 1, the operating system will auto-detect Linux-WLAN-compatible NIC cards and enter a line similar to.

alias      eth2       orinoco_pci

in the /etc/modprobe.conf file. In other words, it detects them as an Ethernet eth device instead of a WLAN wlan device.

This seems to conflict with the WLAN RPMs, and you'll get errors like this when starting Linux-WLAN:

Starting WLAN Devices: /etc/init.d/wlan: line 119: Error: Device wlan0 does not seem to be present.: command not found
/etc/init.d/wlan: line 120: Make sure you've inserted the appropriate: command not found
/etc/init.d/wlan: line 121: modules or that your modules.conf file contains: command not found
/etc/init.d/wlan: line 122: the appropriate aliase(s).: command not found

You can fix the problem with the proper steps. This example refers to a compatible Orinoco chipset card:

Use the following steps to fix the problem. The example below refers to a compatible Orinoco chipset card. The intention of this procedure is to remove all reference to the Orinoco driver in the Linux configuration files and then force the Linux new hardware detection program, named "kudzu", not to configure the NIC card according to the Linux defaults. The "eth" device will be recreated, but the "ignore" option provided to kudzu will prevent the Orinoco entry in the /etc/modprobe.conf from being reinserted, preventing conflict with the Linux-WLAN package's "wlan" device.

   1. Remove the orinoco_pci line from the /etc/modprobe.conf file. Do not remove the entry for device wlan0.
   2. Edit your /etc/sysconfig/hwconf file, search for orinoco_pci, and remove the orinoco_pci section that refers to your wireless card. (Each section starts and ends with a single - on a new line.)
   3. Reboot.
   4. The Linux boot process always runs kudzu, the program that detects new hardware. Kudzu detects the wireless card and asks whether you want to configure it. Choose ignore. This will reinsert the wireless card in the /etc/sysconfig/hwconf file, but not in the /etc/modprobe.conf file.
   5. Your NIC card should start to function as expected as device wlan0 when you use the ifconfig -a command. Configure the IP address, and activate the NIC as shown earlier in this chapter. Remove the orinoco_pci line from the /etc/modprobe.conf file. DO NOT remove the entry for device wlan0. 

The procedure removes all reference to the Orinoco driver in the Linux configuration files and then forces kudzu not to configure the NIC card according to the Linux defaults. The eth device will be recreated, but the ignore option provided to kudzu will prevent the Orinoco entry in the /etc/modprobe.conf from being reinserted, preventing conflict with the Linux-WLAN package's wlan device. 
```

---

### Post by lupine_nickt on 2006-09-05
Note 1: /etc/modprobe.conf becomes /etc/modprobe.d/aliases (for the purposes of this guide, anyway)

Note 2: in /etc/modprobe.d/blacklist, if you add "blacklist orinoco_cs" (I think that's the module's name - check!), that'll stop it being loaded on boot.

xF,

...Nick

---

### Post by HellSpam on 2006-09-05
I blacklisted the orinoco driver, and it doesn't load the orinoco driver anymore, but decides to load the hostap driver instead. And when I blacklist that as well, it doesn't load the wlan-ng prism2_cs driver. Any idea what I'm doing wrong?

---

