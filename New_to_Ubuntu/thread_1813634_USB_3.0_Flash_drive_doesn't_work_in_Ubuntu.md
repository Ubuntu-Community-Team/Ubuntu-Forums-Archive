---
title: "USB 3.0 Flash drive doesn't work in Ubuntu"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by powerpleb on 2011-07-28
I just bought a Sharkoon USB 3.0 flash drive and it doesn't seem to be working in Ubuntu 11.04. Windows 7 recognizes it and uses it fine.

When I put it into a USB 2.0 port it works OK. In lsusb it shows up as this:
```
Bus 002 Device 006: ID 13fe:5000 Kingston Technology Company Inc.
```

However, putting it into one of the USB 3.0 ports gets no response.
It doesn't show up at all in lsusb.

Moreover, if I insert a USB 2.0 flash drive in the same USB 3.0 port, it works.

This has got me confused. Are USB 3.0 flash drives supported in Ubuntu these days?:confused::confused:

---

### Post by androssofer on 2011-07-28
> **powerpleb said:**
> I just bought a Sharkoon USB 3.0 flash drive and it doesn't seem to be working in Ubuntu 11.04. Windows 7 recognizes it and uses it fine.

When I put it into a USB 2.0 port it works OK. In lsusb it shows up as this:
```
Bus 002 Device 006: ID 13fe:5000 Kingston Technology Company Inc.
```

However, putting it into one of the USB 3.0 ports gets no response.
It doesn't show up at all in lsusb.

Moreover, if I insert a USB 2.0 flash drive in the same USB 3.0 port, it works.

This has got me confused. Are USB 3.0 flash drives supported in Ubuntu these days?:confused::confused:

it is supported... since 9.10 as far as i know... there was however a usb 3 bug found in 11.04. is ur machine fully up to date?

---

### Post by powerpleb on 2011-07-28
> **androssofer said:**
> it is supported... since 9.10 as far as i know... there was however a usb 3 bug found in 11.04. is ur machine fully up to date?

Yea it is. :(

I wonder if it has something to do with this specific flash drive... 

Or even the motherboard. Its a Gigabyte P67-UD5-B3.

---

### Post by Jonny87 on 2011-07-28
I've seen this sort of thing before. To see if it is the same issue, would you mind doing the following;

Open up Disk Utility (type disk into the unity menu)
Find the usb drive in question,
Try to manually mounting it by clicking "Mount Volume".

if it comes up with an error then post the error here in this thread.

---

### Post by powerpleb on 2011-07-28
> **Jonny87 said:**
> I've seen this sort of thing before. To see if it is the same issue, would you mind doing the following;

Open up Disk Utility (type disk into the unity menu)
Find the usb drive in question,
Try to manually mounting it by clicking "Mount Volume".

if it comes up with an error then post the error here in this thread.
I'll try, but if it isn't showing up in lsusb, I doubt it will show up in fdisk.

---

### Post by powerpleb on 2011-07-28
Yeah... Didn't show up. :confused:

---

### Post by Jonny87 on 2011-07-28
> **powerpleb said:**
> I'll try, but if it isn't showing up in lsusb, I doubt it will show up in fdisk.

Thats possibly true. My dad had a very similar not to long ago on his new netbook running 11.04. So this will at least determine if it is the same. If not there's nothing lost.

---

### Post by Jonny87 on 2011-07-28
> **powerpleb said:**
> Yeah... Didn't show up. :confused:
Ok, then perhaps it is something to do with the usb 3.0 bug mentioned earlier. I'll keep thinking but all the best with it.

---

### Post by powerpleb on 2011-07-29
OK, so I've concluded that if it isn't even showing up in lsusb it there must be a problem with USB3 in general. (Even if it was the particular flash drive, it would at least show up even if it wouldn't mount, right?).

Nevertheless, my lsusb output shows the root USB 3.0 hub. So I'm even more confused.
```
Bus 003 Device 005: ID 2109:0810  
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 004: ID 2109:3431  
Bus 002 Device 003: ID 2109:3431  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Also, this is the USB section of lshw:
```
          *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fbdfe000-fbdfffff
        *-communication UNCLAIMED
             description: Communication controller
             product: 6 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:fbfff000-fbfff00f
        *-usb:0
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff

```
This is cat /var/log/kern.log | grep xhci
```
Jul 29 16:29:43 andrew-ubuntu kernel: [  988.279916] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
Jul 29 16:29:45 andrew-ubuntu kernel: [  990.334044] xhci_hcd 0000:02:00.0: Timeout while waiting for stop endpoint command
Jul 29 16:30:38 andrew-ubuntu kernel: [ 1042.285478] xhci_hcd 0000:02:00.0: Timeout while waiting for stop endpoint command
Jul 29 16:31:30 andrew-ubuntu kernel: [ 1094.925001] xhci_hcd 0000:02:00.0: Timeout while waiting for stop endpoin
```
cat /var/log/kern.log | grep usb
```
Jul 29 16:29:43 andrew-ubuntu kernel: [  988.279925] hub 3-0:1.0: couldn't allocate port 2 usb_device
```

Oh, I think I've also found that bug you guys mentioned:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775543)

---

### Post by Maniacal on 2011-08-03
My NEC uPD720200 USB 3.0 Controller worked fine right out of the box under Natty with 2.6.38-10generic kernel. Have a multi-boot system with Win7/64bit on one drive and Natty/64bit on another. I'd just replaced my MB and swapped all hardware over to it along with adding the USB 3.0 Controller. Decided to not reinstall either OS and just go with what was on the drives. Was pleasantly surprised when it worked. Neither OS choked. Natty configured the USB 3.0 Controller right away and gave me access to an external USB 3.0 drive. Had to install drivers under Win7 of course. All was well until I decided to start messing with Natty's kernel. Made some changes, compiled and installed 3.0.0 kernel, and everything worked except for USB 3.0 Controller. Stepped back to generic kernels 2.6.38-8 & 10 with no luck. Now I'm running on a new installation of Natty and the USB 3.0 Controller still isn't working. Natty does see the Controller when I type "lshw" in Terminal, and a 3.0 root hub  when I type "lsusb". It still works under Win7 and all other USB ports on the system are working fine under Natty. I feel like an idiot for even touching the kernel. Have read bug report on Launchpad and subscribed to emails and comments. Now it's time to just wait it out.

---

### Post by Maniacal on 2011-08-06
Good News! Swapped my external 4TB RAID drive from USB 2.0 to eSATA. The NEC uPD720200 USB 3.0 Controller came back to life on next boot. Have access to by USB 3.0 external drive once again under Natty. I'd like to pass this along to the folks working this bug on Launchpad but haven't figured out how to make a comment in the thread.

---

### Post by simoniemesko on 2011-08-17
Hm, my usb port seems to have smae problem on natty. no luck for me. My flash key used to be hot and camera light on when plugged in usb2.0, but no luck on 3.0. Would like to see more replyies to solve it...

---

