---
title: "module configuration already contains alias directive"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-05-18
could someone please tell me what the three repeats of the module configuration message below mean?

```
matt@Darwin:~$ ndiswrapper -l
mrv8335 : driver installed
	device (11AB:1FAA) present
matt@Darwin:~$ ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive
```

thanks

---

### Post by kevdog on 2008-05-18
Look in your /etc/modules file.  Is ndiswrapper listed multiple times?  It should only be listed once.

---

### Post by Ayuthia on 2008-05-18
Just to add to kevdog, /etc/modules/ndiswrapper already has the alias lines created.  But like kevdog says, it is listed multiple times most likely because of what he said.

---

### Post by scholzilla on 2008-05-19
Thank you both. Indeed, ndiswrapper was listed twice. However, after removing the second occurrence and rebooting, ndiswrapper -m still gives me the same output. Further troubleshooting help would be greatly appreciated as I'm completely stuck. Summarizing:

```
matt@Darwin:~$ ndiswrapper -l
mrv8335 : driver installed
	device (11AB:1FAA) present

matt@Darwin:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 

matt@Darwin:~$ ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive
```

here are the revised contents of /etc/modules:

```
 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper
```

For completeness sake, let me tell you that I'm running hardy on a 64bit architecture. I was unable to restore the native wireless functionality which is for some reason irrevocably disabled in BIOS, so I unwisely bought a Netgear WG511v2 (made in China) PCI card and installed the driver according to instructions found elsewhere on an ubuntu troubleshooting wiki and elsewhere on the forums. No need to send me a link elsewhere, I think I've been everywhere.

lspci lists it as:

Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

and alas:

```
matt@Darwin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by Ayuthia on 2008-05-19
> **scholzilla said:**
> Thank you both. Indeed, ndiswrapper was listed twice. However, after removing the second occurrence and rebooting, ndiswrapper -m still gives me the same output. Further troubleshooting help would be greatly appreciated as I'm completely stuck. Summarizing:

```
matt@Darwin:~$ ndiswrapper -l
mrv8335 : driver installed
	device (11AB:1FAA) present

matt@Darwin:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 

matt@Darwin:~$ ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive
```

here are the revised contents of /etc/modules:

```
 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper
```

For completeness sake, let me tell you that I'm running hardy on a 64bit architecture. I was unable to restore the native wireless functionality which is for some reason irrevocably disabled in BIOS, so I unwisely bought a Netgear WG511v2 (made in China) PCI card and installed the driver according to instructions found elsewhere on an ubuntu troubleshooting wiki and elsewhere on the forums. No need to send me a link elsewhere, I think I've been everywhere.

lspci lists it as:

Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

and alas:

```
matt@Darwin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Can you post your lshw -C network information?

---

### Post by scholzilla on 2008-05-25
I'm sorry it's taken me so long to respond--I had to move. I hope you wouldn't mind continuing to troubleshoot this with me. Here is the output you requested from lspci -C network

 ```
 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=150.135.93.40 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
```

Is there an issue here with the "width" being 32 bits for the Ethernet controller and the Ethernet interface having a 64 bit width? Thanks again for your help.

---

### Post by Ayuthia on 2008-05-25
> **scholzilla said:**
> I'm sorry it's taken me so long to respond--I had to move. I hope you wouldn't mind continuing to troubleshoot this with me. Here is the output you requested from lspci -C network

 ```
 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=150.135.93.40 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
```

Is there an issue here with the "width" being 32 bits for the Ethernet controller and the Ethernet interface having a 64 bit width? Thanks again for your help.

I don't think so.  Can you check dmesg (go to the Terminal and type dmesg) after you do the following from the Terminal:
```
sudo modprobe -r ndiswrapper 
sudo depmod -ae
sudo modprobe ndiswrapper
```
The UNCLAIMED message is saying that ndiswrapper is not loading for some reason.  dmesg is a good place to see what is happening.

---

### Post by scholzilla on 2008-05-26
Thanks again for your persistence. I suspect this is the part of the dmesg output you are interested in:

```
[  212.067493] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  212.114339] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  212.114348] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[  212.116205] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[  212.119177] usbcore: registered new interface driver ndiswrapper
[  654.938771] usbcore: deregistering interface driver ndiswrapper
[  654.934964] ndiswrapper (ntoskernel_exit:2708): object ffff8100360e0630(2) was not freed, freeing it now
[  669.786879] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  669.806991] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  669.807003] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[  669.812447] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[  669.815227] usbcore: registered new interface driver ndiswrapper
```

Looks like a driver issue? I'm not sure how to follow up on the line that says "check system log for messages from 'loadndisdriver'" The gnome system log spits out the same output as above.

---

### Post by Ayuthia on 2008-05-26
> **scholzilla said:**
> Thanks again for your persistence. I suspect this is the part of the dmesg output you are interested in:

```
[  212.067493] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  212.114339] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  212.114348] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[  212.116205] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[  212.119177] usbcore: registered new interface driver ndiswrapper
[  654.938771] usbcore: deregistering interface driver ndiswrapper
[  654.934964] ndiswrapper (ntoskernel_exit:2708): object ffff8100360e0630(2) was not freed, freeing it now
[  669.786879] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  669.806991] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  669.807003] ndiswrapper (load_sys_files:210): couldn't prepare driver 'mrv8335'
[  669.812447] ndiswrapper (load_wrap_driver:112): couldn't load driver mrv8335; check system log for messages from 'loadndisdriver'
[  669.815227] usbcore: registered new interface driver ndiswrapper
```

Looks like a driver issue? I'm not sure how to follow up on the line that says "check system log for messages from 'loadndisdriver'" The gnome system log spits out the same output as above.

```
ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
```
This is saying that the driver you are using is a 32-bit driver.  You will need to find a Windows (but not Vista) 64-bit driver.

---

### Post by Fainblat on 2009-04-23
Hey, my problem is almost the same. But the diferencies are that my iwconfig shows the right access point AND my dmesg showed the following:

 513.684910] ndiswrapper: device wlan0 removed                                  
[  513.685440] ndiswrapper 0000:03:00.0: PCI INT A disabled                       
[  513.687020] usbcore: deregistering interface driver ndiswrapper
[  531.784838] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  531.797750] ndiswrapper: driver oem18 (Customer,12/30/2005,3.2.3.2) loaded
[  531.797931] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  531.797945] ndiswrapper 0000:03:00.0: setting latency timer to 64
[  531.798504] ndiswrapper: using IRQ 20
[  532.053288] wlan0: ethernet device ok:10:ok:0e:7f:3f using NDIS driver: oem18,version: 0x3020007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[  532.056572] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  532.058196] usbcore: registered new interface driver ndiswrapper

Any help? Thank you.

Ah, one more thing: I have the same problem when I do the ndiswrapper -m line. And I use an 8.10 intrepid. I made a sudo kwrite on the modules file and checked there was no line for ndiswrapper. So, I put one there, but the error persisted.

Hope you help me. Thank you!

---

### Post by Fainblat on 2009-04-23
The iwlist scan gets to see all the networks, the iwconfig is all right. It just doesnt change the bit rate - it stays at 1 mb - and it doesnt get to internet. What can I do????

---

### Post by Fainblat on 2009-04-26
Solved.

---

