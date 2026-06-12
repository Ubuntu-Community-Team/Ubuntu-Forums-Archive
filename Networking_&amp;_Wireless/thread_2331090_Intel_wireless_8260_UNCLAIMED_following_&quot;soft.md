---
title: "Intel wireless 8260 UNCLAIMED following &quot;software update&quot; on 14.04.4"
date: 2016-07-18
forum: Networking &amp; Wireless
---

### Post by richardgmorris on 2016-07-18
Hello,

I have a Dell Precision 5510, running 14.04.4 (with Kernel updated to 3.19.0 for Skylake support).

I used "Ubuntu Software Updater" today and, after a reboot, there is now no option for "enabling wireless" when clicking on the network icon in the taskbar.

Running ```
lshw -C network
``` shows the wireless controller as "UNCLAIMED".  However, I have what I believe to be the correct driver installed ("btusb-iwlwifi-intel8260") which shows up under the "Additional Drivers" tab of "Software and Updates".

I ran the wireless info script, and have attached the resulting txt file.

Apologies, if i) the answer is obvious, or ii) I am doing something stupid, but I'm not an advanced user and am not really sure how to proceed.

Any help is much appreciated...

------------------------------------

Additional info...

Full output of ```
lshw -C network
``` is

```
 *-network UNCLAIMED            description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ddc00000-ddc01fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 9c:eb:e8:30:a0:98
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.07.0 (2014/10/09) duplex=full ip=172.16.112.125 link=yes multicast=yes port=MII speed=1Gbit/s
```

Running ```
lspci -nnk | grep 0280 -A2
``` gives

```
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Device [8086:0050]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:525a] (rev 01)
```

Running ```
sudo modprobe iwlwifi
``` gives

```
modprobe: ERROR: could not insert 'iwlwifi': Required key not available
```

Running ```
dmesg | grep iwl
``` returns nothing.


-------------------------------------------------

---

### Post by chili555 on 2016-07-18
There are a couple of possibilities here. First and, perhaps easiest, please turn off secure boot in the computer's BIOS and try again:```
sudo modprobe iwlwifi
```May we also see:```
modinfo iwlwifi | grep 24F3 | grep 0050
```

---

### Post by gbegin on 2016-07-18
This could be an issue related to drivers not working starting with Ubuntu's 3.19.0-65 kernel. This is caused by a change made by Canonical whereby kernel and kernel driver signing is now being enforced when secure boot is enabled. During the update process, when a pop-up box asked me to review the secure boot settings, I left them as they were (enabled, I assume). 

See:

[https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/1574727](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/1574727)

and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221) 

As recommended in 

[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19985774](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19985774)

disabling secure boot from the BIOS corrected the problem for me. 

You could also use sudo mokutil --disable-validation from the terminal.

---

### Post by richardgmorris on 2016-07-18
Thankyou both chili and gbegin.  I really appreciate your help.  Turning off UEFI in the BIOS appears to have solved the problem.

For others with a Dell, this is done by pressing F2 when the Dell logo appears after a restart.  Then just navigating to "secure boot" and unchecking UEFI.

On chili's request:

Running ```
sudo modprobe iwlwifi
``` now returns nothing.

Running ```
modinfo iwlwifi | grep 24F3 | grep 0050
``` returns ```
alias:          pci:v00008086d000024F3sv*sd00000050bc*sc*i*
```

Let me know if you have any other thoughts...

---

