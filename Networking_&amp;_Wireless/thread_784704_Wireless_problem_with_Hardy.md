---
title: "Wireless problem with Hardy"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ranlil on 2008-05-06
I upgraded over the net using my pc card wireless adapter.  After the completion of the upgrade,and rebooting the wireless adapter doesn't show up.  Not even to be configured.  It worked great in all the previous versions, automatically without loading drivers.  It always showed up before as a IBM 22 Mbps adapter.  Now I'm wired until this gets figured out or fall back.

Sure would appreciate some help.

---

### Post by chili555 on 2008-05-06
Tell us more:```
sudo lshw -C network
```Thanks.

---

### Post by ranlil on 2008-05-07
Sorry.... It was TI

*-network UNCLAIMED     
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64

---

### Post by chili555 on 2008-05-07
Could you please show us:```
dmesg | grep acx
```Let's try to see what's not working, if we can.

---

### Post by ranlil on 2008-05-08
[   37.599332] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   37.599354] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   37.608154] acx: found ACX100-based wireless network card at 0000:06:00.0, irq:9, phymem1:0x1C010000, phymem2:0x1C000000, mem1:0xccb4e000, mem1_size:4096, mem2:0xccc60000, mem2_size:65536
[   37.620185] acx: loading firmware for acx100 chipset with radio ID 11
[   37.635306] acx: firmware image 'acx/default/tiacx100c11' was not provided. Check your hotplug scripts
[   37.648813] acx: firmware image 'acx/default/tiacx100' was not provided. Check your hotplug scripts
[   37.648837] acx: reset_dev() FAILED
[   37.660965] acx_pci: probe of 0000:06:00.0 failed with error -5
[   37.661116] usbcore: registered new interface driver acx_usb

---

### Post by chili555 on 2008-05-09
Hmmm. Appears to not find the needed firmware. This is installed in *linux-restricted-modules-`uname -r`*. `uname -r` is just a convenient way to say, 'matching my running kernel.' The little tick marks are both the little mark on the same key with ~.

The best way to see if you have it installed is:```
sudo apt-get install linux-restricted-modules-`uname -r`
```Either it will install or it will say you already have the latest version.

If you have it installed, please do:```
sudo updatedb
locate acx/default/tiacx100c11
```Let's see if the firmware is in the right place.

---

### Post by ranlil on 2008-05-09
It comes back with:
E: Couldn't find package linux-restricted-modules

---

### Post by ranlil on 2008-05-09
WOW!!  I finally got it.  Because of your help, I figured out the restricted drivers weren't installed and the sytax must have changed in Hardy for getting them.  I went into the package manager and checked the restricted drivers box under repositories.  Then I ran the update manager and it said it was up to date.  I hit check again and it finally loaded and installed everything.

I can't thank you enough for your help!

---

### Post by Muley63 on 2008-05-26
I had the same problem with my D-Link wireless 520+ and nVidia 6200. Everytime the kernel is updated, my graphics and networks goes out and I always forget to check my restricted drivers. Thanks for the memory assist!

If you're experiencing the same problem, reboot to a an older kernel (hit 'Esc' at GRUB) and install the restricted drivers in Synaptic.

I checked the following in Synaptic:

    1. **linux-restricted-modules**, Generic Linux restricted modules.
    2. **linux-restricted-modules-2.6.24-17-generic,**  Non-free Linux 2.6.24 modules on x86/x86_64
    3. **linux-restricted-modules-generic,**   Restricted Linux modules for generic kernels

Thanks, Chill

---

