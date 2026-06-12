---
title: "Anker USB 2.5G Ethernet adapter on Ubuntu 22.04.1"
date: 2022-11-07
forum: Networking &amp; Wireless
---

### Post by mxhajduczenia on 2022-11-07
Good evening, Ubuntu forum. 

I have recently purchased a USB-C Anker 2.5G Ethernet adapter to be able to connect to the home wired network for higher throughput. The adapter works as advertised when it works correctly. I noticed that it works just fine when the system has been rebooted and the adapter is plugged into the USB-C port, it works just fine. After the system has been suspended, no matter what I do, the adapter is not recognized anymore. 

When the adapter is not recognized, all I can see is my WiFi network entry as shown below

```
lshw -C network
  *-network                 
       description: Wireless interface
       product: Comet Lake PCH-LP CNVi WiFi
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 00
       serial: 10:3d:1c:07:2e:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-52-generic firmware=66.f1c864e0.0 QuZ-a0-hr-b0-66.u ip=192.168.150.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:e0110000-e0113fff
```

Following the recommendations I found elsewhere, I did install the latest RTL8152 drivers for the chipset that the adapter is using and they are properly showing up in lsmod as shown below. 

```
lsmod | grep r8
r8152                 241664  0

```

Is there anything else I should be aware as far as these USB adapters are concerned? It is pretty annoying to have to reboot the system all the time to have it working correctly. 

Regards

M

---

### Post by mxhajduczenia on 2022-11-07
After a system reboot, this is what I can see in terms of network devices. The second entry does show r8152 driver used as expected, but it does disappear once the system has been suspended. 

```
lshw -C network
  *-network                 
       description: Wireless interface
       product: Comet Lake PCH-LP CNVi WiFi
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 00
       serial: 10:3d:1c:07:2e:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-52-generic firmware=66.f1c864e0.0 QuZ-a0-hr-b0-66.u ip=192.168.150.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:e0110000-e0113fff
  *-network
       description: Ethernet interface
       physical id: 14
       bus info: usb@4:1
       logical name: enx00e04c92d40b
       serial: 00:e0:4c:92:d4:0b
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v2.15.0 (2021/04/15) duplex=full ip=192.168.150.22 link=yes multicast=yes port=MII speed=1Gbit/s
```

---

### Post by mxhajduczenia on 2022-11-07
Some more debugging via dmesg sequence 

STEP 1: Device initialized during the boot process, all works fine 

```
sudo dmesg | grep r8
[    0.119521] percpu: Embedded 60 pages/cpu s208896 r8192 d28672 u262144
[    0.119533] pcpu-alloc: s208896 r8192 d28672 u262144 alloc=1*2097152
[    1.807418] r8152: loading out-of-tree module taints kernel.
[    1.813359] r8152: module verification failed: signature and/or required key missing - tainting kernel
[    2.033809] r8152 4-1:1.0 (unnamed net_device) (uninitialized): netif_napi_add() called with weight 256
[    2.034224] r8152 4-1:1.0 eth0: v2.15.0 (2021/04/15)
[    2.034229] r8152 4-1:1.0 eth0: This product is covered by one or more of the following patents:
[    2.034312] usbcore: registered new interface driver r8152
[    2.054400] r8152 4-1:1.0 enx00e04c92d40b: renamed from eth0
[    3.757696] r8152 4-1:1.0 eth0: v2.15.0 (2021/04/15)
[    3.757699] r8152 4-1:1.0 eth0: This product is covered by one or more of the following patents:
[    3.812033] r8152 4-1:1.0 enx00e04c92d40b: renamed from eth0
[    6.688353] r8152 4-1:1.0 enx00e04c92d40b: carrier on
```

STEP 2: device removed and then plugged back in 

```
[  655.501827] usb 4-1: USB disconnect, device number 2
[  655.502134] xhci_hcd 0000:37:00.0: WARN Set TR Deq Ptr cmd failed due to incorrect slot or ep state.
[  667.009502] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
[  667.030503] usb 4-1: New USB device found, idVendor=0bda, idProduct=8156, bcdDevice=31.00
[  667.030513] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[  667.030517] usb 4-1: Product: USB 10/100/1G/2.5G LAN
[  667.030520] usb 4-1: Manufacturer: Realtek
[  667.030522] usb 4-1: SerialNumber: 001000001
[  667.166486] usb 4-1: reset SuperSpeed USB device number 3 using xhci_hcd
```

STEP 3: suspend the system, remove the adapter, wake the system up, and then plug in he adapter - network did come back up

```
[  791.650931] usb 4-1: new SuperSpeed USB device number 4 using xhci_hcd
[  791.671864] usb 4-1: New USB device found, idVendor=0bda, idProduct=8156, bcdDevice=31.00
[  791.671879] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[  791.671885] usb 4-1: Product: USB 10/100/1G/2.5G LAN
[  791.671889] usb 4-1: Manufacturer: Realtek
[  791.671893] usb 4-1: SerialNumber: 001000001
[  791.811145] usb 4-1: reset SuperSpeed USB device number 4 using xhci_hcd
```

STEP 4: suspend the system, remove the adapter, (give it some time, about 2 minutes), plug in the adapter, and wake the system up with adapter in, driver is not accessible anymore and network is not visible

```
[  906.078174] ACPI: EC: interrupt unblocked
[  907.712397] xhci_hcd 0000:37:00.0: can't change power state from D3cold to D0 (config space inaccessible)
[  907.788616] xhci_hcd 0000:37:00.0: can't change power state from D3cold to D0 (config space inaccessible)
[  907.788639] xhci_hcd 0000:37:00.0: Controller not ready at resume -19
[  907.788640] xhci_hcd 0000:37:00.0: PCI post-resume error -19!
[  907.788641] xhci_hcd 0000:37:00.0: HC died; cleaning up
[  907.788644] PM: dpm_run_callback(): pci_pm_resume+0x0/0x100 returns -19
[  907.788652] xhci_hcd 0000:37:00.0: PM: failed to resume async: error -19
[  908.074749] OOM killer enabled.
[  908.074751] Restarting tasks ... done.
[  908.085161] mei_hdcp 0000:00:16.0-b638ab7e-94e2-4ea2-a552-d1c54b627f04: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
[  908.103611] thermal thermal_zone12: failed to read out thermal zone (-61)
[  908.103904] PM: suspend exit
[  908.111346] usbcore: registered new interface driver r8152
```

It *seems* that waking the system up from a suspended state breaks something in the USB adapter initialization process. I am able to reproduce it reliably, i.e., after a clean system reboot, when I repeat step 4 above, I always end up with a broken network adapter irrespective of the installed drivers. If process outlined in step 3 is followed, i.e., adapter is plugged in after the system comes out of suspended state, everything seems to recover correctly and the network adapter comes back online. 

Any clue what this might be and how to remedy it?

M

---

### Post by TheFu on 2022-11-08
For USB connected devices like this, you need to update the suspend power on it so that the suspend event unplugs the device and that the power-on event re-plugs the device.  I remember doing this on a laptop years ago, but I don't recall exactly which files I created/changed to achieve it. Plus, it was for an older release, not 22.04.

Looks like there is a touchpad (which is an internal USB connection on most laptops) example script that unloads some kernel modules for suspend|suspend_hybrid|hibernate options and lets the automatic replug code handle what needs to happen when the system comes up to power again.  This is under /etc/ somewhere.  I'd use 'sudo grep -rl suspend . '  to find the files of interest on your system for examples.

The easy answer is to just manually disconnect the USB and reconnect it after the system comes out of standby, before any network resources (especially storage) are contacted by some user action.

It's pretty late here, so I won't look directly on my laptop for the files.  My eyes are starting to gloss over.  I was looking in the backup storage for the laptop and didn't see the files I modified. I don't backup everything, so I'm a bit worried that change was placed somewhere that isn't part of my backups.  Hummmm.  I'd guess somewhere under /lib/ ... which I don't backup.

---

### Post by mxhajduczenia on 2022-11-08
First and foremost, thanks for the answer despite the late hour 

> **TheFu said:**
> I remember doing this on a laptop years ago, but I don't recall exactly which files I created/changed to achieve it. Plus, it was for an older release, not 22.04.

This does sound like a problem / behavior that has existed for a good long while then. Is there any reason why it is not fixed at the OS level? I would assume that all USB devices will require a similar behavior, i.e., offload before suspend and load on resume? It seems a bit awkward to have to dabble with it manually under OS version 22 when USB-attached devices are neither new nor exotic at this time. With standard Ethernet ports (and other) going the way of dodo on many laptops, the number of USB-attached external devices will only increase, I would think. 

> **TheFu said:**
> The easy answer is to just manually disconnect the USB and reconnect it  after the system comes out of standby, before any network resources  (especially storage) are contacted by some user action. 

Since I am not a fan of messing with my primary work laptop for experimentation purposes, I will likely stick around with plugging the adapter only when the machine is out of suspend state. It is annoying, though, so perhaps I will stand up another one just to experiment some and see what I can achieve. At this time, I am not sure what to even search for as far as "update the suspend power" is concerned. Any pointers would be really appreciated. 

thanks !

M

---

### Post by TheFu on 2022-11-08
> **mxhajduczenia said:**
> 
This does sound like a problem / behavior that has existed for a good long while then. Is there any reason why it is not fixed at the OS level? I would assume that all USB devices will require a similar behavior, i.e., offload before suspend and load on resume? It seems a bit awkward to have to dabble with it manually under OS version 22 when USB-attached devices are neither new nor exotic at this time. With standard Ethernet ports (and other) going the way of dodo on many laptops, the number of USB-attached external devices will only increase, I would think. 



Since I am not a fan of messing with my primary work laptop for experimentation purposes, I will likely stick around with plugging the adapter only when the machine is out of suspend state. It is annoying, though, so perhaps I will stand up another one just to experiment some and see what I can achieve. At this time, I am not sure what to even search for as far as "update the suspend power" is concerned. Any pointers would be really appreciated. 


Why questions are hard to answer, since nobody here works for Canonical nor is part of the Linux Kernel development team.  Everyone here, including the moderators are just other users around the world hoping to help find solutions in the real-world.

There are an endless number of USB devices. Each has a driver.  The quality of those drivers varies greatly. The only people who can fix that would be the chip makers ... so , not Anker, but the company who makes the driver for the chip they used.  You may want to complain to Anker, since they have the ear of the manufacturers and I bet you'll actually find someone there who will listen and pass on the complaint.

When I suggested unplugging and re-plugging in the USB device after adding power from standby modes, that's a physical thing. No need to mess with the OS settings.  I would mention that waiting 5 seconds from the unplug to the re-plug would allow enough time for the OS to recognize the change.  USB connections don't trip a physical connector, it is only an electrical notification that something changed for the OS to see.  It really surprises me that it works nearly all the time, but with every OS, recognizing that a device is plugged in does take a few seconds.

You and I seem to be odd in this world. Most people with laptops either only use wifi or they get laptops with ethernet ports. The first time I saw a laptop without a built-in ethernet port was around 2011. I wasn't happy.  Wifi just doesn't compare to gigE ethernet for stability, performance, security or ease of use.  In the mid-2000s, one of my projects was to roll out wifi access to over 1200+ corporate locations.  That project taught me to avoid wifi whenever possible for a number of reasons, so I'm with you on using a USB-toGigE adapter.  I have one connected to my laptop right now, but it isn't running 22.04.  I don't have any 2.5Gbps network gear, just GigE.  It isn't like my storage is that fast.

---

### Post by mxhajduczenia on 2022-11-08
> **TheFu said:**
> You and I seem to be odd in this world. Most people with laptops either only use wifi or they get laptops with ethernet ports. The first time I saw a laptop without a built-in ethernet port was around 2011. I wasn't happy.  Wifi just doesn't compare to gigE ethernet for stability, performance, security or ease of use.  In the mid-2000s, one of my projects was to roll out wifi access to over 1200+ corporate locations.  That project taught me to avoid wifi whenever possible for a number of reasons, so I'm with you on using a USB-toGigE adapter.  I have one connected to my laptop right now, but it isn't running 22.04.  I don't have any 2.5Gbps network gear, just GigE.  It isn't like my storage is that fast.

Unfortunately, the future seems to be geared towards super slim laptops with USB ports (if you get any at all) or no ports at all and everything done wirelessly. While it is certainly convenient for some couch work, there are plenty of times when a good old wired Ethernet comes in handy as you pointed out. Being able to push a few GB worth of files for backup over WiFi is a pain, irrespective of what next wave of WiFi comes around. 

At home I am all GigE right now and that is more than plenty for me for home use. I got a 2.5GE adapter for test work I am doing to see how far past 1GE limit I can get and it is surprisingly well performed (I was able to hit 2.45 Gbps under favorable conditions). I would like to keep with it, since it works very well and the only downside is the whole behavior when the laptop comes out of suspended state. 

> **TheFu said:**
>  When I suggested unplugging and re-plugging in the USB device after  adding power from standby modes, that's a physical thing. No need to  mess with the OS settings.  I would mention that waiting 5 seconds from  the unplug to the re-plug would allow enough time for the OS to  recognize the change.  USB connections don't trip a physical connector,  it is only an electrical notification that something changed for the OS  to see.  It really surprises me that it works nearly all the time, but  with every OS, recognizing that a device is plugged in does take a few  seconds. 

Understood, I would be happy with whatever - right now I will just make sure (as long as I can remember) to plug the adapter only with the laptop out of the suspend state. Not ideal, but workable most of the time. If there was a way to trip the OS to re-discover the device (I have been reading a bit about the USB offload?) after leaving the suspend state, that might do the job. 

Perhaps this is not the best place to post a question like this?

M

---

### Post by TheFu on 2022-11-08
> **mxhajduczenia said:**
>  Understood, I would be happy with whatever - right now I will just make sure (as long as I can remember) to plug the adapter only with the laptop out of the suspend state. Not ideal, but workable most of the time. If there was a way to trip the OS to re-discover the device (I have been reading a bit about the USB offload?) after leaving the suspend state, that might do the job. 

Perhaps this is not the best place to post a question like this?

M

I don't think you'll need to worry about it when going into suspend, just after returning to full power.  If I remember, I'll look on my laptop for the specific file.  I haven't really used that laptop much the last year.

---

### Post by mxhajduczenia on 2022-11-09
[https://answers.launchpad.net/ubuntu/+question/703762](https://answers.launchpad.net/ubuntu/+question/703762) - I believe it was a driver issue - the new one from Realtek (had to find it, build it, and remove existing 2.15.0 driver) seems to be working correctly. 

Thanks for the time and attention !

---

### Post by TheFu on 2022-11-10
> **mxhajduczenia said:**
> [https://answers.launchpad.net/ubuntu/+question/703762](https://answers.launchpad.net/ubuntu/+question/703762) - I believe it was a driver issue - the new one from Realtek (had to find it, build it, and remove existing 2.15.0 driver) seems to be working correctly. 

Thanks for the time and attention !

Appears that my laptop isn't using any special post-standby stuff anymore. I looked. It is just working.
If this is solved with the new drivers, please use the "thread tools" button/link near the top to help others in the community know that.

---

