---
title: "No wireless devices found??"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by drewsfca on 2008-06-11
Using vista, my HP Pavilion dv9000 can always detect typically five plus available wireless signals.  Ubunti zero are detected.  I'm guessing when I installed ubuntu yesterday it didn't recognize some of my device drivers.  I'm no techy though.  Any way to fix this? Please help.

---

### Post by cdtech on 2008-06-11
I have the same laptop. What do you get with this:
lshw -C network

---

### Post by issih on 2008-06-11
Almost certainly driver issues of one form or another. We are going to need a fair bit more information to point you in the right direction.

first open a terminal (Applications->Accessories->Terminal)

Post the output of the following commands
```
iwconfig
```

```
iwlist scan
```

```
sudo lshw -C network
```
N.B. enter your login password when prompted.

This should let us work out if what hardware you have, whether ubuntu is actually loading a driver for it, and if it is working at all.

---

### Post by cdtech on 2008-06-11
Well, there wont be any configuration nor list from the scan because the driver is not installed but we can see if it's the Broadcom to install the driver.

---

### Post by drewsfca on 2008-06-11
drew@drew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

drew@drew-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

drew@drew-laptop:~$ sudo lshw -c network
[sudo] password for drew: 
 
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

drew@drew-laptop:~$

---

### Post by cdtech on 2008-06-11
That should be a capital "C".
lshw -C network

---

### Post by drewsfca on 2008-06-11
Any ideas on what's next?

---

### Post by cdtech on 2008-06-11
> **drewsfca said:**
> Any ideas on what's next?

Copy and paste this:
lshw -C network

And show us the output.

---

### Post by drewsfca on 2008-06-11
drew@drew-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
drew@drew-laptop:~$

---

### Post by cdtech on 2008-06-11
What flavor of Ubuntu are you running?

---

### Post by drewsfca on 2008-06-11
> **cdtech said:**
> what Flavor Of Ubuntu Are You Running?

8.04

---

### Post by cdtech on 2008-06-11
Do you have System > Administration > Windows wireless drivers?

If so select that and tell me what you get.

---

### Post by drewsfca on 2008-06-11
No, I don't have that option

---

### Post by cdtech on 2008-06-11
Better yet here is a site where the broadcom is a step by step to get it working I have to go

```
http://ubuntuforums.org/showthread.php?t=405990
http://ph.ubuntuforums.com/showthread.php?t=616801

```

---

